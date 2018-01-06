---
title: "Vorgehensweise: Ausführen Code beim Bereitstellungsschritten | Microsoft Docs"
ms.custom: 
ms.date: 02/02/2017
ms.reviewer: 
ms.suite: 
ms.technology: office-development
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- VB
- CSharp
helpviewer_keywords: SharePoint development in Visual Studio, extending deployment
ms.assetid: 6b0a52e5-e0ba-41bc-9e8a-1013e51fd3ba
caps.latest.revision: "21"
author: gewarren
ms.author: gewarren
manager: ghogen
ms.workload: office
ms.openlocfilehash: a147b9f6def49565334004bda1f8c4c80b0e7bfa
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 12/22/2017
---
# <a name="how-to-run-code-when-deployment-steps-are-executed"></a>Gewusst wie: Ausführen von Code bei der Ausführung von Bereitstellungsschritten
  Wenn Sie zusätzliche Aufgaben für einen Schritt der Bereitstellung in einer SharePoint-Projekt ausführen möchten, können Sie Ereignisse behandeln, die von SharePoint-Projektelemente vor und nach der Ausführung jedes Bereitstellungsschritts durch Visual Studio ausgelöst werden. Weitere Informationen finden Sie unter [Erweitern von SharePoint-Packen und-Bereitstellen](../sharepoint/extending-sharepoint-packaging-and-deployment.md).  
  
### <a name="to-run-code-when-deployment-steps-are-executed"></a>Um Code auszuführen, wenn Bereitstellungsschritte ausgeführt werden  
  
1.  Erstellen Sie eine projektelementerweiterung, ein projekterweiterung oder einen neuen Projektelementtyp eine Definition. Weitere Informationen finden Sie unter den folgenden Themen:  
  
    -   [Vorgehensweise: Erstellen einer SharePoint-Projektelementerweiterung](../sharepoint/how-to-create-a-sharepoint-project-item-extension.md)  
  
    -   [Vorgehensweise: Erstellen einer SharePoint-Projekterweiterung](../sharepoint/how-to-create-a-sharepoint-project-extension.md)  
  
    -   [Vorgehensweise: Definieren eines SharePoint-Projektelementtyps](../sharepoint/how-to-define-a-sharepoint-project-item-type.md)  
  
2.  In der Erweiterung verarbeiten die <xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectItemEvents.DeploymentStepStarted> und <xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectItemEvents.DeploymentStepCompleted> Ereignisse ein <xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectItemType> Objekt (in einem projektelementerweiterung oder die projekterweiterung) oder ein <xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectItemTypeDefinition> Objekt (in eine Definition einer neuen Projektelementtyp).  
  
3.  Verwenden Sie im Ereignis-Handler die <xref:Microsoft.VisualStudio.SharePoint.DeploymentStepStartedEventArgs> und <xref:Microsoft.VisualStudio.SharePoint.DeploymentStepCompletedEventArgs> Parameter zum Abrufen von Informationen zu den Bereitstellungsschritt. Beispielsweise können Sie bestimmen, welche Bereitstellungsschritt ausgeführt wird, und gibt an, ob die Projektmappe wird bereitgestellt oder zurückgezogen.  
  
## <a name="example"></a>Beispiel  
 Im folgenden Codebeispiel wird veranschaulicht, wie behandelt die <xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectItemEvents.DeploymentStepStarted> und <xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectItemEvents.DeploymentStepCompleted> Ereignisse in einer Erweiterung für das Projektelement Listeninstanz. Diese Erweiterung schreibt eine weitere Nachricht an die **Ausgabe** Fenster, wenn Visual Studio der Anwendungspool wiederverwendet wird, beim Bereitstellen oder Zurückziehen der Lösung.  
  
 [!code-vb[SPExtensibility.ProjectSystemExtension.General#4](../sharepoint/codesnippet/VisualBasic/projectsystemexamples/extension/handledeploymentstepevents.vb#4)]
 [!code-csharp[SPExtensibility.ProjectSystemExtension.General#4](../sharepoint/codesnippet/CSharp/projectsystemexamples/extension/handledeploymentstepevents.cs#4)]  
  
## <a name="compiling-the-code"></a>Kompilieren des Codes  
 Dieses Beispiel erfordert Verweise auf die folgenden Assemblys:  
  
-   Microsoft.VisualStudio.SharePoint  
  
-   System.ComponentModel.Composition  
  
## <a name="deploying-the-extension"></a>Bereitstellen der Erweiterung  
 Zum Bereitstellen der Erweiterung erstellen Sie eine [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] -Erweiterung (VSIX) Verpacken, für die Assembly und alle anderen Dateien, die Sie mit der Erweiterung verteilen möchten. Weitere Informationen finden Sie unter [Bereitstellen von Erweiterungen für SharePoint-Tools in Visual Studio](../sharepoint/deploying-extensions-for-the-sharepoint-tools-in-visual-studio.md).  
  
## <a name="see-also"></a>Siehe auch  
 [Erweitern von SharePoint-Packen und-bereitstellen](../sharepoint/extending-sharepoint-packaging-and-deployment.md)   
 [Exemplarische Vorgehensweise: Erstellen eines benutzerdefinierten Bereitstellungsschritts für SharePoint-Projekte](../sharepoint/walkthrough-creating-a-custom-deployment-step-for-sharepoint-projects.md)   
 [Vorgehensweise: Ausführen von Code beim Bereitstellen oder Zurückziehen eines SharePoint-Projekts](../sharepoint/how-to-run-code-when-a-sharepoint-project-is-deployed-or-retracted.md)  
  
  