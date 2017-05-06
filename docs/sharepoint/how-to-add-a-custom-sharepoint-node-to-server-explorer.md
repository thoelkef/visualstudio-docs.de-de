---
title: "How to: Add a Custom SharePoint Node to Server Explorer"
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
  - "SharePoint development in Visual Studio, extending SharePoint Connections node in Server Explorer"
  - "SharePoint Connections [SharePoint development in Visual Studio], creating a new node type"
ms.assetid: b992a192-f926-45e6-9416-85ddfe1061d0
caps.latest.revision: 36
author: "kempb"
ms.author: "kempb"
manager: "ghogen"
caps.handback.revision: 35
---
# How to: Add a Custom SharePoint Node to Server Explorer
  Sie können benutzerdefinierte Knoten unter dem Knoten **SharePoint\-Verbindungen** in **Server\-Explorer** hinzufügen.  Dies ist hilfreich, wenn Sie zusätzliche SharePoint\-Komponenten anzeigen möchten, die standardmäßig in **Server\-Explorer** nicht angezeigt werden.  Weitere Informationen finden Sie unter [Extending the SharePoint Connections Node in Server Explorer](../sharepoint/extending-the-sharepoint-connections-node-in-server-explorer.md).  
  
 Um einen benutzerdefinierten Knoten hinzuzufügen, erstellen Sie zuerst eine Klasse, die den neuen Knoten definiert.  Erstellen Sie anschließend eine Erweiterung, die den Knoten als untergeordnetes Element eines vorhandenen Knotens hinzufügt.  
  
### So definieren Sie den neuen Knoten  
  
1.  Erstellen Sie ein Klassenbibliotheksprojekt.  
  
2.  Fügen Sie Verweise auf die folgenden Assemblys hinzu:  
  
    -   Microsoft.VisualStudio.SharePoint  
  
    -   Microsoft.VisualStudio.SharePoint.Explorer.Extensions  
  
    -   System.ComponentModel.Composition  
  
    -   System.Drawing  
  
3.  Erstellen Sie eine Klasse, die die <xref:Microsoft.VisualStudio.SharePoint.Explorer.IExplorerNodeTypeProvider>\-Schnittstelle implementiert.  
  
4.  Fügen Sie der Klasse die folgenden Attribute hinzu:  
  
    -   <xref:System.ComponentModel.Composition.ExportAttribute>.  Anhand dieses Attributs kann Visual Studio Ihre <xref:Microsoft.VisualStudio.SharePoint.Explorer.IExplorerNodeTypeProvider>\-Implementierung erkennen und laden.  Übergeben Sie den Typ <xref:Microsoft.VisualStudio.SharePoint.Explorer.IExplorerNodeTypeProvider> an den Attributkonstruktor.  
  
    -   <xref:Microsoft.VisualStudio.SharePoint.Explorer.ExplorerNodeTypeAttribute>.  In einer Knotendefinition gibt dieses Attribut den Zeichenfolgenbezeichner für den neuen Knoten an.  Es wird empfohlen, das Format *Unternehmensname*.*Knotenname* zu verwenden, um sicherzustellen, dass alle Knoten einen eindeutigen Bezeichner haben.  
  
5.  Verwenden Sie in der Implementierung der <xref:Microsoft.VisualStudio.SharePoint.Explorer.IExplorerNodeTypeProvider.InitializeType%2A>\-Methode Member des *typeDefinition*\-Parameters, um das Verhalten des neuen Knotens zu konfigurieren.  Dieser Parameter ist ein <xref:Microsoft.VisualStudio.SharePoint.Explorer.IExplorerNodeTypeDefinition>\-Objekt, das Zugriff auf die in der <xref:Microsoft.VisualStudio.SharePoint.Explorer.IExplorerNodeEvents>\-Schnittstelle definierten Ereignisse bietet.  
  
     Im folgenden Codebeispiel wird das Definieren eines neuen Knotens veranschaulicht.  In diesem Beispiel wird davon ausgegangen, dass das Projekt ein Symbol mit dem Namen CustomChildNodeIcon als eingebettete Ressource enthält.  
  
     [!code-csharp[SPExtensibility.ProjectSystemExtension.General#6](../snippets/csharp/VS_Snippets_OfficeSP/spextensibility.projectsystemextension.general/cs/extension/serverexplorernode.cs#6)]
     [!code-vb[SPExtensibility.ProjectSystemExtension.General#6](../snippets/visualbasic/VS_Snippets_OfficeSP/spextensibility.projectsystemextension.general/vb/extension/serverexplorernode.vb#6)]  
  
### So fügen Sie den neuen Knoten als untergeordnetes Element eines vorhandenen Knotens hinzu  
  
1.  Erstellen Sie im Projekt der Knotendefinition eine Klasse, die die <xref:Microsoft.VisualStudio.SharePoint.Explorer.IExplorerNodeTypeExtension>\-Schnittstelle implementiert.  
  
2.  Fügen Sie der Klasse das <xref:System.ComponentModel.Composition.ExportAttribute>\-Attribut hinzu.  Anhand dieses Attributs kann Visual Studio Ihre <xref:Microsoft.VisualStudio.SharePoint.Explorer.IExplorerNodeTypeExtension>\-Implementierung erkennen und laden.  Übergeben Sie den <xref:Microsoft.VisualStudio.SharePoint.Explorer.IExplorerNodeTypeExtension>\-Typ an den Attributkonstruktor.  
  
3.  Fügen Sie der Klasse das <xref:Microsoft.VisualStudio.SharePoint.Explorer.ExplorerNodeTypeAttribute>\-Attribut hinzu.  In einer Knotenerweiterung gibt dieses Attribut den Zeichenfolgenbezeichner für den Knotentyp an, den Sie erweitern möchten.  
  
     Übergeben Sie einen der folgenden Enumerationswerte an den Attributkonstruktor, um einen integrierten, von Visual Studio bereitgestellten Knotentyp anzugeben:  
  
    -   <xref:Microsoft.VisualStudio.SharePoint.Explorer.ExplorerNodeTypes>: Geben Sie mithilfe dieser Werte Website\-Verbindungsknoten \(die Knoten, von denen Website\-URLs angezeigt werden\), Websiteknoten oder alle anderen übergeordneten Knoten im **Server\-Explorer** an.  
  
    -   <xref:Microsoft.VisualStudio.SharePoint.Explorer.Extensions.ExtensionNodeTypes>: Verwenden Sie diese Werte, um einen der integrierten Knoten anzugeben, die auf einer SharePoint\-Website eine einzelne Komponente darstellen, z. B. ein Knoten, der eine Liste, ein Feld oder einen Inhaltstyp darstellt.  
  
4.  Behandeln Sie in der Implementierung der <xref:Microsoft.VisualStudio.SharePoint.Explorer.IExplorerNodeTypeExtension.Initialize%2A>\-Methode das <xref:Microsoft.VisualStudio.SharePoint.Explorer.IExplorerNodeEvents.NodeChildrenRequested>\-Ereignis des <xref:Microsoft.VisualStudio.SharePoint.Explorer.IExplorerNodeType>\-Parameters.  
  
5.  Fügen Sie den neuen Knoten im <xref:Microsoft.VisualStudio.SharePoint.Explorer.IExplorerNodeEvents.NodeChildrenRequested>\-Ereignishandler der Auflistung der untergeordneten Knoten des <xref:Microsoft.VisualStudio.SharePoint.Explorer.ExplorerNodeEventArgs.Node%2A>\-Objekts hinzu, das vom Ereignisargumentparameter verfügbar gemacht wird.  
  
     Im folgenden Codebeispiel wird veranschaulicht, wie der neue Knoten als untergeordnetes Element des SharePoint\-Websiteknotens im **Server\-Explorer** hinzugefügt wird.  
  
     [!code-csharp[SPExtensibility.ProjectSystemExtension.General#7](../snippets/csharp/VS_Snippets_OfficeSP/spextensibility.projectsystemextension.general/cs/extension/serverexplorernode.cs#7)]
     [!code-vb[SPExtensibility.ProjectSystemExtension.General#7](../snippets/visualbasic/VS_Snippets_OfficeSP/spextensibility.projectsystemextension.general/vb/extension/serverexplorernode.vb#7)]  
  
## Vollständiges Beispiel  
 Das folgende Beispiel enthält den vollständigen Code, den Sie benötigen, um einen einfachen Knoten zu definieren und als untergeordnetes Element des SharePoint\-Websiteknotens im **Server\-Explorer** hinzuzufügen.  
  
 [!code-csharp[SPExtensibility.ProjectSystemExtension.General#5](../snippets/csharp/VS_Snippets_OfficeSP/spextensibility.projectsystemextension.general/cs/extension/serverexplorernode.cs#5)]
 [!code-vb[SPExtensibility.ProjectSystemExtension.General#5](../snippets/visualbasic/VS_Snippets_OfficeSP/spextensibility.projectsystemextension.general/vb/extension/serverexplorernode.vb#5)]  
  
## Kompilieren des Codes  
 In diesem Beispiel wird davon ausgegangen, dass das Projekt ein Symbol mit dem Namen CustomChildNodeIcon als eingebettete Ressource enthält.  Für dieses Beispiel sind außerdem Verweise auf die folgenden Assemblys erforderlich:  
  
-   Microsoft.VisualStudio.SharePoint  
  
-   System.ComponentModel.Composition  
  
-   System.Drawing  
  
## Bereitstellen der Erweiterung  
 Um die **Server\-Explorer**\-Erweiterung bereitzustellen, erstellen Sie ein [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)]\-Erweiterungspaket \(VSIX\) für die Assembly und alle weiteren Dateien, die Sie mit der Erweiterung verteilen möchten.  Weitere Informationen erhalten Sie unter [Deploying Extensions for the SharePoint Tools in Visual Studio](../sharepoint/deploying-extensions-for-the-sharepoint-tools-in-visual-studio.md).  
  
## Siehe auch  
 [Extending the SharePoint Connections Node in Server Explorer](../sharepoint/extending-the-sharepoint-connections-node-in-server-explorer.md)   
 [How to: Extend a SharePoint Node in Server Explorer](../sharepoint/how-to-extend-a-sharepoint-node-in-server-explorer.md)   
 [Walkthrough: Extending Server Explorer to Display Web Parts](../sharepoint/walkthrough-extending-server-explorer-to-display-web-parts.md)  
  
  