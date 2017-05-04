---
title: "How to: Get Data for a Built-In SharePoint Node in Server Explorer | Microsoft Docs"
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
  - "SharePoint Connections [SharePoint development in Visual Studio], extending a node"
  - "SharePoint development in Visual Studio, extending SharePoint Connections node in Server Explorer"
ms.assetid: 86d04e0a-c114-427e-9945-da5fa339fda4
caps.latest.revision: 7
author: "kempb"
ms.author: "kempb"
manager: "ghogen"
caps.handback.revision: 6
---
# How to: Get Data for a Built-In SharePoint Node in Server Explorer
  Für jeden integrierten SharePoint\-Knoten im Server\-Explorer können Sie Daten für die zugrunde liegende, durch den Knoten dargestellte SharePoint\-Komponente abrufen.  Weitere Informationen finden Sie unter [Extending the SharePoint Connections Node in Server Explorer](../sharepoint/extending-the-sharepoint-connections-node-in-server-explorer.md).  
  
## Beispiel  
 Im folgenden Codebeispiel wird veranschaulicht, wie Daten für die zugrunde liegende, durch einen Listenknoten im Server\-Explorer dargestellte SharePoint\-Liste abgerufen werden.  Standardmäßig ist für Listenknoten das Kontextmenüelement **In Browser anzeigen** verfügbar, auf das Sie klicken können, um die Listen in einem Webbrowser zu öffnen.  In diesem Beispiel werden Listenknoten erweitert, indem dem Kontextmenü das Element **In Visual Studio anzeigen** hinzufügt wird, um die Listen direkt in Visual Studio zu öffnen.  Mit dem Code wird auf die Listendaten für den Knoten zugegriffen, um die URL der in Visual Studio zu öffnenden Liste abzurufen.  
  
 [!code-csharp[SPExtensibility.ProjectSystemExtension.General#10](../snippets/csharp/VS_Snippets_OfficeSP/spextensibility.projectsystemextension.general/cs/extension/serverexplorerextensionnodeinfo.cs#10)]
 [!code-vb[SPExtensibility.ProjectSystemExtension.General#10](../snippets/visualbasic/VS_Snippets_OfficeSP/spextensibility.projectsystemextension.general/vb/extension/serverexplorerextensionnodeinfo.vb#10)]  
  
 In diesem Beispiel wird das <xref:EnvDTE.DTE>\-Objekt, das zum Öffnen von Listen in Visual Studio verwendet wird, mithilfe des SharePoint\-Projektdiensts abgerufen.  Weitere Informationen zum SharePoint\-Projektdienst finden Sie unter [Using the SharePoint Project Service](../sharepoint/using-the-sharepoint-project-service.md).  
  
 Weitere Informationen zu den grundlegenden Aufgaben beim Erstellen einer Erweiterung für einen SharePoint\-Knoten finden Sie unter [How to: Extend a SharePoint Node in Server Explorer](../sharepoint/how-to-extend-a-sharepoint-node-in-server-explorer.md).  
  
## Kompilieren des Codes  
 Für dieses Beispiel sind Verweise auf die folgenden Assemblys erforderlich:  
  
-   EnvDTE  
  
-   Microsoft.VisualStudio.SharePoint  
  
-   Microsoft.VisualStudio.SharePoint.Explorer.Extensions  
  
-   System.ComponentModel.Composition  
  
## Bereitstellen der Erweiterung  
 Um die **Server\-Explorer**\-Erweiterung bereitzustellen, erstellen Sie ein [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)]\-Erweiterungspaket \(VSIX\) für die Assembly und alle weiteren Dateien, die Sie mit der Erweiterung verteilen möchten.  Weitere Informationen erhalten Sie unter [Deploying Extensions for the SharePoint Tools in Visual Studio](../sharepoint/deploying-extensions-for-the-sharepoint-tools-in-visual-studio.md).  
  
## Siehe auch  
 [Extending the SharePoint Connections Node in Server Explorer](../sharepoint/extending-the-sharepoint-connections-node-in-server-explorer.md)   
 [How to: Extend a SharePoint Node in Server Explorer](../sharepoint/how-to-extend-a-sharepoint-node-in-server-explorer.md)   
 [Using the SharePoint Project Service](../sharepoint/using-the-sharepoint-project-service.md)   
 [Deploying Extensions for the SharePoint Tools in Visual Studio](../sharepoint/deploying-extensions-for-the-sharepoint-tools-in-visual-studio.md)  
  
  