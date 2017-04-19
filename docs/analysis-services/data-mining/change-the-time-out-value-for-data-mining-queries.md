---
title: "&#196;ndern des Timeoutwerts f&#252;r Data Mining-Abfragen | Microsoft Docs"
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
helpviewer_keywords: 
  - "Timeout"
ms.assetid: f1add4bc-e882-440a-a98b-333cfa274c3e
caps.latest.revision: 12
author: "Minewiskan"
ms.author: "owend"
manager: "jhubbard"
caps.handback.revision: 12
---
# &#196;ndern des Timeoutwerts f&#252;r Data Mining-Abfragen
  Wenn Sie ein Prognosegütediagramm erstellen oder eine Vorhersageabfrage ausführen, kann es viel Zeit in Anspruch nehmen, alle für die Vorhersage erforderlichen Daten zu generieren. Um ein Timeout der Abfrage zu verhindern, können Sie den Wert ändern, der festlegt, wie lange der [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] -Server auf den Abschluss einer Abfrage wartet.  
  
 Der Standardwert ist 15. Wenn Ihre Modelle komplex sind oder die Datenquelle umfangreich ist, reicht dies unter Umständen nicht aus. Bei Bedarf können Sie den Wert heraufsetzen, um genügend Zeit für die Verarbeitung bereitzustellen. Beispiel: wenn Sie **Abfragetimeout** auf 600 setzen, kann die Abfrage bis zu 10 Minuten lang ausgeführt werden.  
  
 Weitere Informationen zu Vorhersageabfragen finden Sie unter [Data Mining-Abfragetasks und Anweisungen](../../analysis-services/data-mining/data-mining-query-tasks-and-how-tos.md).  
  
### Konfigurieren des Timeoutwerts für Data Mining-Abfragen  
  
1.  Klicken Sie in [!INCLUDE[ssBIDevStudioFull](../../includes/ssbidevstudiofull-md.md)]im Menü **Extras** auf **Optionen**.  
  
2.  Erweitern Sie im Bereich **Optionen** **Business Intelligence-Designer**.  
  
3.  Klicken Sie auf das Textfeld **Abfragetimeout** , und geben Sie einen Wert für die Anzahl der Sekunden ein.  
  
## Siehe auch  
 [Data Mining-Abfragetasks und Anweisungen](../../analysis-services/data-mining/data-mining-query-tasks-and-how-tos.md)   
 [Data Mining-Abfrage](../../analysis-services/data-mining/data-mining-queries.md)  
  
  