---
title: 'Vorgehensweise: Erweitern eines SharePoint-Knotens im Server-Explorer | Microsoft Docs'
ms.custom: 
ms.date: 02/02/2017
ms.reviewer: 
ms.suite: 
ms.technology: office-development
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- SharePoint Connections [SharePoint development in Visual Studio], extending a node
- SharePoint development in Visual Studio, extending SharePoint Connections node in Server Explorer
ms.assetid: 5e443950-12e6-40d1-864b-c384b6be4ce4
caps.latest.revision: "16"
author: gewarren
ms.author: gewarren
manager: ghogen
ms.workload: office
ms.openlocfilehash: 063586b6a4a839b8500ea3ef1729331bf82338ad
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 12/22/2017
---
# <a name="how-to-extend-a-sharepoint-node-in-server-explorer"></a>Gewusst wie: Erweitern eines SharePoint-Knotens im Server-Explorer
  Sie können die Knoten erweitern die **SharePoint-Verbindungen** Knoten **Server-Explorer**. Dies ist hilfreich, wenn Sie neue untergeordnete Knoten, Kontextmenüeinträge oder Eigenschaften auf einen vorhandenen Knoten hinzufügen möchten. Weitere Informationen finden Sie unter [Erweitern des SharePoint-Verbindungsknotens im Server-Explorer](../sharepoint/extending-the-sharepoint-connections-node-in-server-explorer.md).  
  
### <a name="to-extend-a-sharepoint-node-in-server-explorer"></a>Erweitern ein SharePoint-Knotens im Server-Explorer  
  
1.  Erstellen Sie ein Klassenbibliotheksprojekt.  
  
2.  Fügen Sie Verweise auf die folgenden Assemblys hinzu:  
  
    -   Microsoft.VisualStudio.SharePoint  
  
    -   Microsoft.VisualStudio.SharePoint.Explorer.Extensions  
  
    -   System.ComponentModel.Composition  
  
3.  Erstellen Sie eine Klasse, die die <xref:Microsoft.VisualStudio.SharePoint.Explorer.IExplorerNodeTypeExtension>-Schnittstelle implementiert.  
  
4.  Hinzufügen der <xref:System.ComponentModel.Composition.ExportAttribute> -Attribut der Klasse. Mit diesem Attribut können Sie Visual Studio erkennt und lädt die <xref:Microsoft.VisualStudio.SharePoint.Explorer.IExplorerNodeTypeExtension> Implementierung. Übergeben Sie die <xref:Microsoft.VisualStudio.SharePoint.Explorer.IExplorerNodeTypeExtension> Typ an den Attributkonstruktor.  
  
5.  Hinzufügen der <xref:Microsoft.VisualStudio.SharePoint.Explorer.ExplorerNodeTypeAttribute> -Attribut der Klasse. Dieses Attribut gibt den Zeichenfolgenbezeichner für den Typ des Knotens, die Sie erweitern möchten.  
  
     Um integrierte Knotentypen aufgeführt, die von Visual Studio bereitgestellten anzugeben, übergeben Sie einen der folgenden Enumerationswerte an den Attributkonstruktor aus:  
  
    -   <xref:Microsoft.VisualStudio.SharePoint.Explorer.ExplorerNodeTypes>: Wird verwendet, diese Werte an der Website-Verbindungsknoten (die Knoten, die URLs der Website anzeigen), Standort, Knoten oder alle anderen übergeordneten Knoten im **Server-Explorer**.  
  
    -   <xref:Microsoft.VisualStudio.SharePoint.Explorer.Extensions.ExtensionNodeTypes>: Verwenden Sie diese Werte, um einen der integrierten Knoten anzugeben, die auf einer SharePoint-Website, z. B. ein Knoten eine einzelne Komponente darstellen, die Liste, ein Feld oder einen Inhaltstyp darstellt.  
  
6.  In der Implementierung von der <xref:Microsoft.VisualStudio.SharePoint.Explorer.IExplorerNodeTypeExtension.Initialize%2A> Methode verwenden, Mitglied der *NodeType* Parameter Funktionen auf den Knoten hinzufügen. Dieser Parameter ist ein <xref:Microsoft.VisualStudio.SharePoint.Explorer.IExplorerNodeType> -Objekt, das Zugriff auf die in definierten Ereignisse ermöglicht die <xref:Microsoft.VisualStudio.SharePoint.Explorer.IExplorerNodeEvents> Schnittstelle. Beispielsweise können Sie die folgenden Ereignisse behandeln:  
  
    -   <xref:Microsoft.VisualStudio.SharePoint.Explorer.IExplorerNodeEvents.NodeChildrenRequested>: Dieses Ereignis, um neue untergeordnete Knoten des Knotens hinzufügen zu behandeln. Weitere Informationen finden Sie unter [wie: Hinzufügen eines benutzerdefinierten SharePoint-Knotens zum Server-Explorer](../sharepoint/how-to-add-a-custom-sharepoint-node-to-server-explorer.md).  
  
    -   <xref:Microsoft.VisualStudio.SharePoint.Explorer.IExplorerNodeEvents.NodeMenuItemsRequested>: Verarbeiten Sie dieses Ereignis zum Hinzufügen eines benutzerdefinierten Kontextmenüelements auf den Knoten.  
  
    -   <xref:Microsoft.VisualStudio.SharePoint.Explorer.IExplorerNodeEvents.NodePropertiesRequested>: Dieses Ereignis, um benutzerdefinierte Eigenschaften des Knotens hinzufügen zu behandeln. Die Eigenschaften werden der **Eigenschaften** Fenster, wenn der Knoten ausgewählt ist.  
  
## <a name="example"></a>Beispiel  
 Im folgenden Codebeispiel wird veranschaulicht, wie zwei verschiedene Arten von Knoten Erweiterungen zu erstellen:  
  
-   Eine Erweiterung, die SharePoint-Websiteknoten ein Kontextmenüelement hinzugefügt. Wenn Sie das Menüelement klicken, wird der Name des Knotens, auf den geklickt wurde.  
  
-   Eine Erweiterung, die eine benutzerdefinierte Eigenschaft mit dem Namen fügt **ContosoExampleProperty** auf jedem Knoten, der ein Feld mit dem Namen **Text**.  
  
 [!code-csharp[SPExtensibility.ProjectSystemExtension.General#9](../sharepoint/codesnippet/CSharp/projectsystemexamples/extension/serverexplorerextension.cs#9)]
 [!code-vb[SPExtensibility.ProjectSystemExtension.General#9](../sharepoint/codesnippet/VisualBasic/projectsystemexamples/extension/serverexplorerextension.vb#9)]  
  
 Diese Erweiterung hinzugefügt Knoten eine bearbeitbare Zeichenfolgeneigenschaft. Sie können auch benutzerdefinierte Eigenschaften erstellen, in denen schreibgeschützte Daten aus dem SharePoint-Server angezeigt. Ein Beispiel hierzu finden Sie unter [Exemplarische Vorgehensweise: Erweitern von Server-Explorer zum Anzeigen von Webparts](../sharepoint/walkthrough-extending-server-explorer-to-display-web-parts.md).  
  
## <a name="compiling-the-code"></a>Kompilieren des Codes  
 Dieses Beispiel erfordert Verweise auf die folgenden Assemblys:  
  
-   Microsoft.VisualStudio.SharePoint  
  
-   Microsoft.VisualStudio.SharePoint.Explorer.Extensions  
  
-   System.ComponentModel.Composition  
  
-   System.Windows.Forms  
  
## <a name="deploying-the-extension"></a>Bereitstellen der Erweiterung  
 Bereitstellen der **Server-Explorer** Erweiterung erstellen Sie eine [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] Erweiterung (VSIX) Verpacken, für die Assembly und alle anderen Dateien, die Sie mit der Erweiterung verteilen möchten. Weitere Informationen finden Sie unter [Bereitstellen von Erweiterungen für SharePoint-Tools in Visual Studio](../sharepoint/deploying-extensions-for-the-sharepoint-tools-in-visual-studio.md).  
  
## <a name="see-also"></a>Siehe auch  
 [Vorgehensweise: Hinzufügen eines benutzerdefinierten SharePoint-Knotens zu Server-Explorer](../sharepoint/how-to-add-a-custom-sharepoint-node-to-server-explorer.md)   
 [Erweitern des SharePoint-Verbindungsknotens im Server-Explorer](../sharepoint/extending-the-sharepoint-connections-node-in-server-explorer.md)   
 [Exemplarische Vorgehensweise: Erweitern von Server-Explorer zum Anzeigen von Webparts](../sharepoint/walkthrough-extending-server-explorer-to-display-web-parts.md)   
 [Zuordnen von benutzerdefinierten Daten zu SharePoint-Tools-Erweiterungen](../sharepoint/associating-custom-data-with-sharepoint-tools-extensions.md)  
  
  