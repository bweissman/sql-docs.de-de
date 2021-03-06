---
title: Arbeiten mit der Konsole Beispielskriptdateien (OracleToSQL) | Microsoft-Dokumentation
ms.prod: sql
ms.custom: ''
ms.date: 01/19/2017
ms.reviewer: ''
ms.technology: ssma
ms.topic: conceptual
helpviewer_keywords:
- Sample Console Script Files, ServersConnectionFileSample.xml
- Sample Console Script Files, SqlStatementConversionSample.xml
- Sample Console Script Files,VariableValueFileSample.xml
ms.assetid: c6202dcc-b994-457b-9b2f-0cd89e79792d
author: Shamikg
ms.author: Shamikg
manager: v-thobro
ms.openlocfilehash: 2eb30c45af544fc57c0d3dfd328ce2d4c2246746
ms.sourcegitcommit: 61381ef939415fe019285def9450d7583df1fed0
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 10/01/2018
ms.locfileid: "47675308"
---
# <a name="working-with-the-sample-console-script-files-oracletosql"></a>Arbeiten mit den Beispielskriptdateien der Konsole (OracleToSQL)
Einige Beispieldateien wurden für die Benutzer-Verweis und die Verwendung zusammen mit dem Produkt bereitgestellt. Dieser Abschnitt beschreibt die Möglichkeit, diese Skripts entsprechend die Anforderungen der Endbenutzer leicht anpassen.  
  
## <a name="sample-console-script-files"></a>Beispielskriptdateien der Konsole  
Referenz für den Benutzer haben die folgenden Konsole beispielskriptdateien für verschiedene Szenarien bereitgestellt wurde:  
  
-   ServersConnectionFileSample.xml  
  
-   VariableValueFileSample.xml  
  
-   AssessmentReportGenerationSample.xml  
  
-   SqlStatementConversionSample.xml  
  
-   ConversionAndDataMigrationSample.xml  
  
-   **ServersConnectionFileSample.xml:**  
  
    -   In diesem Beispiel gibt die verschiedenen Modi der Verbindung verfügbar, mit der Quelle und Ziel-Datenbank und der Benutzer kann einem anderen Modus gemäß der Anforderung auswählen. Dieses Beispiel enthält die Serverdefinitionen.  
  
    -   Der Benutzer kann einfach die Werte ändern, um die erforderlichen Quell- und Ziel-Serverdefinitionen mit der erforderlichen Datenbank verbinden. Im Beispiel alle Werte wurde bereitgestellt, z.B. Variablenwerte, die in verfügbar sind die **VariableValueFileSample.xml**.  Alle anderen Verbindungsparameter können aus der Verbindung des Benutzers arbeiten Serverdatei entfernt werden.  
  
    -   Weitere Informationen zum Herstellen einer Verbindung mit der Quelle und Ziel-Server finden Sie unter [erstellen den Server Connection Files &#40;OracleToSQL&#41; ](../../ssma/oracle/creating-the-server-connection-files-oracletosql.md) .  
  
-   **VariableValueFileSample.xml:** alle Variablen, die in der Beispielkonsole verwendet wurden, Skriptdateien und `ServersConnectionFileSample.xml` haben in dieser Datei sortiert wurden. Werte mit Benutzer definiert, welche und übergeben Sie diese Datei als ein zusätzliches Befehlszeilenargument zusammen mit der Skriptdatei, zum Ausführen der Beispiel-Console-Skripts, die der Benutzer hat die Variable Beispiel einfach zu ersetzen.  
  
    Weitere Informationen zu der Datei mit Variablen Werten, finden Sie unter [erstellen Variable Value Files &#40;OracleToSQL&#41;](../../ssma/oracle/creating-variable-value-files-oracletosql.md).  
  
-   **AssessmentReportGenerationSample.xml:** in diesem Beispiel kann der Benutzer ein XML-Bewertungsbericht generieren, die verwendet kann vom Benutzer für die Analyse, bevor er beginnt, konvertieren und Migrieren von Daten.  
  
    In der `generate-assessment-report` Befehl, der Benutzer hat den Wert den Variablen Zwischenschritte ändern (finden Sie unter **VariableValueFileSample.xml**) in der `object-name` -Attribut auf die Datenbank Namen an, von dem Benutzer verwendet wird. Je nach Art des Objekts angegeben wird die `object-type` Wert müssen auch geändert werden.  
  
    Wenn der Benutzer verfügt über mehrere Objekte bewerten / er Datenbanken können angeben, mehrere `metabase-object` Knoten wie in der `generate-assessment-report` des Befehls Beispiel 4 von der Konsole-Beispielskriptdatei.  
  
    Weitere Informationen zum Erstellen von Berichten finden Sie unter [Generieren von Berichten &#40;OracleToSQL&#41;](../../ssma/oracle/generating-reports-oracletosql.md).  
  
    > [!NOTE]  
    > -   Sicherstellen, dass der Wert der Variablen Befehlszeilenargument-Datei an die Konsolenanwendung übergeben wird und VariableValueFileSample.xml wird mit den angegebenen Benutzer aktualisiert Werte.  
    > -   Stellen Sie sicher, dass Befehlszeilenargument für Server Connection-Datei an die Konsolenanwendung übergeben wird und die ServersConnectionFileSample.xml mit Parameterwerten für die richtigen Server aktualisiert wird.  
  
-   **SqlStatementConversionSample.xml:**  
    In diesem Beispiel kann der Benutzer die entsprechenden generieren `t-sql` Skript für die Quelldatenbank `sql` Befehls als Eingabe.  
  
    In der `convert-sql-statement` Befehl, der Benutzer hat den Wert den Variablen Zwischenschritte ändern (finden Sie unter **VariableValueFileSample.xml**) in der `context` -Attribut auf den Namen der Datenbank, die von dem Benutzer verwendet wird. Der Benutzer benötigen Sie auch so ändern Sie die `sql` -Attributwert auf die Quelldatenbank `sql` -Befehl, der er konvertiert werden müssen.  
  
    Der Benutzer bieten auch Sql-Dateien konvertiert werden. Dies wurde veranschaulicht, der `convert-sql-statement` des Befehls Beispiel 4 von der Konsole-Beispielskriptdatei.  
  
    > [!NOTE]  
    > Sicherstellen, dass der Wert der Variablen Befehlszeilenargument-Datei an die Konsolenanwendung übergeben wird und VariableValueFileSample.xml wird mit den angegebenen Benutzer aktualisiert Werte.  
  
-   **ConversionAndDataMigrationSample.xml:**  
     In diesem Beispiel kann der Benutzer eine End-to-End-Migration von der Konvertierung in die Datenmigration ausführen. Die Liste der erforderlichen Attributwerte, die sie ändern müssen, ist im folgenden aufgeführt:  
  
    **Befehlsname**  
  
    `map-schema`  
  
    Schemazuordnung der Quelldatenbank mit dem Zielschema.  
  
    **Attribut**  
  
    -   `source-schema:` Gibt an, die Quelldatenbank, die erforderlich sind, konvertiert werden soll.  
  
    -   `sql-server-schema`: Gibt an, die Zieldatenbank, die für die Migration  
  
    **Befehlsname**  
  
    `convert-schema`  
  
    -   Führt die schemakonvertierung aus der Quelle in das Zielschema.  
  
    -   Wenn der Benutzer verfügt über mehrere Objekte bewerten / er Datenbanken können angeben, mehrere `metabase-object` Knoten wie in der `convert-schema` des Befehls Beispiel 4 von der Konsole-Beispielskriptdatei.  
  
    **Attribut**  
  
    `object-name`: Geben Sie die Quelldatenbank / Objektnamen Sie, die erforderlich sind, konvertiert werden soll. Sicherstellen, dass die entsprechenden `object-type` basierend auf dem Typ des Objekts, das im angegebenen geändert wird die `object-name`  
  
    **Befehlsname**  
  
    `synchronize-target`  
  
    -   Synchronisiert die Zielobjekte mit der Zieldatenbank an.  
  
    -   Wenn der Benutzer verfügt über mehrere Objekte bewerten / er Datenbanken können angeben, mehrere `metabase-object` Knoten wie in der `synchronize-target` des Befehls Beispiel 3 von der Konsole-Beispielskriptdatei.  
  
    **Attribut**  
  
    `object-name:` Geben Sie die Sql Server-Datenbank / Objektnamen Sie, die erforderlich sind, erstellt werden. Sicherstellen, dass die entsprechenden `object-type` basierend auf dem Typ des Objekts, das im angegebenen geändert wird die `object-name`  
  
    **Befehlsname**  
  
    `migrate-data`  
  
    -   Werden die Quelldaten zum Ziel migriert.  
  
    -   Wenn der Benutzer verfügt über mehrere Objekte bewerten / er Datenbanken können angeben, mehrere `metabase-object` Knoten wie in der `migrate-data` des Befehls Beispiel 2 von der Konsole-Beispielskriptdatei.  
  
    **Attribut**  
  
    `object-name:` Gibt an, die Quelldatenbank / Tabellen an, der migriert werden muss. Sicherstellen, dass die entsprechenden `object-type` basierend auf dem Typ des Objekts, das im angegebenen geändert wird die `object-name`  
  
## <a name="see-also"></a>Siehe auch  
[Erstellen die Variable Value Files &#40;OracleToSQL&#41;](../../ssma/oracle/creating-variable-value-files-oracletosql.md)  
[Erstellen die Server-Verbindungsdateien &#40;OracleToSQL&#41;](../../ssma/oracle/creating-the-server-connection-files-oracletosql.md)  
[Generieren von Berichten &#40;OracleToSQL&#41;](../../ssma/oracle/generating-reports-oracletosql.md)  
  
