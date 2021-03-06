---
title: Festlegen von DCOM-Stream, die Marshalling-Formats | Microsoft-Dokumentation
ms.prod: sql
ms.prod_service: connectivity
ms.technology: connectivity
ms.custom: ''
ms.date: 01/19/2017
ms.reviewer: ''
ms.topic: conceptual
helpviewer_keywords:
- dcom stream marshaling format in rds [ADO]
ms.assetid: 46664ac5-d6e6-4457-8bae-3a98300f2a41
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: 33359afb2910c75e34ff38c9606ff71b3760cbc1
ms.sourcegitcommit: 61381ef939415fe019285def9450d7583df1fed0
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 10/01/2018
ms.locfileid: "47802858"
---
# <a name="setting-dcom-stream-marshaling-format"></a>Festlegen des DCOM-Datenstrom-Marshalling-Formats
Ein Clientcomputer mithilfe von Komponenten von RDS 1.5 oder früher ist nicht kompatibel ist, mit dem Server über die Komponenten von RDS-2.0 oder höher. Wenn DCOM als zugrunde liegendes Protokoll verwendet wird, wird die Unterstützung für RDS-2.0 oder höher eine effizientere Transport [Recordset](../../../ado/reference/ado-api/recordset-object-ado.md) Objekte. Wenn der Client die Komponenten von RDS 1.5 oder früher ausgeführt wird, können Sie Ihre Server für mit der vorherigen RDS-Unterstützung (RDS-1.0 bezeichnet) oder die neuere RDS-Unterstützung (RDS 2.0 oder höher) festlegen. Legen Sie entweder die folgenden Registrierungseinträge an:  
  
> [!IMPORTANT]
>  Ab Windows 8 und Windows Server 2012, sind nicht mehr RDS-Server-Komponenten in das Windows-Betriebssystem enthalten (finden Sie unter Windows 8 und [Windows Server 2012 Compatibility Cookbook](https://www.microsoft.com/en-us/download/details.aspx?id=27416) Einzelheiten). RDS-Client-Komponenten werden in einer zukünftigen Version von Windows entfernt werden. Nutzen Sie diese Funktionen bei Neuentwicklungen nicht mehr, und planen Sie die Änderung von Anwendungen, die diese Funktion zurzeit verwenden. Anwendungen, die RDS zu migrieren sollten [WCF Data Service](http://go.microsoft.com/fwlink/?LinkId=199565).  
  
```  
[HKEY_CLASSES_ROOT]  
\CLSID\[58ECEE30-E715-11CF-B0E3-00AA003F000F}\ADTGOptions]"MarshalFormat"="RDS10"  
```  
  
 -oder-  
  
```  
[HKEY_CLASSES_ROOT]  
\CLSID\[58ECEE30-E715-11CF-B0E3-00AA003F000F}\ADTGOptions]"MarshalFormat"="RDS20"  
```


