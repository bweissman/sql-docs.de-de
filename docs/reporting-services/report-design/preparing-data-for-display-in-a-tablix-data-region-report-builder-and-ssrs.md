---
title: "Vorbereiten von Daten f&#252;r die Anzeige in einem Tablix-Datenbereich (Berichts-Generator und SSRS) | Microsoft Docs"
ms.custom: ""
ms.date: "03/14/2017"
ms.prod: "sql-server-2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "reporting-services-sharepoint"
  - "reporting-services-native"
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: fbb00dc6-7887-480c-b771-cab6fecb8dcc
caps.latest.revision: 5
author: "maggiesMSFT"
ms.author: "maggies"
manager: "erikre"
caps.handback.revision: 5
---
# Vorbereiten von Daten f&#252;r die Anzeige in einem Tablix-Datenbereich (Berichts-Generator und SSRS)
  Ein Tablix-Datenbereich zeigt Daten aus einem Dataset an. Sie können alle für das Dataset abgerufenen Daten anzeigen oder Filter erstellen, sodass nur eine Teilmenge der Daten angezeigt wird. Sie können auch bedingte Ausdrücke hinzufügen, um NULL-Werte aufzufüllen, oder die Abfrage für ein Dataset so ändern, dass Spalten mit Definitionen der Sortierreihenfolge für eine vorhandene Spalte enthalten sind.  
  
> [!NOTE]  
>  [!INCLUDE[ssRBRDDup](../../includes/ssrbrddup-md.md)]  
  
## Verwenden von NULL- und leeren Werten in Feldwerten  
 Daten für die Feldauflistung in einem Dataset enthalten alle zur Laufzeit aus der Datenquelle abgerufenen Werte, einschließlich von NULL- und leeren Werten. Normalerweise können NULL-Werte und leere Werte nicht unterschieden werden. Dies stellt in den meisten Fällen das gewünschte Verhalten dar. Beispiel: Numerische Aggregatfunktionen wie [Sum](../../reporting-services/report-design/sum-function-report-builder-and-ssrs.md) und [Avg](../../reporting-services/report-design/avg-function-report-builder-and-ssrs.md) ignorieren NULL-Werte. Weitere Informationen finden Sie unter [Aggregatfunktionsreferenz &#40;Berichts-Generator und SSRS&#41;](../../reporting-services/report-design/aggregate-functions-reference-report-builder-and-ssrs.md).  
  
 Wenn Sie NULL-Werte auf andere Weise behandeln möchten, können Sie bedingte Ausdrücke oder benutzerdefinierten Code verwenden, um den NULL-Wert durch einen benutzerdefinierten Wert zu ersetzen. Durch den folgenden Ausdruck wird beispielsweise der Text `Null` für jeden NULL-Wert im Feld `[Size]`eingesetzt.  
  
```  
=IIF(Fields!Size.Value IS NOTHING,"Null",Fields!Size.Value)  
```  
  
 Weitere Informationen über das Ausschließen von NULL-Werten in den Daten vor dem Abruf der Daten aus einer [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] -Datenquelle mithilfe von [!INCLUDE[tsql](../../includes/tsql-md.md)] -Abfragen finden Sie unter "NULL-Werte" und "NULL-Werte und Joins" in der [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] -Dokumentation in der [SQL Server-Onlinedokumentation](http://go.microsoft.com/fwlink/?linkid=120955).  
  
## Behandeln von NULL-Feldnamen  
 Die Überprüfung auf NULL-Werte in einem Ausdruck ist problemlos möglich, sofern das Feld selbst im Abfrageresultset vorhanden ist. Sie können in benutzerdefinierten Code überprüfen, ob das Feld selbst in den Auflistungsfeldern vorhanden ist, die zur Laufzeit von der Datenquelle zurückgegeben werden. Weitere Informationen finden Sie unter [Verweise auf Datasetfeld-Sammlungen &#40;Berichts-Generator und SSRS&#41;](../../reporting-services/report-design/dataset-fields-collection-references-report-builder-and-ssrs.md).  
  
## Hinzufügen einer Sortierenreihenfolge-Spalte  
 Standardmäßig können Sie Werte in einem Datasetfeld alphabetisch sortieren. Um in einer anderen Reihenfolge zu sortieren, können Sie dem Dataset eine neue Spalte hinzufügen, die die für den Datenbereich gewünschte Sortierreihenfolge definiert. Wenn Sie beispielsweise nach dem Feld `[Color]` mit weißen und schwarzen Elementen am Anfang sortieren möchten, können Sie die Spalte `[ColorSortOrder]`wie in der folgenden Abfrage hinzufügen:  
  
```  
SELECT ProductID, p.Name, Color,  
   CASE  
      WHEN p.Color = 'White' THEN 1  
      WHEN p.Color = 'Black' THEN 2  
      WHEN p.Color = 'Blue' THEN 3  
      WHEN p.Color = 'Yellow' THEN 4  
      ELSE 5  
   END As ColorSortOrder  
FROM Production.Product p  
```  
  
 Um einen Tabellendatenbereich nach dieser Sortierreihenfolge zu sortieren, legen Sie den Sortierausdruck für die Detailgruppe auf `=Fields!ColorSortOrder.Value`fest. Weitere Informationen finden Sie unter [Sortieren von Daten in einem Datenbereich &#40;Berichts-Generator und SSRS&#41;](../../reporting-services/report-design/sort-data-in-a-data-region-report-builder-and-ssrs.md).  
  
## Siehe auch  
 [Datasetfeld-Sammlung &#40;Berichts-Generator und SSRS&#41;](../../reporting-services/report-data/dataset-fields-collection-report-builder-and-ssrs.md)   
 [Ausdrücke &#40;Berichts-Generator und SSRS&#41;](../../reporting-services/report-design/expressions-report-builder-and-ssrs.md)   
 [Filtern, Gruppieren und Sortieren von Daten &#40;Berichts-Generator und SSRS&#41;](../../reporting-services/report-design/filter-group-and-sort-data-report-builder-and-ssrs.md)  
  
  