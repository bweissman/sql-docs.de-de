---
title: DTAXML-Element (DTA) | Microsoft-Dokumentation
ms.custom: ''
ms.date: 03/14/2017
ms.prod: sql
ms.prod_service: sql-tools
ms.reviewer: ''
ms.technology:
- database-engine
ms.topic: conceptual
dev_langs:
- XML
helpviewer_keywords:
- DTAXML element
ms.assetid: 3d9942ed-8a27-40db-a7c9-808984d914a2
author: stevestein
ms.author: sstein
manager: craigg
ms.openlocfilehash: f09e7899d3723e646f285dbc599a30556f6df039
ms.sourcegitcommit: 61381ef939415fe019285def9450d7583df1fed0
ms.translationtype: MTE75
ms.contentlocale: de-DE
ms.lasthandoff: 10/01/2018
ms.locfileid: "47778078"
---
# <a name="dtaxml-element-dta"></a>DTAXML-Element (DTA)
[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md](../../includes/appliesto-ss-xxxx-xxxx-xxx-md.md)]
  Das Stammelement einer XML-Eingabe- oder -Ausgabedatei des Datenbankoptimierungsratgebers. **DTAXML** enthält alle Elemente, die die vom Datenbankoptimierungsratgeber generierte Optimierungseingabe und -ausgabe beschreiben.  
  
## <a name="syntax"></a>Syntax  
  
```  
  
<DTAXML   
    xmlns:xsi="http://www.w3.org/2001/XMLSchema-instance"   
    xmlns="http://schemas.microsoft.com/sqlserver/2004/07/dta">  
    ...code removed here...  
</DTAXML>  
```  
  
## <a name="element-attributes"></a>Elementattribute  
  
|attribute|und Beschreibung|  
|---------------|-----------------|  
|**xmlns:xsi**|Erforderlich. Identifiziert den XML-Schemainstanzennamespace. Attribute aus diesem Namespace dienen zum Verweisen auf das Schema, das zum Überprüfen der XML-Datei des Datenbankoptimierungsratgebers verwendet wird.<br /><br /> Erforderlicher Wert: [http://www.w3.org/2001/XMLSchema-instance](http://www.w3.org/2001/XMLSchema-instance)|  
|**xmlns**|Erforderlich. Identifiziert den Namespace des Datenbankoptimierungsratgebers.<br /><br /> Wenn Sie die XML-Datei des Datenbankoptimierungsratgebers mit dem XML-Editor in [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)]bearbeiten, wird dieser Wert von der F1-Hilfe und der dynamischen Hilfe verwendet, um mögliche Referenzthemen in der [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] -Onlinedokumentation zu ermitteln.<br /><br /> Erforderlicher Wert:<br /><br /> für das[XML-Schema des Datenbankoptimierungsratgebers](http://go.microsoft.com/fwlink/?LinkId=43100)|  
  
## <a name="element-characteristics"></a>Elementmerkmale  
  
|Merkmal|und Beschreibung|  
|--------------------|-----------------|  
|**Datentyp und -länge**|Keine.|  
|**Standardwert**|Keine.|  
|**Vorkommen**|Einmal pro DTA XML-Datei erforderlich.|  
  
## <a name="element-relationships"></a>Elementbeziehungen  
  
|Beziehung|Elemente|  
|------------------|--------------|  
|**Übergeordnetes Element**|None|  
|**Untergeordnete Elemente**|[DTAInput-Element &#40;DTA&#41;](../../tools/dta/dtainput-element-dta.md)<br /><br /> **DTAOutput**-Element (weitere Informationen finden Sie im Thema zum [XML-Schema für den Datenbankoptimierungsratgeber](http://schemas.microsoft.com/sqlserver/))|  
  
## <a name="remarks"></a>Remarks  
 Weitere Informationen zu XML-Namespaces finden Sie unter [Namespaces in an XML Document](http://go.microsoft.com/fwlink/?LinkId=7341) (in Englisch) in der [!INCLUDE[msCoName](../../includes/msconame-md.md)] MSDN Library.  
  
## <a name="example"></a>Beispiel  
 Beispiele für typische **DTAXML**-Elemente finden Sie unter [Beispiele für XML-Eingabedateien &#40;DTA&#41;](../../tools/dta/xml-input-file-samples-dta.md).  
  
## <a name="see-also"></a>Weitere Informationen finden Sie unter  
 [XML-Eingabedateireferenz &amp;amp;#40;Datenbankoptimierungsratgeber&amp;amp;#41;](../../tools/dta/xml-input-file-reference-database-engine-tuning-advisor.md)   
 [Starten und Verwenden des Datenbankoptimierungsratgebers](../../relational-databases/performance/start-and-use-the-database-engine-tuning-advisor.md)  
  
  
