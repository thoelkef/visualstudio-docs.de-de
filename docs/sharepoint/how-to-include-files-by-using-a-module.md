---
title: 'Vorgehensweise: Einschließen von Dateien mithilfe eines Moduls | Microsoft Docs'
ms.custom: ''
ms.date: 02/02/2017
ms.technology:
- office-development
ms.topic: conceptual
dev_langs:
- VB
- CSharp
- VB
- CSharp
helpviewer_keywords:
- SharePoint development in Visual Studio, modules
- modules [SharePoint development in Visual Studio]
author: TerryGLee
ms.author: tglee
manager: douge
ms.workload:
- office
ms.openlocfilehash: 6af9ef6114a3ac187c50d17f16c39c89b08370dd
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/16/2018
---
# <a name="how-to-include-files-by-using-a-module"></a>Gewusst wie: Einschließen von Dateien mithilfe eines Moduls
  *Module* (nicht zu verwechseln mit [!INCLUDE[vbprvb](../sharepoint/includes/vbprvb-md.md)] Module) sind Container, mit denen Sie z. B. Gestaltungsvorlagen ASPX-Dateien, Textdateien oder Bilder in SharePoint bereitstellen können.  
  
 Sie können zum Bereitstellen einer Datei in einer Dokumentbibliothek oder als eine normale Datei (z. B. "default.aspx") außerhalb einer Dokumentbibliothek auswählen. Geben Sie zum Hinzufügen einer Datei in eine Dokumentbibliothek `Type="GhostableInLibrary"` als ein Attribut in der **Datei** Element. Diese Einstellung wird angewiesen, SharePoint, erstellen Sie ein Listenelement aus, um mit Ihrer Datei zu wechseln, wenn sie in der Bibliothek hinzugefügt wird. Um eine Datei außerhalb einer Dokumentbibliothek bereitstellen möchten, geben Sie entweder `Type="Ghostable"` , oder lassen Sie nur die **Typ** Attribut.  
  
## <a name="adding-a-module-to-a-sharepoint-solution"></a>Hinzufügen eines Moduls zu einer SharePoint-Lösung  
  
#### <a name="to-add-a-module"></a>So fügen Sie ein Modul hinzu  
  
1.  In [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)]öffnen oder erstellen Sie ein SharePoint-Projekt.  
  
     Weitere Informationen finden Sie unter [SharePoint-Projekte und Projektelementvorlagen](../sharepoint/sharepoint-project-and-project-item-templates.md).  
  
2.  In **Projektmappen-Explorer**, wählen Sie den Projektknoten, und wählen Sie dann auf der Menüleiste **Projekt**, **neues Element hinzufügen**.  
  
     Das Dialogfeld **Neues Element hinzufügen** wird angezeigt.  
  
3.  Wählen Sie in der Liste der SharePoint-Vorlagen, die **Modul** Vorlage, und wählen Sie dann die **hinzufügen** Schaltfläche.  
  
     Dieser Schritt erstellt einen Knoten in das Projekt mit dem Namen Module1.  
  
4.  Löschen Sie unter Module1 die Datei "Sample.txt".  
  
     "Sample.txt" ist in allen neuen Modulen z. B. Zwecke enthalten, und es ist nicht erforderlich. (Beachten Sie, dass einen Eintrag Löschen der Datei auch aus dem Modul "Elements.xml"-Datei entfernt werden.).  
  
5.  Wenn Sie Ihre Dateien auf einer bestimmten Ordnerstruktur in SharePoint bereitstellen möchten, erstellen Sie diesen Ordner unter Module1 in [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] durch Auswählen des Module1-Knotens, klicken Sie dann auf der Menüleiste **Projekt**, **neu Ordner**.  
  
6.  Wählen Sie den Ordner, in dem die Datei hinzufügen und anschließend auf der Menüleiste die Optionen werden sollen **Projekt**, **vorhandenes Element hinzufügen**.  
  
7.  Wählen Sie eine oder mehrere Dateien, die Sie verwenden möchten, für SharePoint bereitzustellen, und wählen Sie dann die **hinzufügen** Schaltfläche.  
  
     Wenn Sie eine Datei zum Projekt hinzufügen, wird ein entsprechender Eintrag automatisch an das Modul "Elements.xml"-Datei hinzugefügt. Wenn das Projekt bereitgestellt wird, werden die Dateien auf SharePoint-Server, relativ zum Stammverzeichnis des Projekts, das durch angegeben wird kopiert die **Datei** des Elements **Url** Attribut, z. B. `Url="Module1/New Folder/SomeFile.doc`. Wenn Sie den Bereitstellungsspeicherort für eine Datei ändern möchten, entweder verschieben Sie sie in einen anderen Ordner im **Projektmappen-Explorer** oder ändern dessen **Url** Einstellung.  
  
8.  Für alle Dateien, die in einer Dokumentbibliothek angezeigt werden sollen, fügen die `Type="GhostableInLibrary"` -Attributs auf ihren Eintrag in der Datei "Elements.xml". Ein auf ein Objekt angewendeter  
  
    ```  
    <File Path="Module1\Some Folder\SomePage.aspx" Url="Module1/Some Folder/SomePage.aspx" Type="GhostableInLibrary" />  
    ```  
  
9. Bereitstellen des Projekts.  
  
     Die Dateien an den angegebenen Speicherorten in SharePoint kopieren.  
  
## <a name="see-also"></a>Siehe auch  
 [Verpacken und Bereitstellen von SharePoint-Lösungen](../sharepoint/packaging-and-deploying-sharepoint-solutions.md)   
 [Entwickeln von SharePoint-Projektmappen](../sharepoint/developing-sharepoint-solutions.md)  
  
  