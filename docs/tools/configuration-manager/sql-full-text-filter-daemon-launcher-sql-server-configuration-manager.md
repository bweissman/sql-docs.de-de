---
title: "Startprogramm f&#252;r SQL-Volltextfilterdaemon (SQL Server-Konfigurations-Manager) | Microsoft Docs"
ms.custom: ""
ms.date: "03/14/2017"
ms.prod: "sql-server-2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "database-engine"
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: d0dc03db-5f76-4558-b041-1ac7b9b5bb16
caps.latest.revision: 8
author: "BYHAM"
ms.author: "rickbyh"
manager: "jhubbard"
caps.handback.revision: 8
---
# Startprogramm f&#252;r SQL-Volltextfilterdaemon (SQL Server-Konfigurations-Manager)
  Ab [!INCLUDE[ssKatmai](../../includes/sskatmai-md.md)] wird der FDHOST (SQL-Volltextfilterdaemon)-Startprogrammdienst von der [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]-Volltextsuche zum Starten des Filterdaemon-Hostprozesses verwendet, der für das Filtern bei der Volltextsuche und die Wörtertrennung verantwortlich ist. Dieser Dienst muss ausgeführt werden, damit die Volltextsuche verwendet werden kann. Der FDHOST-Startprogrammdienst ist ein instanzabhängiger Dienst, dem eine bestimmte Instanz von [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] zugeordnet ist. Der FDHOST-Startprogrammdienst gibt die Dienstkontoinformationen an jeden gestarteten Filterdaemon-Hostprozess weiter. Informationen zu den Prozessen des Filterdaemonhosts finden Sie unter „Architektur der Volltextsuche“ in der [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]-Onlinedokumentation.  
  
  