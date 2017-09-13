---
title: "Kommentare, Formen, andere Objekte, die von Excel Services nicht unterstützt | Microsoft Docs"
ms.custom: 
ms.date: 03/14/2017
ms.prod: sql-server-2016
ms.reviewer: 
ms.suite: 
ms.technology:
- analysis-services
ms.tgt_pltfrm: 
ms.topic: reference
ms.assetid: ade92e15-dfbf-496b-9378-a00bd83ba750
caps.latest.revision: 6
author: Minewiskan
ms.author: owend
manager: erikre
ms.translationtype: MT
ms.sourcegitcommit: 876522142756bca05416a1afff3cf10467f4c7f1
ms.openlocfilehash: bb73f60aea4a67a2e7fe7967dc9411762fe8e8f9
ms.contentlocale: de-de
ms.lasthandoff: 09/01/2017

---
# <a name="comments-shapes-other-objects-not-supported-by-excel-services"></a>Kommentare, Formen, andere Objekte, die von Excel Services nicht unterstützt.
  Dieser Fehler tritt auf, wenn Sie einer [!INCLUDE[ssGemini](../../includes/ssgemini-md.md)] -Arbeitsmappe Slicer aus einer [!INCLUDE[ssGemini](../../includes/ssgemini-md.md)] -Feldliste hinzufügen.  
  
## <a name="details"></a>Details  
  
|||  
|-|-|  
|Gilt für|[!INCLUDE[ssGemini](../../includes/ssgemini-md.md)] für SharePoint|  
|Produktversion|[!INCLUDE[ssKilimanjaro](../../includes/sskilimanjaro-md.md)], [!INCLUDE[ssSQL11](../../includes/sssql11-md.md)], [!INCLUDE[ssSQL14](../../includes/sssql14-md.md)]|  
|Ursache|Das Shape-Objekt, mit dem die Positionierung und Formatierung von Slicern gesteuert wird, die einer Arbeitsmappe aus der [!INCLUDE[ssGemini](../../includes/ssgemini-md.md)] -Feldliste hinzugefügt wurden, kann von Excel Web Access nicht gerendert werden.|  
|Meldungstext|Die folgenden Funktionen werden von Excel Services nicht unterstützt und möglicherweise nur teilweise oder überhaupt nicht angezeigt:<br /><br /> Kommentare, Formen oder andere Objekte<br /><br /> Einige Funktionen z. B. externe Datenabfragen, zeigen zwischengespeicherte Daten an, die nur in Microsoft Excel aktualisiert werden können.|  
  
## <a name="explanation"></a>Erklärung  
 Excel Web Access zeigt diesen Fehler an, wenn Sie eine [!INCLUDE[ssGemini](../../includes/ssgemini-md.md)] -Arbeitsmappe in einem Browser öffnen und in der Meldung **Nicht unterstützte Features. Möglicherweise wird die Arbeitsmappe nicht wie vorgesehen angezeigt** auf die Schaltfläche **Details**klicken.  
  
 Dieser Fehler tritt auf, weil die [!INCLUDE[ssGemini](../../includes/ssgemini-md.md)] -Arbeitsmappe Slicer enthält, deren Layout über ein ausgeblendetes Shape-Objekt in Excel gesteuert wird. Das Shape-Objekt steuert die Formatierung und Positionierung der Slicer in horizontalen und vertikalen Platzierungen.  
  
 Shape-Objekte können von Excel Services nicht gerendert werden, dies ist jedoch kein Problem, weil es sich um ein ausgeblendetes Objekt handelt.  
  
## <a name="user-action"></a>Benutzeraktion  
 Dieser Fehler kann ignoriert werden. Klicken Sie auf **OK** , um die Fehlermeldung zu schließen und die Verwendung von Arbeitsmappe und Slicern ohne Probleme fortzusetzen.  
  
  