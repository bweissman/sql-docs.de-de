---
title: "&#196;ndern von XML-Indizes | Microsoft Docs"
ms.custom: ""
ms.date: "03/14/2017"
ms.prod: "sql-server-2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "dbe-xml"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "XML-Indizes [SQL Server], ändern"
  - "Ändern von Indizes"
ms.assetid: 24d50fe1-c6ec-49e6-91a3-9791851ba53d
caps.latest.revision: 12
author: "BYHAM"
ms.author: "rickbyh"
manager: "jhubbard"
caps.handback.revision: 12
---
# &#196;ndern von XML-Indizes
  Die [ALTER INDEX &#40;Transact-SQL&#41;](../../t-sql/statements/alter-index-transact-sql.md)[!INCLUDE[tsql](../../includes/tsql-md.md)]-DDL-Anweisung kann zum Ändern vorhandener XML-Indizes und Nicht-XML-Indizes verwendet werden. Nicht alle ALTER INDEX-Optionen sind jedoch für XML-Indizes verfügbar. Die folgenden Optionen sind beim Ändern von XML-Indizes nicht zulässig:  
  
-   Die REBUILD- und SET-Option IGNORE_DUP_KEY ist für XML-Indizes nicht zulässig. Die REBUILD-Option ONLINE muss für sekundäre XML-Indizes auf OFF festgelegt werden. Die Option DROP_EXISTING ist in der ALTER INDEX-Anweisung nicht zulässig.  
  
-   Die Änderungen der primary key-Einschränkung in der user-Tabelle werden nicht automatisch an XML-Indizes weitergegeben. Der Benutzer muss die XML-Indizes zuerst löschen und dann neu erstellen.  
  
-   Wenn ALTER INDEX ALL angegeben wird, gilt dies für Nicht-XML- und XML-Indizes. Möglicherweise werden Indizierungsoptionen angegeben, die nicht für beide Indextypen zulässig sind. In diesem Fall schlägt die gesamte Anweisung fehl.  
  
## Beispiel: Ändern eines XML-Index  
 Im folgenden Beispiel wird ein XML-Index erstellt und dann durch Festlegen der Option `ALLOW_ROW_LOCKS` auf `OFF` geändert. Wenn `ALLOW_ROW_LOCKS` auf `OFF` festgelegt wurde, sind die Zeilen gesperrt, und der Zugriff auf die angegebenen Indizes erfolgt über die Sperren auf Seiten- und Tabellenebene.  
  
```  
CREATE TABLE T (Col1 INT PRIMARY KEY, XmlCol XML)  
GO  
-- Create primary XML index.   
CREATE PRIMARY XML INDEX PIdx_T_XmlCol   
ON T(XmlCol)  
GO  
-- Note the type 3 is index on XML type.  
SELECT *  
FROM sys.xml_indexes  
WHERE object_id = object_id('T')  
AND name='PIdx_T_XmlCol'  
  
-- Modify and set an index option.  
ALTER INDEX PIdx_T_XmlCol on T   
SET (ALLOW_ROW_LOCKS = OFF)  
```  
  
## Beispiel: Deaktivieren und Aktivieren eines XML-Index  
 Standardmäßig ist ein XML-Index aktiviert. Wenn ein XML-Index deaktiviert ist, verwenden die Abfragen, die für eine XML-Spalte ausgeführt werden, den XML-Index nicht. Verwenden Sie `ALTER INDEX` mit der Option `REBUILD`, um einen XML-Index zu aktivieren.  
  
```  
CREATE TABLE T (Col1 INT PRIMARY KEY, XmlCol XML)  
GO  
CREATE PRIMARY XML INDEX PIdx_T_XmlCol ON T(XmlCol)  
GO  
ALTER INDEX PIdx_T_XmlCol on T DISABLE  
Go  
-- Verify index is disabled.  
SELECT *  
FROM sys.xml_indexes  
WHERE object_id = object_id('T')  
AND name='PIdx_T_XmlCol'  
-- Rebuild the index.  
ALTER INDEX PIdx_T_XmlCol on T REBUILD  
Go  
```  
  
## Siehe auch  
 [XML-Indizes &#40;SQL Server&#41;](../../relational-databases/xml/xml-indexes-sql-server.md)  
  
  