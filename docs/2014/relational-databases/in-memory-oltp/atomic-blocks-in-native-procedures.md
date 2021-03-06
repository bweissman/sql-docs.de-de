---
title: Atomic-Blöcke | Microsoft-Dokumentation
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: in-memory-oltp
ms.topic: conceptual
ms.assetid: 40e0e749-260c-4cfc-a848-444d30c09d85
author: CarlRabeler
ms.author: carlrab
manager: craigg
ms.openlocfilehash: 4bad6da6de694d9b835a6d3fe23fbc68d8642f50
ms.sourcegitcommit: 3da2edf82763852cff6772a1a282ace3034b4936
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 10/02/2018
ms.locfileid: "48124100"
---
# <a name="atomic-blocks"></a>ATOMIC-Blöcke
  `BEGIN ATOMIC` ist Teil des ANSI SQL-Standards. [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] unterstützt ATOMIC-Blöcke nur auf der obersten Ebene systemintern kompilierter gespeicherter Prozeduren.  
  
-   Jede systemintern kompilierte gespeicherte Prozedur enthält genau einen Block mit [!INCLUDE[tsql](../../includes/tsql-md.md)] -Anweisungen. Dies ist ein ATOMIC-Block.  
  
-   Nicht systemeigene interpretierte gespeicherte [!INCLUDE[tsql](../../includes/tsql-md.md)] -Prozeduren und Ad-hoc-Batches unterstützen keine ATOMIC-Blöcke.  
  
 ATOMIC-Blöcke werden (unteilbar) innerhalb der Transaktion ausgeführt. Entweder werden alle Anweisungen im Block erfolgreich ausgeführt, oder für den gesamten Block wird ein Rollback zu dem Sicherungspunkt ausgeführt, der beim Starten des Blocks erstellt wurde. Darüber hinaus sind die Sitzungseinstellungen für den ATOMIC-Block fest definiert. Wird derselbe ATOMIC-Block in Sitzungen mit unterschiedlichen Einstellungen ausgeführt, ergibt sich unabhängig von den Einstellungen der aktuellen Sitzung dasselbe Verhalten.  
  
## <a name="transactions-and-error-handling"></a>Transaktionen und Fehlerbehandlung  
 Wenn in einer Sitzung bereits eine Transaktion vorhanden ist (da von einem Batch eine `BEGIN TRANSACTION`-Anweisung ausgeführt wurde und die Transaktion aktiv bleibt), wird durch das Starten eines ATOMIC-Blocks in der Transaktion ein Sicherungspunkt erstellt. Wenn der Block ohne Ausnahme beendet wird, wird der erstellte Sicherungspunkt für den Block festgeschrieben. Für die Transaktion wird jedoch erst ein Commit ausgeführt, wenn für die Transaktion auf Sitzungsebene ein Commit erfolgt. Wenn der Block eine Ausnahme auslöst, wird für den ausgeführten Teil des Blocks ein Rollback ausgeführt, die Transaktion auf Sitzungsebene wird jedoch weiterhin ausgeführt, sofern die Ausnahme nicht zum Fehlschlagen der Transaktion führt. Beispielsweise kann ein Schreibkonflikt zum Fehlschlagen einer Transaktion führen, ein Typumwandlungsfehler jedoch nicht.  
  
 Wenn eine Sitzung keine aktive Transaktion enthält, wird durch `BEGIN ATOMIC` eine neue Transaktion gestartet. Wenn außerhalb des Blockbereichs keine Ausnahme ausgelöst wird, wird für die Transaktion am Ende des Blocks ein Commit ausgeführt. Wenn der Block eine Ausnahme auslöst (d. h., die Ausnahme wird nicht innerhalb des Blocks abgefangen und behandelt), wird ein Rollback für die Transaktion ausgeführt. Für Transaktionen, die einen einzelnen atomic-Block umfassen (eine einzelne systemintern kompilierte gespeicherte Prozedur), Sie müssen nicht schreiben explizite `BEGIN TRANSACTION` und `COMMIT` oder `ROLLBACK` Anweisungen.  
  
 Systemintern kompilierte gespeicherte Prozeduren unterstützen die `TRY`, `CATCH`, und `THROW` Konstrukte zur Fehlerbehandlung. `RAISERROR` wird nicht unterstützt.  
  
 Das folgende Beispiel veranschaulicht das Fehlerbehandlungsverhalten bei ATOMIC-Blöcken und systemintern kompilierten gespeicherten Prozeduren:  
  
```tsql  
-- sample table  
CREATE TABLE dbo.t1 (  
  c1 int not null primary key nonclustered  
)  
WITH (MEMORY_OPTIMIZED=ON)  
GO  
  
-- sample proc that inserts 2 rows  
CREATE PROCEDURE dbo.usp_t1 @v1 bigint not null, @v2 bigint not null  
WITH NATIVE_COMPILATION, SCHEMABINDING, EXECUTE AS OWNER  
AS  
BEGIN ATOMIC  
WITH (TRANSACTION ISOLATION LEVEL = SNAPSHOT, LANGUAGE = N'us_english', DELAYED_DURABILITY = ON)  
  
  INSERT dbo.t1 VALUES (@v1)  
  INSERT dbo.t1 VALUES (@v2)  
  
END  
GO  
  
-- insert two rows  
EXEC dbo.usp_t1 1, 2  
GO  
  
-- verify we have no active transaction  
SELECT @@TRANCOUNT  
GO  
  
-- verify the rows 1 and 2 were committed  
SELECT c1 FROM dbo.t1  
GO  
  
-- execute proc with arithmetic overflow  
EXEC dbo.usp_t1 3, 4444444444444  
GO  
-- expected error message:  
-- Msg 8115, Level 16, State 0, Procedure usp_t1  
-- Arithmetic overflow error converting bigint to data type int.  
  
-- verify we have no active transaction  
SELECT @@TRANCOUNT  
GO  
  
-- verify rows 3 was not committed; usp_t1 has been rolled back  
SELECT c1 FROM dbo.t1  
GO  
  
-- start a new transaction  
BEGIN TRANSACTION  
  -- insert rows 3 and 4  
  EXEC dbo.usp_t1 3, 4  
  
  -- verify there is still an active transaction  
  SELECT @@TRANCOUNT  
  
  -- verify the rows 3 and 4 were inserted  
  SELECT c1 FROM dbo.t1 WITH (SNAPSHOT)   
  ORDER BY c1  
  
  -- catch the arithmetic overflow error  
  BEGIN TRY  
    EXEC dbo.usp_t1 5, 4444444444444  
  END TRY  
  BEGIN CATCH  
    PRINT N'Error occurred: ' + error_message()  
  END CATCH  
  
  -- verify there is still an active transaction  
  SELECT @@TRANCOUNT  
  
  -- verify rows 3 and 4 are still in the table, and row 5 has not been inserted  
  SELECT c1 FROM dbo.t1 WITH (SNAPSHOT)   
  ORDER BY c1  
  
COMMIT  
GO  
  
-- verify we have no active transaction  
SELECT @@TRANCOUNT  
GO  
  
-- verify rows 3 and 4 has been committed  
SELECT c1 FROM dbo.t1  
ORDER BY c1  
GO  
```  
  
 Bei folgenden, für speicheroptimierte Tabellen spezifischen Fehlern schlägt eine Transaktion fehl. Wenn sie im Bereich eines ATOMIC-Blocks auftreten, wird die Transaktion abgebrochen: 10772, 41301, 41302, 41305, 41325, 41332 und 41333.  
  
## <a name="session-settings"></a>Sitzungseinstellungen  
 Die Sitzungseinstellungen in ATOMIC-Blöcken werden bei der Kompilierung der gespeicherte Prozedur fest definiert. Einige Einstellungen können angegeben werden, mit `BEGIN ATOMIC` während andere immer denselben festen sind.  
  
 Die folgenden Optionen sind für `BEGIN ATOMIC` erforderlich:  
  
|Erforderliche Einstellung|Description|  
|----------------------|-----------------|  
|`TRANSACTION ISOLATION LEVEL`|Unterstützte Werte sind `SNAPSHOT`, `REPEATABLEREAD`, und `SERIALIZABLE`.|  
|`LANGUAGE`|Bestimmt Datums- und Uhrzeitformate sowie Systemmeldungen. Alle Sprachen und Aliase in [sys.syslanguages &#40;Transact-SQL&#41;](/sql/relational-databases/system-compatibility-views/sys-syslanguages-transact-sql) werden unterstützt.|  
  
 Die folgenden Einstellungen sind optional:  
  
|Optionale Einstellung|Description|  
|----------------------|-----------------|  
|`DATEFORMAT`|Alle Datumsformate von [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] werden unterstützt. Wenn angegeben, `DATEFORMAT` überschreibt das Standarddatumsformat zugeordneten `LANGUAGE`.|  
|`DATEFIRST`|Falls angegeben, überschreibt `DATEFIRST` den Standardwert, der `LANGUAGE` zugeordnet ist.|  
|`DELAYED_DURABILITY`|Unterstützte Werte sind `OFF` und `ON`.<br /><br /> [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]-Transaktionscommits können entweder vollständig dauerhaft (Standardeinstellung) oder verzögert dauerhaft sein. Weitere Informationen finden Sie unter [Steuern der Transaktionsdauerhaftigkeit](../logs/control-transaction-durability.md).|  
  
 Die folgenden SET-Optionen verfügen für alle ATOMIC-Blöcke in allen systemintern kompilierten gespeicherten Prozeduren über denselben Systemstandardwert:  
  
|SET-Option|Systemstandard für ATOMIC-Blöcke|  
|----------------|--------------------------------------|  
|ANSI_NULLS|ON|  
|ANSI_PADDING|ON|  
|ANSI_WARNING|ON|  
|ARITHABORT|ON|  
|ARITHIGNORE|OFF|  
|CONCAT_NULL_YIELDS_NULL|ON|  
|IDENTITY_INSERT|OFF|  
|NOCOUNT|ON|  
|NUMERIC_ROUNDABORT|OFF|  
|QUOTED_IDENTIFIER|ON|  
|ROWCOUNT|0|  
|TEXTSIZE|0|  
|XACT_ABORT|OFF<br /><br /> Nicht abgefangene Ausnahmen bewirken ein Rollback für den ATOMIC-Block, führen jedoch nicht zu einem Abbruch der Transaktion, solange die Transaktion durch den Fehler nicht fehlschlägt.|  
  
## <a name="see-also"></a>Siehe auch  
 [Systemintern kompilierte gespeicherte Prozeduren](natively-compiled-stored-procedures.md)  
  
  
