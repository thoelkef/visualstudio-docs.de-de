---
title: "Associating Custom Data with SharePoint Tools Extensions | Microsoft Docs"
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
  - "projects [SharePoint development in Visual Studio], associating custom data"
  - "project items [SharePoint development in Visual Studio], associating custom data"
  - "SharePoint project items, associating custom data"
  - "SharePoint projects, associating custom data"
  - "SharePoint development in Visual Studio, extensibility features"
ms.assetid: cfc87272-85a1-4c36-89e4-2662417d59ea
caps.latest.revision: 27
author: "kempb"
ms.author: "kempb"
manager: "ghogen"
caps.handback.revision: 26
---
# Associating Custom Data with SharePoint Tools Extensions
  Sie können bestimmten Objekten in SharePoint\-Tools\-Erweiterungen benutzerdefinierte Daten hinzufügen.  Dies ist nützlich, wenn sich in einem Teil der Erweiterung Daten befinden, auf die später von anderem Code in der Erweiterung zugegriffen werden soll.  Anstatt eine benutzerdefinierte Möglichkeit zum Speichern von Daten und Zugreifen auf Daten zu implementieren, können Sie die Daten einem Objekt in der Erweiterung zuordnen und später die Daten aus dem gleichen Objekt abrufen.  
  
 Das Hinzufügen benutzerdefinierter Daten zu Objekten ist auch nützlich, wenn Sie Daten beibehalten möchten, die in Visual Studio für ein bestimmtes Element relevant sind.  SharePoint\-Tools\-Erweiterungen werden nur einmal in Visual Studio geladen, deshalb kann die Erweiterung jederzeit auch mit mehreren anderen Elementen \(z. B. Projekten, Projektelementen oder **Server Explorer**\-Knoten\) funktionieren.  Verfügen Sie über benutzerdefinierte Daten, die nur für ein bestimmtes Element relevant sind, können die Daten dem Objekt hinzugefügt werden, das dieses Element darstellt.  
  
 Wenn Sie Objekten in SharePoint\-Tools\-Erweiterungen benutzerdefinierte Daten hinzufügen, werden diese nicht beibehalten.  Die Daten sind nur für die Lebensdauer des Objekts verfügbar.  Wird das Objekt durch die automatische Speicherbereinigung freigegeben, gehen die Daten verloren.  
  
 In Erweiterungen des SharePoint\-Projektsystems können Sie auch Zeichenfolgendaten speichern, die nach dem Entladen einer Erweiterung erhalten bleiben.  Weitere Informationen finden Sie unter [Saving Data in Extensions of the SharePoint Project System](../sharepoint/saving-data-in-extensions-of-the-sharepoint-project-system.md).  
  
## Objekte mit benutzerdefinierten Daten  
 Sie können jedem Objekt im SharePoint\-Tools\-Objektmodell, das die <xref:Microsoft.VisualStudio.SharePoint.IAnnotatedObject>\-Schnittstelle implementiert, benutzerdefinierte Daten hinzufügen.  Mit dieser Schnittstelle wird nur die Eigenschaft <xref:Microsoft.VisualStudio.SharePoint.IAnnotatedObject.Annotations%2A> definiert, die eine Auflistung benutzerdefinierter Datenobjekte darstellt.  <xref:Microsoft.VisualStudio.SharePoint.IAnnotatedObject> wird von folgenden Typen implementiert:  
  
-   <xref:Microsoft.VisualStudio.SharePoint.IMappedFolder>  
  
-   <xref:Microsoft.VisualStudio.SharePoint.IMenuItem>  
  
-   <xref:Microsoft.VisualStudio.SharePoint.ISharePointProject>  
  
-   <xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectFeature>  
  
-   <xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectFeatureResourceFile>  
  
-   <xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectItem>  
  
-   <xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectItemFile>  
  
-   <xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectItemType>  
  
-   <xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectItemTypeDefinition>  
  
-   <xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectMember>  
  
-   <xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectPackage>  
  
-   <xref:Microsoft.VisualStudio.SharePoint.Deployment.IDeploymentContext>  
  
-   <xref:Microsoft.VisualStudio.SharePoint.Explorer.IExplorerNode>  
  
-   <xref:Microsoft.VisualStudio.SharePoint.Explorer.IExplorerNodeType>  
  
-   <xref:Microsoft.VisualStudio.SharePoint.Explorer.IExplorerNodeTypeDefinition>  
  
## Hinzufügen und Abrufen von benutzerdefinierten Daten  
 Zum Hinzufügen von benutzerdefinierten Daten zu einem Objekt in einer SharePoint\-Tools\-Erweiterung rufen Sie die <xref:Microsoft.VisualStudio.SharePoint.IAnnotatedObject.Annotations%2A>\-Eigenschaft des Objekts ab, dem Sie Daten hinzufügen möchten, und verwenden Sie dann die <xref:Microsoft.VisualStudio.SharePoint.IAnnotationDictionary.Add%2A>\-Methode, um dem Objekt Daten hinzuzufügen.  
  
 Wenn Sie benutzerdefinierte Daten aus einem Objekt in einer SharePoint\-Tools\-Erweiterung abrufen möchten, rufen Sie die <xref:Microsoft.VisualStudio.SharePoint.IAnnotatedObject.Annotations%2A>\-Eigenschaft des Objekts ab, und verwenden Sie dann eine der folgenden Methoden:  
  
-   <xref:Microsoft.VisualStudio.SharePoint.IAnnotationDictionary.TryGetValue%2A>.  Diese Methode gibt **true** zurück, wenn das Datenobjekt vorhanden ist, bzw. **false**, wenn es nicht vorhanden ist.  Mit dieser Methode können Sie Instanzen von Werttypen oder Verweistypen abrufen.  
  
-   <xref:Microsoft.VisualStudio.SharePoint.IAnnotationDictionary.GetValue%2A>.  Diese Methode gibt das Datenobjekt zurück, wenn dieses vorhanden ist, bzw. **null**, wenn es nicht vorhanden ist.  Mit dieser Methode können Sie nur Instanzen von Verweistypen abrufen.  
  
 Im folgenden Codebeispiel wird ermittelt, ob ein bestimmtes Datenobjekt einem Projektelement bereits zugeordnet wurde.  Ist das Datenobjekt dem Projektelement noch nicht zugeordnet, wird das Objekt der <xref:Microsoft.VisualStudio.SharePoint.IAnnotatedObject.Annotations%2A>\-Eigenschaft des Projektelements vom Code hinzugefügt.  Unter [How to: Add a Property to a Custom SharePoint Project Item Type](../sharepoint/how-to-add-a-property-to-a-custom-sharepoint-project-item-type.md) wird dieses Beispiel noch einmal in einem umfassenderen Beispiel veranschaulicht.  
  
 [!code-csharp[SPExtensibility.ProjectItemExtension.MenuAndProperty#13](../snippets/csharp/VS_Snippets_OfficeSP/spextensibility.projectitemextension.menuandproperty/cs/extension/projectitemtypeproperty.cs#13)]
 [!code-vb[SPExtensibility.ProjectItemExtension.MenuAndProperty#13](../snippets/visualbasic/VS_Snippets_OfficeSP/spextensibility.projectitemextension.menuandproperty/vb/extension/projectitemtypeproperty.vb#13)]  
  
## Siehe auch  
 [Programming Concepts and Features for SharePoint Tools Extensions](../sharepoint/programming-concepts-and-features-for-sharepoint-tools-extensions.md)   
 [Walkthrough: Creating a Custom Action Project Item with an Item Template, Part 1](../sharepoint/walkthrough-creating-a-custom-action-project-item-with-an-item-template-part-1.md)   
 [Walkthrough: Extending Server Explorer to Display Web Parts](../sharepoint/walkthrough-extending-server-explorer-to-display-web-parts.md)   
 [How to: Add a Property to SharePoint Projects](../sharepoint/how-to-add-a-property-to-sharepoint-projects.md)   
 [How to: Add a Property to a Custom SharePoint Project Item Type](../sharepoint/how-to-add-a-property-to-a-custom-sharepoint-project-item-type.md)  
  
  