---
title: GetRoot (Datenbank-Engine) | Microsoft-Dokumentation
ms.custom: ''
ms.date: 7/22/2017
ms.prod: sql
ms.prod_service: database-engine, sql-database
ms.reviewer: ''
ms.technology: t-sql
ms.topic: language-reference
f1_keywords:
- GetRoot
- GetRoot_TSQL
dev_langs:
- TSQL
helpviewer_keywords:
- GetRoot [Database Engine]
ms.assetid: 240b70f1-eeda-44ab-b4bb-9e4af80fa7c0
author: MikeRayMSFT
ms.author: mikeray
manager: craigg
ms.openlocfilehash: ba02bf9f5bf5511b9e334921170e493c8cc84ebc
ms.sourcegitcommit: 61381ef939415fe019285def9450d7583df1fed0
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 10/01/2018
ms.locfileid: "47598948"
---
# <a name="getroot-database-engine"></a>GetRoot (Datenbank-Engine)
[!INCLUDE[tsql-appliesto-ss2008-asdb-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-asdb-xxxx-xxx-md.md)]

Gibt den Stamm der Hierarchiestruktur zurück. GetRoot() ist eine statische Methode.
  
## <a name="syntax"></a>Syntax  
  
```sql
-- Transact-SQL syntax  
hierarchyid::GetRoot ( )   
```  
  
```sql
-- CLR syntax  
static SqlHierarchyId GetRoot ( )   
```  
  
## <a name="return-types"></a>Rückgabetypen  
**SQL Server-Rückgabetyp: hierarchyid**
  
**CLR-Rückgabetyp: SqlHierarchyId**
  
## <a name="remarks"></a>Remarks  
Wird verwendet, um den Stammknoten in einer Hierarchiestruktur zu bestimmen.
  
## <a name="examples"></a>Beispiele  
  
### <a name="a-transact-sql-example"></a>A. Beispiel für Transact-SQL  
Im folgenden Beispiel wird der Stamm der Hierarchiestruktur zurückgegeben.
  
```sql
SELECT OrgNode.ToString() AS Text_OrgNode, *  
FROM HumanResources.EmployeeDemo  
WHERE OrgNode = hierarchyid::GetRoot()  
```  
  
### <a name="b-clr-example"></a>B. CLR-Beispiel  
Im folgenden Codeausschnitt wird die GetRoot()-Methode aufgerufen:
  
```sql
SqlHierarchyId.GetRoot()  
```  
  
## <a name="see-also"></a>Siehe auch
[hierarchyid-Datentyp-Methodenverweis](http://msdn.microsoft.com/library/01a050f5-7580-4d5f-807c-7f11423cbb06)  
[Hierarchische Daten &#40;SQL Server&#41;](../../relational-databases/hierarchical-data-sql-server.md)  
[hierarchyid &#40;Transact-SQL&#41;](../../t-sql/data-types/hierarchyid-data-type-method-reference.md)
  
  
