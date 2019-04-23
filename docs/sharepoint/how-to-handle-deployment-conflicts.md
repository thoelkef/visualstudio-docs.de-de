---
title: 'Vorgehensweise: Behandeln von Bereitstellungskonflikten | Microsoft-Dokumentation'
ms.date: 02/02/2017
ms.topic: conceptual
helpviewer_keywords:
- SharePoint development in Visual Studio, extending deployment
author: John-Hart
ms.author: johnhart
manager: jillfra
ms.workload:
- office
ms.openlocfilehash: 62e7740915d341eee1bbf5e112c4f09297c98be1
ms.sourcegitcommit: 1fc6ee928733e61a1f42782f832ead9f7946d00c
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/22/2019
ms.locfileid: "60066142"
---
# <a name="how-to-handle-deployment-conflicts"></a>Vorgehensweise: Behandeln von Bereitstellungskonflikten
  Sie können Ihren eigenen Code zum Behandeln von Bereitstellungskonflikten für ein SharePoint-Projektelement bereitstellen. Beispielsweise können Sie bestimmen, ob alle Dateien in das aktuelle Projektelement bereits in den Speicherort der Bereitstellung vorhanden sein, und klicken Sie dann die bereitgestellten Dateien löschen, bevor das aktuelle Projektelement bereitgestellt wird. Weitere Informationen zu Bereitstellungskonflikte, finden Sie unter [Erweitern von SharePoint-Packen und-Bereitstellen](../sharepoint/extending-sharepoint-packaging-and-deployment.md).

### <a name="to-handle-a-deployment-conflict"></a>Um einen Bereitstellungskonflikt zu behandeln.

1. Erstellen Sie eine projektelementerweiterung, ein projekterweiterung oder einen neuen Projektelementtyp eine Definition. Weitere Informationen finden Sie unter den folgenden Themen:

    - [Vorgehensweise: Erstellen einer SharePoint-projektelementerweiterung](../sharepoint/how-to-create-a-sharepoint-project-item-extension.md)

    - [Vorgehensweise: Erstellen einer SharePoint-projekterweiterung](../sharepoint/how-to-create-a-sharepoint-project-extension.md)

    - [Vorgehensweise: Definieren Sie einen SharePoint-Projektelementtyp](../sharepoint/how-to-define-a-sharepoint-project-item-type.md)

2. In der Erweiterung verarbeiten die <xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectItemEvents.DeploymentStepStarted> Ereignis eine <xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectItemType> Objekt (in einem projektelementerweiterung oder projekterweiterung) oder ein <xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectItemTypeDefinition> Objekt (in einer Definition von einer neuen Projektelementtyp).

3. Bestimmen Sie im Ereignishandler, ob es sich bei einem Konflikt zwischen dem Projektelement, das bereitgestellt wird und die bereitgestellte Projektmappe auf der SharePoint-Website, die basierend auf Kriterien, die für Ihr Szenario gelten. Sie können die <xref:Microsoft.VisualStudio.SharePoint.SharePointProjectItemEventArgs.ProjectItem%2A> -Eigenschaft des Parameters für Ereignisargumente des Projektelements zu analysieren, das bereitgestellt wird, und Sie können die Dateien auf den Speicherort für die Bereitstellung analysieren, durch den Aufruf eines SharePoint-Befehls, die Sie zu diesem Zweck definieren.

     Für viele Arten von Konflikten zunächst empfiehlt um zu bestimmen, welche Bereitstellungsschritt ausgeführt wird. Sie erreichen dies, indem die <xref:Microsoft.VisualStudio.SharePoint.DeploymentStepStartedEventArgs.DeploymentStepInfo%2A> Eigenschaft des Parameters für Ereignisargumente. Obwohl es in der Regel zum Erkennen von Konflikten bei der integrierten sinnvoll <xref:Microsoft.VisualStudio.SharePoint.Deployment.DeploymentStepIds.AddSolution> Bereitstellungsschritt, sehen Sie sich für Konflikte bei jedem Bereitstellungsschritt.

4. Wenn ein Konflikt vorhanden ist, verwenden Sie die <xref:Microsoft.VisualStudio.SharePoint.Deployment.IDeploymentConflictCollection.Add%2A> -Methode der der <xref:Microsoft.VisualStudio.SharePoint.DeploymentStepStartedEventArgs.Conflicts%2A> Eigenschaft der Ereignisargumente zum Erstellen eines neuen <xref:Microsoft.VisualStudio.SharePoint.Deployment.IDeploymentConflict> Objekt. Dieses Objekt stellt den Bereitstellungskonflikt dar. Der Aufruf der <xref:Microsoft.VisualStudio.SharePoint.Deployment.IDeploymentConflictCollection.Add%2A> -Methode, geben Sie auch die Methode, die aufgerufen wird, um den Konflikt zu lösen.

## <a name="example"></a>Beispiel
 Im folgenden Codebeispiel wird veranschaulicht, der grundlegende Prozess für die Behandlung von Umgebungskonflikts in einer projektelementerweiterung für die Definition Projektelemente. Um einen Bereitstellungskonflikt für einen anderen Typ des Projektelements zu behandeln, eine andere Zeichenfolge übergeben, die die <xref:Microsoft.VisualStudio.SharePoint.SharePointProjectItemTypeAttribute>. Weitere Informationen finden Sie unter [Erweitern von SharePoint-Projektelemente](../sharepoint/extending-sharepoint-project-items.md).

 Aus Gründen der Einfachheit der <xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectItemEvents.DeploymentStepStarted> -Ereignishandler in diesem Beispiel wird davon ausgegangen, dass ein Bereitstellungskonflikt vorhanden ist (d. h. es immer Fügt ein neues <xref:Microsoft.VisualStudio.SharePoint.Deployment.IDeploymentConflict> Objekt), und die `Resolve` -Methode einfach zurückgegeben **"true"** an, dass der Konflikt wurde gelöst. In einem realen Szenario Ihre <xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectItemEvents.DeploymentStepStarted> -Ereignishandler wird zuerst fest, ob ein Konflikt zwischen einer Datei in das aktuelle Projektelement und eine Datei am Speicherort Bereitstellung vorhanden ist, und fügen Sie eine <xref:Microsoft.VisualStudio.SharePoint.Deployment.IDeploymentConflict> -Objekt nur, wenn ein Konflikt vorhanden ist. Sie können z. B. Verwenden der `e.ProjectItem.Files` Eigenschaft im Ereignishandler zum Analysieren von Dateien in das Projektelement, und Sie können einen SharePoint-Befehl, um die Dateien auf den Speicherort für die Bereitstellung zu analysieren aufrufen. Auf ähnliche Weise, in einem realen Szenario der `Resolve` Methode kann einen SharePoint-Befehl zum Auflösen des Konflikts in der SharePoint-Website aufrufen. Weitere Informationen zum Erstellen von SharePoint-Befehle finden Sie unter [Vorgehensweise: Erstellen eines SharePoint-Befehls](../sharepoint/how-to-create-a-sharepoint-command.md).

 [!code-vb[SPExtensibility.ProjectItemExtension.DeploymentConflict#1](../sharepoint/codesnippet/VisualBasic/deploymentconflict/extension/deploymentconflictextension.vb#1)]
 [!code-csharp[SPExtensibility.ProjectItemExtension.DeploymentConflict#1](../sharepoint/codesnippet/CSharp/deploymentconflict/extension/deploymentconflictextension.cs#1)]

## <a name="compile-the-code"></a>Kompilieren des Codes
 Dieses Beispiel erfordert Verweise auf die folgenden Assemblys:

- Microsoft.VisualStudio.SharePoint

- System.ComponentModel.Composition

## <a name="deploy-the-extension"></a>Bereitstellen der Erweiterung
 Erstellen Sie zum Bereitstellen der Erweiterungs eine [!include[vsprvs](../sharepoint/includes/vsprvs-md.md)] -Erweiterung (VSIX) Verpacken, für die Assembly und alle anderen Dateien, die Sie mit der Erweiterung verteilen möchten. Weitere Informationen finden Sie unter [Bereitstellen von Erweiterungen für SharePoint-Tools in Visual Studio](../sharepoint/deploying-extensions-for-the-sharepoint-tools-in-visual-studio.md).

## <a name="see-also"></a>Siehe auch
- [Erweitern von SharePoint-Packen und-bereitstellen](../sharepoint/extending-sharepoint-packaging-and-deployment.md)
- [Erweitern von SharePoint-Projektelemente](../sharepoint/extending-sharepoint-project-items.md)
- [Vorgehensweise: Ausführen von Code bei der Bereitstellung ausgeführt werden](../sharepoint/how-to-run-code-when-deployment-steps-are-executed.md)
- [Vorgehensweise: Erstellen eines SharePoint-Befehls](../sharepoint/how-to-create-a-sharepoint-command.md)
