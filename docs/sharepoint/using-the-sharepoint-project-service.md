---
title: "Using the SharePoint Project Service | Microsoft Docs"
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
  - "SharePoint development in Visual Studio, extensibility features"
ms.assetid: bfb6cbc7-6c28-4e1a-abb4-88f149e7712c
caps.latest.revision: 34
author: "kempb"
ms.author: "kempb"
manager: "ghogen"
caps.handback.revision: 33
---
# Using the SharePoint Project Service
  Das SharePoint\-Projektsystem beinhaltet einen Projektdienst, den Sie verwenden können, um mit dem Projektsystem zusammenhängende Aufgaben auszuführen.  Der Projektdienst ist ein <xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectService>\-Objekt.  
  
 Sie können in jeder SharePoint\-Tools\-Erweiterung auf den SharePoint\-Projektdienst zugreifen.  Sie können auch in anderen Arten von Visual Studio\-Erweiterungen, z. B. Add\-Ins und VSPackages, auf ihn zugreifen.  Weitere Informationen dazu finden Sie unter [How to: Retrieve the SharePoint Project Service](../sharepoint/how-to-retrieve-the-sharepoint-project-service.md).  
  
## Funktionen des Projektdiensts  
 In der folgenden Tabelle sind die Aufgaben aufgelistet, die Sie mithilfe des SharePoint\-Projektdiensts und der <xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectService>\-Methode oder \-Eigenschaft ausführen können, um die einzelnen Aufgaben auszuführen.  
  
|Aufgabe|Zu verwendender Member|  
|-------------|----------------------------|  
|Zugriff auf beliebige SharePoint\-Projekte, die in Visual Studio geöffnet sind.|<xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectService.Projects%2A>\-Eigenschaft.|  
|Zugriff auf alle verfügbaren SharePoint\-Projektelementtypen \(einschließlich integrierter und benutzerdefinierter Projektelementtypen\).|<xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectService.ProjectItemTypes%2A>\-Eigenschaft.|  
|Zugriff auf alle die Bereitstellungsschritte, die für SharePoint\-Projekte verfügbar sind \(einschließlich integrierter und benutzerdefinierter Bereitstellungsschritte\).|<xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectService.DeploymentSteps%2A>\-Eigenschaft.|  
|Zugriff auf Ereignisse, die ausgelöst werden, wenn ein Entwickler Code in einem SharePoint\-Projekt umgestaltet.|<xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectService.CodeRefactoringEvents%2A>\-Eigenschaft.|  
|Ausführen eines benutzerdefinierten *SharePoint\-Befehls*, der einen Aufruf in das SharePoint\-Server\-Objektmodell ausführt.  Weitere Informationen zu SharePoint\-Befehlen finden Sie unter [Calling into the SharePoint Object Models](../sharepoint/calling-into-the-sharepoint-object-models.md).|<xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectService.SharePointConnection%2A>\-Eigenschaft.|  
|Konvertieren eines Typs im SharePoint\-Projektsystem in einen Typ im Visual Studio\-Automatisierungsobjektmodell oder \-Integrationsobjektmodell und umgekehrt.  Weitere Informationen finden Sie unter [Converting Between SharePoint Project System Types and Other Visual Studio Project Types](../sharepoint/converting-between-sharepoint-project-system-types-and-other-visual-studio-project-types.md).|<xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectService.Convert%2A>\-Methode.|  
|Schreiben von Nachrichten an das Fenster **Ausgabe** oder das Fenster **Fehlerliste** in Visual Studio.|<xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectService.Logger%2A>\-Eigenschaft.|  
|Zugriff auf andere in Visual Studio verfügbare Dienste.|<xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectService.ServiceProvider%2A>\-Eigenschaft.|  
|Abrufen des Pfads zum Installationsordner der lokalen SharePoint\-Website, der zum Debuggen der Projektmappe verwendet wird.|<xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectService.SharePointInstallPath%2A>\-Eigenschaft.|  
|Bestimmt, ob [!INCLUDE[moss_14_long](../sharepoint/includes/moss-14-long-md.md)] oder [!INCLUDE[wss_14_long](../sharepoint/includes/wss-14-long-md.md)] auf dem Computer installiert ist.|<xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectService.IsSharePointInstalled%2A>\-Eigenschaft.|  
|Überprüfen einer Funktion oder eines Pakets in einer SharePoint\-Lösung.|<xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectService.PackageValidationProvider%2A>\-Eigenschaft.|  
  
## Siehe auch  
 [Converting Between SharePoint Project System Types and Other Visual Studio Project Types](../sharepoint/converting-between-sharepoint-project-system-types-and-other-visual-studio-project-types.md)   
 [How to: Retrieve the SharePoint Project Service](../sharepoint/how-to-retrieve-the-sharepoint-project-service.md)   
 [Extending the SharePoint Tools in Visual Studio](../sharepoint/extending-the-sharepoint-tools-in-visual-studio.md)   
 [Overview of the Programming Model of SharePoint Tools Extensions](../sharepoint/overview-of-the-programming-model-of-sharepoint-tools-extensions.md)   
 [Vorgehensweise: Abrufen eines Diensts vom DTE\-Objekt](http://msdn.microsoft.com/library/bb166401.aspx)  
  
  