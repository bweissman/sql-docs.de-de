---
title: Dialogfeld „IP-Adresse hinzufügen“ (SQL Server Management Studio) | Microsoft-Dokumentation
ms.custom: ''
ms.date: 06/14/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: high-availability
ms.topic: conceptual
f1_keywords:
- sql12.swb.availabilitygrouplistener.addipaddress.f1
ms.assetid: 98c9ad3b-ff3c-4c1d-b344-59a72fca137c
author: MashaMSFT
ms.author: mathoma
manager: craigg
ms.openlocfilehash: 68bd85258bd3fd259386f020394ffb5bc70a9781
ms.sourcegitcommit: 3da2edf82763852cff6772a1a282ace3034b4936
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 10/02/2018
ms.locfileid: "48164670"
---
# <a name="add-ip-address-dialog-box-sql-server-management-studio"></a>Dialogfeld IP-Adresse hinzufügen (SQL Server Management Studio)
  In diesem F1-Hilfethema werden die Optionen des Dialogfelds **IP-Adresse hinzufügen** beschrieben. Auf dieses Dialogfeld wird über das Dialogfeld **Neuer Verfügbarkeitsgruppenlistener** und über die Registerkarte **Listener** der Seite **Replikate angeben** des [!INCLUDE[ssAoNewAgWiz](../../../includes/ssaonewagwiz-md.md)] oder des [!INCLUDE[ssAoAddRepWiz](../../../includes/ssaoaddrepwiz-md.md)] von [!INCLUDE[ssCurrent](../../../includes/sscurrent-md.md)]zugegriffen.  
  
## <a name="prerequisites"></a>Erforderliche Komponenten  
 Bevor Sie beginnen, einem Verfügbarkeitsgruppenlistener Subnetze hinzuzufügen, stellen Sie sicher, dass Sie die IP-Adresse für jedes Subnetz und bei einer IPv4-Adresse die Subnetzmaske kennen.  
  
##  <a name="PageOptions"></a> Optionen für "IP-Adresse hinzufügen"  
 **Subnetz**  
 Verwenden Sie die Dropdownliste, um eine Adresse für das Subnetz auszuwählen, das Sie dem Verfügbarkeitsgruppenlistener hinzufügen. Standardmäßig besitzt ein Subnetz sowohl eine IPv4-Adresse als auch eine IPv6-Adresse. Beim ersten Verwenden des Dialogfelds **IP-Adresse hinzufügen** zeigt die Dropdownliste **Subnetz** beide Subnetzadressen für jedes Subnetz an, das ein Replikat für die Verfügbarkeitsgruppe hostet. Um dem Listener ein angegebenes Subnetz hinzuzufügen, wählen Sie eine der Subnetzadressen aus.  
  
 Nachdem Sie das Dialogfeld **IP-Adresse hinzufügen** abgeschlossen und auf **OK** geklickt haben, um dem Listener eine ausgewählte Subnetzadresse hinzuzufügen, filtert die Dropdownliste **Subnetz** diese Subnetzadresse heraus. Alle nicht ausgewählten Subnetzadressen verbleiben in der Dropdownliste. Stellen Sie sicher, dass Sie dem Listener nur genau eine Subnetzadresse pro Subnetz hinzufügen, anderenfalls schlägt die Listenererstellung fehl.  
  
 **Adressen**  
 Verwenden Sie dieses Feld, um eine statische IP-Adresse für die ausgewählte Subnetzadresse einzugeben. Wenden Sie sich an Ihren Netzwerkadministrator, um diese IP-Adresse zu erhalten. Stellen Sie sicher, dass Sie eine gültige Adresse für die ausgewählte Subnetzadresse eingeben, anderenfalls schlägt die Listenererstellung fehl.  
  
 **IPv4-Adresse**  
 Wenn Sie die IPv4-Subnetzadresse eines Subnetzes ausgewählt haben, geben Sie hier eine gültige statische IPv4-Adresse ein.  
  
 **Subnetzmaske**  
 Bei einer IPv4-Adresse zeigt dieses schreibgeschützte Feld die Subnetzmaske des ausgewählten Subnetzes an.  
  
 **IPv6-Adresse**  
 Wenn Sie die IPv6-Subnetzadresse eines Subnetzes ausgewählt haben, geben Sie hier eine gültige statische IPv6-Adresse ein.  
  
 **OK**  
 Klicken Sie hier, um das Subnetz, dessen Adresse Sie ausgewählt haben, mit der angegebenen statischen IP-Adresse hinzuzufügen. Dem Subnetzraster des Dialogfelds **Neuer Verfügbarkeitsgruppenlistener** oder **Replikate angeben** wird eine Zeile mit diesen Werten hinzugefügt.  
  
> [!IMPORTANT]  
>  Im Dialogfeld **IP-Adresse hinzufügen** wird die IP-Adresse nicht überprüft. Auch verhindert das Dialogfeld nicht, dass Sie die zweite Subnetzadresse für ein Subnetz hinzufügen, das Sie bereits dem Verfügbarkeitsgruppenlistener hinzugefügt haben.  
  
 **Abbrechen**  
 Klicken Sie, um die Auswahl abzubrechen und zum Dialogfeld **Neuer Verfügbarkeitsgruppenlistener** oder zur Registerkarte **Listener** zurückzukehren, ohne eine statische IP-Adresse für ein Subnetz hinzuzufügen.  
  
  
##  <a name="RelatedTasks"></a> Verwandte Aufgaben  
  
-   [Erstellen oder Konfigurieren eines Verfügbarkeitsgruppenlisteners &#40;SQL Server&#41;](create-or-configure-an-availability-group-listener-sql-server.md)  
  
-   [Verwenden des Dialogfelds Neue Verfügbarkeitsgruppe &#40;SQL Server Management Studio&#41;](use-the-new-availability-group-dialog-box-sql-server-management-studio.md)  
  
-   [Verwenden des Assistenten zum Hinzufügen von Replikaten zu Verfügbarkeitsgruppen &#40;SQL Server Management Studio&#41;](use-the-add-replica-to-availability-group-wizard-sql-server-management-studio.md)  
  
  
## <a name="see-also"></a>Siehe auch  
 [Übersicht über AlwaysOn-Verfügbarkeitsgruppen &#40;SQLServer&#41;](overview-of-always-on-availability-groups-sql-server.md)   
 [Verfügbarkeitsgruppenlistener, Clientkonnektivität und Anwendungsfailover &#40;SQL Server&#41;](../../listeners-client-connectivity-application-failover.md)   
 [AlwaysOn-Clientkonnektivität (SQLServer)](always-on-client-connectivity-sql-server.md)  
  
  
