---
title: "How to: Define a SharePoint Project Item Type"
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
  - "SharePoint project items, defining your own types"
  - "project items [SharePoint development in Visual Studio], defining your own types"
  - "SharePoint development in Visual Studio, defining new project item types"
ms.assetid: 18b56e7c-4efb-47a2-abfc-e9018ae38267
caps.latest.revision: 28
author: "kempb"
ms.author: "kempb"
manager: "ghogen"
caps.handback.revision: 27
---
# How to: Define a SharePoint Project Item Type
  Definieren Sie einen Projektelementtyp, wenn Sie ein benutzerdefiniertes SharePoint\-Projektelement erstellen möchten.  Weitere Informationen finden Sie unter [Defining Custom SharePoint Project Item Types](../sharepoint/defining-custom-sharepoint-project-item-types.md).  
  
### So definieren Sie einen Projektelementtyp  
  
1.  Erstellen Sie ein Klassenbibliotheksprojekt.  
  
2.  Fügen Sie Verweise auf die folgenden Assemblys hinzu:  
  
    -   Microsoft.VisualStudio.SharePoint  
  
    -   System.ComponentModel.Composition  
  
3.  Erstellen Sie eine Klasse, die die <xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectItemTypeProvider>\-Schnittstelle implementiert.  
  
4.  Fügen Sie der Klasse die folgenden Attribute hinzu:  
  
    -   <xref:System.ComponentModel.Composition.ExportAttribute>.  Anhand dieses Attributs kann Visual Studio Ihre <xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectItemTypeProvider>\-Implementierung erkennen und laden.  Übergeben Sie den Typ <xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectItemTypeProvider> an den Attributkonstruktor.  
  
    -   <xref:Microsoft.VisualStudio.SharePoint.SharePointProjectItemTypeAttribute>.  In einer Projektelementtypdefinition gibt dieses Attribut den Zeichenfolgenbezeichner für das neue Projektelement an.  Es wird empfohlen, das Format *Unternehmensname*.*Funktionsname* zu verwenden, um sicherzustellen, dass alle Projektelemente einen eindeutigen Namen haben.  
  
    -   <xref:Microsoft.VisualStudio.SharePoint.SharePointProjectItemIconAttribute>.  Dieses Attribut gibt das Symbol an, das im **Projektmappen\-Explorer** für dieses Projektelement angezeigt wird.  Dieses Attribut ist optional. Wenn Sie es nicht auf die Klasse anwenden, zeigt Visual Studio ein Standardsymbol für das Projektelement an.  Wenn Sie dieses Attribut festlegen, übergeben Sie den vollqualifizierten Namen eines Symbols oder einer Bitmap, die in die Assembly eingebettet ist.  
  
5.  Verwenden Sie in der Implementierung der <xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectItemTypeProvider.InitializeType%2A>\-Methode Member des *projectItemTypeDefinition*\-Parameters, um das Verhalten des Projektelementtyps zu definieren.  Dieser Parameter ist ein <xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectItemTypeDefinition>\-Objekt, das Zugriff auf die in den <xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectItemEvents>\- und <xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectItemFileEvents>\-Schnittstellen definierten Ereignisse bietet.  Wenn Sie auf eine bestimmte Instanz des Projektelementtyps zugreifen möchten, behandeln Sie <xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectItemEvents>\-Ereignisse wie <xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectItemEvents.ProjectItemAdded> und <xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectItemEvents.ProjectItemInitialized>.  
  
## Beispiel  
 Im folgenden Codebeispiel wird das Definieren eines einfachen Projektelementtyps veranschaulicht.  Dieser Projektelementtyp schreibt eine Meldung in die Fenster **Ausgabe** und **Fehlerliste**, wenn einem Projekt von einem Benutzer ein Projektelement dieses Typs hinzugefügt wird.  
  
 [!code-csharp[SPExtensibility.ProjectSystemExtension.General#2](../snippets/csharp/VS_Snippets_OfficeSP/spextensibility.projectsystemextension.general/cs/extension/projectitemtype.cs#2)]
 [!code-vb[SPExtensibility.ProjectSystemExtension.General#2](../snippets/visualbasic/VS_Snippets_OfficeSP/spextensibility.projectsystemextension.general/vb/extension/projectitemtype.vb#2)]  
  
 In diesem Beispiel wird der SharePoint\-Projektdienst verwendet, um die Meldung in die Fenster **Ausgabe** und **Fehlerliste** zu schreiben.  Weitere Informationen finden Sie unter [Using the SharePoint Project Service](../sharepoint/using-the-sharepoint-project-service.md).  
  
## Kompilieren des Codes  
 Für dieses Beispiel sind Verweise auf die folgenden Assemblys erforderlich:  
  
-   Microsoft.VisualStudio.SharePoint  
  
-   System.ComponentModel.Composition  
  
## Bereitstellen des Projektelements  
 Um Ihr Projektelement anderen Entwicklern zur Verfügung zu stellen, können Sie eine Projektvorlage oder eine Projektelementvorlage erstellen.  Weitere Informationen finden Sie unter [Creating Item Templates and Project Templates for SharePoint Project Items](../sharepoint/creating-item-templates-and-project-templates-for-sharepoint-project-items.md).  
  
 Erstellen Sie zum Bereitstellen des Projektelements ein [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)]\-Erweiterungspaket \(VSIX\) für die Assembly, die Vorlage und alle weiteren Dateien, die Sie mit dem Projektelement verteilen möchten.  Weitere Informationen finden Sie unter [Deploying Extensions for the SharePoint Tools in Visual Studio](../sharepoint/deploying-extensions-for-the-sharepoint-tools-in-visual-studio.md).  
  
## Siehe auch  
 [Defining Custom SharePoint Project Item Types](../sharepoint/defining-custom-sharepoint-project-item-types.md)   
 [Creating Item Templates and Project Templates for SharePoint Project Items](../sharepoint/creating-item-templates-and-project-templates-for-sharepoint-project-items.md)   
 [Walkthrough: Creating a Custom Action Project Item with an Item Template, Part 1](../sharepoint/walkthrough-creating-a-custom-action-project-item-with-an-item-template-part-1.md)   
 [Exemplarische Vorgehensweise: Erstellen eines Projektelements "Websitespalte" mit einer Projektvorlage, Teil 1](../sharepoint/walkthrough-creating-a-site-column-project-item-with-a-project-template-part-1.md)   
 [How to: Add a Property to a Custom SharePoint Project Item Type](../sharepoint/how-to-add-a-property-to-a-custom-sharepoint-project-item-type.md)   
 [How to: Add a Shortcut Menu Item to a Custom SharePoint Project Item Type](../sharepoint/how-to-add-a-shortcut-menu-item-to-a-custom-sharepoint-project-item-type.md)  
  
  