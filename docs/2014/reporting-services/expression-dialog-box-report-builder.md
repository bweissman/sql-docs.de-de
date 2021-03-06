---
title: Ausdruck (Dialogfeld) (Berichts-Generator) | Microsoft-Dokumentation
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology:
- reporting-services-native
ms.topic: conceptual
f1_keywords:
- "10040"
helpviewer_keywords:
- expressions
ms.assetid: e89c4d97-5d41-4b55-8695-79329edac15d
author: maggiesmsft
ms.author: douglasl
manager: craigg
ms.openlocfilehash: 6df6a544e02eeef685234fad0ca11d0bc898e617
ms.sourcegitcommit: 3da2edf82763852cff6772a1a282ace3034b4936
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 10/02/2018
ms.locfileid: "48220900"
---
# <a name="expression-dialog-box-report-builder"></a>Ausdruck (Dialogfeld) (Berichts-Generator)
  Verwenden der **Ausdruck** Dialogfeld schreiben [!INCLUDE[msCoName](../includes/msconame-md.md)] [!INCLUDE[vbprvb](../includes/vbprvb-md.md)] -Ausdrücke für berichtselementeigenschaften-Elementeigenschaften. Mit Ausdrücken können Sie zahlreiche Eigenschaften wie Farbe, Schriftart und Rahmen festlegen. Zur Laufzeit werden die Ausdrücke vom Berichtsprozessor ausgewertet, und das Ergebnis wird durch den Wert der Eigenschaft ersetzt.  
  
 Das Dialogfeld **Ausdruck** enthält ein Codefenster, eine Kategoriestruktur, Kategorieelemente, einen Beschreibungsbereich sowie einen Beispielbereich. Die **Ausdruck** Dialogfeld ist kontextabhängig; die Kategorieelemente und Beschreibungen verändern sich der Ausdruckskategorie, mit dem Sie arbeiten. Weitere Informationen finden Sie unter [Beispiele für Ausdrücke &#40;Berichts-Generator und SSRS&#41;](report-design/expression-examples-report-builder-and-ssrs.md), [Ausdrücke &#40;Berichts-Generator und SSRS&#41;](report-design/expressions-report-builder-and-ssrs.md)  
  
## <a name="expression-constructs"></a>Ausdruckskonstrukte  
 Ausdrücke beginnen mit einem Gleichheitszeichen (=) und können Konstanten, Literale, Operatoren und Verweise auf integrierte Felder, Auflistungen und Funktionen, [!INCLUDE[vbprvb](../includes/vbprvb-md.md)]-Laufzeitbibliotheksfunktionen, [!INCLUDE[dnprdnshort](../includes/dnprdnshort-md.md)]-CLR-Klassen (Common Language Runtime) sowie benutzerdefinierte Funktionen enthalten. Die folgende Liste beschreibt die Kategorien und Werte, die Sie einem Ausdruck hinzufügen können.  
  
 **Ausdruck festlegen für:***\<PropertyName >*   
 Der Name der Eigenschaft, für die Sie einen Ausdruck definieren. Sie können diese Einstellung auch im Eigenschaftenfenster nach dem Namen vornehmen.  
  
 **Konstanten**  
 Stellt für Eigenschaften, die auf Konstanten basieren, eine Liste vordefinierter gültiger Werte für diese Eigenschaft bereit. Beispielsweise zeigt eine Eigenschaft auf Grundlage der Farbe gültige Farbnamen an. Für eine Eigenschaft, die einen booleschen Datentyp darstellt, lauten die Werte `True` und `False`.  
  
 Nicht alle Elemente, die Ausdrücke unterstützen, können auf eine Konstante festgelegt werden. Wenn eine Eigenschaft nicht auf einen konstanten Wert festgelegt werden kann, ist dies in der Beschreibung angegeben.  
  
 **Integrierte Felder**  
 Bietet eine Liste der in der globalen Auflistung enthaltenen Elemente, die Sie in einem Ausdruck verwenden können. Einige Auflistungen werden nur unterstützt, nachdem der Bericht auf dem Server veröffentlicht wurde. Weitere Informationen finden Sie unter [Integrierte Sammlungen in Ausdrücken &#40;Berichts-Generator und SSRS&#41;](report-design/built-in-collections-in-expressions-report-builder.md).  
  
 **Parameter**  
 Bietet eine Liste von Berichtsparametern.  
  
 **Felder (**  *\<Ausgewähltes Dataset >* **)**  
 Zeigt die Liste von Feldern für das in der Datasets-Kategorie ausgewählte Dataset an. Doppelklicken Sie auf ein Feld, um es in das Feld **Ausdruck** zu kopieren.  
  
 **Datasets**  
 Bietet eine Liste der verfügbaren Datasets und zeigt die Felder an, die Mitglied des Datasets sind.  
  
 **Variablen**  
 Zeigt eine Liste von Berichtsvariablen an. Weitere Informationen finden Sie unter [Verweise auf Berichts- und Gruppenvariablenauflistungen &#40;Berichts-Generator und SSRS&#41;](report-design/built-in-collections-report-and-group-variables-references-report-builder.md).  
  
 **Operatoren**  
 Zeigt die Operatoren an, die Sie in einer Berechnung oder bei einer Zeichenfolgebearbeitung verwenden können. Weitere Informationen finden Sie unter [Operatoren in Ausdrücken &#40;Berichts-Generator und SSRS&#41;](report-design/operators-in-expressions-report-builder-and-ssrs.md).  
  
 **Allgemeine Funktionen**  
 Zeigt allgemeine, nach Typ gruppierte Funktionen an. Wenn Sie im Bereich Element eine Funktion auswählen, werden eine Beschreibung und ein Beispiel angezeigt.  
  
 Zu den häufig verwendeten Funktionen gehören integrierte Berichts- und Aggregationsfunktionen, [!INCLUDE[vbprvb](../includes/vbprvb-md.md)]-Laufzeitbibliotheksfunktionen und [!INCLUDE[dnprdnshort](../includes/dnprdnshort-md.md)] Common Language Runtime (CLR)-Klassen im <xref:System.Math>- und <xref:System.Convert>-Namespace. Sie können auch Verweise auf CLR-Klassen und externe Assemblys hinzufügen, die nicht in der Kategorieliste angezeigt werden. Weitere Informationen finden Sie unter [Benutzerdefinierter Code und Assemblyverweise in Ausdrücken in Berichts-Designer &#40;SSRS&#41;](report-design/custom-code-and-assembly-references-in-expressions-in-report-designer-ssrs.md).  
  
## <a name="options"></a>Tastatur  
 Codefenster  
 Im oben angezeigten Codefenster können Sie einen Ausdruck eingeben. Wenn Sie das Dialogfeld **Ausdruck** öffnen, enthält das Codefenster den Ausdruck. Sie können den Ausdruck ersetzen oder bearbeiten. Sie können Funktionsaufrufe, Operatoren, Konstanten, Felder, Parameter, Elemente aus den globalen Auflistungen sowie Verweise auf benutzerdefinierten Code hinzufügen. Das Codefenster zeigt Ihre Änderungen sofort an.  
  
 Ein geschwungener roter Unterstrich signalisiert einen Syntaxfehler. Zeigen Sie auf den unterstrichenen Text, um die Fehlermeldung einzublenden.  
  
 Wenn Sie Begriffe aus globalen Auflistungen, gefolgt von einem Interpunktionstrennzeichen, eingeben, wird eine Dropdownliste mit verfügbaren Mitgliedern oder Eigenschaften angezeigt. Geben Sie über die Dropdownliste die ersten Zeichen ein, gefolgt von einem Tabulator, um die Auswahl automatisch auszufüllen.  
  
 Wenn Sie einen Funktionsnamen, gefolgt von einer linken Klammer, eingeben, wird eine QuickInfo mit Informationen zu den Parametern und Rückgabewerten der Funktion angezeigt.  
  
 **Kategorie**  
 Zeigt Kategorien von Ausdrücken an. Durch Auswahl einer Kategorie wird ein Kontext für die Erstellung eines Ausdrucks bereitgestellt und die Liste der gültigen Werte im Bereich Element geändert. Z. B. für einen Ausdruck für einen Textfeldwert erweitern Sie allgemeine Funktionen, und wählen Sie Aggregatfunktionen anzuzeigende `Avg`, `Count`, und andere Funktionen in der **Element** Bereich.  
  
 **Element**  
 Zeigt die Liste der gültigen Felder für die ausgewählte Kategorie an. Doppelklicken Sie auf ein Element, um den Ausdruckstext für dieses Element an der Einfügemarke im Codefenster hinzuzufügen.  
  
 **Werte**  
 Abhängig von der ausgewählten Kategorie und dem Element enthält der dritte Bereich eine Beschreibung, einen Beispielausdruck oder eine Liste gültiger Werte. Ziehen Sie am Rand des Dialogfelds, um den Beispielbereich zu erweitern.  
  
## <a name="see-also"></a>Siehe auch  
 [Ausdrücke &#40;Berichts-Generator und SSRS&#41;](report-design/expressions-report-builder-and-ssrs.md)   
 [Formatieren von Berichtselementen (Berichts-Generator und SSRS)](report-design/formatting-report-items-report-builder-and-ssrs.md)   
 [Formatieren von Zahlen und Datumsangaben &#40;Berichts-Generator und SSRS&#41;](report-design/formatting-numbers-and-dates-report-builder-and-ssrs.md)   
 [Parameters Collection References (Report Builder and SSRS) (Verweise auf Parameterauflistungen (Berichts-Generator und SSRS))](report-design/built-in-collections-parameters-collection-references-report-builder.md)   
 [Beispiele für Gruppierungsausdrücke (Berichts-Generator und SSRS)](report-design/group-expression-examples-report-builder-and-ssrs.md)   
 [Beispiele für Filtergleichungen &#40;Berichts-Generator und SSRS&#41;](report-design/filter-equation-examples-report-builder-and-ssrs.md)   
 [Datasetfeldauflistungen &#40;Berichts-Generator und SSRS&#41;](report-design/built-in-collections-dataset-fields-collection-references-report-builder.md)   
 [Referenz zu Aggregatfunktionen &#40;Berichts-Generator und SSRS&#41;](report-design/report-builder-functions-aggregate-functions-reference.md)   
 [Datentypen in Ausdrücken (Berichts-Generator und SSRS)](report-design/data-types-in-expressions-report-builder-and-ssrs.md)   
 [Wählen Sie das Dialogfeld Farbe &#40;Berichts-Generator und SSRS&#41;](../../2014/reporting-services/select-color-dialog-box-report-builder-and-ssrs.md)  
  
  
