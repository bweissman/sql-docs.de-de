---
title: Sys. dm_operation_status (Azure SQL-Datenbank) | Microsoft-Dokumentation
ms.custom: ''
ms.date: 06/05/2017
ms.prod: ''
ms.prod_service: sql-database, sql-data-warehouse
ms.reviewer: ''
ms.technology: system-objects
ms.topic: language-reference
f1_keywords:
- dm_operation_status_TSQL
- dm_operation_status
- sys.dm_operation_status
- sys.dm_operation_status_TSQL
dev_langs:
- TSQL
helpviewer_keywords:
- dm_operation_status dynamic management view
- sys.dm_operation_status dynamic management view
ms.assetid: cc847784-7f61-4c69-8b78-5f971bb24d61
author: stevestein
ms.author: sstein
manager: craigg
monikerRange: = azuresqldb-current || = azure-sqldw-latest || = sqlallproducts-allversions
ms.openlocfilehash: 335888ba664751bb20348472736ad697b8fe2b6d
ms.sourcegitcommit: 61381ef939415fe019285def9450d7583df1fed0
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 10/01/2018
ms.locfileid: "47633478"
---
# <a name="sysdmoperationstatus-azure-sql-database"></a>sys.dm_operation_status (Azure SQL-Datenbank)
[!INCLUDE[tsql-appliesto-xxxxxx-asdb-asdw-xxx-md](../../includes/tsql-appliesto-xxxxxx-asdb-asdw-xxx-md.md)]

  Gibt Informationen zu den Vorgängen zurück, die für Datenbanken auf einem [!INCLUDE[ssSDSfull](../../includes/sssdsfull-md.md)]-Server ausgeführt werden.  
  
|Spaltenname|Datentyp|Description|  
|-----------------|---------------|-----------------|  
|session_activity_id|**uniqueidentifier**|ID des Vorgangs. Nicht null ist.|  
|resource_type|**int**|Bezeichnet den Typ der Ressource, für die der Vorgang ausgeführt wird. Nicht null ist. In der aktuellen Version verfolgt diese Sicht nur die Vorgänge nach, die für [!INCLUDE[ssSDS](../../includes/sssds-md.md)] ausgeführt werden. Der entsprechende ganzzahlige Wert ist 0.|  
|resource_type_desc|**nvarchar(2048)**|Beschreibung des Ressourcentyps, für den der Vorgang ausgeführt wird. In der aktuellen Version verfolgt diese Sicht nur die Vorgänge nach, die für [!INCLUDE[ssSDS](../../includes/sssds-md.md)] ausgeführt werden.|  
|major_resource_id|**sql_variant**|Name von [!INCLUDE[ssSDS](../../includes/sssds-md.md)], für die der Vorgang ausgeführt wird. Nicht NULL.|  
|minor_resource_id|**sql_variant**|Nur zur internen Verwendung. Nicht null ist.|  
|Vorgang|**nvarchar(60)**|Für [!INCLUDE[ssSDS](../../includes/sssds-md.md)] ausgeführter Vorgang, z. B. CREATE oder ALTER.|  
|state|**tinyint**|Der Zustand des Vorgangs.<br /><br /> 0 = Ausstehend<br />1 = Vorgang wird ausgeführt<br />2 = Abgeschlossen<br />3 = Fehler<br />4 = Abgebrochen|  
|state_desc|**nvarchar(120)**|PENDING = Vorgang wartet auf verfügbare Ressource oder verfügbares Kontingent.<br /><br /> IN_PROGRESS = Vorgang wurde gestartet und wird ausgeführt.<br /><br /> COMPLETED = Vorgang wurde erfolgreich abgeschlossen.<br /><br /> FAILED = Vorgang ist fehlgeschlagen. Finden Sie unter den **Error_desc** Spalte.<br /><br /> CANCELLED = Vorgang wurde auf Anforderung des Benutzers beendet.|  
|percent_complete|**int**|Prozentsatz des Vorgangs, der abgeschlossen wurde. Werte sind nicht fortlaufend, und die gültigen Werte sind nachfolgend aufgeführt. Nicht NULL ist.<br/><br/>0 = Vorgang wurde nicht gestartet werden.<br/>50 = Vorgang wird ausgeführt<br/>100 = Vorgang wurde abgeschlossen|  
|error_code|**int**|Code, der den Fehler angibt, der während eines fehlgeschlagenen Vorgangs aufgetreten ist. Wenn der Wert 0 ist, bedeutet dies, dass der Vorgang erfolgreich abgeschlossen wurde.|  
|error_desc|**nvarchar(2048)**|Beschreibung des Fehlers, der während eines fehlgeschlagenen Vorgangs aufgetreten ist.|  
|error_severity|**int**|Schweregrad des Fehlers, der während eines fehlgeschlagenen Vorgangs aufgetreten ist. Weitere Informationen zu den Fehler Schweregraden finden Sie unter [Schweregrade von Datenbank-Engine-Fehler](http://go.microsoft.com/fwlink/?LinkId=251052).|  
|error_state|**int**|Zur künftigen Verwendung reserviert. Zukünftige Kompatibilität wird nicht sichergestellt.|  
|start_time|**datetime**|Zeitstempel, an dem der Vorgang begonnen wurde.|  
|last_modify_time|**datetime**|Zeitstempel, an dem der Datensatz zuletzt für einen länger ausgeführten Vorgang geändert wurde. Im Fall von erfolgreich abgeschlossenen Vorgängen wird in diesem Feld der Zeitstempel angezeigt, an dem der Vorgang abgeschlossen wurde.|  
  
## <a name="permissions"></a>Berechtigungen  
 Diese Ansicht ist nur verfügbar, in der **master** Datenbank, um die prinzipalanmeldung auf Serverebene.  
  
## <a name="remarks"></a>Hinweise  
 Um diese Ansicht verwenden zu können, müssen Sie mit verbunden werden die **master** Datenbank. Verwenden der `sys.dm_operation_status` anzeigen in der **master** Datenbank mit der [!INCLUDE[ssSDS](../../includes/sssds-md.md)] Server verfolgen den Status der folgenden Vorgänge ausgeführt werden, auf eine [!INCLUDE[ssSDS](../../includes/sssds-md.md)]:  
  
-   Datenbank erstellen  
  
-   Kopieren einer Datenbank. Mit Datenbankkopie wird ein Datensatz in dieser Sicht auf den Quell- und Zielservern erstellt.  
  
-   Datenbank ändern  
  
-   Ändern der Leistungsebene einer Dienstebene  
  
-   Ändern der Dienstebene einer Datenbank, z. B. von Basic in Standard.  
  
-   Einrichten einer Georeplikationsbeziehung  
  
-   Beenden einer Georeplikationsbeziehung  
  
-   Datenbank wiederherstellen  
  
-   Datenbank löschen  
  
## <a name="example"></a>Beispiel  
 Zeigen Sie die neuesten georeplikationsvorgänge Datenbank "Mydb" zugeordnet.  
  
```  
SELECT * FROM sys.dm_ operation_status   
   WHERE major_resource_id = ‘myddb’   
   ORDER BY start_time DESC;  
```  
  
## <a name="see-also"></a>Siehe auch  
 [Geografische Replikation, dynamische Verwaltungssichten und-Funktionen &#40;Azure SQL-Datenbank&#41;](../../relational-databases/system-dynamic-management-views/geo-replication-dynamic-management-views-and-functions-azure-sql-database.md)   
 [dm_geo_replication_link_status &#40;Azure SQL-Datenbank&#41;](../../relational-databases/system-dynamic-management-views/sys-dm-geo-replication-link-status-azure-sql-database.md)   
 [Sys. geo_replication_links &#40;Azure SQL-Datenbank&#41;](../../relational-databases/system-dynamic-management-views/sys-geo-replication-links-azure-sql-database.md)   
 [ALTER DATABASE &#40;Azure SQL-Datenbank&#41;](../../t-sql/statements/alter-database-azure-sql-database.md)  
  
  
