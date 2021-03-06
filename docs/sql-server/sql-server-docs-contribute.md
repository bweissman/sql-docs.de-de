---
title: Mitwirken an der SQL Server-Dokumentation | Microsoft-Dokumentation
ms.date: 08/13/2018
ms.prod: sql
ms.reviewer: ''
ms.custom: ''
ms.topic: conceptual
author: rothja
ms.author: jroth
manager: craigg
monikerRange: '>= aps-pdw-2016 || = azuresqldb-current || = azure-sqldw-latest || >= sql-server-2016 || >= sql-server-linux-2017 || = sqlallproducts-allversions'
ms.openlocfilehash: 881189fdec593d48b443d85ee548ca1bb80b24a8
ms.sourcegitcommit: 7fe14c61083684dc576d88377e32e2fc315b7107
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 10/26/2018
ms.locfileid: "50146055"
---
# <a name="how-to-contribute-to-sql-server-documentation"></a>Mitwirken an der SQL Server-Dokumentation

[!INCLUDE[appliesto-ss-asdb-asdw-pdw-md.md](../includes/appliesto-ss-asdb-asdw-pdw-md.md)]

An der SQL Server-Dokumentation kann jeder mitwirken. Beispielsweise können Rechtschreibfehler korrigiert, genauere Erklärungen vorgeschlagen und die technische Richtigkeit geprüft werden. In diesem Artikel werden die ersten Schritte hierfür beschrieben.

Wenn Sie zur Dokumentation beitragen möchten, stehen Ihnen zwei Hauptworkflows zur Verfügung:

|||
|---|---|
| [Bearbeiten von Inhalten im Browser](#githubui) | Geeignet für kleinere Bearbeitungen eines Artikels |
| [Lokales Bearbeiten von Inhalten mit Tools](#tools) | Geeignet für komplexere Bearbeitungen in mehreren Artikeln und bei häufigen Beiträgen für docs.microsoft.com |

## <a id="githubui"></a> Bearbeiten von Inhalten im Browser

Sie können im Browser einfache Änderungen an SQL Server-Inhalten vornehmen und diese dann an Microsoft übermitteln. Der vollständige Ablauf ist im Artikel [Leitfaden für Mitwirkende an der Microsoft-Dokumentation: Übersicht](https://docs.microsoft.com/contribute/#quick-edits-to-existing-documents) dokumentiert. Im folgenden Video wird der gesamte Ablauf zur Übermittlung von Änderungen in Ihrem Browser veranschaulicht:

> [!VIDEO https://www.microsoft.com/en-us/videoplayer/embed/RE23pxh]

> [!TIP]
> Beachten Sie, dass die Position der Schaltfläche **Bearbeiten** etwas anders ist als im Video, doch der Ablauf ist derselbe.
>
> ![Schaltfläche „Bearbeiten“](./media/sql-server-docs-contribute/edit-sql-server-docs.png)

## <a id="tools"></a> Lokales Bearbeiten von Inhalten mit Tools

Eine weitere Bearbeitungsoption besteht darin, das **sql-docs**- oder **azure-docs**-Repository zu forken und es lokal auf dem Computer zu klonen. Anschließend können Sie mithilfe eines Markdown-Editors und eines Git-Clients die Änderungen übermitteln. Dieser Workflow eignet sich für Bearbeitungen, die komplexer sind oder mehrere Dateien betreffen. Außerdem ist er gut für Mitwirkende geeignet, die häufig Beiträge bei docs.microsoft.com einreichen.

Weitere Informationen zu dieser Bearbeitungsoption finden Sie in den folgenden Artikeln:

- [Einrichten eines GitHub-Kontos](https://docs.microsoft.com/contribute/get-started-setup-github)
- [Install content authoring tools (Installieren von Erstellungstools für Inhalte)](https://docs.microsoft.com/contribute/get-started-setup-tools)
- [Lokales Einrichten von Git für die Dokumentation](https://docs.microsoft.com/contribute/get-started-setup-local)
- [Verwenden von Tools zum Einreichen von Änderungen](https://docs.microsoft.com/contribute/how-to-write-workflows-major)

Wenn Sie einen Pull Request mit umfassenden Änderungen an der Dokumentation einreichen, wird in GitHub ein Kommentar angezeigt, in dem Sie aufgefordert werden, online eine **Lizenzvereinbarung für Mitwirkende** zu übermitteln. Sie müssen dieses Onlineformular ausfüllen, damit Ihr Pull Request akzeptiert wird.

## <a name="recognition"></a>Nennung als Mitwirkender

Nachdem Ihre Änderungen akzeptiert wurden, werden Sie am Anfang des Artikels als Mitwirkender genannt.

![Nennung als Mitwirkender bei Einreichung von Inhaltsänderungen](./media/sql-server-docs-contribute/contribution-recognition.png)

## <a name="sql-docs-overview"></a>Übersicht über sql-docs

Dieser Abschnitt enthält zusätzliche Hinweise zur Arbeit mit dem **sql-docs**-Repository.

> [!IMPORTANT]
> Diese beziehen sich ausschließlich auf **sql-docs**. Wenn Sie stattdessen einen SQL-Artikel der Azure-Dokumentation bearbeiten, finden Sie auf [GitHub in der Infodatei des azure-docs-Repositorys](https://github.com/MicrosoftDocs/azure-docs/blob/master/README.md) weitere Informationen.

Zur Organisation von Inhalten werden im [sql-docs](https://github.com/MicrosoftDocs/sql-docs)-Repository die folgenden Standardordner verwendet:

| Ordner | und Beschreibung |
|---|---|
| [docs](https://github.com/MicrosoftDocs/sql-docs/tree/live/docs) | Enthält alle veröffentlichten SQL Server-Inhalte. In Unterordnern werden verschiedene Inhaltsbereiche organisiert. |
| [docs/includes](https://github.com/MicrosoftDocs/sql-docs/tree/live/docs/includes) | Enthält Includedateien. Diese Dateien bestehen aus Inhaltsblöcken, die in ein oder mehrere Artikel aufgenommen werden können. |
| **./media** | Jeder Ordner kann über einen **media**-Unterordner für Artikelbilder verfügen. Der **media**-Ordner enthält wiederum Unterordner mit denselben Namen der Artikel, in denen die Bilder angezeigt werden. Bei den Bildern sollte es sich um PNG-Dateien handeln, deren Dateinamen aus Kleinbuchstaben bestehen und keine Leerzeichen enthalten. |
| **TOC.MD** | Eine Inhaltsverzeichnisdatei. In jedem Unterordner kann eine TOC.MD-Datei verwendet werden. |

#### <a name="applies-to-includes"></a>applies-to-Includedateien

In jedem SQL Server-Artikel befindet sich nach dem Titel ein Verweis auf die **applies-to**-Includedatei. Damit wird angegeben, auf welche Bereiche oder Versionen von SQL Server sich der Artikel bezieht.

Im folgenden Markdown-Beispiel wird die Includedatei **appliesto-ss-asdb-asdw-pdw-md.md** abgerufen.

```Markdown
[!INCLUDE[appliesto-ss-asdb-asdw-pdw-md](../includes/appliesto-ss-asdb-asdw-pdw-md.md)]
```

Dadurch wird der folgende Text am Anfang des Artikels angezeigt:

![applies-to-Text](./media/sql-server-docs-contribute/applies-to.png)

Mit den folgenden Tipps finden Sie die richtige applies-to-Includedatei für Ihren Artikel:

- Eine Liste häufig verwendeter Includedateien finden Sie unter [SQL Server-Includedateien für die Versionsverwaltung und „Applies-to“](applies-to-includes.md).
- Suchen Sie nach anderen Artikeln, in denen es um dasselbe Feature oder um eine vergleichbare Aufgabe geht. Wenn Sie diese Artikel bearbeiten, können Sie das Markdown-Element für den Link zur applies-to-Includedatei kopieren. Dabei können Sie die Bearbeitung abbrechen, ohne die Änderungen zu senden.
- Durchsuchen Sie das Verzeichnis [docs/includes](https://github.com/MicrosoftDocs/sql-docs/tree/live/docs/includes) nach Dateien, die den Text „applies-to“ enthalten. Über die Schaltfläche **Find** (Suchen) können Sie in GitHub die Ergebnisse schnell filtern. Klicken Sie auf die Datei, um festzustellen, wie diese gerendert wird.
- Beachten Sie die Namenskonvention. Wenn der Name mehrmals den Buchstaben „x“ enthält, ist dieser vermutlich ein Platzhalter, der darauf hinweist, dass ein bestimmter Dienst nicht unterstützt wird. Durch **appliesto-xx-xxxx-asdw-xxx-md.md** wird beispielsweise angegeben, dass ausschließlich Azure SQL Data Warehouse unterstützt wird, da nur die Zeichenfolge **asdw** vorhanden ist. Die anderen Felder enthalten hingegen nur den Buchstaben „x“.
- In einigen Includedateien werden Versionsnummern wie **tsql-appliesto-ss2017-xxxx-xxxx-xxx-md.md** angegeben. Verwenden Sie diese Includedateien nur, wenn Sie wissen, dass dieses Feature mit einer bestimmten Version von SQL Server eingeführt wurde.

## <a name="contributor-resources"></a>Ressourcen für Mitwirkende

- [Leitfaden für Mitwirkende an der Dokumentation auf docs.microsoft.com](https://docs.microsoft.com/contribute/)
- [Microsoft-Styleguide](https://docs.microsoft.com/teamblog/style-guide)
- [Markdown-Grundlagen](https://help.github.com/articles/getting-started-with-writing-and-formatting-on-github/)

> [!TIP]
> Wenn Sie nicht Feedback zur Dokumentation, sondern zu einem SQL Server-Produkt geben möchten, können Sie die [hierfür eingerichtete Seite](https://feedback.azure.com/forums/908035-sql-server) nutzen.

## <a name="next-steps"></a>Nächste Schritte

Auf GitHub können Sie einen genaueren Blick auf das [sql-docs-Repository](https://github.com/MicrosoftDocs/sql-docs) werfen.

Außerdem haben Sie die Möglichkeit, Artikel zu suchen, Änderungen einzureichen und die SQL Server-Community zu unterstützen. 

Wir bedanken uns für Ihre Hilfe.
