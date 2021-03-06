---
title: SQLState-Eigenschaft | Microsoft-Dokumentation
ms.prod: sql
ms.prod_service: connectivity
ms.technology: connectivity
ms.custom: ''
ms.date: 01/19/2017
ms.reviewer: ''
ms.topic: conceptual
apitype: COM
f1_keywords:
- Error::GetSQLState
- Error::SQLState
- Error::get_SQLState
helpviewer_keywords:
- SQLState property
ms.assetid: f9e25967-54b0-444d-af2a-0d2c75365d3e
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: 00ab80a10b2c7c411cee0fb6061467d67cfbd4a2
ms.sourcegitcommit: 61381ef939415fe019285def9450d7583df1fed0
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 10/01/2018
ms.locfileid: "47822138"
---
# <a name="sqlstate-property"></a>SQLState-Eigenschaft
Gibt den SQL-Status für einen bestimmten [Fehler](../../../ado/reference/ado-api/error-object.md) Objekt.  
  
## <a name="return-value"></a>Rückgabewert  
 Gibt einen fünf Zeichen **Zeichenfolge** Wert, der den ANSI SQL-Standard folgt und den Fehlercode angibt.  
  
## <a name="remarks"></a>Hinweise  
 Verwenden der **SQLState** -Eigenschaft in der fünfstellige Fehlercode, der der Anbieter zurückgibt, tritt ein Fehler bei der Verarbeitung einer SQL-Anweisung. Z. B. stammen bei Verwendung von Microsoft OLE DB-Anbieter für ODBC mit einer Microsoft SQL Server-Datenbank, SQL-Fehlercodes für Status ODBC, basierend entweder auf Fehler, die speziell für ODBC oder Fehler, die stammen von Microsoft SQL Server, und klicken Sie dann an ODBC zugeordnet sind Fehler. Diese Fehlercodes werden in die ANSI SQL-standard dokumentiert, aber möglicherweise von verschiedenen Datenquellen unterschiedlich implementiert werden.  
  
## <a name="applies-to"></a>Gilt für  
 [Error-Objekt](../../../ado/reference/ado-api/error-object.md)  
  
## <a name="see-also"></a>Siehe auch  
 [Description, HelpContext, HelpFile, NativeError, Anzahl, Quelle und SQLState Eigenschaften – Beispiel (VB)](../../../ado/reference/ado-api/description-helpcontext-helpfile-nativeerror-number-source-example-vb.md)   
 [Description, HelpContext, HelpFile, NativeError, Anzahl, Quelle und SQLState Eigenschaften – Beispiel (VC++)](../../../ado/reference/ado-api/description-helpcontext-helpfile-nativeerror-number-source-example-vc.md)   
