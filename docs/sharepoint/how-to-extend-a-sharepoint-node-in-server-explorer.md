---
title: "How to: Extend a SharePoint Node in Server Explorer"
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
  - "SharePoint Connections [SharePoint development in Visual Studio], extending a node"
  - "SharePoint development in Visual Studio, extending SharePoint Connections node in Server Explorer"
ms.assetid: 5e443950-12e6-40d1-864b-c384b6be4ce4
caps.latest.revision: 16
author: "kempb"
ms.author: "kempb"
manager: "ghogen"
caps.handback.revision: 15
---
# How to: Extend a SharePoint Node in Server Explorer
  Sie können benutzerdefinierte Knoten im **Server\-Explorer** unter dem Knoten **SharePoint\-Verbindungen** erweitern.  Dies ist beim Hinzufügen von neuen untergeordneten Knoten, Kontextmenüelementen oder Eigenschaften zu einem vorhandenen Knoten hilfreich.  Weitere Informationen finden Sie unter [Extending the SharePoint Connections Node in Server Explorer](../sharepoint/extending-the-sharepoint-connections-node-in-server-explorer.md).  
  
### So erweitern Sie einen SharePoint\-Knoten im Server\-Explorer  
  
1.  Erstellen Sie ein Klassenbibliotheksprojekt.  
  
2.  Fügen Sie Verweise auf die folgenden Assemblys hinzu:  
  
    -   Microsoft.VisualStudio.SharePoint  
  
    -   Microsoft.VisualStudio.SharePoint.Explorer.Extensions  
  
    -   System.ComponentModel.Composition  
  
3.  Erstellen Sie eine Klasse, die die <xref:Microsoft.VisualStudio.SharePoint.Explorer.IExplorerNodeTypeExtension>\-Schnittstelle implementiert.  
  
4.  Fügen Sie der Klasse das <xref:System.ComponentModel.Composition.ExportAttribute>\-Attribut hinzu.  Anhand dieses Attributs kann Visual Studio Ihre <xref:Microsoft.VisualStudio.SharePoint.Explorer.IExplorerNodeTypeExtension>\-Implementierung erkennen und laden.  Übergeben Sie den <xref:Microsoft.VisualStudio.SharePoint.Explorer.IExplorerNodeTypeExtension>\-Typ an den Attributkonstruktor.  
  
5.  Fügen Sie der Klasse das <xref:Microsoft.VisualStudio.SharePoint.Explorer.ExplorerNodeTypeAttribute>\-Attribut hinzu.  Dieses Attribut gibt den Zeichenfolgenbezeichner für den Knotentyp an, den Sie erweitern möchten.  
  
     Übergeben Sie einen der folgenden Enumerationswerte an den Attributkonstruktor, um einen integrierten, von Visual Studio bereitgestellten Knotentyp anzugeben:  
  
    -   <xref:Microsoft.VisualStudio.SharePoint.Explorer.ExplorerNodeTypes>: Geben Sie mithilfe dieser Werte Website\-Verbindungsknoten \(die Knoten, von denen Website\-URLs angezeigt werden\), Websiteknoten oder alle anderen übergeordneten Knoten im **Server\-Explorer** an.  
  
    -   <xref:Microsoft.VisualStudio.SharePoint.Explorer.Extensions.ExtensionNodeTypes>: Verwenden Sie diese Werte, um einen der integrierten Knoten anzugeben, die auf einer SharePoint\-Website eine einzelne Komponente darstellen, z. B. ein Knoten, der eine Liste, ein Feld oder einen Inhaltstyp darstellt.  
  
6.  Verwenden Sie in der Implementierung der <xref:Microsoft.VisualStudio.SharePoint.Explorer.IExplorerNodeTypeExtension.Initialize%2A>\-Methode Member des *nodeType*\-Parameters, um dem Knoten Funktionen hinzuzufügen.  Dieser Parameter ist ein <xref:Microsoft.VisualStudio.SharePoint.Explorer.IExplorerNodeType>\-Objekt, das Zugriff auf die in der <xref:Microsoft.VisualStudio.SharePoint.Explorer.IExplorerNodeEvents>\-Schnittstelle definierten Ereignisse bietet.  Sie können z. B. folgende Ereignisse bearbeiten:  
  
    -   <xref:Microsoft.VisualStudio.SharePoint.Explorer.IExplorerNodeEvents.NodeChildrenRequested>: Bearbeiten Sie dieses Ereignis, um dem Knoten neue untergeordnete Knoten hinzuzufügen.  Weitere Informationen erhalten Sie unter [How to: Add a Custom SharePoint Node to Server Explorer](../sharepoint/how-to-add-a-custom-sharepoint-node-to-server-explorer.md).  
  
    -   <xref:Microsoft.VisualStudio.SharePoint.Explorer.IExplorerNodeEvents.NodeMenuItemsRequested>: Bearbeiten Sie dieses Ereignis, um dem Knoten ein benutzerdefiniertes Kontextmenüelement hinzuzufügen.  
  
    -   <xref:Microsoft.VisualStudio.SharePoint.Explorer.IExplorerNodeEvents.NodePropertiesRequested>: Bearbeiten Sie dieses Ereignis, um dem Knoten benutzerdefinierte Eigenschaften hinzuzufügen.  Die Eigenschaften erscheinen bei Auswahl des Knotens im Fenster **Eigenschaften**.  
  
## Beispiel  
 Im folgenden Codebeispiel wird die Erstellung zweier unterschiedlicher Typen von Knotenerweiterungen veranschaulicht:  
  
-   Eine Erweiterung, die SharePoint\-Websiteknoten ein Kontextmenüelement hinzufügt.  Beim Klicken auf das Menüelement wird der Name des angeklickten Knotens angezeigt.  
  
-   Eine Erweiterung, die jedem Knoten, der ein Feld mit dem Namen **Text** darstellt, eine benutzerdefinierte Eigenschaft mit dem Namen **ContosoExampleProperty** hinzufügt.  
  
 [!code-csharp[SPExtensibility.ProjectSystemExtension.General#9](../snippets/csharp/VS_Snippets_OfficeSP/spextensibility.projectsystemextension.general/cs/extension/serverexplorerextension.cs#9)]
 [!code-vb[SPExtensibility.ProjectSystemExtension.General#9](../snippets/visualbasic/VS_Snippets_OfficeSP/spextensibility.projectsystemextension.general/vb/extension/serverexplorerextension.vb#9)]  
  
 Diese Erweiterung fügt Knoten eine bearbeitbare Zeichenfolgeneigenschaft hinzu.  Sie können auch benutzerdefinierte Eigenschaften erstellen, die schreibgeschützte Daten auf dem SharePoint\-Server anzeigen.  Ein Beispiel, das die Vorgehensweise veranschaulicht, finden Sie unter [Walkthrough: Extending Server Explorer to Display Web Parts](../sharepoint/walkthrough-extending-server-explorer-to-display-web-parts.md).  
  
## Kompilieren des Codes  
 Für dieses Beispiel sind Verweise auf die folgenden Assemblys erforderlich:  
  
-   Microsoft.VisualStudio.SharePoint  
  
-   Microsoft.VisualStudio.SharePoint.Explorer.Extensions  
  
-   System.ComponentModel.Composition  
  
-   System.Windows.Forms  
  
## Bereitstellen der Erweiterung  
 Um die **Server\-Explorer**\-Erweiterung bereitzustellen, erstellen Sie ein [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)]\-Erweiterungspaket \(VSIX\) für die Assembly und alle weiteren Dateien, die Sie mit der Erweiterung verteilen möchten.  Weitere Informationen erhalten Sie unter [Deploying Extensions for the SharePoint Tools in Visual Studio](../sharepoint/deploying-extensions-for-the-sharepoint-tools-in-visual-studio.md).  
  
## Siehe auch  
 [How to: Add a Custom SharePoint Node to Server Explorer](../sharepoint/how-to-add-a-custom-sharepoint-node-to-server-explorer.md)   
 [Extending the SharePoint Connections Node in Server Explorer](../sharepoint/extending-the-sharepoint-connections-node-in-server-explorer.md)   
 [Walkthrough: Extending Server Explorer to Display Web Parts](../sharepoint/walkthrough-extending-server-explorer-to-display-web-parts.md)   
 [Associating Custom Data with SharePoint Tools Extensions](../sharepoint/associating-custom-data-with-sharepoint-tools-extensions.md)  
  
  