---
title: "How to: Add a Shortcut Menu Item to a Custom SharePoint Project Item Type | Microsoft Docs"
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
  - "SharePoint project items, defining your own types"
  - "project items [SharePoint development in Visual Studio], defining your own types"
  - "SharePoint development in Visual Studio, defining new project item types"
ms.assetid: f6ec47a7-e7d9-4e26-810b-77943a1ab04c
caps.latest.revision: 10
author: "kempb"
ms.author: "kempb"
manager: "ghogen"
caps.handback.revision: 9
---
# How to: Add a Shortcut Menu Item to a Custom SharePoint Project Item Type
  Wenn Sie einen benutzerdefinierten SharePoint\-Projektelementtyp definieren, können Sie dem Projektelement ein Kontextmenüelement hinzufügen.  Das Menüelement wird angezeigt, wenn der Benutzer im **Projektmappen\-Explorer** mit der rechten Maustaste auf das Projektelement klickt.  
  
 Im Folgenden wird angenommen, dass bereits ein eigener SharePoint\-Projektelementtyp definiert wurde.  Weitere Informationen finden Sie unter [How to: Define a SharePoint Project Item Type](../sharepoint/how-to-define-a-sharepoint-project-item-type.md).  
  
### So fügen Sie einem benutzerdefinierten Projektelementtyp ein Kontextmenüelement hinzu  
  
1.  Behandeln Sie in der <xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectItemTypeProvider.InitializeType%2A>\-Methode Ihrer <xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectItemTypeProvider>\-Implementierung das <xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectItemEvents.ProjectItemMenuItemsRequested>\-Ereignis des *projectItemTypeDefinition*\-Parameters.  
  
2.  Fügen Sie im Ereignishandler für das <xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectItemEvents.ProjectItemMenuItemsRequested>\-Ereignis der <xref:Microsoft.VisualStudio.SharePoint.SharePointProjectItemMenuItemsRequestedEventArgs.ViewMenuItems%2A>\- oder <xref:Microsoft.VisualStudio.SharePoint.SharePointProjectItemMenuItemsRequestedEventArgs.AddMenuItems%2A>\-Auflistung des Parameters für Ereignisargumente ein neues <xref:Microsoft.VisualStudio.SharePoint.IMenuItem>\-Objekt hinzu.  
  
3.  Im <xref:Microsoft.VisualStudio.SharePoint.IMenuItem.Click>\-Ereignishandler für das neue \- Objekt <xref:Microsoft.VisualStudio.SharePoint.IMenuItem>, führen Sie die Aufgaben aus, die Sie ausführen möchten, wenn ein Benutzer das Kontextmenüelement auswählt.  
  
## Beispiel  
 Im folgenden Codebeispiel wird veranschaulicht, wie einem benutzerdefinierten Projektelementtyp ein Kontextmenüelement hinzugefügt wird.  Wenn der Benutzer das Kontextmenü im Projektelement in **Projektmappen\-Explorer** wird und im **Schreiben Sie Nachricht in das Ausgabefenster** Menüelement auswählt, zeigt Visual Studio eine Meldung im Fenster **Ausgabe** an.  
  
 [!code-csharp[SPExtensibility.ProjectItemExtension.MenuAndProperty#4](../snippets/csharp/VS_Snippets_OfficeSP/spextensibility.projectitemextension.menuandproperty/cs/extension/projectitemtypemenu.cs#4)]
 [!code-vb[SPExtensibility.ProjectItemExtension.MenuAndProperty#4](../snippets/visualbasic/VS_Snippets_OfficeSP/spextensibility.projectitemextension.menuandproperty/vb/extension/projectitemtypemenu.vb#4)]  
  
 In diesem Beispiel wird der SharePoint\-Projektdienst verwendet, um die Nachricht in das Fenster **Ausgabe** zu schreiben.  Weitere Informationen finden Sie unter [Using the SharePoint Project Service](../sharepoint/using-the-sharepoint-project-service.md).  
  
## Kompilieren des Codes  
 Für dieses Beispiel ist ein Klassenbibliotheksprojekt mit Verweisen auf die folgenden Assemblys erforderlich:  
  
-   Microsoft.VisualStudio.SharePoint  
  
-   System.ComponentModel.Composition  
  
## Bereitstellen des Projektelements  
 Um Ihr Projektelement anderen Entwicklern zur Verfügung zu stellen, können Sie eine Projektvorlage oder eine Projektelementvorlage erstellen.  Weitere Informationen finden Sie unter [Creating Item Templates and Project Templates for SharePoint Project Items](../sharepoint/creating-item-templates-and-project-templates-for-sharepoint-project-items.md).  
  
 Erstellen Sie zum Bereitstellen des Projektelements ein [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)]\-Erweiterungspaket \(VSIX\) für die Assembly, die Vorlage und alle weiteren Dateien, die Sie mit dem Projektelement verteilen möchten.  Weitere Informationen finden Sie unter [Deploying Extensions for the SharePoint Tools in Visual Studio](../sharepoint/deploying-extensions-for-the-sharepoint-tools-in-visual-studio.md).  
  
## Siehe auch  
 [How to: Define a SharePoint Project Item Type](../sharepoint/how-to-define-a-sharepoint-project-item-type.md)   
 [How to: Add a Property to a Custom SharePoint Project Item Type](../sharepoint/how-to-add-a-property-to-a-custom-sharepoint-project-item-type.md)   
 [Defining Custom SharePoint Project Item Types](../sharepoint/defining-custom-sharepoint-project-item-types.md)  
  
  