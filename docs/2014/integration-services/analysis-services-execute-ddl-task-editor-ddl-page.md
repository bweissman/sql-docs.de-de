---
title: Analysis Services-Task DDL-Task-Editor (Seite DDL) | Microsoft-Dokumentation
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology:
- integration-services
ms.topic: conceptual
f1_keywords:
- sql12.dts.designer.asexecuteddltask.ddl.f1
helpviewer_keywords:
- Analysis Services Execute DDL Task Editor
ms.assetid: f21bf8d0-ec5f-4c18-9de0-8875addb927b
author: douglaslms
ms.author: douglasl
manager: craigg
ms.openlocfilehash: e8f07c94b986c697721188a50e2ec5d478ac0b1b
ms.sourcegitcommit: 7fe14c61083684dc576d88377e32e2fc315b7107
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 10/26/2018
ms.locfileid: "50146856"
---
# <a name="analysis-services-execute-ddl-task-editor-ddl-page"></a>Editor für den Analysis Services-Task 'DDL ausführen' (Seite DDL)
  Auf der Seite **DDL** des Dialogfelds **Editor für den Analysis Services-Task „DDL ausführen“** können Sie eine Verbindung mit einem [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)]-Projekt oder einer [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)]-Datenbank angeben sowie Informationen zur Quelle der DDL-Anweisungen (Data Definition Language) angeben.  
  
 Informationen, um sich mit diesem Thema vertraut zu machen, finden Sie unter [Analysis Services Execute DDL Task](control-flow/analysis-services-execute-ddl-task.md).  
  
## <a name="static-options"></a>Statische Optionen  
 **Verbindung**  
 Wählen Sie ein [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)]-Projekt oder einen [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)]-Verbindungs-Manager aus der Liste aus, oder klicken Sie auf \<**Neue Verbindung...**>, und erstellen Sie im Dialogfeld **Analysis Services-Verbindungs-Manager hinzufügen** eine neue Verbindung.  
  
 **Verwandte Themen:** [Referenz zur Benutzeroberfläche des Dialogfelds Analysis Services-Verbindungs-Manager hinzufügen](connection-manager/add-analysis-services-connection-manager-dialog-box-ui-reference.md), [Analysis Services-Verbindungs-Manager](connection-manager/analysis-services-connection-manager.md)  
  
 **SourceType**  
 Geben Sie den Quelltyp der DDL-Anweisung an. Für diese Eigenschaft sind die in der folgenden Tabelle aufgeführten Optionen verfügbar:  
  
|value|Description|  
|-----------|-----------------|  
|**Direct Input**|Legen Sie die Quelle der im Textfeld **SourceDirect** gespeicherten DDL-Anweisung fest. Wenn Sie diesen Wert auswählen, werden im folgenden Abschnitt die dynamischen Optionen angezeigt.|  
|**File Connection**|Legen Sie die Quelle für eine Datei fest, in der die DDL-Anweisung enthalten ist. Wenn Sie diesen Wert auswählen, werden im folgenden Abschnitt die dynamischen Optionen angezeigt.|  
|**Variable**|Legen Sie die Quelle für eine Variable fest. Wenn Sie diesen Wert auswählen, werden im folgenden Abschnitt die dynamischen Optionen angezeigt.|  
  
## <a name="dynamic-options"></a>Dynamische Optionen  
  
### <a name="sourcetype--direct-input"></a>SourceType = Direkteingabe  
 **Quelle**  
 Geben Sie die DDL-Anweisungen ein, oder klicken Sie auf die Schaltfläche mit den drei Punkten **(…)** , und geben Sie dann die Anweisungen im Dialogfeld **DDL-Anweisungen** ein.  
  
### <a name="sourcetype--file-connection"></a>SourceType = File Connection  
 **Quelle**  
 Wählen Sie eine Dateiverbindung aus der Liste aus, oder klicken Sie auf \<**Neue Verbindung...**>, und erstellen Sie im Dialogfeld **Dateiverbindungs-Manager** eine neue Verbindung.  
  
 **Verwandte Themen:** [Dateiverbindungs-Manager](connection-manager/file-connection-manager.md)  
  
### <a name="sourcetype--variable"></a>SourceType = Variable  
 **Quelle**  
 Wählen Sie eine Variable aus der Liste aus, oder klicken Sie auf \<**Neue Variable...**>, und erstellen Sie im Dialogfeld **Variable hinzufügen** eine neue Variable.  
  
 **Verwandte Themen:** [Integration Services-Variablen &#40;SSIS&#41;](integration-services-ssis-variables.md)  
  
## <a name="see-also"></a>Siehe auch  
 [Fehler- und Meldungsreferenz von Integration Services](../../2014/integration-services/integration-services-error-and-message-reference.md)   
 [Editor für den Analysis Services-Task „DDL ausführen“ &#40;Seite „Allgemein“&#41;](general-page-of-integration-services-designers-options.md)   
 [Seite Ausdrücke](expressions/expressions-page.md)   
 [Ablaufsteuerung](control-flow/control-flow.md)   
 [Analysis Services Scripting Language &#40;ASSL&#41; Verweis](https://docs.microsoft.com/bi-reference/assl/analysis-services-scripting-language-assl-for-xmla)   
 [XML for Analysis-Referenz &#40;XMLA&#41;](https://docs.microsoft.com/bi-reference/xmla/xml-for-analysis-xmla-reference)  
  
  
