---
title: "SQL Server-Konfigurations-Manager | Microsoft Docs"
ms.custom: 
  - "SQL2016_New_Updated"
ms.date: "02/25/2016"
ms.prod: "sql-server-2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "database-engine"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "Protokolle [SQL Server], verwalten"
  - "Netzwerkprotokolle [SQL Server], verwalten"
  - "SQL Server-Clientkonfiguration"
  - "Konten [SQL Server]"
  - "SQL Server-Konfigurations-Manager"
  - "SQL Server-Netzwerkkonfiguration"
  - "Konten [SQL Server], Dienste"
  - "Dienste [SQL Server], verwalten"
  - "Tools [SQL Server], SQL Server-Konfigurations-Manager"
  - "Konfigurationsmanager [SQL Server]"
ms.assetid: e6beaea4-164c-4078-95ae-b9e28b0aefe8
caps.latest.revision: 58
author: "BYHAM"
ms.author: "rickbyh"
manager: "jhubbard"
caps.handback.revision: 58
---
# SQL Server-Konfigurations-Manager
  [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] -Konfigurations-Manager ist ein Tool zum Verwalten der Dienste, die mit [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)]verknüpft sind, zum Konfigurieren der Netzwerkprotokolle, die von [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)]verwendet werden, und zum Verwalten der Konfiguration der Netzwerkkonnektivität von [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] -Clientcomputern. [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] -Konfigurations-Manager ist ein [!INCLUDE[msCoName](../includes/msconame-md.md)] Management Console-Snap-In, auf das Sie über das Startmenü zugreifen können. Er lässt sich auch einer beliebigen anderen [!INCLUDE[msCoName](../includes/msconame-md.md)] Management Console-Anzeige hinzufügen. [!INCLUDE[msCoName](../includes/msconame-md.md)] Management Console (**mmc.exe**) verwendet die Datei **SQLServerManager\<Version>.msc** (z.B. **SQLServerManager13.msc** für [!INCLUDE[ssSQL15](../includes/sssql15-md.md)]), um den Konfigurations-Manager zu öffnen. Nachfolgend sind die Pfade der letzten vier Versionen aufgeführt (unter der Annahme, dass Windows auf Laufwerk C installiert wurde).  
  
|||  
|-|-|  
|[!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] 2016|C:\Windows\SysWOW64\SQLServerManager13.msc|  
|[!INCLUDE[ssSQL14](../includes/sssql14-md.md)]|C:\Windows\SysWOW64\SQLServerManager12.msc|  
|[!INCLUDE[ssSQL11](../includes/sssql11-md.md)]|C:\Windows\SysWOW64\SQLServerManager11.msc|  
|[!INCLUDE[ssKatmai](../includes/sskatmai-md.md)]|C:\Windows\SysWOW64\SQLServerManager10.msc|  
  
> [!NOTE]  
>  Da der [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)]-Konfigurations-Manager ein Snap-In für das [!INCLUDE[msCoName](../includes/msconame-md.md)]-Verwaltungskonsolenprogramm und kein eigenständiges Programm ist, wird der [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)]-Konfigurations-Manager in neueren Versionen von Windows nicht als Anwendung angezeigt.  
>   
>  -   **Windows 10**:  
>          Geben Sie zum Öffnen des [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)]-Konfigurations-Managers auf der **Startseite** Folgendes ein: SQLServerManager13.msc (für [!INCLUDE[ssSQL15](../includes/sssql15-md.md)]). Ersetzen Sie für frühere Versionen von [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] 13 durch eine kleinere Zahl. Durch Klicken auf „SQLServerManager13.msc“ wird der Konfigurations-Manager geöffnet. Um den Konfigurations-Manager an die Startseite oder Taskleiste anzuheften, klicken Sie mit der rechten Maustaste auf „SQLServerManager13.msc“, und klicken Sie dann auf **Dateispeicherort öffnen**. Klicken Sie im Windows-Explorer mit der rechten Maustaste auf „SQLServerManager13.msc“, und klicken Sie dann auf **An Startmenü anheften** oder **An Taskleiste anheften**.  
> -   **Windows 8**:  
>          Um den [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)]-Konfigurations-Manager im Charm **Suchen** unter **Apps** zu öffnen, geben Sie **SQLServerManager\<Version>.msc** ein, z.B. **SQLServerManager13.msc**, und drücken Sie dann die **EINGABETASTE**.  
  
 [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] -Konfigurations-Manager und SQL Server Management Studio verwenden Windows-Verwaltungsinstrumentation (WMI, Window Management Instrumentation) zum Anzeigen und Ändern einiger Servereinstellungen. WMI bietet eine vereinheitlichte Schnittstellenfunktion zu API-Aufrufen, mit denen die Registrierungsvorgänge verwaltet werden, die von den [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)]-Tools angefordert werden. Außerdem werden die Steuerungs- und Bearbeitungsfunktionen für die ausgewählten SQL-Dienste der Snap-In-Komponente des [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)]-Konfigurations-Managers verbessert. Informationen zum Konfigurieren von Berechtigungen in Bezug auf WMI finden Sie unter [Konfigurieren von WMI zum Anzeigen des Serverstatus in SQL Server-Tools](../ssms/configure-wmi-to-show-server-status-in-sql-server-tools.md).  
  
 Informationen zum Starten, Beenden, Anhalten, Fortsetzen oder Konfigurieren von Diensten auf einem anderen Computer mithilfe des [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)]-Konfigurations-Managers finden Sie unter [Herstellen einer Verbindung mit einem anderen Computer &#40;SQL Server-Konfigurations-Manager&#41;](../database-engine/configure-windows/connect-to-another-computer-sql-server-configuration-manager.md).  
  
## Verwalten von Diensten  
 Mit dem [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] -Konfigurations-Manager können Sie die Dienste starten, anhalten, fortsetzen oder beenden, Diensteigenschaften anzeigen oder Diensteigenschaften ändern.  
  
 Verwenden Sie den [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)]-Konfigurations-Manager, um das [!INCLUDE[ssDE](../includes/ssde-md.md)] mit Startparametern zu starten.  Weitere Informationen finden Sie unter [Konfigurieren von Serverstartoptionen &#40;SQL Server-Konfigurations-Manager&#41;](../database-engine/configure-windows/configure-server-startup-options-sql-server-configuration-manager.md).  
  
## Ändern der von den Diensten verwendeten Konten  
 Verwenden Sie zum Verwalten der [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] -Dienste den [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] -Konfigurations-Manager.  
  
> [!IMPORTANT]  
>  Verwenden Sie immer [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] -Tools, z. B. den [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] -Konfigurations-Manager, um das von den [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] - oder [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] -Agent-Diensten verwendete Konto oder das Kennwort für das Konto zu ändern. Zusätzlich zum Ändern des Kontonamens konfiguriert der [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] -Konfigurations-Manager weitere Einstellungen. So legt er z. B. Berechtigungen in der Windows-Registrierung fest, damit die [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] -Einstellungen vom neuen Konto gelesen werden können. Mit anderen Tools, z. B. dem Windows-Dienstkontroll-Manager, kann der Kontoname geändert werden, aber nicht die zugehörigen Einstellungen. Wenn der Dienst nicht auf den [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] -Teil der Registrierung zugreifen kann, wird der Dienst möglicherweise nicht ordnungsgemäß gestartet.  
  
 Ein weiterer Vorteil des Änderns von Kennwörtern mithilfe des [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)]-Konfigurations-Managers, SMO oder WMI besteht darin, dass die Änderung sofort in Kraft tritt, ohne dass der Dienst neu gestartet werden muss.  
  
## Verwalten von Server- & Clientnetzwerkprotokollen  
 [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] -Konfigurations-Manager können Sie Server- und Clientnetzwerkprotokolle und Konnektivitätsoptionen konfigurieren. Nachdem die richtigen Protokolle aktiviert wurden, müssen Sie die Servernetzwerkverbindungen im Normalfall nicht ändern. Sie können aber den [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)]-Konfigurations-Manager verwenden, wenn Sie die Serververbindungen so konfigurieren müssen, dass [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] bei der Überwachung an bestimmten Netzwerkprotokolle, Ports oder Pipes lauscht. Weitere Informationen zum Aktivieren von Protokollen finden Sie unter [Aktivieren oder Deaktivieren eines Servernetzwerkprotokolls](../database-engine/configure-windows/enable-or-disable-a-server-network-protocol.md). Informationen zum Aktivieren des Zugriffs auf Protokolle über eine Firewall finden Sie unter [Konfigurieren der Windows-Firewall für SQL Server-Zugriff](../sql-server/install/configure-the-windows-firewall-to-allow-sql-server-access.md).  
  
 [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] -Konfigurations-Manager ermöglicht Ihnen, Server- und Clientnetzwerkprotokolle zu verwalten sowie die Protokollverschlüsselung zu erzwingen, Aliaseigenschaften anzuzeigen oder ein Protokoll zu aktivieren bzw. deaktivieren.  
  
 [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] -Konfigurations-Manager können Sie ein Alias erstellen oder entfernen, die Reihenfolge für die Verwendung der Protokolle ändern oder Serveraliaseigenschaften anzeigen, z. B. Folgende:  
  
-   Serveralias - Serveralias, der für den Computer verwendet wird, mit dem der Client eine Verbindung herstellt  
  
-   Protokoll - Netzwerkprotokoll, das für den Konfigurationseintrag verwendet wird  
  
-   Verbindungsparameter - Parameter, die mit der Verbindungsadresse für die Netzwerkprotokollkonfiguration verknüpft sind  
  
 Außerdem können Sie mit dem [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] -Konfigurations-Manager Informationen zu Failover-Clusterinstanzen anzeigen. Für einige Aktionen, z. B. Starten und Beenden der Dienste, sollten Sie aber die Clusterverwaltung verwenden.  
  
### Verfügbare Netzwerkprotokolle  
 [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] unterstützt die Protokolle Shared Memory, TCP/IP und Named Pipes. Informationen zur Auswahl eines Netzwerkprotokolls finden Sie unter [Configure Client Protocols](../database-engine/configure-windows/configure-client-protocols.md). [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] unterstützt nicht die Netzwerkprotokolle VIA, Banyan VINES Sequenced Packet Protocol (SSP), Multiprotocol, AppleTalk oder NWLink IPX/SPX. Clients, die zuvor Verbindungen mit diesen Protokollen hergestellt haben, müssen zum Herstellen der Verbindung mit [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] ein anderes Protokoll auswählen. Sie können den [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] -Konfigurations-Manager nicht zum Konfigurieren des Winsockproxy verwenden. Informationen zum Konfigurieren des Winsockproxys finden Sie in der ISA Server-Dokumentation.  
  
## Verwandte Aufgaben  
 [Verwalten von Diensten: Themen zur Vorgehensweise &#40;SQL Server-Konfigurations-Manager&#41;](../Topic/Managing%20Services%20How-to%20Topics%20\(SQL%20Server%20Configuration%20Manager\).md)  
  
 [Starten, Beenden, Anhalten, Fortsetzen und Neustarten des Datenbankmoduls, SQL Server-Agent oder des SQL Server-Browsers](../database-engine/configure-windows/start, stop, pause, resume, restart sql server services.md)  
  
 [Starten, Beenden oder Anhalten des SQL Server-Agent-Dienstes](../ssms/agent/start-stop-or-pause-the-sql-server-agent-service.md)  
  
 [Festlegen des automatischen Starts einer Instanz von SQL Server &#40;SQL Server-Konfigurations-Manager&#41;](../database-engine/configure-windows/scm services - set an instance to start automatically.md)  
  
 [Verhindern des automatischen Starts einer Instanz von SQL Server &#40;SQL Server-Konfigurations-Manager&#41;](../database-engine/configure-windows/scm services - prevent automatic startup of an instance.md)  
  
  