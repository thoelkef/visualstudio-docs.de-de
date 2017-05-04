---
title: "How to: Add a Shortcut Menu Item to SharePoint Projects | Microsoft Docs"
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
ms.assetid: bb251fe9-f1bf-4ddd-9359-4b7f78fbd50f
caps.latest.revision: 9
author: "kempb"
ms.author: "kempb"
manager: "ghogen"
caps.handback.revision: 8
---
# How to: Add a Shortcut Menu Item to SharePoint Projects
  Jedem SharePoint\-Projekt kann ein Kontextmenüelement hinzugefügt werden.  Das Menüelement wird angezeigt, wenn der Benutzer im Projektmappen\-Explorer mit der rechten Maustaste auf einen Projektknoten klickt.  
  
 Im Folgenden wird vorausgesetzt, dass bereits eine Projekterweiterung erstellt wurde.  Weitere Informationen finden Sie unter [How to: Create a SharePoint Project Extension](../sharepoint/how-to-create-a-sharepoint-project-extension.md).  
  
### So fügen Sie SharePoint\-Projekten ein Kontextmenüelement hinzu  
  
1.  Behandeln Sie in der <xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectExtension.Initialize%2A>\-Methode der <xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectExtension>\-Implementierung das <xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectEvents.ProjectMenuItemsRequested>\-Ereignis des *projectService*\-Parameters.  
  
2.  Fügen Sie im Ereignishandler für das <xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectEvents.ProjectMenuItemsRequested>\-Ereignis ein neues <xref:Microsoft.VisualStudio.SharePoint.IMenuItem>\-Objekt zur <xref:Microsoft.VisualStudio.SharePoint.SharePointProjectMenuItemsRequestedEventArgs.ActionMenuItems%2A>\-Auflistung oder zur <xref:Microsoft.VisualStudio.SharePoint.SharePointProjectMenuItemsRequestedEventArgs.AddMenuItems%2A>\-Auflistung des Parameters für Ereignisargumente hinzu.  
  
3.  Führen Sie im <xref:Microsoft.VisualStudio.SharePoint.IMenuItem.Click>\-Ereignishandler für das neue <xref:Microsoft.VisualStudio.SharePoint.IMenuItem>\-Objekt die Aufgaben aus, die ausgeführt werden sollen, wenn ein Benutzer auf das Kontextmenüelement klickt.  
  
## Beispiel  
 Im folgenden Codebeispiel wird das Hinzufügen eines Kontextmenüelements zu SharePoint\-Projektknoten im Projektmappen\-Explorer veranschaulicht.  Wenn der Benutzer mit der rechten Maustaste auf einen Projektknoten und anschließend auf das Menüelement zum Schreiben der Nachricht in das Ausgabefenster klickt, wird im Ausgabefenster eine Meldung angezeigt.  In diesem Beispiel wird die Meldung mithilfe des SharePoint\-Projektdiensts angezeigt.  Weitere Informationen finden Sie unter [Using the SharePoint Project Service](../sharepoint/using-the-sharepoint-project-service.md).  
  
 [!code-csharp[SPExtensibility.ProjectExtension.Menu#1](../snippets/csharp/VS_Snippets_OfficeSP/spextensibility.projectextension.menu/cs/extension/projectitemextensionmenu.cs#1)]
 [!code-vb[SPExtensibility.ProjectExtension.Menu#1](../snippets/visualbasic/VS_Snippets_OfficeSP/spextensibility.projectextension.menu/vb/extension/projectitemextensionmenu.vb#1)]  
  
## Kompilieren des Codes  
 Für dieses Beispiel ist ein Klassenbibliotheksprojekt mit Verweisen auf die folgenden Assemblys erforderlich:  
  
-   Microsoft.VisualStudio.SharePoint  
  
-   System.ComponentModel.Composition  
  
## Bereitstellen der Erweiterung  
 Erstellen Sie ein [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)]\-Erweiterungspaket \(VSIX\) für die Assembly und alle weiteren Dateien, die Sie mit der Erweiterung verteilen möchten, um die Erweiterung bereitzustellen.  Weitere Informationen erhalten Sie unter [Deploying Extensions for the SharePoint Tools in Visual Studio](../sharepoint/deploying-extensions-for-the-sharepoint-tools-in-visual-studio.md).  
  
## Siehe auch  
 [Extending SharePoint Projects](../sharepoint/extending-sharepoint-projects.md)   
 [How to: Create a SharePoint Project Extension](../sharepoint/how-to-create-a-sharepoint-project-extension.md)   
 [How to: Add a Property to SharePoint Projects](../sharepoint/how-to-add-a-property-to-sharepoint-projects.md)  
  
  