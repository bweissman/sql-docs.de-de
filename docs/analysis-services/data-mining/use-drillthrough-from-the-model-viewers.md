---
title: "Verwenden von Drillthrough mit den Modell-Viewern | Microsoft Docs"
ms.custom: ""
ms.date: "03/01/2017"
ms.prod: "sql-server-2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "analysis-services"
  - "analysis-services/data-mining"
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: e5e065ad-c688-4c2c-8c82-7f3038e04915
caps.latest.revision: 6
author: "Minewiskan"
ms.author: "owend"
manager: "jhubbard"
caps.handback.revision: 6
---
# Verwenden von Drillthrough mit den Modell-Viewern
  Abhängig vom Modelltyp können Sie Drillthrough von den Durchsuchen-Viewern auf der Registerkarte **Miningmodell-Viewer** des Data Mining-Designers verwenden, um die im Miningmodell verwendeten Fälle zu prüfen oder zusätzliche Spalten in der Miningstruktur anzuzeigen. Obwohl viele Modelltypen kein Drillthrough unterstützen, da die Muster im Modell nicht direkt mit bestimmten Fällen verknüpft werden können, unterstützen die folgenden Modelltypen Drillthrough.  
  
 Drillthrough muss für das Modell aktiviert worden sein, und Sie benötigen die entsprechenden Berechtigungen. Die Drillthroughoption könnte auch deaktiviert werden, wenn sich das Modell in einem nicht verarbeiteten Status befindet, und zwar unabhängig von, ob das Modell zuvor verarbeitet wurde und Inhalte besitzt. Um Modellfalldaten mithilfe von Drillthrough abzurufen, muss der Cache der Struktur und des Modells jeweils aktuell sein.  
  
### Verwenden von Drillthrough im Microsoft Struktur-Viewer  
  
1.  Wählen Sie im Data Mining-Designer ein Entscheidungsstrukturmodell und anschließend die Option **Modell durchsuchen** aus, um das Modell im **Microsoft Struktur-Viewer**zu öffnen. Klicken Sie in SQL Server Management Studio mit der rechten Maustaste auf das Modell, und wählen Sie **Durchsuchen** aus.  
  
2.  Klicken Sie mit der rechten Maustaste auf einen beliebigen Knoten im Strukturdiagramm, und wählen Sie **Drillthrough ausführen** aus.  
  
3.  Wählen Sie eine der folgenden Optionen aus: **Nur Modellspalten** oder **Modell- und Strukturspalten**. Wenn Sie nicht über Berechtigungen verfügen, ist unter Umständen keine Option verfügbar.  
  
4.  Das Dialogfeld **Drillthrough ausführen** wird geöffnet, in dem die Falldaten und/oder Strukturdaten angezeigt werden. Die Titelleiste des Dialogfelds enthält auch eine Beschreibung des Knotens, von dem aus die Drillthroughabfrage ausgeführt wurde.  
  
5.  Klicken Sie mit der rechten Maustaste auf eine beliebige Stelle in den Ergebnissen, und wählen Sie **Alles kopieren** aus, um die Ergebnisse in der Zwischenablage zu speichern.  
  
### Verwenden von Drillthrough im Microsoft Cluster-Viewer  
  
1.  Wählen Sie im Data Mining-Designer ein Clusteringmodell aus, und wählen Sie **Modell durchsuchen** aus, um das Modell im **Microsoft Cluster-Viewer**zu öffnen. Klicken Sie in SQL Server Management Studio mit der rechten Maustaste auf das Modell, und wählen Sie **Durchsuchen** aus.  
  
2.  Klicken Sie auf der Registerkarte **Cluster** mit der rechten Maustaste auf einen beliebigen Knoten.  
  
3.  Wählen Sie **Drillthrough ausführen**und anschließend eine der folgenden Optionen aus: **Nur Modellspalten** oder **Modell- und Strukturspalten**. Wenn Sie nicht über Berechtigungen verfügen, ist unter Umständen keine Option verfügbar.  
  
4.  Das Dialogfeld **Drillthrough ausführen** wird geöffnet, in dem die Falldaten und/oder Strukturdaten angezeigt werden. Die Titelleiste des Dialogfelds enthält auch eine Beschreibung, die den Cluster für die Fälle kennzeichnet.  
  
5.  Klicken Sie mit der rechten Maustaste auf eine beliebige Stelle in den Ergebnissen, und wählen Sie **Alles kopieren** aus, um die Ergebnisse in der Zwischenablage zu speichern.  
  
### Verwenden von Drillthrough im Microsoft Association Rules-Viewer  
  
1.  Wählen Sie im Data Mining-Designer ein Zuordnungsmodell aus, und wählen Sie **Modell durchsuchen** aus, um das Modell im **Microsoft Association Rules-Viewer**zu öffnen. Klicken Sie in SQL Server Management Studio mit der rechten Maustaste auf das Modell, und wählen Sie **Durchsuchen** aus.  
  
2.  Klicken Sie auf der Registerkarte **Regeln** mit der rechten Maustaste auf eine beliebige Zeile, die eine Regel darstellt. Klicken Sie auf der Registerkarte **Itemsets** auf eine beliebige Zeile, die ein Itemset enthält.  
  
3.  Wählen Sie **Drillthrough ausführen**und anschließend eine der folgenden Optionen aus: **Nur Modellspalten** oder **Modell- und Strukturspalten**. Wenn Sie nicht über Berechtigungen verfügen, ist unter Umständen keine Option verfügbar.  
  
4.  Das Dialogfeld **Drillthrough ausführen** wird geöffnet, in dem die Falldaten und/oder Strukturdaten angezeigt werden. Die Titelleiste des Dialogfelds enthält auch eine Beschreibung zur Identifizierung des Regelnamens.  
  
5.  Klicken Sie mit der rechten Maustaste auf eine beliebige Stelle in den Ergebnissen, und wählen Sie **Alles kopieren** aus, um die vollständigen Fallergebnisse in der Zwischenablage zu speichern. Sie können auch **Kopieren** auswählen, um nur den ausgewählten Fall zu kopieren. Wenn das Modell eine geschachtelte Tabellenspalte enthält, wird nur der Name der geschachtelten Tabellenspalte eingefügt. Wenn Sie die Datenwerte in der geschachtelten Tabellenspalte für die einzelnen Fälle abrufen möchten, müssen Sie eine Abfrage für den Modellinhalt erstellen.  
  
### Verwenden von Drillthrough im Microsoft Sequence Cluster-Viewer  
  
1.  Wählen Sie im Data Mining-Designer ein Clusteringmodell aus, und wählen Sie **Modell durchsuchen** aus, um das Modell im **Microsoft Cluster-Viewer**zu öffnen. Klicken Sie in SQL Server Management Studio mit der rechten Maustaste auf das Modell, und wählen Sie **Durchsuchen** aus.  
  
2.  Klicken Sie auf der Registerkarte **Clusterdiagramm** mit der rechten Maustaste auf einen beliebigen Knoten, der einen Cluster darstellt. Klicken Sie auf der Registerkarte **Clusterprofile** an einer beliebigen Stelle in einem Clusterprofil oder in dem Cluster, das die gesamte Modellauffüllung darstellt.  
  
3.  Wählen Sie **Drillthrough ausführen**und anschließend eine der folgenden Optionen aus: **Nur Modellspalten** oder **Modell- und Strukturspalten**. Wenn Sie nicht über Berechtigungen verfügen, ist unter Umständen keine Option verfügbar.  
  
4.  Das Dialogfeld **Drillthrough ausführen** wird geöffnet, in dem die Falldaten und/oder Strukturdaten angezeigt werden. Die Titelleiste des Dialogfelds enthält auch eine Beschreibung, die den Cluster für die Fälle kennzeichnet.  
  
5.  Klicken Sie mit der rechten Maustaste auf eine beliebige Stelle in den Ergebnissen, und wählen Sie **Alles kopieren** aus, um die Ergebnisse in der Zwischenablage zu speichern. Wenn das Modell eine geschachtelte Tabellenspalte enthält, wird nur der Name der geschachtelten Tabellenspalte eingefügt. Wenn Sie die Datenwerte in der geschachtelten Tabellenspalte für die einzelnen Fälle abrufen möchten, müssen Sie eine Abfrage für den Modellinhalt erstellen.  
  
## Siehe auch  
 [Tasks und Anweisungen für Miningmodell-Viewer](../../analysis-services/data-mining/mining-model-viewer-tasks-and-how-tos.md)   
 [Miningmodell-Drillthrough](../../analysis-services/data-mining/drillthrough-on-mining-models.md)   
 [Drillthrough in Miningstrukturen](../../analysis-services/data-mining/drillthrough-on-mining-structures.md)  
  
  