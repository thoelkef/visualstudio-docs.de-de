---
title: Definieren von benutzerdefinierten SharePoint-Projektelementtypen | Microsoft-Dokumentation
ms.custom: ''
ms.date: 02/02/2017
ms.technology:
- office-development
ms.topic: conceptual
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- SharePoint project items, defining your own types
- project items [SharePoint development in Visual Studio], defining your own types
- SharePoint development in Visual Studio, defining new project item types
author: TerryGLee
ms.author: tglee
manager: douge
ms.workload:
- office
ms.openlocfilehash: f32f429186aa0c4a657503ca9744bf570d624f25
ms.sourcegitcommit: 240c8b34e80952d00e90c52dcb1a077b9aff47f6
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 10/23/2018
ms.locfileid: "49869508"
---
# <a name="define-custom-sharepoint-project-item-types"></a>Definieren von benutzerdefinierten SharePoint-Projektelementtypen
  Definieren Sie einen neuen SharePoint-Projektelementtyp, wenn Sie eine neue Art von SharePoint-Projektelement erstellen möchten. Visual Studio umfasst z. B. keine SharePoint-Projektelemente zum Hinzufügen von Feldern oder benutzerdefinierte Aktionen auf einer SharePoint-Website. Sie können eigene Typen von SharePoint-Projektelemente zum Erstellen von Feldern, benutzerdefinierte Aktionen oder andere Typen von SharePoint-Komponenten definieren.  
  
## <a name="tasks-for-defining-sharepoint-project-item-types"></a>Aufgaben zum Definieren von SharePoint-Projektelementtypen
 Um einen benutzerdefinierten Projektelementtyp definieren möchten, erstellen Sie eine Visual Studio-Erweiterungsassembly, implementiert die <xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectItemTypeProvider> Schnittstelle. Weitere Informationen finden Sie unter [wie: definieren ein SharePoint-Projektelementtyps](../sharepoint/how-to-define-a-sharepoint-project-item-type.md).  
  
 Wenn Sie einen benutzerdefinierten Projektelementtyp definieren, können Sie auch die folgende Funktionen auf das Projektelement hinzufügen:  
  
- Hinzufügen eines Kontextmenüelements auf das Projektelement. Das Menüelement angezeigt wird, wenn Sie das Kontextmenü für das Projektelement in öffnen **Projektmappen-Explorer** durch Rechtsklick auf das Projektelement, oder indem Sie ihn auswählen und dann auf die **UMSCHALT** +  **F10** Schlüssel. Weitere Informationen finden Sie unter [Vorgehensweise: Hinzufügen ein Kontextmenüelements zu einer benutzerdefinierten SharePoint-Projektelementtyp](../sharepoint/how-to-add-a-shortcut-menu-item-to-a-custom-sharepoint-project-item-type.md).  
  
- Fügen Sie eine benutzerdefinierte Eigenschaft, auf das Projektelement. Die Eigenschaft wird in der **Eigenschaften** Fenster bei der Auswahl des Projektelement im **Projektmappen-Explorer**. Weitere Informationen finden Sie unter [Vorgehensweise: Hinzufügen einer Eigenschaft zu einer benutzerdefinierten SharePoint-Projektelementtyp](../sharepoint/how-to-add-a-property-to-a-custom-sharepoint-project-item-type.md).  
  
  Damit können andere Entwickler, um Ihr Projektelement in Visual Studio verwenden, erstellen Sie eine SPDATA-Datei aus, und erstellen Sie eine Elementvorlage oder die Projektvorlage, die mit dem Projektelement zugeordnet ist. Weitere Informationen finden Sie unter [Erstellen von Vorlagen und Projektvorlagen für SharePoint-Projektelemente](../sharepoint/creating-item-templates-and-project-templates-for-sharepoint-project-items.md).  
  
## <a name="understand-the-relationship-between-project-item-types-and-project-item-instances"></a>Verstehen Sie die Beziehung zwischen Projektelementtypen und Instanzen von Project-Element
 Wenn Sie einen SharePoint-Projektelementtyp definieren, lädt Visual Studio die Erweiterung aus, wenn ein SharePoint-Projekt ein Projektelement des zugeordneten Typs hinzugefügt wird. Z. B., wenn Sie einen neuen definieren **benutzerdefinierte Aktion** Projektelementtyp, Visual Studio lädt die Erweiterung aus, wenn ein Benutzer fügt eine **benutzerdefinierte Aktion** Projektelements, das ein Projekt. Visual Studio verwendet die gleiche Instanz der Erweiterung für alle Instanzen der zugeordneten Projektelementtyps. Im vorherigen Beispiel, wenn der Benutzer eine zweite Befehl fügt der **benutzerdefinierte Aktion** Projektelement für das Projekt, die gleiche Instanz der Erweiterung wird verwendet, um das zweite Projektelement anpassen.  
  
 Für den Zugriff auf eine bestimmte Instanz des Projektelementtyps, behandeln Sie eines der der <xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectItemEvents> Ereignisse der *ProjectItemTypeDefinition* Parameter in der Implementierung von der <xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectItemTypeProvider.InitializeType%2A> Methode. Um zu bestimmen, wann ein Projektelement des benutzerdefinierten Typs zu einem Projekt hinzugefügt wird, z. B. Behandeln der <xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectItemEvents.ProjectItemAdded> Ereignis. Weitere Informationen finden Sie unter [wie: definieren ein SharePoint-Projektelementtyps](../sharepoint/how-to-define-a-sharepoint-project-item-type.md).  
  
## <a name="see-also"></a>Siehe auch
 [Gewusst wie: definieren ein SharePoint-Projektelementtyps](../sharepoint/how-to-define-a-sharepoint-project-item-type.md)   
 [Gewusst wie: Hinzufügen einer Eigenschaft zu einer benutzerdefinierten SharePoint-Projektelementtyp](../sharepoint/how-to-add-a-property-to-a-custom-sharepoint-project-item-type.md)   
 [Gewusst wie: Hinzufügen ein Kontextmenüelements zu einer benutzerdefinierten SharePoint-Projektelementtyp](../sharepoint/how-to-add-a-shortcut-menu-item-to-a-custom-sharepoint-project-item-type.md)   
 [Erstellen von Elementvorlagen und Projektvorlagen für SharePoint-Projektelemente](../sharepoint/creating-item-templates-and-project-templates-for-sharepoint-project-items.md)   
 [Exemplarische Vorgehensweise: Erstellen Sie benutzerdefinierte Aktionsprojektelement mit einer Elementvorlage, Teil 1](../sharepoint/walkthrough-creating-a-custom-action-project-item-with-an-item-template-part-1.md)   
 [Exemplarische Vorgehensweise: Erstellen der Website-Spaltenelement-Projekt mit einer Projektvorlage, Teil 1](../sharepoint/walkthrough-creating-a-site-column-project-item-with-a-project-template-part-1.md)   
 [Exemplarische Vorgehensweise: Erstellen eines Projektelements benutzerdefinierte Aktion mit einer Elementvorlage, Teil 2](../sharepoint/walkthrough-creating-a-custom-action-project-item-with-an-item-template-part-2.md)   
 [Exemplarische Vorgehensweise: Erstellen eines Projektelements Spalte mit einer Projektvorlage, Teil 2](../sharepoint/walkthrough-creating-a-site-column-project-item-with-a-project-template-part-2.md)   
 [Bereitstellen von Erweiterungen für SharePoint-Tools in Visual Studio](../sharepoint/deploying-extensions-for-the-sharepoint-tools-in-visual-studio.md)  
  
