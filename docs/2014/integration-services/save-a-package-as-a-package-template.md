---
title: Speichern eines Pakets als Paketvorlage | Microsoft-Dokumentation
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology:
- integration-services
ms.topic: conceptual
helpviewer_keywords:
- reusing packages
- templates [Integration Services]
ms.assetid: efe66cec-3933-4f6e-8d35-fe3d300de66c
author: douglaslms
ms.author: douglasl
manager: craigg
ms.openlocfilehash: fd04a8b1b0882fe6db6385052009d72551d1d0e3
ms.sourcegitcommit: 3da2edf82763852cff6772a1a282ace3034b4936
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 10/02/2018
ms.locfileid: "48187840"
---
# <a name="save-a-package-as-a-package-template"></a>Speichern eines Pakets als Paketvorlage
  In diesem Thema wird beschrieben, wie Sie beim Erstellen neuer Integration Services-Pakete in [!INCLUDE[ssBIDevStudioFull](../includes/ssbidevstudiofull-md.md)]benutzerdefinierte Pakete als Vorlagen festlegen und verwenden. [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)] verwendet standardmäßig eine Paketvorlage, die ein leeres Paket erstellt, wenn Sie einem [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)] -Projekt ein neues Paket hinzufügen. Sie können diese Standardvorlage nicht ersetzen. Es können jedoch neue Vorlagen hinzugefügt werden.  
  
 Sie haben die Möglichkeit, mehrere Pakete als Vorlagen festzulegen. Sie müssen zunächst benutzerdefinierte Pakete erstellen, bevor Sie diese als Vorlagen implementieren können.  
  
 Wenn Sie benutzerdefinierte Pakete als Vorlagen zum Erstellen von Paketen verwenden, haben die neuen Pakete denselben Namen und GUID wie die Vorlage. Sie sollten den Wert der `Name`-Eigenschaft aktualisieren und einen neuen GUID für die `ID`-Eigenschaft generieren, um die Pakete voneinander zu unterscheiden. Weitere Informationen finden Sie unter [Erstellen von Paketen in SQL Server Data Tools](create-packages-in-sql-server-data-tools.md) und [Festlegen von Paketeigenschaften](set-package-properties.md).  
  
### <a name="to-designate-a-custom-package-as-a-package-template"></a>So legen Sie ein benutzerdefiniertes Paket als Paketvorlage fest  
  
1.  Suchen Sie im Dateisystem nach dem Paket, welches Sie als Vorlage verwenden möchten.  
  
2.  Kopieren Sie das Paket in den Ordner DataTransformationItems. Dieser Ordner befindet sich standardmäßig unter C:\Programme\Microsoft Visual Studio 9.0\Common7\IDE\PrivateAssemblies\ProjectItems\DataTransformationProject.  
  
3.  Wiederholen Sie die Schritte 1 und 2 für jedes als Vorlage zu verwendende Paket.  
  
### <a name="to-use-a-custom-package-as-a-package-template"></a>So verwenden Sie ein benutzerdefiniertes Paket als Paketvorlage  
  
1.  Öffnen Sie in [!INCLUDE[ssBIDevStudioFull](../includes/ssbidevstudiofull-md.md)]das [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)] -Projekt, in dem Sie ein Paket erstellen möchten.  
  
2.  Klicken Sie im Projektmappen-Explorer mit der rechten Maustaste auf das Projekt, zeigen Sie auf **Hinzufügen**, und klicken Sie dann auf **Neues Element**.  
  
3.  Klicken Sie im Dialogfeld **Neues Element hinzufügen -\<Projektname>** auf das als Vorlage zu verwendende Paket.  
  
     Die Vorlagenliste enthält die Standardpaketvorlage mit der Bezeichnung Neues SSIS-Paket. Das Paketsymbol identifiziert die als Paketvorlage verwendbaren Vorlagen.  
  
4.  Klicken Sie auf **Hinzufügen**.  
  
## <a name="see-also"></a>Siehe auch  
 [Erstellen von Paketen in SQL Server Data Tools](create-packages-in-sql-server-data-tools.md)   
 [Integration Services &#40;SSIS&#41; Packages](../../2014/integration-services/integration-services-ssis-packages.md) (Integration Services-Pakete [SSIS])  
  
  
