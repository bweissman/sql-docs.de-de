---
title: "Browserunterst&#252;tzung f&#252;r Reporting Services und Power View | Microsoft Docs"
ms.custom: 
  - "SQL2016_New_Updated"
ms.date: "03/30/2017"
ms.prod: "sql-server-2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "reporting-services-sharepoint"
  - "reporting-services-native"
ms.tgt_pltfrm: ""
ms.topic: "get-started-article"
helpviewer_keywords: 
  - "displaying reports"
  - "scripts [Reporting Services], requirements"
  - "viewing reports"
  - "browsers [Reporting Services]"
  - "Web browsers [Reporting Services], about browser support"
  - "browsing reports [Reporting Services]"
  - "components [Reporting Services], browsers"
  - "Web browsers [Reporting Services]"
ms.assetid: 48a75bbb-0029-4c43-891d-dc8f4fc0ebe1
caps.latest.revision: 121
author: "guyinacube"
ms.author: "asaxton"
manager: "erikre"
caps.handback.revision: 121
---
# Browserunterst&#252;tzung f&#252;r Reporting Services und Power View
[!INCLUDE[feedback_stackoverflow_msdn_connect_md](../includes/feedback-stackoverflow-msdn-connect-md.md)]

Erfahren Sie, welche Browserversionen zum Verwalten und Anzeigen von [!INCLUDE[ssCurrent](../includes/sscurrent-md.md)] [!INCLUDE[ssRSnoversion](../includes/ssrsnoversion-md.md)], der ReportViewer-Steuerelemente und Power View unterstützt werden.
  
 **Gilt für:** [!INCLUDE[ssRSnoversion](../includes/ssrsnoversion-md.md)] nativer Modus | [!INCLUDE[ssRSnoversion](../includes/ssrsnoversion-md.md)] SharePoint-Modus  
  
##  <a name="bkmk_webportal"></a> Browseranforderungen für das [!INCLUDE[ssRSWebPortal](../includes/ssrswebportal.md)]

Im Folgenden finden Sie die aktuelle Liste der unterstützten Browser für das [!INCLUDE[ssRSWebPortal](../includes/ssrswebportal.md)].

**Microsoft Windows**  
*Windows 7, 8.1, 10; Windows Server 2008 R2, 2012, 2012 R2*
- Microsoft Edge (+)
- Microsoft Internet Explorer 10 oder 11
- Google Chrome (+)
- Mozilla Firefox (+)

**Apple OS X**  
*OS X 10.9-10.11*

- Apple Safari (+)
- Google Chrome (+)
- Mozilla Firefox (+)

**Apple iOS**  
*iPhone und iPad mit iOS 9*

- Apple Safari (+)

**Google Android**  
*Smartphones und Tablets mit Android 4.4 (KitKat) oder höher*

- Google Chrome (+)

 **(+)** neueste öffentlich freigegebene Version  
  
##  <a name="bkmk_reportviewer"></a> Browseranforderungen für das ReportViewer-Websteuerelement (2015) 
 Im Folgenden finden Sie die aktuelle Liste der Browser, die mit dem ReportViewer-Websteuerelement (2015) unterstützt werden. Der Berichts-Viewer unterstützt die Anzeige von Berichten vom [!INCLUDE[ssRSnoversion](../includes/ssrsnoversion-md.md)]-Webportal und von den SharePoint-Bibliotheken.  
  
**Microsoft Windows**  
*Windows 7, 8.1, 10; Windows Server 2008 R2, 2012, 2012 R2*

- Microsoft Edge (+)
- Microsoft Internet Explorer 10 oder 11
- Google Chrome (+)
- Mozilla Firefox (+)

**Apple OS X**  
*OS X 10.9-10.11*

- Apple Safari (+)
  
 **(+)** neueste öffentlich freigegebene Version  
  
 Informationen bei Verwendung eines SharePoint-Produkts, das in [!INCLUDE[ssRSnoversion](../includes/ssrsnoversion-md.md)] integriert ist, finden Sie unter [Planen der Browserunterstützung in SharePoint 2016](http://technet.microsoft.com//library/cc263526\(v=office.16\).aspx).  
  
###  <a name="bkmk_authentication"></a> Authentifizierungsanforderungen  
 Browser unterstützen spezifische Authentifizierungsschemas, die vom Berichtsserver verarbeitet werden müssen, damit die Clientanforderung nicht fehlschlägt. In der folgenden Tabelle sind die Standardauthentifizierungstypen angegeben, die von den einzelnen unter einem Windows-Betriebssystem ausgeführten Browsern unterstützt werden.  
  
|**Browsertyp**|**Unterstützt**|**Browserstandard**|**Serverstandard**|  
|----------------------|------------------|-------------------------|------------------------|  
|**Microsoft Edge** (+)|Negotiate, Kerberos, NTLM, Basic|Aushandeln|Ja. Die Standardauthentifizierungseinstellungen können mit Edge verwendet werden.|  
|**Microsoft Internet Explorer**|Negotiate, Kerberos, NTLM, Basic|Aushandeln|Ja. Die Standardauthentifizierungseinstellungen können mit Internet Explorer verwendet werden.|  
|**Google Chrome**(+)|Negotiate, NTLM, Basic|Aushandeln|Ja. Die Standardauthentifizierungseinstellungen können mit Chrome verwendet werden.|  
|**Mozilla Firefox**(+)|NTLM, Standard|NTLM|Ja. Die Standardauthentifizierungseinstellungen können mit Firefox verwendet werden.|  
|**Apple Safari**(+)|NTLM, Standard|Standard|Ja. Die Standardauthentifizierungseinstellungen können mit Safari verwendet werden.|  
  
 **(+)** neueste öffentlich freigegebene Version  
  
### Skriptanforderungen zum Anzeigen von Berichten  
 Um den Berichts-Viewer zu verwenden, konfigurieren Sie den Browser für die Ausführung von Skripts.  
  
 Wenn die Skripterstellung nicht aktiviert ist, wird beim Öffnen eines Berichts eine Fehlermeldung ähnlich der folgenden angezeigt:  
  
-   **Der Browser unterstützt keine Skripts oder ist so konfiguriert, dass die Ausführung von Skripts nicht zulässig ist. Klicken Sie hier, um den Bericht ohne Skripts anzuzeigen**.  
  
 Wenn Sie den Bericht ohne Skriptunterstützung anzeigen, wird der Bericht ohne Funktionen des Berichts-Viewers, wie z. B. die Berichtssymbolleiste oder die Dokumentstruktur, in HTML gerendert.  
  
> [!NOTE]  
>  Die Berichtssymbolleiste ist Teil der HTML-Viewerkomponente. Die Symbolleiste wird standardmäßig oberhalb der jeweiligen in einem Browserfenster gerenderten Berichte angezeigt. Der Berichts-Viewer stellt Funktionen bereit, mit denen Sie den Bericht nach Informationen durchsuchen, einen Bildlauf zu einer bestimmten Seite durchführen und die Seitengröße aus Darstellungsgründen anpassen können. Weitere Informationen zur Berichtssymbolleiste oder zum HTML-Viewer finden Sie unter [HTML Viewer and the Report Toolbar](../reporting-services/html-viewer-and-the-report-toolbar.md).  
  
##  <a name="bkmk_controls"></a> Browserunterstützung für ReportViewer-Webserversteuerelemente in Visual Studio  
 Das ReportViewer-Webserversteuerelement wird verwendet, um Berichtsfunktionen in eine ASP.NET-Webanwendung einzubetten. Die Steuerelemente sind in Visual Studio enthalten und unterstützen andere Browser und Browserversionen als die anderen in diesem Thema beschriebenen Komponenten. Der Browsertyp, mit dem die Anwendung angezeigt wird, bestimmt die Art der ReportViewer-Funktionalität, die Sie in der Anwendung bereitstellen können. Ermitteln Sie mithilfe der Tabelle in diesem Thema, welche der unterstützten Browser Einschränkungen bei den Berichtsfunktionen unterliegen und welche Plattformen unterstützt werden.  
  
 Verwenden Sie einen Browser, in dem die Skriptunterstützung aktiviert ist. Wenn der Browser keine Skripts ausführen kann, können Sie den Bericht nicht anzeigen.  
  
**Microsoft Windows**  
*Windows 7, 8.1, 10; Windows Server 2008 R2, 2012, 2012 R2*

- Microsoft Edge (+)
- Microsoft Internet Explorer 10 oder 11
- Google Chrome (+)
- Mozilla Firefox (+)
  
 **(+)** neueste öffentlich freigegebene Version  
  
##  <a name="bkmk_powerview"></a> Power View-Browserunterstützung  

**Microsoft Windows**  
*Windows 7, 8.1, 10; Windows Server 2008 R2, 2012, 2012 R2*

- Microsoft Internet Explorer 10 oder 11
- Mozilla Firefox (+)
  
**Apple OS X**  
*OS X 10.9-10.11*

- Apple Safari (+)
  
 **(+)** neueste öffentlich freigegebene Version  
  
 Weitere Informationen zur SharePoint 2016-Browserunterstützung finden Sie unter [Planen der Browserunterstützung in SharePoint 2013](http://technet.microsoft.com//library/cc263526\(v=office.16\).aspx).  
  
## Siehe auch  
[Suchen und Anzeigen von Berichten im Web-Portal &#40;Berichts-Generator und SSRS&#41;](http://msdn.microsoft.com/de-de/8556807e-f2e2-4a7b-bb1b-ac5ea1872e51)  
[Reporting Services-Tools](../reporting-services/tools/reporting-services-tools.md)  
[Webportal (einheitlicher SSRS-Modus)](http://msdn.microsoft.com/de-de/7349e626-6ed5-4d21-b05f-cf042ad9ad70)  
[HTML-Viewer und die Berichtssymbolleiste](../reporting-services/html-viewer-and-the-report-toolbar.md)  
[URL-Zugriffsparameterverweis](../reporting-services/url-access-parameter-reference.md)  
[!INCLUDE[feedback_stackoverflow_msdn_connect_md](../includes/feedback-stackoverflow-msdn-connect-md.md)]