---
title: "Transformations-Editor f&#252;r &#220;berwachung | Microsoft Docs"
ms.custom: ""
ms.date: "03/01/2017"
ms.prod: "sql-server-2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "integration-services"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "sql13.dts.designer.audittransformation.f1"
helpviewer_keywords: 
  - "Transformations-Editor für Überwachung"
ms.assetid: 32786a34-5870-4fde-83c7-ec74d62404b8
caps.latest.revision: 13
author: "douglaslMS"
ms.author: "douglasl"
manager: "jhubbard"
caps.handback.revision: 13
---
# Transformations-Editor f&#252;r &#220;berwachung
  Mithilfe der Überwachungstransformation werden in den Datenfluss eines Pakets Daten zur Umgebung, in der das Paket ausgeführt wird, eingeschlossen. Dem Datenfluss kann z. B. der Name des Pakets, Computers und Operators hinzugefügt werden. [!INCLUDE[ssISnoversion](../../../includes/ssisnoversion-md.md)] enthält Systemvariablen, die diese Informationen bereitstellen.  
  
 Weitere Informationen zur Überwachungstransformation finden Sie unter [Audit Transformation](../../../integration-services/data-flow/transformations/audit-transformation.md).  
  
## enthalten  
 **Name der Ausgabespalte**  
 Geben Sie den Namen der neuen Ausgabespalte an, die die Überwachungsinformationen enthalten soll.  
  
 **Überwachungstyp**  
 Wählen Sie eine verfügbare Systemvariable zum Bereitstellen der Überwachungsinformationen aus.  
  
|Wert|Description|  
|-----------|-----------------|  
|**GUID der Ausführungsinstanz**|Fügen Sie die GUID ein, die die Ausführungsinstanz des Pakets eindeutig identifiziert.|  
|**Paket-ID**|Fügen Sie die GUID ein, die das Paket eindeutig identifiziert.|  
|**Paketname**|Fügen Sie den Paketnamen ein.|  
|**Versions-ID**|Fügen Sie die GUID ein, die die Paketversion eindeutig identifiziert.|  
|**Startzeit der Ausführung**|Fügen Sie den Zeitpunkt ein, zu dem mit der Ausführung des Pakets begonnen wird.|  
|**Computername**|Fügen Sie den Namen des Computers ein, auf dem das Paket gestartet wurde.|  
|**Benutzername**|Fügen Sie den Anmeldenamen des Benutzers ein, der das Paket gestartet hat.|  
|**Taskname**|Fügen Sie den Namen von dem Datenflusstask ein, mit dem die Überwachungstransformation verknüpft ist.|  
|**Task-ID**|Fügen Sie die GUID ein, die den mit der Überwachungstransformation verknüpften Datenflusstask eindeutig identifiziert.|  
  
## Siehe auch  
 [Fehler- und Meldungsreferenz von Integration Services](../../../integration-services/integration-services-error-and-message-reference.md)  
  
  