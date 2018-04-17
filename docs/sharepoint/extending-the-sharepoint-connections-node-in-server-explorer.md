---
title: Erweitern des SharePoint-Verbindungsknotens im Server-Explorer | Microsoft Docs
ms.custom: ''
ms.date: 02/02/2017
ms.technology:
- office-development
ms.topic: conceptual
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- SharePoint Connections [SharePoint development in Visual Studio], extending a node
- SharePoint development in Visual Studio, extending SharePoint Connections node in Server Explorer
- SharePoint Connections [SharePoint development in Visual Studio], creating a new node type
author: TerryGLee
ms.author: tglee
manager: douge
ms.workload:
- office
ms.openlocfilehash: 0eabca43f604d92ecab78dccae281a450f7c0400
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/16/2018
---
# <a name="extending-the-sharepoint-connections-node-in-server-explorer"></a>Erweitern des SharePoint-Verbindungsknotens im Server-Explorer
  In Visual Studio können Sie mit der lokalen SharePoint-Websites auf dem Entwicklungscomputer verbinden, mithilfe der **SharePoint-Verbindungen** Knoten in der**Server-Explorer** Fenster. Dieser Knoten zeigt viele der Komponenten der lokalen SharePoint-Websites in einer hierarchischen Strukturansicht an. Beispielsweise können Sie die Listen, Dokumentbibliotheken und Inhaltstypen auf lokalen Standorten anzeigen. Weitere Informationen zur Verwendung von **Server-Explorer** zur Verbindung mit lokalen SharePoint-Websites finden Sie unter [Durchsuchen von SharePoint-Verbindungen mithilfe von Server-Explorer](../sharepoint/browsing-sharepoint-connections-using-server-explorer.md).  
  
 Sie erweitern die **SharePoint-Verbindungen** Knoten durch Erstellen von Erweiterungen für vorhandene Knoten oder durch Erstellen eines benutzerdefinierten Knotentyps und der Hierarchie von Knoten hinzufügen.  
  
## <a name="tasks-for-extending-the-sharepoint-connections-node"></a>Aufgaben zum Erweitern des SharePoint-Verbindungsknotens  
 Um einen vorhandenen Knoten zu erweitern, erstellen Sie eine Visual Studio-Erweiterung, implementiert die <xref:Microsoft.VisualStudio.SharePoint.Explorer.IExplorerNodeTypeExtension> Schnittstelle. Wenn Sie einen Knoten erweitern, können Sie Funktionen auf den Knoten wie Kontextmenüeinträge oder benutzerdefinierte Eigenschaften hinzufügen. Weitere Informationen finden Sie unter [wie: Erweitern eines SharePoint-Knotens im Server-Explorer](../sharepoint/how-to-extend-a-sharepoint-node-in-server-explorer.md).  
  
 Um einen benutzerdefinierten Knotentyp zu erstellen, erstellen Sie eine Visual Studio-Erweiterung, implementiert die <xref:Microsoft.VisualStudio.SharePoint.Explorer.IExplorerNodeTypeProvider> Schnittstelle. Erstellen Sie einen benutzerdefinierten Knoten aus, wenn Sie Komponenten von SharePoint-Websites anzuzeigen, die nicht in angezeigt werden soll **Server-Explorer** standardmäßig. Beispielsweise **Server-Explorer** wird nicht angezeigt, die der Webpartkatalog von einer SharePoint-Website vom Standardwert zu verwenden, aber Sie können hinzufügen einen benutzerdefinierten Knoten, die dies tut. Weitere Informationen finden Sie unter [wie: Hinzufügen eines benutzerdefinierten SharePoint-Knotens zum Server-Explorer](../sharepoint/how-to-add-a-custom-sharepoint-node-to-server-explorer.md) und [Exemplarische Vorgehensweise: Erweitern von Server-Explorer zum Anzeigen von Webparts](../sharepoint/walkthrough-extending-server-explorer-to-display-web-parts.md).  
  
## <a name="adding-custom-properties-to-nodes"></a>Hinzufügen von benutzerdefinierten Eigenschaften zu Knoten  
 Wenn Sie einen Knoten zu erweitern oder erstellen einen benutzerdefinierten Knotentyp, können Sie benutzerdefinierte Eigenschaften auf den Knoten hinzufügen. Die Eigenschaften werden der **Eigenschaften** Fenster, wenn der Knoten ausgewählt ist.  
  
 Es gibt zwei Arten von benutzerdefinierten Eigenschaften, die Sie auf einen Knoten hinzufügen können:  
  
-   Eigenschaften, die einen Satz von schreibgeschützten Daten aus der SharePoint-Website anzuzeigen. Die Daten beschreibt die SharePoint-Komponente, die den Knoten darstellt. Eine exemplarische Vorgehensweise veranschaulicht, finden Sie unter [Exemplarische Vorgehensweise: Erweitern von Server-Explorer zum Anzeigen von Webparts](../sharepoint/walkthrough-extending-server-explorer-to-display-web-parts.md).  
  
-   Eigenschaften, die benutzerdefinierte Lese/Schreib-Daten anzuzeigen. Ein Codebeispiel, das veranschaulicht, wie Sie dies tun, finden Sie unter [wie: Erweitern eines SharePoint-Knotens im Server-Explorer](../sharepoint/how-to-extend-a-sharepoint-node-in-server-explorer.md).  
  
## <a name="getting-data-for-built-in-nodes"></a>Abrufen von Daten für integrierte Knoten  
 Alle von Visual Studio bereitgestellten integrierten Knoten enthalten einige Daten über die SharePoint-Komponente, die sie darstellen. So enthält beispielsweise ein Knoten, der eine Liste auf der SharePoint-Website stellt einige Daten über die Liste, z. B. den Titel und die URL der Standardansicht für die Liste.  
  
 Auf diese Daten zuzugreifen, rufen Sie ein Datenobjekt aus dem <xref:Microsoft.VisualStudio.SharePoint.IAnnotatedObject.Annotations%2A> Eigenschaft von der <xref:Microsoft.VisualStudio.SharePoint.Explorer.IExplorerNode> Objekt, das den Knoten darstellt, Sie von Interesse sind. Der Typ des Datenobjekts hängt vom Typ des Knotens ab.  
  
 Im folgenden Codebeispiel wird veranschaulicht, wie das Datenobjekt für eine Listenknoten abgerufen wird. Dieses Beispiel im Kontext eines umfangreicheren Beispiels finden Sie unter [Vorgehensweise: Abrufen von Daten für einen integrierten SharePoint-Knotens im Server-Explorer](../sharepoint/how-to-get-data-for-a-built-in-sharepoint-node-in-server-explorer.md).  
  
 [!code-vb[SPExtensibility.ProjectSystemExtension.General#11](../sharepoint/codesnippet/VisualBasic/projectsystemexamples/extension/serverexplorerextensionnodeinfo.vb#11)]
 [!code-csharp[SPExtensibility.ProjectSystemExtension.General#11](../sharepoint/codesnippet/CSharp/projectsystemexamples/extension/serverexplorerextensionnodeinfo.cs#11)]  
  
 Die folgende Tabelle enthält die Objekt-Datentypen für jeden integrierten Knotentyp.  
  
|Knotentyp|Objekt-Datentyp|  
|---------------|----------------------|  
|Knoten des SharePoint-Website|<xref:Microsoft.VisualStudio.SharePoint.Explorer.IExplorerSiteNodeInfo>|  
|Inhaltstyp|<xref:Microsoft.VisualStudio.SharePoint.Explorer.Extensions.IContentTypeNodeInfo>|  
|Feature|<xref:Microsoft.VisualStudio.SharePoint.Explorer.Extensions.IFeatureNodeInfo>|  
|Feld|<xref:Microsoft.VisualStudio.SharePoint.Explorer.Extensions.IFieldNodeInfo>|  
|Liste|<xref:Microsoft.VisualStudio.SharePoint.Explorer.Extensions.IListNodeInfo>|  
|Listenvorlage|<xref:Microsoft.VisualStudio.SharePoint.Explorer.Extensions.IListTemplateNodeInfo>|  
|Listenansicht (Microsoft.SharePoint.SPView)|<xref:Microsoft.VisualStudio.SharePoint.Explorer.Extensions.IListViewNodeInfo>|  
|Workflow-Zuordnung|<xref:Microsoft.VisualStudio.SharePoint.Explorer.Extensions.IWorkflowAssociationNodeInfo>|  
|Workflow-Vorlage|<xref:Microsoft.VisualStudio.SharePoint.Explorer.Extensions.IWorkflowTemplateNodeInfo>|  
  
 Weitere Informationen zum Verwenden der <xref:Microsoft.VisualStudio.SharePoint.IAnnotatedObject.Annotations%2A> Eigenschaft finden Sie unter [Zuordnen von benutzerdefinierten Daten zu SharePoint-Tools-Erweiterungen](../sharepoint/associating-custom-data-with-sharepoint-tools-extensions.md).  
  
## <a name="see-also"></a>Siehe auch  
 [Exemplarische Vorgehensweise: Erweitern von Server-Explorer zum Anzeigen von Webparts](../sharepoint/walkthrough-extending-server-explorer-to-display-web-parts.md)   
 [Vorgehensweise: Erweitern eines SharePoint-Knotens im Server-Explorer](../sharepoint/how-to-extend-a-sharepoint-node-in-server-explorer.md)   
 [Vorgehensweise: Hinzufügen eines benutzerdefinierten SharePoint-Knotens zu Server-Explorer](../sharepoint/how-to-add-a-custom-sharepoint-node-to-server-explorer.md)   
 [Vorgehensweise: Abrufen von Daten für einen integrierten SharePoint-Knotens im Server-Explorer](../sharepoint/how-to-get-data-for-a-built-in-sharepoint-node-in-server-explorer.md)   
 [Zuordnen von benutzerdefinierten Daten zu SharePoint-Tools-Erweiterungen](../sharepoint/associating-custom-data-with-sharepoint-tools-extensions.md)   
 [Durchsuchen von SharePoint-Verbindungen mit dem Server-Explorer](../sharepoint/browsing-sharepoint-connections-using-server-explorer.md)   
 [Erweitern der SharePoint-Tools in Visual Studio](../sharepoint/extending-the-sharepoint-tools-in-visual-studio.md)  
  
  