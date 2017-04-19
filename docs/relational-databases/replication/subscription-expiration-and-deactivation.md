---
title: "Abonnementablauf und -deaktivierung | Microsoft Docs"
ms.custom: ""
ms.date: "03/07/2017"
ms.prod: "sql-server-2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "replication"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "Verteiler [SQL Server-Replikation], Beibehaltungsdauer der Verteilung"
  - "Abonnements [SQL Server-Replikation], Ablauf"
  - "Veröffentlichungen [SQL Server-Replikation], Beibehaltungsdauer der Veröffentlichung"
  - "Ablauf [SQL Server-Replikation]"
  - "Aufbewahrungsdauer [SQL Server-Replikation]"
  - "Aufbewahrungsdauer der Veröffentlichung"
  - "Beibehaltungsdauer für die Verteilung"
  - "Abonnements [SQL Server-Replikation], Deaktivierung"
  - "Deaktivieren von Abonnements"
ms.assetid: 4d03f5ab-e721-4f56-aebc-60f6a56c1e07
caps.latest.revision: 45
author: "BYHAM"
ms.author: "rickbyh"
manager: "jhubbard"
caps.handback.revision: 45
---
# Abonnementablauf und -deaktivierung
  Abonnements können deaktiviert werden oder ablaufen, wenn sie nicht innerhalb einer angegebenen *Beibehaltungsdauer*synchronisiert werden. Die stattfindende Aktion hängt vom Typ der Replikation und der überschrittenen Beibehaltungsdauer ab.  
  
 Zum Festlegen von Beibehaltungsdauern finden Sie unter [Festlegen des Ablaufdatums für Abonnements](../../relational-databases/replication/publish/set-the-expiration-period-for-subscriptions.md), [legen die Beibehaltungsdauer für die Verteilung für Transaktionspublikationen & #40; SQL Server Management Studio & #41;](../../relational-databases/replication/set distribution retention period for transactional publications.md), und [konfigurieren, Veröffentlichung und Verteilung](../../relational-databases/replication/configure-publishing-and-distribution.md).  
  
## Transaktionsreplikation  
 Die maximale Beibehaltungsdauer von Transaktionsreplikationen (die **@max_distretention** Parameter [Sp_adddistributiondb & #40; Transact-SQL & #41;](../../relational-databases/system-stored-procedures/sp-adddistributiondb-transact-sql.md)) und die Beibehaltungsdauer der Veröffentlichung (die **@retention** Parameter [Sp_addpublication & #40; Transact-SQL & #41;](../../relational-databases/system-stored-procedures/sp-addpublication-transact-sql.md)):  
  
-   Wenn ein Abonnement nicht innerhalb der maximalen verteilungsbeibehaltungsdauer (standardmäßig 72 Stunden) synchronisiert wird und Änderungen in der Verteilungsdatenbank, die nicht an den Abonnenten übermittelt wurden, das Abonnement wird als deaktiviert gekennzeichnet durch die **Verteilungscleanup** Auftrag, der auf dem Verteiler ausgeführt wird. Das Abonnement muss erneut initialisiert werden.  
  
-   Wenn ein Abonnement nicht innerhalb der Beibehaltungsdauer der Veröffentlichung (standardmäßig 336 Stunden) synchronisiert wird, wird das Abonnement abläuft und gelöscht werden die **Bereinigung abgelaufener Abonnements** Auftrag, der auf dem Verleger ausgeführt wird. Das Abonnement muss neu erstellt und synchronisiert werden.  
  
     Wenn ein Pushabonnement abläuft, wird es vollständig entfernt. Bei Pullabonnements ist dies nicht der Fall. Sie müssen einen Cleanup der Pullabonnements auf dem Abonnenten ausführen. Weitere Informationen finden Sie unter [Delete a Pull Subscription](../../relational-databases/replication/delete-a-pull-subscription.md).  
  
## Mergereplikation  
 Die Mergereplikation verwendet Beibehaltungsdauer der Veröffentlichung (die **@retention** und **@retention_period_unit** Parameter [Sp_addmergepublication & #40; Transact-SQL & #41;](../../relational-databases/system-stored-procedures/sp-addmergepublication-transact-sql.md)). Wenn ein Abonnement abläuft, muss es erneut initialisiert werden, da Metadaten für das Abonnement entfernt werden. Abonnements, die nicht erneut initialisiert werden, werden vom Auftrag **Cleanup abgelaufener Abonnements** gelöscht, der auf dem Verleger ausgeführt wird. Dieser Auftrag wird standardmäßig einmal pro Tag ausgeführt, und es werden dabei alle Pushabonnements gelöscht, die seit einem Zeitraum, der der doppelten Beibehaltungsdauer der Veröffentlichung entspricht, nicht synchronisiert wurden. Beispiel:  
  
-   Wenn eine Veröffentlichung eine Beibehaltungsdauer von 14 Tagen aufweist, kann ein Abonnement ablaufen, wenn es nicht innerhalb von 14 Tagen synchronisiert wurde.  
  
     Wenn auf dem Verleger [!INCLUDE[ssVersion2005](../../includes/ssversion2005-md.md)] oder eine höhere Version ausgeführt wird und der Agent für das Abonnement aus [!INCLUDE[ssVersion2005](../../includes/ssversion2005-md.md)] oder einer höheren Version stammt, läuft ein Abonnement nur ab, wenn Änderungen an den Daten in der Partition dieses Abonnements vorgenommen wurden. Nehmen wir beispielsweise an, dass ein Abonnent Kundendaten nur für Kunden in Deutschland empfängt. Falls die Beibehaltungsdauer auf 14 Tage festgelegt wurde, läuft das Abonnement nur dann am Tag 14 ab, wenn während der letzten 14 Tage Änderungen an den deutschen Kundendaten vorgenommen wurden.  
  
-   14 bis 27 Tage nach der letzten Synchronisierung kann das Abonnement erneut initialisiert werden.  
  
-   28 Tage nach der letzten Synchronisierung wird das Abonnement vom Auftrag **Cleanup abgelaufener Abonnements** gelöscht. Wenn ein Pushabonnement abläuft, wird es vollständig entfernt. Bei Pullabonnements ist dies nicht der Fall. Sie müssen einen Cleanup der Pullabonnements auf dem Abonnenten ausführen. Weitere Informationen finden Sie unter [Delete a Pull Subscription](../../relational-databases/replication/delete-a-pull-subscription.md).  
  
### Überlegungen für das Festlegen der Beibehaltungsdauer der Veröffentlichung für Mergeveröffentlichungen  
 Beachten Sie bei der Festlegung der Beibehaltungsdauer für Mergeveröffentlichungen Folgendes:  
  
-   Die Beibehaltungsdauer für Mergeveröffentlichungen weist eine 24-stündige Kulanzfrist auf, um Abonnenten in unterschiedlichen Zeitzonen aufzunehmen. Wenn Sie beispielsweise eine Beibehaltungsdauer von einem Tag festgelegt haben, beträgt die tatsächliche Beibehaltungsdauer 48 Stunden.  
  
-   Der Cleanup der Metadaten für die Mergereplikation hängt von der Beibehaltungsdauer der Veröffentlichung ab:  
  
    -   Die Replikation kann der Cleanup von Metadaten aus den Veröffentlichungs- und Abonnementdatenbanken erst ausführen, wenn das Ablaufdatum erreicht ist. Geben Sie keinen zu hohen Wert für die Beibehaltungsdauer an, da dies zu einer Beeinträchtigung der Replikationsleistung führen kann. Es wird empfohlen, eine niedrigere Einstellung zu verwenden, wenn Sie zuverlässig einschätzen können, dass alle Abonnenten innerhalb dieser Zeitspanne regelmäßig synchronisiert werden.  
  
    -   Es ist möglich, um anzugeben, dass Abonnements nie ablaufen (Wert 0 für **@retention**), aber es wird dringend empfohlen, dass Sie diesen Wert nicht verwenden, da Metadaten kann nicht bereinigt werden.  
  
-   Die Beibehaltungsdauer für alle Wiederveröffentlichungen muss auf einen Wert festgelegt werden, der gleich oder niedriger ist als die auf dem ursprünglichen Verleger festgelegte Beibehaltungsdauer. Verwenden Sie zudem dieselben Beibehaltungsdauerwerte für Veröffentlichungen für alle Verleger und ihre alternativen Synchronisierungspartner. Das Verwenden unterschiedlicher Werte kann zu mangelnder Konvergenz der Daten führen. Wenn Sie die Beibehaltungsdauer der Veröffentlichung ändern müssen, sollten Sie den Abonnenten erneut initialisieren, um sicherzustellen, dass die Daten konvergieren.  
  
-   Wenn die Beibehaltungsdauer der Veröffentlichung nach einem Cleanup erhöht wird und für ein Abonnement ein Mergevorgang mit dem Verleger versucht wird (auf dem die Metadaten bereits gelöscht wurden), dann läuft das Abonnement nicht ab, weil die Beibehaltungsdauer erhöht wurde. Allerdings verfügt der Verleger nicht über ausreichende Metadaten zum Herunterladen der Änderungen auf den Abonnenten. Dies führt zu mangelnder Konvergenz der Daten.  
  
## Siehe auch  
 [Erneutes Initialisieren von Abonnements](../../relational-databases/replication/reinitialize-subscriptions.md)   
 [Replikations-Agent-Verwaltung](../../relational-databases/replication/agents/replication-agent-administration.md)   
 [Abonnieren von Veröffentlichungen](../../relational-databases/replication/subscribe-to-publications.md)  
  
  