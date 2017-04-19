---
title: "Erstellen eines Datenattributs (Master Data Services) | Microsoft Docs"
ms.custom: 
  - "SQL2016_New_Updated"
ms.date: "03/15/2017"
ms.prod: "sql-server-2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "master-data-services"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "Erstellen von Datenattributen [Master Data Services]"
  - "Attribute [Master Data Services], Erstellen von Datenattributen"
ms.assetid: 22a8f1a3-b4f2-4cfa-8495-7daad5ce9d12
caps.latest.revision: 13
author: "sabotta"
ms.author: "carlasab"
manager: "jhubbard"
caps.handback.revision: 13
---
# Erstellen eines Datenattributs (Master Data Services)
  Erstellen Sie in [!INCLUDE[ssMDSshort](../includes/ssmdsshort-md.md)]ein Datumsattribut, wenn Sie möchten, dass Benutzer ein Datum als Attributwert eingeben.  
  
> [!NOTE]  
>  Das Attribut heißt DateTime, aber Zeitwerte werden nicht unterstützt.  
  
## Erforderliche Komponenten  
 So führen Sie diese Prozedur aus  
  
-   Sie müssen über die Berechtigung verfügen, auf den Funktionsbereich **Systemverwaltung** zuzugreifen.  
  
-   Sie müssen ein Modelladministrator sein. Weitere Informationen finden Sie unter [Administratoren &#40;Master Data Services&#41;](../master-data-services/administrators-master-data-services.md).  
  
-   Sie müssen eine Entität haben, für das Sie das Attribut erstellen. Weitere Informationen finden Sie unter [Erstellen einer Entität &#40;Master Data Services&#41;](../master-data-services/create-an-entity-master-data-services.md).  
  
### So erstellen Sie ein Datumsattribut  
  
1.  Klicken Sie in [!INCLUDE[ssMDSmdm](../includes/ssmdsmdm-md.md)]auf **Systemverwaltung**.  
  
2.  Wählen Sie auf der Seite **Modell verwalten** im Raster ein Modell aus, und klicken Sie dann auf **Entitäten**.  
  
3.  Wählen Sie auf der Seite **Entität verwalten** die Zeile der Entität aus, für die Sie ein Attribut erstellen möchten.  
  
4.  Klicken Sie auf **Attribute**.  
  
5.  Führen Sie auf der Seite **Attribute verwalten** einen der folgenden Schritte aus, und klicken Sie dann auf **Hinzufügen**.  
  
    -   Wenn das Attribut für Blattelemente bestimmt ist, wählen Sie **Blatt** im Listenfeld **Elementtypen** aus.  
  
    -   Wenn das Attribut für konsolidierte Elemente bestimmt ist, wählen Sie **Konsolidiert** im Listenfeld **Elementtypen** aus.  
  
    -   Wenn das Attribut für Sammlungen bestimmt ist, wählen Sie **Sammlung** im Listenfeld **Elementtypen** aus.  
  
6.  Geben Sie im Feld **Name** einen Namen für das Attribut ein. Eine Liste von Wörtern, die nicht als Attributnamen verwendet werden sollten, finden Sie unter [Reservierte Wörter &#40;Master Data Services&#41;](../master-data-services/reserved-words-master-data-services.md).  
  
7.  Geben Sie optional einen Anzeigenamen ein und in das Feld **Beschreibung** eine Beschreibung des Attributs ein.  
  
8.  Geben Sie im Feld **Pixelbreite anzeigen** die Breite der Attributspalte ein, die im **Explorerraster** angezeigt werden soll.  
  
9. Wählen Sie in der Liste **Attributtyp** die Option **Freiform** aus.  
  
10. Wählen Sie aus der Liste **Datentyp** die Option **DateTime**aus.  
  
11. Wählen Sie aus der Liste **Eingabeformat** ein Format für Datumsangaben aus.  
  
12. Optional können Sie **Änderungsnachverfolgung aktivieren** auswählen, um Änderungen an Gruppen von Attributen nachzuverfolgen. Weitere Informationen finden Sie unter [Hinzufügen von Attributen zu einer Änderungsnachverfolgungsgruppe &#40;Master Data Services&#41;](../master-data-services/add-attributes-to-a-change-tracking-group-master-data-services.md).  
  
13. Klicken Sie auf **Speichern**.  
  
## So zeigen Sie den Zeitbereich eines datetime-Werts an  
 Damit der Zeitbereich eines datetime-Werts in der Benutzeroberfläche angezeigt wird, müssen Sie ein geeignetes Eingabeformat für das Attribut auswählen. Da keine der integrierten Masken für Datetime-Attribute hierzu geeignet ist, können Sie eine neue Maske hinzufügen, die die Anzeige der Uhrzeit ermöglicht. Fügen Sie dazu der Tabelle mdm.tblList der MDS-Datenbank, in der integrierte Masken gespeichert werden, eine Zeile hinzu. Die Zeile sollte über die folgenden Werte verfügen:  
  
|||  
|-|-|  
|ListCode|lstInputMask|  
|ListName|Eingabeformat|  
|Seq|19|  
|List Option|dd/MM/yyyy hh:mm:ss tt|  
|Option ID|19|  
|Sichtbar|1|  
|Group_ID|3|  
  
 Nachdem Sie in die Tabelle mdm.tblList eine Zeile mit den oben angegebenen Werten eingegeben haben, steht im Listenfeld Eingabeformat die Maske "dd/MM/yyyy hh:mm:ss tt" zur Verfügung. Anschließend können Sie diese Maske auswählen, um das Datum und die Uhrzeit in einer datetime-Attributspalte einer Entität im MDS-Explorer anzuzeigen.  
  
 Die Input Mask ist eine benutzerdefinierte .NET DateTime-Formatzeichenfolge. Weitere Informationen finden Sie unter [Benutzerdefinierte Datums- und Uhrzeit-Formatzeichenfolgen](https://msdn.microsoft.com/en-us/library/8kb3ddd4\(v=vs.110\).aspx)  
  
## Siehe auch  
 [Attribute &#40;Master Data Services&#41;](../master-data-services/attributes-master-data-services.md)   
 [Ändern eines Attributnamens und Datentyps &#40;Master Data Services&#41;](../master-data-services/change-an-attribute-name-and-data-type-master-data-services.md)   
 [Erstellen eines domänenbasierten Attributs &#40;Master Data Services&#41;](../master-data-services/create-a-domain-based-attribute-master-data-services.md)   
 [Erstellen eines Dateiattributs &#40;Master Data Services&#41;](../master-data-services/create-a-file-attribute-master-data-services.md)  
  
  