---
title: "Ausf&#252;hren einer Vorschau f&#252;r Berichte | Microsoft Docs"
ms.custom: ""
ms.date: "05/05/2016"
ms.prod: "sql-server-2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "reporting-services-sharepoint"
  - "reporting-services-native"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "Berichts-Designer (Reporting Services), Vorschau von Berichten"
  - "Ausführen einer Vorschau für Berichte [Reporting Services]"
  - "Drucken einer Vorschau"
  - "Testserver [Reporting Services]"
ms.assetid: 85117f6c-828e-45c9-810f-e700d9bfba67
caps.latest.revision: 44
author: "guyinacube"
ms.author: "asaxton"
manager: "erikre"
caps.handback.revision: 44
---
# Ausf&#252;hren einer Vorschau f&#252;r Berichte
  Wenn Sie einen [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)]-Bericht entwerfen, möchten Sie ihn ggf. anzeigen, bevor Sie ihn in einer Produktionsumgebung veröffentlichen. Dazu gibt es mehrere Möglichkeiten: Sie können im Berichts-Designer in den Vorschaumodus wechseln, im Berichts-Designer das Vorschaufenster verwenden oder den Bericht auf einem Berichtsserver in einer Testumgebung veröffentlichen.  
  
> [!NOTE]  
>  Wenn Sie eine Vorschau für einen Bericht anzeigen, werden die Daten für den Bericht auf dem lokalen Computer in einer Datei zwischengespeichert. Wenn Sie für denselben Bericht erneut eine Vorschau anzeigen, indem Sie dieselbe Abfrage und dieselben Parameter und Anmeldeinformationen verwenden, ruft der Berichts-Designer die zwischengespeicherte Kopie ab, anstatt die Abfrage erneut auszuführen. Die Datendatei wird in demselben Verzeichnis wie die Berichtsdefinitionsdatei unter dem Namen „*\<Berichtsname>*.rdl.data“ gespeichert. Die Datei wird nicht gelöscht, wenn Sie den Berichts-Designer schließen.  
  
## Vorschaumodus  
 Sie zeigen die Vorschau eines Berichts im Berichts-Designer an, indem Sie auf ![ssrs_ssdt_preview](../../reporting-services/media/ssrs-ssdt-preview.png "ssrs_ssdt_preview") klicken. Dadurch wird der Bericht lokal mit derselben Berichtsverarbeitungs- und Renderingfunktionalität ausgeführt, die auf dem Berichtsserver zur Verfügung steht. Der Bericht wird als interaktives Bild angezeigt, in dem Sie Parameter auswählen, auf Links klicken, die Dokumentstruktur anzeigen und ausgeblendete Bereiche des Berichts erweitern bzw. reduzieren können. Darüber hinaus können Sie den Bericht in jedes installierte Renderingformat exportieren.  
  
## Eigenständige Vorschau  
 Sie können auch das Berichtsprojekt in einer Debugkonfiguration ausführen, um eine Vorschau des Berichts anzuzeigen, zum Beispiel zum Debuggen von benutzerdefinierten Assemblys, die Sie geschrieben haben. Der Bericht wird im Standardbrowser geöffnet. Ein Berichtsprojekt kann auf drei Arten ausgeführt werden:  
  
-   Durch Klicken im Menü **Debuggen** auf **Debuggen starten**.  
  
-   Durch Klicken auf der [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)]-Standardsymbolleiste von ![ssrs_ssdt_startdebug](../../reporting-services/reports/media/ssrs-ssdt-startdebug.png "ssrs_ssdt_startdebug") auf die Schaltfläche **Starten**.  
  
-   Durch Drücken von **F5**.  
  
 Falls Sie eine Projektkonfiguration verwenden, die zwar den Bericht erstellt, aber nicht bereitstellt, wird der in der **StartItem** -Eigenschaft angegebene Bericht der aktuellen Konfiguration in einem separaten Vorschaufenster geöffnet. Im Vorschaufenster wird der Bericht genauso und mit derselben Funktionalität angezeigt wie im Vorschaumodus.  
  
> [!NOTE]  
>  Vor dem Debuggen eines Berichts müssen Sie ein Startelement festlegen. Beispiel: Wenn Sie den Debugmodus ausführen und der Browser die Seite des Hauptberichtsservers und nicht Ihren Bericht im Vorschaumodus öffnet. Klicken Sie zum Festlegen eines Startelements im Projektmappen-Explorer mit der rechten Maustaste auf das Berichtsprojekt, klicken Sie auf **Eigenschaften**, und wählen Sie unter **StartItem** den Namen des anzuzeigenden Berichts aus.  
  
 Wenn Sie einen bestimmten Bericht in der Vorschau anzeigen möchten, der nicht als Startelement für das Projekt festgelegt ist, wählen Sie eine Konfiguration aus, die den Bericht zwar erstellt, jedoch nicht bereitstellt (z.B. die DebugLocal-Konfiguration). Klicken Sie dann mit der rechten Maustaste auf den Bericht, und klicken Sie anschließend auf **Ausführen**. Sie müssen eine Konfiguration auswählen, die den Bericht nicht bereitstellt. Andernfalls wird der Bericht auf dem Berichtsserver veröffentlicht und nicht lokal in einem Vorschaufenster angezeigt.  
  
## Veröffentlichen auf einem Testserver  
 Ferner können Sie Berichte auch testen, indem Sie sie auf einem Testserver veröffentlichen, zum Bericht wechseln und die Vorschau anzeigen. Das Veröffentlichen eines Berichts auf einem Testserver unterscheidet sich nicht vom Veröffentlichen auf einem Produktionsserver. Informationen zum Veröffentlichen eines Berichts finden Sie unter [Veröffentlichen von Berichten auf einem Berichtsserver](../../reporting-services/reports/publishing-reports-to-a-report-server.md).  
  
## Siehe auch  
 [Drucken von Berichten &#40;Berichts-Generator und SSRS&#41;](../../reporting-services/report-builder/print-reports-report-builder-and-ssrs.md)   
 [Drucken eines Berichts &#40;Berichts-Generator und SSRS&#41;](../../reporting-services/report-builder/print-a-report-report-builder-and-ssrs.md)   
 [Veröffentlichen von Berichten](../Topic/Publish%20Reports.md)   
 [Verwenden benutzerdefinierter Assemblys mit Berichten](../../reporting-services/custom-assemblies/using-custom-assemblies-with-reports.md)  
  
  