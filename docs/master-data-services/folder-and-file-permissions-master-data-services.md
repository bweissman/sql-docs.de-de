---
title: "Ordner- und Dateiberechtigungen (Master Data Services) | Microsoft Docs"
ms.custom: ""
ms.date: "03/14/2017"
ms.prod: "sql-server-2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "master-data-services"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "Sicherheit [Master Data Services], Datei- und Ordner-"
  - "Ordner [Master Data Services]"
  - "Dateien [Master Data Services]"
ms.assetid: 6402d81d-7349-47b1-95ca-99b0c0f4f373
caps.latest.revision: 10
author: "sabotta"
ms.author: "carlasab"
manager: "jhubbard"
caps.handback.revision: 10
---
# Ordner- und Dateiberechtigungen (Master Data Services)
  Bei der Installation von [!INCLUDE[ssMDSshort](../includes/ssmdsshort-md.md)]werden Ordner und Dateien im Dateisystem in dem Installationspfad installiert, der für freigegebenen Funktionen von [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] festgelegt wurde. Wenn Sie den Standardinstallationspfad für freigegebene Funktionen von [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] verwenden, lautet der Installationspfad für [!INCLUDE[ssMDSshort](../includes/ssmdsshort-md.md)] wie folgt: *Laufwerk*:\Programme\Microsoft SQL Server\130\Master Data Services. Sie können den Installationspfad für freigegebene Funktionen ändern; achten Sie dabei jedoch auf Berechtigungen, die vom übergeordneten Ordner geerbt werden, und auf explizit für [!INCLUDE[ssMDSshort](../includes/ssmdsshort-md.md)]festgelegte Berechtigungen.  
  
## Geerbte Berechtigungen  
 Der Order **Microsoft SQL Server** , der Ordner **Master Data Services** und die meisten Unterordner und Dateien erben Berechtigungen vom übergeordneten Ordner, der bei der Installation von [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] angegeben wurde. Bei Auswahl des Standardinstallationspfads lautet der übergeordnete Ordner, von dem Berechtigungen geerbt werden, *Laufwerk*:\Programme. In der folgenden Tabelle werden die Standardberechtigungen für den Ordner **Programme**beschrieben.  
  
> [!NOTE]  
>  Wenn Sie die Standardberechtigungen für den Ordner **Programme** ändern oder einen anderen Installationspfad auswählen, erben die [!INCLUDE[ssMDSshort](../includes/ssmdsshort-md.md)]-Ordner und -Dateien Berechtigungen von dem jeweils übergeordneten Ordner, d.h. die Berechtigungen können sich von denen in der nachfolgenden Tabelle unterscheiden.  
  
###### Standardberechtigungen im Ordner Programme  
  
|Gruppen- oder Kontoname|Berechtigungen|  
|---------------------------|-----------------|  
|CREATOR OWNER|Spezielle Berechtigungen|  
|SYSTEM|Spezielle Berechtigungen|  
|Administratoren|Spezielle Berechtigungen|  
|Benutzer|Lesen & Ausführen, Ordnerinhalt auflisten, Lesen|  
|TrustedInstaller|Ordnerinhalt auflisten, Spezielle Berechtigungen|  
  
## Explizite Berechtigungen  
 Der Ordner **MDSTempDir** und die Datei Web.config von [!INCLUDE[ssMDSshort](../includes/ssmdsshort-md.md)] (im Ordner **WebApplication**) erben keine Berechtigungen. Sie verfügen über Berechtigungen, die bei der Installation von [!INCLUDE[ssMDSshort](../includes/ssmdsshort-md.md)]explizit festgelegt werden und vom ausgewählten Installationspfad unabhängig sind. Ändern Sie diese Berechtigungen nicht.  
  
###### Berechtigungen im Ordner "MDSTempDir"  
  
|Gruppen- oder Kontoname|Berechtigungen|  
|---------------------------|-----------------|  
|SYSTEM|Ändern, Lesen & Ausführen, Ordnerinhalt auflisten, Lesen, Schreiben|  
|Administratoren|Ändern, Lesen & Ausführen, Ordnerinhalt auflisten, Lesen, Schreiben|  
|MDS_ServiceAccounts|Ändern, Lesen & Ausführen, Ordnerinhalt auflisten, Lesen, Schreiben|  
  
###### Berechtigungen in der Datei "Web.config"  
  
|Gruppen- oder Kontoname|Berechtigungen|  
|---------------------------|-----------------|  
|SYSTEM|Vollzugriff, Ändern, Lesen & Ausführen, Lesen, Schreiben|  
|Administratoren|Vollzugriff, Ändern, Lesen & Ausführen, Lesen, Schreiben|  
|MDS_ServiceAccounts|Lesen & Ausführen, Lesen|  
  
 Weitere Informationen zu den Inhalten der Web.config-Datei von [!INCLUDE[ssMDSshort](../includes/ssmdsshort-md.md)] finden Sie unter [Webkonfigurationsreferenz &#40;Master Data Services&#41;](../master-data-services/web-configuration-reference-master-data-services.md).  
  
## Siehe auch  
 [Installieren von Master Data Services](../master-data-services/install-windows/install-master-data-services.md)  
  
  