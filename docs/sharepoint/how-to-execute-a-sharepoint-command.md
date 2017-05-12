---
title: "How to: Execute a SharePoint Command"
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
  - "SharePoint commands [SharePoint development in Visual Studio], executing"
ms.assetid: 2d1a163b-b601-4dac-bcea-328f24cb4d57
caps.latest.revision: 23
author: "kempb"
ms.author: "kempb"
manager: "ghogen"
caps.handback.revision: 22
---
# How to: Execute a SharePoint Command
  Wenn Sie das Serverobjektmodell in einer SharePoint\-Tools\-Erweiterung verwenden möchten, müssen Sie einen benutzerdefinierten *SharePoint\-Befehl* erstellen, um die API aufzurufen.  Nach der Definition des Befehls und der Bereitstellung mit der SharePoint\-Tools\-Erweiterung kann der Befehl von der Erweiterung ausgeführt werden, um das SharePoint\-Serverobjektmodell aufzurufen.  Zum Ausführen des Befehls verwenden Sie eine der ExecuteCommand\-Methoden eines <xref:Microsoft.VisualStudio.SharePoint.ISharePointConnection>\-Objekts.  
  
 Weitere Informationen über den Zweck von SharePoint\-Befehlen finden Sie [Calling into the SharePoint Object Models](../sharepoint/calling-into-the-sharepoint-object-models.md).  
  
### So führen Sie einen SharePoint\-Befehl aus  
  
1.  Rufen Sie in der SharePoint\-Tools\-Erweiterung ein <xref:Microsoft.VisualStudio.SharePoint.ISharePointConnection>\-Objekt ab.  Das Vorgehensweise zum Abrufen eines <xref:Microsoft.VisualStudio.SharePoint.ISharePointConnection>\-Objekts ist abhängig vom Typ der Erweiterung, die Sie erstellen:  
  
    -   Verwenden Sie in einer Erweiterung des SharePoint\-Projektsystems die <xref:Microsoft.VisualStudio.SharePoint.ISharePointProject.SharePointConnection%2A>\-Eigenschaft.  
  
         Weitere Informationen zu Projektsystemerweiterungen finden Sie unter [Extending the SharePoint Project System](../sharepoint/extending-the-sharepoint-project-system.md).  
  
    -   Verwenden Sie in einer Erweiterung des Knotens **SharePoint\-Verbindungen** in **Server\-Explorer** die <xref:Microsoft.VisualStudio.SharePoint.Explorer.IExplorerNodeContext.SharePointConnection%2A>\-Eigenschaft.  Mit der <xref:Microsoft.VisualStudio.SharePoint.Explorer.IExplorerNode.Context%2A>\-Eigenschaft können Sie ein <xref:Microsoft.VisualStudio.SharePoint.Explorer.IExplorerNodeContext>\-Objekt abrufen.  
  
         Weitere Informationen zu **Server\-Explorer**\-Erweiterungen erhalten Sie unter [Extending the SharePoint Connections Node in Server Explorer](../sharepoint/extending-the-sharepoint-connections-node-in-server-explorer.md).  
  
    -   In einem Code, der nicht Teil einer Erweiterung der SharePoint\-Tools ist, z. B. in einem Projektvorlagen\-Assistenten, verwenden Sie die <xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectService.SharePointConnection%2A>\-Eigenschaft.  
  
         Weitere Informationen zum Abrufen des Projektdiensts finden Sie unter [Using the SharePoint Project Service](../sharepoint/using-the-sharepoint-project-service.md).  
  
2.  Rufen Sie eine der ExecuteCommand\-Methoden des <xref:Microsoft.VisualStudio.SharePoint.ISharePointConnection>\-Objekts auf.  Übergeben Sie die Bezeichnung des auszuführenden Befehls an das erste Argument der ExecuteCommand\-Methode.  Wenn der Befehl über einen benutzerdefinierten Parameter verfügt, übergeben Sie diesen Parameter an das zweite Argument der ExecuteCommand\-Methode.  
  
     Für jede unterstützte Befehlssignatur liegt eine andere ExecuteCommand\-Überladung vor.  In der folgenden Tabelle sind die unterstützten Signaturen und die Überladungen für jede Signatur aufgeführt.  
  
    |Befehlssignatur|Zu verwendende ExecuteCommand\-Überladung|  
    |---------------------|-----------------------------------------------|  
    |Der Befehl verfügt nur über den <xref:Microsoft.VisualStudio.SharePoint.Commands.ISharePointCommandContext>\-Standardparameter und keinen Rückgabewert.|<xref:Microsoft.VisualStudio.SharePoint.ISharePointConnection.ExecuteCommand%2A>|  
    |Der Befehl verfügt nur über den <xref:Microsoft.VisualStudio.SharePoint.Commands.ISharePointCommandContext>\-Standardparameter und einen Rückgabewert.|<xref:Microsoft.VisualStudio.SharePoint.ISharePointConnection.ExecuteCommand%2A>|  
    |Der Befehl verfügt über zwei Parameter \(den <xref:Microsoft.VisualStudio.SharePoint.Commands.ISharePointCommandContext>\-Standardparameter und einen benutzerdefinierten Parameter\) und keinen Rückgabewert.|<xref:Microsoft.VisualStudio.SharePoint.ISharePointConnection.ExecuteCommand%2A>|  
    |Der Befehl verfügt über zwei Parameter und einen Rückgabewert.|<xref:Microsoft.VisualStudio.SharePoint.ISharePointConnection.ExecuteCommand%2A>|  
  
## Beispiel  
 Im folgenden Codebeispiel wird veranschaulicht, wie die <xref:Microsoft.VisualStudio.SharePoint.ISharePointConnection.ExecuteCommand%2A>\-Überladung verwendet wird, um den bereits unter [How to: Create a SharePoint Command](../sharepoint/how-to-create-a-sharepoint-command.md) beschriebenen `Contoso.Commands.UpgradeSolution`\-Befehl aufzurufen.  
  
 [!code-csharp[SPExtensibility.ProjectExtension.UpgradeDeploymentStep#6](../snippets/csharp/VS_Snippets_OfficeSP/spextensibility.projectextension.upgradedeploymentstep/CS/deploymentstepextension/upgradestep.cs#6)]
 [!code-vb[SPExtensibility.ProjectExtension.UpgradeDeploymentStep#6](../snippets/visualbasic/VS_Snippets_OfficeSP/spextensibility.projectextension.upgradedeploymentstep/vb/deploymentstepextension/upgradestep.vb#6)]  
  
 Die in diesem Beispiel gezeigte `Execute`\-Methode ist eine Implementierung der <xref:Microsoft.VisualStudio.SharePoint.Deployment.IDeploymentStep.Execute%2A>\-Methode der <xref:Microsoft.VisualStudio.SharePoint.Deployment.IDeploymentStep>\-Schnittstelle in einem benutzerdefinierten Bereitstellungsschritt.  Unter [Walkthrough: Creating a Custom Deployment Step for SharePoint Projects](../sharepoint/walkthrough-creating-a-custom-deployment-step-for-sharepoint-projects.md) wird dieser Code noch einmal in einem umfassenderen Beispiel verwendet.  
  
 Beachten Sie die folgenden Details beim Aufrufen der <xref:Microsoft.VisualStudio.SharePoint.ISharePointConnection.ExecuteCommand%2A>\-Methode:  
  
-   Der erste Parameter identifiziert den Befehl, den Sie aufrufen möchten.  Diese Zeichenfolge stimmt mit dem Wert überein, den Sie in der Befehlsdefinition an <xref:Microsoft.VisualStudio.SharePoint.Commands.SharePointCommandAttribute> übergeben.  
  
-   Der zweite Parameter ist der Wert, den Sie an den benutzerdefinierten zweiten Parameter des Befehls übergeben möchten.  In diesem Fall ist dies der vollständige Pfad der WSP\-Datei, mit der die SharePoint\-Website aktualisiert wird.  
  
-   Im Code wird der implizite <xref:Microsoft.VisualStudio.SharePoint.Commands.ISharePointCommandContext>\-Parameter nicht an den Befehl übergeben.  Der Parameter wird automatisch an den Befehl übergeben, wenn Sie den Befehl von einer Erweiterung des SharePoint\-Projektsystems oder einer Erweiterung des Knotens **SharePoint\-Verbindungen** in **Server\-Explorer** aufrufen.  In anderen Lösungen, z. B. in einem Projektvorlagen\-Assistent, der die <xref:Microsoft.VisualStudio.TemplateWizard.IWizard>\-Schnittstelle implementiert, ist dieser Parameter **null**.  
  
## Kompilieren des Codes  
 Dieses Beispiel erfordert einen Verweis auf die Microsoft.VisualStudio.SharePoint\-Assembly.  
  
## Siehe auch  
 [Calling into the SharePoint Object Models](../sharepoint/calling-into-the-sharepoint-object-models.md)   
 [How to: Create a SharePoint Command](../sharepoint/how-to-create-a-sharepoint-command.md)   
 [Walkthrough: Extending Server Explorer to Display Web Parts](../sharepoint/walkthrough-extending-server-explorer-to-display-web-parts.md)  
  
  