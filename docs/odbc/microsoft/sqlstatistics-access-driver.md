---
title: SQLStatistics (Access-Treiber) | Microsoft-Dokumentation
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
helpviewer_keywords:
- Access driver [ODBC], SQLStatistics
- SQLStatistics function [ODBC], Access Driver
ms.assetid: 6117ac77-1020-4f0c-8eed-e671c34c1f21
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: bc5a354aeaf186b4baeabd96e7424939fe463bfb
ms.sourcegitcommit: 61381ef939415fe019285def9450d7583df1fed0
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 10/01/2018
ms.locfileid: "47777418"
---
# <a name="sqlstatistics-access-driver"></a>SQLStatistics (Access-Treiber)
> [!NOTE]  
>  Dieses Thema enthält die Access-Treiber-spezifische Informationen. Allgemeine Informationen zu dieser Funktion finden Sie unter den entsprechenden Themen unter [ODBC-API-Referenz](../../odbc/reference/syntax/odbc-api-reference.md).  
  
|Spalte|Kommentare|  
|------------|--------------|  
|TABLE_QUALIFIER|Der Pfad zu einer Datenbankdatei wird für Microsoft Access zurückgegeben.<br /><br /> Musterabgleich wird nicht unterstützt der *SzTableQualifier* Argument.|  
|TABLE_OWNER|In diesem Artikel wird NULL zurückgegeben, da der Name des Besitzers nicht unterstützt wird.|  
|table_name|Der Tabellenname nicht durch Trennzeichen getrennten.<br /><br /> Musterabgleich wird nicht unterstützt der *SzTableName* Argument.|  
|INDEX_QUALIFIER|Immer wird NULL zurückgegeben.|  
|INDEX_NAME|Index abhängig.|  
|TYPE|Nur SQL_TABLE_STAT oder SQL_INDEX_OTHER wird für den Typ zurückgegeben.|  
|SEQ_IN_INDEX|Index abhängig.|  
|COLUMN_NAME|Index abhängig.|  
|COLLATION|Index abhängig.|  
|CARDINALITY|Nur zurückgegeben für Microsoft Access.|  
|PAGES|Immer wird NULL zurückgegeben.|  
  
 Filtern von basiert auf Eindeutigkeit (das *fUnique* Argument). Die *fAccuracy* Parameter wird ignoriert.
