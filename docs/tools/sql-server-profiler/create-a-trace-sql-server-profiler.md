---
title: "Erstellen einer Ablaufverfolgung (SQL Server Profiler) | Microsoft Docs"
ms.custom: ""
ms.date: "08/01/2016"
ms.prod: "sql-server-2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "database-engine"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "Ablaufverfolgungen [SQL Server], erstellen"
ms.assetid: 0302fa6d-d2b5-43fe-ad70-7a337575b112
caps.latest.revision: 28
author: "JennieHubbard"
ms.author: "jhubbard"
manager: "jhubbard"
caps.handback.revision: 28
---
# Erstellen einer Ablaufverfolgung (SQL Server Profiler)
  In diesem Thema wird beschrieben, wie Sie mit [!INCLUDE[ssSqlProfiler](../../includes/sssqlprofiler-md.md)] eine Ablaufverfolgung erstellen können.  
  
### So erstellen Sie eine Ablaufverfolgung  
  
1.  Klicken Sie im Menü **Datei** auf **Neue Ablaufverfolgung**, und stellen Sie eine Verbindung mit einer Instanz von [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]her.  
  
     Das Dialogfeld **Ablaufverfolgungseigenschaften** wird angezeigt.  
  
    > **HINWEIS:** Wenn die Option **Ablaufverfolgung sofort nach dem Herstellen der Verbindung starten** ausgewählt wurde, wird die Ablaufverfolgung sofort gestartet, ohne dass das Dialogfeld **Ablaufverfolgungseigenschaften** angezeigt wird. Um diese Einstellung zu deaktivieren, klicken Sie im Menü **Extras* *auf **Optionen**, und deaktivieren Sie das Kontrollkästchen „Ablaufverfolgung sofort nach dem Herstellen der Verbindung starten“.  
  
2.  Geben Sie im Feld **Ablaufverfolgungsname** einen Namen für die Ablaufverfolgung ein.  
  
3.  Wählen Sie in der Liste **Vorlage verwenden** eine Ablaufverfolgungsvorlage als Basis für die Ablaufverfolgung aus, oder wählen Sie **Leer** aus, wenn Sie keine Vorlage verwenden möchten.  
  
4.  Führen Sie eine der folgenden Aktionen aus, um die Ergebnisse der Ablaufverfolgung zu speichern:  
  
    -   Klicken Sie auf **In Datei speichern**, um die Ablaufverfolgung in einer Datei aufzuzeichnen. Geben Sie einen Wert für **Maximale Dateigröße festlegen**an. Der Standardwert ist 5 MB.  
  
         Sie können auch die Option **Dateirollover aktivieren** auswählen, um automatisch neue Dateien zu erstellen, sobald die maximale Dateigröße erreicht wird. Darüber hinaus können Sie die Option **Ablaufverfolgungsdaten von Serverprozessen**auswählen. Dadurch werden die Ablaufverfolgungsdaten nicht durch die Clientanwendung, sondern durch den Dienst verarbeitet, der die Ablaufverfolgung ausführt. Wenn der Server die Ablaufverfolgungsdaten verarbeitet, werden auch bei hoher Belastung keine Ereignisse ausgelassen, wodurch die Serverleistung natürlich beeinträchtigt werden kann.  
  
    -   Klicken Sie auf **In Tabelle speichern** , um die Ablaufverfolgung in einer Datenbanktabelle zu erfassen.  
  
         Klicken Sie optional auf **Maximale Zeilenzahl festlegen**, und geben Sie einen Wert an.  
  
    > **VORSICHT:** Wenn Sie die Ergebnisse der Ablaufverfolgung nicht in einer Datei oder Tabelle speichern, können Sie die Ablaufverfolgung nur anzeigen, solange [!INCLUDE[ssSqlProfiler](../../includes/sssqlprofiler-md.md)] geöffnet ist. Sobald die Ablaufverfolgung beendet und [!INCLUDE[ssSqlProfiler](../../includes/sssqlprofiler-md.md)]geschlossen wird, gehen die Ergebnisse der Ablaufverfolgung verloren. Damit das nicht geschieht, klicken Sie im Menü **Datei** auf **Speichern** . Auf diese Weise werden die Ergebnisse gespeichert, bevor Sie [!INCLUDE[ssSqlProfiler](../../includes/sssqlprofiler-md.md)]schließen.  
  
5.  Aktivieren Sie optional das Kontrollkästchen **Beendigungszeit für Ablaufverfolgung aktivieren** , und geben Sie das Datum und die Uhrzeit zum Beenden der Ablaufverfolgung an.  
  
6.  Klicken Sie auf die Registerkarte **Ereignisauswahl**, um Ereignisse, Datenspalten oder Filter hinzuzufügen oder zu entfernen. Weitere Informationen finden Sie unter [Angeben von Ereignissen und Datenspalten für eine Ablaufverfolgungsdatei &#40;SQL Server Profiler&#41;](../../tools/sql-server-profiler/specify-events-and-data-columns-for-a-trace-file-sql-server-profiler.md).  
  
7.  Klicken Sie auf **Ausführen** , um die Ablaufverfolgung zu starten.  
  
## Siehe auch  
 [Erforderliche Berechtigungen zum Ausführen von SQL Server Profiler](../../tools/sql-server-profiler/permissions-required-to-run-sql-server-profiler.md)   
 [Vorlagen und Berechtigungen in SQL Server Profiler](../../tools/sql-server-profiler/sql-server-profiler-templates-and-permissions.md)   
 [SQL Server Profiler](../../tools/sql-server-profiler/sql-server-profiler.md)   
 [Korrelieren einer Ablaufverfolgung mit Windows-Leistungsprotokolldaten &#40;SQL Server Profiler&#41;](../../tools/sql-server-profiler/correlate-a-trace-with-windows-performance-log-data-sql-server-profiler.md)  
  
  