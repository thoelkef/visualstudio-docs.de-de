---
title: "How to: Handle Deployment Conflicts"
ms.custom: ""
ms.date: "02/02/2017"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "office-development"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "SharePoint development in Visual Studio, extending deployment"
ms.assetid: 8e545873-3fed-46cf-a95f-27b5fc0d5f83
caps.latest.revision: 14
author: "kempb"
ms.author: "kempb"
manager: "ghogen"
caps.handback.revision: 13
---
# How to: Handle Deployment Conflicts
  Sie können eigenen Code angeben, um Bereitstellungskonflikte für SharePoint\-Projektelemente zu behandeln.  Beispielsweise können Sie ermitteln, ob Dateien im aktuellen Projektelement am Bereitstellungsspeicherort bereits vorhanden sind und die bereitgestellten Dateien löschen, bevor das aktuelle Projektelement bereitgestellt wird.  Weitere Informationen zu Bereitstellungskonflikten finden Sie unter [Extending SharePoint Packaging and Deployment](../sharepoint/extending-sharepoint-packaging-and-deployment.md).  
  
### So behandeln Sie ein Bereitstellungskonflikt  
  
1.  Erstellen Sie eine Projektelementerweiterung, eine Projekterweiterung oder eine Definition eines neuen Projektelementtyps.  Weitere Informationen finden Sie unter den folgenden Themen:  
  
    -   [How to: Create a SharePoint Project Item Extension](../sharepoint/how-to-create-a-sharepoint-project-item-extension.md)  
  
    -   [How to: Create a SharePoint Project Extension](../sharepoint/how-to-create-a-sharepoint-project-extension.md)  
  
    -   [How to: Define a SharePoint Project Item Type](../sharepoint/how-to-define-a-sharepoint-project-item-type.md)  
  
2.  Behandeln Sie in der Erweiterung das <xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectItemEvents.DeploymentStepStarted>\-Ereignis eines <xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectItemType>\-Objekts \(in einer Projektelementerweiterung oder einer Projekterweiterung oder eines <xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectItemTypeDefinition>\-Objekts \(in der Definition eines neuen Projektelementtyps\).  
  
3.  Ermitteln Sie im Ereignishandler, ob ein Konflikt zwischen dem Projektelement, das bereitgestellt wird, und der Projektmappe, die auf der SharePoint\-Website bereitgestellt wurde, besteht, und verwenden Sie dazu die Kriterien für Ihr Szenario.  Mit der <xref:Microsoft.VisualStudio.SharePoint.SharePointProjectItemEventArgs.ProjectItem%2A>\-Eigenschaft des Parameters für Ereignisargumente können Sie das Projektelement analysieren, das bereitgestellt wird, und Sie können die Dateien am Bereitstellungsspeicherort analysieren, indem Sie einen SharePoint\-Befehl aufrufen, den Sie zu diesem Zweck definieren.  
  
     Bei vielen Konflikten ist es empfehlenswert, zunächst zu ermitteln, welcher Bereitstellungsschritt ausgeführt wird.  Sie können dazu die <xref:Microsoft.VisualStudio.SharePoint.DeploymentStepStartedEventArgs.DeploymentStepInfo%2A>\-Eigenschaft des Parameters für Ereignisargumente verwenden.  Typischerweise werden Konflikte im Rahmen des integrierten <xref:Microsoft.VisualStudio.SharePoint.Deployment.DeploymentStepIds.AddSolution>\-Bereitstellungsschritts identifiziert. Grundsätzlich können Sie jedoch in allen Bereitstellungsschritten eine Prüfung auf Konflikte durchführen.  
  
4.  Wenn ein Konflikt vorhanden ist, können Sie mit der <xref:Microsoft.VisualStudio.SharePoint.Deployment.IDeploymentConflictCollection.Add%2A>\-Methode für die <xref:Microsoft.VisualStudio.SharePoint.DeploymentStepStartedEventArgs.Conflicts%2A>\-Eigenschaft der Ereignisargumente ein neues <xref:Microsoft.VisualStudio.SharePoint.Deployment.IDeploymentConflict>\-Objekt erstellen.  Dieses Objekt stellt den Bereitstellungskonflikt dar.  Geben Sie im Aufruf der <xref:Microsoft.VisualStudio.SharePoint.Deployment.IDeploymentConflictCollection.Add%2A>\-Methode außerdem die Methode an, die aufgerufen wird, um den Konflikt zu lösen.  
  
## Beispiel  
 Im folgenden Codebeispiel wird der grundlegende Prozess zur Behandlung eines Bereitstellungskonflikts in einer Projektelementerweiterung für die Projektelemente einer Listendefinition veranschaulicht.  Um einen Bereitstellungskonflikt für einen anderen Projektelementtyp zu behandeln, übergeben Sie eine andere Zeichenfolge an das <xref:Microsoft.VisualStudio.SharePoint.SharePointProjectItemTypeAttribute>.  Weitere Informationen finden Sie unter [Extending SharePoint Project Items](../sharepoint/extending-sharepoint-project-items.md).  
  
 Der Einfachheit halber geht der <xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectItemEvents.DeploymentStepStarted>\-Ereignishandler in diesem Beispiel davon aus, dass ein Bereitstellungskonflikt vorhanden ist \(d. h., es wird immer ein neues <xref:Microsoft.VisualStudio.SharePoint.Deployment.IDeploymentConflict>\-Objekt hinzugefügt\), und von der `Resolve`\-Methode wird einfach **true** zurückgegeben, um anzugeben, dass ein Konflikt gelöst wurde.  In einem realen Szenario würde vom <xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectItemEvents.DeploymentStepStarted>\-Ereignishandler zunächst geprüft, ob ein Konflikt zwischen einer Datei in dem aktuellen Projektelement und einer Datei am Bereitstellungsspeicherort besteht, und ein <xref:Microsoft.VisualStudio.SharePoint.Deployment.IDeploymentConflict>\-Objekt würde im Anschluss nur hinzugefügt, wenn tatsächlich ein Konflikt vorliegt.  Beispielsweise können Sie mit der `e.ProjectItem.Files`\-Eigenschaft im Ereignishandler die Dateien im Projektelement analysieren, und durch Aufrufen eines SharePoint\-Befehls können Sie die Dateien am Bereitstellungsspeicherort analysieren.  Analog zu einem realen Szenario würde von der `Resolve`\-Methode ein SharePoint\-Befehl aufgerufen, um den Konflikt auf der SharePoint\-Website zu lösen.  Weitere Informationen zum Erstellen von SharePoint\-Befehlen finden Sie unter [How to: Create a SharePoint Command](../sharepoint/how-to-create-a-sharepoint-command.md).  
  
 [!code-csharp[SPExtensibility.ProjectItemExtension.DeploymentConflict#1](../snippets/csharp/VS_Snippets_OfficeSP/spextensibility.projectitemextension.deploymentconflict/cs/extension/deploymentconflictextension.cs#1)]
 [!code-vb[SPExtensibility.ProjectItemExtension.DeploymentConflict#1](../snippets/visualbasic/VS_Snippets_OfficeSP/spextensibility.projectitemextension.deploymentconflict/vb/extension/deploymentconflictextension.vb#1)]  
  
## Kompilieren des Codes  
 Für dieses Beispiel sind Verweise auf die folgenden Assemblys erforderlich:  
  
-   Microsoft.VisualStudio.SharePoint  
  
-   System.ComponentModel.Composition  
  
## Bereitstellen der Erweiterung  
 Erstellen Sie ein [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)]\-Erweiterungspaket \(VSIX\) für die Assembly und alle weiteren Dateien, die Sie mit der Erweiterung verteilen möchten, um die Erweiterung bereitzustellen.  Weitere Informationen erhalten Sie unter [Deploying Extensions for the SharePoint Tools in Visual Studio](../sharepoint/deploying-extensions-for-the-sharepoint-tools-in-visual-studio.md).  
  
## Siehe auch  
 [Extending SharePoint Packaging and Deployment](../sharepoint/extending-sharepoint-packaging-and-deployment.md)   
 [Extending SharePoint Project Items](../sharepoint/extending-sharepoint-project-items.md)   
 [How to: Run Code When Deployment Steps are Executed](../sharepoint/how-to-run-code-when-deployment-steps-are-executed.md)   
 [How to: Create a SharePoint Command](../sharepoint/how-to-create-a-sharepoint-command.md)  
  
  