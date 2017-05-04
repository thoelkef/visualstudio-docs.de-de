---
title: "How to: Retrieve the SharePoint Project Service | Microsoft Docs"
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
  - "SharePoint project service"
ms.assetid: 3d8b7adf-2603-4247-9b61-6326a1dd0dec
caps.latest.revision: 15
author: "kempb"
ms.author: "kempb"
manager: "ghogen"
caps.handback.revision: 14
---
# How to: Retrieve the SharePoint Project Service
  Sie können auf den SharePoint\-Projektdienst in den folgenden Projektmappentypen zugreifen:  
  
-   Eine Erweiterung des SharePoint\-Projektsystems, z. B. eine Projekterweiterung, Projektelementerweiterung oder Projektelementtypdefinition.  Weitere Informationen zu diesen Erweiterungstypen finden Sie unter [Extending the SharePoint Project System](../sharepoint/extending-the-sharepoint-project-system.md).  
  
-   Eine Erweiterung des Knotens **SharePoint\-Verbindungen** in **Server\-Explorer**.  Weitere Informationen zu diesen Erweiterungstypen finden Sie unter [Extending the SharePoint Connections Node in Server Explorer](../sharepoint/extending-the-sharepoint-connections-node-in-server-explorer.md).  
  
-   Ein anderer Erweiterungstyp für Visual Studio, z. B. ein Add\-In oder ein VSPackage.  
  
## Abrufen des Diensts in Projektsystemerweiterungen  
 In jeder Erweiterung des SharePoint\-Projektsystems können Sie mit der <xref:Microsoft.VisualStudio.SharePoint.ISharePointProject.ProjectService%2A>\-Eigenschaft eines <xref:Microsoft.VisualStudio.SharePoint.ISharePointProject>\-Objekts auf den Projektdienst zugreifen.  
  
 Sie können den Projektdienst auch mit den folgenden Prozeduren abrufen.  
  
#### So rufen Sie den Dienst in einer Projekterweiterung ab  
  
1.  Suchen Sie in Ihrer Implementierung der <xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectExtension>\-Schnittstelle die <xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectExtension.Initialize%2A>\-Methode.  
  
2.  Verwenden Sie den *projectService*\-Parameter, um auf den Dienst zuzugreifen.  
  
     Im folgenden Codebeispiel wird veranschaulicht, wie der Projektdienst verwendet wird, um in einer einfachen Projekterweiterung eine Meldung in das Fenster **Ausgabe** und das Fenster **Fehlerliste** zu schreiben.  
  
     [!code-csharp[SPExtensibility.ProjectService.FromProjectSystemExtensions#1](../snippets/csharp/VS_Snippets_OfficeSP/spextensibility.projectservice.fromprojectsystemextensions/cs/extension/extension.cs#1)]
     [!code-vb[SPExtensibility.ProjectService.FromProjectSystemExtensions#1](../snippets/visualbasic/VS_Snippets_OfficeSP/spextensibility.projectservice.fromprojectsystemextensions/vb/extension/extension.vb#1)]  
  
     Weitere Informationen zum Erstellen von Projekterweiterungen finden Sie unter [How to: Create a SharePoint Project Extension](../sharepoint/how-to-create-a-sharepoint-project-extension.md).  
  
#### So rufen Sie den Dienst in einer Projektelementerweiterung ab  
  
1.  Suchen Sie in Ihrer Implementierung der <xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectItemTypeExtension>\-Schnittstelle die <xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectItemTypeExtension.Initialize%2A>\-Methode.  
  
2.  Verwenden Sie die <xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectItemType.ProjectService%2A>\-Eigenschaft des *projectItemType*\-Parameters, um den Dienst abzurufen.  
  
     Im folgenden Codebeispiel wird veranschaulicht, wie der Projektdienst verwendet wird, um in einer einfachen Erweiterung des Projektelements **Listendefinition** eine Meldung in das Fenster **Ausgabe** und das Fenster **Fehlerliste** zu schreiben.  
  
     [!code-csharp[SPExtensibility.ProjectService.FromProjectSystemExtensions#2](../snippets/csharp/VS_Snippets_OfficeSP/spextensibility.projectservice.fromprojectsystemextensions/cs/extension/extension.cs#2)]
     [!code-vb[SPExtensibility.ProjectService.FromProjectSystemExtensions#2](../snippets/visualbasic/VS_Snippets_OfficeSP/spextensibility.projectservice.fromprojectsystemextensions/vb/extension/extension.vb#2)]  
  
     Weitere Informationen zum Erstellen von Projektelementerweiterungen finden Sie unter [How to: Create a SharePoint Project Item Extension](../sharepoint/how-to-create-a-sharepoint-project-item-extension.md).  
  
#### So rufen Sie den Dienst in einer Projektelementtypdefinition ab  
  
1.  Suchen Sie in Ihrer Implementierung der <xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectItemTypeProvider>\-Schnittstelle die <xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectItemTypeProvider.InitializeType%2A>\-Methode.  
  
2.  Verwenden Sie die <xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectItemTypeDefinition.ProjectService%2A>\-Eigenschaft des *typeDefinition*\-Parameters, um den Dienst abzurufen.  
  
     Im folgenden Codebeispiel wird veranschaulicht, wie der Projektdienst verwendet wird, um in einer einfachen Projektelementtypdefinition eine Meldung in das Fenster **Ausgabe** und das Fenster **Fehlerliste** zu schreiben.  
  
     [!code-csharp[SPExtensibility.ProjectService.FromProjectSystemExtensions#3](../snippets/csharp/VS_Snippets_OfficeSP/spextensibility.projectservice.fromprojectsystemextensions/cs/extension/extension.cs#3)]
     [!code-vb[SPExtensibility.ProjectService.FromProjectSystemExtensions#3](../snippets/visualbasic/VS_Snippets_OfficeSP/spextensibility.projectservice.fromprojectsystemextensions/vb/extension/extension.vb#3)]  
  
     Weitere Informationen über das Definieren von Projektelementtypen, finden Sie unter [How to: Define a SharePoint Project Item Type](../sharepoint/how-to-define-a-sharepoint-project-item-type.md).  
  
## Abrufen des Diensts in Server\-Explorer\-Erweiterungen  
 In einer Erweiterung des Knotens **SharePoint\-Verbindungen** in **Server\-Explorer** können Sie mit der <xref:Microsoft.VisualStudio.SharePoint.Explorer.IExplorerNode.ServiceProvider%2A>\-Eigenschaft eines <xref:Microsoft.VisualStudio.SharePoint.Explorer.IExplorerNode>\-Objekts auf den Projektdienst zugreifen.  
  
#### So rufen Sie den Dienst in einer Server\-Explorer\-Erweiterung ab  
  
1.  Rufen Sie das <xref:System.IServiceProvider>\-Objekt der <xref:Microsoft.VisualStudio.SharePoint.Explorer.IExplorerNode.ServiceProvider%2A>\-Eigenschaft eines <xref:Microsoft.VisualStudio.SharePoint.Explorer.IExplorerNode>\-Objekts in Ihrer Erweiterung ab.  
  
2.  Verwenden Sie die <xref:System.IServiceProvider.GetService%2A>\-Methode, um ein <xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectService>\-Projekt anzufordern.  
  
     Im folgenden Codebeispiel wird veranschaulicht, wie der Projektdienst verwendet wird, um eine Meldung in die Fenster **Ausgabe** und **Fehlerliste** eines Kontextmenüs zu schreiben, das die Erweiterung in **Server\-Explorer** Listenknoten hinzufügt.  
  
     [!code-csharp[SPExtensibility.ProjectService.FromSPExplorerExtensions#1](../snippets/csharp/VS_Snippets_OfficeSP/spextensibility.projectservice.fromspexplorerextensions/cs/extension/extension.cs#1)]
     [!code-vb[SPExtensibility.ProjectService.FromSPExplorerExtensions#1](../snippets/visualbasic/VS_Snippets_OfficeSP/spextensibility.projectservice.fromspexplorerextensions/vb/extension/extension.vb#1)]  
  
     Weitere Informationen zum Erweitern des Knotens **SharePoint\-Verbindungen** in **Server\-Explorer** finden Sie unter [How to: Extend a SharePoint Node in Server Explorer](../sharepoint/how-to-extend-a-sharepoint-node-in-server-explorer.md).  
  
## Abrufen des Diensts in anderen Visual Studio\-Erweiterungen  
 Sie können den Projektdienst in einem VSPackage oder in einer beliebigen anderen Visual Studio\-Erweiterung abrufen, die über Zugriff auf ein <xref:EnvDTE80.DTE2>\-Objekt im Automatisierungsobjektmodell verfügt, z. B. ein Add\-In oder ein Projektvorlagen\-Assistent, der die <xref:Microsoft.VisualStudio.TemplateWizard.IWizard>\-Schnittstelle implementiert.  
  
 In einem VSPackage können Sie mit einer der folgenden Methoden ein <xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectService>\-Objekt anfordern:  
  
-   Die <xref:System.IServiceProvider.GetService%2A>\-Methode eines verwalteten VSPackages, das sich von der <xref:Microsoft.VisualStudio.Shell.Package>\-Klasse ableitet.  Weitere Informationen finden Sie unter [Gewusst wie: Abrufen eines Diensts](../Topic/How%20to:%20Get%20a%20Service.md).  
  
-   Die statische <xref:Microsoft.VisualStudio.Shell.Package.GetGlobalService%2A>\-Methode.  Weitere Informationen finden Sie unter [Gewusst wie: Verwenden von GetGlobalService](../Topic/How%20to:%20Use%20GetGlobalService.md).  
  
 In einer Visual Studio\-Erweiterung mit Zugriff auf ein <xref:EnvDTE80.DTE2>\-Objekt können Sie ein <xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectService>\-Objekt anfordern, indem Sie die <xref:Microsoft.VisualStudio.Shell.ServiceProvider.GetService%2A>\-Methode eines <xref:Microsoft.VisualStudio.Shell.ServiceProvider>\-Objekts verwenden.  Weitere Informationen finden Sie unter [Gewusst wie: Abrufen eines Diensts vom DTE-Objekt](../Topic/How%20to:%20Get%20a%20Service%20from%20the%20DTE%20Object.md).  
  
### Beispiel  
 Im folgenden Codebeispiel wird veranschaulicht, wie der Projektdienst in einem Visual Studio\-Add\-In abgerufen wird.  Wenn Sie diesen Code verwenden möchten, führen Sie ihn von der `Connect`\-Klasse in einem Add\-In\-Projekt aus.  Das `_applicationObject`\-Objekt wird automatisch in Add\-In\-Projekte generiert. Dieses Objekt ist eine Instanz der <xref:EnvDTE80.DTE2>\-Schnittstelle.  
  
 [!code-csharp[SPExtensibility.ProjectService.FromDTE#1](../snippets/csharp/VS_Snippets_OfficeSP/spextensibility.projectservice.fromdte/cs/connect.cs#1)]
 [!code-vb[SPExtensibility.ProjectService.FromDTE#1](../snippets/visualbasic/VS_Snippets_OfficeSP/spextensibility.projectservice.fromdte/vb/connect.vb#1)]  
  
 Dieses Beispiel setzt Folgendes voraus:  
  
-   Ein Visual Studio\-Add\-In\-Projekt.  Weitere Informationen finden Sie unter [Gewusst wie: Erstellen von Add-Ins](../Topic/How%20to:%20Create%20an%20Add-In.md).  
  
-   Verweise auf die Assemblys Microsoft.VisualStudio.OLE.Interop, Microsoft.VisualStudio.Shell und Microsoft.VisualStudio.SharePoint.  
  
## Siehe auch  
 [Using the SharePoint Project Service](../sharepoint/using-the-sharepoint-project-service.md)   
 [Gewusst wie: Erstellen von Add-Ins](../Topic/How%20to:%20Create%20an%20Add-In.md)   
 [Gewusst wie: Abrufen eines Diensts](../Topic/How%20to:%20Get%20a%20Service.md)   
 [Gewusst wie: Abrufen eines Diensts vom DTE-Objekt](../Topic/How%20to:%20Get%20a%20Service%20from%20the%20DTE%20Object.md)   
 [Gewusst wie: Verwenden von Assistenten mit Projektvorlagen](../Topic/How%20to:%20Use%20Wizards%20with%20Project%20Templates.md)  
  
  