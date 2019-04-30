---
title: 'Vorgehensweise: Führen Code bei einer SharePoint-Projekt ist, bereitstellen oder Zurückziehen | Microsoft-Dokumentation'
ms.date: 02/02/2017
ms.topic: conceptual
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- SharePoint development in Visual Studio, extending deployment
author: John-Hart
ms.author: johnhart
manager: jillfra
ms.workload:
- office
ms.openlocfilehash: 4aadc089fba5c1f55488c72bfd5c3e46ebf59487
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/23/2019
ms.locfileid: "62813471"
---
# <a name="how-to-run-code-when-a-sharepoint-project-is-deployed-or-retracted"></a>Vorgehensweise: Ausführen von Code beim Bereitstellen oder Zurückziehen ein SharePoint-Projekts
  Wenn Sie beim Bereitstellen oder Zurückziehen ein SharePoint-Projekts weitere Aufgaben ausführen möchten, können Sie Ereignisse behandeln, die von Visual Studio ausgelöst werden. Weitere Informationen finden Sie unter [Erweitern von SharePoint-Packen und-Bereitstellen](../sharepoint/extending-sharepoint-packaging-and-deployment.md).

### <a name="to-run-code-when-a-sharepoint-project-is-deployed-or-retracted"></a>Zum Ausführen von Code, wenn ein SharePoint-Projekt bereitstellen oder Zurückziehen

1. Erstellen Sie eine projektelementerweiterung, ein projekterweiterung oder einen neuen Projektelementtyp eine Definition. Weitere Informationen finden Sie unter den folgenden Themen:

   - [Vorgehensweise: Erstellen einer SharePoint-projektelementerweiterung](../sharepoint/how-to-create-a-sharepoint-project-item-extension.md)

   - [Vorgehensweise: Erstellen einer SharePoint-projekterweiterung](../sharepoint/how-to-create-a-sharepoint-project-extension.md)

   - [Vorgehensweise: Definieren Sie einen SharePoint-Projektelementtyp](../sharepoint/how-to-define-a-sharepoint-project-item-type.md)

2. In der Erweiterung, Zugriff auf die <xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectService> Objekt. Weitere Informationen finden Sie unter [Vorgehensweise: Abrufen des SharePoint-Projektdiensts](../sharepoint/how-to-retrieve-the-sharepoint-project-service.md).

3. Behandeln der <xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectEvents.DeploymentStarted> und <xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectEvents.DeploymentCompleted> Ereignisse des Projektdiensts.

4. In den Ereignisdaten Ereignishandlern, verwendet der <xref:Microsoft.VisualStudio.SharePoint.DeploymentEventArgs> Parameter, um Informationen zu der aktuellen bereitstellungssitzung. Sie können beispielsweise bestimmen, welches Projekt in der aktuellen bereitstellungssitzung und gibt an, ob es gerade bereitgestellt oder zurückgezogen.

   Im folgenden Codebeispiel wird veranschaulicht, wie behandelt die <xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectEvents.DeploymentStarted> und <xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectEvents.DeploymentCompleted> Ereignisse in einer projekterweiterung. Diese Erweiterung schreibt eine weitere Nachricht an die **Ausgabe** anzeigen, wenn die Bereitstellung gestartet oder beendet werden, für eine SharePoint-Projekt.

   [!code-csharp[SPExtensibility.ProjectSystemExtension.General#12](../sharepoint/codesnippet/CSharp/projectsystemexamples/extension/handleprojectdeploymentevents.cs#12)]
   [!code-vb[SPExtensibility.ProjectSystemExtension.General#12](../sharepoint/codesnippet/VisualBasic/projectsystemexamples/extension/handleprojectdeploymentevents.vb#12)]

## <a name="compile-the-code"></a>Kompilieren des Codes
 Dieses Beispiel erfordert Verweise auf die folgenden Assemblys:

- Microsoft.VisualStudio.SharePoint

- System.ComponentModel.Composition

## <a name="deploy-the-extension"></a>Bereitstellen der Erweiterung
 Erstellen Sie zum Bereitstellen der Erweiterungs eine [!include[vsprvs](../sharepoint/includes/vsprvs-md.md)] -Erweiterung (VSIX) Verpacken, für die Assembly und alle anderen Dateien, die Sie mit der Erweiterung verteilen möchten. Weitere Informationen finden Sie unter [Bereitstellen von Erweiterungen für SharePoint-Tools in Visual Studio](../sharepoint/deploying-extensions-for-the-sharepoint-tools-in-visual-studio.md).

## <a name="see-also"></a>Siehe auch
- [Erweitern von SharePoint-Packen und-bereitstellen](../sharepoint/extending-sharepoint-packaging-and-deployment.md)
- [Vorgehensweise: Ausführen von Code bei der Bereitstellung ausgeführt werden](../sharepoint/how-to-run-code-when-deployment-steps-are-executed.md)
