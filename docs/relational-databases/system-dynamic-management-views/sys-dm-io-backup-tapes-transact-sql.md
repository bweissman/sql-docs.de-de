---
title: Sys. dm_io_backup_tapes (Transact-SQL) | Microsoft-Dokumentation
ms.custom: ''
ms.date: 06/10/2016
ms.prod: sql
ms.reviewer: ''
ms.technology: system-objects
ms.topic: language-reference
f1_keywords:
- sys.dm_io_backup_tapes
- dm_io_backup_tapes_TSQL
- sys.dm_io_backup_tapes_TSQL
- dm_io_backup_tapes
dev_langs:
- TSQL
helpviewer_keywords:
- sys.dm_io_backup_tapes dynamic management view
ms.assetid: 2e27489e-cf69-4a89-9036-77723ac3de66
author: stevestein
ms.author: sstein
manager: craigg
ms.openlocfilehash: 195c8dc2db7011801023e7e21e68ed1f5ed75a6f
ms.sourcegitcommit: 61381ef939415fe019285def9450d7583df1fed0
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 10/01/2018
ms.locfileid: "47603468"
---
# <a name="sysdmiobackuptapes-transact-sql"></a>sys.dm_io_backup_tapes (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]

  Gibt die Liste der Bandmedien und den Status von Einbindungsanforderungen für Sicherungen zurück.   
 
|Spaltenname|Datentyp|Description|  
|-----------------|---------------|-----------------|  
|**physical_device_name**|**nvarchar(520)**|Der Name des tatsächlichen physischen Mediums, auf dem eine Sicherung erstellt werden kann. Lässt keine NULL-Werte zu.|  
|**logical_device_name**|**nvarchar(256)**|Vom Benutzer angegebener Name für das Laufwerk (von **Sys. backup_devices**). NULL, wenn kein benutzerdefinierter Name verfügbar ist. Lässt NULL-Werte zu.|  
|**status**|**int**|Bandstatus:<br /><br /> 1 = Geöffnet und kann verwendet werden<br /><br /> 2 = Einbindung erfolgt<br /><br /> 3 = In Verwendung<br /><br /> 4 = Wird geladen<br /><br /> **Hinweis:** beim Laden eines Bandes ist (**Status = 4**), die medienbezeichnung noch nicht gelesen. Spalten, die medienbezeichnung von-Werten, z. B. kopieren **Media_sequence_number**, zeigen erwartete Werte an, die von der tatsächlichen Werte auf dem Band abweichen können. Nachdem Sie die Bezeichnung gelesen wurde, **Status** Änderungen an **3** (in der Verwendung), und die medienbezeichnung Spalten klicken Sie dann das Band wider, die geladen wird.<br /><br /> Lässt keine NULL-Werte zu.|  
|**status_desc**|**nvarchar(520)**|Bandstatusbeschreibung:<br /><br /> AVAILABLE<br /><br /> MOUNT PENDING<br /><br /> IN USE<br /><br /> LOADING MEDIA<br /><br /> Lässt keine NULL-Werte zu.|  
|**mount_request_time**|**datetime**|Uhrzeit, zu der die Einbindung angefordert wurde. NULL, wenn keine Einbindung aussteht (**Status! = 2**). Lässt NULL-Werte zu.|  
|**mount_expiration_time**|**datetime**|Uhrzeit, zu der die Einbindungssanforderung abläuft (Timeout). NULL, wenn keine Einbindung aussteht (**Status! = 2**). Lässt NULL-Werte zu.|  
|**database_name**|**nvarchar(256)**|Die Datenbank, die auf dem Medium gesichert werden soll. Lässt NULL-Werte zu.|  
|**spid**|**int**|Sitzungs-ID. Diese identifiziert den Benutzer des Bandes. Lässt NULL-Werte zu.|  
|**Befehl**|**int**|Der Befehl, durch den die Sicherung ausgeführt wird. Lässt NULL-Werte zu.|  
|**command_desc**|**nvarchar(120)**|Beschreibung des Befehls. Lässt NULL-Werte zu.|  
|**media_family_id**|**int**|Index der Medienfamilie (1... *n*), *n* ist die Anzahl der Medienfamilien im Mediensatz. Lässt NULL-Werte zu.|  
|**media_set_name**|**nvarchar(256)**|Name des Mediensatzes (sofern vorhanden) gemäß Angabe durch die Option MEDIANAME zum Zeitpunkt der Erstellung des Mediensatzes. Lässt NULL-Werte zu.|  
|**media_set_guid**|**uniqueidentifier**|Bezeichner, der den Mediensatz eindeutig identifiziert. Lässt NULL-Werte zu.|  
|**media_sequence_number**|**int**|Index eines Volumes innerhalb einer Medienfamilie (1... *n*). Lässt NULL-Werte zu.|  
|**tape_operation**|**int**|Bandvorgang, der ausgeführt wird:<br /><br /> 1 = Lesen<br /><br /> 2 = Formatieren<br /><br /> 3 = Initialisieren<br /><br /> 4 = Anfügen<br /><br /> Lässt NULL-Werte zu.|  
|**tape_operation_desc**|**nvarchar(120)**|Ausgeführter Bandvorgang:<br /><br /> READ<br /><br /> FORMAT<br /><br /> INIT<br /><br /> APPEND<br /><br /> Lässt NULL-Werte zu.|  
|**mount_request_type**|**int**|Typ der Einbindungsanforderung:<br /><br /> 1 = Bestimmtes Band. Das identifizierte Band die **Media_\***  Felder ist erforderlich.<br /><br /> 2 = Nächste Medienfamilie. Die nächste nicht wiederhergestellte Medienfamilie wird angefordert. Wird verwendet, wenn bei der Wiederherstellung weniger Medien als Medienfamilien vorhanden sind.<br /><br /> 3 = Anschlussband. Die Medienfamilie wird erweitert, und ein Anschlussband wird angefordert.<br /><br /> Lässt NULL-Werte zu.|  
|**mount_request_type_desc**|**nvarchar(120)**|Typ der Einbindungsanforderung:<br /><br /> SPECIFIC TAPE<br /><br /> NEXT MEDIA FAMILY<br /><br /> CONTINUATION VOLUME<br /><br /> Lässt NULL-Werte zu.|  
  
## <a name="permissions"></a>Berechtigungen  
 Der Benutzer benötigt die VIEW SERVER STATE-Berechtigung auf dem Server.  
  
## <a name="see-also"></a>Siehe auch  
 [Dynamische Verwaltungssichten und -funktionen &#40;Transact-SQL&#41;](~/relational-databases/system-dynamic-management-views/system-dynamic-management-views.md)   
 [E/A im Zusammenhang, dynamische Verwaltungssichten und-Funktionen &#40;Transact-SQL&#41;](../../relational-databases/system-dynamic-management-views/i-o-related-dynamic-management-views-and-functions-transact-sql.md)  
  
  

