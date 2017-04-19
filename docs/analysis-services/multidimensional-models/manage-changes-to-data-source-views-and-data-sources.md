---
title: "Verwalten von &#196;nderungen an Datenquellensichten und Datenquellen | Microsoft Docs"
ms.custom: ""
ms.date: "03/01/2017"
ms.prod: "sql-server-2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "analysis-services"
  - "analysis-services/multidimensional-tabular"
  - "analysis-services/data-mining"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "Ändern von Datenquellen"
  - "Ändern von Datenquellensichten"
  - "Datenquellenansichten [Analysis Services], Schemaaktualisierungen"
  - "Datenquellen [Analysis Services], Schemaaktualisierungen"
ms.assetid: 928c9f63-365a-43fd-9bbd-78828cc7e54d
caps.latest.revision: 25
author: "Minewiskan"
ms.author: "owend"
manager: "erikre"
caps.handback.revision: 25
---
# Verwalten von &#196;nderungen an Datenquellensichten und Datenquellen
  Wird der Schemagenerierungs-Assistent erneut ausgeführt, verwendet er dieselbe Datenquelle und Datenquellensicht wie für die ursprüngliche Generierung. Wenn Sie eine Datenquelle oder Datenquellensicht hinzufügen, wird diese vom Assistenten nicht verwendet. Wenn Sie die ursprüngliche Datenquelle oder Datenquellensicht nach der Anfangsgenerierung löschen, müssen Sie den Assistenten von Anfang an ausführen. Alle bisherigen Einstellungen im Assistenten werden ebenfalls gelöscht. Alle vorhandenen Objekte in einer zugrunde liegenden Datenbank, die mit einer gelöschten Datenquelle oder Datenquellensicht verbunden waren, werden bei dem nächsten Ausführen des Schemagenerierungs-Assistenten als vom Benutzer erstellte Objekte behandelt.  
  
 Gibt die Datenquellensicht nicht den tatsächlichen Status der zugrunde liegenden Datenbank zum Zeitpunkt der Generierung wieder, ist es möglich, dass bei der Generierung des Schemas für die Themenbereichsdatenbank durch den Schemagenerierungs-Assistenten Fehler auftreten. Wenn die Datenquellensicht beispielsweise angibt, dass der Datentyp einer Spalte **int**ist, der Datentyp der Spalte tatsächlich aber auf **string**festgelegt wurde, legt der Schemagenerierungs-Assistent den Datentyp für den Fremdschlüssel in Übereinstimmung mit der Datenquellensicht auf **INT** fest und erzeugt dann beim Erstellen der Beziehung einen Fehler, da der tatsächliche Datentyp **string**ist.  
  
 Wenn Sie allerdings die Datenquellen-Verbindungszeichenfolge auf eine andere Datenbank aus der vorherigen Generierung ändern, wird kein Fehler generiert. Es wird die neue Datenbank verwendet und keine Änderung an der vorherigen Datenbank vorgenommen.  
  
## Siehe auch  
 [Grundlegendes zur inkrementellen Generierung](../../analysis-services/multidimensional-models/understanding-incremental-generation.md)  
  
  