---
title: Konvertieren zwischen SharePoint-Projektsystemtypen und anderen Visual Studio-Projekttypen | Microsoft-Dokumentation
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
ms.openlocfilehash: c5010a4cfba970f63cfa887f4c3be943cbdde731
ms.sourcegitcommit: e6b13898cfbd89449f786c2e8f3e3e7377afcf25
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 06/22/2018
ms.locfileid: "36326178"
---
# <a name="convert-between-sharepoint-project-system-types-and-other-visual-studio-project-types"></a>Konvertieren Sie zwischen SharePoint-Projektsystemtypen und anderen Visual Studio-Projekttypen
  In einigen Fällen können Sie ein Objekt sein, in SharePoint-Projektsystem und gewünschten Features eines entsprechenden Objekts in der Visual Studio-Automatisierungsobjektmodell oder-Integrationsobjektmodell und umgekehrt. In diesen Fällen können Sie die <xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectService.Convert%2A> -Methode der SharePoint-Projektdiensts auf das Objekt in ein anderes Objektmodell konvertieren.

 Angenommen, Sie haben eine <xref:Microsoft.VisualStudio.SharePoint.ISharePointProject> -Objekt, aber Sie Methoden verwenden, die nur auf zur Verfügung stehen soll ein <xref:EnvDTE.Project> oder <xref:Microsoft.VisualStudio.Shell.Interop.IVsProject> Objekt. In diesem Fall können Sie die <xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectService.Convert%2A> Methode zum Konvertieren der <xref:Microsoft.VisualStudio.SharePoint.ISharePointProject> auf eine <xref:EnvDTE.Project> oder <xref:Microsoft.VisualStudio.Shell.Interop.IVsProject>.

 Weitere Informationen über das Automatisierungsobjektmodell von Visual Studio und das Visual Studio-Integrationsobjektmodell finden Sie unter [Übersicht über das Programmiermodell von SharePoint-tools Extensions](../sharepoint/overview-of-the-programming-model-of-sharepoint-tools-extensions.md).

## <a name="types-of-conversions"></a>Typen von Konvertierungen
 Die folgende Tabelle enthält die Typen, die diese Methode zwischen SharePoint-Projektsystem und die andere Visual Studio-Objektmodelle konvertieren kann.

|Systemtyp für SharePoint-Projekt|Entsprechenden Typen in den Objektmodellen Automatisierungs- und integrationsobjektmodelle|
|------------------------------------|-------------------------------------------------------------------------|
|<xref:Microsoft.VisualStudio.SharePoint.ISharePointProject>|<xref:EnvDTE.Project><br /><br /> oder<br /><br /> Einer beliebigen Schnittstelle in das Visual Studio-Integrationsobjektmodell, das vom zugrunde liegenden COM-Objekt für das Projekt implementiert wird. Diese Schnittstellen umfassen <xref:Microsoft.VisualStudio.Shell.Interop.IVsHierarchy>, <xref:Microsoft.VisualStudio.Shell.Interop.IVsProject> (oder eine abgeleitete Schnittstelle) und <xref:Microsoft.VisualStudio.Shell.Interop.IVsBuildPropertyStorage>. Eine Liste der wichtigsten Schnittstellen, die von Projekten implementiert werden, finden Sie unter [Hauptkomponenten eines Projektmodells](../extensibility/internals/project-model-core-components.md).|
|<xref:Microsoft.VisualStudio.SharePoint.IMappedFolder><br /><br /> <xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectItem><br /><br /> <xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectItemFile><br /><br /> <xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectFeature><br /><br /> <xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectFeatureResourceFile><br /><br /> <xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectPackage>|<xref:EnvDTE.ProjectItem><br /><br /> oder<br /><br /> Ein<xref:System.UInt32> Wert (auch als eine VSITEMID bezeichnet) ab, das Projektmitglied in identifiziert, die <xref:Microsoft.VisualStudio.Shell.Interop.IVsHierarchy> , die Sie enthält. Dieser Wert kann an übergeben werden die *Itemid* Parameter einiger <xref:Microsoft.VisualStudio.Shell.Interop.IVsHierarchy> Methoden.|

## <a name="example"></a>Beispiel
 Im folgenden Codebeispiel wird veranschaulicht, wie Sie mit der <xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectService.Convert%2A> Methode zum Konvertieren einer <xref:Microsoft.VisualStudio.SharePoint.ISharePointProject> -Objekt an eine <xref:EnvDTE.Project>.

 [!code-csharp[SPExtensibility.ProjectService.FromDTE#2](../sharepoint/codesnippet/CSharp/spprojectserviceaddin/connect.cs#2)]
 [!code-vb[SPExtensibility.ProjectService.FromDTE#2](../sharepoint/codesnippet/VisualBasic/spprojectserviceaddin/connect.vb#2)]

 Für dieses Beispiel benötigen Sie Folgendes:

-   Eine Erweiterung der SharePoint-Projektsystem, die einen Verweis auf die *EnvDTE.dll* Assembly. Weitere Informationen finden Sie unter [Erweitern der SharePoint-Projektsystem](../sharepoint/extending-the-sharepoint-project-system.md).

-   Code, der registriert die `projectService_ProjectAdded` Methode zum Behandeln der <xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectEvents.ProjectAdded> Ereignis eine <xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectService> Objekt. Ein Beispiel finden Sie unter [Vorgehensweise: Erstellen einer SharePoint-projekterweiterung](../sharepoint/how-to-create-a-sharepoint-project-extension.md).

## <a name="see-also"></a>Siehe auch

- [Verwenden Sie die SharePoint-Projektdiensts](../sharepoint/using-the-sharepoint-project-service.md)
- [Gewusst wie: Abrufen des SharePoint-Projektdiensts](../sharepoint/how-to-retrieve-the-sharepoint-project-service.md)
- [Übersicht über das Programmiermodell von SharePoint-tools extensions](../sharepoint/overview-of-the-programming-model-of-sharepoint-tools-extensions.md)

