---
title: 'Vorgehensweise: Führen Code beim Bereitstellungsschritten | Microsoft-Dokumentation'
ms.date: 02/02/2017
ms.topic: conceptual
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- SharePoint development in Visual Studio, extending deployment
author: TerryGLee
ms.author: tglee
manager: douge
ms.workload:
- office
ms.openlocfilehash: 62ab9019eb9722baca523aeff00b4ed511039497
ms.sourcegitcommit: 37fb7075b0a65d2add3b137a5230767aa3266c74
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 01/02/2019
ms.locfileid: "53883255"
---
# <a name="how-to-run-code-when-deployment-steps-are-executed"></a>Vorgehensweise: Ausführen von Code bei der Bereitstellung ausgeführt werden
  Wenn Sie zusätzliche Aufgaben für einen Schritt der Bereitstellung in einer SharePoint-Projekt ausführen möchten, können Sie Ereignisse behandeln, die ausgelöst werden, von SharePoint-Projektelemente vor und nach der Visual Studio jeden Schritt der Bereitstellung ausgeführt wird. Weitere Informationen finden Sie unter [Erweitern von SharePoint-Packen und-Bereitstellen](../sharepoint/extending-sharepoint-packaging-and-deployment.md).  
  
### <a name="to-run-code-when-deployment-steps-are-executed"></a>Um Code auszuführen, wenn Bereitstellungsschritte ausgeführt werden  
  
1.  Erstellen Sie eine projektelementerweiterung, ein projekterweiterung oder einen neuen Projektelementtyp eine Definition. Weitere Informationen finden Sie unter den folgenden Themen:  
  
    -   [Vorgehensweise: Erstellen einer SharePoint-projektelementerweiterung](../sharepoint/how-to-create-a-sharepoint-project-item-extension.md)  
  
    -   [Vorgehensweise: Erstellen einer SharePoint-projekterweiterung](../sharepoint/how-to-create-a-sharepoint-project-extension.md)  
  
    -   [Vorgehensweise: Definieren Sie einen SharePoint-Projektelementtyp](../sharepoint/how-to-define-a-sharepoint-project-item-type.md)  
  
2.  In der Erweiterung verarbeiten die <xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectItemEvents.DeploymentStepStarted> und <xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectItemEvents.DeploymentStepCompleted> Ereignisse eine <xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectItemType> Objekt (in einem projektelementerweiterung oder projekterweiterung) oder ein <xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectItemTypeDefinition> Objekt (in einer Definition von einer neuen Projektelementtyp).  
  
3.  In den Ereignisdaten Ereignishandlern, verwendet der <xref:Microsoft.VisualStudio.SharePoint.DeploymentStepStartedEventArgs> und <xref:Microsoft.VisualStudio.SharePoint.DeploymentStepCompletedEventArgs> Parameter zum Abrufen von Informationen über den Bereitstellungsschritt. Sie können z. B. bestimmen, welche Bereitstellungsschritt ausgeführt wird, und gibt an, ob die Lösung wird bereitgestellt oder zurückgezogen.  
  
## <a name="example"></a>Beispiel  
 Im folgenden Codebeispiel wird veranschaulicht, wie behandelt die <xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectItemEvents.DeploymentStepStarted> und <xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectItemEvents.DeploymentStepCompleted> Ereignisse in einer Erweiterung für das Projektelement Listeninstanz. Diese Erweiterung schreibt eine weitere Nachricht an die **Ausgabe** Wartungszeitfensters, in Visual Studio der Anwendungspool wiederverwendet wird, beim Bereitstellen oder Zurückziehen der Lösung.  
  
 [!code-vb[SPExtensibility.ProjectSystemExtension.General#4](../sharepoint/codesnippet/VisualBasic/projectsystemexamples/extension/handledeploymentstepevents.vb#4)]
 [!code-csharp[SPExtensibility.ProjectSystemExtension.General#4](../sharepoint/codesnippet/CSharp/projectsystemexamples/extension/handledeploymentstepevents.cs#4)]  
  
## <a name="compile-the-code"></a>Kompilieren des Codes  
 Dieses Beispiel erfordert Verweise auf die folgenden Assemblys:  
  
-   Microsoft.VisualStudio.SharePoint  
  
-   System.ComponentModel.Composition  
  
## <a name="deploy-the-extension"></a>Bereitstellen der Erweiterung  
 Erstellen Sie zum Bereitstellen der Erweiterungs eine [!include[vsprvs](../sharepoint/includes/vsprvs-md.md)] -Erweiterung (VSIX) Verpacken, für die Assembly und alle anderen Dateien, die Sie mit der Erweiterung verteilen möchten. Weitere Informationen finden Sie unter [Bereitstellen von Erweiterungen für SharePoint-Tools in Visual Studio](../sharepoint/deploying-extensions-for-the-sharepoint-tools-in-visual-studio.md).  
  
## <a name="see-also"></a>Siehe auch
 [Erweitern von SharePoint-Packen und-bereitstellen](../sharepoint/extending-sharepoint-packaging-and-deployment.md)   
 [Exemplarische Vorgehensweise: Erstellen eines benutzerdefinierten Bereitstellungsschritts für SharePoint-Projekte](../sharepoint/walkthrough-creating-a-custom-deployment-step-for-sharepoint-projects.md)   
 [Vorgehensweise: Ausführen von Code beim Bereitstellen oder Zurückziehen ein SharePoint-Projekts](../sharepoint/how-to-run-code-when-a-sharepoint-project-is-deployed-or-retracted.md)  
