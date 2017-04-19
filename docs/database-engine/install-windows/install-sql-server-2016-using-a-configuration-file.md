---
title: "Installieren von SQL Server 2016 mithilfe einer Konfigurationsdatei | Microsoft Docs"
ms.custom: ""
ms.date: "01/20/2016"
ms.prod: "sql-server-2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "setup-install"
ms.tgt_pltfrm: ""
ms.topic: "home-page"
ms.assetid: a832153a-6775-4bed-83f0-55790766d885
caps.latest.revision: 34
author: "MikeRayMSFT"
ms.author: "mikeray"
manager: "jhubbard"
caps.handback.revision: 34
---
# Installieren von SQL Server 2016 mithilfe einer Konfigurationsdatei
  [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] -Setup bietet die Möglichkeit, eine Konfigurationsdatei auf der Grundlage von Systemstandards und Laufzeiteingaben zu generieren. Sie können die Konfigurationsdatei verwenden, um [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] im gesamten Unternehmen mit der gleichen Konfiguration bereitzustellen. Außerdem können manuelle Installationen über das gesamte Unternehmen hinweg standardisiert werden, indem eine Batchdatei erstellt wird, die Setup.exe startet.  
  
 Setup unterstützt die Verwendung der Konfigurationsdatei nur über die Eingabeaufforderung. Die Verarbeitungsreihenfolge der Parameter während der Verwendung der Konfigurationsdatei wird im Folgenden erläutert:  
  
-   Die Konfigurationsdatei überschreibt die Standards in einem Paket  
  
-   Befehlszeilenwerte überschreiben die Werte in der Konfigurationsdatei  
  
 Die Konfigurationsdatei kann zur Nachverfolgung der Parameter und Werte der einzelnen Installationen verwendet werden. Aus diesem Grund ist die Konfigurationsdatei hilfreich beim Überprüfen und Überwachen der Installationen.  
  
## Struktur der Konfigurationsdatei  
 Die Datei ConfigurationFile.ini ist eine Textdatei mit Parametern (Name/Wert-Paar) und beschreibenden Kommentaren.  
  
 Im Folgenden finden Sie ein Beispiel für eine ConfigurationFile.ini-Datei:  
  
```  
; Microsoft SQL Server Configuration file  
[OPTIONS]  
; Specifies a Setup work flow, like INSTALL, UNINSTALL, or UPGRADE.   
; This is a required parameter.   
ACTION="Install"  
; Specifies features to install, uninstall, or upgrade.   
; The list of top-level features include SQL, AS, RS, IS, and Tools.   
; The SQL feature will install the database engine, replication, and full-text.   
; The Tools feature will install Management Tools, Books online,   
; SQL Server Data Tools, and other shared components.   
FEATURES=SQL,Tools  
```  
  
#### So generieren Sie eine Konfigurationsdatei  
  
1.  Legen Sie das [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]-Installationsmedium ein. Doppelklicken Sie im Stammordner auf Setup.exe. Wenn Sie eine Installation über eine Netzwerkfreigabe vornehmen möchten, suchen Sie den Stammordner in der Freigabe, und doppelklicken Sie auf setup.exe.  
  
    > [!NOTE]  
    >  [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Express Edition-Setup erstellt nicht automatisch eine Konfigurationsdatei. Der folgende Befehl startet das Setup und erstellt eine Konfigurationsdatei.  
    >   
    >  SETUP.exe /UIMODE=Normal /ACTION=INSTALL  
  
2.  Folgen Sie dem Assistenten durch die Seite **Installationsbereit** . Der Pfad zur Konfigurationsdatei wird auf der Seite **Installationsbereit** im Abschnitt mit dem Konfigurationsdateipfad angegeben. Weitere Informationen über die Installation von [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] finden Sie unter [Installieren von SQL Server 2016 vom Installations-Assistenten aus &#40;Setup&#41;](../../database-engine/install-windows/install-sql-server-2016-from-the-installation-wizard-setup.md).  
  
3.  Brechen Sie das Setupprogramm ab, ohne dabei die Installation abzuschließen, um die INI-Datei zu generieren.  
  
    > [!NOTE]  
    >  Die Setupinfrastruktur schreibt alle entsprechenden Parameter für die Aktionen, die ausgeführt wurden, mit Ausnahme vertraulicher Daten wie Kennwörter. Der /IAcceptSQLServerLicenseTerms-Parameter wird auch nicht in die Konfigurationsdatei geschrieben und erfordert entweder eine Änderung der Konfigurationsdatei oder die Angabe eines Werts an der Eingabeaufforderung. Weitere Informationen finden Sie unter [Installieren von SQL Server 2016 über die Eingabeaufforderung](../../database-engine/install-windows/install-sql-server-2016-from-the-command-prompt.md). Zusätzlich wird bei booleschen Parametern, bei denen der Wert normalerweise nicht über die Eingabeaufforderung angegeben wird, ein Wert eingefügt.  
  
## Verwenden der Konfigurationsdatei zur Installation von [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]  
 Sie können die Konfigurationsdatei nur bei Befehlszeileninstallationen verwenden.  
  
> [!NOTE]  
>  Wenn Sie Änderungen an der Konfigurationsdatei vornehmen müssen, empfiehlt es sich, eine Kopie zu erstellen und mit dieser zu arbeiten.  
  
#### So installieren Sie eine eigenständige [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]-Instanz mithilfe einer Konfigurationsdatei  
  
-   Führen Sie die Installation über die Eingabeaufforderung aus, und geben Sie die ConfigurationFile.ini mithilfe des *ConfigurationFile* -Parameters an.  
  
#### So verwenden Sie eine Konfigurationsdatei zum Vorbereiten und Abschließen eines Images einer eigenständigen [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]-Instanz (SysPrep)  
  
1.  So bereiten Sie eine oder mehrere Instanzen von [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] vor und konfigurieren sie auf dem gleichen Computer.  
  
    -   Führen Sie **Vorbereiten eines Images von einer eigenständigen [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]-Instanz** auf der Seite **Erweitert** des Installationscenters aus, und zeichnen Sie die Datei zur Vorbereitung der Imagekonfiguration auf.  
  
    -   Verwenden Sie die gleiche Datei zur Vorbereitung der Imagekonfiguration als Vorlage für weitere Instanzen von [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].  
  
    -   Führen Sie **Abschließen eines Images von einer vorbereiteten eigenständigen [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]-Instanz** auf der Seite **Erweitert** des Installationscenters aus, um eine vorbereitete Instanz auf dem Computer zu konfigurieren.  
  
2.  So bereiten Sie ein Image des Betriebssystems, einschließlich einer nicht konfigurierten vorbereiteten Instanz von [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)], mit dem Windows-Tool SysPrep vor.  
  
    -   Führen Sie **Vorbereiten eines Images von einer eigenständigen [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]-Instanz** auf der Seite „Erweitert“ des Installationscenters aus, und zeichnen Sie die Datei zur Vorbereitung der Imagekonfiguration auf.  
  
    -   Führen Sie **Abschließen eines Images von einer vorbereiteten eigenständigen [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]-Instanz** auf der Seite **Erweitert** des Installationscenters aus, brechen Sie den Befehl jedoch auf der Seite **Das Image kann jetzt abgeschlossen werden** ab, nachdem Sie die vollständige Konfigurationsdatei aufgezeichnet haben.  
  
    -   Die abgeschlossene Imagekonfigurationsdatei kann mit dem Windows-Image zum Automatisieren der Konfiguration der vorbereiteten Instanzen gespeichert werden.  
  
#### So installieren Sie einen [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]-Failovercluster mithilfe der Konfigurationsdatei  
  
1.  Option für die integrierte Installation (Erstellen Sie auf einem Knoten einen Failovercluster mit einem einzelnen Knoten, und führen Sie für zusätzliche Knoten AddNode auf den Knoten aus):  
  
    -   Führen Sie die Option zum Installieren eines Failoverclusters aus, und zeichnen Sie die Konfigurationsdatei auf, in der alle Installationseinstellungen aufgelistet sind.  
  
    -   Führen Sie die Installation des Failoverclusters über die Befehlszeile aus, indem Sie den *ConfigurationFile*-Parameter angeben.  
  
    -   Führen Sie für zusätzliche Knoten, die hinzugefügt werden sollen, AddNode aus, um die für den vorhandenen Failovercluster zutreffende Datei ConfigurationFile.ini aufzuzeichnen.  
  
    -   Führen Sie AddNode an der Befehlszeile für alle zusätzlichen Knoten aus, die Teil des Failoverclusters werden, indem Sie mithilfe des ConfigurationFile-Parameters die gleiche Konfigurationsdatei angeben.  
  
2.  Option für die erweiterte Installation (Bereiten Sie den Failovercluster für alle Failoverclusterknoten vor, und führen Sie danach für den Knoten, der den freigegebenen Datenträger besitzt, die Option zum Abschließen aus):  
  
    -   Führen Sie **Vorbereiten** für einen der Knoten aus, und zeichnen Sie die Datei ConfigurationFile.ini auf.  
  
    -   Geben Sie beim Setupvorgang für alle Knoten, die für den Failovercluster vorbereitet werden, die gleiche ConfigurationFile.ini-Datei an.  
  
    -   Nachdem alle Knoten vorbereitet wurden, führen Sie einen vollständigen Failoverclustervorgang für den Knoten aus, der den freigegebenen Datenträger besitzt, und zeichnen Sie die Datei ConfigurationFile.ini auf.  
  
    -   Sie können dann diese ConfigurationFile.ini-Datei angeben, um den Failovercluster abzuschließen.  
  
#### So fügen Sie mithilfe der Konfigurationsdatei einen Knoten zu einem [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] -Failovercluster hinzu oder entfernen diesen  
  
-   Wenn Sie über eine Konfigurationsdatei verfügen, mit der bereits ein Knoten zu einem Failovercluster hinzugefügt oder daraus entfernt wurde, können Sie diese Datei erneut zum Hinzufügen oder Entfernen zusätzlicher Knoten verwenden.  
  
#### So aktualisieren Sie einen [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] -Failovercluster mithilfe der Konfigurationsdatei  
  
1.  Führen Sie das Upgrade für den passiven Knoten aus, und zeichnen Sie die Datei ConfigurationFile.ini auf. Sie können dazu entweder das tatsächliche Upgrade ausführen oder am Ende den Vorgang beenden, ohne das tatsächliche Update auszuführen.  
  
2.  Geben Sie für alle zusätzlichen Knoten, die aktualisiert werden sollen, die Datei ConfigurationFile.ini an, um den Vorgang abzuschließen.  
  
## Beispielsyntax  
 Im Folgenden finden Sie einige Beispiele für das Verwenden der Konfigurationsdatei:  
  
-   Angeben der Konfigurationsdatei an der Eingabeaufforderung:  
  
```  
Setup.exe /ConfigurationFile=MyConfigurationFile.INI  
```  
  
-   Angeben von Kennwörtern an der Eingabeaufforderung und nicht in der Konfigurationsdatei:  
  
```  
Setup.exe /SQLSVCPASSWORD="************" /AGTSVCPASSWORD="************" /ASSVCPASSWORD="************" /ISSVCPASSWORD="************" /RSSVCPASSWORD="************" /ConfigurationFile=MyConfigurationFile.INI  
```  
  
## Siehe auch  
 [Installieren von SQL Server 2016 von der Eingabeaufforderung](../../database-engine/install-windows/install-sql-server-2016-from-the-command-prompt.md)   
 [SQL Server-Failoverclusterinstallation](../../sql-server/failover-clusters/install/sql-server-failover-cluster-installation.md)   
 [Aktualisieren einer SQL Server-Failoverclusterinstanz](../../sql-server/failover-clusters/windows/upgrade-a-sql-server-failover-cluster-instance.md)  
  
  