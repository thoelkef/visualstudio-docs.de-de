---
title: Erweitern des SharePoint-Verbindungsknotens im Server-Explorer | Microsoft-Dokumentation
ms.date: 02/02/2017
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
ms.openlocfilehash: 36e99b5d239b48add1de5c281c35e698607500d5
ms.sourcegitcommit: 37fb7075b0a65d2add3b137a5230767aa3266c74
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 01/02/2019
ms.locfileid: "53933926"
---
# <a name="extend-the-sharepoint-connections-node-in-server-explorer"></a>Erweitern des SharePoint-Verbindungsknotens im Server-Explorer
  In Visual Studio können Sie mit der lokalen SharePoint-Websites auf dem Entwicklungscomputer verbinden, mit der **SharePoint-Verbindungen** Knoten in der **Server-Explorer** Fenster. Dieser Knoten zeigt viele der Komponenten der lokalen SharePoint-Websites in einer hierarchischen Strukturansicht an. Beispielsweise können Sie die Listen, Dokumentbibliotheken und Inhaltstypen auf lokale Standorte anzeigen. Weitere Informationen zur Verwendung von **Server-Explorer** zum Verbinden mit lokalen SharePoint-Websites finden Sie unter [Durchsuchen von SharePoint-Verbindungen mithilfe von Server-Explorer](../sharepoint/browsing-sharepoint-connections-using-server-explorer.md).  
  
 Sie können erweitern, die **SharePoint-Verbindungen** Knoten durch das Erstellen von Erweiterungen für vorhandene Knoten, oder erstellen einen benutzerdefinierten Knotentyp und zum Hinzufügen der Hierarchie von Knoten.  
  
## <a name="tasks-for-extending-the-sharepoint-connections-node"></a>Aufgaben zum Erweitern des SharePoint-Verbindungsknotens
 Um einen vorhandenen Knoten zu erweitern, erstellen Sie eine Visual Studio-Erweiterung, implementiert die <xref:Microsoft.VisualStudio.SharePoint.Explorer.IExplorerNodeTypeExtension> Schnittstelle. Wenn Sie einen Knoten erweitern, können Sie Funktionen auf den Knoten, z. B. eigene Elemente des Kontextmenüs oder benutzerdefinierte Eigenschaften hinzufügen. Weitere Informationen finden Sie unter [Vorgehensweise: Erweitern eines SharePoint-Knotens im Server-Explorer](../sharepoint/how-to-extend-a-sharepoint-node-in-server-explorer.md).  
  
 Um einen benutzerdefinierten Knotentyp zu erstellen, erstellen Sie eine Visual Studio-Erweiterung, implementiert die <xref:Microsoft.VisualStudio.SharePoint.Explorer.IExplorerNodeTypeProvider> Schnittstelle. Erstellen Sie einen benutzerdefinierten Knoten aus, wenn Komponenten von SharePoint-Websites anzuzeigen, die nicht im angezeigt werden sollen **Server-Explorer** standardmäßig. Z. B. **Server-Explorer** wird nicht angezeigt, die der Webpartkatalog der SharePoint-Website vom Standardwert zu verwenden, aber Sie hinzufügen können, einen benutzerdefinierten Knoten, die dies tut. Weitere Informationen finden Sie unter [Vorgehensweise: Fügen Sie einen benutzerdefinierten SharePoint-Knoten zum Server-Explorer](../sharepoint/how-to-add-a-custom-sharepoint-node-to-server-explorer.md) und [Exemplarische Vorgehensweise: Erweitern Sie Server-Explorer, um die Anzeige von Webparts](../sharepoint/walkthrough-extending-server-explorer-to-display-web-parts.md).  
  
## <a name="add-custom-properties-to-nodes"></a>Fügen benutzerdefinierter Eigenschaften zu Knoten hinzu
 Wenn Sie einen Knoten zu erweitern oder eines benutzerdefinierten Knotentyps erstellen, können Sie benutzerdefinierte Eigenschaften auf den Knoten hinzufügen. Die Eigenschaften werden in der **Eigenschaften** anzeigen, wenn der Knoten ausgewählt ist.  
  
 Es gibt zwei Arten von benutzerdefinierten Eigenschaften, die Sie einen Knoten hinzufügen können:  
  
-   Eigenschaften, die einen Satz von schreibgeschützten Daten aus der SharePoint-Website anzuzeigen. Die Daten beschreiben, die SharePoint-Komponente, die vom Knoten dargestellt wird. Eine exemplarische Vorgehensweise, die veranschaulicht, wie Sie dies tun, finden Sie unter [Exemplarische Vorgehensweise: Erweitern Sie Server-Explorer, um die Anzeige von Webparts](../sharepoint/walkthrough-extending-server-explorer-to-display-web-parts.md).  
  
-   Eigenschaften, benutzerdefinierte Lese/Schreib-Daten anzeigen. Ein Codebeispiel, das veranschaulicht, wie Sie dies tun, finden Sie unter [Vorgehensweise: Erweitern eines SharePoint-Knotens im Server-Explorer](../sharepoint/how-to-extend-a-sharepoint-node-in-server-explorer.md).  
  
## <a name="get-data-for-built-in-nodes"></a>Abrufen von Daten für integrierte Knoten
 Alle von Visual Studio bereitgestellte integrierte Knoten enthalten einige Daten über die SharePoint-Komponente, die sie darstellen. Beispielsweise stellt ein Knoten, der eine Liste auf der SharePoint-Website stellt einige Daten über die Liste, z. B. den Titel und die URL der Standardansicht für die Liste bereit.  
  
 Um diese Daten zuzugreifen, rufen Sie ein Datenobjekt aus dem <xref:Microsoft.VisualStudio.SharePoint.IAnnotatedObject.Annotations%2A> Eigenschaft der <xref:Microsoft.VisualStudio.SharePoint.Explorer.IExplorerNode> -Objekt, das vom Knoten dargestellt, Sie interessiert sind. Der Typ des Objekts hängt von den Typ des Knotens ab.  
  
 Im folgenden Codebeispiel wird veranschaulicht, wie Sie das Datenobjekt für einen Listenknoten abrufen. Dieses Beispiel im Kontext eines größeren Beispiels, finden Sie unter [Vorgehensweise: Abrufen von Daten für einen integrierten SharePoint-Knoten im Server-Explorer](../sharepoint/how-to-get-data-for-a-built-in-sharepoint-node-in-server-explorer.md).  
  
 [!code-vb[SPExtensibility.ProjectSystemExtension.General#11](../sharepoint/codesnippet/VisualBasic/projectsystemexamples/extension/serverexplorerextensionnodeinfo.vb#11)]
 [!code-csharp[SPExtensibility.ProjectSystemExtension.General#11](../sharepoint/codesnippet/CSharp/projectsystemexamples/extension/serverexplorerextensionnodeinfo.cs#11)]  
  
 Die folgende Tabelle enthält die Objekt-Datentypen für jeden integrierten Knotentyp.  
  
|Knotentyp|Datenobjekttyp|  
|---------------|----------------------|  
|SharePoint-Websiteknoten|<xref:Microsoft.VisualStudio.SharePoint.Explorer.IExplorerSiteNodeInfo>|  
|Inhaltstyp|<xref:Microsoft.VisualStudio.SharePoint.Explorer.Extensions.IContentTypeNodeInfo>|  
|Feature|<xref:Microsoft.VisualStudio.SharePoint.Explorer.Extensions.IFeatureNodeInfo>|  
|Feld|<xref:Microsoft.VisualStudio.SharePoint.Explorer.Extensions.IFieldNodeInfo>|  
|Liste|<xref:Microsoft.VisualStudio.SharePoint.Explorer.Extensions.IListNodeInfo>|  
|Listenvorlage|<xref:Microsoft.VisualStudio.SharePoint.Explorer.Extensions.IListTemplateNodeInfo>|  
|Listenansicht (Microsoft.SharePoint.SPView)|<xref:Microsoft.VisualStudio.SharePoint.Explorer.Extensions.IListViewNodeInfo>|  
|Workflowzuordnung|<xref:Microsoft.VisualStudio.SharePoint.Explorer.Extensions.IWorkflowAssociationNodeInfo>|  
|Workflow-Vorlage|<xref:Microsoft.VisualStudio.SharePoint.Explorer.Extensions.IWorkflowTemplateNodeInfo>|  
  
 Weitere Informationen zur Verwendung der <xref:Microsoft.VisualStudio.SharePoint.IAnnotatedObject.Annotations%2A> -Eigenschaft finden Sie unter [Erweiterungen Zuordnen von benutzerdefinierte Daten mit SharePoint-tools](../sharepoint/associating-custom-data-with-sharepoint-tools-extensions.md).  
  
## <a name="see-also"></a>Siehe auch
 [Exemplarische Vorgehensweise: Erweitern Sie Server-Explorer, um die Anzeige von Webparts](../sharepoint/walkthrough-extending-server-explorer-to-display-web-parts.md)   
 [Vorgehensweise: Erweitern eines SharePoint-Knotens im Server-Explorer](../sharepoint/how-to-extend-a-sharepoint-node-in-server-explorer.md)   
 [Vorgehensweise: Fügen Sie einen benutzerdefinierten SharePoint-Knoten zum Server-Explorer](../sharepoint/how-to-add-a-custom-sharepoint-node-to-server-explorer.md)   
 [Vorgehensweise: Abrufen von Daten für einen integrierten SharePoint-Knoten im Server-Explorer](../sharepoint/how-to-get-data-for-a-built-in-sharepoint-node-in-server-explorer.md)   
 [Zuordnen von benutzerdefinierten Daten zu SharePoint-Tools-Erweiterungen](../sharepoint/associating-custom-data-with-sharepoint-tools-extensions.md)   
 [Durchsuchen von SharePoint-Verbindungen mit Server-Explorer](../sharepoint/browsing-sharepoint-connections-using-server-explorer.md)   
 [Erweitern von SharePoint-Tools in Visual Studio](../sharepoint/extending-the-sharepoint-tools-in-visual-studio.md)  
