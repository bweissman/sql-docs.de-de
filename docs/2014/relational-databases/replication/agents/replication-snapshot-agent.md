---
title: Replikationsmomentaufnahme-Agent | Microsoft-Dokumentation
ms.custom: ''
ms.date: 10/29/2018
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology:
- replication
ms.topic: conceptual
helpviewer_keywords:
- Snapshot Agent, executables
- agents [SQL Server replication], Snapshot Agent
- command prompt [SQL Server replication]
- Snapshot Agent, parameter reference
ms.assetid: 2028ba45-4436-47ed-bf79-7c957766ea04
author: MashaMSFT
ms.author: mathoma
manager: craigg
ms.openlocfilehash: 0914e0c2abea1ab4dc15b5d3410f6d717403ef27
ms.sourcegitcommit: 3e1efbe460723f9ca0a8f1d5a0e4a66f031875aa
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 10/30/2018
ms.locfileid: "50237006"
---
# <a name="replication-snapshot-agent"></a>Replikationsmomentaufnahme-Agent
  Der Replikationsmomentaufnahme-Agent ist eine ausführbare Datei, die Momentaufnahmedateien vorbereitet, die das Schema und die Daten von veröffentlichten Tabellen und Datenbankobjekten enthalten, die Dateien im Momentaufnahmeordner speichert und Synchronisierungsaufträge in der Verteilungsdatenbank aufzeichnet.  
  
> [!NOTE]  
>  Parameter können in beliebiger Reihenfolge angegeben werden.  
  
## <a name="syntax"></a>Syntax  
  
```  
  
      snapshot [ -?]   
-Publisherserver_name[\instance_name]   
-Publication publication_name   
[-70Subscribers]   
[-BcpBatchSizebcp_batch_size]  
[-DefinitionFiledef_path_and_file_name]  
[-Distributorserver_name[\instance_name]]  
[-DistributorDeadlockPriority [-1|0|1] ]  
[-DistributorLogindistributor_login]  
[-DistributorPassworddistributor_password]  
[-DistributorSecurityMode [0|1] ]  
[-DynamicFilterHostNamedynamic_filter_host_name]  
[-DynamicFilterLogindynamic_filter_login]  
[-DynamicSnapshotLocationdynamic_snapshot_location]   
[-EncryptionLevel [0|1|2]]  
[-FieldDelimiterfield_delimiter]  
[-HistoryVerboseLevel [0|1|2|3] ]  
[-HRBcpBlocksnumber_of_blocks ]  
[-HRBcpBlockSizeblock_size ]  
[-HRBcpDynamicBlocks ]  
[-KeepAliveMessageIntervalkeep_alive_interval]  
[-LoginTimeOutlogin_time_out_seconds]  
[-MaxBcpThreadsnumber_of_threads ]  
[-MaxNetworkOptimization [0|1]]  
[-Outputoutput_path_and_file_name]  
[-OutputVerboseLevel [0|1|2] ]  
[-PacketSizepacket_size]
[-PrefetchTables [0|1] ]  
[-ProfileNameprofile_name]  
[-PublisherDBpublisher_database]  
[-PublisherDeadlockPriority [-1|0|1] ]  
[-PublisherFailoverPartnerserver_name[\instance_name] ]  
[-PublisherLoginpublisher_login]  
[-PublisherPasswordpublisher_password]   
[-PublisherSecurityMode [0|1] ]  
[-QueryTimeOutquery_time_out_seconds]  
[-ReplicationType [1|2] ]  
[-RowDelimiterrow_delimiter]  
[-StartQueueTimeoutstart_queue_timeout_seconds]  
[-UsePerArticleContentsViewuse_per_article_contents_view]  
```  
  
## <a name="arguments"></a>Argumente  
 **-?**  
 Druckt alle verfügbaren Parameter.  
  
 **-Publisher** *Servername*[**\\***Instanzname*]  
 Der Name des Verlegers. Geben Sie server_name für die Standardinstanz von [!INCLUDE[msCoName](../../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] auf diesem Server an. Geben Sie *server_name***\\***instance_name* für eine benannte Instanz von [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] auf diesem Server an.  
  
 **-Publication** *publication*  
 Der Name der Veröffentlichung. Dieser Parameter ist nur gültig, wenn die Veröffentlichung so festgelegt ist, dass sie immer eine Momentaufnahme für neue oder neu initialisierte Abonnements zur Verfügung hat.  
  
 **-70Subscribers**  
 Muss verwendet werden, wenn Abonnenten vorhanden sind, auf denen [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] , Version 7.0, ausgeführt wird.  
  
 **-BcpBatchSize** *bcp*_ *batch*\_ *size*  
 Die Anzahl von Zeilen, die in einem Massenkopiervorgang gesendet werden sollen. Bei Ausführung eines **bcp in** -Vorgangs entspricht die Batchgröße der Anzahl von Zeilen, die als eine Transaktion an den Server gesendet werden sollen, und ebenso der Anzahl von Zeilen, die gesendet werden müssen, bevor der Verteilungs-Agent eine **bcp** -Statusmeldung protokolliert. Bei Ausführung eines **bcp out** -Vorgangs wird eine feste Batchgröße von 1000 verwendet. Durch den Wert 0 wird angezeigt, dass keine Meldungsprotokollierung ausgeführt wird.  
  
 **-DefinitionFile** *def_path_and_file_name*  
 Der Pfad der Agentdefinitionsdatei. Eine Agentdefinitionsdatei enthält Befehlszeilenargumente für den Agent. Der Inhalt der Datei wird als ausführbare Datei analysiert. Verwenden Sie doppelte Anführungszeichen ("), um Argumentwerte anzugeben, die beliebige Zeichen enthalten.  
  
 **-Distributor** *Servername*[**\\***Instanzname*]  
 Der Name des Verteilers. Geben Sie *server_name* für die Standardinstanz von [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] auf diesem Server an. Geben Sie *server_name***\\***instance_name* für eine benannte Instanz von [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] auf diesem Server an.  
  
 **-DistributorDeadlockPriority** [**-1**|**0**|**1**]  
 Die Priorität der Momentaufnahme-Agent-Verbindung mit dem Verteiler, wenn ein Deadlock auftritt. Dieser Parameter wird angegeben, um Deadlocks zu beheben, die möglicherweise während der Momentaufnahmegenerierung zwischen dem Momentaufnahme-Agent und Benutzeranwendungen auftreten.  
  
|Wert von DistributorDeadlockPriority|Description|  
|---------------------------------------|-----------------|  
|**-1**|Bei Auftreten eines Deadlocks auf dem Verteiler haben andere Anwendungen als der Momentaufnahme-Agent Priorität.|  
|**0** (Standard)|Es wird keine Priorität zugewiesen.|  
|**1**|Bei Auftreten eines Deadlocks auf dem Verteiler hat der Momentaufnahme-Agent Priorität.|  
  
 **-DistributorLogin** *distributor_login*  
 Der Anmeldename, der verwendet wird, um mithilfe der [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] -Authentifizierung eine Verbindung mit dem Verteiler herzustellen.  
  
 **-DistributorPassword** *distributor_password*  
 Das Kennwort, das verwendet wird, um mithilfe der [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] -Authentifizierung eine Verbindung mit dem Verteiler herzustellen. .  
  
 **-DistributorSecurityMode** [ **0**| **1**]  
 Gibt den Sicherheitsmodus des Verteilers an. Der Wert **0** steht für den [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] -Authentifizierungsmodus (Standard), der Wert **1** für den Windows-Authentifizierungsmodus.  
  
 **-DynamicFilterHostName** *dynamic_filter_host_name*  
 Wird verwendet, um einen Wert für [HOST_NAME &#40;Transact-SQL&#41;](/sql/t-sql/functions/host-name-transact-sql) bei der Filterung festzulegen, wenn eine dynamische Momentaufnahme erstellt wird. Wenn z. B. für einen Artikel die Teilmengenfilterklausel `rep_id = HOST_NAME()` angegeben wird und Sie die **DynamicFilterHostName** -Eigenschaft auf "FBJones" festlegen, bevor Sie den Merge-Agent aufrufen, werden nur Zeilen repliziert, in denen in der Spalte **rep_id** der Wert "FBJones" enthalten ist.  
  
 **-DynamicFilterLogin** *dynamic_filter_login*  
 Wird verwendet, um einen Wert für [SUSER_SNAME &#40;Transact-SQL&#41;](/sql/t-sql/functions/suser-sname-transact-sql) bei der Filterung festzulegen, wenn eine dynamische Momentaufnahme erstellt wird. Wenn z. B. für einen Artikel die Teilmengenfilterklausel `user_id = SUSER_SNAME()` angegeben wird und Sie die **DynamicFilterLogin** -Eigenschaft auf "rsmith" festlegen, bevor Sie die **Run** -Methode des **SQLSnapshot** -Objekts aufrufen, enthält die Momentaufnahme nur Zeilen, in denen in der Spalte **user_id** der Wert "rsmith" enthalten ist.  
  
 **-DynamicSnapshotLocation** *dynamic_snapshot_location*  
 Der Speicherort, an dem die dynamische Momentaufnahme generiert werden soll.  
  
 **-EncryptionLevel** [ **0** | **1** | **2** ]  
 Die Ebene der SSL-Verschlüsselung (Secure Sockets Layer), die vom Momentaufnahme-Agent beim Herstellen von Verbindungen verwendet wird.  
  
|Wert von EncryptionLevel|Description|  
|---------------------------|-----------------|  
|**0**|Gibt an, dass SSL nicht verwendet wird.|  
|**1**|Gibt an, dass SSL verwendet wird, der Agent jedoch nicht überprüft, ob das SSL-Serverzertifikat von einem vertrauenswürdigen Aussteller signiert wurde.|  
|**2**|Gibt an, dass SSL verwendet und das Zertifikat überprüft wird.|  

 > [!NOTE]  
 >  Ein gültiges SSL-Zertifikat ist mit einem vollqualifizierten Domänennamen der SQL Server definiert. Erstellen Sie einen Alias in der Reihenfolge, bis der Agent eine Verbindung herstellen, wenn Sie - EncryptionLevel auf 2 festlegen auf dem lokalen SQL Server. Der Parameter "-Alias-Name" muss den Namen des Servers und der Parameter "Server" sollte festgelegt werden, um den vollqualifizierten Namen der SQL Server.
  
 Weitere Informationen finden Sie unter [Sicherheitsübersicht &#40;Replikation&#41;](../security/security-overview-replication.md).  
  
 **-FieldDelimiter** *field_delimiter*  
 Das Zeichen oder die Zeichenfolge, das bzw. die das Ende eines Felds in der [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] -Datendatei für das Massenkopieren markiert. Der Standardwert ist \n\<x$3>\n.  
  
 **-HistoryVerboseLevel** [ **1**| **2**| **3**]  
 Gibt den Umfang des Verlaufs an, der während eines Momentaufnahmevorgangs protokolliert wird. Sie können die negativen Auswirkungen der Verlaufsprotokollierung auf die Leistung minimieren, indem Sie den Wert **1**auswählen.  
  
|Wert von <legacyBold>HistoryVerboseLevel</legacyBold>|Description|  
|-------------------------------|-----------------|  
|**0**|Statusmeldungen werden entweder an der Konsole ausgegeben oder in eine Ausgabedatei geschrieben. Verlaufsdatensätze werden nicht in der Verteilungsdatenbank protokolliert.|  
|**1**|Aktualisieren Sie immer eine vorherige Verlaufsmeldung mit dem gleichen Status (Start, Status, Erfolg usw.). Wenn kein vorheriger Datensatz mit dem gleichen Status vorhanden ist, fügen Sie einen neuen Datensatz ein.|  
|**2** (Standardwert)|Fügen Sie neue Verlaufsdatensätze ein, es sei denn, der Datensatz bezieht sich z. B. auf Leerlaufmeldungen oder Meldungen zu Aufträgen mit langer Ausführungszeit. In diesen Fällen aktualisieren Sie die vorherigen Datensätze.|  
|**3**|Fügen Sie immer neue Datensätze ein, es sei denn, ein Datensatz bezieht sich auf Leerlaufmeldungen.|  
  
 **-HRBcpBlocks** *number_of_blocks*  
 Die Anzahl von **bcp** -Datenblöcken, die zwischen dem Lese- und dem Schreibthread in die Warteschlange gestellt werden. Der Standardwert lautet "50". **HRBcpBlocks** wird nur mit Oracle-Veröffentlichungen verwendet.  
  
> [!NOTE]  
>  Dieser Parameter wird zur Leistungsoptimierung für **bcp** von einem Oracle-Verleger verwendet.  
  
 -**HRBcpBlockSize** > *Blockgröße*  
 Die Größe jedes einzelnen **bcp** -Datenblocks in Kilobytes (KB). Der Standardwert ist 64 KB. **HRBcpBlocks** wird nur mit Oracle-Veröffentlichungen verwendet.  
  
> [!NOTE]  
>  Dieser Parameter wird zur Leistungsoptimierung für **bcp** von einem Oracle-Verleger verwendet.  
  
 **-HRBcpDynamicBlocks**  
 Gibt an, ob die Größe jedes einzelnen **bcp** -Datenblocks dynamisch zunehmen kann. **HRBcpBlocks** wird nur mit Oracle-Veröffentlichungen verwendet.  
  
> [!NOTE]  
>  Dieser Parameter wird zur Leistungsoptimierung für **bcp** von einem Oracle-Verleger verwendet.  
  
 **-KeepAliveMessageInterval** *keep_alive_interval*  
 Gibt an, wie viele Sekunden der Momentaufnahme-Agent wartet, bevor die Meldung, dass auf eine Back-End-Nachricht gewartet wird, in der [MSsnapshot_history](/sql/relational-databases/system-tables/mssnapshot-history-transact-sql) -Tabelle protokolliert wird. Der Standardwert beträgt 300 Sekunden.  
  
 **-LoginTimeOut** *login_time_out_seconds*  
 Die Anzahl von Sekunden, nach denen ein Timeout bei der Anmeldung eintritt. Der Standardwert ist **15** Sekunden.  
  
 **-MaxBcpThreads** *number_of_threads*  
 Gibt die Anzahl von Massenkopiervorgängen an, die parallel ausgeführt werden können. Die maximale Anzahl von Threads und gleichzeitig vorhandenen ODBC-Verbindungen entspricht entweder **MaxBcpThreads** oder der Anzahl von Massenkopieranforderungen, die in der Verteilungsdatenbank in der Synchronisierungstransaktion enthalten sind. Dabei gilt der jeweils kleinere Wert. Der Wert von**MaxBcpThreads** muss größer als **0** sein. Es ist keine hartcodierte Obergrenze vorhanden. Der Standardwert lautet **1**.  
  
 \- **MaxNetworkOptimization** [ **0**| **1**]  
 Wird verwendet, wenn irrelevante Löschvorgänge an den Abonnenten gesendet werden. Bei irrelevanten Löschvorgängen handelt es sich um DELETE-Befehle, die für Zeilen, die nicht zur Partition des Abonnenten gehören, an den Abonnenten gesendet werden. Irrelevante Löschvorgänge beeinträchtigen weder die Datenintegrität noch die Konvergenz, allerdings können sie zu unnötigem Netzwerkverkehr führen. Der Standardwert von **MaxNetworkOptimization** lautet **0**. Wenn Sie **MaxNetworkOptimization** auf **1** festlegen, minimieren Sie dadurch das Risiko irrelevanter Löschvorgänge, wodurch der Netzwerkverkehr verringert und eine Netzwerkoptimierung erzielt wird. Gleichzeitig werden bei Festlegung dieses Parameters auf **1** u. U. mehr Metadaten gespeichert, und auf dem Verleger kann es zu Leistungseinbußen kommen, wenn mehrere Ebenen von Joinfiltern und komplexe Teilmengenfilter vorhanden sind. Daher sollten Sie die Replikationstopologie sorgfältig bewerten und **MaxNetworkOptimization** nur dann auf **1** festlegen, wenn durch irrelevante Löschvorgänge mehr Netzwerkverkehr entsteht, als akzeptabel ist.  
  
> [!NOTE]  
>  Die Festlegung dieses Parameters auf **1** ist nur dann nützlich, wenn die Synchronisierungsoptimierungsoption der Mergeveröffentlichung auf **true** festgelegt ist (der **@keep_partition_changes**-Parameter von [sp_addmergepublication &#40;Transact-SQL&#41;](/sql/relational-databases/system-stored-procedures/sp-addmergepublication-transact-sql)).  
  
 **-Output** *output_path_and_file_name*  
 Der Pfad der Agentausgabedatei. Wenn kein Dateiname angegeben ist, wird die Ausgabe an die Konsole gesendet. Wenn eine Datei mit dem angegebenen Namen vorhanden ist, wird die Ausgabe an diese Datei angefügt.  
  
 **-OutputVerboseLevel** [ **0**| **1**| **2**]  
 Gibt an, ob die Ausgabe ausführlich sein soll.  
  
|Wert von OutputVerboseLevel|Description|  
|------------------------------|-----------------|  
|**0**|Nur Fehlermeldungen werden gedruckt.|  
|**1** (Standard)|Alle Statusberichtsmeldungen werden gedruckt (Standard).|  
|**2**|Alle Fehlermeldungen und Statusberichtsmeldungen werden gedruckt, was zum Debuggen nützlich ist.|  

 **-PrefetchTables** [ **0**| **1**]  
 Optionaler Parameter, der angibt, ob die Tabellenobjekte vorab abgerufen und zwischengespeichert werden.  Standardmäßig werden bestimmte Tabelleneigenschaften mithilfe der SMO-Komponente basierend auf einer internen Berechnung vorab abgerufen.  Dieser Parameter kann in Szenarien hilfreich sein, in denen die Ausführung des SMO-Vorabrufvorgangs erheblich länger dauert. Wenn dieser Parameter nicht verwendet wird, wird diese Entscheidung zur Laufzeit basierend auf dem Prozentsatz der Tabellen getroffen, die der Veröffentlichung als Artikel hinzugefügt werden.  
  
|Wert von OutputVerboseLevel|Description|  
|------------------------------|-----------------|  
|**0**|Der Aufruf der Prefetch-Methode der SMO-Komponente ist deaktiviert.|  
|**1**|Der Momentaufnahmen-Agent ruft die Prefetch-Methode auf, um einige Tabelleneigenschaften mithilfe von SMO zwischenzuspeichern.|  
  
 **-PacketSize** *packet_size*  
 Die vom Momentaufnahme-Agent beim Herstellen der Verbindung mit [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)]verwendete Paketgröße (in Bytes). Der Standardwert ist 8192 Bytes.  
  
> [!NOTE]  
>  Sie sollten die Paketgröße nur dann ändern, wenn Sie sicher sind, dass die Leistung dadurch verbessert werden kann. Für die meisten Anwendungen empfiehlt sich die Standardpaketgröße.  
  
 **-ProfileName** *profile_name*  
 Gibt ein Agentprofil an, das für Agentparameter verwendet werden soll. Wenn **ProfileName** den Wert NULL aufweist, wird das Agentprofil deaktiviert. Wenn **ProfileName** nicht angegeben ist, wird das Standardprofil für den Agenttyp verwendet. Weitere Informationen finden Sie unter [Replication Agent Profiles](replication-agent-profiles.md).  
  
 **-PublisherDB** *publisher_database*  
 Der Name der Veröffentlichungsdatenbank. *Der Parameter wird von Oracle-Verlegern nicht unterstützt.*  
  
 **-PublisherDeadlockPriority** [**-1**|**0**|**1**]  
 Die Priorität der Momentaufnahme-Agent-Verbindung mit dem Verleger, wenn ein Deadlock auftritt. Dieser Parameter wird angegeben, um Deadlocks zu beheben, die möglicherweise während der Momentaufnahmegenerierung zwischen dem Momentaufnahme-Agent und Benutzeranwendungen auftreten.  
  
|Wert von PublisherDeadlockPriority|Description|  
|-------------------------------------|-----------------|  
|**-1**|Bei Auftreten eines Deadlocks auf dem Verleger haben andere Anwendungen als der Momentaufnahme-Agent Priorität.|  
|**0** (Standard)|Es wird keine Priorität zugewiesen.|  
|**1**|Bei Auftreten eines Deadlocks auf dem Verleger hat der Momentaufnahme-Agent Priorität.|  
  
 **-PublisherFailoverPartner** *Servername*[**\\***Instanzname*]  
 Gibt die Failoverpartnerinstanz von [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] an, die an einer Datenbank-Spiegelungssitzung mit der Veröffentlichungsdatenbank teilnimmt. Weitere Informationen finden Sie unter [Datenbankspiegelung und Replikation &#40;SQL Server&#41;](../../../database-engine/database-mirroring/database-mirroring-and-replication-sql-server.md).  
  
 **-PublisherLogin** *publisher_login*  
 Der Anmeldename, der verwendet wird, um mithilfe der [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] -Authentifizierung eine Verbindung mit dem Verleger herzustellen.  
  
 **-PublisherPassword** *Herausgeberkennwort*  
 Das Kennwort, das verwendet wird, um mithilfe der [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] -Authentifizierung eine Verbindung mit dem Verleger herzustellen. .  
  
 **-PublisherSecurityMode** [ **0**| **1**]  
 Gibt den Sicherheitsmodus des Verlegers an. Der Wert **0** steht für die [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] -Authentifizierung (Standard), der Wert **1** für den Windows-Authentifizierungsmodus.  
  
 **-QueryTimeOut** *query_time_out_seconds*  
 Die Anzahl von Sekunden, nach denen ein Timeout bei der Abfrage eintritt. Die Standardeinstellung ist 1800 Sekunden.  
  
 **-ReplicationType** [ **1**| **2**]  
 Gibt den Typ der Replikation an. Der Wert **1** steht für die Transaktionsreplikation, der Wert **2** für die Mergereplikation.  
  
 **-RowDelimiter** *row_delimiter*  
 Das Zeichen oder die Zeichenfolge, das bzw. die das Ende einer Zeile in der [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] -Datendatei für das Massenkopieren markiert. Der Standardwert ist \n\<,@g>\n.  
  
 **-StartQueueTimeout** *start_queue_timeout_seconds*  
 Die maximale Anzahl von Sekunden, die der Momentaufnahme-Agent wartet, wenn die Anzahl gleichzeitig ausgeführter dynamischer Momentaufnahmeprozesse den Grenzwert erreicht, der mit der **@max_concurrent_dynamic_snapshots**-Eigenschaft von [sp_addmergepublication &#40;Transact-SQL&#41;](/sql/relational-databases/system-stored-procedures/sp-addmergepublication-transact-sql) festgelegt wurde. Wenn der Momentaufnahme-Agent nach Verstreichen der maximalen Anzahl von Sekunden immer noch wartet, wird der Agent beendet. Der Wert 0 bedeutet, dass der Agent unbegrenzt wartet, der Vorgang jedoch abgebrochen werden kann.  
  
 \- **UsePerArticleContentsView** *use_per_article_contents_view*  
 Dieser Parameter wurde als veraltet markiert und wird lediglich aus Gründen der Abwärtskompatibilität unterstützt.  
  
## <a name="remarks"></a>Hinweise  
  
> [!IMPORTANT]  
>  Wenn Sie den [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] -Agent so installiert haben, dass er unter einem lokalen Systemkonto und nicht unter einem Domänenbenutzerkonto (Standard) ausgeführt wird, kann der Dienst nur auf den lokalen Computer zugreifen. Wenn der Momentaufnahme-Agent, der unter dem [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] -Agent ausgeführt wird, so konfiguriert ist, dass beim Anmelden bei [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)]der Windows-Authentifizierungsmodus verwendet wird, schlägt der Momentaufnahme-Agent fehl. Die Standardeinstellung ist die [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] -Authentifizierung.  
  
 Führen Sie zum Starten des Momentaufnahme-Agents von der Eingabeaufforderung **snapshot.exe** aus. Informationen hierzu finden Sie im [Abschnitt zu den ausführbaren Dateien von Replikations-Agents](../concepts/replication-agent-executables-concepts.md).  
  
## <a name="see-also"></a>Siehe auch  
 [Replikations-Agent-Verwaltung](replication-agent-administration.md)  
  
  
