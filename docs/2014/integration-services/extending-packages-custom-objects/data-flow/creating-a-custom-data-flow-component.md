---
title: Erstellen einer benutzerdefinierten Datenflusskomponente | Microsoft-Dokumentation
ms.custom: ''
ms.date: 03/09/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology:
- docset-sql-devref
- integration-services
ms.tgt_pltfrm: ''
ms.topic: reference
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- design-time component interface [Integration Services]
- custom data flow components [Integration Services], about data flow components
- custom data flow components [Integration Services]
- data flow components [Integration Services]
- data flow components [Integration Services], developing
ms.assetid: 9d96bcf5-eba8-44bd-b113-ed51ad0d0521
caps.latest.revision: 26
author: douglaslMS
ms.author: douglasl
manager: craigg
ms.openlocfilehash: 5662a410ef85dc5df64abfd5d84c13bc7a37264c
ms.sourcegitcommit: c18fadce27f330e1d4f36549414e5c84ba2f46c2
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 07/02/2018
ms.locfileid: "37331840"
---
# <a name="creating-a-custom-data-flow-component"></a>Erstellen einer benutzerdefinierten Datenflusskomponente
  In [!INCLUDE[msCoName](../../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] [!INCLUDE[ssISnoversion](../../../includes/ssisnoversion-md.md)] stellt der Datenflusstask ein Objektmodell zur Verfügung, das Entwicklern das Erstellen von benutzerdefinierten Datenflusskomponenten (Quellen, Transformationen und Ziele) anhand von [!INCLUDE[msCoName](../../../includes/msconame-md.md)] [!INCLUDE[dnprdnshort](../../../includes/dnprdnshort-md.md)] und verwaltetem Code ermöglicht.  
  
 Ein Datenflusstask besteht aus Komponenten, die eine <xref:Microsoft.SqlServer.Dts.Pipeline.Wrapper.IDTSComponentMetaData100>-Schnittstelle und eine Auflistung von <xref:Microsoft.SqlServer.Dts.Pipeline.Wrapper.IDTSPath100>-Objekten enthalten, die die Verschiebung von Daten zwischen Komponenten definieren.  
  
> [!NOTE]  
>  Wenn Sie einen benutzerdefinierten Anbieter erstellen, müssen Sie die Datei "ProviderDescriptors.xml" mit den Metadatenspaltenwerten aktualisieren.  
  
## <a name="design-time-and-run-time"></a>Entwurfszeit und Laufzeit  
 Vor der Ausführung befindet sich der Datenflusstask im so genannten Entwurfszeitstatus, während er inkrementelle Änderungen durchläuft. Zu den Änderungen kann das Hinzufügen oder Entfernen von Komponenten, das Hinzufügen oder Entfernen von Pfadobjekten zur Verbindung von Komponenten sowie Änderungen an den Metadaten der Komponenten gehören. Wenn Metadaten-Änderungen auftreten, kann die Komponente die Änderungen überwachen und darauf reagieren. Zum Beispiel kann eine Komponente bestimmte Änderungen nicht zulassen oder zusätzliche Änderungen als Reaktion auf eine Änderung vornehmen. Zur Entwurfszeit interagiert der Designer mit einer Komponente durch die Entwurfszeitschnittstelle <xref:Microsoft.SqlServer.Dts.Pipeline.Wrapper.IDTSDesigntimeComponent100>.  
  
 Zur Ausführungszeit wird vom Datenflusstask die Reihenfolge von Komponenten überprüft, ein Ausführungsplan vorbereitet und ein Pool von Arbeitsthreads verwaltet, die den Arbeitsplan ausführen. Auch wenn jeder Arbeitsthread einige interne Arbeiten im Datenflusstask ausführt, besteht die Hauptaufgabe des Arbeitsthread darin, die Methoden der Komponenten über die Laufzeitschnittstelle <xref:Microsoft.SqlServer.Dts.Pipeline.Wrapper.IDTSRuntimeComponent100> aufzurufen.  
  
## <a name="creating-a-component"></a>Erstellen einer Komponente  
 Zum Erstellen einer Datenflusskomponente leiten Sie eine Klasse von der <xref:Microsoft.SqlServer.Dts.Pipeline.PipelineComponent>-Basisklasse ab, wenden die <xref:Microsoft.SqlServer.Dts.Pipeline.DtsPipelineComponentAttribute>-Klasse an und überschreiben dann die entsprechenden Methoden der Basisklasse. Mit <xref:Microsoft.SqlServer.Dts.Pipeline.PipelineComponent> werden die Schnittstellen <xref:Microsoft.SqlServer.Dts.Pipeline.Wrapper.IDTSDesigntimeComponent100> und <xref:Microsoft.SqlServer.Dts.Pipeline.Wrapper.IDTSRuntimeComponent100> implementiert und die Methoden zum Überschreiben in der Komponente zur Verfügung gestellt.  
  
 Abhängig von den in der Komponente verwendeten Objekten erfordert Ihr Projekt Verweise auf einige oder alle der folgenden Assemblys:  
  
|Funktion|Verweis auf Assembly|Zu importierender Namespace|  
|-------------|---------------------------|-------------------------|  
|Datenfluss|Microsoft.SqlServer.PipelineHost|<xref:Microsoft.SqlServer.Dts.Pipeline>|  
|Datenfluss-Wrapper|Microsoft.SqlServer.DTSPipelineWrap|<xref:Microsoft.SqlServer.Dts.Pipeline.Wrapper>|  
|Typ|Microsoft.SQLServer.ManagedDTS|<xref:Microsoft.SqlServer.Dts.Runtime>|  
|Laufzeit-Wrapper|Microsoft.SqlServer.DTSRuntimeWrap|<xref:Microsoft.SqlServer.Dts.Runtime.Wrapper>|  
  
 Im folgenden Codebeispiel werden eine einfache, von der Basisklasse abgeleitete Komponente veranschaulicht und <xref:Microsoft.SqlServer.Dts.Pipeline.DtsPipelineComponentAttribute> angewendet. Sie müssen einen Verweis auf die DTSPipelineWrap-Assembly hinzufügen.  
  
```csharp  
using System;  
using Microsoft.SqlServer.Dts.Pipeline;  
using Microsoft.SqlServer.Dts.Pipeline.Wrapper;  
  
namespace Microsoft.Samples.SqlServer.Dts  
{  
    [DtsPipelineComponent(DisplayName = "SampleComponent", ComponentType = ComponentType.Transform )]  
    public class BasicComponent: PipelineComponent  
    {  
        // TODO: Override the base class methods.  
    }  
}  
```  
  
```vb  
Imports Microsoft.SqlServer.Dts.Pipeline  
Imports Microsoft.SqlServer.Dts.Pipeline.Wrapper  
  
<DtsPipelineComponent(DisplayName:="SampleComponent", ComponentType:=ComponentType.Transform)> _  
Public Class BasicComponent  
  
    Inherits PipelineComponent  
  
    ' TODO: Override the base class methods.  
  
End Class  
```  
  
![Integration Services (kleines Symbol)](../../media/dts-16.gif "Integration Services (kleines Symbol)")**bleiben oben, um das Datum mit Integration Services** <br /> Die neuesten Downloads, Artikel, Beispiele und Videos von Microsoft sowie ausgewählte Lösungen aus der Community finden Sie auf MSDN auf der [!INCLUDE[ssISnoversion](../../../includes/ssisnoversion-md.md)] -Seite:<br /><br /> [Besuchen Sie die Integration Services-Seite auf MSDN](http://go.microsoft.com/fwlink/?LinkId=136655)<br /><br /> Abonnieren Sie die auf der Seite verfügbaren RSS-Feeds, um automatische Benachrichtigungen zu diesen Updates zu erhalten.  
  
## <a name="see-also"></a>Siehe auch  
 [Entwickeln einer Benutzeroberfläche für eine Datenflusskomponente](developing-a-user-interface-for-a-data-flow-component.md)  
  
  