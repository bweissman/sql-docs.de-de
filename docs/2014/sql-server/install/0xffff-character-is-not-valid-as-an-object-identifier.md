---
title: 0xFFFF-Zeichen ist nicht gültig ist, als Objektbezeichner | Microsoft-Dokumentation
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology:
- database-engine
ms.topic: conceptual
helpviewer_keywords:
- 0xFFFF character [SQL Server]
ms.assetid: b2c9c8cf-9194-45e0-be6b-2d5ec52e8153
author: mashamsft
ms.author: mathoma
manager: craigg
ms.openlocfilehash: 7a91a64358ccd23e923d30a291b044800ce710ae
ms.sourcegitcommit: 3da2edf82763852cff6772a1a282ace3034b4936
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 10/02/2018
ms.locfileid: "48112780"
---
# <a name="0xffff-character-is-not-valid-as-an-object-identifier"></a>0xFFFF-Zeichen ist als Objektbezeichner nicht gültig
  Der Upgrade Advisor hat das 0xFFFF-Zeichen in einem Objektbezeichner erkannt. Wenn der Datenbank-Kompatibilitätsmodus auf 90 oder höher festgelegt ist, kann in [!INCLUDE[ssVersion2005](../../includes/ssversion2005-md.md)] und höher nicht auf Objekte wie Datenbanken, Tabellen und Spalten verwiesen werden, die dieses Zeichen in ihrem Bezeichner enthalten. Die Objekte können zudem nicht umbenannt werden. Wenn Sie auf [!INCLUDE[ssKatmai](../../includes/sskatmai-md.md)] aktualisieren, behalten die Benutzerdatenbanken ihren Kompatibilitätsmodus bei. Bevor Sie den Datenbank-Kompatibilitätsmodus in 90 oder höher ändern, benennen Sie das Objekt um, das das Zeichen 0xFFFF enthält.  
  
 Weitere Informationen über Bezeichner finden Sie unter "Bezeichner" in der [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]-Onlinedokumentation. Weitere Informationen über Datenbankkompatibilitätsmodi finden Sie unter "sp_dbcmptlevel" in der [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]-Onlinedokumentation.  
  
## <a name="component"></a>Komponente  
 [!INCLUDE[ssDE](../../includes/ssde-md.md)]  
  
## <a name="see-also"></a>Siehe auch  
 [Datenbank-Engine-Upgrade-Probleme](../../../2014/sql-server/install/database-engine-upgrade-issues.md)   
 [SQL Server 2014 Upgrade Advisor &#91;neu&#93;](/sql/2014/sql-server/install/sql-server-2014-upgrade-advisor)  
  
  
