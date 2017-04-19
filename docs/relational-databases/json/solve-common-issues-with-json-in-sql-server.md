---
title: "H&#228;ufig gestellte Fragen zu JSON in SQL Server | Microsoft Docs"
ms.custom: 
  - "SQL2016_New_Updated"
ms.date: "07/07/2016"
ms.prod: "sql-server-2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "dbe-json"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "JSON, Häufig gestellte Fragen"
ms.assetid: feae120b-55cc-4601-a811-278ef1c551f9
caps.latest.revision: 9
author: "douglaslMS"
ms.author: "douglasl"
manager: "jhubbard"
caps.handback.revision: 9
---
# H&#228;ufig gestellte Fragen zu JSON in SQL Server
[!INCLUDE[tsql-appliesto-ss2016-asdb-xxxx-xxx_md](../../includes/tsql-appliesto-ss2016-asdb-xxxx-xxx-md.md)]

 Hier finden Sie Antworten auf einige häufig gestellte Fragen zu der integrierten JSON-Unterstützung in SQL Server.  
 
## FOR JSON- und JSON-Ausgabe

### FOR JSON PATH oder FOR JSON AUTO?  
 **Frage:** Ich muss das JSON-Textergebnis aus einer einfachen SQL-Abfrage auf einer einzelnen Tabelle erstellen. FOR JSON PATH und FOR JSON AUTO erzeugen dieselbe Ausgabe. Welche dieser beiden Optionen sollte ich verwenden?  
  
 **Antwort:** Verwenden Sie FOR JSON PATH. Obwohl kein Unterschied in der JSON-Ausgabe besteht, besitzt AUTO-Modus zusätzliche Logik, die überprüft, ob Spalten geschachtelt werden sollen. Betrachten Sie PATH als Standardoption.  

### Erstellen einer geschachtelten JSON-Struktur  
 **Frage:** Ich muss mit mehreren Arrays auf der gleichen Ebene komplexe JSON-Objekte erstellen. FOR JSON PATH kann geschachtelter Objekte mithilfe von Pfaden erstellen.FOR JSON AUTO erstellt eine zusätzliche Schachtelungsebene für jede Tabelle. Mit keiner dieser beiden Optionen kann ich die gewünschte Ausgabe generieren. Wie kann ich ein benutzerdefiniertes JSON-Format erstellen, das die vorhandenen Optionen nicht direkt unterstützen?  
  
 **Antwort:** Erstellen Sie eine beliebige Datenstruktur, indem Sie FOR JSON-Abfragen als Spaltenausdrücke hinzufügen, die JSON-Text zurückgeben. Sie können JSON auch manuell mithilfe der Funktion JSON_QUERY erstellen, wie im folgenden Beispiel gezeigt.  
  
```tsql  
SELECT col1, col2, col3,  
             (SELECT col11, col12, col13 FROM t11 WHERE t11.FK = t1.PK FOR JSON PATH) as t11,  
             (SELECT col21, col22, col23 FROM t21 WHERE t21.FK = t1.PK FOR JSON PATH) as t21,  
             (SELECT col31, col32, col33 FROM t31 WHERE t31.FK = t1.PK FOR JSON PATH) as t31,  
             JSON_QUERY('{"'+col4'":"'+col5+'"}' as t41  
FROM t1  
FOR JSON PATH  
```  
  
Jedes Ergebnis einer FOR JSON-Abfrage oder die Funktion JSON_QUERY in den Spaltenausdrücken wird als separates geschachteltes JSON-Unterobjekt formatiert und im Hauptergebnis aufgenommen.  

### Verhindern von doppelt geschütztem JSON in der FOR JSON-Ausgabe  
 **Frage:** Ich habe einen JSON-Text, der in einer Tabellenspalte gespeichert ist. Ich möchte ihn in der Ausgabe von FOR JSON einschließen. FOR JSON schützt alle Zeichen in JSON, also erhalte ich eine JSON-Zeichenfolge anstelle eines geschachtelten-Objekts, wie im folgenden Beispiel gezeigt.  
  
```tsql  
SELECT 'Text' as myText, '{"day":23}' as myJson  
FOR JSON PATH  
```  
  
 Diese Abfrage generiert die folgende Ausgabe:  
  
```json  
[{"myText":"Text","myJson":"{\"day\":23}"}]  
```  
  
 Wie kann ich verhindern, dass dieses Verhalten auftritt? Ich möchte, dass `{"day":23}` als JSON-Objekt und nicht als geschützter Text zurückgegeben wird.  
  
 **Antwort:** Ein JSON-Objekt, das in einer Textspalte oder als Literal gespeichert wird, wird wie jeder beliebige Text behandelt. Es ist in doppelte Anführungszeichen eingeschlossen und geschützt. Wenn ein ungeschütztes JSON-Objekt zurückgegeben werden soll, müssen Sie diese Spalte als Argument an die Funktion JSON_QUERY übergeben, wie im folgenden Beispiel gezeigt.  
  
```tsql  
SELECT col1, col2, col3, JSON_QUERY(jsoncol1) AS jsoncol1  
FROM tab1  
FOR JSON PATH  
```  
  
 JSON_QUERY ohne den optionalen zweiten Parameter gibt nur das erste Argument als Ergebnis zurück. Da JSON_QUERY valides JSON zurückgibt, weiß FOR JSON, dass dieses Ergebnis nicht geschützt werden muss.

### Ein mit der WITHOUT_ARRAY_WRAPPER-Klausel generiertes JSON wird in der FOR JSON-Ausgabe geschützt  
 **Frage:** Ich versuche, einen Spaltenausdruck mit FOR JSON und der Option WITHOUT_ARRAY_WRAPPER zu formatieren.  
  
```tsql  
SELECT 'Text' as myText,  
       (SELECT 12 day, 8 mon FOR JSON PATH, WITHOUT_ARRAY_WRAPPER) as myJson  
FOR JSON PATH   
```  
  
 Es scheint, dass der von der FOR JSON-Abfrage zurückgegebene Text als Klartext geschützt wird. Dies geschieht nur, wenn WITHOUT_ARRAY_WRAPPER angegeben wird. Warum wird es nicht als ein JSON-Objekt behandelt und im Ergebnis ungeschützt eingefügt?  
  
 **Antwort:** Wenn Sie die Option WITHOUT_ARRAY_WRAPPER angeben, ist der generierte JSON-Text nicht unbedingt gültig. Daher geht die äußere FOR JSON-Anweisung davon aus, dass es sich hierbei um Klartext handelt und schützt die Zeichenfolge. Wenn Sie sicher sind, dass die JSON-Ausgabe gültig ist, binden Sie diese mithilfe der JSON_QUERY-Funktion ein, um sie auf ordnungsgemäß formatierte JSON heraufzustufen, wie im folgenden Beispiel gezeigt.  
  
```tsql  
SELECT 'Text' as myText,  
      JSON_QUERY((SELECT 12 day, 8 mon FOR JSON PATH, WITHOUT_ARRAY_WRAPPER)) as myJson  
FOR JSON PATH    
```  

## OPENJSON und JSON-Eingabe

### Zurückgeben eines geschachtelten untergeordneten JSON-Objekts aus dem JSON-Text mit OPENJSON  
 **Frage:** Ich kann kein Array komplexer JSON-Objekte öffnen, das sowohl skalare Werte als auch Objekte und Arrays enthält, die OPENJSON mit einem expliziten Schema verwenden. Wenn ich auf einen Schlüssel in der WITH-Klausel verweise, werden nur skalare Werte zurückgegeben. Objekte und Arrays werden als NULL-Werte zurückgegeben. Wie kann ich Objekte oder Arrays in JSON-Objekten extrahieren?  
  
 **Antwort:** Wenn Sie ein Objekt oder Array als eine Spalte zurückgeben möchten, verwenden Sie die Option AS JSON in der Spaltendefinition, wie im folgenden Beispiel gezeigt.  
  
```tsql  
SELECT scalar1, scalar2, obj1, obj2, arr1  
FROM OPENJSON(@json)  
             WITH ( scalar1 int,  
                          scalar2 datetime2,  
                          obj1 NVARCHAR(MAX) AS JSON,  
                          obj2 NVARCHAR(MAX) AS JSON,  
                          arr1 NVARCHAR(MAX) AS JSON)  
```  

### Verwenden von OPENJSON anstelle von JSON_VALUE zur Rückgabe lange Textwerte  
 **Frage:** Ich habe einen Beschreibungsschlüssel im JSON-Text, der langen Text enthält. `JSON_VALUE(@json, '$.description')` gibt NULL zurück, statt eines Werts.  
  
 **Antwort:** JSON_VALUE ist dafür konzipiert, kleine skalare Werte zurückzugeben. Im Allgemeinen gibt die Funktion NULL zurück, statt eines Überlauffehlers. Wenn längere Werte zurückgegeben werden sollen, verwenden Sie OPENJSON, das NVARCHAR(MAX)-Werte unterstützt, wie im folgenden Beispiel gezeigt.  
  
```tsql  
SELECT myText FROM OPENJSON(@json) WITH (myText NVARCHAR(MAX) '$.description')  
```  

### Verwenden von OPENJSON anstelle von JSON_VALUE zur Behandlung doppelter Schlüssel  
 **Frage:** Ich habe doppelte Schlüssel im JSON-Text. JSON_VALUE gibt nur den ersten Schlüssel zurück, der im Pfad gefunden wird. Wie kann ich alle Schlüssel zurückgeben, die den gleichen Namen haben?  
  
 **Antwort:** Die integrierten Skalarfunktionen von JSON geben nur das erste Vorkommen des Objekts, auf das verwiesen wird, zurück. Wenn Sie mehr als einen Schlüssel benötigen, verwenden Sie die OPENJSON-Tabellenwertfunktion, wie im folgenden Beispiel gezeigt.  
  
```tsql  
SELECT value FROM OPENJSON(@json, '$.info.settings')  
WHERE [key] = 'color'  
```  

### OPENJSON erfordert Kompatibilitätsgrad 130  
 **Frage:** Ich versuche, OPENJSON in SQL Server 2016 auszuführen, und erhalte die folgende Fehlermeldung.  
  
 `Msg 208, Level 16, State 1 ‘Invalid object name OPENJSON’`  
  
 **Antwort:** Die OPENJSON-Funktion steht nur für Kompatibilitätsgrad 130 zur Verfügung. Wenn der Kompatibilitätsgrad Ihrer DB kleiner als 130 ist, wird OPENJSON ausgeblendet. Andere JSON-Funktionen sind für alle Kompatibilitätsgrade verfügbar.  
 
## Andere Fragen

### Referenzschlüssel, die nicht-alphanumerische Zeichen in JSON-Text enthalten  
 **Frage:** Schlüssel in meinem JSON-Text enthalten nicht-alphanumerische Zeichen. Wie kann ich diese Eigenschaften verweisen?  
  
 **Antwort:** In JSON-Pfaden müssen Sie diese in Anführungszeichen einschließen. Beispiel: `JSON_VALUE(@json, '$."$info"."First Name".value')`.
 