---
title: CALL-Anweisung (MDX) | Microsoft Docs
ms.custom: 
ms.date: 03/02/2016
ms.prod: sql-server-2016
ms.reviewer: 
ms.suite: 
ms.technology:
- analysis-services
ms.tgt_pltfrm: 
ms.topic: language-reference
f1_keywords:
- CALL
dev_langs:
- kbMDX
helpviewer_keywords:
- voids [MDX]
- stored procedures [MDX]
- CALL statement
ms.assetid: b534a20b-924c-43b8-832d-24e57d50425c
caps.latest.revision: 35
author: Minewiskan
ms.author: owend
manager: erikre
ms.translationtype: MT
ms.sourcegitcommit: 1419847dd47435cef775a2c55c0578ff4406cddc
ms.openlocfilehash: 3d5bc0d9875d602135fd92722b73c07176a1df59
ms.contentlocale: de-de
ms.lasthandoff: 08/02/2017

---
# <a name="mdx-data-manipulation---call"></a>Datenbearbeitung für MDX - AUFRUF
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx_md](../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]

  Führt eine gespeicherte Prozedur, die "void" zurückgibt, im aktuellen Bereich oder optional für einen angegebenen Cube aus.  
  
## <a name="syntax"></a>Syntax  
  
```  
  
CALL SP_Name   
   [ (SP_Argument   
      [, SP_Argument ,...n]  
      ) ]   
[ONCube_Expression]  
```  
  
## <a name="arguments"></a>Argumente  
 *SP_Name*  
 Ein gültiger Zeichenfolgenausdruck, der den Namen einer gespeicherten Prozedur bereitstellt.  
  
 *SP_Argument*  
 Ein gültiger Zeichenfolgenausdruck, der ein Argument für die aufgerufene gespeicherte Prozedur bereitstellt.  
  
 *Cube_Expression*  
 Ein gültiger Zeichenfolgen-Cube-Ausdruck, der den Namen des Cubes bereitstellt.  
  
## <a name="remarks"></a>Hinweise  
 Die **Aufrufen** -Anweisung führt eine angegebene registrierte gespeicherte Prozedur, einschließlich optional ein oder mehrere Argumente für die angegebene gespeicherte Prozedur. Die **Aufrufen** -Anweisung ist nur mit gespeicherten Prozeduren, die ' void ' zurückgeben. Die Anweisung kann nicht mit anderen Funktionen oder Operatoren in einem MDX-Ausdruck kombiniert werden. Registrierte gespeicherte Prozeduren, die Werte zurückgeben, können direkt in MDX-Ausdrücken aufgerufen und mit anderen MDX-Funktionen und -Operatoren kombiniert werden.  
  
 Wenn kein Cube angegeben wird, führt die Anweisung die gespeicherte Prozedur mit dem aktuellen Cube als Argument aus.  
  
> [!NOTE]  
>  Wenn die gespeicherte Prozedur nicht auf dem Client registriert ist die **Aufrufen** Anweisung versucht, auf die gespeicherte Prozedur von einer Instanz von Aufrufen [!INCLUDE[msCoName](../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)].  
  
## <a name="see-also"></a>Siehe auch  
 [MDX-Datenbearbeitungsanweisungen &#40; MDX &#41;](../mdx/mdx-data-manipulation-statements-mdx.md)   
 [Verwenden gespeicherte Prozeduren &#40; MDX &#41;](../mdx/using-stored-procedures-mdx.md)  
  
  
