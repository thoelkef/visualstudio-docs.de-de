---
title: "Saving Data in Extensions of the SharePoint Project System"
ms.custom: ""
ms.date: "02/02/2017"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "office-development"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "SharePoint project items, saving string data"
  - "project items [SharePoint development in Visual Studio], saving string data"
  - "projects [SharePoint development in Visual Studio], saving string data"
  - "SharePoint projects, saving string data"
ms.assetid: 903b9da7-2eea-404c-9a7a-7bc15cb90d6c
caps.latest.revision: 13
author: "kempb"
ms.author: "kempb"
manager: "ghogen"
caps.handback.revision: 12
---
# Saving Data in Extensions of the SharePoint Project System
  Wenn Sie das SharePoint\-Projektsystem erweitern, können Sie Zeichenfolgendaten speichern, die auch nach Abschluss eines SharePoint\-Projekts erhalten bleiben.  Die Daten werden i. d. R. mit einem bestimmten Projektelement oder mit dem Projekt selbst verknüpft.  
  
 Wenn Sie über Daten verfügen, die nicht beibehalten werden müssen, können Sie die Daten jedem Objekt im SharePoint\-Tools\-Objektmodell hinzufügen, das die <xref:Microsoft.VisualStudio.SharePoint.IAnnotatedObject>\-Schnittstelle implementiert.  Weitere Informationen finden Sie unter [Associating Custom Data with SharePoint Tools Extensions](../sharepoint/associating-custom-data-with-sharepoint-tools-extensions.md).  
  
## Speichern von einem Projektelement zugeordneten Daten  
 Wenn Sie über Daten verfügen, die mit einem bestimmten SharePoint\-Projektelement verknüpft sind, beispielsweise der Wert einer Eigenschaft, die einem Projektelement hinzugefügt wird, können Sie die Daten in einer SPDATA\-Datei für das Projektelement speichern.  Verwenden Sie dazu die <xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectItem.ExtensionData%2A>\-Eigenschaft eines <xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectItem>\-Objekts.  Daten, die Sie dieser Eigenschaft hinzufügen, werden im **ExtensionData**\-Element in der SPDATA\-Datei für das Projektelement gespeichert.  Weitere Informationen finden Sie unter [ExtensionData Element](../sharepoint/extensiondata-element.md).  
  
 Im folgenden Codebeispiel wird veranschaulicht, wie die <xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectItem.ExtensionData%2A>\-Eigenschaft verwendet wird, um den Wert einer Zeichenfolgeneigenschaft zu speichern, die in einem benutzerdefinierten SharePoint\-Projektelementtyp definiert ist.  Unter [How to: Add a Property to a Custom SharePoint Project Item Type](../sharepoint/how-to-add-a-property-to-a-custom-sharepoint-project-item-type.md) wird dieses Beispiel noch einmal in einem umfassenderen Beispiel veranschaulicht.  
  
 [!code-csharp[SPExtensibility.ProjectItemExtension.MenuAndProperty#14](../snippets/csharp/VS_Snippets_OfficeSP/spextensibility.projectitemextension.menuandproperty/cs/extension/projectitemtypeproperty.cs#14)]
 [!code-vb[SPExtensibility.ProjectItemExtension.MenuAndProperty#14](../snippets/visualbasic/VS_Snippets_OfficeSP/spextensibility.projectitemextension.menuandproperty/vb/extension/projectitemtypeproperty.vb#14)]  
  
## Speichern von einem Projekt zugeordneten Daten  
 Wenn Sie über Daten auf Projektebene verfügen, beispielsweise der Wert einer Eigenschaft, die Sie SharePoint\-Projekten hinzufügen, können Sie die Daten in der Projektdatei \(.csproj oder .vbproj\) oder in der Benutzeroptionsdatei für Projekte \(.scproj.user oder .vbproj.user\) speichern.  Die Datei, die Sie auswählen, um die Daten speichern, ist abhängig davon, wie die Daten verwendet werden sollen:  
  
-   Wenn Sie die Daten für alle Entwicklern verfügbar machen wollen, die das SharePoint\-Projekt öffnen, speichern Sie die Daten in der Projektdatei.  Diese Datei wird immer in die Quellcodeverwaltungs\-Datenbanken eingecheckt, sodass die Daten in dieser Datei für andere Entwicklern zur Verfügung stehen, die das Projekt auschecken.  
  
-   Wenn die Daten nur für den aktuellen Entwickler verfügbar sein sollen, der das SharePoint\-Projekt in Visual Studio geöffnet hat, speichern Sie die Daten in der Benutzeroptionsdatei für Projekte.  Diese Datei i. d. R. nicht in die Quellcodeverwaltungs\-Datenbanken eingecheckt, sodass die Daten in dieser Datei nicht für andere Entwicklern zur Verfügung stehen, die das Projekt auschecken.  
  
### Speichern von Daten in der Projektdatei  
 Um Daten in der Projektdatei zu speichern, konvertieren Sie ein <xref:Microsoft.VisualStudio.SharePoint.ISharePointProject>\-Objekt in ein <xref:Microsoft.VisualStudio.Shell.Interop.IVsBuildPropertyStorage>\-Objekt, und verwenden Sie anschließend die <xref:Microsoft.VisualStudio.Shell.Interop.IVsBuildPropertyStorage.SetPropertyValue%2A>\-Methode.  Im folgenden Codebeispiel wird veranschaulicht, wie diese Methode verwendet wird, um den Wert einer Projekteigenschaft in der Projektdatei zu speichern.  Unter [How to: Add a Property to SharePoint Projects](../sharepoint/how-to-add-a-property-to-sharepoint-projects.md) wird dieses Beispiel noch einmal in einem umfassenderen Beispiel veranschaulicht.  
  
 [!code-csharp[SpExt_SPCustomPrjProperty#3](../snippets/csharp/VS_Snippets_OfficeSP/spext_spcustomprjproperty/cs/customspproperty/customproperty.cs#3)]
 [!code-vb[SpExt_SPCustomPrjProperty#3](../snippets/visualbasic/VS_Snippets_OfficeSP/spext_spcustomprjproperty/vb/customspproperty/customproperty.vb#3)]  
  
 Weitere Informationen zum Konvertieren von <xref:Microsoft.VisualStudio.SharePoint.ISharePointProject>\-Objekten in andere Typen im Automatisierungsobjektmodell oder Integrationsobjektmodell von Visual Studio finden Sie unter [Converting Between SharePoint Project System Types and Other Visual Studio Project Types](../sharepoint/converting-between-sharepoint-project-system-types-and-other-visual-studio-project-types.md).  
  
### Speichern von Daten in der Benutzeroptionsdatei für Projekte  
 Mit der <xref:Microsoft.VisualStudio.SharePoint.ISharePointProject.ProjectUserFileData%2A>\-Eigenschaft eines <xref:Microsoft.VisualStudio.SharePoint.ISharePointProject>\-Objekts können Sie Daten in der Benutzeroptionsdatei für Projekte speichern.  Im folgenden Codebeispiel wird veranschaulicht, wie diese Eigenschaft verwendet wird, um den Wert einer Projekteigenschaft in der Benutzeroptionsdatei für Projekte zu speichern.  Unter [How to: Add a Property to SharePoint Projects](../sharepoint/how-to-add-a-property-to-sharepoint-projects.md) wird dieses Beispiel noch einmal in einem umfassenderen Beispiel veranschaulicht.  
  
 [!code-csharp[SpExt_SPCustomPrjProperty#2](../snippets/csharp/VS_Snippets_OfficeSP/spext_spcustomprjproperty/cs/customspproperty/customproperty.cs#2)]
 [!code-vb[SpExt_SPCustomPrjProperty#2](../snippets/visualbasic/VS_Snippets_OfficeSP/spext_spcustomprjproperty/vb/customspproperty/customproperty.vb#2)]  
  
## Siehe auch  
 [Extending the SharePoint Project System](../sharepoint/extending-the-sharepoint-project-system.md)   
 [Associating Custom Data with SharePoint Tools Extensions](../sharepoint/associating-custom-data-with-sharepoint-tools-extensions.md)   
 [Converting Between SharePoint Project System Types and Other Visual Studio Project Types](../sharepoint/converting-between-sharepoint-project-system-types-and-other-visual-studio-project-types.md)  
  
  