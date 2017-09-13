---
title: DROP SEQUENCE (Transact-SQL) | Microsoft Docs
ms.custom:
- SQL2016_New_Updated
ms.date: 05/11/2017
ms.prod: sql-non-specified
ms.reviewer: 
ms.suite: 
ms.technology:
- database-engine
ms.tgt_pltfrm: 
ms.topic: language-reference
f1_keywords:
- DROP SEQUENCE
- DROP_SEQUENCE_TSQL
dev_langs:
- TSQL
helpviewer_keywords:
- DROP SEQUENCE statement
- sequence number object, dropping
ms.assetid: c25772d3-61af-4aa7-b58b-a6f67a793e3d
caps.latest.revision: 20
author: BYHAM
ms.author: rickbyh
manager: jhubbard
ms.translationtype: MT
ms.sourcegitcommit: 876522142756bca05416a1afff3cf10467f4c7f1
ms.openlocfilehash: 6d7247c5e809c8e26fbd17dc01e8c2f624a170ff
ms.contentlocale: de-de
ms.lasthandoff: 09/01/2017

---
# <a name="drop-sequence-transact-sql"></a>DROP SEQUENCE (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2012-asdb-xxxx-xxx_md](../../includes/tsql-appliesto-ss2012-asdb-xxxx-xxx-md.md)]

  Entfernt ein Sequenzobjekt aus der aktuellen Datenbank.  
  
 ![Themenlinksymbol](../../database-engine/configure-windows/media/topic-link.gif "Topic link icon") [Transact-SQL Syntax Conventions (Transact-SQL-Syntaxkonventionen)](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>Syntax  
  
```  
DROP SEQUENCE [ IF EXISTS ] { [ database_name . [ schema_name ] . | schema_name. ]    sequence_name } [ ,...n ]  
 [ ; ]  
```  
  
## <a name="arguments"></a>Argumente  
 *IF VORHANDEN IST*  
 **Gilt für**: [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] ([!INCLUDE[ssSQL15](../../includes/sssql15-md.md)] bis zur [aktuellen Version](http://go.microsoft.com/fwlink/p/?LinkId=299658)).  
  
 Bedingt löscht die Sequenz nur, wenn sie bereits vorhanden ist.  
  
 *database_name*  
 Der Name der Datenbank, in der das Sequenzobjekt erstellt wurde.  
  
 *schema_name*  
 Der Name des Schemas, zu dem das Sequenzobjekt gehört.  
  
 *sequence_name*  
 Der Name der Sequenz, die gelöscht werden soll. Der Typ ist **Sysname**.  
  
## <a name="remarks"></a>Hinweise  
 Sequenzobjekte weisen keine andauernde Beziehung zur generierten Zahl auf. Daher können Sequenzobjekte gelöscht werden, auch wenn die generierte Zahl noch verwendet wird.  
  
 Ein Sequenzobjekt kann gelöscht werden, während eine gespeicherte Prozedur oder ein Trigger darauf verweisen, da es nicht schemagebunden ist. Ein Sequenzobjekt kann nicht gelöscht werden, wenn als Standardwert in einer Tabelle darauf verwiesen wird. Das Objekt, das auf die Sequenz verweist, ist in der Fehlermeldung aufgeführt.  
  
 Um alle Sequenzobjekte in der Datenbank aufzulisten, führen Sie die folgende Anweisung aus.  
  
```  
SELECT sch.name + '.' + seq.name AS [Sequence schema and name]   
    FROM sys.sequences AS seq  
    JOIN sys.schemas AS sch  
        ON seq.schema_id = sch.schema_id ;  
GO  
```  
  
## <a name="security"></a>Sicherheit  
  
### <a name="permissions"></a>Berechtigungen  
 Erfordert die ALTER- oder CONTROL-Berechtigung für das Schema.  
  
### <a name="audit"></a>Überwachung  
 Überwachen der **DROP SEQUENCE**, Überwachen der **SCHEMA_OBJECT_CHANGE_GROUP**.  
  
## <a name="examples"></a>Beispiele  
 Im folgenden Beispiel wird das Sequenzobjekt `CountBy1` aus der aktuellen Datenbank entfernt.  
  
```  
DROP SEQUENCE CountBy1 ;  
GO  
```  
  
## <a name="see-also"></a>Siehe auch  
 [ALTER SEQUENCE &#40; Transact-SQL &#41;](../../t-sql/statements/alter-sequence-transact-sql.md)   
 [Erstellen Sie SEQUENCE &#40; Transact-SQL &#41;](../../t-sql/statements/create-sequence-transact-sql.md)   
 [NÄCHSTEN Wert für &#40; Transact-SQL &#41;](../../t-sql/functions/next-value-for-transact-sql.md)   
 [Sequenznummern](../../relational-databases/sequence-numbers/sequence-numbers.md)  
  
  
