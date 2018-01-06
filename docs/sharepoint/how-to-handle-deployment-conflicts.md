---
title: 'Vorgehensweise: Behandeln von Bereitstellungskonflikten | Microsoft Docs'
ms.custom: 
ms.date: 02/02/2017
ms.reviewer: 
ms.suite: 
ms.technology: office-development
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords: SharePoint development in Visual Studio, extending deployment
ms.assetid: 8e545873-3fed-46cf-a95f-27b5fc0d5f83
caps.latest.revision: "14"
author: gewarren
ms.author: gewarren
manager: ghogen
ms.workload: office
ms.openlocfilehash: c908262a0ff74bb8574fd76f788611165934375b
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 12/22/2017
---
# <a name="how-to-handle-deployment-conflicts"></a>Gewusst wie: Behandeln von Bereitstellungskonflikten
  Sie können Ihren eigenen Code zum Behandeln von Bereitstellungskonflikten für ein SharePoint-Projektelement bereitstellen. Beispielsweise können Sie bestimmen, ob alle Dateien im aktuellen Projektelement bereits in den Speicherort für die Bereitstellung vorhanden sein, und klicken Sie dann den bereitgestellten Dateien löschen, bevor das aktuelle Projektelement bereitgestellt wird. Weitere Informationen zu Bereitstellungskonflikte, finden Sie unter [Erweitern von SharePoint-Packen und-Bereitstellen](../sharepoint/extending-sharepoint-packaging-and-deployment.md).  
  
### <a name="to-handle-a-deployment-conflict"></a>Um einen Bereitstellungskonflikt zu behandeln.  
  
1.  Erstellen Sie eine projektelementerweiterung, ein projekterweiterung oder einen neuen Projektelementtyp eine Definition. Weitere Informationen finden Sie unter den folgenden Themen:  
  
    -   [Vorgehensweise: Erstellen einer SharePoint-Projektelementerweiterung](../sharepoint/how-to-create-a-sharepoint-project-item-extension.md)  
  
    -   [Vorgehensweise: Erstellen einer SharePoint-Projekterweiterung](../sharepoint/how-to-create-a-sharepoint-project-extension.md)  
  
    -   [Vorgehensweise: Definieren eines SharePoint-Projektelementtyps](../sharepoint/how-to-define-a-sharepoint-project-item-type.md)  
  
2.  In der Erweiterung verarbeiten die <xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectItemEvents.DeploymentStepStarted> -Ereignis für ein <xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectItemType> Objekt (in einem projektelementerweiterung oder die projekterweiterung) oder ein <xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectItemTypeDefinition> Objekt (in eine Definition einer neuen Projektelementtyp).  
  
3.  In der Ereignishandler bestimmt, ob ein Konflikt zwischen dem Projektelement, das bereitgestellt wird und die bereitgestellte Projektmappe auf der SharePoint-Website auf Basis von Kriterien, die für Ihr Szenario gelten. Sie können die <xref:Microsoft.VisualStudio.SharePoint.SharePointProjectItemEventArgs.ProjectItem%2A> -Eigenschaft des Parameters für Ereignisargumente des Projektelements zu analysieren, das bereitgestellt wird, und Sie können die Dateien an den Bereitstellungsspeicherort analysieren, indem Aufrufen eines SharePoint-Befehls, die für diesen Zweck definiert.  
  
     Für viele Typen von Konflikten zuerst empfiehlt um zu bestimmen, welche Bereitstellungsschritt ausgeführt wird. Sie erreichen dies, indem die <xref:Microsoft.VisualStudio.SharePoint.DeploymentStepStartedEventArgs.DeploymentStepInfo%2A> Eigenschaft des Parameters für die Ereignisargumente. Obwohl es in der Regel zum Erkennen von Konflikten bei der integrierten sinnvoll <xref:Microsoft.VisualStudio.SharePoint.Deployment.DeploymentStepIds.AddSolution> Bereitstellungsschritt, sehen Sie sich für Konflikte während eines beliebigen Bereitstellungsschritts.  
  
4.  Verwenden, wenn ein Konflikt vorhanden ist, die <xref:Microsoft.VisualStudio.SharePoint.Deployment.IDeploymentConflictCollection.Add%2A> Methode der <xref:Microsoft.VisualStudio.SharePoint.DeploymentStepStartedEventArgs.Conflicts%2A> -Eigenschaft der Ereignisargumente zum Erstellen eines neuen <xref:Microsoft.VisualStudio.SharePoint.Deployment.IDeploymentConflict> Objekt. Dieses Objekt stellt den Bereitstellungskonflikt dar. Der Aufruf der <xref:Microsoft.VisualStudio.SharePoint.Deployment.IDeploymentConflictCollection.Add%2A> -Methode, geben Sie auch die Methode, die aufgerufen wird, um den Konflikt zu lösen.  
  
## <a name="example"></a>Beispiel  
 Im folgenden Codebeispiel wird veranschaulicht, der grundlegende Prozess für die Behandlung eines Konflikts Bereitstellung in einer projektelementerweiterung für die Definition Projektelemente. Um einen Bereitstellungskonflikt für einen anderen Typ des Projektelements zu behandeln, übergeben Sie eine andere Zeichenfolge an die <xref:Microsoft.VisualStudio.SharePoint.SharePointProjectItemTypeAttribute>. Weitere Informationen finden Sie unter [Erweitern von SharePoint-Projektelemente](../sharepoint/extending-sharepoint-project-items.md).  
  
 Aus Gründen der Einfachheit der <xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectItemEvents.DeploymentStepStarted> -Ereignishandler in diesem Beispiel wird davon ausgegangen, dass ein Bereitstellungskonflikt vorhanden ist (d. h. es immer Fügt eine neue <xref:Microsoft.VisualStudio.SharePoint.Deployment.IDeploymentConflict> Objekt), und die `Resolve` Methodenrückgabe einfach **"true"** gibt an, dass der Konflikt wurde gelöst. In einem realen Szenario Ihre <xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectItemEvents.DeploymentStepStarted> Ereignishandler zuerst fest, ob ein Konflikt zwischen einer Datei im aktuellen Projektelement und eine Datei auf den Speicherort für die Bereitstellung vorhanden ist, und fügen Sie dann ein <xref:Microsoft.VisualStudio.SharePoint.Deployment.IDeploymentConflict> Objekt nur, wenn ein Konflikt vorhanden ist. Sie können z. B. Verwenden der `e.ProjectItem.Files` Eigenschaft im Ereignishandler zum Analysieren von Dateien in das Projektelement, und Sie möglicherweise analysieren Sie die Dateien auf den Speicherort für die Bereitstellung ein SharePoint-Befehls aufrufen. Auf ähnliche Weise, in einem realen Szenario die `Resolve` Methode möglicherweise einen SharePoint-Befehl aus, um die konfliktlösung auf SharePoint-Website aufrufen. Weitere Informationen zum Erstellen von SharePoint-Befehlen finden Sie unter [Vorgehensweise: Erstellen eines SharePoint-Befehls](../sharepoint/how-to-create-a-sharepoint-command.md).  
  
 [!code-vb[SPExtensibility.ProjectItemExtension.DeploymentConflict#1](../sharepoint/codesnippet/VisualBasic/deploymentconflict/extension/deploymentconflictextension.vb#1)]
 [!code-csharp[SPExtensibility.ProjectItemExtension.DeploymentConflict#1](../sharepoint/codesnippet/CSharp/deploymentconflict/extension/deploymentconflictextension.cs#1)]  
  
## <a name="compiling-the-code"></a>Kompilieren des Codes  
 Dieses Beispiel erfordert Verweise auf die folgenden Assemblys:  
  
-   Microsoft.VisualStudio.SharePoint  
  
-   System.ComponentModel.Composition  
  
## <a name="deploying-the-extension"></a>Bereitstellen der Erweiterung  
 Zum Bereitstellen der Erweiterung erstellen Sie eine [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] -Erweiterung (VSIX) Verpacken, für die Assembly und alle anderen Dateien, die Sie mit der Erweiterung verteilen möchten. Weitere Informationen finden Sie unter [Bereitstellen von Erweiterungen für SharePoint-Tools in Visual Studio](../sharepoint/deploying-extensions-for-the-sharepoint-tools-in-visual-studio.md).  
  
## <a name="see-also"></a>Siehe auch  
 [Erweitern von SharePoint-Packen und-bereitstellen](../sharepoint/extending-sharepoint-packaging-and-deployment.md)   
 [Erweitern von SharePoint-Projektelementen](../sharepoint/extending-sharepoint-project-items.md)   
 [Vorgehensweise: Ausführen Code beim von Bereitstellungsschritten](../sharepoint/how-to-run-code-when-deployment-steps-are-executed.md)   
 [Vorgehensweise: Erstellen eines SharePoint-Befehls](../sharepoint/how-to-create-a-sharepoint-command.md)  
  
  