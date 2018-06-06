---
title: Konvertieren zwischen SharePoint-Projektsystemtypen und anderen Visual Studio-Projekttypen | Microsoft Docs
ms.custom: ''
ms.date: 02/02/2017
ms.technology:
- office-development
ms.topic: conceptual
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- SharePoint project service
author: TerryGLee
ms.author: tglee
manager: douge
ms.workload:
- office
ms.openlocfilehash: 64de38fe796ce3c1e0d333a22582ad2973e1c4d2
ms.sourcegitcommit: 4cd4aef53e7035d23e7d1d0f66f51ac8480622a1
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 06/05/2018
ms.locfileid: "34765358"
---
# <a name="convert-between-sharepoint-project-system-types-and-other-visual-studio-project-types"></a>Konvertieren Sie zwischen SharePoint-Projektsystemtypen und anderen Visual Studio-Projekttypen
  In einigen Fällen möglicherweise Sie ein Objekt in der SharePoint-Projektsystem und Funktionen in ein entsprechendes Objekt in der Visual Studio-Automatisierungsobjektmodell oder-Integrationsobjektmodell verwendet werden sollen oder umgekehrt. In diesen Fällen können Sie die <xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectService.Convert%2A> Methode von der SharePoint-Projektdienst, das Objekt in ein anderes Objektmodell zu konvertieren.  
  
 Angenommen, Sie haben eine <xref:Microsoft.VisualStudio.SharePoint.ISharePointProject> Methoden verwenden, die nur auf verfügbaren-Objekt, aber Sie möchten eine <xref:EnvDTE.Project> oder <xref:Microsoft.VisualStudio.Shell.Interop.IVsProject> Objekt. In diesem Fall können Sie die <xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectService.Convert%2A> -Methode zum Konvertieren der <xref:Microsoft.VisualStudio.SharePoint.ISharePointProject> auf eine <xref:EnvDTE.Project> oder <xref:Microsoft.VisualStudio.Shell.Interop.IVsProject>.  
  
 Weitere Informationen über das Automatisierungsobjektmodell von Visual Studio und Visual Studio-Integrationsobjektmodell finden Sie unter [Überblick über die Programmierung Modell der SharePoint-Tools-Erweiterungen](../sharepoint/overview-of-the-programming-model-of-sharepoint-tools-extensions.md).  
  
## <a name="types-of-conversions"></a>Typen von Konvertierungen
 Die folgende Tabelle enthält die Typen, die diese Methode zwischen SharePoint-Projektsystem und anderen Visual Studio-Objektmodellen konvertiert werden kann.  
  
|Systemtyp für SharePoint-Projekt|Entsprechenden Typen in den Objektmodellen Integration und Automatisierung|  
|------------------------------------|-------------------------------------------------------------------------|  
|<xref:Microsoft.VisualStudio.SharePoint.ISharePointProject>|<xref:EnvDTE.Project><br /><br /> oder<br /><br /> Eine beliebige Schnittstelle in der Visual Studio-Integrationsobjektmodell, das vom zugrunde liegenden COM-Objekt für das Projekt implementiert wird. Zu diesen Schnittstellen gehören <xref:Microsoft.VisualStudio.Shell.Interop.IVsHierarchy>, <xref:Microsoft.VisualStudio.Shell.Interop.IVsProject> (oder eine abgeleitete Schnittstelle) und <xref:Microsoft.VisualStudio.Shell.Interop.IVsBuildPropertyStorage>. Eine Liste der wichtigsten Schnittstellen, die von Projekten implementiert werden, finden Sie unter [Projekt Modell Kernkomponenten](/visualstudio/extensibility/internals/project-model-core-components).|  
|<xref:Microsoft.VisualStudio.SharePoint.IMappedFolder><br /><br /> <xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectItem><br /><br /> <xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectItemFile><br /><br /> <xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectFeature><br /><br /> <xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectFeatureResourceFile><br /><br /> <xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectPackage>|<xref:EnvDTE.ProjectItem><br /><br /> oder<br /><br /> Ein<xref:System.UInt32> Wert (auch als ein VSITEMID bezeichnet), die in das Project-Element identifiziert den <xref:Microsoft.VisualStudio.Shell.Interop.IVsHierarchy> , die Sie enthält. Dieser Wert kann übergeben werden, um die *Itemid* Parameter einiger <xref:Microsoft.VisualStudio.Shell.Interop.IVsHierarchy> Methoden.|  
  
## <a name="example"></a>Beispiel  
 Im folgenden Codebeispiel wird veranschaulicht, wie die <xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectService.Convert%2A> -Methode zum Konvertieren einer <xref:Microsoft.VisualStudio.SharePoint.ISharePointProject> -Objekt an eine <xref:EnvDTE.Project>.  
  
 [!code-csharp[SPExtensibility.ProjectService.FromDTE#2](../sharepoint/codesnippet/CSharp/spprojectserviceaddin/connect.cs#2)]
 [!code-vb[SPExtensibility.ProjectService.FromDTE#2](../sharepoint/codesnippet/VisualBasic/spprojectserviceaddin/connect.vb#2)]  
  
 Für dieses Beispiel benötigen Sie Folgendes:  
  
-   Eine Erweiterung der SharePoint-Projektsystem, die einen Verweis auf die *EnvDTE.dll* Assembly. Weitere Informationen finden Sie unter [Erweitern des SharePoint-Projektsystems](../sharepoint/extending-the-sharepoint-project-system.md).  
  
-   Code, der registriert die `projectService_ProjectAdded` Methode zum Behandeln der <xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectEvents.ProjectAdded> -Ereignis für ein <xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectService> Objekt. Ein Beispiel finden Sie unter [Vorgehensweise: Erstellen einer SharePoint-Projekterweiterung](../sharepoint/how-to-create-a-sharepoint-project-extension.md).  
  
## <a name="see-also"></a>Siehe auch
 [Verwenden des SharePoint-Projektdiensts](../sharepoint/using-the-sharepoint-project-service.md)   
 [Vorgehensweise: Abrufen des SharePoint-Projektdiensts](../sharepoint/how-to-retrieve-the-sharepoint-project-service.md)   
 [Übersicht über das Programmiermodell von Erweiterungen für SharePoint-Tools](../sharepoint/overview-of-the-programming-model-of-sharepoint-tools-extensions.md)  
  
