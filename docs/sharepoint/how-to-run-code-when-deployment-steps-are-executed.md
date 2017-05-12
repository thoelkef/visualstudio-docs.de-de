---
title: "How to: Run Code When Deployment Steps are Executed"
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
  - "SharePoint development in Visual Studio, extending deployment"
ms.assetid: 6b0a52e5-e0ba-41bc-9e8a-1013e51fd3ba
caps.latest.revision: 21
author: "kempb"
ms.author: "kempb"
manager: "ghogen"
caps.handback.revision: 20
---
# How to: Run Code When Deployment Steps are Executed
  Wenn Sie zusätzliche Aufgaben für einen Bereitstellungsschritt in einem SharePoint\-Projekt ausführen möchten, können Sie Ereignisse behandeln, die von den SharePoint\-Projektelementen vor und nach der Ausführung jedes Bereitstellungsschritts durch Visual Studio ausgelöst werden.  Weitere Informationen finden Sie unter [Extending SharePoint Packaging and Deployment](../sharepoint/extending-sharepoint-packaging-and-deployment.md).  
  
### So führen Sie Code bei der Ausführung von Bereitstellungsschritten aus  
  
1.  Erstellen Sie eine Projektelementerweiterung, eine Projekterweiterung oder eine Definition eines neuen Projektelementtyps.  Weitere Informationen finden Sie unter den folgenden Themen:  
  
    -   [How to: Create a SharePoint Project Item Extension](../sharepoint/how-to-create-a-sharepoint-project-item-extension.md)  
  
    -   [How to: Create a SharePoint Project Extension](../sharepoint/how-to-create-a-sharepoint-project-extension.md)  
  
    -   [How to: Define a SharePoint Project Item Type](../sharepoint/how-to-define-a-sharepoint-project-item-type.md)  
  
2.  Behandeln Sie in der Erweiterung das <xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectItemEvents.DeploymentStepStarted>\- und <xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectItemEvents.DeploymentStepCompleted>\-Ereignis eines <xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectItemType>\-Objekts \(in einer Projektelementerweiterung oder Projekterweiterung\) oder eines <xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectItemTypeDefinition>\-Objekts \(in einer Definition eines neuen Projektelementtyps\).  
  
3.  Verwenden Sie in den Ereignishandlern den <xref:Microsoft.VisualStudio.SharePoint.DeploymentStepStartedEventArgs>\-Parameter und den <xref:Microsoft.VisualStudio.SharePoint.DeploymentStepCompletedEventArgs>\-Parameter, um Informationen zum Bereitstellungsschritt abzurufen.  Sie können z. B. ermitteln, welcher Bereitstellungsschritt ausgeführt wird und ob die Projektmappe bereitgestellt oder zurückgenommen wird.  
  
## Beispiel  
 Im folgenden Codebeispiel wird veranschaulicht, wie das <xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectItemEvents.DeploymentStepStarted>\-Ereignis und das <xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectItemEvents.DeploymentStepCompleted>\-Ereignis in einer Erweiterung für das Listeninstanzprojektelement behandelt werden.  Diese Erweiterung zeigt eine zusätzliche Meldung im Fenster **Ausgabe** an, wenn Visual Studio den Anwendungspool beim Bereitstellen oder Zurücknehmen der Projektmappe wiederverwendet.  
  
 [!code-csharp[SPExtensibility.ProjectSystemExtension.General#4](../snippets/csharp/VS_Snippets_OfficeSP/spextensibility.projectsystemextension.general/cs/extension/handledeploymentstepevents.cs#4)]
 [!code-vb[SPExtensibility.ProjectSystemExtension.General#4](../snippets/visualbasic/VS_Snippets_OfficeSP/spextensibility.projectsystemextension.general/vb/extension/handledeploymentstepevents.vb#4)]  
  
## Kompilieren des Codes  
 Für dieses Beispiel sind Verweise auf die folgenden Assemblys erforderlich:  
  
-   Microsoft.VisualStudio.SharePoint  
  
-   System.ComponentModel.Composition  
  
## Bereitstellen der Erweiterung  
 Erstellen Sie ein [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)]\-Erweiterungspaket \(VSIX\) für die Assembly und alle weiteren Dateien, die Sie mit der Erweiterung verteilen möchten, um die Erweiterung bereitzustellen.  Weitere Informationen erhalten Sie unter [Deploying Extensions for the SharePoint Tools in Visual Studio](../sharepoint/deploying-extensions-for-the-sharepoint-tools-in-visual-studio.md).  
  
## Siehe auch  
 [Extending SharePoint Packaging and Deployment](../sharepoint/extending-sharepoint-packaging-and-deployment.md)   
 [Walkthrough: Creating a Custom Deployment Step for SharePoint Projects](../sharepoint/walkthrough-creating-a-custom-deployment-step-for-sharepoint-projects.md)   
 [How to: Run Code When a SharePoint Project is Deployed or Retracted](../sharepoint/how-to-run-code-when-a-sharepoint-project-is-deployed-or-retracted.md)  
  
  