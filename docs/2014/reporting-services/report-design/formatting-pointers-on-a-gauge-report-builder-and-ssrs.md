---
title: Formatieren von Zeigern auf einem Messgerät (Berichts-Generator und SSRS) | Microsoft-Dokumentation
ms.custom: ''
ms.date: 04/27/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology:
- reporting-services-native
ms.topic: conceptual
ms.assetid: 2fdf670a-5237-48fe-813d-97657c5c77d2
author: maggiesMSFT
ms.author: maggies
manager: craigg
ms.openlocfilehash: 625aa7736ba6cc9ac4b1b77a65c0be31688d1e37
ms.sourcegitcommit: 3da2edf82763852cff6772a1a282ace3034b4936
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 10/02/2018
ms.locfileid: "48183190"
---
# <a name="formatting-pointers-on-a-gauge-report-builder-and-ssrs"></a>Formatieren von Zeigern auf einem Messgerät (Berichts-Generator und SSRS)
  Ein Messgerätzeiger gibt den aktuellen Wert des Messgeräts an. Standardmäßig werden beim Hinzufügen eines Felds die darin enthaltenen Werte zu einem Wert aggregiert, der vom Zeiger auf dem Messgerät angezeigt wird. Sie können dem Messgerät mehrere Zeiger hinzufügen, die auf unterschiedliche Werte auf der gleichen Skala zeigen, oder Sie können mehrere Skalen und einen Zeiger für jede hinzugefügte Skala hinzufügen. Nachdem Sie einem Messgerät ein Feld hinzugefügt haben, müssen Sie den maximalen und den minimalen Wert für die entsprechende Skala festlegen, um einen Kontext zum Zeigerwert anzugeben. Sie haben auch die Möglichkeit, den minimalen und den maximalen Wert für einen Bereich festzulegen, wodurch auf der Skala ein kritischer Bereich angegeben wird.  
  
 Sie können die Darstellungseigenschaften für den Zeiger festlegen, indem Sie mit der rechten Maustaste auf den Zeiger klicken und die Option **Radiale Zeigereigenschaften** oder **Lineare Zeigereigenschaften**auswählen. Jeder Messgerätzeiger enthält denselben Eigenschaftensatz. Darüber hinaus sind jedoch auch entsprechende Darstellungseigenschaften vorhanden, die für die einzelnen Messgerättypen spezifisch sind:  
  
-   Auf einem radialen Messgerät können Sie einen Nadelzeiger und eine Nadelabdeckung angeben.  
  
-   Auf einem linearen Messgerät können Sie einen Thermometerzeiger angeben, der eine Variation des Balkenzeigers darstellt. Beim Thermometerzeiger können Sie die Form der Thermometeranzeige angeben.  
  
> [!NOTE]  
>  [!INCLUDE[ssRBRDDup](../../includes/ssrbrddup-md.md)]  
  
##  <a name="HowPointer"></a> Verbinden des Zeigers mit Daten  
 Standardmäßig enthält ein hinzugefügtes Messgerät einen Zeiger ohne zugeordnetes Feld. Dieser wird als leerer Zeiger bezeichnet. Er zeigt 0 (null) an, bis dem Datenbereich ein Feld hinzugefügt wird. Wenn Sie dem Datenbereich ein Feld hinzufügen, wird der Zeiger mit diesem Feld verbunden. Wenn Sie ein Feld aus dem Datenbereich löschen, wird auch der Zeiger gelöscht, der dem betreffenden Feld zugeordnet ist.  
  
 Wenn Sie nach dem Hinzufügen von Daten mit der rechten Maustaste auf den Zeiger klicken, werden die Optionen **Zeigerwert löschen** und **Zeiger löschen** angezeigt. Mit der Option **Zeigerwert löschen** wird das an das Messgerät angefügte Feld entfernt, der Zeiger wird jedoch für das Messgerät weiterhin angezeigt. Mit der Option **Zeiger löschen** wird das Feld aus dem Messgerät entfernt, und der angezeigte Zeiger wird ebenfalls gelöscht. Wenn Sie dem Messgerät wieder ein Feld hinzufügen, wird der Standardzeiger erneut angezeigt werden. Beim Festlegen des Zeigers **Hidden** Eigenschaft `True`, der Zeiger wird nicht auf der Entwurfsoberfläche, sondern zur Laufzeit ausgeblendet.  
  
  
##  <a name="DisplayingMultiple"></a> Anzeigen von mehreren Zeigern auf dem Messgerät  
 Sie können dem Messgerät mehrere Zeiger hinzufügen, sodass auf der gleichen Skala auf unterschiedliche Werte gezeigt wird. Dies ermöglicht es Ihnen, gleichzeitig einen niedrigen und einen hohen Wert anzuzeigen. Wenn Sie auf dem Messgerät für die Skala mehrere Zeiger angeben möchten, klicken Sie auf eine beliebige Stelle auf dem Messgerät, und klicken Sie im Kontextmenü auf **Zeiger hinzufügen** . Sie können auch eine Skala hinzufügen, indem Sie mit der rechten Maustaste auf eine beliebige Stelle auf dem Messgerät klicken und anschließend auf **Skalierung hinzufügen**klicken. Anschließend können Sie einen neuen Zeiger hinzufügen, der automatisch der letzten Skala zugeordnet wird.  
  
 Wenn Zeiger einander überlappen, wird die Zeichnungsreihenfolge der Zeiger durch die Reihenfolge bestimmt, in der sie dem Messgerät hinzugefügt wurden. Sie können die Zeichnungsreihenfolge der Zeiger nicht ändern, indem Sie die Reihenfolge der Felder in Datenbereich ändern. Wenn Sie die Zeichnungsreihenfolge für mehrere Zeiger ändern möchten, öffnen Sie den Eigenschaftenbereich und klicken auf **Zeiger (…)**. Ändern Sie dann die Reihenfolge der Zeiger in der Pointer-Auflistung.  
  
  
##  <a name="SettingGradients"></a> Festlegen von Farbverläufen für eine Nadelabdeckung  
 Eine Nadelabdeckung, die über oder unter dem Zeiger gezeichnet werden kann, kann nur für ein radiales Messgerät angegeben werden. Alle Arten für Nadelabdeckungen werden mit integrierten Farbverläufen gezeichnet, die nicht geändert werden können. Die Ausnahme ist die `RoundedDark` Format, in dem Sie eine Verlaufsfarbe und die Art des Farbverlaufs angeben können.  
  
  
##  <a name="SettingSnappingInterval"></a> Festlegen eines Ausrichtungsintervalls  
 Durch das Ausrichtungsintervall wird das Vielfache festgelegt, auf das Werte gerundet werden. Standardmäßig zeigt das Messgerät auf den exakten Wert des Felds, das Sie im Datenbereich angegeben haben. Möglicherweise soll der exakte Wert jedoch nach oben oder unten gerundet werden, sodass der Zeiger an einem vordefinierten Intervall ausgerichtet wird. Beispiel: Wenn der Wert auf dem Messgerät 34,2 beträgt und Sie ein Ausrichtungsintervall von 5 festlegen, zeigt der Messgerätzeiger auf 35. Wenn der Wert auf dem Messgerät 31,2 beträgt und Sie ein Ausrichtungsintervall von 5 festlegen, zeigt der Messgerätzeiger auf 30. Weitere Informationen finden Sie unter [Festlegen eines Ausrichtungsintervalls auf einem Messgerät &#40;Berichts-Generator und SSRS&#41;](../set-a-snapping-interval-on-a-gauge-report-builder-and-ssrs.md).  
  
  
##  <a name="SpecifyingImage"></a> Festlegen eines Bilds als Zeiger auf einem radialen Messgerät  
 Neben der Auswahl aus der integrierten Liste von Zeigerstilen können Sie auch ein Bild als Zeiger angeben. Dies ist insbesondere dann effektiv, wenn Sie einen vorhandenen Nadelzeigerstil durch ein Bild ersetzen. Der Zeiger wird mit dem Bild überlagert, sämtliche Zeigerfunktionen bleiben jedoch erhalten. Farb- und Farbverlaufsoptionen sind nicht verfügbar, wenn ein Bild für den Zeiger verwendet wird.  
  
 Wenn das Bild für den Zeiger eine unregelmäßige Form aufweist, empfiehlt es sich, die Farbe als transparent festzulegen, sodass die Bereiche des Bilds ausgeblendet werden, die auf dem Messgerät nicht angezeigt werden sollen. Wenn Sie eine transparente Farbe definieren, überlagert das Messgerät den vorhandenen Zeiger mit dem Bild und beschneidet das Bild, sodass nur die Form des Zeigers angezeigt wird. Die Größe des Bilds wird vom Messgerät an die Größe des Zeigers angepasst. Wenn Sie für einen Zeiger ein Bild angeben, werden alle Zeiger, die dem Messgerät später hinzugefügt werden, unter diesem Bild gezeichnet. Deshalb empfiehlt es sich, kein Bild für den Zeiger anzugeben, wenn das Messgerät mehrere Zeiger aufweisen soll. Weitere Informationen finden Sie unter [Festlegen eines Bilds als Zeiger auf einem Messgerät &#40;Berichts-Generator und SSRS&#41;](../specify-an-image-as-a-pointer-on-a-gauge-report-builder-and-ssrs.md).  
  
  
## <a name="see-also"></a>Siehe auch  
 [Formatieren von Skalen auf einem Messgerät &#40;Berichts-Generator und SSRS&#41;](formatting-scales-on-a-gauge-report-builder-and-ssrs.md)   
 [Formatieren von Bereichen auf einem Messgerät &#40;Berichts-Generator und SSRS&#41;](formatting-ranges-on-a-gauge-report-builder-and-ssrs.md)   
 [Messgeräte &#40;Berichts-Generator und SSRS&#41;](gauges-report-builder-and-ssrs.md)  
  
  
