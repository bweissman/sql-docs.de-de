---
title: Erstellen, ändern und Löschen von Sichten | Microsoft-Dokumentation
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology:
- database-engine
- docset-sql-devref
ms.topic: reference
helpviewer_keywords:
- views [SMO]
ms.assetid: 7d445c0e-77ef-4734-993b-e022de31df23
author: stevestein
ms.author: sstein
manager: craigg
ms.openlocfilehash: 7898003a6d3a6057b9982e1b130ca6cf4c559aaa
ms.sourcegitcommit: 3da2edf82763852cff6772a1a282ace3034b4936
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 10/02/2018
ms.locfileid: "48072100"
---
# <a name="creating-altering-and-removing-views"></a>Erstellen, Ändern und Löschen von Sichten
  In [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] Management Objects (SMO) werden [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)]-Sichten durch das <xref:Microsoft.SqlServer.Management.Smo.View>-Objekt dargestellt.  
  
 Die <xref:Microsoft.SqlServer.Management.Smo.View.TextBody%2A>-Eigenschaft des <xref:Microsoft.SqlServer.Management.Smo.View>-Objekts definiert die Sicht. Dies entspricht dem von der [!INCLUDE[tsql](../../../includes/tsql-md.md)] SELECT-Anweisung zum Erstellen einer Ansicht.  
  
## <a name="example"></a>Beispiel  
 Zum Verwenden eines angegebenen Codebeispiels müssen Sie die Programmierumgebung, Programmiervorlage und die zu verwendende Programmiersprache auswählen, um Ihre Anwendung zu erstellen. Weitere Informationen finden Sie unter [erstellen Sie eine Visual Basic-SMO-Projekts in Visual Studio .NET](../../../database-engine/dev-guide/create-a-visual-basic-smo-project-in-visual-studio-net.md) oder [Erstellen eines Visual C&#35; SMO-Projekts in Visual Studio .NET](../how-to-create-a-visual-csharp-smo-project-in-visual-studio-net.md).  
  
## <a name="creating-altering-and-removing-a-view-in-visual-basic"></a>Erstellen, Ändern und Löschen einer Sicht in Visual Basic  
 In diesem Codebeispiel wird gezeigt, wie eine Sicht von zwei Tabellen mit einem inneren Join erstellt wird. Die Sicht wird erstellt, mit dem Textmodus, sodass die <xref:Microsoft.SqlServer.Management.Smo.View.TextHeader%2A> Eigenschaft muss festgelegt werden.  
  
<!-- TODO: review snippet reference  [!CODE [SMO How to#SMO_VBViews1](SMO How to#SMO_VBViews1)]  -->  
  
## <a name="creating-altering-and-removing-a-view-in-visual-c"></a>Erstellen, Ändern und Löschen einer Sicht in Visual C#  
 In diesem Codebeispiel wird gezeigt, wie eine Sicht von zwei Tabellen mit einem inneren Join erstellt wird. Die Sicht wird erstellt, mit dem Textmodus, sodass die <xref:Microsoft.SqlServer.Management.Smo.View.TextHeader%2A> Eigenschaft muss festgelegt werden.  
  
```  
{  
        //Connect to the local, default instance of SQL Server.   
        Server srv;   
        srv = new Server();   
        //Reference the AdventureWorks2012 database.   
        Database db;   
        db = srv.Databases["AdventureWorks2012"];   
        //Define a View object variable by supplying the parent database, view name and schema in the constructor.   
        View myview;   
        myview = new View(db, "Test_View", "Sales");   
        //Set the TextHeader and TextBody property to define the view.   
        myview.TextHeader = "CREATE VIEW [Sales].[Test_View] AS";   
        myview.TextBody = "SELECT h.SalesOrderID, d.OrderQty FROM Sales.SalesOrderHeader AS h INNER JOIN Sales.SalesOrderDetail AS d ON h.SalesOrderID = d.SalesOrderID";   
        //Create the view on the instance of SQL Server.   
        myview.Create();   
        //Remove the view.   
        myview.Drop();   
        }  
```  
  
## <a name="creating-altering-and-removing-a-view-in-powershell"></a>Erstellen, Ändern und Löschen einer Sicht in PowerShell  
 In diesem Codebeispiel wird gezeigt, wie eine Sicht von zwei Tabellen mit einem inneren Join erstellt wird. Die Sicht wird erstellt, mit dem Textmodus, sodass die <xref:Microsoft.SqlServer.Management.Smo.View.TextHeader%2A> Eigenschaft muss festgelegt werden.  
  
```  
# Set the path context to the local, default instance of SQL Server and get a reference to AdventureWorks2012  
CD \sql\localhost\default\databases  
$db = get-item Adventureworks2012  
  
# Define a View object variable by supplying the parent database, view name and schema in the constructor.   
$myview  = New-Object -TypeName Microsoft.SqlServer.Management.SMO.View `  
-argumentlist $db, "Test_View", "Sales"  
  
# Set the TextHeader and TextBody property to define the view.   
$myview.TextHeader = "CREATE VIEW [Sales].[Test_View] AS"  
$myview.TextBody ="SELECT h.SalesOrderID, d.OrderQty FROM Sales.SalesOrderHeader AS h INNER JOIN Sales.SalesOrderDetail AS d ON h.SalesOrderID = d.SalesOrderID"  
  
# Create the view on the instance of SQL Server.   
$myview.Create()  
  
# Remove the view.   
$myview.Drop();  
```  
  
## <a name="see-also"></a>Siehe auch  
 <xref:Microsoft.SqlServer.Management.Smo.View>  
  
  
