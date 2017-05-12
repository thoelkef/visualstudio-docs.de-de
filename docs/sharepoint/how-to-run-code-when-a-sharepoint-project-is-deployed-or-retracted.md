---
title: "How to: Run Code When a SharePoint Project is Deployed or Retracted"
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
ms.assetid: 353bbe6d-9b76-48ad-9fba-7e3c3712452f
caps.latest.revision: 5
author: "kempb"
ms.author: "kempb"
manager: "ghogen"
caps.handback.revision: 4
---
# How to: Run Code When a SharePoint Project is Deployed or Retracted
  Wenn Sie beim Bereitstellen oder Zurückziehen eines SharePoint\-Projekts zusätzliche Aufgaben ausführen möchten, können Sie von Visual Studio ausgelöste Ereignisse behandeln.  Weitere Informationen finden Sie unter [Extending SharePoint Packaging and Deployment](../sharepoint/extending-sharepoint-packaging-and-deployment.md).  
  
### So führen Sie Code beim Bereitstellen oder Zurückziehen eines SharePoint\-Projekts aus  
  
1.  Erstellen Sie eine Projektelementerweiterung, eine Projekterweiterung oder eine Definition eines neuen Projektelementtyps.  Weitere Informationen finden Sie unter den folgenden Themen:  
  
    -   [How to: Create a SharePoint Project Item Extension](../sharepoint/how-to-create-a-sharepoint-project-item-extension.md)  
  
    -   [How to: Create a SharePoint Project Extension](../sharepoint/how-to-create-a-sharepoint-project-extension.md)  
  
    -   [How to: Define a SharePoint Project Item Type](../sharepoint/how-to-define-a-sharepoint-project-item-type.md)  
  
2.  Greifen Sie in der Erweiterung auf das <xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectService>\-Objekt zu.  Weitere Informationen finden Sie unter [How to: Retrieve the SharePoint Project Service](../sharepoint/how-to-retrieve-the-sharepoint-project-service.md).  
  
3.  Behandeln Sie das <xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectEvents.DeploymentStarted>\-Ereignis und das <xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectEvents.DeploymentCompleted>\-Ereignis des Projektdiensts.  
  
4.  Rufen Sie in den Ereignishandlern mithilfe des <xref:Microsoft.VisualStudio.SharePoint.DeploymentEventArgs>\-Parameters Informationen zur aktuellen Bereitstellungssitzung ab.  So können Sie beispielsweise ermitteln, welches Projekt sich in der aktuellen Bereitstellungssitzung befindet und ob es bereitgestellt oder zurückgezogen wird.  
  
 Im folgenden Codebeispiel wird die Behandlung des <xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectEvents.DeploymentStarted>\-Ereignisses und des <xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectEvents.DeploymentCompleted>\-Ereignisses in einer Projekterweiterung veranschaulicht.  Von dieser Erweiterung wird bei Start und Fertigstellung der Bereitstellung für ein SharePoint\-Projekt eine zusätzliche Meldung in das Ausgabefenster geschrieben.  
  
 [!code-csharp[SPExtensibility.ProjectSystemExtension.General#12](../snippets/csharp/VS_Snippets_OfficeSP/spextensibility.projectsystemextension.general/cs/extension/handleprojectdeploymentevents.cs#12)]
 [!code-vb[SPExtensibility.ProjectSystemExtension.General#12](../snippets/visualbasic/VS_Snippets_OfficeSP/spextensibility.projectsystemextension.general/vb/extension/handleprojectdeploymentevents.vb#12)]  
  
## Kompilieren des Codes  
 Für dieses Beispiel sind Verweise auf die folgenden Assemblys erforderlich:  
  
-   Microsoft.VisualStudio.SharePoint  
  
-   System.ComponentModel.Composition  
  
## Bereitstellen der Erweiterung  
 Erstellen Sie ein [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)]\-Erweiterungspaket \(VSIX\) für die Assembly und alle weiteren Dateien, die Sie mit der Erweiterung verteilen möchten, um die Erweiterung bereitzustellen.  Weitere Informationen erhalten Sie unter [Deploying Extensions for the SharePoint Tools in Visual Studio](../sharepoint/deploying-extensions-for-the-sharepoint-tools-in-visual-studio.md).  
  
## Siehe auch  
 [Extending SharePoint Packaging and Deployment](../sharepoint/extending-sharepoint-packaging-and-deployment.md)   
 [How to: Run Code When Deployment Steps are Executed](../sharepoint/how-to-run-code-when-deployment-steps-are-executed.md)  
  
  