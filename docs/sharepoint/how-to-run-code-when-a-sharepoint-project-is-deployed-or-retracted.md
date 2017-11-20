---
title: "Vorgehensweise: Ausführen Code When a SharePoint Project ist bereitstellen oder Zurückziehen | Microsoft Docs"
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
ms.assetid: 353bbe6d-9b76-48ad-9fba-7e3c3712452f
caps.latest.revision: "5"
author: gewarren
ms.author: gewarren
manager: ghogen
ms.openlocfilehash: 0650bfdb7961728fed34147c05f6333d8255e373
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 10/31/2017
---
# <a name="how-to-run-code-when-a-sharepoint-project-is-deployed-or-retracted"></a>Gewusst wie: Ausführen von Code beim Bereitstellen oder Zurückziehen eines SharePoint-Projekts
  Wenn Sie zusätzliche Aufgaben ausführen, wenn ein SharePoint-Projekt bereitstellen oder zurückziehen möchten, können Sie Ereignisse behandeln, die von Visual Studio ausgelöst werden. Weitere Informationen finden Sie unter [Erweitern von SharePoint-Packen und-Bereitstellen](../sharepoint/extending-sharepoint-packaging-and-deployment.md).  
  
### <a name="to-run-code-when-a-sharepoint-project-is-deployed-or-retracted"></a>Zum Ausführen von Code, wenn ein SharePoint-Projekt bereitstellen oder Zurückziehen  
  
1.  Erstellen Sie eine projektelementerweiterung, ein projekterweiterung oder einen neuen Projektelementtyp eine Definition. Weitere Informationen finden Sie unter den folgenden Themen:  
  
    -   [Vorgehensweise: Erstellen einer SharePoint-Projektelementerweiterung](../sharepoint/how-to-create-a-sharepoint-project-item-extension.md)  
  
    -   [Vorgehensweise: Erstellen einer SharePoint-Projekterweiterung](../sharepoint/how-to-create-a-sharepoint-project-extension.md)  
  
    -   [Vorgehensweise: Definieren eines SharePoint-Projektelementtyps](../sharepoint/how-to-define-a-sharepoint-project-item-type.md)  
  
2.  In der Erweiterung Zugriff auf die <xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectService> Objekt. Weitere Informationen finden Sie unter [wie: Abrufen des SharePoint-Projektdiensts](../sharepoint/how-to-retrieve-the-sharepoint-project-service.md).  
  
3.  Behandeln der <xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectEvents.DeploymentStarted> und <xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectEvents.DeploymentCompleted> Ereignisse des Projektdiensts.  
  
4.  Verwenden Sie im Ereignis-Handler die <xref:Microsoft.VisualStudio.SharePoint.DeploymentEventArgs> Parameter, um Informationen über die aktuelle Bereitstellung Sitzung abzurufen. Beispielsweise können Sie bestimmen, welches Projekt in der aktuellen Sitzung für die Bereitstellung wird und gibt an, ob es gerade bereitgestellt oder zurückgezogen.  
  
 Im folgenden Codebeispiel wird veranschaulicht, wie behandelt die <xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectEvents.DeploymentStarted> und <xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectEvents.DeploymentCompleted> Ereignisse in einer projekterweiterung. Diese Erweiterung schreibt eine weitere Nachricht an die **Ausgabe** Fenster bei der Bereitstellung beginnt und für eine SharePoint-Projekt abgeschlossen ist.  
  
 [!code-csharp[SPExtensibility.ProjectSystemExtension.General#12](../sharepoint/codesnippet/CSharp/projectsystemexamples/extension/handleprojectdeploymentevents.cs#12)]
 [!code-vb[SPExtensibility.ProjectSystemExtension.General#12](../sharepoint/codesnippet/VisualBasic/projectsystemexamples/extension/handleprojectdeploymentevents.vb#12)]  
  
## <a name="compiling-the-code"></a>Kompilieren des Codes  
 Dieses Beispiel erfordert Verweise auf die folgenden Assemblys:  
  
-   Microsoft.VisualStudio.SharePoint  
  
-   System.ComponentModel.Composition  
  
## <a name="deploying-the-extension"></a>Bereitstellen der Erweiterung  
 Zum Bereitstellen der Erweiterung erstellen Sie eine [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] -Erweiterung (VSIX) Verpacken, für die Assembly und alle anderen Dateien, die Sie mit der Erweiterung verteilen möchten. Weitere Informationen finden Sie unter [Bereitstellen von Erweiterungen für SharePoint-Tools in Visual Studio](../sharepoint/deploying-extensions-for-the-sharepoint-tools-in-visual-studio.md).  
  
## <a name="see-also"></a>Siehe auch  
 [Erweitern von SharePoint-Packen und-bereitstellen](../sharepoint/extending-sharepoint-packaging-and-deployment.md)   
 [Vorgehensweise: Ausführen von Code bei der Ausführung von Bereitstellungsschritten](../sharepoint/how-to-run-code-when-deployment-steps-are-executed.md)  
  
  