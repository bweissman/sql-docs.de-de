---
title: FileStream und FileTable gespeicherte Systemprozeduren (Transact-SQL) | Microsoft-Dokumentation
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql
ms.prod_service: database-engine
ms.reviewer: ''
ms.technology: system-objects
ms.topic: language-reference
dev_langs:
- TSQL
helpviewer_keywords:
- FileTables [SQL Server], catalog views
ms.assetid: 2c83a4a7-720b-4435-a3b5-788c29f56949
author: MashaMSFT
ms.author: mathoma
manager: craigg
ms.openlocfilehash: 79d01c66d26e15518f2acdb2babfa0fa805da536
ms.sourcegitcommit: 61381ef939415fe019285def9450d7583df1fed0
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 10/01/2018
ms.locfileid: "47842367"
---
# <a name="filestream-and-filetable-system-stored-procedures-transact-sql"></a>FileStream und FileTable gespeicherte Systemprozeduren (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2012-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2012-xxxx-xxxx-xxx-md.md)]

  Dieser Abschnitt beschreibt die gespeicherten Systemprozeduren auf die FileTable, und Filestream-Funktion.  

## <a name="filestream-and-filetable-system-stored-procedures"></a>FileStream und Filetable gespeicherten Systemprozeduren
  [Sp_filestream_force_garbage_collection (Transact-SQL)](filestream-and-filetable-sp-filestream-force-garbage-collection.md)

   Erzwingt die Ausführung des FILESTREAM-Garbage Collectors und löscht alle nicht benötigten FILESTREAM-Dateien.

  [Sp_kill_filestream_non_transacted_handles (Transact-SQL)](filestream-and-filetable-sp-kill-filestream-non-transacted-handles.md)

  Schließt nicht transaktionale Dateihandles für FileTable-Daten.


## <a name="see-also"></a>Siehe auch
[FileStream](../../relational-databases/blob/filestream-sql-server.md)
<br>[Filetables](../../relational-databases/blob/filetables-sql-server.md)
<br>[Dynamische Verwaltungssichten für Filestream und FileTable (Transact-SQL)](../system-dynamic-management-views/filestream-and-filetable-dynamic-management-views-transact-sql.md)
<br>[Katalogsichten für Filestream und FileTable (Transact-SQL)](../system-catalog-views/filestream-and-filetable-catalog-views-transact-sql.md)
  
  
