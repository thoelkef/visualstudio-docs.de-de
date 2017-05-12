---
title: "How to: Add a Property to a SharePoint Project Item Extension"
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
ms.assetid: 4fd97ef2-86e7-4d92-8e34-5b0ec3cc43a0
caps.latest.revision: 20
author: "kempb"
ms.author: "kempb"
manager: "ghogen"
caps.handback.revision: 19
---
# How to: Add a Property to a SharePoint Project Item Extension
  Sie können eine Projektelementerweiterung verwenden, wenn Sie einem bereits in Visual Studio installierten SharePoint\-Projektelement eine Eigenschaft hinzufügen möchten.  Diese Eigenschaft wird im **Eigenschaftenfenster** angezeigt, wenn Sie das Projektelement im **Projektmappen\-Explorer** auswählen.  
  
 Im Folgenden wird angenommen, dass bereits eine Projektelementerweiterung erstellt wurde.  Weitere Informationen erhalten Sie unter [How to: Create a SharePoint Project Item Extension](../sharepoint/how-to-create-a-sharepoint-project-item-extension.md).  
  
### So fügen Sie einer Projektelementerweiterung eine Eigenschaft hinzu  
  
1.  Definieren Sie eine Klasse mit einer öffentlichen Eigenschaft, die die dem Projektelementtyp hinzuzufügende Eigenschaft darstellt.  Wenn Sie einem Projektelementtyp mehrere Eigenschaften hinzufügen möchten, können Sie alle Eigenschaften in der gleichen Klasse oder in unterschiedlichen Klassen definieren.  
  
2.  Behandeln Sie in der <xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectItemTypeExtension.Initialize%2A>\-Methode der <xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectItemTypeExtension>\-Implementierung das <xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectItemEvents.ProjectItemPropertiesRequested>\-Ereignis des *projectItemType*\-Parameters.  
  
3.  Fügen Sie im Ereignishandler für das <xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectItemEvents.ProjectItemPropertiesRequested>\-Ereignis der <xref:Microsoft.VisualStudio.SharePoint.SharePointProjectItemPropertiesRequestedEventArgs.PropertySources%2A>\-Auflistung des Ereignisargumentparameters eine Instanz der Eigenschaftenklasse hinzu.  
  
## Beispiel  
 Im folgenden Codebeispiel wird veranschaulicht, wie Sie einem Projektelement vom Typ "Ereignisempfänger" eine Eigenschaft mit dem Namen **Example Property** hinzufügen.  
  
 [!code-csharp[SPExtensibility.ProjectItemExtension.MenuAndProperty#8](../snippets/csharp/VS_Snippets_OfficeSP/spextensibility.projectitemextension.menuandproperty/cs/extension/projectitemextensionproperty.cs#8)]
 [!code-vb[SPExtensibility.ProjectItemExtension.MenuAndProperty#8](../snippets/visualbasic/VS_Snippets_OfficeSP/spextensibility.projectitemextension.menuandproperty/vb/extension/projectitemextensionproperty.vb#8)]  
  
### Grundlegendes zum Code  
 Damit stets die gleiche Instanz der `CustomProperties`\-Klasse beim <xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectItemEvents.ProjectItemPropertiesRequested>\-Ereignis verwendet wird, wird im folgenden Codebeispiel das Eigenschaftenobjekt in der <xref:Microsoft.VisualStudio.SharePoint.IAnnotatedObject.Annotations%2A>\-Eigenschaft des Projektelements gespeichert, sobald das Ereignis zum ersten Mal auftritt.  Vom Code wird dann jedes Mal, wenn das Ereignis auftritt, dieses Objekt abgerufen.  Weitere Informationen zur Verwendung der <xref:Microsoft.VisualStudio.SharePoint.IAnnotatedObject.Annotations%2A>\-Eigenschaft zum Zuordnen von Daten zu Projektelementen finden Sie unter [Associating Custom Data with SharePoint Tools Extensions](../sharepoint/associating-custom-data-with-sharepoint-tools-extensions.md).  
  
 Um die Änderungen des Eigenschaftswerts permanent zu speichern, speichert der **set**\-Accessor für `ExampleProperty` den neuen Wert in der <xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectItem.ExtensionData%2A>\-Eigenschaft des <xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectItem>\-Objekts, dem die Eigenschaft zugewiesen ist.  Weitere Informationen zur Verwendung der <xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectItem.ExtensionData%2A>\-Eigenschaft zum Speichern von Daten mit Projektelementen finden Sie unter [Saving Data in Extensions of the SharePoint Project System](../sharepoint/saving-data-in-extensions-of-the-sharepoint-project-system.md).  
  
### Angeben des Verhaltens benutzerdefinierter Eigenschaften  
 Sie können definieren, wie eine benutzerdefinierte Eigenschaft angezeigt wird und sich im **Eigenschaftenfenster** verhält, indem Sie Attribute aus dem <xref:System.ComponentModel>\-Namespace auf die Eigenschaftendefinition anwenden.  Die folgenden Attribute sind in vielen Szenarien hilfreich:  
  
-   <xref:System.ComponentModel.DisplayNameAttribute>: Gibt den Namen der Eigenschaft an, die im **Eigenschaftenfenster** angezeigt wird.  
  
-   <xref:System.ComponentModel.DescriptionAttribute>: Gibt die Beschreibungszeichenfolge an, die bei Auswahl der Eigenschaft unten im **Eigenschaftenfenster** angezeigt wird.  
  
-   <xref:System.ComponentModel.DefaultValueAttribute>: Gibt den Standardwert für die Eigenschaft an.  
  
-   <xref:System.ComponentModel.TypeConverterAttribute>: Gibt eine benutzerdefinierte Konvertierung zwischen der Zeichenfolge, die im **Eigenschaftenfenster** angezeigt wird, und einem Eigenschaftswert an, der keine Zeichenfolge ist.  
  
-   <xref:System.ComponentModel.EditorAttribute>: Gibt einen benutzerdefinierten Editor zum Ändern der Eigenschaft an.  
  
## Kompilieren des Codes  
 Für diese Beispiele ist ein Klassenbibliotheksprojekt mit Verweisen auf die folgenden Assemblys erforderlich:  
  
-   Microsoft.VisualStudio.SharePoint  
  
-   System.ComponentModel.Composition  
  
## Bereitstellen der Erweiterung  
 Erstellen Sie ein [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)]\-Erweiterungspaket \(VSIX\) für die Assembly und alle weiteren Dateien, die Sie mit der Erweiterung verteilen möchten, um die Erweiterung bereitzustellen.  Weitere Informationen erhalten Sie unter [Deploying Extensions for the SharePoint Tools in Visual Studio](../sharepoint/deploying-extensions-for-the-sharepoint-tools-in-visual-studio.md).  
  
## Siehe auch  
 [How to: Create a SharePoint Project Item Extension](../sharepoint/how-to-create-a-sharepoint-project-item-extension.md)   
 [How to: Add a Shortcut Menu Item to a SharePoint Project Item Extension](../sharepoint/how-to-add-a-shortcut-menu-item-to-a-sharepoint-project-item-extension.md)   
 [Extending SharePoint Project Items](../sharepoint/extending-sharepoint-project-items.md)   
 [Walkthrough: Extending a SharePoint Project Item Type](../sharepoint/walkthrough-extending-a-sharepoint-project-item-type.md)  
  
  