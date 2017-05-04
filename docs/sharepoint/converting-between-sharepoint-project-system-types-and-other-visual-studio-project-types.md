---
title: "Converting Between SharePoint Project System Types and Other Visual Studio Project Types | Microsoft Docs"
ms.custom: ""
ms.date: "02/02/2017"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "office-development"
ms.tgt_pltfrm: ""
ms.topic: "article"
dev_langs: 
  - "VB"
  - "CSharp"
helpviewer_keywords: 
  - "SharePoint project service"
ms.assetid: ad5d8ab2-1659-4e6a-8783-47e0dad44b11
caps.latest.revision: 13
author: "kempb"
ms.author: "kempb"
manager: "ghogen"
caps.handback.revision: 12
---
# Converting Between SharePoint Project System Types and Other Visual Studio Project Types
  Manchmal benötigen Sie bei der Arbeit mit einem Objekt im SharePoint\-Projektsystem unter Umständen die Funktionen eines entsprechenden Objekts im Visual Studio\-Automatisierungsobjektmodell oder im Integrationsobjektmodell und umgekehrt.  In einem solchen Fall können Sie das Objekt mithilfe der <xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectService.Convert%2A>\-Methode des SharePoint\-Projektdiensts in ein anderes Objektmodell konvertieren.  
  
 Beispiel: Sie verfügen über ein <xref:Microsoft.VisualStudio.SharePoint.ISharePointProject>\-Objekt, möchten jedoch Methoden verwenden, die nur für ein <xref:EnvDTE.Project>\-Objekt oder für ein <xref:Microsoft.VisualStudio.Shell.Interop.IVsProject>\-Objekt verfügbar sind.  In diesem Fall können Sie <xref:Microsoft.VisualStudio.SharePoint.ISharePointProject> mithilfe der <xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectService.Convert%2A>\-Methode zu <xref:EnvDTE.Project> oder zu <xref:Microsoft.VisualStudio.Shell.Interop.IVsProject> konvertieren.  
  
 Weitere Informationen zum Visual Studio\-Automatisierungsobjektmodell und dem Visual Studio\-Integrationsobjektmodell finden Sie unter [Overview of the Programming Model of SharePoint Tools Extensions](../sharepoint/overview-of-the-programming-model-of-sharepoint-tools-extensions.md).  
  
## Konvertierungstypen  
 In der folgenden Tabelle sind die Typen aufgeführt, die mit dieser Methode zwischen dem SharePoint\-Projektsystem und den anderen Visual Studio\-Objektmodellen konvertiert werden können.  
  
|SharePoint\-Projektsystemtyp|Entsprechende Typen im Automatisierungs\- und im Integrationsobjektmodell|  
|----------------------------------|-------------------------------------------------------------------------------|  
|<xref:Microsoft.VisualStudio.SharePoint.ISharePointProject>|<xref:EnvDTE.Project><br /><br /> oder<br /><br /> Jede Schnittstelle im Visual Studio\-Integrationsobjektmodell, das vom zugrunde liegende COM\-Objekt für das Projekt implementiert wird.  Diese Schnittstellen schließen <xref:Microsoft.VisualStudio.Shell.Interop.IVsHierarchy>, <xref:Microsoft.VisualStudio.Shell.Interop.IVsProject> \(oder eine abgeleitete Schnittstelle\) und <xref:Microsoft.VisualStudio.Shell.Interop.IVsBuildPropertyStorage> ein.  Eine Liste der wichtigsten Schnittstellen, die von Projekten implementiert werden, finden Sie unter [Projekt-Modell-Kernkomponenten](../extensibility/internals/project-model-core-components.md).|  
|<xref:Microsoft.VisualStudio.SharePoint.IMappedFolder><br /><br /> <xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectItem><br /><br /> <xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectItemFile><br /><br /> <xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectFeature><br /><br /> <xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectFeatureResourceFile><br /><br /> <xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectPackage>|<xref:EnvDTE.ProjectItem><br /><br /> oder<br /><br /> Ein <xref:System.UInt32>\-Wert \(auch: VSITEMID\) zum Angeben des Projektmembers in <xref:Microsoft.VisualStudio.Shell.Interop.IVsHierarchy>, in dem er enthalten ist.  Dieser Wert kann an den *itemid*\-Parameter einiger <xref:Microsoft.VisualStudio.Shell.Interop.IVsHierarchy>\-Methoden übergeben werden.|  
  
## Beispiel  
 Im folgenden Codebeispiel wird veranschaulicht, wie mit der <xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectService.Convert%2A>\-Methode ein <xref:Microsoft.VisualStudio.SharePoint.ISharePointProject>\-Objekt in ein <xref:EnvDTE.Project> konvertiert wird.  
  
 [!code-csharp[SPExtensibility.ProjectService.FromDTE#2](../snippets/csharp/VS_Snippets_OfficeSP/spextensibility.projectservice.fromdte/cs/connect.cs#2)]
 [!code-vb[SPExtensibility.ProjectService.FromDTE#2](../snippets/visualbasic/VS_Snippets_OfficeSP/spextensibility.projectservice.fromdte/vb/connect.vb#2)]  
  
 Dieses Beispiel setzt Folgendes voraus:  
  
-   Eine Erweiterung des SharePoint\-Projektsystems mit einem Verweis auf die Assembly EnvDTE.dll.  Weitere Informationen finden Sie unter [Extending the SharePoint Project System](../sharepoint/extending-the-sharepoint-project-system.md).  
  
-   Code, in dem die `projectService_ProjectAdded`\-Methode registriert ist, um das <xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectEvents.ProjectAdded>\-Ereignis eines <xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectService>\-Objekts zu behandeln.  Ein Beispiel finden Sie unter [How to: Create a SharePoint Project Extension](../sharepoint/how-to-create-a-sharepoint-project-extension.md).  
  
## Siehe auch  
 [Using the SharePoint Project Service](../sharepoint/using-the-sharepoint-project-service.md)   
 [How to: Retrieve the SharePoint Project Service](../sharepoint/how-to-retrieve-the-sharepoint-project-service.md)   
 [Overview of the Programming Model of SharePoint Tools Extensions](../sharepoint/overview-of-the-programming-model-of-sharepoint-tools-extensions.md)  
  
  