---
title: Erstellen, ändern und Löschen von benutzerdefinierten Funktionen | Microsoft-Dokumentation
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology:
- database-engine
- docset-sql-devref
ms.topic: reference
helpviewer_keywords:
- user-defined functions [SMO]
ms.assetid: 0ebebd3b-0775-41c2-989d-aa4cf81af12a
author: stevestein
ms.author: sstein
manager: craigg
ms.openlocfilehash: ced5a796739ea508440fea9ddbb645443fdda786
ms.sourcegitcommit: 3da2edf82763852cff6772a1a282ace3034b4936
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 10/02/2018
ms.locfileid: "48054500"
---
# <a name="creating-altering-and-removing-user-defined-functions"></a>Erstellen, Ändern und Löschen von benutzerdefinierten Funktionen
  Die <xref:Microsoft.SqlServer.Management.Smo.UserDefinedFunction> Objekt bietet Funktionen, die Benutzer programmgesteuert benutzerdefinierte Funktionen in verwalten kann [!INCLUDE[msCoName](../../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)]. Benutzerdefinierte Funktionen unterstützen sowohl Eingabe- und Ausgabeparameter als auch direkte Verweise auf Tabellenspalten.  
  
 [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] erfordert, dass Assemblys in einer Datenbank, bevor diese registriert werden können verwendet werden, innerhalb von gespeicherten Prozeduren, benutzerdefinierte Funktionen, Trigger und benutzerdefinierte Datentypen. SMO unterstützt diese Funktion mit dem <xref:Microsoft.SqlServer.Management.Smo.SqlAssembly>-Objekt.  
  
 Die <xref:Microsoft.SqlServer.Management.Smo.UserDefinedFunction> -Objekt verweist auf die .NET-Assembly mit den <xref:Microsoft.SqlServer.Management.Smo.UserDefinedFunction.AssemblyName%2A>, <xref:Microsoft.SqlServer.Management.Smo.UserDefinedFunction.ClassName%2A>, und <xref:Microsoft.SqlServer.Management.Smo.UserDefinedFunction.MethodName%2A> Eigenschaften.  
  
 Bei der <xref:Microsoft.SqlServer.Management.Smo.UserDefinedFunction> Objekt auf eine .NET-Assembly verweist, müssen Sie die Assembly registrieren, durch das Erstellen einer <xref:Microsoft.SqlServer.Management.Smo.SqlAssembly> -Objekts und zum Hinzufügen der <xref:Microsoft.SqlServer.Management.Smo.SqlAssemblyCollection> -Objekt, das gehört die <xref:Microsoft.SqlServer.Management.Smo.Database> Objekt.  
  
## <a name="example"></a>Beispiel  
 Zum Verwenden eines angegebenen Codebeispiels müssen Sie die Programmierumgebung, Programmiervorlage und die zu verwendende Programmiersprache auswählen, um Ihre Anwendung zu erstellen. Weitere Informationen finden Sie unter [erstellen Sie eine Visual Basic-SMO-Projekts in Visual Studio .NET](../../../database-engine/dev-guide/create-a-visual-basic-smo-project-in-visual-studio-net.md) oder [Erstellen eines Visual C&#35; SMO-Projekts in Visual Studio .NET](../how-to-create-a-visual-csharp-smo-project-in-visual-studio-net.md).  
  
## <a name="creating-a-scalar-user-defined-function-in-visual-basic"></a>Erstellen einer benutzerdefinierten Skalarfunktion in Visual Basic  
 In diesem Codebeispiel wird veranschaulicht, wie zum Erstellen und entfernen eine skalare benutzerdefinierte Funktion, die eine Eingabe <xref:System.DateTime> -Objektparameter und einen ganzzahligen Rückgabetyp in [!INCLUDE[vbprvb](../../../includes/vbprvb-md.md)]. Die benutzerdefinierte Funktion wird erstellt, auf die [!INCLUDE[ssSampleDBnormal](../../../includes/sssampledbnormal-md.md)] Datenbank. Im Beispiel wird die benutzerdefinierte Funktion ISOweek erstellt, die ein Datumsargument annimmt und die Nummer der ISO-Woche berechnet. Damit diese Funktion ordnungsgemäß berechnet wird, muss die DATEFIRST-Option der Datenbank auf 1 festgelegt werden, bevor die Funktion aufgerufen wird.  
  
<!-- TODO: review snippet reference  [!CODE [SMO How to#SMO_VBUserDefFuncs1](SMO How to#SMO_VBUserDefFuncs1)]  -->  
  
## <a name="creating-a-scalar-user-defined-function-in-visual-c"></a>Erstellen einer benutzerdefinierten Skalarfunktion in Visual C#  
 In diesem Codebeispiel wird veranschaulicht, wie zum Erstellen und entfernen eine skalare benutzerdefinierte Funktion, die eine Eingabe <xref:System.DateTime> -Objektparameter und einen ganzzahligen Rückgabetyp in [!INCLUDE[csprcs](../../../includes/csprcs-md.md)]. Die benutzerdefinierte Funktion wird erstellt, auf die [!INCLUDE[ssSampleDBnormal](../../../includes/sssampledbnormal-md.md)] Datenbank. Im Beispiel wird die folgende benutzerdefinierte Funktion erstellt. `ISOweek`. installiert haben. Diese Funktion nimmt ein Datumsargument an und berechnet die Nummer der ISO-Woche. Damit diese Funktion richtige Werte berechnet, muss die Datenbankoption `DATEFIRST` auf `1` festgelegt werden, bevor die Funktion aufgerufen wird.  
  
```  
{  
            //Connect to the local, default instance of SQL Server.   
           Server srv = new Server();  
            //Reference the AdventureWorks2012 database.   
           Database db = srv.Databases["AdventureWorks2012"];  
  
            //Define a UserDefinedFunction object variable by supplying the parent database and the name arguments in the constructor.   
            UserDefinedFunction udf = new UserDefinedFunction(db, "IsOWeek");  
  
            //Set the TextMode property to false and then set the other properties.   
            udf.TextMode = false;  
            udf.DataType = DataType.Int;  
            udf.ExecutionContext = ExecutionContext.Caller;  
            udf.FunctionType = UserDefinedFunctionType.Scalar;  
            udf.ImplementationType = ImplementationType.TransactSql;  
  
            //Add a parameter.   
  
     UserDefinedFunctionParameter par = new UserDefinedFunctionParameter(udf, "@DATE", DataType.DateTime);  
            udf.Parameters.Add(par);  
  
            //Set the TextBody property to define the user-defined function.   
            udf.TextBody = "BEGIN DECLARE @ISOweek int SET @ISOweek= DATEPART(wk,@DATE)+1 -DATEPART(wk,CAST(DATEPART(yy,@DATE) as CHAR(4))+'0104') IF (@ISOweek=0) SET @ISOweek=dbo.ISOweek(CAST(DATEPART(yy,@DATE)-1 AS CHAR(4))+'12'+ CAST(24+DATEPART(DAY,@DATE) AS CHAR(2)))+1 IF ((DATEPART(mm,@DATE)=12) AND ((DATEPART(dd,@DATE)-DATEPART(dw,@DATE))>= 28)) SET @ISOweek=1 RETURN(@ISOweek) END;";  
  
            //Create the user-defined function on the instance of SQL Server.   
            udf.Create();  
  
            //Remove the user-defined function.   
            udf.Drop();  
        }  
```  
  
## <a name="creating-a-scalar-user-defined-function-in-powershell"></a>Erstellen einer benutzerdefinierten Skalarfunktion in PowerShell  
 In diesem Codebeispiel wird veranschaulicht, wie zum Erstellen und entfernen eine skalare benutzerdefinierte Funktion, die eine Eingabe <xref:System.DateTime> -Objektparameter und einen ganzzahligen Rückgabetyp in [!INCLUDE[csprcs](../../../includes/csprcs-md.md)]. Die benutzerdefinierte Funktion wird erstellt, auf die [!INCLUDE[ssSampleDBnormal](../../../includes/sssampledbnormal-md.md)] Datenbank. Im Beispiel wird die folgende benutzerdefinierte Funktion erstellt. `ISOweek`. installiert haben. Diese Funktion nimmt ein Datumsargument an und berechnet die Nummer der ISO-Woche. Damit diese Funktion richtige Werte berechnet, muss die Datenbankoption `DATEFIRST` auf `1` festgelegt werden, bevor die Funktion aufgerufen wird.  
  
```  
# Set the path context to the local, default instance of SQL Server and get a reference to AdventureWorks2012  
CD \sql\localhost\default\databases  
$db = get-item Adventureworks2012  
  
# Define a user defined function object variable by supplying the parent database and name arguments in the constructor.   
$udf  = New-Object -TypeName Microsoft.SqlServer.Management.SMO.UserDefinedFunction `  
-argumentlist $db, "IsOWeek"  
  
# Set the TextMode property to false and then set the other properties.   
$udf.TextMode = $false  
$udf.DataType = [Microsoft.SqlServer.Management.SMO.DataType]::Int   
$udf.ExecutionContext = [Microsoft.SqlServer.Management.SMO.ExecutionContext]::Caller  
$udf.FunctionType = [Microsoft.SqlServer.Management.SMO.UserDefinedFunctionType]::Scalar  
$udf.ImplementationType = [Microsoft.SqlServer.Management.SMO.ImplementationType]::TransactSql  
  
# Define a Parameter object variable by supplying the parent function, name and type arguments in the constructor.  
$type = [Microsoft.SqlServer.Management.SMO.DataType]::DateTime  
$par  = New-Object -TypeName Microsoft.SqlServer.Management.SMO.UserDefinedFunctionParameter `  
-argumentlist $udf, "@DATE",$type  
  
# Add the parameter to the function  
$udf.Parameters.Add($par)  
  
#Set the TextBody property to define the user-defined function.   
$udf.TextBody = "BEGIN DECLARE @ISOweek int SET @ISOweek= DATEPART(wk,@DATE)+1 -DATEPART(wk,CAST(DATEPART(yy,@DATE) as CHAR(4))+'0104') IF (@ISOweek=0) SET @ISOweek=dbo.ISOweek(CAST(DATEPART(yy,@DATE)-1 AS CHAR(4))+'12'+ CAST(24+DATEPART(DAY,@DATE) AS CHAR(2)))+1 IF ((DATEPART(mm,@DATE)=12) AND ((DATEPART(dd,@DATE)-DATEPART(dw,@DATE))>= 28)) SET @ISOweek=1 RETURN(@ISOweek) END;"  
  
# Create the user-defined function on the instance of SQL Server.   
$udf.Create()  
  
# Remove the user-defined function.   
$udf.Drop()  
```  
  
## <a name="see-also"></a>Siehe auch  
 <xref:Microsoft.SqlServer.Management.Smo.UserDefinedFunction>  
  
  
