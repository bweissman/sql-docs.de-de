---
title: "Azure Storage-Verbindungs-Manager | Microsoft Docs"
ms.custom: 
  - "SQL2016_New_Updated"
ms.date: "03/01/2017"
ms.prod: "sql-server-2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "integration-services"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "sql13.dts.designer.afpstorageconn.f1"
  - "sql14.dts.designer.afpstorageconn.f1"
ms.assetid: 68bd1d04-d20f-4357-a34e-7c9c76457062
caps.latest.revision: 13
author: "douglaslMS"
ms.author: "douglasl"
manager: "jhubbard"
caps.handback.revision: 11
---
# Azure Storage-Verbindungs-Manager
  Der **Azure Storage-Verbindungs-Manager** ermöglicht es, eine Verbindung zwischen einem SSIS-Paket und einem Azure Storage-Konto mithilfe der Werte zu erstellen, die Sie für die Eigenschaften „Speicherkontoname“ und „Kontoschlüssel“ angeben.  
  
>   [!NOTE] Laden Sie [hier](https://www.microsoft.com/download/details.aspx?id=49492) unbedingt die neueste Version des Azure Feature Pack herunter, um sicherzustellen, dass der Azure Storage-Verbindungs-Manager und die Komponenten, die ihn verwenden (Blobquelle, Blobziel, Blob-Upload- und Blob-Download-Task) sowohl Verbindungen mit allgemeinen Speicherkonten als auch Blobspeicherkonten herstellen können. Weitere Informationen zu diesen beiden Typen von Speicherkonten finden Sie unter [Einführung in Microsoft Azure Storage](https://azure.microsoft.com/en-us/documentation/articles/storage-introduction/#general-purpose-storage-accounts).
  
 Der **Azure Storage-Verbindungs-Manager** ist eine Komponente des SQL Server Integration Services (SSIS) Feature Pack für Azure für SQL Server 2016. Laden Sie das Feature Pack [hier](http://go.microsoft.com/fwlink/?LinkID=626967) herunter.  
  
1.  Wählen Sie im Dialogfeld **SSIS-Verbindungs-Manager hinzufügen** die Option **AzureStorage** aus, und klicken Sie auf **Hinzufügen**.  
  
2.  Wählen Sie im Editor-Dialogfeld „Azure Storage-Verbindungs-Manager“ **Azure-Konto verwenden** aus, um eine Verbindung zu einem Azure Storage-Dienst über das Internet herzustellen, oder wählen Sie **Lokales Entwicklerkonto verwenden** aus, um eine Verbindung zum lokalen Dienst herzustellen, der vom Azure Storage-Emulator gehostet wird.  
  
3.  Gehen Sie bei Auswahl von **Azure-Konto verwenden** folgendermaßen vor:  
  
    1.  Geben Sie Werte in die Felder **Speicherkontoname** und **Kontoschlüssel** an. Diese Werte werden als vertrauliche Daten im SSIS-Paket gespeichert.  
  
    2.  Wählen Sie **HTTPS verwenden** aus, wenn Sie HTTPS anstelle von HTTP für die Verbindung mit dem Azure Storage-Dienst verwenden möchten.  
  
4.  Klicken Sie auf **OK** , um das Dialogfeld zu schließen.  
  
5.  Die Eigenschaften des Verbindungs-Managers, die Sie im Fenster **Eigenschaften** erstellt haben, werden angezeigt.  
  
  