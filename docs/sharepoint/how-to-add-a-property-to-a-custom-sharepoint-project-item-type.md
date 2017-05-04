---
title: "How to: Add a Property to a Custom SharePoint Project Item Type | Microsoft Docs"
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
ms.assetid: 47e940f6-1779-4530-aea6-c43a370c544f
caps.latest.revision: 16
author: "kempb"
ms.author: "kempb"
manager: "ghogen"
caps.handback.revision: 15
---
# How to: Add a Property to a Custom SharePoint Project Item Type
  Wenn Sie einen benutzerdefinierten SharePoint\-Projektelementtyp definieren, können Sie dem Projektelement eine Eigenschaft hinzufügen.  Diese Eigenschaft wird im **Eigenschaftenfenster** angezeigt, wenn Sie das Projektelement im **Projektmappen\-Explorer** auswählen.  
  
 Im Folgenden wird angenommen, dass bereits ein eigener SharePoint\-Projektelementtyp definiert wurde.  Weitere Informationen finden Sie unter [How to: Define a SharePoint Project Item Type](../sharepoint/how-to-define-a-sharepoint-project-item-type.md).  
  
### So fügen Sie einer Definition eines Projektelementtyps eine Eigenschaft hinzu  
  
1.  Definieren Sie eine Klasse mit einer öffentlichen Eigenschaft, die der Eigenschaft entspricht, die Sie dem benutzerdefinierten Projektelementtyp hinzufügen.  Wenn Sie einem benutzerdefinierten Projektelementtyp mehrere Eigenschaften hinzufügen möchten, können Sie alle Eigenschaften in der gleichen Klasse oder in anderen Klassen definieren.  
  
2.  Behandeln Sie in der <xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectItemTypeProvider.InitializeType%2A>\-Methode der <xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectItemTypeProvider>\-Implementierung das <xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectItemEvents.ProjectItemPropertiesRequested>\-Ereignis des *projectItemTypeDefinition*\-Parameters.  
  
3.  Fügen Sie im Ereignishandler für das <xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectItemEvents.ProjectItemPropertiesRequested>\-Ereignis der <xref:Microsoft.VisualStudio.SharePoint.SharePointProjectItemPropertiesRequestedEventArgs.PropertySources%2A>\-Auflistung des Ereignisargumentparameters eine Instanz der benutzerdefinierten Eigenschaftenklasse hinzu.  
  
## Beispiel  
 Im folgenden Codebeispiel wird veranschaulicht, wie Sie einem benutzerdefinierten Projektelementtyp eine Eigenschaft mit dem Namen **Example Property** hinzufügen.  
  
 [!code-csharp[SPExtensibility.ProjectItemExtension.MenuAndProperty#11](../snippets/csharp/VS_Snippets_OfficeSP/spextensibility.projectitemextension.menuandproperty/cs/extension/projectitemtypeproperty.cs#11)]
 [!code-vb[SPExtensibility.ProjectItemExtension.MenuAndProperty#11](../snippets/visualbasic/VS_Snippets_OfficeSP/spextensibility.projectitemextension.menuandproperty/vb/extension/projectitemtypeproperty.vb#11)]  
  
### Grundlegendes zum Code  
 Damit stets die gleiche Instanz der `CustomProperties`\-Klasse beim <xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectItemEvents.ProjectItemPropertiesRequested>\-Ereignis verwendet wird, wird im folgenden Codebeispiel das Eigenschaftenobjekt in der <xref:Microsoft.VisualStudio.SharePoint.IAnnotatedObject.Annotations%2A>\-Eigenschaft des Projektelements gespeichert, sobald das Ereignis zum ersten Mal auftritt.  Vom Code wird dann jedes Mal, wenn das Ereignis auftritt, dieses Objekt abgerufen.  Weitere Informationen zur Verwendung der <xref:Microsoft.VisualStudio.SharePoint.IAnnotatedObject.Annotations%2A>\-Eigenschaft zum Speichern von Daten mit Projektelementen finden Sie unter [Associating Custom Data with SharePoint Tools Extensions](../sharepoint/associating-custom-data-with-sharepoint-tools-extensions.md).  
  
 Um die Änderungen des Eigenschaftswerts permanent zu speichern, speichert der **set**\-Accessor für `ExampleProperty` den neuen Wert in der <xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectItem.ExtensionData%2A>\-Eigenschaft des <xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectItem>\-Objekts, dem die Eigenschaft zugewiesen ist.  Weitere Informationen zur Verwendung der <xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectItem.ExtensionData%2A>\-Eigenschaft zum Speichern von Daten mit Projektelementen finden Sie unter [Saving Data in Extensions of the SharePoint Project System](../sharepoint/saving-data-in-extensions-of-the-sharepoint-project-system.md).  
  
### Angeben des Verhaltens benutzerdefinierter Eigenschaften  
 Sie können definieren, wie eine benutzerdefinierte Eigenschaft angezeigt wird und sich im **Eigenschaftenfenster** verhält, indem Sie Attribute aus dem <xref:System.ComponentModel>\-Namespace auf die Eigenschaftendefinition anwenden.  Die folgenden Attribute sind in vielen Szenarien hilfreich:  
  
-   <xref:System.ComponentModel.DisplayNameAttribute>: Gibt den Namen der Eigenschaft an, die im **Eigenschaftenfenster** angezeigt wird.  
  
-   <xref:System.ComponentModel.DescriptionAttribute>: Gibt die Beschreibungszeichenfolge an, die bei Auswahl der Eigenschaft unten im **Eigenschaftenfenster** angezeigt wird.  
  
-   <xref:System.ComponentModel.DefaultValueAttribute>: Gibt den Standardwert für die Eigenschaft an.  
  
-   <xref:System.ComponentModel.TypeConverterAttribute>: Gibt eine benutzerdefinierte Konvertierung zwischen der Zeichenfolge, die im **Eigenschaftenfenster** angezeigt wird, und einem Eigenschaftswert an, der keine Zeichenfolge ist.  
  
-   <xref:System.ComponentModel.EditorAttribute>: Gibt einen benutzerdefinierten Editor zum Ändern der Eigenschaft an.  
  
## Kompilieren des Codes  
 Für diese Codebeispiele ist ein Klassenbibliotheksprojekt mit Verweisen auf die folgenden Assemblys erforderlich:  
  
-   Microsoft.VisualStudio.SharePoint  
  
-   System.ComponentModel.Composition  
  
## Bereitstellen des Projektelements  
 Um Ihr Projektelement anderen Entwicklern zur Verfügung zu stellen, können Sie eine Projektvorlage oder eine Projektelementvorlage erstellen.  Weitere Informationen finden Sie unter [Creating Item Templates and Project Templates for SharePoint Project Items](../sharepoint/creating-item-templates-and-project-templates-for-sharepoint-project-items.md).  
  
 Erstellen Sie zum Bereitstellen des Projektelements ein [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)]\-Erweiterungspaket \(VSIX\) für die Assembly, die Vorlage und alle weiteren Dateien, die Sie mit dem Projektelement verteilen möchten.  Weitere Informationen erhalten Sie unter [Deploying Extensions for the SharePoint Tools in Visual Studio](../sharepoint/deploying-extensions-for-the-sharepoint-tools-in-visual-studio.md).  
  
## Siehe auch  
 [How to: Define a SharePoint Project Item Type](../sharepoint/how-to-define-a-sharepoint-project-item-type.md)   
 [How to: Add a Shortcut Menu Item to a Custom SharePoint Project Item Type](../sharepoint/how-to-add-a-shortcut-menu-item-to-a-custom-sharepoint-project-item-type.md)   
 [Defining Custom SharePoint Project Item Types](../sharepoint/defining-custom-sharepoint-project-item-types.md)  
  
  