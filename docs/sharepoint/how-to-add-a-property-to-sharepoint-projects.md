---
title: "How to: Add a Property to SharePoint Projects"
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
  - "projects [SharePoint development in Visual Studio], extending"
  - "SharePoint development in Visual Studio, extending projects"
  - "SharePoint projects, extending"
ms.assetid: c5eb4900-c35f-490a-b856-bf167da2d293
caps.latest.revision: 17
author: "kempb"
ms.author: "kempb"
manager: "ghogen"
caps.handback.revision: 16
---
# How to: Add a Property to SharePoint Projects
  Mit einer Projekterweiterung können Sie SharePoint\-Projekten eine Eigenschaft hinzufügen.  Diese Eigenschaft wird im **Eigenschaftenfenster** angezeigt, wenn Sie das Projekt im **Projektmappen\-Explorer** auswählen.  
  
 Im Folgenden wird vorausgesetzt, dass bereits eine Projekterweiterung erstellt wurde.  Weitere Informationen finden Sie unter [How to: Create a SharePoint Project Extension](../sharepoint/how-to-create-a-sharepoint-project-extension.md).  
  
### So fügen Sie einem SharePoint\-Projekt eine Eigenschaft hinzu  
  
1.  Definieren Sie eine Klasse mit einer öffentlichen Eigenschaft, die die SharePoint\-Projekten hinzuzufügende Eigenschaft darstellt.  Wenn Sie mehrere Eigenschaften hinzufügen möchten, können Sie alle Eigenschaften in der gleichen Klasse oder in unterschiedlichen Klassen definieren.  
  
2.  Behandeln Sie in der <xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectExtension.Initialize%2A>\-Methode der <xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectExtension>\-Implementierung das <xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectEvents.ProjectPropertiesRequested>\-Ereignis des *projectService*\-Parameters.  
  
3.  Fügen Sie im Ereignishandler für das <xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectEvents.ProjectPropertiesRequested>\-Ereignis der <xref:Microsoft.VisualStudio.SharePoint.SharePointProjectPropertiesRequestedEventArgs.PropertySources%2A>\-Auflistung des Ereignisargumentparameters eine Instanz der Eigenschaftenklasse hinzu.  
  
## Beispiel  
 Im folgenden Codebeispiel wird veranschaulicht, wie SharePoint\-Projekten zwei Eigenschaften hinzugefügt werden.  Bei der einen Eigenschaft werden die Daten in der Benutzeroptionsdatei für Projekte beibehalten \(.vbproj.user\-Datei oder .csproj.user\-Datei\).  Bei der anderen Eigenschaft werden die Daten in der Projektdatei beibehalten \(CSPROJ\-Datei oder VBPROJ\-Datei\).  
  
 [!code-csharp[SpExt_SPCustomPrjProperty#1](../snippets/csharp/VS_Snippets_OfficeSP/spext_spcustomprjproperty/cs/customspproperty/customproperty.cs#1)]
 [!code-vb[SpExt_SPCustomPrjProperty#1](../snippets/visualbasic/VS_Snippets_OfficeSP/spext_spcustomprjproperty/vb/customspproperty/customproperty.vb#1)]  
  
### Grundlegendes zum Code  
 Damit stets die gleiche Instanz der `CustomProjectProperties`\-Klasse beim <xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectEvents.ProjectPropertiesRequested>\-Ereignis verwendet wird, wird im folgenden Codebeispiel das Eigenschaftenobjekt in der <xref:Microsoft.VisualStudio.SharePoint.IAnnotatedObject.Annotations%2A>\-Eigenschaft des Projekts gespeichert, sobald das Ereignis zum ersten Mal auftritt.  Vom Code wird dann jedes Mal, wenn das Ereignis auftritt, dieses Objekt abgerufen.  Weitere Informationen zur Verwendung der <xref:Microsoft.VisualStudio.SharePoint.IAnnotatedObject.Annotations%2A>\-Eigenschaft zum Zuordnen von Daten zu Projekten finden Sie unter [Associating Custom Data with SharePoint Tools Extensions](../sharepoint/associating-custom-data-with-sharepoint-tools-extensions.md).  
  
 Um Änderungen an Eigenschaftswerten beizubehalten, verwenden die **set**\-Accessoren für die Eigenschaften folgende APIs:  
  
-   `CustomUserFileProperty` speichert den Wert mit der <xref:Microsoft.VisualStudio.SharePoint.ISharePointProject.ProjectUserFileData%2A>\-Eigenschaft in der Benutzeroptionsdatei für Projekte.  
  
-   `CustomProjectFileProperty` speichert den Wert mit der <xref:Microsoft.VisualStudio.Shell.Interop.IVsBuildPropertyStorage.SetPropertyValue%2A>\-Methode in der Projektdatei.  
  
 Weitere Informationen zum Beibehalten von Daten in diesen Dateien finden Sie unter [Saving Data in Extensions of the SharePoint Project System](../sharepoint/saving-data-in-extensions-of-the-sharepoint-project-system.md).  
  
### Angeben des Verhaltens benutzerdefinierter Eigenschaften  
 Sie können definieren, wie eine benutzerdefinierte Eigenschaft angezeigt wird und sich im **Eigenschaftenfenster** verhält, indem Sie Attribute aus dem <xref:System.ComponentModel>\-Namespace auf die Eigenschaftendefinition anwenden.  Die folgenden Attribute sind in vielen Szenarien hilfreich:  
  
-   <xref:System.ComponentModel.DisplayNameAttribute>: Gibt den Namen der Eigenschaft an, die im **Eigenschaftenfenster** angezeigt wird.  
  
-   <xref:System.ComponentModel.DescriptionAttribute>: Gibt die Beschreibungszeichenfolge an, die bei Auswahl der Eigenschaft unten im **Eigenschaftenfenster** angezeigt wird.  
  
-   <xref:System.ComponentModel.DefaultValueAttribute>: Gibt den Standardwert für die Eigenschaft an.  
  
-   <xref:System.ComponentModel.TypeConverterAttribute>: Gibt eine benutzerdefinierte Konvertierung zwischen der Zeichenfolge, die im **Eigenschaftenfenster** angezeigt wird, und einem Eigenschaftswert an, der keine Zeichenfolge ist.  
  
-   <xref:System.ComponentModel.EditorAttribute>: Gibt einen benutzerdefinierten Editor zum Ändern der Eigenschaft an.  
  
## Kompilieren des Codes  
 Für dieses Beispiel sind Verweise auf die folgenden Assemblys erforderlich:  
  
-   Microsoft.VisualStudio.SharePoint  
  
-   Microsoft.VisualStudio.Shell  
  
-   Microsoft.VisualStudio.Shell.Interop  
  
-   Microsoft.VisualStudio.Shell.Interop.8.0  
  
-   System.ComponentModel.Composition  
  
## Bereitstellen der Erweiterung  
 Erstellen Sie ein [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)]\-Erweiterungspaket \(VSIX\) für die Assembly und alle weiteren Dateien, die Sie mit der Erweiterung verteilen möchten, um die Erweiterung bereitzustellen.  Weitere Informationen erhalten Sie unter [Deploying Extensions for the SharePoint Tools in Visual Studio](../sharepoint/deploying-extensions-for-the-sharepoint-tools-in-visual-studio.md).  
  
## Siehe auch  
 [Extending SharePoint Projects](../sharepoint/extending-sharepoint-projects.md)   
 [How to: Create a SharePoint Project Extension](../sharepoint/how-to-create-a-sharepoint-project-extension.md)   
 [How to: Add a Shortcut Menu Item to SharePoint Projects](../sharepoint/how-to-add-a-shortcut-menu-item-to-sharepoint-projects.md)   
 [Extending the SharePoint Project System](../sharepoint/extending-the-sharepoint-project-system.md)  
  
  