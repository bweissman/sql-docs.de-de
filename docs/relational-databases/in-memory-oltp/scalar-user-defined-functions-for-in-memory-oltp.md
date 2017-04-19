---
title: "Benutzerdefinierte Skalarfunktionen f&#252;r In-Memory-OLTP | Microsoft Docs"
ms.custom: 
  - "SQL2016_New_Updated"
ms.date: "03/20/2017"
ms.prod: "sql-server-2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "database-engine-imoltp"
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: d2546e40-fdfc-414b-8196-76ed1f124bf5
caps.latest.revision: 9
author: "sabotta"
ms.author: "carlasab"
manager: "jhubbard"
caps.handback.revision: 9
---
# Benutzerdefinierte Skalarfunktionen f&#252;r In-Memory-OLTP
[!INCLUDE[tsql-appliesto-ss2016-asdb-xxxx-xxx_md](../../includes/tsql-appliesto-ss2016-asdb-xxxx-xxx-md.md)]

  In [!INCLUDE[ssSQL15](../../includes/sssql15-md.md)] können Sie nativ kompilierte benutzerdefinierte Skalarfunktionen erstellen und löschen. Sie können auch die folgenden benutzerdefinierten Funktionen ändern. Durch native Kompilierung wird die Leistung der Auswertung benutzerdefinierter Funktionen in Transact-SQL verbessert.  
  
 Wenn Sie eine nativ kompilierte benutzerdefinierte Skalarfunktion ändern, bleibt die Anwendung verfügbar, während der Vorgang ausgeführt und die neue Version der Funktion kompiliert wird.  
  
 Informationen zu unterstützten T-SQL-Konstrukten finden Sie unter [Unterstützte Funktionen für nativ kompilierte T-SQL-Module](../../relational-databases/in-memory-oltp/supported-features-for-natively-compiled-t-sql-modules.md).  
  
## Erstellen, Löschen und Ändern von benutzerdefinierten Funktionen  
 CREATE FUNCTION wird zum Erstellen der nativ kompilierten benutzerdefinierten Skalarfunktion, DROP FUNCTION zum Entfernen der benutzerdefinierten Funktion und ALTER FUNCTION zum Ändern der Funktion verwendet. BEGIN ATOMIC WITH wird für die benutzerdefinierten Funktionen benötigt.  
  
 Informationen zur unterstützten Syntax und zu Einschränkungen finden Sie in den folgenden Themen.  
  
-   [CREATE FUNCTION &#40;Transact-SQL&#41;](../../t-sql/statements/create-function-transact-sql.md)  
  
-   [ALTER FUNCTION &#40;Transact-SQL&#41;](../../t-sql/statements/alter-function-transact-sql.md)  
  
-   [DROP FUNCTION &#40;Transact-SQL&#41;](../../t-sql/statements/drop-function-transact-sql.md)  
  
     Die DROP FUNCTION-Syntax für nativ kompilierte benutzerdefinierte Skalarfunktionen entspricht der Syntax für interpretierte benutzerdefinierte Funktionen.  
  
-   [EXECUTE &#40;Transact-SQL&#41;](../../t-sql/language-elements/execute-transact-sql.md)  
  
 Die gespeicherte Prozedur [sp_recompile &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/sp-recompile-transact-sql.md) kann mit der nativ kompilierten benutzerdefinierten Skalarfunktion verwendet werden. Dies führt dazu, dass die Funktion mithilfe der in den Metadaten vorhandenen Definition erneut kompiliert wird.  
  
 Das folgende Beispiel zeigt eine skalare benutzerdefinierte Funktion aus der [AdventureWorks2016CTP3](https://www.microsoft.com/download/details.aspx?id=49502) -Beispieldatenbank.  
  
```tsql  
CREATE FUNCTION [dbo].[ufnLeadingZeros_native](@Value int)   
RETURNS varchar(8)   
WITH NATIVE_COMPILATION, SCHEMABINDING  
AS   
BEGIN ATOMIC WITH (TRANSACTION ISOLATION LEVEL = SNAPSHOT, LANGUAGE = N'English')  
  
    DECLARE @ReturnValue varchar(8);  
    SET @ReturnValue = CONVERT(varchar(8), @Value);  
       DECLARE @i int = 0, @count int = 8 - LEN(@ReturnValue)  
  
    WHILE @i < @count  
       BEGIN  
            SET @ReturnValue = '0' + @ReturnValue;  
            SET @i += 1  
       END  
  
    RETURN (@ReturnValue);  
  
END  
```  
  
## Aufrufen benutzerdefinierter Funktionen  
 Nativ kompilierte benutzerdefinierte Skalarfunktionen können in Ausdrücken und am gleichen Ort wie integrierte Skalarfunktionen und interpretierte benutzerdefinierte Skalarfunktionen verwendet werden. Nativ kompilierte benutzerdefinierte Skalarfunktionen können auch mit der EXECUTE-Anweisung, in einer Transact-SQL-Anweisung und in einer nativ kompilierten gespeicherten Prozedur verwendet werden.  
  
 Sie können diese benutzerdefinierten Skalarfunktionen in nativ kompilierten gespeicherten Prozeduren, in nativ kompilierten benutzerdefinierten Funktionen und überall dort verwenden, wo integrierte Funktionen zulässig sind. Sie können nativ kompilierte benutzerdefinierte Skalarfunktionen auch in herkömmlichen Transact-SQL-Modulen verwenden.  
  
 Sie können diese benutzerdefinierten Skalarfunktionen im Interop-Modus überall dort verwenden, wo eine interpretierte benutzerdefinierte Skalarfunktion verwendet werden kann. Diese Verwendung unterliegt den containerübergreifenden Transaktionseinschränkungen, wie im Abschnitt**Unterstützte Isolationsstufen für containerübergreifende Transaktionen** des Themas [Transaktionen mit speicheroptimierten Tabellen](../../relational-databases/in-memory-oltp/transactions-with-memory-optimized-tables.md) beschrieben. Weitere Informationen zum Interop-Modus finden Sie unter [Zugreifen auf speicheroptimierte Tabellen mit interpretiertem Transact-SQL](../../relational-databases/in-memory-oltp/accessing-memory-optimized-tables-using-interpreted-transact-sql.md).  
  
 Nativ kompilierte benutzerdefinierte Skalarfunktionen benötigen einen expliziten Ausführungskontext. Weitere Informationen finden Sie unter [EXECUTE AS-Klausel &#40;Transact-SQL&#41;](../../t-sql/statements/execute-as-clause-transact-sql.md). EXECUTE AS CALLER wird nicht unterstützt. Weitere Informationen finden Sie unter [EXECUTE &#40;Transact-SQL&#41;](../../t-sql/language-elements/execute-transact-sql.md).  
  
 Die unterstützte Syntax für Transact-SQL-EXECUTE-Anweisungen für nativ kompilierte benutzerdefinierte Skalarfunktionen finden Sie unter [EXECUTE &#40;Transact-SQL&#41;](../../t-sql/language-elements/execute-transact-sql.md). Die unterstützte Syntax zum Ausführen benutzerdefinierter Funktionen in einer nativ kompilierten gespeicherten Prozedur finden Sie unter [Unterstützte Funktionen für nativ kompilierte T-SQL-Module](../../relational-databases/in-memory-oltp/supported-features-for-natively-compiled-t-sql-modules.md).  
  
## Hinweise und Parameter  
 Die Unterstützung für Tabellen-, Join- und Abfragehinweise in nativ kompilierten benutzerdefinierten Skalarfunktionen entspricht der Unterstützung für diese Hinweise für nativ kompilierte gespeicherte Prozeduren. Wie bei interpretierten benutzerdefinierten Skalarfunktionen wirken sich die in einer Transact-SQL-Abfrage enthaltenen Abfragehinweise, die auf eine nativ kompilierte benutzerdefinierte Skalarfunktion verweisen, nicht auf den Abfrageplan für diese benutzerdefinierte Funktion aus.  
  
 Die für die nativ kompilierten benutzerdefinierten Skalarfunktionen unterstützten Parameter sind alle Parameter, die für nativ kompilierte gespeicherte Prozeduren unterstützt werden. Dies gilt nur, solange die Parameter für benutzerdefinierte Skalarfunktionen zulässig sind. Ein Beispiel für einen unterstützten Parameter ist der Tabellenwertparameter.  
  
## Schemagebunden  
 Folgendes gilt für nativ kompilierte benutzerdefinierte Skalarfunktionen.  
  
-   Müssen schemagebunden sein, indem das WITH SCHEMABINDING-Argument in CREATE FUNCTION und ALTER FUNCTION verwendet wird.  
  
-   Können nicht gelöscht oder geändert werden, wenn von einer schemagebundenen gespeicherten Prozedur oder einer benutzerdefinierten Funktion auf sie verwiesen wird.  
  
## SHOWPLAN_XML  
 Nativ kompilierte benutzerdefinierte Skalarfunktionen unterstützen SHOWPLAN_XML. Es entspricht dem allgemeinen SHOWPLAN_XML-Schema, wie bei nativ kompilierten gespeicherten Prozeduren. Das Basiselement für die benutzerdefinierten Funktionen ist `<UDF>`.  
  
 STATISTICS XML wird für nativ kompilierte benutzerdefinierte Skalarfunktionen nicht unterstützt. Beim Ausführen einer Abfrage mit Verweis auf die benutzerdefinierte Funktion mit aktivierter STATISTICS XML-Anweisung wird der XML-Inhalt ohne den Teil für die benutzerdefinierte Funktion zurückgegeben.  
  
## Berechtigungen  
 Wie bei nativ kompilierten gespeicherten Prozeduren werden beim Erstellen der Funktion die Berechtigungen für die Objekte überprüft, auf die von einer nativ kompilierten benutzerdefinierten Skalarfunktion verwiesen wird. CREATE FUNCTION schlägt fehl, wenn der Benutzer, dessen Identität angenommen wurde, nicht über die richtigen Berechtigungen verfügt. Wenn das Ändern der Berechtigungen dazu führt, dass der Benutzer, dessen Identität angenommen wurde, nicht mehr über die richtigen Berechtigungen verfügt, schlagen die nachfolgenden Ausführungen der benutzerdefinierten Funktion fehl.  
  
 Wenn Sie eine nativ kompilierte benutzerdefinierte Skalarfunktion in einer nativ kompilierten gespeicherten Prozedur verwenden, werden die Berechtigungen für die Ausführung der benutzerdefinierten Funktion beim Erstellen der äußeren Prozedur überprüft. Falls der Benutzer, dessen Identität von der äußeren Prozedur angenommen wurde, über keine EXEC-Berechtigungen für die benutzerdefinierte Funktion verfügt, schlägt die Erstellung der gespeicherten Prozedur fehl. Falls der Benutzer nach Ändern der Berechtigungen nicht mehr über EXEC-Berechtigungen verfügt, schlägt die Ausführung der äußeren Prozedur fehl.  
  
## Siehe auch  
 [Integrierte Funktionen &#40;Transact-SQL&#41;](../Topic/Built-in%20Functions%20\(Transact-SQL\).md)   
 [Speichern eines Ausführungsplans im XML-Format](../../relational-databases/performance/save-an-execution-plan-in-xml-format.md)  
  
  