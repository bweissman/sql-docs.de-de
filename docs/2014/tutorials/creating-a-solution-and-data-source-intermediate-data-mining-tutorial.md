---
title: Erstellen einer Projektmappe und Datenquelle (mittleres Datamining Tutorial) | Microsoft-Dokumentation
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology:
- analysis-services
ms.topic: conceptual
ms.assetid: 0488b231-1045-4169-aabb-c1005d86ca30
author: minewiskan
ms.author: owend
manager: craigg
ms.openlocfilehash: 1ad99c202d858bbdf5de47a21fe26070328e2de2
ms.sourcegitcommit: 3da2edf82763852cff6772a1a282ace3034b4936
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 10/02/2018
ms.locfileid: "48119630"
---
# <a name="creating-a-solution-and-data-source-intermediate-data-mining-tutorial"></a>Erstellen einer Projektmappe und einer Datenquelle (Data Mining-Lernprogramm für Fortgeschrittene)
  Um mit dem Datamining zu arbeiten, müssen Sie zunächst ein Projekt in erstellen [!INCLUDE[ssBIDevStudioFull](../includes/ssbidevstudiofull-md.md)] mithilfe der Vorlage **mehrdimensionale Analysis Services und Data Mining-Projekt**. Wenn Sie die Vorlage öffnen, werden alle Schemas in den Designer geladen, die Sie möglicherweise für Data Mining benötigen: Datenquellen, Miningstrukturen und Miningmodelle und sogar Cubes, wenn die Miningstruktur mehrdimensionale Daten verwendet.  
  
 Wenn Sie das Projekt erstellen, wird Ihre Lösung bis zur Bereitstellung als lokale Datei gespeichert. Beim Bereitstellen der Lösung [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] sucht nach dem [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] Server in den Projekteigenschaften angegeben und erstellt ein neues [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] Datenbank mit dem gleichen Namen wie das Projekt. In der Standardeinstellung [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] verwendet die **"localhost"** -Instanz für neue Projekte. Wenn Sie eine benannte Instanz verwenden oder einen anderen Namen für die Standardinstanz angegeben haben, müssen Sie für die Eigenschaft der Bereitstellungsdatenbank des Projekts den Speicherort angeben, an dem Data Mining-Objekte erstellt werden sollen.  
  
 Weitere Informationen zu [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] -Projekten finden Sie unter [Erstellen eines Analysis Services-Projekts &#40;SSDT&#41;](../analysis-services/multidimensional-models/create-an-analysis-services-project-ssdt.md).  
  
### <a name="to-create-a-new-analysis-services-project-for-this-tutorial"></a>So erstellen Sie ein neues Analysis Services-Projekt für dieses Lernprogramm  
  
1.  Öffnen Sie [!INCLUDE[ssBIDevStudioFull](../includes/ssbidevstudiofull-md.md)].  
  
2.  Zeigen Sie im Menü **Datei** auf **Neu**, und klicken Sie dann auf **Projekt**.  
  
3.  Wählen Sie die Vorlage für multidimensionale Projekte bzw. **Data Mining-Projekte von Analysis Services** aus dem Bereich **Installierte Vorlagen** aus.  
  
4.  Geben Sie im Feld **Name** den Namen **DM Intermediate**für das neue Projekt ein.  
  
5.  [!INCLUDE[clickOK](../includes/clickok-md.md)]  
  
### <a name="to-change-the-instance-where-data-mining-objects-are-stored-optional"></a>So ändern Sie die Instanz, in der Data Mining-Objekte gespeichert werden (optional)  
  
1.  In [!INCLUDE[ssBIDevStudioFull](../includes/ssbidevstudiofull-md.md)]auf die **Projekt** Menü klicken Sie auf **Eigenschaften**.  
  
2.  Klicken Sie auf der linken Seite des Bereichs **Eigenschaftenseiten** auf **Bereitstellung**.  
  
3.  Überprüfen Sie, dass als **Servername** der Name **localhost**verwendet wird. Wenn Sie eine andere Instanz verwenden, geben Sie den Namen der Instanz ein. Bei Verwendung eine benannte Instanz von [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)], geben Sie den Computernamen, und klicken Sie dann den Namen der Instanz. [!INCLUDE[clickOK](../includes/clickok-md.md)]  
  
### <a name="to-change-the-deployment-properties-for-a-project-optional"></a>So ändern Sie die Bereitstellungseigenschaften für ein Projekt (optional)  
  
1.  Klicken Sie im Projektmappen-Explorer mit der rechten Maustaste auf das Projekt und klicken Sie dann auf **Eigenschaften**.  
  
     – oder –  
  
     In [!INCLUDE[ssBIDevStudioFull](../includes/ssbidevstudiofull-md.md)]auf die **Projekt** , wählen Sie im Menü **Eigenschaften**.  
  
2.  Klicken Sie auf der linken Seite des Bereichs **Eigenschaftenseiten** auf **Bereitstellung**.  
  
     Wählen Sie im Bereich **Optionen** den **Bereitstellungsmodus**aus. Wählen Sie **Alle Objekte bereitstellen** aus, um Objekte zu überschreiben, oder wählen Sie **Nur geänderte Objekte bereitstellen** aus, um Objekte zu aktualisieren oder neue Objekte hinzuzufügen.  
  
## <a name="creating-a-data-source"></a>Erstellen einer Datenquelle  
 In der Basic Data Mining Tutorial, in dem Sie erstellt haben eine *Datenquelle* , speichert Verbindungsinformationen für die [!INCLUDE[ssSampleDBDWobject](../includes/sssampledbdwobject-md.md)] Datenbank. Führen Sie die gleichen Schritte aus, um die [!INCLUDE[ssSampleDBDWobject](../includes/sssampledbdwobject-md.md)]-Datenquelle in dieser Lösung zu erstellen.  
  
#### <a name="to-create-a-data-source"></a>So erstellen Sie eine Datenquelle  
  
-   [Erstellen einer Datenquelle &#40;Lernprogramm zu Datamining-Grundlagen&#41;](../../2014/tutorials/creating-a-data-source-basic-data-mining-tutorial.md)  
  
 Eine Datenquelle kann mehrere Datenquellensichten unterstützten und die einzelnen Datenquellensichten können mehrere Tabellen aufweisen. Aber da die Datenquelle und die Datenquelle bereitgestellt werden Ihre [!INCLUDE[msCoName](../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] -Datenbank zusammen mit der Datamining-Modelle, die Sie in die Datenquellensicht, die nur die Tabellen aufzunehmen erstellen, als bewährte Methode für jede Datamining-Modell oder eine Gruppe von Modellen erforderlich sind.  
  
 In den folgenden Lektionen fügen Sie Datenquellensichten zur Unterstützung jedes neuen Szenarios hinzu. Nur in der Market Basket- und der Sequenzcluster-Lektion wird die gleiche Datenquellensicht verwendet. Sonst wird für jedes Szenario eine andere Datenquellensicht verwendet, sodass die Lektionen keine weiteren Gemeinsamkeiten aufweisen und unabhängig voneinander abgeschlossen werden können.  
  
|Szenario|In der Datenquellensicht enthaltene Daten|  
|--------------|-------------------------------------------|  
|[Lektion 2: Erstellen eines Planungserstellungsszenarios &#40;Datamining-Lernprogramm für fortgeschrittene&#41;](../../2014/tutorials/lesson-2-building-a-forecasting-scenario-intermediate-data-mining-tutorial.md)|Monatliche Verkaufsberichte für Fahrradmodelle in unterschiedlichen Regionen (als einzelne Sicht gesammelt).|  
|[Lektion 3: Erstellen eines Warenkorbszenarios &#40;Datamining-Lernprogramm für fortgeschrittene&#41;](../../2014/tutorials/lesson-3-building-a-market-basket-scenario-intermediate-data-mining-tutorial.md)|Eine Tabelle, die eine Liste mit Kundenaufträgen und eine geschachtelte Tabelle, in der die einzelnen Käufe für jeden Kunden angezeigt werden, enthält.|  
|[Lektion 4: Erstellen eines Sequenzclusterszenarios &#40;Datamining-Lernprogramm für fortgeschrittene&#41;](../../2014/tutorials/lesson-4-build-sequence-clustering-scenario-intermediate-data-mining.md)|Die gleichen Daten, die für die Warenkorbanalyse verwendet werden, sowie ein Bezeichner, der die Reihenfolge anzeigt, in der Elemente gekauft wurden.|  
|[Lektion 5: Erstellen von neuronalen Netzwerk- und logistischen Regressionsmodellen &#40;Datamining-Lernprogramm für fortgeschrittene&#41;](../../2014/tutorials/lesson-5-build-models-intermediate-data-mining-tutorial.md)|Eine einzelne Tabelle, die vorläufige Nachverfolgungsdaten für die Leistung in einem Callcenter enthält.|  
  
## <a name="next-lesson"></a>Nächste Lektion  
 [Lektion 2: Erstellen eines Planungserstellungsszenarios &#40;Datamining-Lernprogramm für fortgeschrittene&#41;](../../2014/tutorials/lesson-2-building-a-forecasting-scenario-intermediate-data-mining-tutorial.md)  
  
## <a name="see-also"></a>Siehe auch  
 [Datamining-Projekte](../../2014/analysis-services/data-mining/data-mining-projects.md)   
 [Datenquellsichten in mehrdimensionalen Modellen](../analysis-services/multidimensional-models/data-source-views-in-multidimensional-models.md)  
  
  
