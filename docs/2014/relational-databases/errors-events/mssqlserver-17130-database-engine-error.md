---
title: MSSQLSERVER_17130 | Microsoft-Dokumentation
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: supportability
ms.topic: conceptual
helpviewer_keywords:
- 17130 (Database Engine error)
ms.assetid: 7ce6afca-221d-402f-89df-da7e74a339a8
author: MashaMSFT
ms.author: mathoma
manager: craigg
ms.openlocfilehash: 4f8d62a98d39a65db78f79fdfaf3ecdb2921408e
ms.sourcegitcommit: 3da2edf82763852cff6772a1a282ace3034b4936
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 10/02/2018
ms.locfileid: "48142873"
---
# <a name="mssqlserver17130"></a>MSSQLSERVER_17130
    
## <a name="details"></a>Details  
  
|||  
|-|-|  
|Produktname|SQL Server|  
|Ereignis-ID|17130|  
|Ereignisquelle|MSSQLSERVER|  
|Komponente|SQLEngine|  
|Symbolischer Name|INIT_NOLOCKSPACE|  
|Meldungstext|Nicht genügend Arbeitsspeicher für die konfigurierte Anzahl von Sperren. Das Starten wird mit einer kleineren Sperrhashtabelle versucht. Dies kann Auswirkungen auf die Leistung haben. Bitten Sie den Datenbankadministrator, mehr Arbeitsspeicher für diese Instanz der Datenbank-Engine zu konfigurieren.|  
  
## <a name="explanation"></a>Erklärung  
 Nicht genug Arbeitsspeicher für die gewünschte Hashtabellengröße des Sperren-Managers.  Es wird versucht, eine kleinere Hashtabelle zuzuordnen.  
  
## <a name="user-action"></a>Benutzeraktion  
 Überprüfen Sie die Konfigurationsparameter des Serverarbeitsspeichers (minimaler/maximaler Serverarbeitsspeicher) und die Arbeitsspeicherauslastung. Stellen Sie für SQL Server mehr Arbeitsspeicher zur Verfügung.  
  
  
