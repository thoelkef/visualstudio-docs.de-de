---
title: "Extending SharePoint Project Items"
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
ms.assetid: f09f6664-196d-46d6-819f-3c6500f23536
caps.latest.revision: 22
author: "kempb"
ms.author: "kempb"
manager: "ghogen"
caps.handback.revision: 21
---
# Extending SharePoint Project Items
  Erstellen Sie eine Projektelementerweiterung, wenn Sie einem SharePoint\-Projektelementtyp weitere Funktionen hinzufügen möchten, der in Visual Studio bereits installiert ist.  Sie können in Visual Studio z. B. eine Erweiterung für die integrierten Projektelemente **Ereignisempfänger** oder **Listendefinition** erstellen, oder Sie können eine Erweiterung für einen benutzerdefinierten Projektelementtyp erstellen.  Außerdem können Sie eine Erweiterung für alle Typen von SharePoint\-Projektelementen erstellen.  
  
## Aufgaben beim Erweitern von SharePoint\-Projektelementen  
 Um ein Projektelement zu erweitern, erstellen Sie eine Visual Studio\-Erweiterungsassembly, die die <xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectItemTypeExtension>\-Schnittstelle implementiert.  Weitere Informationen finden Sie unter [How to: Create a SharePoint Project Item Extension](../sharepoint/how-to-create-a-sharepoint-project-item-extension.md).  
  
 Wenn Sie ein Projektelement erweitern, können Sie dem Projektelement auch die folgende Funktionalität hinzufügen:  
  
-   Fügen Sie dem Projektelement ein Kontextmenüelement hinzu.  Das Menüelement wird angezeigt, wenn Sie das Kontextmenü für das Projektelement in **Projektmappen\-Explorer** öffnen.  Sie öffnen das Kontextmenü, indem Sie auf das Projektelement mit der rechten Maustaste klicken oder indem Sie sie auswählen und dann die UMSCHALT\+F10\-Tasten auswählen.  Weitere Informationen finden Sie unter [How to: Add a Shortcut Menu Item to a SharePoint Project Item Extension](../sharepoint/how-to-add-a-shortcut-menu-item-to-a-sharepoint-project-item-extension.md).  
  
-   Fügen Sie dem Projektelement eine benutzerdefinierte Eigenschaft hinzu.  Die Eigenschaft wird im **Eigenschaften** angezeigt, wenn Sie das Projektelement in **Projektmappen\-Explorer** auswählen.  Weitere Informationen finden Sie unter [How to: Add a Property to a SharePoint Project Item Extension](../sharepoint/how-to-add-a-property-to-a-sharepoint-project-item-extension.md).  
  
 Eine exemplarische Vorgehensweise, die das Erstellen, Bereitstellen und Testen einer Projektelementerweiterung veranschaulicht, finden Sie unter [Walkthrough: Extending a SharePoint Project Item Type](../sharepoint/walkthrough-extending-a-sharepoint-project-item-type.md).  
  
## Grundlegendes zur Beziehung zwischen Projektelementerweiterungen und Projektelementinstanzen  
 Während der Erstellung einer Projektelementerweiterung lädt Visual Studio die Erweiterung, wenn einem SharePoint\-Projekt ein Projektelement des zugeordneten Typs hinzugefügt wird.  Wenn Sie z. B. eine Erweiterung für Projektelemente vom Typ **Ereignisempfänger** erstellen, lädt Visual Studio die Erweiterung, wenn ein Benutzer einem Projekt ein Projektelement vom Typ **Ereignisempfänger** hinzufügt.  Visual Studio verwendet die gleiche Instanz Ihrer Erweiterung für alle Instanzen des zugeordneten Projektelementtyps.  Wenn der Benutzer dem Projekt im vorherigen Beispiel ein zweites Projektelement vom Typ **Ereignisempfänger** hinzufügt, wird die gleiche Instanz der Erweiterung verwendet, um das zweite Projektelement anzupassen.  
  
 Um auf eine bestimmte Instanz des erweiterten Projektelementtyps zuzugreifen, behandeln Sie eines der <xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectItemEvents>\-Ereignisse des *projectItemType*\-Parameters in der Implementierung der <xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectItemTypeExtension.Initialize%2A>\-Methode.  Wenn Sie z. B. festlegen möchten, wann ein Projektelement des Typs, für den Sie eine Erweiterung eingerichtet haben, einem Projekt hinzugefügt wird, behandeln Sie das <xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectItemEvents.ProjectItemAdded>\-Ereignis.  Weitere Informationen finden Sie unter [How to: Create a SharePoint Project Item Extension](../sharepoint/how-to-create-a-sharepoint-project-item-extension.md).  
  
## Bezeichner für SharePoint\-Projektelemente  
 Jedes SharePoint\-Projektelement verfügt über einen zugehörigen Zeichenfolgenbezeichner.  Sie müssen den Bezeichner für ein Projektelement kennen, wenn Sie die folgenden Aufgaben ausführen möchten:  
  
-   Erstellen einer Erweiterung für das Projektelement.  In diesem Fall müssen Sie den Bezeichner für das Projektelement, das Sie erweitern möchten, an den Konstruktor von <xref:Microsoft.VisualStudio.SharePoint.SharePointProjectItemTypeAttribute> übergeben.  Um eine Erweiterung für alle Projektelementtypen zu erstellen, übergeben Sie den Zeichenfolgenwert **\***.  
  
-   Programmgesteuertes Hinzufügen eines Projektelements zu einem Projekt.  In diesem Fall müssen Sie den Bezeichner für das Projektelement an die <xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectItemCollection.Add%2A>\-Methode übergeben.  
  
 In der folgenden Tabelle sind die Bezeichner für die SharePoint\-Projektelemente aufgeführt, die in Visual Studio enthalten sind.  
  
|Projektelementname|Zeichenfolgenbezeichner|  
|------------------------|-----------------------------|  
|Geschäftsdatenkatalogmodell|Microsoft.VisualStudio.SharePoint.BusinessDataConnectivity|  
|Inhaltstyp|Microsoft.VisualStudio.SharePoint.ContentType|  
|Ereignisempfänger|Microsoft.VisualStudio.SharePoint.EventHandler|  
|Leeres Element|Microsoft.VisualStudio.SharePoint.GenericElement|  
|Listendefinition<br /><br /> Listendefinition aus Inhaltstyp|Microsoft.VisualStudio.SharePoint.ListDefinition|  
|Listeninstanz|Microsoft.VisualStudio.SharePoint.ListInstance|  
|Modul|Microsoft.VisualStudio.SharePoint.Module|  
|Sequenzieller Workflow<br /><br /> Zustandsautomatworkflow|Microsoft.VisualStudio.SharePoint.Workflow|  
|Websitedefinition|Microsoft.VisualStudio.SharePoint.SiteDefinition|  
|Visuelles Webpart|Microsoft.VisualStudio.SharePoint.VisualWebPart|  
|Webpart|Microsoft.VisualStudio.SharePoint.WebPart|  
|Workflowzuordnungsformular|Microsoft.VisualStudio.SharePoint.WorkflowAssociation|  
  
## Siehe auch  
 [How to: Create a SharePoint Project Item Extension](../sharepoint/how-to-create-a-sharepoint-project-item-extension.md)   
 [How to: Add a Shortcut Menu Item to a SharePoint Project Item Extension](../sharepoint/how-to-add-a-shortcut-menu-item-to-a-sharepoint-project-item-extension.md)   
 [How to: Add a Property to a SharePoint Project Item Extension](../sharepoint/how-to-add-a-property-to-a-sharepoint-project-item-extension.md)   
 [Walkthrough: Extending a SharePoint Project Item Type](../sharepoint/walkthrough-extending-a-sharepoint-project-item-type.md)   
 [Extending the SharePoint Project System](../sharepoint/extending-the-sharepoint-project-system.md)  
  
  