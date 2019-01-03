---
title: 'Vorgehensweise: Schließen Sie Dateien mithilfe eines Moduls | Microsoft-Dokumentation'
ms.date: 02/02/2017
ms.topic: conceptual
dev_langs:
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
ms.openlocfilehash: d0cfe558c21a941ed5cc16eccef2e014acfbcdb7
ms.sourcegitcommit: 37fb7075b0a65d2add3b137a5230767aa3266c74
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 01/02/2019
ms.locfileid: "53923492"
---
# <a name="how-to-include-files-by-using-a-module"></a>Vorgehensweise: Schließen Sie Dateien mithilfe eines Moduls
  *Module* (nicht zu verwechseln mit [!INCLUDE[vbprvb](../sharepoint/includes/vbprvb-md.md)] Module) sind Container, die Ihnen ermöglichen, z. B. Gestaltungsvorlagen ASPX-Dateien, Textdateien oder Bilder in SharePoint bereitstellen.  
  
 Sie können auch eine Datei in einer Dokumentbibliothek oder als normale Datei (z. B. "default.aspx") bereitstellen außerhalb einer Dokumentbibliothek. Geben Sie zum Hinzufügen einer Datei in eine Dokumentbibliothek `Type="GhostableInLibrary"` als Attribut in der **Datei** Element. Diese Einstellung weist SharePoint erstellen Sie ein Listenelement, um mit der Datei zu wechseln, wenn es in der Bibliothek hinzugefügt wird. Geben Sie zum Bereitstellen einer Datei außerhalb einer Dokumentbibliothek `Type="Ghostable"` oder lassen Sie nur die **Typ** Attribut.  
  
## <a name="add-a-module-to-a-sharepoint-solution"></a>Fügen Sie ein Modul auf einer SharePoint-Lösung  
  
#### <a name="to-add-a-module"></a>Ein Modul hinzufügen  
  
1.  In [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)]öffnen oder erstellen Sie ein SharePoint-Projekt.  
  
     Weitere Informationen finden Sie unter [SharePoint-Projekt und Projekt Elementvorlagen](../sharepoint/sharepoint-project-and-project-item-templates.md).  
  
2.  In **Projektmappen-Explorer**, wählen Sie den Projektknoten und anschließend auf der Menüleiste die Optionen **Projekt** > **neues Element hinzufügen**.  
  
     Das Dialogfeld **Neues Element hinzufügen** wird angezeigt.  
  
3.  Wählen Sie in der Liste der SharePoint-Vorlagen, die **Modul** Vorlage, und wählen Sie dann die **hinzufügen** Schaltfläche.  
  
     Dieser Schritt erstellt einen Knoten in das Projekt mit dem Namen "Module1".  
  
4.  Löschen Sie unter "Module1", die *"Sample.txt"* Datei.  
  
     "Sample.txt" befindet sich auf alle neuen Module z. B. Zweck und ist nicht erforderlich. (Beachten Sie, dass einen Eintrag löschen Sie die Datei auch vom des Moduls entfernt werden. *"Elements.xml"* Datei.)  
  
5.  Wenn Sie Ihre Dateien auf einer bestimmten Ordnerstruktur in SharePoint bereitstellen möchten, erstellen Sie diese Ordner unter "Module1" im [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] durch Auswählen der Knoten Module1, und klicken Sie dann auf der Menüleiste die Optionen **Projekt**, **neu Ordner**.  
  
6.  Wählen Sie den Ordner, in dem Sie fügen der Datei, und anschließend auf der Menüleiste die Optionen möchten **Projekt**, **vorhandenes Element hinzufügen**.  
  
7.  Wählen Sie eine oder mehrere Dateien, die Sie verwenden möchten, für SharePoint bereitzustellen, und wählen Sie dann die **hinzufügen** Schaltfläche.  
  
     Wenn Sie eine Datei zum Projekt hinzufügen, wird ein entsprechender Eintrag vorgenommen des Moduls "Elements.xml"-Datei automatisch hinzugefügt. Wenn das Projekt bereitgestellt wird, werden die Dateien auf SharePoint-Server, relativ zum Stammverzeichnis des Projekts, die von angegeben wird kopiert die **Datei** des Elements **Url** Attribut, z. B. `Url="Module1/New Folder/SomeFile.doc`. Wenn Sie den Speicherort für die Bereitstellung für eine Datei ändern möchten, entweder verschieben Sie sie in einen anderen Ordner in **Projektmappen-Explorer** oder ändern Sie seine **Url** festlegen.  
  
8.  Fügen Sie für alle Dateien, die in einer Dokumentbibliothek angezeigt werden sollen, die `Type="GhostableInLibrary"` -Attribut auf den entsprechenden Eintrag unter *"Elements.xml"*. Ein auf ein Objekt angewendeter  
  
    ```xml  
    <File Path="Module1\Some Folder\SomePage.aspx" Url="Module1/Some Folder/SomePage.aspx" Type="GhostableInLibrary" />  
    ```  
  
9. Bereitstellen des Projekts.  
  
     Die Dateien kopieren, für die angegebenen Orte in SharePoint.  
  
## <a name="see-also"></a>Siehe auch
 [Packen und Bereitstellen von SharePoint-Lösungen](../sharepoint/packaging-and-deploying-sharepoint-solutions.md)   
 [Entwickeln von SharePoint-Projektmappen](../sharepoint/developing-sharepoint-solutions.md)  
