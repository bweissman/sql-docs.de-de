---
title: Azure SQL DW-Uploadtask | Microsoft-Dokumentation
ms.custom: ''
ms.date: 12/29/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology:
- integration-services
ms.topic: conceptual
f1_keywords:
- SQL12.DTS.DESIGNER.AFPDWUPTASK.F1
- SQL11.DTS.DESIGNER.AFPDWUPTASK.F1
ms.assetid: 112cf764-f85a-4c1a-b732-d299d717c0d4
author: yualan
ms.author: douglasl
manager: craigg
ms.openlocfilehash: 651ad07d91d3cf8a351ca6faa9f912c6bd01c07c
ms.sourcegitcommit: 3da2edf82763852cff6772a1a282ace3034b4936
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 10/02/2018
ms.locfileid: "48063700"
---
# <a name="azure-sql-dw-upload-task"></a>Azure SQL DW-Uploadtask
Der **Azure SQL DW-Uploadtask** ermöglicht einem SSIS-Paket, lokale Daten in eine Tabelle in Azure SQL Data Warehouse (DW) hochzuladen. Das gegenwärtig unterstützte Quelldatenformat ist Text mit Trennzeichen in UTF8-Codierung. Der Hochladevorgang folgt den effizienten PolyBase-Ansatz. Insbesondere werden Daten zunächst in Azure Blob Storage und dann in Azure SQL Data Warehouse hochgeladen. Darum ist ein Azure Blob Storage-Konto erforderlich, um diesen Task zu verwenden.

Um einen **Azure SQL DW-Uploadtask**hinzuzufügen, ziehen Sie ihn mittels Drag &amp; Drop aus der SSIS-Toolbox auf den Designercanvas, und doppelklicken Sie, oder klicken Sie mit der rechten Maustaste darauf, und klicken Sie anschließend auf **Bearbeiten** , um das Dialogfeld des Task-Editors anzuzeigen.

Konfigurieren Sie auf der Seite **Allgemein** die folgenden Eigenschaften.

Feld|Description
-----|-----------
LocalDirectory|Gibt das lokale Verzeichnis mit den Datendateien an, die hochgeladen werden sollen.
Rekursiv|Gibt an, ob Unterverzeichnisse rekursiv durchsucht werden sollen.
FileName|Geben Sie einen Namensfilter zum Auswählen von Dateien mit einem bestimmten Namensmuster an. Beispiel: „MeinArbeitsblatt\*.xsl\* “ schließt „MeinArbeitsblatt001.xsl“ und „MeinArbeitsblattABC.xslx“ ein.
RowDelimiter|Gibt ein oder mehrere Zeichen an, die das Ende jeder Zeile markieren.
ColumnDelimiter|Gibt ein oder mehrere Zeichen an, die das Ende jeder Spalte markieren. Beispiel: &#124; (senkrechter Strich), \t (Tabulator), ' (einfaches Anführungszeichen), " (doppeltes Anführungszeichen) und 0x5c (umgekehrter Schrägstrich).
IsFirstRowHeader|Gibt an, ob die erste Zeile in jeder Datendatei Spaltennamen statt tatsächlicher Daten enthält.
AzureStorageConnection|Gibt einen Azure Storage-Verbindungs-Manager an.
BlobContainer|Gibt den Namen des Blobcontainers an, zu dem lokale Daten hochgeladen und über PolyBase an Azure DW weitergeleitet werden. Falls noch nicht vorhanden ist, wird ein neuer Container erstellt.
BlobDirectory|Gibt das Blobverzeichnis an (virtuelle Hierarchiestruktur), zu dem lokale Daten hochgeladen und über PolyBase an Azure DW weitergeleitet werden.
RetainFiles|Gibt an, ob die zu Azure Storage hochgeladenen Dateien beibehalten werden sollen.
CompressionType|Gibt an, welches Komprimierungsformat beim Hochladen von Dateien in Azure Storage verwendet werden soll. Die lokale Quelle ist nicht betroffen.
CompressionLevel|Gibt an, welcher Komprimierungsgrad für das Komprimierungsformat verwendet werden soll.
AzureDwConnection|Gibt einen ADO.NET-Verbindungs-Manager für Azure SQL Data Warehouse an.
TableName|Gibt den Namen der Zieltabelle an. Wählen Sie entweder einen vorhandenen Tabellennamen, oder erstellen Sie einen neuen durch Auswahl von **\<<Neue Tabelle...>**.
TableDistribution|Gibt die Verteilungsmethode für die neue Tabelle an. Gilt, wenn für **TableName**ein neuer Tabellenname angegeben wird.
HashColumnName|Gibt an, welche Spalte für die Verteilung der Hashtabelle verwendet werden soll. Gilt, wenn **HASH** für **TableDistribution**angegeben wird.

Je nachdem, ob Sie zu einer neuen oder einer vorhandenen Tabelle hochladen, sehen Sie eine andere Seite **Zuordnungen** . Konfigurieren Sie im ersten Fall, welche Quellspalten zugeordnet werden sollen, sowie ihre entsprechenden Namen in der zu erstellenden Zieltabelle. Konfigurieren Sie im letzten Fall die Zuordnungsbeziehungen zwischen Quell- und Zielspalten.

Konfigurieren Sie auf der Seite **Spalten** die Datentypeigenschaften für jede Quellspalte.

Die Seite **T-SQL** zeigt das zum Laden von Daten aus Azure Blob Storage in Azure SQL Data Warehouse verwendete T-SQL an. Das T-SQL wird automatisch von Konfigurationen auf den anderen Seiten generiert und als Teil der Taskausführung ausgeführt. Um das generierte T-SQL wahlweise nach Ihren speziellen Bedürfnissen manuell zu bearbeiten, klicken Sie auf die Schaltfläche **Bearbeiten** . Sie können später durch Klicken auf die Schaltfläche **Zurücksetzen** das automatisch generierte wiederherstellen.
