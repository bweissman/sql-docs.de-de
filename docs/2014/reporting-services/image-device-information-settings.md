---
title: Bildgerät-Informationseinstellungen | Microsoft-Dokumentation
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology:
- reporting-services-native
ms.topic: conceptual
helpviewer_keywords:
- images [Reporting Services], rendering
- device information settings [Reporting Services], IMAGE rendering
ms.assetid: edad9498-69f7-4726-8699-fa615f704dff
author: markingmyname
ms.author: maghan
manager: craigg
ms.openlocfilehash: 6737a32eb7597f8115a7ee6797bcf1aedbd006b8
ms.sourcegitcommit: 3da2edf82763852cff6772a1a282ace3034b4936
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 10/02/2018
ms.locfileid: "48220780"
---
# <a name="image-device-information-settings"></a>Geräteinformationseinstellungen für Bilder
  In der folgenden Tabelle sind die Geräteinformationseinstellungen zum Rendern in das Bildformat aufgeführt.  
  
|Einstellung|value|  
|-------------|-----------|  
|**Spalten**|Die für den Bericht gewünschte Anzahl der Spalten. Dieser Wert überschreibt die ursprünglichen Einstellungen des Berichts.|  
|**ColumnSpacing**|Der für den Bericht gewünschte Spaltenabstand. Dieser Wert überschreibt die ursprünglichen Einstellungen des Berichts.|  
|`DpiX`|Die horizontale Auflösung des Ausgabebilds. Der Standardwert ist **96** Gilt für `BMP`, `GIF`, `PNG`, und `TIFF` Ausgabeformate.|  
|`DpiY`|Die vertikale Auflösung des Ausgabebilds. Der Standardwert ist **96** Gilt für `BMP`, `GIF`, `PNG`, und `TIFF` Ausgabeformate.|  
|**EndPage**|Die letzte Seite des zu rendernden Berichts. Der Standardwert ist der Wert für `StartPage`.|  
|**MarginBottom**|Der für den Bericht gewünschte Wert für den unteren Rand in Zoll. Sie müssen eine ganze Zahl oder einen Dezimalwert gefolgt von "in" einschließen (z. B. `1in`). Dieser Wert überschreibt die ursprünglichen Einstellungen des Berichts.|  
|**MarginLeft**|Der für den Bericht gewünschte Wert für den linken Rand in Zoll. Sie müssen eine ganze Zahl oder einen Dezimalwert gefolgt von "in" einschließen (z. B. `1in`). Dieser Wert überschreibt die ursprünglichen Einstellungen des Berichts.|  
|**MarginRight**|Der für den Bericht gewünschte Wert für den rechten Rand in Zoll. Sie müssen eine ganze Zahl oder einen Dezimalwert gefolgt von "in" einschließen (z. B. `1in`). Dieser Wert überschreibt die ursprünglichen Einstellungen des Berichts.|  
|**MarginTop**|Der für den Bericht gewünschte Wert für den oberen Rand in Zoll. Sie müssen eine ganze Zahl oder einen Dezimalwert gefolgt von "in" einschließen (z. B. `1in`). Dieser Wert überschreibt die ursprünglichen Einstellungen des Berichts.|  
|**Ausgabeformat**|Eines der [!INCLUDE[ndptecgdiexpanded](../includes/ndptecgdiexpanded-md.md)] ([!INCLUDE[ndptecgdi](../includes/ndptecgdi-md.md)]) unterstützten Ausgabeformate: `BMP`, `EMF`, `GIF`, `JPEG`, `PNG`, oder `TIFF`.|  
|**PageHeight**|Die für den Bericht gewünschte Seitenhöhe in Zoll. Sie müssen eine ganze Zahl oder einen Dezimalwert gefolgt von "in" einschließen (z. B. `11in`). Dieser Wert überschreibt die ursprünglichen Einstellungen des Berichts.|  
|**PageWidth**|Die für den Bericht gewünschte Seitenbreite in Zoll. Sie müssen eine ganze Zahl oder einen Dezimalwert gefolgt von "in" einschließen (z. B. `8.5in`). Dieser Wert überschreibt die ursprünglichen Einstellungen des Berichts.|  
|**PrintDpiX**|Die horizontale Auflösung des Ausgabebilds. Der Standardwert lautet `300`. Gilt für die erweiterte Metadatei (`EMF`) Ausgabeformat.|  
|**PrintDpiY**|Die vertikale Auflösung des Ausgabebilds. Der Standardwert lautet `300`. Gilt für die erweiterte Metadatei (`EMF`) Ausgabeformat.|  
|`StartPage`|Die erste Seite des zu rendernden Berichts. Der Wert `0` gibt an, dass alle Seiten des Berichts gerendert werden. Der Standardwert lautet `1`.|  
  
## <a name="see-also"></a>Siehe auch  
 [Übergeben von Geräteinformationseinstellungen an Renderingerweiterungen](report-server-web-service/net-framework/passing-device-information-settings-to-rendering-extensions.md)   
 [Anpassen der Parameter für Renderingerweiterungen in der Datei „RSReportServer.config“](customize-rendering-extension-parameters-in-rsreportserver-config.md)   
 [Technische Referenz (SSRS)](../../2014/reporting-services/technical-reference-ssrs.md)  
  
  
