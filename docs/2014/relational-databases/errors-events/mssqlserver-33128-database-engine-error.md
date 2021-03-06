---
title: MSSQLSERVER_33128 | Microsoft-Dokumentation
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: supportability
ms.topic: conceptual
helpviewer_keywords:
- 33128 (Database Engine error)
ms.assetid: 12c1096f-d120-439b-85f3-f794859503c9
author: MashaMSFT
ms.author: mathoma
manager: craigg
ms.openlocfilehash: a995a68849ed55dbf136191a061ac6f855703a66
ms.sourcegitcommit: 3da2edf82763852cff6772a1a282ace3034b4936
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 10/02/2018
ms.locfileid: "48057791"
---
# <a name="mssqlserver33128"></a>MSSQLSERVER_33128
    
## <a name="details"></a>Details  
  
|||  
|-|-|  
|Produktname|SQL Server|  
|Ereignis-ID|33128|  
|Ereignisquelle|MSSQLSERVER|  
|Komponente|SQLEngine|  
|Symbolischer Name|SEC_DEPRECATED_ALGO|  
|Meldungstext|Verschlüsselung fehlgeschlagen. Schlüssel verwendet veralteten Algorithmus '%.*ls', der nicht mehr unterstützt wird.|  
  
## <a name="explanation"></a>Erklärung  
 Diese Meldung wird angezeigt, wenn Sie auf den Verschlüsselungsalgorithmus RC4 (oder RC4_128) verweisen. RC4 und RC4_128 sind schwache Algorithmen und veraltet. Verwenden Sie stattdessen einen stärkeren Algorithmus, z. B. einen der AES-Algorithmen.  
  
 Wenn der Kompatibilitätsgrad der Datenbank 90 oder 100 beträgt, wird der Vorgang erfolgreich abgeschlossen, das Veraltungsereignis ausgelöst und die Meldung nur im Ringpuffer angezeigt.  
  
 Wenn der Kompatibilitätsgrad der Datenbank 110 oder höher beträgt, werden Entschlüsselungsvorgänge erfolgreich abgeschlossen, das Veraltungsereignis ausgelöst und die Meldung nur im Ringpuffer angezeigt. Verschlüsselungsvorgänge schlagen fehl, das Veraltungsereignis wird ausgelöst, und die Meldung wird für den Benutzer sowie im Ringpuffer angezeigt.  
  
> [!NOTE]  
>  Der Ringpuffer ist eine interne Komponente, die nicht vollständig dokumentiert ist und nicht für die Verwendung durch Kunden bestimmt ist. Meldungen aus dem Ringpuffer sind bei der Kontaktaufnahme mit dem [!INCLUDE[msCoName](../../includes/msconame-md.md)]-Kundensupport hilfreich. Zum Anzeigen des Ringpuffers fragen Sie die dynamische Verwaltungssicht sys.dm_os_ring_buffers ab.  
  
|Status|Description|  
|-----------|-----------------|  
|1|Ein RC4-Schlüssel wird in der integrierten encryptbykey()-Funktion verwendet. Die integrierte Funktion gibt NULL zurück. Diese Meldung wird nur im Ringpuffer angezeigt.|  
|2|Ein RC4-Schlüssel wird in von der integrierten decryptbykey()-Funktion verwendet. Diese Meldung wird nur im Ringpuffer angezeigt.|  
|3|Ein veralteter RC4-Schlüssel wird mit einem symmetrischen Schlüssel verschlüsselt. Dies wird den Benutzern und im Ringpuffer angezeigt. Veraltete symmetrische RC4-Schlüssel können in Kompatibilitätsgrad 110 nicht geändert werden. Verwenden Sie für Verschlüsselungsvorgänge nach Möglichkeit keine RC4-Schlüssel. Legen Sie bei Bedarf den Abwärtskompatibilitätsgrad auf 90 oder 100 fest.|  
|4|Ein Nicht-RC4-Schlüssel wird mit einem veralteten symmetrischen RC4-Schlüssel verschlüsselt. Dies wird den Benutzern und im Ringpuffer angezeigt. Ändern Sie die Anwendung so, dass keine symmetrischen RC4-Schlüssel verwendet werden, oder legen Sie den Abwärtskompatibilitätsgrad auf 90 oder 100 fest.|  
|5|Ein veralteter RC4-Schlüssel wird mit einem symmetrischen Schlüssel entschlüsselt. Diese Meldung wird nur im Ringpuffer angezeigt.|  
|6|Ein Nicht-RC4-Schlüssel wird mit einem symmetrischen RC4-Schlüssel entschlüsselt. Diese Meldung wird nur im Ringpuffer angezeigt.|  
|7|Ein symmetrischer RC4-Schlüssel wird durch das Zertifikat verschlüsselt. Dies wird den Benutzern und im Ringpuffer angezeigt.|  
|8|Ein symmetrischer RC4-Schlüssel wird durch das Zertifikat entschlüsselt. Diese Meldung wird nur im Ringpuffer angezeigt.|  
|9|Ein symmetrischer RC4-Schlüssel wird mit dem EKM-Schlüssel verschlüsselt.|  
|10|Ein symmetrischer RC4-Schlüssel wird mit dem EKM-Schlüssel entschlüsselt. Diese Meldung wird nur im Ringpuffer angezeigt.|  
  
## <a name="user-action"></a>Benutzeraktion  
 Verwenden Sie stattdessen einen stärkeren Algorithmus, z. B. einen der AES-Algorithmen. (Empfohlen)  
  
 Verwenden Sie die Anweisung ALTER DATABASE SET COMPATIBILITY_LEVEL, um den Kompatibilitätsgrad der Datenbank auf 100 festzulegen. (Nicht empfohlen.)  
  
  
