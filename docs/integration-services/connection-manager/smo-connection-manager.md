---
title: "SMO-Verbindungs-Manager | Microsoft Docs"
ms.custom: ""
ms.date: "03/14/2017"
ms.prod: "sql-server-2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "integration-services"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "Verbindungen [Integration Services], SMO"
  - "SMO-Verbindungs-Manager"
  - "Verbindungs-Manager [Integration Services], SMO"
ms.assetid: d273f1fb-a6a8-4f2f-a5ff-55c2e3de4723
caps.latest.revision: 21
author: "douglaslMS"
ms.author: "douglasl"
manager: "jhubbard"
caps.handback.revision: 21
---
# SMO-Verbindungs-Manager
  Mit einem SMO-Verbindungs-Manager kann ein Paket eine Verbindung mit einem SMO-Server (SQL Management Object) herstellen. Die Übertragungstasks von [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] verwenden einen SMO-Verbindungs-Manager. Beispielsweise verwendet der Task Anmeldungen übertragen, der [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] -Anmeldungen überträgt, einen SMO-Verbindungs-Manager.  
  
 Wenn Sie einem Paket einen SMO-Verbindungs-Manager hinzufügen, erstellt [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] einen Verbindungs-Manager, der zur Laufzeit in eine SMO-Verbindung aufgelöst wird, die Eigenschaften des Verbindungs-Managers festlegt und der **Connections**-Sammlung im Paket den Verbindungs-Manager hinzufügt. Die **ConnectionManagerType** -Eigenschaft des Verbindungs-Managers ist auf **SMOServer**festgelegt.  
  
 Es gibt folgende Möglichkeiten, um einen SMO-Verbindungs-Manager zu konfigurieren:  
  
-   Geben Sie den Namen eines Servers an, auf dem [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] installiert ist.  
  
-   Wählen Sie den Authentifizierungsmodus zum Herstellen einer Verbindung mit dem Server aus.  
  
## Konfiguration des SMO-Verbindungs-Managers  
 Sie können Eigenschaften mit dem [!INCLUDE[ssIS](../../includes/ssis-md.md)] -Designer oder programmgesteuert festlegen.  
  
 Weitere Informationen zu den Eigenschaften, die Sie im [!INCLUDE[ssIS](../../includes/ssis-md.md)]-Designer festlegen können, finden Sie unter [SMO-Verbindungs-Manager-Editor](../../integration-services/connection-manager/smo-connection-manager-editor.md).  
  
 Weitere Informationen zum programmgesteuerten Konfigurieren eines Verbindungs-Managers finden Sie unter <xref:Microsoft.SqlServer.Dts.Runtime.ConnectionManager> und [Programmgesteuertes Hinzufügen von Verbindungen](../../integration-services/building-packages-programmatically/adding-connections-programmatically.md).  
  
## Siehe auch  
 [Integration Services-Verbindungen &#40;SSIS&#41;](../../integration-services/connection-manager/integration-services-ssis-connections.md)  
  
  