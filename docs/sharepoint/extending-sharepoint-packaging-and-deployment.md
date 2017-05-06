---
title: "Extending SharePoint Packaging and Deployment"
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
ms.assetid: 4789ebb2-12bc-42b9-9427-e63d77137765
caps.latest.revision: 19
author: "kempb"
ms.author: "kempb"
manager: "ghogen"
caps.handback.revision: 18
---
# Extending SharePoint Packaging and Deployment
  Sie können den Paketerstellungs\- und Bereitstellungsprozess für SharePoint\-Projekte erweitern.  
  
 [!INCLUDE[autoOutline](../Token/autoOutline_md.md)]  
  
##  <a name="creating_deployment_steps"></a> Erstellen von Bereitstellungsschritten  
 Wenn Sie ein SharePoint\-Projekt bereitstellen, führt [!INCLUDE[vs_current_short](../sharepoint/includes/vs-current-short-md.md)] eine Reihe von Schritten zur Bereitstellung aus.  Visual Studio umfasst integrierte Bereitstellungsschritte für viele Aufgaben wie das Zurückziehen und Hinzufügen von Projektmappen.  Sie können jedoch auch eigene Bereitstellungsschritte erstellen.  
  
 Eine exemplarische Vorgehensweise, in der das Erstellen eines Bereitstellungsschritts gezeigt wird, finden Sie unter [Walkthrough: Creating a Custom Deployment Step for SharePoint Projects](../sharepoint/walkthrough-creating-a-custom-deployment-step-for-sharepoint-projects.md).  
  
##  <a name="creating_deployment_configurations"></a> Erstellen von Bereitstellungskonfigurationen  
 Bei einer Bereitstellungskonfiguration handelt es sich um eine Reihe von Bereitstellungsschritten. Sie werden für ein angegebenes Projekt ausgeführt, können sich aber auf alle SharePoint\-Projektelemente auswirken.  Jede Bereitstellungskonfiguration umfasst einen Satz an Schritten, der beim Bereitstellen des Projekts ausgeführt wird, und einen anderen Satz, der ausgeführt wird, wenn das Projekt zurückgezogen wird.  [!INCLUDE[vs_current_short](../sharepoint/includes/vs-current-short-md.md)] umfasst zwei integrierte Bereitstellungskonfigurationen. Sie können jedoch auch Ihre eigene erstellen.  Beim Erstellen einer Bereitstellungskonfiguration können Sie integrierte und von Ihnen erstellte Bereitstellungsschritte einbeziehen.  
  
 Eine exemplarische Vorgehensweise, in der das Erstellen einer Bereitstellungskonfiguration gezeigt wird, finden Sie unter [Walkthrough: Creating a Custom Deployment Step for SharePoint Projects](../sharepoint/walkthrough-creating-a-custom-deployment-step-for-sharepoint-projects.md).  
  
##  <a name="run_code_before_and_after_each_deployment_step"></a> Ausführen von Code beim Bereitstellen oder Zurückziehen einer Projektmappe  
 Sie können Ereignisse verarbeiten, um zusätzliche Aufgaben auszuführen, wenn eine SharePoint\-Lösung bereitgestellt oder zurückgezogen wird.  Visual Studio löst Ereignisse aus, die Sie in den folgenden Szenarien behandeln können:  
  
-   Vor und nach der Ausführung jedes Bereitstellungsschritts für ein SharePoint\-Projektelement.  Weitere Informationen finden Sie unter [How to: Run Code When Deployment Steps are Executed](../sharepoint/how-to-run-code-when-deployment-steps-are-executed.md).  
  
-   Vor und nach der Bereitstellung oder Zurückziehung eines SharePoint\-Projekts.  Weitere Informationen finden Sie unter [How to: Run Code When a SharePoint Project is Deployed or Retracted](../sharepoint/how-to-run-code-when-a-sharepoint-project-is-deployed-or-retracted.md).  
  
##  <a name="deployment_conflicts"></a> Behandeln von Bereitstellungskonflikten  
 Einige SharePoint\-Projektelementtypen, einschließlich Module, Webparts, Listeninstanzen und Inhaltstypen, bieten eine integrierte Bereitstellungskonfliktlösung.  Beim Bereitstellen einer Lösung, die eins dieser Projektelemente enthält, prüft Visual Studio zunächst, ob eine Datei bereits auf der SharePoint\-Website mit demselben Namen, der URL oder ID wie die Datei im Element vorhanden ist, die Sie bereitstellen.  Wenn ein Konflikt vorhanden ist, kann Visual Studio den Konflikt automatisch lösen, alternativ kann es Sie auffordern zu bestimmen, ob Visual Studio den Konflikt beheben oder ob die Bereitstellung abgebrochen werden soll.  Weitere Informationen finden Sie unter [Problembehandlung beim SharePoint-Packen und -Bereitstellen](../sharepoint/troubleshooting-sharepoint-packaging-and-deployment.md).  
  
 Sie können dieses Feature erweitern, indem Sie Ihren eigenen Code bereitstellen, der nach Bereitstellungskonflikten sucht und diese behebt.  Weitere Informationen finden Sie unter [How to: Handle Deployment Conflicts](../sharepoint/how-to-handle-deployment-conflicts.md).  
  
##  <a name="run_command_line_operations_before_or_after_a_project_is_deployed"></a> Ausführen von Befehlszeilenvorgängen vor oder nach der Bereitstellung eines Projekts  
 Wenn Sie beim Bereitstellen einer SharePoint\-Lösung einen Befehlszeilenvorgang ausführen möchten, können Sie die Eigenschaften <xref:Microsoft.VisualStudio.SharePoint.ISharePointProject.PreDeploymentCommand%2A> und <xref:Microsoft.VisualStudio.SharePoint.ISharePointProject.PostDeploymentCommand%2A> eines <xref:Microsoft.VisualStudio.SharePoint.ISharePointProject>\-Objekts festlegen.  Visual Studio führt diese Befehle vor und nach der Bereitstellung des Projekts aus.  
  
 In einigen Fällen werden möglicherweise Bereitstellungskonflikte angezeigt.  Es gibt mehrere Möglichkeiten, Konflikte zu lösen.  Weitere Informationen finden Sie unter [Problembehandlung beim SharePoint-Packen und -Bereitstellen](../sharepoint/troubleshooting-sharepoint-packaging-and-deployment.md).  
  
##  <a name="customizing_validation_rules"></a> Anpassen von Validierungsregeln  
 Vor dem Bereitstellen eines Lösungspakets \(.wsp\) können Sie benutzerdefinierte Feature\- und Paketvalidierungsregeln erstellen, um sicherzustellen, dass das Feature oder Paket gültig ist.  Beispielsweise können Sie Entwicklern Informationen, Warnungen oder Fehler melden, um sie beim Beheben von Überprüfungsproblemen zu unterstützen.  Weitere Informationen finden Sie unter [How to: Create Custom Feature and Package Validation Rules for SharePoint Solutions](../sharepoint/how-to-create-custom-feature-and-package-validation-rules-for-sharepoint-solutions.md).  
  
## Siehe auch  
 [How to: Run Code When Deployment Steps are Executed](../sharepoint/how-to-run-code-when-deployment-steps-are-executed.md)   
 [Walkthrough: Creating a Custom Deployment Step for SharePoint Projects](../sharepoint/walkthrough-creating-a-custom-deployment-step-for-sharepoint-projects.md)   
 [How to: Create Custom Feature and Package Validation Rules for SharePoint Solutions](../sharepoint/how-to-create-custom-feature-and-package-validation-rules-for-sharepoint-solutions.md)   
 [Extending the SharePoint Project System](../sharepoint/extending-the-sharepoint-project-system.md)  
  
  