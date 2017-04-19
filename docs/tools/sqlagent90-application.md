---
title: "sqlagent90 (Anwendung) | Microsoft Docs"
ms.custom: ""
ms.date: "03/14/2017"
ms.prod: "sql-server-2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "database-engine"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "Starten des SQL Server-Agents"
  - "sqlagent90 (Anwendung)"
  - "SQL Server-Agent, starten"
  - "Eingabeaufforderungs-Hilfsprogramme [SQL Server], sqlagent90"
ms.assetid: e8b80e8d-d0c9-4500-a868-0ce08233da08
caps.latest.revision: 34
author: "JennieHubbard"
ms.author: "jhubbard"
manager: "jhubbard"
caps.handback.revision: 34
---
# sqlagent90 (Anwendung)
  Mit der Anwendung **sqlagent90** wird der [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)]-Agent über die Eingabeaufforderung gestartet. Normalerweise sollte der [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)]-Agent über [!INCLUDE[ssManStudioFull](../includes/ssmanstudiofull-md.md)] oder mithilfe von SQL-SMO-Methoden in einer Anwendung gestartet werden. Führen Sie **sqlagent90** nur dann über die Eingabeaufforderung aus, wenn Sie Probleme im [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)]-Agent diagnostizieren, oder wenn Sie von Ihrem primären Anbieter für technischen Support dazu aufgefordert werden.  
  
## Syntax  
  
```  
  
sqlagent90  
-c [-v] [-i instance_name]  
```  
  
## Argumente  
 **-c**  
 Zeigt an, dass der [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)]-Agent über die Eingabeaufforderung ausgeführt wird und unabhängig vom Microsoft Windows-Dienststeuerungs-Manager ist. Wenn **-c** verwendet wird, kann der [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)]-Agent weder über die Anwendung Dienste in der Verwaltung noch über den [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)]-Konfigurations-Manager gesteuert werden. Dieses Argument ist verbindlich.  
  
 **-v**  
 Zeigt an, dass der [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)]-Agent im ausführlichen Modus ausgeführt wird und dass Diagnoseinformationen im Eingabeaufforderungsfenster ausgegeben werden sollen. Die Diagnoseinformationen sind mit den Informationen identisch, die in das Fehlerprotokoll des [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)]-Agents geschrieben werden.  
  
 **-i** *Instanzname*  
 Zeigt an, dass der [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)]-Agent eine Verbindung mit der benannten [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)]-Instanz herstellt, die mit *Instanzname* angegeben wird.  
  
## Hinweise  
 Nach dem Anzeigen einer Copyrightmeldung zeigt **sqlagent90** Ausgaben nur dann im Eingabeaufforderungsfenster an, wenn der Schalter **-v** angegeben ist. Zum Beenden von **sqlagent90** drücken Sie STRG+C an der Eingabeaufforderung. Schließen Sie das Eingabeaufforderungsfenster nicht, bevor Sie **sqlagent90** beendet haben.  
  
## Siehe auch  
 [Automatisierte Administrationstasks &#40;SQL Server Agent&#41;](../ssms/agent/automated-administration-tasks-sql-server-agent.md)  
  
  