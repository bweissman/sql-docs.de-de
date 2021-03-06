---
title: Anzeigen und Analysieren von Ablaufverfolgungen mit SQL Server Profiler | Microsoft-Dokumentation
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology:
- database-engine
ms.topic: conceptual
helpviewer_keywords:
- Profiler [SQL Server Profiler], viewing traces
- SQL Server Profiler, viewing traces
- traces [SQL Server], viewing
- SQL Server Profiler, troubleshooting
- troubleshooting [SQL Server], traces
- events [SQL Server], finding inside trace
- Profiler [SQL Server Profiler], troubleshooting
- traces [SQL Server], events
ms.assetid: 17e821ca-a12e-4192-acc1-96765d9ae266
author: stevestein
ms.author: sstein
manager: craigg
ms.openlocfilehash: e6739f427642151bec0fd193c26d40a16af51e94
ms.sourcegitcommit: 3da2edf82763852cff6772a1a282ace3034b4936
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 10/02/2018
ms.locfileid: "48213430"
---
# <a name="view-and-analyze-traces-with-sql-server-profiler"></a>Anzeigen und Analysieren von Ablaufverfolgungen mit SQL Server Profiler
  Verwenden Sie [!INCLUDE[ssSqlProfiler](../../includes/sssqlprofiler-md.md)] , um aufgezeichnete Ereignisdaten in einer Ablaufverfolgung anzuzeigen. [!INCLUDE[ssSqlProfiler](../../includes/sssqlprofiler-md.md)] zeigt Daten je nach definierten Ablaufverfolgungseigenschaften an. Eine Möglichkeit, [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] -Daten zu analysieren, besteht darin, die Daten in ein anderes Programm wie [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] oder den Optimierungsratgeber von [!INCLUDE[ssDE](../../includes/ssde-md.md)] zu kopieren. [!INCLUDE[ssDE](../../includes/ssde-md.md)] Wenn bei der Ablaufverfolgung die **Text** -Datenspalte einbezogen wird, kann der Optimierungsratgeber eine Ablaufverfolgungsdatei mit SQL-Batch- und RPC-Ereignissen verwenden. Verwenden Sie die im Lieferumfang von [!INCLUDE[ssDE](../../includes/ssde-md.md)] enthaltene vordefinierte Optimierungsvorlage, um sicherzustellen, dass für den Optimierungsratgeber von [!INCLUDE[ssSqlProfiler](../../includes/sssqlprofiler-md.md)]die richtigen Ereignisse und Spalten aufgezeichnet werden.  
  
 Wenn Sie mit [!INCLUDE[ssSqlProfiler](../../includes/sssqlprofiler-md.md)]eine Ablaufverfolgung aufrufen und die Ablaufverfolgungsdatei durch gespeicherte Systemprozeduren von [!INCLUDE[ssSqlProfiler](../../includes/sssqlprofiler-md.md)] oder der SQL-Ablaufverfolgung erstellt wurde, muss diese Datei nicht die Dateierweiterung TRC tragen.  
  
> [!NOTE]  
>  [!INCLUDE[ssSqlProfiler](../../includes/sssqlprofiler-md.md)] kann auch Protokolldateien der SQL-Ablaufverfolgung sowie allgemeine SQL-Skriptdateien lesen. Wenn Sie eine Protokolldatei der SQL-Ablaufverfolgung öffnen, die nicht die Dateierweiterung LOG aufweist (z.B. „trace.txt“), legen Sie als Dateiformat **SQLTrace_Log** fest.  
  
 Um die Ablaufverfolgungsanalyse zu erleichtern, können Sie das Anzeigeformat für Datum und Uhrzeit in [!INCLUDE[ssSqlProfiler](../../includes/sssqlprofiler-md.md)] konfigurieren.  
  
## <a name="troubleshooting-data"></a>Problembehandlung von Daten  
 Mit [!INCLUDE[ssSqlProfiler](../../includes/sssqlprofiler-md.md)]können Sie die Problembehandlung für Daten ausführen, indem Sie Ablaufverfolgungen oder Ablaufverfolgungsdateien nach der Datenspalte **Duration**, **CPU**, **Reads**oder **Writes** in Gruppen zusammenfassen. Zu den Daten, für die Sie eine Problembehandlung durchführen können, gehören beispielsweise Abfragen, deren Ergebnisse nicht zufrieden stellend ausfallen, oder die eine außergewöhnlich hohe Anzahl logischer Lesevorgänge aufweisen.  
  
 Zusätzliche Informationen stehen zur Verfügung, wenn die Ablaufverfolgungen in Tabellen gespeichert werden und [!INCLUDE[tsql](../../includes/tsql-md.md)] für die Abfrage der Ereignisdaten verwendet wird. Wenn Sie z.B. feststellen möchten, welche **SQL:BatchCompleted**-Ereignisse eine überlange Wartezeit aufweisen, führen Sie Folgendes aus:  
  
```  
SELECT  TextData, Duration, CPU  
FROM    trace_table_name  
WHERE   EventClass = 12 -- SQL:BatchCompleted events  
AND     CPU < (Duration * 1000)  
```  
  
> [!NOTE]  
>  Der Server meldet die Dauer eines Ereignisses in Mikrosekunden (ein Millionstel oder 10<sup>-6</sup> einer Sekunde) und den Umfang der vom Ereignis verbrauchten CPU-Zeit in Millisekunden (ein Tausendstel oder 10<sup>-3</sup> einer Sekunde). In [!INCLUDE[ssSqlProfiler](../../includes/sssqlprofiler-md.md)] zeigt die grafische Benutzeroberfläche die **Duration** -Spalte standardmäßig in Millisekunden an. Wird jedoch eine Ablaufverfolgung entweder in einer Datei oder in einer Datenbanktabelle gespeichert, wird der Wert der **Duration** -Spalte in Mikrosekunden aufgezeichnet.  
  
## <a name="displaying-object-names-when-viewing-traces"></a>Anzeigen von Objektnamen bei der Anzeige von Ablaufverfolgungen  
 Wenn Sie statt des Objektbezeichners (**ObjectID**) lieber den Namen eines Objekts anzeigen möchten, müssen Sie zusammen mit der Datenspalte **ObjectName** auch die Datenspalten **ServerName** und **DatabaseID** aufzeichnen.  
  
 Wenn auf der Grundlage der **ObjectID** -Datenspalte gruppiert werden soll, stellen Sie sicher, dass Sie zuerst nach den Datenspalten **ServerName** und **DatabaseID** und erst anschließend nach der **ObjectID** -Datenspalte gruppieren. Analog müssen Sie, wenn Sie auf der Grundlage der **IndexID** -Datenspalte gruppieren möchten, sicherstellen, dass Sie zuerst nach den Datenspalten **ServerName**, **DatabaseID**und **ObjectID** und erst anschließend nach der **IndexID** -Datenspalte gruppieren. Diese Reihenfolge muss beim Gruppieren eingehalten werden, weil die Objekt- und Index-IDs für die verschiedenen Server und Datenbanken (und die Index-IDs für die verschiedenen Objekte) nicht eindeutig erkennbar sind.  
  
## <a name="finding-specific-events-within-a-trace"></a>Suchen nach bestimmten Ereignissen in einer Ablaufverfolgung  
 Gehen Sie wie folgt vor, um in einer Ablaufverfolgung nach Ereignissen zu suchen und diese zu gruppieren:  
  
1.  Erstellen Sie eine Ablaufverfolgung.  
  
    -   Zeichnen Sie beim Definieren der Ablaufverfolgung neben allen anderen gewünschten Datenspalten auch die Datenspalten **EventClass**, **ClientProcessID** und **StartTime** auf. Weitere Informationen finden Sie unter [Erstellen einer Ablaufverfolgung &#40;SQL Server Profiler&#41;](create-a-trace-sql-server-profiler.md).  
  
    -   Gruppieren Sie die aufgezeichneten Daten nach der Datenspalte **Event Class**, und zeichnen Sie die Ablaufverfolgung in einer Datei oder Tabelle auf. Klicken Sie im Dialogfeld „Ablaufverfolgungseigenschaften“ auf der Registerkarte **Ereignisauswahl** auf **Spalten organisieren**, um die aufgezeichneten Daten zu gruppieren. Weitere Informationen finden Sie unter [Organisieren von in einer Ablaufverfolgung angezeigten Spalten &#40;SQL Server Profiler&#41;](organize-columns-displayed-in-a-trace-sql-server-profiler.md).  
  
    -   Starten Sie die Ablaufverfolgung, und beenden Sie sie nach Ablauf der festgelegten Zeit oder nach Erfassung der festgelegten Anzahl von Ereignissen.  
  
2.  Suchen Sie nach den Zielereignissen.  
  
    -   Öffnen Sie die Ablaufverfolgungsdatei oder -tabelle, und erweitern Sie den Knoten der gewünschten Ereignisklasse, z.B. **Deadlock Chain**. Weitere Informationen finden Sie unter [Öffnen einer Ablaufverfolgungsdatei &#40;SQL Server Profiler&#41;](open-a-trace-file-sql-server-profiler.md) oder unter [Öffnen einer Ablaufverfolgungstabelle &#40;SQL Server Profiler&#41;](open-a-trace-table-sql-server-profiler.md).  
  
    -   Durchsuchen Sie die Daten der Ablaufverfolgung, bis Sie die gesuchten Ereignisse finden (klicken Sie in **im Menü** Bearbeiten **auf** Suchen [!INCLUDE[ssSqlProfiler](../../includes/sssqlprofiler-md.md)] , um nach Werten in der Ablaufverfolgung zu suchen). Beachten Sie bei den Ereignissen, für die Sie die Ablaufverfolgung durchführen, die Werte in den Datenspalten **ClientProcessID** und **StartTime** .  
  
3.  Zeigen Sie die Ereignisse im Kontext an.  
  
    -   Zeigen Sie die Eigenschaften der Ablaufverfolgung an, und gruppieren Sie die Daten nicht auf Grundlage der Datenspalte **Event Class**, sondern nach der Datenspalte **ClientProcessID** .  
  
    -   Erweitern Sie die Knoten für jede einzelne Clientprozess-ID, die Sie anzeigen möchten. Durchsuchen Sie die Ablaufverfolgung manuell oder mithilfe der Option **Suchen** , bis Sie die zuvor notierten **Start Time**-Werte der Zielereignisse finden. Die Ereignisse werden in chronologischer Reihenfolge mit den anderen Ereignissen angezeigt, die zu den einzelnen ausgewählten Client-Prozess-IDs gehören. Beispielsweise werden das **Deadlock** -Ereignis und das **Deadlock Chain**-Ereignis, die bei der Ablaufverfolgung aufgezeichnet wurden, innerhalb der erweiterten Client-Prozess-ID sofort nach den **SQL:BatchStarting**-Ereignissen angezeigt.  
  
 Diese Methode kann auch verwendet werden, um nach anderen gruppierten Ereignissen zu suchen. Sobald Sie die gesuchten Ereignisse gefunden haben, gruppieren Sie diese nach der Ereignisklasse **ClientProcessID**, **ApplicationName**oder einer anderen Ereignisklasse, um zugehörige Aktivitäten in chronologischer Reihenfolge anzuzeigen.  
  
## <a name="see-also"></a>Siehe auch  
 [Anzeigen einer gespeicherten Ablaufverfolgung &#40;Transact-SQL&#41;](../../relational-databases/sql-trace/view-a-saved-trace-transact-sql.md)   
 [sys.fn_trace_getinfo &#40;Transact-SQL&#41;](/sql/relational-databases/system-functions/sys-fn-trace-getinfo-transact-sql)   
 [Anzeigen von Filterinformationen &#40;SQL Server Profiler&#41;](view-filter-information-sql-server-profiler.md)   
 [Anzeigen von Filterinformationen &#40;Transact-SQL&#41;](../../relational-databases/sql-trace/view-filter-information-transact-sql.md)   
 [Öffnen einer Ablaufverfolgungsdatei &#40;SQL Server Profiler&#41;](open-a-trace-file-sql-server-profiler.md)   
 [Öffnen einer Ablaufverfolgungstabelle &#40;SQL Server Profiler&#41;](open-a-trace-table-sql-server-profiler.md)  
  
  
