---
title: "Defining Custom SharePoint Project Item Types | Microsoft Docs"
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
ms.assetid: be300c24-fd1b-4fc7-a4e9-a5df1d81d3fc
caps.latest.revision: 22
author: "kempb"
ms.author: "kempb"
manager: "ghogen"
caps.handback.revision: 21
---
# Defining Custom SharePoint Project Item Types
  Definieren Sie einen neuen SharePoint\-Projektelementtyp, wenn Sie eine neue Art von SharePoint\-Projektelement erstellen möchten.  Visual Studio enthält z. B. keine SharePoint\-Projektelemente zum Hinzufügen von Feldern oder benutzerdefinierten Aktionen zu einer SharePoint\-Website.  Sie können eigene Typen von SharePoint\-Projektelementen definieren, um Felder, benutzerdefinierte Aktionen oder sonstige Typen von SharePoint\-Komponenten zu erstellen.  
  
## Aufgaben beim Definieren von SharePoint\-Projektelementtypen  
 Um einen benutzerdefinierten Projektelementtyp zu definieren, erstellen Sie eine Visual Studio\-Erweiterungsassembly, die die <xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectItemTypeProvider>\-Schnittstelle implementiert.  Weitere Informationen finden Sie unter [How to: Define a SharePoint Project Item Type](../sharepoint/how-to-define-a-sharepoint-project-item-type.md).  
  
 Wenn Sie einen benutzerdefinierten Projektelementtyp definieren, können Sie dem Projektelement auch die folgende Funktionalität hinzufügen:  
  
-   Fügen Sie dem Projektelement ein Kontextmenüelement hinzu.  Das Menüelement wird angezeigt, wenn Sie das Kontextmenü für das Projektelement in **Projektmappen\-Explorer** öffnen, indem Sie auf das Projektelement mit der rechten Maustaste klicken oder indem Sie sie auswählen und dann die UMSCHALT\+F10\-Tasten auswählen.  Weitere Informationen finden Sie unter [How to: Add a Shortcut Menu Item to a Custom SharePoint Project Item Type](../sharepoint/how-to-add-a-shortcut-menu-item-to-a-custom-sharepoint-project-item-type.md).  
  
-   Fügen Sie dem Projektelement eine benutzerdefinierte Eigenschaft hinzu.  Die Eigenschaft wird im **Eigenschaften** angezeigt, wenn Sie das Projektelement in **Projektmappen\-Explorer** auswählen.  Weitere Informationen finden Sie unter [How to: Add a Property to a Custom SharePoint Project Item Type](../sharepoint/how-to-add-a-property-to-a-custom-sharepoint-project-item-type.md).  
  
 Um anderen Entwicklern die Verwendung Ihres Projektelements in Visual Studio zu ermöglichen, erstellen Sie eine SPDATA\-Datei und eine Elementvorlage oder eine Projektvorlage, die dem Projektelement zugeordnet ist.  Weitere Informationen finden Sie unter [Creating Item Templates and Project Templates for SharePoint Project Items](../sharepoint/creating-item-templates-and-project-templates-for-sharepoint-project-items.md).  
  
## Grundlegendes zur Beziehung zwischen Projektelementtypen und Projektelementinstanzen  
 Während der Definition eines SharePoint\-Projektelementtyps lädt Visual Studio die Erweiterung, wenn einem SharePoint\-Projekt ein Projektelement des zugeordneten Typs hinzugefügt wird.  Wenn Sie z. B. einen neuen Projektelementtyp **Benutzerdefinierte Aktion** definieren, lädt Visual Studio die Erweiterung, wenn ein Benutzer einem Projekt ein Projektelement vom Typ **Benutzerdefinierte Aktion** hinzufügt.  Visual Studio verwendet die gleiche Instanz Ihrer Erweiterung für alle Instanzen des zugeordneten Projektelementtyps.  Wenn der Benutzer dem Projekt im vorherigen Beispiel ein zweites Projektelement vom Typ **Benutzerdefinierte Aktion** hinzufügt, wird die gleiche Instanz der Erweiterung verwendet, um das zweite Projektelement anzupassen.  
  
 Um auf eine bestimmte Instanz des Projektelementtyps zuzugreifen, behandeln Sie eines der <xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectItemEvents>\-Ereignisse des *projectItemTypeDefinition*\-Parameters in der Implementierung der <xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectItemTypeProvider.InitializeType%2A>\-Methode.  Um z. B. zu bestimmen, wann einem Projekt ein Projektelement des benutzerdefinierten Typs hinzugefügt wird, behandeln Sie das <xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectItemEvents.ProjectItemAdded>\-Ereignis.  Weitere Informationen finden Sie unter [How to: Define a SharePoint Project Item Type](../sharepoint/how-to-define-a-sharepoint-project-item-type.md).  
  
## Siehe auch  
 [How to: Define a SharePoint Project Item Type](../sharepoint/how-to-define-a-sharepoint-project-item-type.md)   
 [How to: Add a Property to a Custom SharePoint Project Item Type](../sharepoint/how-to-add-a-property-to-a-custom-sharepoint-project-item-type.md)   
 [How to: Add a Shortcut Menu Item to a Custom SharePoint Project Item Type](../sharepoint/how-to-add-a-shortcut-menu-item-to-a-custom-sharepoint-project-item-type.md)   
 [Creating Item Templates and Project Templates for SharePoint Project Items](../sharepoint/creating-item-templates-and-project-templates-for-sharepoint-project-items.md)   
 [Walkthrough: Creating a Custom Action Project Item with an Item Template, Part 1](../sharepoint/walkthrough-creating-a-custom-action-project-item-with-an-item-template-part-1.md)   
 [Exemplarische Vorgehensweise: Erstellen eines Projektelements "Websitespalte" mit einer Projektvorlage, Teil 1](../sharepoint/walkthrough-creating-a-site-column-project-item-with-a-project-template-part-1.md)   
 [Walkthrough: Creating a Custom Action Project Item with an Item Template, Part 2](../sharepoint/walkthrough-creating-a-custom-action-project-item-with-an-item-template-part-2.md)   
 [Exemplarische Vorgehensweise: Erstellen eines Projektelements "Websitespalte" mit einer Projektvorlage, Teil 2](../sharepoint/walkthrough-creating-a-site-column-project-item-with-a-project-template-part-2.md)   
 [Deploying Extensions for the SharePoint Tools in Visual Studio](../sharepoint/deploying-extensions-for-the-sharepoint-tools-in-visual-studio.md)  
  
  