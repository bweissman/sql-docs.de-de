---
title: Migration vom einheitlichen Modus zum SharePoint-Modus (SSRS) | Microsoft-Dokumentation
ms.date: 08/17/2017
ms.prod: reporting-services
ms.prod_service: reporting-services-sharepoint, reporting-services-native
ms.topic: conceptual
ms.assetid: c5b15bec-6fde-4174-bcde-d043307244dd
author: markingmyname
ms.author: maghan
ms.openlocfilehash: d413485fc85b0599921524e339a900a5067f496c
ms.sourcegitcommit: 3daacc4198918d33179f595ba7cd4ccb2a13b3c0
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 10/25/2018
ms.locfileid: "50029249"
---
# <a name="native-to-sharepoint-migration-ssrs"></a>Migration vom einheitlichen vom SharePoint-Modus (SSRS)

[!INCLUDE[ssrs-appliesto](../../includes/ssrs-appliesto.md)] [!INCLUDE[ssrs-appliesto-2016](../../includes/ssrs-appliesto-2016.md)] [!INCLUDE[ssrs-appliesto-not-pbirsi](../../includes/ssrs-appliesto-not-pbirs.md)] [!INCLUDE[ssrs-appliesto-sharepoint-2013-2016i](../../includes/ssrs-appliesto-sharepoint-2013-2016.md)]

  Es ist nicht möglich, Upgrades oder Konvertierungen zwischen verschiedenen [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] -Servermodi auszuführen. Beispielsweise können Sie keinen Berichtsserver im einheitlichen Modus auf den SharePoint-Modus aktualisieren bzw. diesen konvertieren. Das Kopieren der Berichtsserver-Datenbanken zwischen verschiedenen Modi ist nicht möglich, weil die Modi verschiedene Datenbankschemas verwenden. Sie können Inhalte zwischen verschiedenen Berichtsservern migrieren. Welche Tools Sie verwenden, hängt vom Berichtsservermodus ab, der für den Quell- und den Zielserver konfiguriert wurde.  
  
##  <a name="bkmk_native_to_sharepoint"></a> Reporting Services-Migrationstool  
 Das Tool unterstützt die Migration von Inhalten von einer Bereitstellung im einheitlichen Modus zu einer Bereitstellung im SharePoint-Modus. Das Tool unterstützt keine Migration von SharePoint-Modus zu SharePoint-Modus oder vom SharePoint-Modus zum einheitlichen Modus.  
  
 Weitere Informationen finden Sie unter [Reporting Services-Migrationstool](http://www.microsoft.com/download/details.aspx?id=29560) (http://www.microsoft.com/download/details.aspx?id=29560).  
  
## <a name="use-script-to-migrate-content"></a>Migrieren von Inhalten mithilfe von Skripts  
 Wenn das Migrationstool Ihren Anforderungen nicht entspricht, können Sie die Berichtsserverdaten manuell migrieren. Im Folgenden sind die Schritte zusammengefasst, die Sie ausführen, um Berichtselemente von einer [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] -Bereitstellung zu einer anderen zu migrieren. Bei dieser Methode wird der einheitliche Modus oder der SharePoint-Modus als Quell- oder Zielserver unterstützt.  
  
1.  Sichern und stellen Sie die Verschlüsselungsschlüssel wieder her. Dies ist der Schlüssel, der zum Verschlüsseln von Daten verwendet wird. Der Verschlüsselungsschlüssel wird außerdem zur Verschlüsselung von Kennwörtern verwendet, z. B. die für Datenquellenverbindungen gespeicherten Kennwörter. Kennwörter selbst können jedoch nicht migriert werden und müssen in der Zielumgebung erneut eingegeben werden.  
  
2.  **[!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] RSS-Skripts:** Schreiben Sie ein Visual Basic-Skript, das SOAP-Methoden des Berichtsserver-Webdiensts aufruft, um Daten von einer Datenbank in eine andere Datenbank zu kopieren. Verwenden Sie das Hilfsprogramm **RS.exe** , um das Skript auszuführen. RS.exe wird mit [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)]installiert.  
  
    -   [Reporting Services-Beispielskript für "rs.exe" zum Migrieren von Inhalten zwischen Berichtsservern](../../reporting-services/tools/sample-reporting-services-rs-exe-script-to-copy-content-between-report-servers.md). In den Themen wird erläutert, wie Sie das von CodePlex herunterladbare Beispielskript verwenden.  
  
    -   Das RSS-Beispielskript auf CodePlex finden Sie unter [Reporting Services-Skript "RS.exe" zum Migrieren von Inhalten von einem Berichtsserver zu einem anderen](http://azuresql.codeplex.com/releases/view/115207).  
  
    -   [Skripterstellung und PowerShell mit Reporting Services](../../reporting-services/tools/scripting-and-powershell-with-reporting-services.md)  
  
 In der folgenden Tabelle sind die [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] -Objekte zusammengefasst, die Sie mithilfe von Skripts migrieren können:  
  
|Objekt|Skripterstellung möglich|Kommentare|  
|------------|---------------------|--------------|  
|Berichte|Benutzerkontensteuerung|Nach der Migration geben Sie die Kennwörter für Datenquellen erneut ein.|  
|Datenquellen|Benutzerkontensteuerung|Nach der Migration verknüpfen Sie Berichte erneut mit Datenquellen.|  
|Modelle|Benutzerkontensteuerung||  
|Datasets|Benutzerkontensteuerung||  
|Berichtsteile||Nach der Migration überprüfen oder aktualisieren Sie den Pfad zu den Berichtsteilen.|  
|Zeitpläne|Benutzerkontensteuerung|Weitere Informationen finden Sie unter dem Thema zur ListSchedules-Methode [Subscription and Delivery Methods](../../reporting-services/report-server-web-service/methods/subscription-and-delivery-methods.md)|  
|Abonnements|ja|Informationen finden Sie im Thema zur ListSubscriptions-Methode unter [Subscription and Delivery Methods](../../reporting-services/report-server-web-service/methods/subscription-and-delivery-methods.md) und im Thema zur <xref:ReportService2010.ReportingService2010.ChangeSubscriptionOwner%2A> -Methode.|  
|Momentaufnahmen|||

Haben Sie dazu Fragen? [Stellen Sie eine Frage im Reporting Services-Forum](https://go.microsoft.com/fwlink/?LinkId=620231)
