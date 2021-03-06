---
title: Explizite Zuordnung von XSD-Elementen und-Attributen zu Tabellen und Spalten (SQLXML 4.0) | Microsoft-Dokumentation
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology:
- database-engine
- docset-sql-devref
ms.topic: reference
helpviewer_keywords:
- explicit schema mapping [SQLXML]
- XPath queries [SQLXML], annotated XSD schemas in queries
- sql:field
- row mapping [SQLXML]
- attribute mapping [SQLXML], explicit mapping
- field annotation
- XSD schemas [SQLXML], mapping attributes and elements
- names [SQLXML]
- relation annotation
- table/view mapping [SQLXML], explicit mapping
- sql:relation
- mapping schema [SQLXML], explicit mapping
- annotated XSD schemas, mapping attributes and elements
- column mapping [SQLXML]
- element mapping [SQLXML], explicit mapping
- table mapping [SQLXML], explicit mapping
- element/attribute mapping [SQLXML]
ms.assetid: 7a5ebeb6-7322-4141-a307-ebcf95976146
author: douglaslMS
ms.author: douglasl
manager: craigg
ms.openlocfilehash: 26fa0d203edf479e93ae95323bc469b506025cf0
ms.sourcegitcommit: 3da2edf82763852cff6772a1a282ace3034b4936
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 10/02/2018
ms.locfileid: "48222280"
---
# <a name="explicit-mapping-of-xsd-elements-and-attributes-to-tables-and-columns-sqlxml-40"></a>Explizite Zuordnung von XSD-Elementen und -Attributen zu Tabellen und Spalten (SQLXML 4.0)
  Wenn ein XSD-Schema zur Bereitstellung einer XML-Sicht der relationalen Datenbank verwendet wird, müssen die Elemente und Attribute des Schemas den Tabellen und Spalten der Datenbank zugeordnet werden. Die Zeilen in der Datenbanktabelle/-sicht werden den Elementen im XML-Dokument zugeordnet. Die Spaltenwerte in der Datenbank werden Attributen oder Elementen zugeordnet.  
  
 Wenn Xpath-Abfragen für das mit Anmerkungen versehene XSD-Schema angegeben werden, werden die Daten für die Elemente und Attribute im Schema aus den Tabellen und Spalten abgerufen, denen sie zugeordnet sind. Um einen einzelnen Wert aus der Datenbank abrufen zu können, muss die im XSD-Schema angegebene Zuordnung sowohl über eine Beziehungs- als auch eine Feldangabe verfügen. Wenn der Name eines Elements/Attributs nicht mit dem Namen der zugeordneten Tabelle/Sicht oder Spalte identisch ist, werden die `sql:relation`-Anmerkung und die `sql:field`-Anmerkung verwendet, um die Zuordnung zwischen einem Element oder Attribut in einem XML-Dokument und der Tabelle (Sicht) oder Spalten in einer Datenbank anzugeben.  
  
## <a name="sql-relation"></a>sql-Beziehung  
 Die `sql:relation`-Anmerkung wird hinzugefügt, um einen XML-Knoten im XSD-Schema einer Datenbanktabelle zuzuordnen. Der Name einer Tabelle (Sicht) wird als Wert der `sql:relation`-Anmerkung angegeben.  
  
 Wenn `sql:relation` für ein Element angegeben wird, gilt der Bereich dieser Anmerkung für alle Attribute und untergeordneten Elemente, die in der komplexen Typdefinition des Elements beschrieben sind. Dadurch wird das Schreiben von Anmerkungen vereinfacht.  
  
 Die `sql:relation` Anmerkung ist auch nützlich, wenn der Bezeichner, die in gültig sind [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] sind in XML nicht gültig. Zum Beispiel ist "Order Details" ein gültiger Tabellenname in [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)], jedoch nicht in XML. In solchen Fällen kann die `sql:relation`-Anmerkung verwendet werden, um die Zuordnung anzugeben. Beispiel:  
  
```  
<xsd:element name="OD" sql:relation="[Order Details]">  
```  
  
## <a name="sql-field"></a>sql-Feld  
 Die `sql-field`-Anmerkung ordnet ein Element oder Attribut einer Datenbankspalte zu. Die `sql:field`-Anmerkung wird hinzugefügt, um einen XML-Knoten im Schema einer Datenbankspalte zuzuordnen. Sie können `sql:field` für ein Element ohne Inhalt angeben.  
  
## <a name="examples"></a>Beispiele  
 Es müssen bestimmte Anforderungen erfüllt sein, damit aus den folgenden Beispielen funktionierende Beispiele erstellt werden können. Weitere Informationen finden Sie unter [Anforderungen für die Ausführung von SQLXML-Beispielen](../sqlxml/requirements-for-running-sqlxml-examples.md).  
  
### <a name="a-specifying-the-sqlrelation-and-sqlfield-annotations"></a>A. Angeben der Anmerkungen sql:relation und sql:field  
 In diesem Beispiel ist das XSD-Schema besteht aus einem  **\<wenden Sie sich an >** -Element komplexen Typs mit  **\<FName >** und  **\<LName >** untergeordnete Elemente und die **ContactID** Attribut.  
  
 Die `sql:relation` -Anmerkung ordnet das  **\<wenden Sie sich an >** -Element der Person.Contact-Tabelle in der AdventureWorks-Datenbank. Die `sql:field` -Anmerkung ordnet das  **\<FName >** -Element der FirstName-Spalte und die  **\<LName >** -Element der LastName-Spalte.  
  
 Wird keine Anmerkung angegeben, für die **ContactID** Attribut. Dies führt zu einer Standardzuordnung des Attributs zur Spalte mit dem gleichen Namen.  
  
```  
<xsd:schema xmlns:xsd="http://www.w3.org/2001/XMLSchema"  
            xmlns:sql="urn:schemas-microsoft-com:mapping-schema">  
  <xsd:element name="Contact" sql:relation="Person.Contact" >  
   <xsd:complexType>  
     <xsd:sequence>  
        <xsd:element name="FName"  
                     sql:field="FirstName"   
                     type="xsd:string" />   
        <xsd:element name="LName"    
                     sql:field="LastName"    
                     type="xsd:string" />  
     </xsd:sequence>  
        <xsd:attribute name="ContactID"   
                       type="xsd:integer" />  
    </xsd:complexType>  
  </xsd:element>  
</xsd:schema>  
```  
  
##### <a name="to-test-a-sample-xpath-query-against-the-schema"></a>So testen Sie eine Beispiel-XPath-Abfrage anhand des Schemas  
  
1.  Kopieren Sie den oben stehenden Schemacode, und fügen Sie ihn in eine Textdatei ein. Speichern Sie die Datei unter dem Dateinamen MySchema-annotated.xml.  
  
2.  Kopieren Sie die unten stehende Vorlage, und fügen Sie sie in eine Textdatei ein. Speichern Sie die Datei unter dem Namen MySchema-annotatedT.xml im gleichen Verzeichnis, in dem Sie MySchema-annotated.xml gespeichert haben.  
  
    ```  
    <ROOT xmlns:sql="urn:schemas-microsoft-com:xml-sql">  
      <sql:xpath-query mapping-schema="MySchema-annotated.xml">  
        /Contact  
      </sql:xpath-query>  
    </ROOT>  
    ```  
  
     Der für das Zuordnungsschema (MySchema-annotated.xml) angegebene Verzeichnispfad bezieht sich auf das Verzeichnis, in dem die Vorlage gespeichert wird. Es kann auch ein absoluter Pfad angegeben werden. Beispiel:  
  
    ```  
    mapping-schema="C:\SqlXmlTest\MySchema-annotated.xml"  
    ```  
  
3.  Erstellen und verwenden Sie das SQLXML 4.0-Testskript (Sqlxml4test.vbs), um die Vorlage auszuführen.  
  
     Weitere Informationen finden Sie unter [Verwenden von ADO zum Ausführen von SQLXML-Abfragen](../sqlxml/using-ado-to-execute-sqlxml-4-0-queries.md).  
  
 Im Folgenden wird ein Teil des Resultsets aufgeführt:  
  
```  
<ROOT xmlns:sql="urn:schemas-microsoft-com:xml-sql">   
 <Contact ContactID="1">   
    <FName>Gustavo</FName>   
    <LName>Achong</LName>   
 </Contact>   
  .....  
</ROOT>  
```  
  
  
