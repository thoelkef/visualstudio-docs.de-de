---
title: 'Vorgehensweise: Abrufen des SharePoint-Projektdiensts | Microsoft-Dokumentation'
ms.date: 02/02/2017
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
ms.openlocfilehash: dfd18de91848c8aabbdabc91fd37763418bb938a
ms.sourcegitcommit: 37fb7075b0a65d2add3b137a5230767aa3266c74
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 01/02/2019
ms.locfileid: "53891601"
---
# <a name="how-to-retrieve-the-sharepoint-project-service"></a>Vorgehensweise: Abrufen des SharePoint-Projektdiensts
  Sie können SharePoint-Projektdiensts in der folgenden Typen von Projektmappen zugreifen:  
  
-   Eine Erweiterung von SharePoint-Projektsystem, z. B. eine projekterweiterung, projektelementerweiterung oder Projektelement-Typdefinition. Weitere Informationen zu diesen Erweiterungen finden Sie unter [Erweitern der SharePoint-Projektsystem](../sharepoint/extending-the-sharepoint-project-system.md).  
  
-   Eine Erweiterung von der **SharePoint-Verbindungen** Knoten **Server-Explorer**. Weitere Informationen zu diesen Erweiterungen finden Sie unter [Erweitern des SharePoint-Verbindungsknotens im Server-Explorer](../sharepoint/extending-the-sharepoint-connections-node-in-server-explorer.md).  
  
-   Eine andere Art von Visual Studio-Erweiterung, z. B. ein VSPackage.  
  
## <a name="retrieve-the-service-in-project-system-extensions"></a>Rufen Sie den Dienst im Project-System-Erweiterungen  
 In jeder Erweiterung der SharePoint-Projektsystem, können Sie den Projektdienst zugreifen, mithilfe der <xref:Microsoft.VisualStudio.SharePoint.ISharePointProject.ProjectService%2A> Eigenschaft eine <xref:Microsoft.VisualStudio.SharePoint.ISharePointProject> Objekt.  
  
 Sie können auch den Projektdienst abrufen, mithilfe der folgenden Verfahren.  
  
#### <a name="to-retrieve-the-service-in-a-project-extension"></a>Den Dienst in einer projekterweiterung abrufen  
  
1.  In der Implementierung von der <xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectExtension> Schnittstelle, suchen Sie nach der <xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectExtension.Initialize%2A> Methode.  
  
2.  Verwenden der *Anwendbarkeitsprüfungen* Parameter, um den Dienst zuzugreifen.  
  
     Im folgenden Codebeispiel wird veranschaulicht, wie Sie den Projektdienst verwenden, zum Schreiben einer Meldung, die **Ausgabe** Fenster und **Fehlerliste** Fenster in einer einfachen projekterweiterung.  
  
     [!code-vb[SPExtensibility.ProjectService.FromProjectSystemExtensions#1](../sharepoint/codesnippet/VisualBasic/spextensibility.projectservice.fromprojectsystemextensions.getprojectservice/extension/extension.vb#1)]
     [!code-csharp[SPExtensibility.ProjectService.FromProjectSystemExtensions#1](../sharepoint/codesnippet/CSharp/spextensibility.projectservice.fromprojectsystemextensions.getprojectservice/extension/extension.cs#1)]  
  
     Weitere Informationen zum Erstellen von Project-Erweiterungen finden Sie unter [Vorgehensweise: Erstellen einer SharePoint-projekterweiterung](../sharepoint/how-to-create-a-sharepoint-project-extension.md).  
  
#### <a name="to-retrieve-the-service-in-a-project-item-extension"></a>Um den Dienst in einer projektelementerweiterung abzurufen.  
  
1.  In der Implementierung von der <xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectItemTypeExtension> Schnittstelle, suchen Sie nach der <xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectItemTypeExtension.Initialize%2A> Methode.  
  
2.  Verwenden der <xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectItemType.ProjectService%2A> Eigenschaft der *ProjectItemType* Parameter, um den Dienst abzurufen.  
  
     Im folgenden Codebeispiel wird veranschaulicht, wie Sie den Projektdienst verwenden, zum Schreiben einer Meldung, die **Ausgabe** Fenster und **Fehlerliste** Fenster in einer einfachen Erweiterung von der **Listendefinition** Projektelement.  
  
     [!code-vb[SPExtensibility.ProjectService.FromProjectSystemExtensions#2](../sharepoint/codesnippet/VisualBasic/spextensibility.projectservice.fromprojectsystemextensions.getprojectservice/extension/extension.vb#2)]
     [!code-csharp[SPExtensibility.ProjectService.FromProjectSystemExtensions#2](../sharepoint/codesnippet/CSharp/spextensibility.projectservice.fromprojectsystemextensions.getprojectservice/extension/extension.cs#2)]  
  
     Weitere Informationen zum Erstellen von Project-Element-Erweiterungen finden Sie unter [Vorgehensweise: Erstellen eine SharePoint-projektelementerweiterung](../sharepoint/how-to-create-a-sharepoint-project-item-extension.md).  
  
#### <a name="to-retrieve-the-service-in-a-project-item-type-definition"></a>Zum Abrufen des Diensts in einem Projektelement-Typdefinition  
  
1.  In der Implementierung von der <xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectItemTypeProvider> Schnittstelle, suchen Sie nach der <xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectItemTypeProvider.InitializeType%2A> Methode.  
  
2.  Verwenden der <xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectItemTypeDefinition.ProjectService%2A> Eigenschaft der *TypeDefinition* Parameter, um den Dienst abzurufen.  
  
     Im folgenden Codebeispiel wird veranschaulicht, wie Sie den Projektdienst verwenden, zum Schreiben einer Meldung, die **Ausgabe** Fenster und **Fehlerliste** Fenster in einer einfachen Definition des Projektelementtyps.  
  
     [!code-vb[SPExtensibility.ProjectService.FromProjectSystemExtensions#3](../sharepoint/codesnippet/VisualBasic/spextensibility.projectservice.fromprojectsystemextensions.getprojectservice/extension/extension.vb#3)]
     [!code-csharp[SPExtensibility.ProjectService.FromProjectSystemExtensions#3](../sharepoint/codesnippet/CSharp/spextensibility.projectservice.fromprojectsystemextensions.getprojectservice/extension/extension.cs#3)]  
  
     Weitere Informationen zum Definieren von Projektelementtypen finden Sie unter [Vorgehensweise: Definieren Sie einen SharePoint-Projektelementtyp](../sharepoint/how-to-define-a-sharepoint-project-item-type.md).  
  
## <a name="retrieve-the-service-in-server-explorer-extensions"></a>Rufen Sie den Dienst in Server Explorer-Erweiterungen  
 In einer Erweiterung des der **SharePoint-Verbindungen** Knoten **Server-Explorer**, können Sie den Projektdienst zugreifen, mithilfe der <xref:Microsoft.VisualStudio.SharePoint.Explorer.IExplorerNode.ServiceProvider%2A> Eigenschaft eine <xref:Microsoft.VisualStudio.SharePoint.Explorer.IExplorerNode> Objekt.  
  
#### <a name="to-retrieve-the-service-in-a-server-explorer-extension"></a>Den Dienst in einer Server-Explorer-Erweiterung abrufen  
  
1.  Abrufen einer <xref:System.IServiceProvider> -Objekt aus der <xref:Microsoft.VisualStudio.SharePoint.Explorer.IExplorerNode.ServiceProvider%2A> Eigenschaft eine <xref:Microsoft.VisualStudio.SharePoint.Explorer.IExplorerNode> Objekt in der Erweiterung.  
  
2.  Verwenden der <xref:System.IServiceProvider.GetService%2A> Methode zum Anfordern einer <xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectService> Objekt.  
  
     Im folgenden Codebeispiel wird veranschaulicht, wie Sie den Projektdienst verwenden, zum Schreiben einer Meldung, die **Ausgabe** Fenster und **Fehlerliste** Fenster über ein Kontextmenü, das die Erweiterung in Listenknotenaddiert**Server-Explorer**.  
  
     [!code-vb[SPExtensibility.ProjectService.FromSPExplorerExtensions#1](../sharepoint/codesnippet/VisualBasic/spextensibility.projectservice.fromspexplorerextensions.getprojectservice/extension/extension.vb#1)]
     [!code-csharp[SPExtensibility.ProjectService.FromSPExplorerExtensions#1](../sharepoint/codesnippet/CSharp/spextensibility.projectservice.fromspexplorerextensions.getprojectservice/extension/extension.cs#1)]  
  
     Weitere Informationen zum Erweitern der **SharePoint-Verbindungen** Knoten **Server-Explorer**, finden Sie unter [Vorgehensweise: Erweitern eines SharePoint-Knotens im Server-Explorer](../sharepoint/how-to-extend-a-sharepoint-node-in-server-explorer.md).  
  
## <a name="retrieve-the-service-in-other-visual-studio-extensions"></a>Rufen Sie den Dienst in anderen Visual Studio-Erweiterungen  
 Sie können in einem VSPackage, oder klicken Sie in jeder Visual Studio-Erweiterung, die Zugriff auf den Projektdienst Abrufen einer <xref:EnvDTE80.DTE2> Objekts im Automatisierungsobjektmodell, z. B. ein Projekt-Assistent, die implementiert die <xref:Microsoft.VisualStudio.TemplateWizard.IWizard> Schnittstelle.  
  
 Sie können in einem VSPackage, Anfordern einer <xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectService> Objekt mit einer der folgenden Methoden:  
  
- Die <xref:System.IServiceProvider.GetService%2A> Methode eines verwalteten VSPackage, das von abgeleitet ist die <xref:Microsoft.VisualStudio.Shell.Package> Klasse. Weitere Informationen finden Sie unter [Vorgehensweise: Abrufen eines Diensts](../extensibility/how-to-get-a-service.md).  
  
- Die statische <xref:Microsoft.VisualStudio.Shell.Package.GetGlobalService%2A> Methode. Weitere Informationen finden Sie unter [Verwenden von GetGlobalService](../extensibility/internals/service-essentials.md#how-to-use-getglobalservice).  
  
  In Visual Studio-Erweiterung, die Zugriff auf eine <xref:EnvDTE80.DTE2> Objekt können Sie anfordern, eine <xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectService> -Objekt unter Verwendung der <xref:Microsoft.VisualStudio.Shell.ServiceProvider.GetService%2A> -Methode der ein <xref:Microsoft.VisualStudio.Shell.ServiceProvider> Objekt. Weitere Informationen finden Sie unter [Abrufen eines Diensts vom DTE-Objekt](../extensibility/how-to-get-a-service.md#getting-a-service-from-the-dte-object).  
  
## <a name="see-also"></a>Siehe auch
 [Verwenden Sie die SharePoint-Projektdiensts](../sharepoint/using-the-sharepoint-project-service.md)   
 [Vorgehensweise: Abrufen eines Diensts](../extensibility/how-to-get-a-service.md)   
 [Vorgehensweise: Verwenden von Assistenten mit Projektvorlagen](../extensibility/how-to-use-wizards-with-project-templates.md)  
