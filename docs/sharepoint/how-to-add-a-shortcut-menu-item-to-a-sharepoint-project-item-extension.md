---
title: "How to: Add a Shortcut Menu Item to a SharePoint Project Item Extension"
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
  - "project items [SharePoint development in Visual Studio], extending"
  - "SharePoint project items, extending"
  - "SharePoint development in Visual Studio, extending project items"
ms.assetid: d00513a6-d66d-4fbe-9efa-ef3b08c9a73a
caps.latest.revision: 17
author: "kempb"
ms.author: "kempb"
manager: "ghogen"
caps.handback.revision: 16
---
# How to: Add a Shortcut Menu Item to a SharePoint Project Item Extension
  Sie können einem vorhandenen SharePoint\-Projektelement mithilfe einer Projektelementerweiterung ein Kontextmenüelement hinzufügen.  Das Menüelement wird angezeigt, wenn der Benutzer im **Projektmappen\-Explorer** mit der rechten Maustaste auf das Projektelement klickt.  
  
 Im Folgenden wird angenommen, dass bereits eine Projektelementerweiterung erstellt wurde.  Weitere Informationen erhalten Sie unter [How to: Create a SharePoint Project Item Extension](../sharepoint/how-to-create-a-sharepoint-project-item-extension.md).  
  
### So fügen Sie ein Kontextmenüelement einer Projektelementerweiterung hinzu  
  
1.  Bearbeiten Sie in der <xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectItemTypeExtension.Initialize%2A>\-Methode Ihrer <xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectItemTypeExtension>\-Implementierung das <xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectItemEvents.ProjectItemMenuItemsRequested>\-Ereignis des *projectItemType*\-Parameters.  
  
2.  Fügen Sie im Ereignishandler für das <xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectItemEvents.ProjectItemMenuItemsRequested>\-Ereignis der <xref:Microsoft.VisualStudio.SharePoint.SharePointProjectItemMenuItemsRequestedEventArgs.ViewMenuItems%2A>\- oder <xref:Microsoft.VisualStudio.SharePoint.SharePointProjectItemMenuItemsRequestedEventArgs.AddMenuItems%2A>\-Auflistung des Parameters für Ereignisargumente ein neues <xref:Microsoft.VisualStudio.SharePoint.IMenuItem>\-Objekt hinzu.  
  
3.  Führen Sie im <xref:Microsoft.VisualStudio.SharePoint.IMenuItem.Click>\-Ereignishandler für das neue <xref:Microsoft.VisualStudio.SharePoint.IMenuItem>\-Objekt die Aufgaben aus, die ausgeführt werden sollen, wenn ein Benutzer auf das Kontextmenüelement klickt.  
  
## Beispiel  
 Im folgenden Codebeispiel wird veranschaulicht, wie dem Ereignisempfänger\-Projektelement ein Kontextmenüelement hinzugefügt wird.  Wenn der Benutzer mit der rechten Maustaste auf das Projektelement im **Projektmappen\-Explorer** klickt und auf das Menüelement zum Schreiben der Nachricht in das Ausgabefenster klickt, zeigt Visual Studio im Fenster **Ausgabe** eine Meldung an.  
  
 [!code-csharp[SPExtensibility.ProjectItemExtension.MenuAndProperty#1](../snippets/csharp/VS_Snippets_OfficeSP/spextensibility.projectitemextension.menuandproperty/cs/extension/projectitemextensionmenu.cs#1)]
 [!code-vb[SPExtensibility.ProjectItemExtension.MenuAndProperty#1](../snippets/visualbasic/VS_Snippets_OfficeSP/spextensibility.projectitemextension.menuandproperty/vb/extension/projectitemextensionmenu.vb#1)]  
  
 In diesem Beispiel wird der SharePoint\-Projektdienst verwendet, um die Nachricht in das Fenster **Ausgabe** zu schreiben.  Weitere Informationen finden Sie unter [Using the SharePoint Project Service](../sharepoint/using-the-sharepoint-project-service.md).  
  
## Kompilieren des Codes  
 Für dieses Beispiel ist ein Klassenbibliotheksprojekt mit Verweisen auf die folgenden Assemblys erforderlich:  
  
-   Microsoft.VisualStudio.SharePoint  
  
-   System.ComponentModel.Composition  
  
## Bereitstellen der Erweiterung  
 Erstellen Sie ein [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)]\-Erweiterungspaket \(VSIX\) für die Assembly und alle weiteren Dateien, die Sie mit der Erweiterung verteilen möchten, um die Erweiterung bereitzustellen.  Weitere Informationen erhalten Sie unter [Deploying Extensions for the SharePoint Tools in Visual Studio](../sharepoint/deploying-extensions-for-the-sharepoint-tools-in-visual-studio.md).  
  
## Siehe auch  
 [How to: Create a SharePoint Project Item Extension](../sharepoint/how-to-create-a-sharepoint-project-item-extension.md)   
 [How to: Add a Property to a SharePoint Project Item Extension](../sharepoint/how-to-add-a-property-to-a-sharepoint-project-item-extension.md)   
 [Extending SharePoint Project Items](../sharepoint/extending-sharepoint-project-items.md)   
 [Walkthrough: Extending a SharePoint Project Item Type](../sharepoint/walkthrough-extending-a-sharepoint-project-item-type.md)  
  
  