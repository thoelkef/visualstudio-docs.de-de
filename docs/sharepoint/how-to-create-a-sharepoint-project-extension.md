---
title: "How to: Create a SharePoint Project Extension | Microsoft Docs"
ms.custom: ""
ms.date: "04/28/2017"
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
ms.assetid: ceecb9cb-4a5d-44c9-992f-9624737ac996
caps.latest.revision: 29
author: "kempb"
ms.author: "kempb"
manager: "ghogen"
caps.handback.revision: 28
---
# How to: Create a SharePoint Project Extension
  Erstellen Sie eine Projekterweiterung, wenn Sie Funktionalität zu einem SharePoint\-Projekt hinzufügen möchten, das in Visual Studio geöffnet ist.  Weitere Informationen finden Sie unter [Extending the SharePoint Project System](../sharepoint/extending-the-sharepoint-project-system.md).  
  
### So erstellen Sie eine Projekterweiterung  
  
1.  Erstellen Sie ein Klassenbibliotheksprojekt.  
  
2.  Fügen Sie Verweise auf die folgenden Assemblys hinzu:  
  
    -   Microsoft.VisualStudio.SharePoint  
  
    -   System.ComponentModel.Composition  
  
3.  Erstellen Sie eine Klasse, die die <xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectExtension>\-Schnittstelle implementiert.  
  
4.  Fügen Sie der Klasse <xref:System.ComponentModel.Composition.ExportAttribute> hinzu.  Anhand dieses Attributs kann Visual Studio Ihre <xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectExtension>\-Implementierung erkennen und laden.  Übergeben Sie den <xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectExtension>\-Typ an den Attributkonstruktor.  
  
5.  Verwenden Sie in der Implementierung der <xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectExtension.Initialize%2A>\-Methode Member des *projectService*\-Parameters, um das Verhalten der Erweiterung zu definieren.  Dieser Parameter ist ein <xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectService>\-Objekt, das Zugriff auf die in der <xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectEvents>\-Schnittstelle definierten Ereignisse bietet.  
  
## Beispiel  
 Im folgenden Codebeispiel wird das Erstellen einer einfachen Projekterweiterung veranschaulicht, die den Großteil der von der <xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectEvents>\-Schnittstelle definierten SharePoint\-Projektereignisse behandelt.  Zum Testen des Codes erstellen Sie in [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] ein SharePoint\-Projekt, und fügen Sie der Lösung weitere Projekte hinzu, ändern Sie Projekteigenschaftswerte oder löschen Sie ein Projekt bzw. schließen Sie ein Projekt aus.  Die Erweiterung benachrichtigt Sie über Ereignisse mit Meldungen in den Fenstern **Ausgabe** und **Fehlerliste**.  
  
 [!code-csharp[SPExtensibility.ProjectSystemExtension.General#3](../snippets/csharp/VS_Snippets_OfficeSP/spextensibility.projectsystemextension.general/cs/extension/projectextension.cs#3)]
 [!code-vb[SPExtensibility.ProjectSystemExtension.General#3](../snippets/visualbasic/VS_Snippets_OfficeSP/spextensibility.projectsystemextension.general/vb/extension/projectextension.vb#3)]
 [!code-vb[SPExtensibility.ProjectSystemExtension.General#3](../snippets/visualbasic/VS_Snippets_OfficeSP/spextensibility.projectsystemextension.general/vb/extension/savedatatoprojectfile.vb#3)]  
  
 In diesem Beispiel wird der SharePoint\-Projektdienst verwendet, um die Meldung in die Fenster **Ausgabe** und **Fehlerliste** zu schreiben.  Weitere Informationen finden Sie unter [Using the SharePoint Project Service](../sharepoint/using-the-sharepoint-project-service.md).  
  
 Beispiele, in denen die Behandlung der <xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectEvents.ProjectMenuItemsRequested>\- und <xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectEvents.ProjectPropertiesRequested>\-Ereignisse veranschaulicht wird, finden Sie unter [How to: Add a Shortcut Menu Item to SharePoint Projects](../sharepoint/how-to-add-a-shortcut-menu-item-to-sharepoint-projects.md) und [How to: Add a Property to SharePoint Projects](../sharepoint/how-to-add-a-property-to-sharepoint-projects.md).  
  
## Kompilieren des Codes  
 Für dieses Beispiel sind Verweise auf die folgenden Assemblys erforderlich:  
  
-   Microsoft.VisualStudio.SharePoint  
  
-   System.ComponentModel.Composition  
  
## Bereitstellen der Erweiterung  
 Erstellen Sie ein [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)]\-Erweiterungspaket \(VSIX\) für die Assembly und alle weiteren Dateien, die Sie mit der Erweiterung verteilen möchten, um die Erweiterung bereitzustellen.  Weitere Informationen erhalten Sie unter [Deploying Extensions for the SharePoint Tools in Visual Studio](../sharepoint/deploying-extensions-for-the-sharepoint-tools-in-visual-studio.md).  
  
## Siehe auch  
 [Extending the SharePoint Project System](../sharepoint/extending-the-sharepoint-project-system.md)   
 [How to: Add a Shortcut Menu Item to SharePoint Projects](../sharepoint/how-to-add-a-shortcut-menu-item-to-sharepoint-projects.md)   
 [How to: Add a Property to SharePoint Projects](../sharepoint/how-to-add-a-property-to-sharepoint-projects.md)   
 [Walkthrough: Creating a SharePoint Project Extension](../sharepoint/walkthrough-creating-a-sharepoint-project-extension.md)  
  
  