---
title: Identitätswechsel und Anmeldeinformationen für Verbindungen | Microsoft-Dokumentation
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: clr
ms.topic: reference
helpviewer_keywords:
- impersonation [CLR integration]
- security [CLR integration]
- database objects [CLR integration], connections
- connections [CLR integration]
- authentication [CLR integration]
- user impersonation [CLR integration]
- credentials [CLR integration]
- database objects [CLR integration], security
ms.assetid: 293dce7d-1db2-4657-992f-8c583d6e9ebb
author: rothja
ms.author: jroth
manager: craigg
ms.openlocfilehash: 05f3255dac93940439174c20b11769a022bcb7bd
ms.sourcegitcommit: 3da2edf82763852cff6772a1a282ace3034b4936
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 10/02/2018
ms.locfileid: "48072700"
---
# <a name="impersonation-and-credentials-for-connections"></a>Identitätswechsel und Anmeldeinformationen für Verbindungen
  In der [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] CLR (Common Language Runtime)-Integration ist die Verwendung der Windows-Authentifizierung zwar komplex, jedoch sicherer als die SQL Server-Authentifizierung. Beachten Sie bei Verwendung der Windows-Authentifizierung folgende Punkte:  
  
 Standardmäßig ist für einen SQL Server-Prozess, der eine ausgehende Verbindung mit Windows herstellt, der Sicherheitskontext des Windows-Dienstkontos für SQL Server erforderlich. Es ist jedoch möglich, einer Proxyidentität eine CLR-Funktion zuzuordnen, sodass ausgehende Verbindungen einen anderen Sicherheitskontext haben als die Verbindungen des Windows-Dienstkontos.  
  
 In einigen Fällen bietet es sich an, die Identität des Aufrufers durch Verwenden der `SqlContext.WindowsIdentity`-Eigenschaft statt Ausführen des Dienstkontos anzunehmen. Die `WindowsIdentity`-Instanz repräsentiert die Identität des Clients, der den Aufrufcode aufgerufen hat, und ist nur verfügbar, wenn der Client die Windows-Authentifizierung verwendet hat. Nachdem Sie die `WindowsIdentity`-Instanz erhalten haben, können Sie `Impersonate` aufrufen, um das Sicherheitstoken des Threads zu ändern, und anschließend ADO.NET-Verbindungen im Auftrag des Clients öffnen.  
  
 Nach dem Aufruf von SQLContext.WindowsIdentity.Impersonate Sie nicht auf die lokale Daten zugreifen und Sie können nicht auf Systemdaten zugreifen. Um auf Daten zugreifen müssen Sie in diesem Fall WindowsImpersonationContext.Undo aufrufen.  
  
 Im folgenden Beispiel wird veranschaulicht, wie die Identität des Aufrufers mit der `SqlContext.WindowsIdentity`-Eigenschaft angenommen wird.  
  
 Visual C#  
  
```  
WindowsIdentity clientId = null;  
WindowsImpersonationContext impersonatedUser = null;  
  
clientId = SqlContext.WindowsIdentity;  
  
// This outer try block is used to protect from   
// exception filter attacks which would prevent  
// the inner finally block from executing and   
// resetting the impersonation.  
try  
{  
   try  
   {  
      impersonatedUser = clientId.Impersonate();  
      if (impersonatedUser != null)  
         return GetFileDetails(directoryPath);  
         else return null;  
   }  
   finally  
   {  
      if (impersonatedUser != null)  
         impersonatedUser.Undo();  
   }  
}  
catch  
{  
   throw;  
}  
```  
  
> [!NOTE]  
>  Weitere Informationen zu verhaltensänderungen beim Identitätswechsel, finden Sie unter [wichtige Änderungen an Funktionen der Datenbank-Engine in SQL Server 2014](../../../database-engine/breaking-changes-to-database-engine-features-in-sql-server-2016.md).  
  
 Wenn Sie die [!INCLUDE[msCoName](../../../includes/msconame-md.md)] Windows-Identitätsinstanz erhalten haben, können Sie diese Instanz standardmäßig nicht an einen anderen Computer weitergeben. Die Windows-Sicherheitsinfrastruktur schränkt diese Möglichkeit standardmäßig ein. Es gibt jedoch einen Mechanismus, der als "Delegierung" bezeichnet wird. Dieser ermöglicht die Weitergabe von Windows-Identitäten über mehrere vertrauenswürdige Computer hinweg. Weitere Informationen finden Sie Informationen zu Delegierung in der TechNet-Artikel "[Kerberos-Protokollübergang und eingeschränkte Delegierung](http://go.microsoft.com/fwlink/?LinkId=50419)".  
  
## <a name="see-also"></a>Siehe auch  
 [SqlContext-Objekt](../../clr-integration-data-access-in-process-ado-net/sqlcontext-object.md)  
  
  
