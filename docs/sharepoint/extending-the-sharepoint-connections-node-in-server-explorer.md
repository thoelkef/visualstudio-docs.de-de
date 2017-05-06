---
title: "Extending the SharePoint Connections Node in Server Explorer"
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
  - "SharePoint Connections [SharePoint development in Visual Studio], creating a new node type"
ms.assetid: 8bfa5950-0ef4-4417-9538-cc8a5a1c35e2
caps.latest.revision: 27
author: "kempb"
ms.author: "kempb"
manager: "ghogen"
caps.handback.revision: 26
---
# Extending the SharePoint Connections Node in Server Explorer
  In Visual Studio können Sie eine Verbindung mit lokalen SharePoint\-Websites der SharePoint\-Website auf dem Entwicklungscomputer herstellen, indem Sie den **SharePoint\-Verbindungen** Knoten im Fenster**Server\-Explorer** verwenden.  Dieser Knoten zeigt viele der Komponenten lokaler SharePoint\-Websites in einer hierarchischen Strukturansicht an.  Sie können z. B. die Listen, Dokumentbibliotheken und Inhaltstypen auf lokalen Websites anzeigen. Weitere Informationen zum Herstellen einer Verbindung mit lokalen SharePoint\-Websites mit dem **Server\-Explorer** finden Sie unter [Durchsuchen von SharePoint-Verbindungen mit dem Server-Explorer](../sharepoint/browsing-sharepoint-connections-using-server-explorer.md).  
  
 Sie können den Knoten **SharePoint\-Verbindungen** erweitern, indem Sie Erweiterungen für vorhandene Knoten erstellen oder benutzerdefinierte Knotentypen erstellen und der Knotenhierarchie hinzufügen.  
  
## Aufgaben zum Erweitern des Knotens "SharePoint\-Verbindungen"  
 Erstellen Sie zum Erweitern eines vorhandenen Knotens eine Visual Studio\-Erweiterung, die die <xref:Microsoft.VisualStudio.SharePoint.Explorer.IExplorerNodeTypeExtension>\-Schnittstelle implementiert.  Wenn Sie einen Knoten erweitern, können Sie ihm Funktionen hinzufügen, z. B. eigene Kontextmenüelemente oder benutzerdefinierte Eigenschaften.  Weitere Informationen finden Sie unter [How to: Extend a SharePoint Node in Server Explorer](../sharepoint/how-to-extend-a-sharepoint-node-in-server-explorer.md).  
  
 Erstellen Sie zum Erstellen eines benutzerdefinierten Knotentyps eine Visual Studio\-Erweiterung, die die <xref:Microsoft.VisualStudio.SharePoint.Explorer.IExplorerNodeTypeProvider>\-Schnittstelle implementiert.  Erstellen Sie einen benutzerdefinierten Knoten, wenn Sie Komponenten von SharePoint\-Websites anzeigen möchten, die in **Server\-Explorer** standardmäßig nicht angezeigt werden.  Zum Beispiel zeigt **Server\-Explorer** den Webpartkatalog einer SharePoint\-Website standardmäßig nicht an, Sie können aber einen benutzerdefinierten Knoten für die Anzeige hinzufügen.  Weitere Informationen finden Sie unter [How to: Add a Custom SharePoint Node to Server Explorer](../sharepoint/how-to-add-a-custom-sharepoint-node-to-server-explorer.md) und [Walkthrough: Extending Server Explorer to Display Web Parts](../sharepoint/walkthrough-extending-server-explorer-to-display-web-parts.md).  
  
## Hinzufügen von benutzerdefinierten Eigenschaften zu Knoten  
 Wenn Sie einen Knoten erweitern oder einen benutzerdefinierten Knotentyp erstellen, können Sie dem Knoten benutzerdefinierte Eigenschaften hinzufügen.  Die Eigenschaften erscheinen bei Auswahl des Knotens im Fenster **Eigenschaften**.  
  
 Zwei Typen von benutzerdefinierten Eigenschaften können einem Knoten hinzugefügt werden:  
  
-   Eigenschaften, die einen Satz schreibgeschützter Daten von der SharePoint\-Website anzeigen.  Die Daten beschreiben die vom Knoten dargestellte SharePoint\-Komponente.  Eine exemplarische Vorgehensweise zur Veranschaulichung finden Sie unter [Walkthrough: Extending Server Explorer to Display Web Parts](../sharepoint/walkthrough-extending-server-explorer-to-display-web-parts.md).  
  
-   Eigenschaften, die benutzerdefinierte Daten mit Lese\-\/Schreibzugriff anzeigen.  Ein Codebeispiel, das diese Vorgehensweise veranschaulicht, finden Sie unter [How to: Extend a SharePoint Node in Server Explorer](../sharepoint/how-to-extend-a-sharepoint-node-in-server-explorer.md).  
  
## Abrufen von Daten für integrierte Knoten  
 Alle in Visual Studio verfügbaren integrierten Knoten enthalten einige Daten zu der von ihnen dargestellten SharePoint\-Komponente.  Ein Knoten, der eine Liste auf der SharePoint\-Website darstellt, enthält z. B. Daten zur Liste wie den Titel und die URL der Standardansicht für die Liste.  
  
 Um auf diese Daten zuzugreifen, rufen Sie ein Datenobjekt von der <xref:Microsoft.VisualStudio.SharePoint.IAnnotatedObject.Annotations%2A>\-Eigenschaft des <xref:Microsoft.VisualStudio.SharePoint.Explorer.IExplorerNode>\-Objekts ab, die den jeweiligen Knoten darstellt.  Der Typ des Datenobjekts hängt vom Knotentyp ab.  
  
 Im folgenden Codebeispiel wird veranschaulicht, wie das Datenobjekt für einen Listenknoten abgerufen wird.  Unter [How to: Get Data for a Built-In SharePoint Node in Server Explorer](../sharepoint/how-to-get-data-for-a-built-in-sharepoint-node-in-server-explorer.md) wird dieses Beispiel noch einmal in einem umfassenderen Beispiel veranschaulicht.  
  
 [!code-csharp[SPExtensibility.ProjectSystemExtension.General#11](../snippets/csharp/VS_Snippets_OfficeSP/spextensibility.projectsystemextension.general/cs/extension/serverexplorerextensionnodeinfo.cs#11)]
 [!code-vb[SPExtensibility.ProjectSystemExtension.General#11](../snippets/visualbasic/VS_Snippets_OfficeSP/spextensibility.projectsystemextension.general/vb/extension/serverexplorerextensionnodeinfo.vb#11)]  
  
 In der folgenden Tabelle sind die Datenobjekttypen für jeden integrierten Knotentyp aufgeführt.  
  
|Knotentyp|Datenobjekttyp|  
|---------------|--------------------|  
|SharePoint\-Websiteknoten|<xref:Microsoft.VisualStudio.SharePoint.Explorer.IExplorerSiteNodeInfo>|  
|Inhaltstyp|<xref:Microsoft.VisualStudio.SharePoint.Explorer.Extensions.IContentTypeNodeInfo>|  
|Feature|<xref:Microsoft.VisualStudio.SharePoint.Explorer.Extensions.IFeatureNodeInfo>|  
|Feld|<xref:Microsoft.VisualStudio.SharePoint.Explorer.Extensions.IFieldNodeInfo>|  
|List|<xref:Microsoft.VisualStudio.SharePoint.Explorer.Extensions.IListNodeInfo>|  
|Listenvorlage|<xref:Microsoft.VisualStudio.SharePoint.Explorer.Extensions.IListTemplateNodeInfo>|  
|Listenansicht \(Microsoft.SharePoint.SPView\)|<xref:Microsoft.VisualStudio.SharePoint.Explorer.Extensions.IListViewNodeInfo>|  
|Workflowzuordnung|<xref:Microsoft.VisualStudio.SharePoint.Explorer.Extensions.IWorkflowAssociationNodeInfo>|  
|Workflowvorlage|<xref:Microsoft.VisualStudio.SharePoint.Explorer.Extensions.IWorkflowTemplateNodeInfo>|  
  
 Weitere Informationen über die Verwendung der <xref:Microsoft.VisualStudio.SharePoint.IAnnotatedObject.Annotations%2A>\-Eigenschaft finden Sie unter [Associating Custom Data with SharePoint Tools Extensions](../sharepoint/associating-custom-data-with-sharepoint-tools-extensions.md).  
  
## Siehe auch  
 [Walkthrough: Extending Server Explorer to Display Web Parts](../sharepoint/walkthrough-extending-server-explorer-to-display-web-parts.md)   
 [How to: Extend a SharePoint Node in Server Explorer](../sharepoint/how-to-extend-a-sharepoint-node-in-server-explorer.md)   
 [How to: Add a Custom SharePoint Node to Server Explorer](../sharepoint/how-to-add-a-custom-sharepoint-node-to-server-explorer.md)   
 [How to: Get Data for a Built-In SharePoint Node in Server Explorer](../sharepoint/how-to-get-data-for-a-built-in-sharepoint-node-in-server-explorer.md)   
 [Associating Custom Data with SharePoint Tools Extensions](../sharepoint/associating-custom-data-with-sharepoint-tools-extensions.md)   
 [Durchsuchen von SharePoint-Verbindungen mit dem Server-Explorer](../sharepoint/browsing-sharepoint-connections-using-server-explorer.md)   
 [Extending the SharePoint Tools in Visual Studio](../sharepoint/extending-the-sharepoint-tools-in-visual-studio.md)  
  
  