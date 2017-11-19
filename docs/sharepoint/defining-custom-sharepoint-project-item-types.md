---
title: Definieren von benutzerdefinierten SharePoint-Projektelementtypen | Microsoft Docs
ms.custom: 
ms.date: 02/02/2017
ms.reviewer: 
ms.suite: 
ms.technology: office-development
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- SharePoint project items, defining your own types
- project items [SharePoint development in Visual Studio], defining your own types
- SharePoint development in Visual Studio, defining new project item types
ms.assetid: be300c24-fd1b-4fc7-a4e9-a5df1d81d3fc
caps.latest.revision: "22"
author: gewarren
ms.author: gewarren
manager: ghogen
ms.openlocfilehash: 980712e717df294a4d390eb66ed2f1740ba2c3f4
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 10/31/2017
---
# <a name="defining-custom-sharepoint-project-item-types"></a>Definieren von benutzerdefinierten SharePoint-Projektelementtypen
  Definieren Sie einen neue SharePoint-Projektelementtyp, wenn Sie eine neue Art von SharePoint-Projektelement erstellen möchten. Visual Studio umfasst z. B. nicht über SharePoint-Projektelemente zum Hinzufügen von Feldern oder benutzerdefinierten Aktionen zu einer SharePoint-Website. Sie können eigene Typen von SharePoint-Projektelemente zum Erstellen von Feldern, benutzerdefinierte Aktionen oder andere Arten von SharePoint-Komponenten definieren.  
  
## <a name="tasks-for-defining-sharepoint-project-item-types"></a>Aufgaben zum Definieren von SharePoint-Projektelementtypen  
 Um einen benutzerdefinierten Projektelementtyp definieren möchten, erstellen Sie eine Assembly der Visual Studio-Erweiterung, die implementiert die <xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectItemTypeProvider> Schnittstelle. Weitere Informationen finden Sie unter [wie: Definieren Sie einen SharePoint-Projektelementtyp](../sharepoint/how-to-define-a-sharepoint-project-item-type.md).  
  
 Wenn Sie einen benutzerdefinierten Projektelementtyp definieren, können Sie auch die folgende Funktionen, die im Projektelement hinzufügen:  
  
-   Das Projektelement ein Kontextmenüelement hinzugefügt. Das Menüelement wird angezeigt, wenn Sie das Kontextmenü für das Projektelement in öffnen **Projektmappen-Explorer** durch Rechtsklick auf das Projektelement oder indem Sie ihn auswählen, und drücken Sie dann UMSCHALT + F10-Tasten. Weitere Informationen finden Sie unter [wie: Hinzufügen eines Kontextmenüelements zu einem benutzerdefinierten SharePoint-Projektelementtyp](../sharepoint/how-to-add-a-shortcut-menu-item-to-a-custom-sharepoint-project-item-type.md).  
  
-   Fügen Sie dem Projektelement eine benutzerdefinierte Eigenschaft hinzu. Die Eigenschaft wird in der **Eigenschaften** Fenster bei der Auswahl des Projektelements im **Projektmappen-Explorer**. Weitere Informationen finden Sie unter [wie: Hinzufügen einer Eigenschaft zu einem benutzerdefinierten SharePoint-Projektelementtyp](../sharepoint/how-to-add-a-property-to-a-custom-sharepoint-project-item-type.md).  
  
 Damit andere Entwickler um Ihr Projektelement in Visual Studio verwenden, erstellen Sie eine SPDATA-Datei, und erstellen Sie eine Elementvorlage oder -Projektvorlage, die das Projektelement zugeordnet ist. Weitere Informationen finden Sie unter [Erstellen von Elementvorlagen und Projektvorlagen für SharePoint-Projektelemente](../sharepoint/creating-item-templates-and-project-templates-for-sharepoint-project-items.md).  
  
## <a name="understanding-the-relationship-between-project-item-types-and-project-item-instances"></a>Grundlegendes zur Beziehung zwischen Projektelementtypen und Instanzen von Project-Element  
 Wenn Sie einen SharePoint-Projektelementtyp definieren, lädt Visual Studio die Erweiterung aus, wenn ein SharePoint-Projekt ein Projektelement des zugeordneten Typs hinzugefügt wird. Angenommen, wenn Sie einen neuen definieren **benutzerdefinierte Aktion** -Projektelementtyp, lädt Visual Studio die Erweiterung aus, wenn ein Benutzer hinzufügt eine **benutzerdefinierte Aktion** Projektelement zu einem Projekt. Visual Studio verwendet dieselbe Instanz der Erweiterung für alle Instanzen des Elementtyps zugeordnete-Projekt. Im vorherigen Beispiel, wenn der Benutzer ein zweites fügt **benutzerdefinierte Aktion** Projektelementdateien auf das Projekt, dieselbe Instanz der Erweiterung wird verwendet, um das zweite Projektelement anzupassen.  
  
 Um eine bestimmte Instanz des Projektelementtyps zuzugreifen, behandeln Sie eines der der <xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectItemEvents> Ereignisse der *ProjectItemTypeDefinition* Parameter in der Implementierung von der <xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectItemTypeProvider.InitializeType%2A> Methode. Um zu bestimmen, wann ein Projektelement des benutzerdefinierten Typs zu einem Projekt hinzugefügt wird, z. B. Behandeln der <xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectItemEvents.ProjectItemAdded> Ereignis. Weitere Informationen finden Sie unter [wie: Definieren Sie einen SharePoint-Projektelementtyp](../sharepoint/how-to-define-a-sharepoint-project-item-type.md).  
  
## <a name="see-also"></a>Siehe auch  
 [Vorgehensweise: Definieren Sie einen SharePoint-Projektelementtyp](../sharepoint/how-to-define-a-sharepoint-project-item-type.md)   
 [Vorgehensweise: Hinzufügen einer Eigenschaft zu einem benutzerdefinierten SharePoint-Projektelementtyp](../sharepoint/how-to-add-a-property-to-a-custom-sharepoint-project-item-type.md)   
 [Vorgehensweise: Hinzufügen ein Kontextmenüelements zu einer benutzerdefinierten SharePoint-Projektelementtyp](../sharepoint/how-to-add-a-shortcut-menu-item-to-a-custom-sharepoint-project-item-type.md)   
 [Erstellen von Elementvorlagen und Projektvorlagen für SharePoint-Projektelemente](../sharepoint/creating-item-templates-and-project-templates-for-sharepoint-project-items.md)   
 [Exemplarische Vorgehensweise: Erstellen eines Projektelements für die benutzerdefinierte Aktion mit einer Elementvorlage, Teil 1](../sharepoint/walkthrough-creating-a-custom-action-project-item-with-an-item-template-part-1.md)   
 [Exemplarische Vorgehensweise: Erstellen ein Projekts Websitespalte mit einer Projektvorlage, Teil 1](../sharepoint/walkthrough-creating-a-site-column-project-item-with-a-project-template-part-1.md)   
 [Exemplarische Vorgehensweise: Erstellen eines Projektelements benutzerdefinierte Aktion mit einer Elementvorlage, Teil 2](../sharepoint/walkthrough-creating-a-custom-action-project-item-with-an-item-template-part-2.md)   
 [Exemplarische Vorgehensweise: Erstellen ein Projekts Websitespalte mit einer Projektvorlage, Teil 2](../sharepoint/walkthrough-creating-a-site-column-project-item-with-a-project-template-part-2.md)   
 [Bereitstellen von Erweiterungen für die SharePoint-Tools in Visual Studio](../sharepoint/deploying-extensions-for-the-sharepoint-tools-in-visual-studio.md)  
  
  