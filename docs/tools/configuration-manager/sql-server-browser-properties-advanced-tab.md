---
title: "Eigenschaften von SQL Server-Browser (Registerkarte Erweitert) | Microsoft Docs"
ms.custom: ""
ms.date: "03/14/2017"
ms.prod: "sql-server-2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "database-engine"
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: ba79137a-cb72-4bf3-a650-e11d02cfce10
caps.latest.revision: 19
author: "BYHAM"
ms.author: "rickbyh"
manager: "jhubbard"
caps.handback.revision: 19
---
# Eigenschaften von SQL Server-Browser (Registerkarte Erweitert)
  Das [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] -Browser-Programm wird als Dienst auf dem Server ausgeführt. [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] -Browser lauscht auf eingehende Anforderungen für [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] -Ressourcen und stellt Informationen zu [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] -Instanzen zur Verfügung, die auf dem Computer installiert sind.  
  
## enthalten  
 **Gruppiert**  
 Zeigt an, ob dieser Dienst als Ressource eines gruppierten Servers installiert ist.  
  
 **Berichterstellung für Kundenfeedback**  
 Gibt an, ob Service Quality Monitoring für diesen Dienst aktiviert wurde. Weitere Informationen zu Berichterstellung für Kundenfeedback finden Sie in der Onlinedokumentation unter "Einstellungen für Fehler- und Verwendungsberichte".  
  
 **Speicherverzeichnis**  
 Der Speicherort, an dem Speicherabbilder im Falle eines Fehlers abgelegt werden.  
  
 **Fehlerberichterstellung**  
 Mit der Einstellung **Ja** werden vom Programm Dr. Watson Informationen an [!INCLUDE[msCoName](../../includes/msconame-md.md)] oder den Fehlerberichtsserver weitergeleitet, wenn ein schwerwiegender Fehler auftritt. Weitere Informationen zur Fehlerberichterstellung finden Sie in der Onlinedokumentation unter "Einstellungen für Fehler- und Verwendungsberichte".  
  
 **Instanz-ID**  
 Gibt die Instanz von [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] an, die diese [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]-Agent-Instanz verwendet hat. Die Standardinstanz ist **MSSQL10_50.MSSQLSERVER**.  
  
## Siehe auch  
 [SQL Server-Browserdienst](../../tools/configuration-manager/sql-server-browser-service.md)  
  
  