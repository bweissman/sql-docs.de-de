---
title: Erstellen einer Serverrolle | Microsoft-Dokumentation
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: security
ms.topic: conceptual
f1_keywords:
- sql12.swb.serverrole.members.f1
- SQL12.SWB.SERVERROLE.GENERAL.F1
- sql12.swb.serverrole.memberships.f1
helpviewer_keywords:
- SERVER ROLE, creating
ms.assetid: 74f19992-8082-4ed7-92a1-04fe676ee82d
author: VanMSFT
ms.author: vanto
manager: craigg
ms.openlocfilehash: d80795317ae9a1d486df2894ab68ee22dfdfc7c2
ms.sourcegitcommit: 3da2edf82763852cff6772a1a282ace3034b4936
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 10/02/2018
ms.locfileid: "48170730"
---
# <a name="create-a-server-role"></a>Erstellen einer Serverrolle
  In diesem Thema wird beschrieben, wie Sie einen neuen Server in [!INCLUDE[ssCurrent](../../../includes/sscurrent-md.md)] mithilfe von [!INCLUDE[ssManStudioFull](../../../includes/ssmanstudiofull-md.md)] oder [!INCLUDE[tsql](../../../includes/tsql-md.md)]erstellen können.  
  
 **In diesem Thema**  
  
-   **Vorbereitungen:**  
  
     [Einschränkungen](#Restrictions)  
  
     [Security](#Security)  
  
-   **So erstellen Sie eine neue Serverrolle mit**  
  
     [SQL Server Management Studio](#SSMSProcedure)  
  
     [Transact-SQL](#TsqlProcedure)  
  
##  <a name="BeforeYouBegin"></a> Vorbereitungsmaßnahmen  
  
###  <a name="Restrictions"></a> Einschränkungen  
 Serverrollen kann keine Berechtigung für sicherungsfähige Elemente auf Datenbankebene gewährt werden. Informationen zum Erstellen von Datenbankrollen finden Sie unter [CREATE ROLE &#40;Transact-SQL&#41;](/sql/t-sql/statements/create-role-transact-sql).  
  
###  <a name="Security"></a> Sicherheit  
  
####  <a name="Permissions"></a> Berechtigungen  
  
-   Erfordert die CREATE SERVER ROLE-Berechtigung oder die Mitgliedschaft in der festen sysadmin-Serverrolle.  
  
-   Erfordert für Anmeldenamen außerdem IMPERSONATE für den *server_principal* , die ALTER-Berechtigung für Serverrollen, die als *server_principal*verwendet werden, oder die Mitgliedschaft in einer Windows-Gruppe, die als server_principal verwendet wird.  
  
-   Wenn Sie die AUTHORIZATION-Option verwenden, um den Besitz für Serverrollen zuzuweisen, sind außerdem folgende Berechtigungen erforderlich:  
  
    -   Um einer Serverrolle einen anderen Anmeldenamen als Besitzer zuzuweisen, ist die IMPERSONATE-Berechtigung für diesen Anmeldenamen erforderlich.  
  
    -   Um einer Serverrolle eine andere Serverrolle als Besitzer zuzuweisen, ist die Mitgliedschaft in der Empfängerserverrolle oder die ALTER-Berechtigung für diese Serverrolle erforderlich.  
  
##  <a name="SSMSProcedure"></a> Verwenden von SQL Server Management Studio  
  
#### <a name="to-create-a-new-server-role"></a>So erstellen Sie eine neue Serverrolle  
  
1.  Erweitern Sie im Objekt-Explorer den Server, auf dem Sie die neue Serverrolle erstellen möchten.  
  
2.  Erweitern Sie den Ordner **Sicherheit** .  
  
3.  Klicken Sie mit der rechten Maustaste auf den Ordner **Serverrollen** , und klicken Sie dann auf **Neue Serverrolle**.  
  
4.  Geben Sie im Dialogfeld **Neue Serverrolle –***server_role_name* auf der Seite **Allgemein** einen Namen für die neue Serverrolle in das Feld **Serverrollenname** ein.  
  
5.  Geben Sie im Feld **Besitzer** den Namen des Serverprinzipals ein, der die neue Rolle besitzt. Klicken Sie alternativ auf die Auslassungspunkte **(…)** , um das Dialogfeld **Serveranmeldenamen oder -rolle auswählen** zu öffnen.  
  
6.  Wählen Sie unter **Sicherungsfähige Elemente**ein oder mehrere sicherungsfähige Elemente auf Serverebene aus. Wenn ein sicherungsfähiges Element ausgewählt ist, können dieser Serverrolle Berechtigungen für dieses sicherungsfähige Element gewährt oder verweigert werden.  
  
7.  Aktivieren Sie im Feld **Berechtigungen: Explizit** das Kontrollkästchen, um für die ausgewählten sicherungsfähigen Elemente Berechtigungen zu gewähren, als Berechtigung mit Recht zum Erteilen zu gewähren oder zu verweigern. Wenn eine Berechtigung nicht für alle ausgewählten sicherungsfähigen Elemente gewährt oder verweigert werden kann, wird die Berechtigung als teilweise ausgewählt dargestellt.  
  
8.  Fügen Sie auf der Seite **Mitglieder** über die Schaltfläche **Hinzufügen** Anmeldungen hinzu, die Einzelpersonen oder Gruppen für die neue Serverrolle darstellen.  
  
9. Eine benutzerdefinierte Serverrolle kann Mitglied einer anderen Serverrolle sein. Aktivieren Sie auf der Seite **Mitgliedschaften** ein Kontrollkästchen, um die aktuelle benutzerdefinierte Serverrolle als Mitglied einer ausgewählten Serverrolle festzulegen.  
  
10. [!INCLUDE[clickOK](../../../includes/clickok-md.md)]  
  
##  <a name="TsqlProcedure"></a> Verwenden von Transact-SQL  
  
#### <a name="to-create-a-new-server-role"></a>So erstellen Sie eine neue Serverrolle  
  
1.  Stellen Sie im **Objekt-Explorer**eine Verbindung mit einer [!INCLUDE[ssDE](../../../includes/ssde-md.md)]-Instanz her.  
  
2.  Klicken Sie in der Standardleiste auf **Neue Abfrage**.  
  
3.  Kopieren Sie das folgende Beispiel, fügen Sie es in das Abfragefenster ein, und klicken Sie auf **Ausführen**.  
  
    ```  
    --Creates the server role auditors that is owned the securityadmin fixed server role.  
    USE master;  
    CREATE SERVER ROLE auditors AUTHORIZATION securityadmin;  
    GO  
    ```  
  
 Weitere Informationen finden Sie unter [CREATE SERVER ROLE &#40;Transact-SQL&#41;](/sql/t-sql/statements/create-server-role-transact-sql).  
  
  
