---
title: Verwenden eine SQL-Anweisung zum Ändern von Daten | Microsoft-Dokumentation
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
ms.assetid: 4704199b-c0ae-4c77-8a2e-6963715b4ffb
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: 89fd14cf4245a3c44dad41b4af5b3b14e779e82b
ms.sourcegitcommit: 61381ef939415fe019285def9450d7583df1fed0
ms.translationtype: MTE75
ms.contentlocale: de-DE
ms.lasthandoff: 10/01/2018
ms.locfileid: "47838289"
---
# <a name="using-an-sql-statement-to-modify-data"></a>Ändern von Daten mit SQL-Anweisungen

[!INCLUDE[Driver_JDBC_Download](../../includes/driver_jdbc_download.md)]

Mit der [executeUpdate](../../connect/jdbc/reference/executeupdate-method-sqlserverstatement.md)-Methode der [SQLServerStatement](../../connect/jdbc/reference/sqlserverstatement-class.md)-Klasse können Sie die in einer [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]-Datenbank enthaltenen Daten über eine SQL-Anweisung ändern. Die executeUpdate-Methode übergibt die SQL-Anweisung zur Verarbeitung an die Datenbank und gibt anschließend einen Wert zurück, der die Anzahl der betroffenen Zeilen angibt.

Sie müssen dazu zuerst mit der [createStatement](../../connect/jdbc/reference/createstatement-method-sqlserverconnection.md)-Methode der [SQLServerConnection](../../connect/jdbc/reference/sqlserverconnection-class.md)-Klasse ein SQLServerStatement-Objekt erstellen.

Im folgenden Beispiel wird eine offene Verbindung zur [!INCLUDE[ssSampleDBnormal](../../includes/sssampledbnormal_md.md)]-Beispieldatenbank an die Funktion übergeben, eine SQL-Anweisung wird erstellt, die neue Daten wird zu der Tabelle hinzufügt, die Anweisung wird anschließend ausgeführt, und der Rückgabewert wird angezeigt.

[!code[JDBC#UsingSQLToModifyData1](../../connect/jdbc/codesnippet/Java/using-an-sql-statement-t_1_1.java)]

> [!NOTE]  
> Wenn Sie eine SQL-Anweisung verwenden müssen, um die Daten in einer [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]-Datenbank zu ändern, müssen Sie die [executeUpdate](../../connect/jdbc/reference/executeupdate-method-sqlserverpreparedstatement.md)-Methode der [SQLServerPreparedStatement](../../connect/jdbc/reference/sqlserverpreparedstatement-class.md)-Klasse verwenden.
>
> Wenn die Spalte, in die Daten eingefügt werden sollen, Sonderzeichen wie Leerzeichen enthält, müssen Sie die einzufügenden Werte angeben, auch wenn es sich um die Standardwerte handelt. Andernfalls schlägt die Einfügeoperation fehl.
>
> Wenn der JDBC-Treiber alle Updatezählungen zurückgeben soll, einschließlich der Updatezählungen, die von eventuell ausgelösten Triggern zurückgegeben werden, müssen Sie die lastUpdateCount-Verbindungseigenschaft auf "false" setzen. Weitere Informationen zur LastUpdateCount-Eigenschaft finden Sie unter [Festlegen der Verbindungseigenschaften](../../connect/jdbc/setting-the-connection-properties.md).

## <a name="see-also"></a>Weitere Informationen finden Sie unter

[Verwenden von Anweisungen mit SQL](../../connect/jdbc/using-statements-with-sql.md)
