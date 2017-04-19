---
title: "Transformations-Editor f&#252;r Zusammenf&#252;hrungsjoin | Microsoft Docs"
ms.custom: ""
ms.date: "03/01/2017"
ms.prod: "sql-server-2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "integration-services"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "sql13.dts.designer.mergejointransformation.f1"
helpviewer_keywords: 
  - "Transformations-Editor für Zusammenführungsjoin"
ms.assetid: ac06f419-30b3-42aa-8b34-42000bec4285
caps.latest.revision: 31
author: "douglaslMS"
ms.author: "douglasl"
manager: "jhubbard"
caps.handback.revision: 31
---
# Transformations-Editor f&#252;r Zusammenf&#252;hrungsjoin
  Im Dialogfeld **Transformations-Editor für Zusammenführungsjoin** geben Sie den Jointyp, die Joinspalten und die Ausgabespalten für zwei Eingaben an, die durch einen Join zusammengeführt werden.  
  
> [!IMPORTANT]  
>  Die Transformation für Zusammenführungsjoin erfordert als Eingabe sortierte Daten. Weitere Informationen zu dieser wichtigen Anforderung finden Sie unter [Sortieren von Daten für die Transformationen für Zusammenführen und Zusammenführungsjoin](../../../integration-services/data-flow/transformations/sort-data-for-the-merge-and-merge-join-transformations.md).  
  
 Weitere Informationen zur Transformation für Zusammenführungsjoins finden Sie unter [Merge Join Transformation](../../../integration-services/data-flow/transformations/merge-join-transformation.md).  
  
## enthalten  
 **Jointyp**  
 Geben Sie an, ob Sie einen inneren Join, einen linken äußeren Join oder einen vollständigen Join verwenden möchten.  
  
 **Eingaben vertauschen**  
 Schalten Sie die Reihenfolge der Eingaben mithilfe der Schaltfläche **Eingaben vertauschen** um. Diese Option kann sich bei linkem äußeren Join als nützlich erweisen.  
  
 **Eingabe**  
 Wählen Sie alle Spalten, die zur zusammengeführten Ausgabe gehören sollen, in der Liste der verfügbaren Eingaben aus.  
  
 Eingaben werden in zwei separaten Tabellen angezeigt. Wählen Sie die Spalten aus, die in die Eingabe eingeschlossen werden sollen. Verschieben Sie die Spalten, um einen Join zwischen den Tabellen zu erstellen. Um einen Join zu löschen, wählen Sie diesen aus und drücken dann ENTF.  
  
 **Eingabespalte**  
 Wählen Sie eine Spalte, die in die zusammengeführte Ausgabe eingeschlossen werden soll, in der Liste der für die ausgewählte Eingabe verfügbaren Spalten aus.  
  
 **Ausgabealias**  
 Geben Sie einen Alias für jede Spalte ein. Standardmäßig wird der Name der Eingabespalte verwendet. Sie können jedoch auch einen beschreibenden Namen angeben, sofern dieser eindeutig ist.  
  
## Siehe auch  
 [Fehler- und Meldungsreferenz von Integration Services](../../../integration-services/integration-services-error-and-message-reference.md)   
 [Sortieren von Daten für die Transformationen für Zusammenführen und Zusammenführungsjoin](../../../integration-services/data-flow/transformations/sort-data-for-the-merge-and-merge-join-transformations.md)   
 [Erweitern eines Datasets mithilfe der Transformation für Zusammenführungsjoins](../../../integration-services/data-flow/transformations/extend-a-dataset-by-using-the-merge-join-transformation.md)   
 [Transformation für Zusammenführen](../../../integration-services/data-flow/transformations/merge-transformation.md)   
 [Transformation für UNION ALL](../../../integration-services/data-flow/transformations/union-all-transformation.md)  
  
  