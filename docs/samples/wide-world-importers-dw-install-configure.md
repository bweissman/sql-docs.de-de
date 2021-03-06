---
title: Beispieldatenbank "WideWorldImporters OLAP" – installieren und konfigurieren Sie-SQL | Microsoft-Dokumentation
ms.prod: sql
ms.prod_service: sql
ms.technology: samples
ms.custom: ''
ms.date: 08/04/2018
ms.reviewer: ''
ms.topic: conceptual
author: MashaMSFT
ms.author: mathoma
manager: craigg
monikerRange: '>=sql-server-2016||>=sql-server-linux-2017||=azure-sqldw-latest||>=aps-pdw-2016||=sqlallproducts-allversions||=azuresqldb-mi-current'
ms.openlocfilehash: 47e2e35095f60e3dec3960b5a83ac8d7ca710ebc
ms.sourcegitcommit: 61381ef939415fe019285def9450d7583df1fed0
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 10/01/2018
ms.locfileid: "47706928"
---
# <a name="wideworldimportersdw-installation-and-configuration"></a>"Wideworldimportersdw" Installation und Konfiguration
[!INCLUDE[appliesto-ss-xxxx-asdw-pdw-md](../includes/appliesto-ss-xxxx-asdw-pdw-md.md)]
Installations- und konfigurationsanweisungen für die Datenbank "wideworldimportersdw".

- [SQL Server 2016](https://www.microsoft.com/evalcenter/evaluate-sql-server-2016) (oder höher) oder [Azure SQL-Datenbank](https://azure.microsoft.com/services/sql-database/). Um die vollständige Version des Beispiels verwenden zu können, verwenden Sie SQL Server-Evaluierung, Developer, Enterprise Edition.
- [SQL Server Management Studio](../ssms/download-sql-server-management-studio-ssms.md). Für die besten Ergebnisse verwenden Sie das Release vom Juni 2016 oder höher.

## <a name="download"></a>Herunterladen

Die neueste Version des Beispiels:

[wide-world-importers-release](http://go.microsoft.com/fwlink/?LinkID=800630)

Herunterladen Sie die Beispiel "wideworldimportersdw" Datenbank sichern/bacpac-Datei, die entspricht Ihrer Version von SQL Server oder Azure SQL-Datenbank.

Quellcode die-Beispieldatenbank neu zu erstellen ist aus folgendem Ort verfügbar. Beachten Sie, dass das Auffüllen der Daten auf ETL aus der OLTP-Datenbank ("wideworldimporters"):

[wide-world-importers-source](https://github.com/Microsoft/sql-server-samples/tree/master/samples/databases/wide-world-importers/wwi-dw-database-scripts)

## <a name="install"></a>Install


### <a name="sql-server"></a>SQL Server

Um eine Sicherung einer SQL Server-Instanz wiederherzustellen, können Sie Management Studio verwenden.

1. Öffnen Sie SQL Server Management Studio, und Verbinden mit der SQL Server-Zielinstanz.
2. Mit der rechten Maustaste auf die **Datenbanken** Knoten, und wählen **Restore Database**.
3. Wählen Sie **Gerät** und klicken Sie auf die Schaltfläche mit den **...**
4. Im Dialogfeld **Sicherungsmedien auswählen**, klicken Sie auf **hinzufügen**, navigieren Sie zu der datenbanksicherung in das Dateisystem des Servers ein, und wählen Sie die Sicherung. Klicken Sie auf **OK**.
5. Bei Bedarf ändern, das der Zielort für die Daten und Protokolldateien, in der **Dateien** Bereich. Beachten Sie, dass es wird empfohlen, zum Hinzufügen von Daten und Protokolldateien auf verschiedenen Laufwerken.
6. Klicken Sie auf **OK**. Dadurch wird die Wiederherstellung der Datenbank ausgelöst. Nachdem der Vorgang abgeschlossen ist, müssen Sie die Datenbank "wideworldimporters" auf Ihrer SQL Server-Instanz installiert.

### <a name="azure-sql-database"></a>Azure SQL-Datenbank

Zum Importieren einer bacpac-Datei in eine neue SQL-Datenbank können Sie Management Studio verwenden.

1. (optional) Wenn Sie noch keinem SQL Server in Azure verfügen, navigieren Sie zu der [Azure-Portal](https://portal.azure.com/) , und erstellen Sie eine neue SQL-Datenbank. Dabei wird eine Datenbank erstellen, erstellen Sie einen Server. Notieren Sie den Server.
   - Finden Sie unter [in diesem Tutorial](https://azure.microsoft.com/documentation/articles/sql-database-get-started/) zum Erstellen einer Datenbank in wenigen Minuten
2. Öffnen Sie SQL Server Management Studio, und Verbinden mit Ihrem Server in Azure.
3. Mit der rechten Maustaste auf die **Datenbanken** Knoten, und wählen **Import Data-Tier Application**.
4. In der **Importeinstellungen** wählen **vom lokalen Datenträger importieren** , und wählen Sie die bacpac-Datei der Beispieldatenbank aus Ihrem Dateisystem.
5. Klicken Sie unter **Datenbankeinstellungen** ändern Sie den Datenbanknamen an *"wideworldimportersdw"* , und wählen Sie die Ziel-Edition und das dienstziel verwenden.
6. Klicken Sie auf **Weiter** und **Fertig stellen** um die Bereitstellung zu starten. Es dauert einige Minuten. Wenn Sie einen Zielpunkt niedriger als S2 angeben, kann es länger dauern.

## <a name="configuration"></a>Konfiguration

[Gilt für SQL Server 2016 (und höher) Enterprise/Developer/Evaluation-Edition]

Die Beispieldatenbank kann Verwenden von PolyBase zur Abfrage von Dateien in Hadoop oder Azure Blob Storage. Allerdings das Feature wird nicht standardmäßig installiert, mit SQL Server – müssen Sie es während des Setups von SQL Server auswählen. Aus diesem Grund ist ein Schritt nach der Installation erforderlich.

1. In SQL Server Management Studio eine Verbindung herstellen Sie, auf die Datenbank "wideworldimportersdw" aus, und öffnen Sie ein neues Abfragefenster.
2. Führen Sie den folgenden T-SQL-Befehl, um die Verwendung von PolyBase in der Datenbank zu aktivieren:

   Führen Sie [Anwendung]. [Configuration_ApplyPolyBase]
