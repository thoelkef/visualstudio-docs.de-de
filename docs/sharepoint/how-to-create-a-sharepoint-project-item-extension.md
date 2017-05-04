---
title: "How to: Create a SharePoint Project Item Extension | Microsoft Docs"
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
  - "project items [SharePoint development in Visual Studio], extending"
  - "SharePoint project items, extending"
  - "SharePoint development in Visual Studio, extending project items"
ms.assetid: 163738b9-e25a-49c9-8f33-4b57a2da6b07
caps.latest.revision: 31
author: "kempb"
ms.author: "kempb"
manager: "ghogen"
caps.handback.revision: 30
---
# How to: Create a SharePoint Project Item Extension
  Erstellen Sie eine Projektelementerweiterung, wenn Sie weitere Funktionen zu einem SharePoint\-Projektelement hinzufügen möchten, das in Visual Studio bereits installiert ist.  Weitere Informationen finden Sie unter [Extending SharePoint Project Items](../sharepoint/extending-sharepoint-project-items.md).  
  
### So erstellen Sie eine Projektelementerweiterung  
  
1.  Erstellen Sie ein Klassenbibliotheksprojekt.  
  
2.  Fügen Sie Verweise auf die folgenden Assemblys hinzu:  
  
    -   Microsoft.VisualStudio.SharePoint  
  
    -   System.ComponentModel.Composition  
  
3.  Erstellen Sie eine Klasse, die die <xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectItemTypeExtension>\-Schnittstelle implementiert.  
  
4.  Fügen Sie der Klasse die folgenden Attribute hinzu:  
  
    -   <xref:System.ComponentModel.Composition.ExportAttribute>.  Anhand dieses Attributs kann Visual Studio Ihre <xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectItemTypeExtension>\-Implementierung erkennen und laden.  Übergeben Sie den Typ <xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectItemTypeExtension> an den Attributkonstruktor.  
  
    -   <xref:Microsoft.VisualStudio.SharePoint.SharePointProjectItemTypeAttribute>.  In einer Projektelementerweiterung identifiziert dieses Attribut das Projektelement, das Sie erweitern möchten.  Übergeben Sie die ID des Projektelements an den Attributkonstruktor.  Eine Liste der IDs der Projektelemente, die in Visual Studio enthalten sind, finden Sie [Extending SharePoint Project Items](../sharepoint/extending-sharepoint-project-items.md)weitere Informationen.  
  
5.  Verwenden Sie in der Implementierung der <xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectItemTypeExtension.Initialize%2A>\-Methode Member des *projectItemType*\-Parameters, um das Verhalten der Erweiterung zu definieren.  Dieser Parameter ist ein <xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectItemType>\-Objekt, das Zugriff auf die in den <xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectItemEvents>\- und <xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectItemFileEvents>\-Schnittstellen definierten Ereignisse bietet.  Wenn Sie auf eine bestimmte Instanz des erweiterten Projektelementtyps zugreifen möchten, behandeln Sie <xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectItemEvents>\-Ereignisse wie <xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectItemEvents.ProjectItemAdded> und <xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectItemEvents.ProjectItemInitialized>.  
  
## Beispiel  
 Im folgenden Codebeispiel wird veranschaulicht, wie eine einfache Erweiterung für das Projektelement Ereignisempfänger erstellt wird.  Jedes Mal, wenn der Benutzer einem SharePoint\-Projekt ein Projektelement vom Typ "Ereignisempfänger" hinzufügt, schreibt diese Erweiterung eine Meldung in die Fenster **Ausgabe** und **Fehlerliste**.  
  
 [!code-csharp[SPExtensibility.ProjectSystemExtension.General#1](../snippets/csharp/VS_Snippets_OfficeSP/spextensibility.projectsystemextension.general/cs/extension/projectitemextension.cs#1)]
 [!code-vb[SPExtensibility.ProjectSystemExtension.General#1](../snippets/visualbasic/VS_Snippets_OfficeSP/spextensibility.projectsystemextension.general/vb/extension/projectitemextension.vb#1)]  
  
 In diesem Beispiel wird der SharePoint\-Projektdienst verwendet, um die Meldung in die Fenster **Ausgabe** und **Fehlerliste** zu schreiben.  Weitere Informationen finden Sie unter [Using the SharePoint Project Service](../sharepoint/using-the-sharepoint-project-service.md).  
  
## Kompilieren des Codes  
 Für dieses Beispiel sind Verweise auf die folgenden Assemblys erforderlich:  
  
-   Microsoft.VisualStudio.SharePoint  
  
-   System.ComponentModel.Composition  
  
## Bereitstellen der Erweiterung  
 Erstellen Sie ein [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)]\-Erweiterungspaket \(VSIX\) für die Assembly und alle weiteren Dateien, die Sie mit der Erweiterung verteilen möchten, um die Erweiterung bereitzustellen.  Weitere Informationen erhalten Sie unter [Deploying Extensions for the SharePoint Tools in Visual Studio](../sharepoint/deploying-extensions-for-the-sharepoint-tools-in-visual-studio.md).  
  
## Siehe auch  
 [Extending SharePoint Project Items](../sharepoint/extending-sharepoint-project-items.md)   
 [Walkthrough: Extending a SharePoint Project Item Type](../sharepoint/walkthrough-extending-a-sharepoint-project-item-type.md)  
  
  