---
title: 'Vorgehensweise: Abrufen des SharePoint-Projektdiensts | Microsoft Docs'
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
ms.openlocfilehash: f1e8cdcc863cfd363b1a73f11ed05ffb5a5ff12e
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/16/2018
---
# <a name="how-to-retrieve-the-sharepoint-project-service"></a>Gewusst wie: Abrufen des SharePoint-Projektdiensts
  Sie können die SharePoint-Projektdienst in den folgenden Typen von Projektmappen zugreifen:  
  
-   Eine Erweiterung der SharePoint-Projektsystem, wie projekterweiterung, projektelementerweiterung oder Projektelementdefinition Typ. Weitere Informationen zu diesen Erweiterungen finden Sie unter [Erweitern des SharePoint-Projektsystems](../sharepoint/extending-the-sharepoint-project-system.md).  
  
-   Eine Erweiterung der **SharePoint-Verbindungen** Knoten **Server-Explorer**. Weitere Informationen zu diesen Erweiterungen finden Sie unter [Erweitern des SharePoint-Verbindungsknotens im Server-Explorer](../sharepoint/extending-the-sharepoint-connections-node-in-server-explorer.md).  
  
-   Ein weiterer Typ von Visual Studio-Erweiterung, z. B. ein VSPackage.  
  
## <a name="retrieving-the-service-in-project-system-extensions"></a>Den Dienst im Projekt System Erweiterungen abrufen  
 In jeder SharePoint-Projektsystem-Erweiterung können Sie den Projektdienst zugreifen, mithilfe der <xref:Microsoft.VisualStudio.SharePoint.ISharePointProject.ProjectService%2A> Eigenschaft ein <xref:Microsoft.VisualStudio.SharePoint.ISharePointProject> Objekt.  
  
 Sie können auch den Projektdienst abrufen, mithilfe der folgenden Verfahren.  
  
#### <a name="to-retrieve-the-service-in-a-project-extension"></a>Den Dienst in einem projekterweiterung abrufen  
  
1.  In der Implementierung von der <xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectExtension> Schnittstelle, suchen Sie nach der <xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectExtension.Initialize%2A> Methode.  
  
2.  Verwenden der *ProjectService* Parameter auf den Dienst zuzugreifen.  
  
     Im folgenden Codebeispiel wird veranschaulicht, wie mithilfe des Projektdiensts schreiben eine Nachricht an die **Ausgabe** Fenster und **Fehlerliste** Fenster in ein einfaches Projekt-Erweiterung.  
  
     [!code-vb[SPExtensibility.ProjectService.FromProjectSystemExtensions#1](../sharepoint/codesnippet/VisualBasic/spextensibility.projectservice.fromprojectsystemextensions.getprojectservice/extension/extension.vb#1)]
     [!code-csharp[SPExtensibility.ProjectService.FromProjectSystemExtensions#1](../sharepoint/codesnippet/CSharp/spextensibility.projectservice.fromprojectsystemextensions.getprojectservice/extension/extension.cs#1)]  
  
     Weitere Informationen zum Erstellen von Project-Erweiterungen finden Sie unter [Vorgehensweise: Erstellen einer SharePoint-Projekterweiterung](../sharepoint/how-to-create-a-sharepoint-project-extension.md).  
  
#### <a name="to-retrieve-the-service-in-a-project-item-extension"></a>Um den Dienst in einer projektelementerweiterung abzurufen.  
  
1.  In der Implementierung von der <xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectItemTypeExtension> Schnittstelle, suchen Sie nach der <xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectItemTypeExtension.Initialize%2A> Methode.  
  
2.  Verwenden der <xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectItemType.ProjectService%2A> Eigenschaft von der *ProjectItemType* Parameter, um den Dienst abzurufen.  
  
     Im folgenden Codebeispiel wird veranschaulicht, wie mithilfe des Projektdiensts schreiben eine Nachricht an die **Ausgabe** Fenster und **Fehlerliste** Fenster in einer einfachen Erweiterung von der **Listendefinition** -Projektelement.  
  
     [!code-vb[SPExtensibility.ProjectService.FromProjectSystemExtensions#2](../sharepoint/codesnippet/VisualBasic/spextensibility.projectservice.fromprojectsystemextensions.getprojectservice/extension/extension.vb#2)]
     [!code-csharp[SPExtensibility.ProjectService.FromProjectSystemExtensions#2](../sharepoint/codesnippet/CSharp/spextensibility.projectservice.fromprojectsystemextensions.getprojectservice/extension/extension.cs#2)]  
  
     Weitere Informationen zum Erstellen von Project-Element-Erweiterungen finden Sie unter [Vorgehensweise: Erstellen einer SharePoint-Projektelementerweiterung](../sharepoint/how-to-create-a-sharepoint-project-item-extension.md).  
  
#### <a name="to-retrieve-the-service-in-a-project-item-type-definition"></a>Zum Abrufen des Diensts in einem Projekt-Typdefinition  
  
1.  In der Implementierung von der <xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectItemTypeProvider> Schnittstelle, suchen Sie nach der <xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectItemTypeProvider.InitializeType%2A> Methode.  
  
2.  Verwenden der <xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectItemTypeDefinition.ProjectService%2A> Eigenschaft von der *TypeDefinition* Parameter, um den Dienst abzurufen.  
  
     Im folgenden Codebeispiel wird veranschaulicht, wie mithilfe des Projektdiensts schreiben eine Nachricht an die **Ausgabe** Fenster und **Fehlerliste** Fenster in ein einfaches Projekt-Typdefinition.  
  
     [!code-vb[SPExtensibility.ProjectService.FromProjectSystemExtensions#3](../sharepoint/codesnippet/VisualBasic/spextensibility.projectservice.fromprojectsystemextensions.getprojectservice/extension/extension.vb#3)]
     [!code-csharp[SPExtensibility.ProjectService.FromProjectSystemExtensions#3](../sharepoint/codesnippet/CSharp/spextensibility.projectservice.fromprojectsystemextensions.getprojectservice/extension/extension.cs#3)]  
  
     Weitere Informationen zum Definieren von Projektelementtypen, finden Sie unter [wie: Definieren Sie einen SharePoint-Projektelementtyp](../sharepoint/how-to-define-a-sharepoint-project-item-type.md).  
  
## <a name="retrieving-the-service-in-server-explorer-extensions"></a>Abrufen des Diensts in Server Explorer-Erweiterungen  
 In einer Erweiterung des der **SharePoint-Verbindungen** Knoten im **Server-Explorer**, erreichen Sie mithilfe des Projektdiensts der <xref:Microsoft.VisualStudio.SharePoint.Explorer.IExplorerNode.ServiceProvider%2A> Eigenschaft ein <xref:Microsoft.VisualStudio.SharePoint.Explorer.IExplorerNode> Objekt.  
  
#### <a name="to-retrieve-the-service-in-a-server-explorer-extension"></a>Den Dienst in einer Server-Explorer-Erweiterung abrufen  
  
1.  Abrufen einer <xref:System.IServiceProvider> -Objekt aus der <xref:Microsoft.VisualStudio.SharePoint.Explorer.IExplorerNode.ServiceProvider%2A> Eigenschaft ein <xref:Microsoft.VisualStudio.SharePoint.Explorer.IExplorerNode> Objekt in der Erweiterung.  
  
2.  Verwenden der <xref:System.IServiceProvider.GetService%2A> Methode zum Anfordern einer <xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectService> Objekt.  
  
     Im folgenden Codebeispiel wird veranschaulicht, wie mithilfe des Projektdiensts schreiben eine Nachricht an die **Ausgabe** Fenster und **Fehlerliste** Fenster über ein Kontextmenü aufrufen, das die Erweiterung in Listenknotenaddiert**Server-Explorer**.  
  
     [!code-vb[SPExtensibility.ProjectService.FromSPExplorerExtensions#1](../sharepoint/codesnippet/VisualBasic/spextensibility.projectservice.fromspexplorerextensions.getprojectservice/extension/extension.vb#1)]
     [!code-csharp[SPExtensibility.ProjectService.FromSPExplorerExtensions#1](../sharepoint/codesnippet/CSharp/spextensibility.projectservice.fromspexplorerextensions.getprojectservice/extension/extension.cs#1)]  
  
     Weitere Informationen zum Erweitern der **SharePoint-Verbindungen** Knoten **Server-Explorer**, finden Sie unter [wie: Erweitern eines SharePoint-Knotens im Server-Explorer](../sharepoint/how-to-extend-a-sharepoint-node-in-server-explorer.md).  
  
## <a name="retrieving-the-service-in-other-visual-studio-extensions"></a>Abrufen des Diensts in anderen Visual Studio-Erweiterungen  
 Sie können Project-Dienst in einem VSPackage oder in jeder Visual Studio-Erweiterung, die Zugriff auf hat abrufen eine <xref:EnvDTE80.DTE2> Objekt in das Automatisierungsobjektmodell, z. B. ein Projekt-Assistent, die implementiert die <xref:Microsoft.VisualStudio.TemplateWizard.IWizard> Schnittstelle.  
  
 Sie können in einem VSPackage Anfordern einer <xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectService> Objekt mithilfe einer der folgenden Methoden:  
  
-   Die <xref:System.IServiceProvider.GetService%2A> Methode eines verwalteten VSPackage, das von abgeleitet ist die <xref:Microsoft.VisualStudio.Shell.Package> Klasse. Weitere Informationen finden Sie unter [Vorgehensweise: Abrufen eines Diensts](../extensibility/how-to-get-a-service.md).  
  
-   Die statische <xref:Microsoft.VisualStudio.Shell.Package.GetGlobalService%2A> Methode. Weitere Informationen finden Sie unter [Verwenden von GetGlobalService](../extensibility/internals/service-essentials.md#how-to-use-getglobalservice).  
  
 In einer Visual Studio-Erweiterung, die Zugriff auf eine <xref:EnvDTE80.DTE2> -Objekt, können Sie anfordern ein <xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectService> Objekt mithilfe der <xref:Microsoft.VisualStudio.Shell.ServiceProvider.GetService%2A> Methode eine <xref:Microsoft.VisualStudio.Shell.ServiceProvider> Objekt. Weitere Informationen finden Sie unter [Abrufen eines Diensts vom DTE-Objekt](../extensibility/how-to-get-a-service.md#getting-a-service-from-the-dte-object).  
  
## <a name="see-also"></a>Siehe auch  
 [Verwenden des SharePoint-Projektdiensts](../sharepoint/using-the-sharepoint-project-service.md)   
 [Vorgehensweise: Abrufen eines Diensts](../extensibility/how-to-get-a-service.md)   
 [Gewusst wie: Verwenden von Assistenten mit Projektvorlagen](../extensibility/how-to-use-wizards-with-project-templates.md)  
  
  