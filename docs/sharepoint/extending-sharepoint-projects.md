---
title: "Extending SharePoint Projects"
ms.custom: ""
ms.date: "02/02/2017"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "office-development"
ms.tgt_pltfrm: ""
ms.topic: "article"
dev_langs: 
  - "VB"
  - "CSharp"
helpviewer_keywords: 
  - "projects [SharePoint development in Visual Studio], extending"
  - "SharePoint development in Visual Studio, extending projects"
  - "SharePoint projects, extending"
ms.assetid: 4643012b-6e6c-4b7c-bb92-b04b34f6c715
caps.latest.revision: 19
author: "kempb"
ms.author: "kempb"
manager: "ghogen"
caps.handback.revision: 18
---
# Extending SharePoint Projects
  Erstellen Sie eine Projekterweiterung, wenn Sie Funktionen auf der Projektebene von SharePoint\-Projekten anpassen möchten.  Sie können z. B. benutzerdefinierte Projekteigenschaften hinzufügen oder auf Ereignisse auf Projektebene reagieren, die ausgelöst werden, wenn der Benutzer in Visual Studio eine SharePoint\-Lösung entwickelt.  
  
## Erstellen von Projekterweiterungen  
 Um ein Projektelement zu erweitern, erstellen Sie eine Visual Studio\-Erweiterungsassembly, die die <xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectExtension>\-Schnittstelle implementiert.  Weitere Informationen finden Sie unter [How to: Create a SharePoint Project Extension](../sharepoint/how-to-create-a-sharepoint-project-extension.md).  
  
 Wenn Sie eine Projekterweiterung erstellen, können Sie den SharePoint\-Projekten auch die folgende Funktionalität hinzufügen:  
  
-   Fügen Sie ein Kontextmenüelement hinzu.  Das Menüelement wird angezeigt, wenn Sie das Kontextmenü für einen SharePoint\-Projektknoten in **Projektmappen\-Explorer** öffnen, indem Sie mit der rechten Maustaste auf den Knoten klicken oder diese auswählen und dann die UMSCHALT\+F10\-Tasten auswählen.  Weitere Informationen finden Sie unter [How to: Add a Shortcut Menu Item to SharePoint Projects](../sharepoint/how-to-add-a-shortcut-menu-item-to-sharepoint-projects.md).  
  
-   Fügen Sie eine benutzerdefinierte Eigenschaft hinzu.  Die Eigenschaft wird im Fenster **Eigenschaften**, wenn Sie ein SharePoint\-Projekt in **Projektmappen\-Explorer** auswählen.  Weitere Informationen finden Sie unter [How to: Add a Property to SharePoint Projects](../sharepoint/how-to-add-a-property-to-sharepoint-projects.md).  
  
 Eine exemplarische Vorgehensweise, die das Erstellen, Bereitstellen und Testen einer Projekterweiterung veranschaulicht, finden Sie unter [Walkthrough: Creating a SharePoint Project Extension](../sharepoint/walkthrough-creating-a-sharepoint-project-extension.md).  
  
## Grundlegendes zur Beziehung zwischen Projekterweiterungen und Projektinstanzen  
 Wenn Sie eine Projekterweiterung erstellen, wird die Erweiterung bei jedem Öffnen eines SharePoint\-Projekts in [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] geladen. [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] enthält mehrere SharePoint\-Projektvorlagen, z. B. Listendefinitionen, Inhaltstypen und Ereignisempfänger.  Es gibt jedoch nur einen SharePoint\-Projekttyp.  Die Projekttypen, die im Dialogfeld **Neues Projekt** angezeigt werden, sind nur Vorlagen, die mindestens ein SharePoint\-Projektelement enthalten bzw. zusammenfassen.  Da es nur einen SharePoint\-Projekttyp gibt, gelten für ein Projekt erstellte Erweiterungen für alle SharePoint\-Projekte.  Beispielsweise können Sie keine Erweiterung erstellen, die nur für ein **Inhaltstyp**\-Projekt gilt.  
  
 Um auf eine bestimmte Projektinstanz zuzugreifen, behandeln Sie eines der <xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectEvents>\-Ereignisse des *projectService*\-Parameters in der Implementierung der <xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectExtension.Initialize%2A>\-Methode.  Um z. B. festzulegen, wann ein SharePoint\-Projekt einer Projektmappe hinzugefügt wird, behandeln Sie das <xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectEvents.ProjectAdded>\-Ereignis.  Weitere Informationen finden Sie unter [How to: Create a SharePoint Project Extension](../sharepoint/how-to-create-a-sharepoint-project-extension.md).  
  
## Siehe auch  
 [How to: Create a SharePoint Project Extension](../sharepoint/how-to-create-a-sharepoint-project-extension.md)   
 [How to: Add a Shortcut Menu Item to SharePoint Projects](../sharepoint/how-to-add-a-shortcut-menu-item-to-sharepoint-projects.md)   
 [How to: Add a Property to SharePoint Projects](../sharepoint/how-to-add-a-property-to-sharepoint-projects.md)   
 [Walkthrough: Creating a SharePoint Project Extension](../sharepoint/walkthrough-creating-a-sharepoint-project-extension.md)   
 [Defining Custom SharePoint Project Item Types](../sharepoint/defining-custom-sharepoint-project-item-types.md)   
 [Extending SharePoint Project Items](../sharepoint/extending-sharepoint-project-items.md)   
 [Extending SharePoint Packaging and Deployment](../sharepoint/extending-sharepoint-packaging-and-deployment.md)   
 [Extending the SharePoint Project System](../sharepoint/extending-the-sharepoint-project-system.md)  
  
  