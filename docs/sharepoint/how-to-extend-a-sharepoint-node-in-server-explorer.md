---
title: 'Vorgehensweise: Erweitern eines SharePoint-Knotens im Server-Explorer | Microsoft-Dokumentation'
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
author: TerryGLee
ms.author: tglee
manager: douge
ms.workload:
- office
ms.openlocfilehash: f61afe90ed48064c79dd40c0c0975155c956e3e8
ms.sourcegitcommit: 240c8b34e80952d00e90c52dcb1a077b9aff47f6
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 10/23/2018
ms.locfileid: "49861838"
---
# <a name="how-to-extend-a-sharepoint-node-in-server-explorer"></a>Gewusst wie: Erweitern eines SharePoint-Knotens im Server-Explorer
  Sie können die Knoten erweitern die **SharePoint-Verbindungen** Knoten **Server-Explorer**. Dies ist nützlich, wenn Sie neue untergeordnete Knoten, Elemente des Kontextmenüs oder Eigenschaften zu einem vorhandenen Knoten hinzufügen möchten. Weitere Informationen finden Sie unter [Erweitern des SharePoint-Verbindungsknotens im Server-Explorer](../sharepoint/extending-the-sharepoint-connections-node-in-server-explorer.md).  
  
### <a name="to-extend-a-sharepoint-node-in-server-explorer"></a>Erweitern ein SharePoint-Knotens im Server-Explorer  
  
1.  Erstellen Sie ein Klassenbibliotheksprojekt.  
  
2.  Fügen Sie Verweise auf die folgenden Assemblys hinzu:  
  
    -   Microsoft.VisualStudio.SharePoint  
  
    -   Microsoft.VisualStudio.SharePoint.Explorer.Extensions  
  
    -   System.ComponentModel.Composition  
  
3.  Erstellen Sie eine Klasse, die die <xref:Microsoft.VisualStudio.SharePoint.Explorer.IExplorerNodeTypeExtension>-Schnittstelle implementiert.  
  
4.  Fügen Sie der Klasse das <xref:System.ComponentModel.Composition.ExportAttribute> -Attribut hinzu. Mit diesem Attribut können Sie Visual Studio zum Ermitteln und Laden Ihre <xref:Microsoft.VisualStudio.SharePoint.Explorer.IExplorerNodeTypeExtension> Implementierung. Übergeben Sie die <xref:Microsoft.VisualStudio.SharePoint.Explorer.IExplorerNodeTypeExtension> Typ an den Attributkonstruktor.  
  
5.  Fügen Sie der Klasse das <xref:Microsoft.VisualStudio.SharePoint.Explorer.ExplorerNodeTypeAttribute> -Attribut hinzu. Dieses Attribut gibt den Zeichenfolgenbezeichner für den Typ des Knotens, die Sie erweitern möchten.  
  
     Um integrierte Knotentypen, die von Visual Studio bereitgestellten anzugeben, übergeben Sie eine der folgenden Enumerationswerte an den Attributkonstruktor:  
  
    -   <xref:Microsoft.VisualStudio.SharePoint.Explorer.ExplorerNodeTypes>: Wird verwendet, diese Werte an der Website-Verbindungsknoten (die Knoten, die Website-URLs anzeigen), Standort, Knoten und alle anderen übergeordneten Knoten in **Server-Explorer**.  
  
    -   <xref:Microsoft.VisualStudio.SharePoint.Explorer.Extensions.ExtensionNodeTypes>: Verwenden Sie diese Werte, um eine der integrierten Knoten anzugeben, die auf einer SharePoint-Website, z. B. ein Knoten eine einzelne Komponente darstellen, die eine Liste, ein Feld oder Inhaltstyp darstellt.  
  
6.  In der Implementierung von der <xref:Microsoft.VisualStudio.SharePoint.Explorer.IExplorerNodeTypeExtension.Initialize%2A> Methode verwenden, Mitglied der *NodeType* Parameter, um Features auf den Knoten hinzufügen. Dieser Parameter ist ein <xref:Microsoft.VisualStudio.SharePoint.Explorer.IExplorerNodeType> -Objekt, das Zugriff auf die in definierten Ereignisse ermöglicht die <xref:Microsoft.VisualStudio.SharePoint.Explorer.IExplorerNodeEvents> Schnittstelle. Beispielsweise können Sie die folgenden Ereignisse behandeln:  
  
    -   <xref:Microsoft.VisualStudio.SharePoint.Explorer.IExplorerNodeEvents.NodeChildrenRequested>: Bearbeiten Sie dieses Ereignis, um neue untergeordnete Knoten auf den Knoten hinzuzufügen. Weitere Informationen finden Sie unter [Vorgehensweise: Hinzufügen ein benutzerdefiniertes SharePoint-Knotens zum Server-Explorer](../sharepoint/how-to-add-a-custom-sharepoint-node-to-server-explorer.md).  
  
    -   <xref:Microsoft.VisualStudio.SharePoint.Explorer.IExplorerNodeEvents.NodeMenuItemsRequested>: Behandeln Sie dieses Ereignis zum Hinzufügen eines benutzerdefinierten Kontextmenüelements auf den Knoten.  
  
    -   <xref:Microsoft.VisualStudio.SharePoint.Explorer.IExplorerNodeEvents.NodePropertiesRequested>: Behandeln Sie dieses Ereignis zum Hinzufügen von benutzerdefinierter Eigenschaften auf den Knoten. Die Eigenschaften werden in der **Eigenschaften** anzeigen, wenn der Knoten ausgewählt ist.  
  
## <a name="example"></a>Beispiel  
 Im folgenden Codebeispiel wird veranschaulicht zwei verschiedene Arten von Knoten Erweiterungen zu erstellen:  
  
- Eine Erweiterung, die SharePoint-Websiteknoten Kontextmenüelement hinzufügt. Wenn Sie das Menüelement klicken, wird der Name des Knotens, der auf die geklickt wurde.  
  
- Eine Erweiterung, die die benutzerdefinierte Eigenschaft fügt **ContosoExampleProperty** für jeden Knoten, die ein Feld namens darstellt **Text**.  
  
  [!code-csharp[SPExtensibility.ProjectSystemExtension.General#9](../sharepoint/codesnippet/CSharp/projectsystemexamples/extension/serverexplorerextension.cs#9)]
  [!code-vb[SPExtensibility.ProjectSystemExtension.General#9](../sharepoint/codesnippet/VisualBasic/projectsystemexamples/extension/serverexplorerextension.vb#9)]  
  
  Diese Erweiterung fügt eine bearbeitbare Zeichenfolgeneigenschaft Knoten hinzu. Sie können auch benutzerdefinierte Eigenschaften erstellen, in denen schreibgeschützte Daten vom SharePoint-Server angezeigt. Ein Beispiel zur Veranschaulichung der Vorgehensweise hierfür finden Sie unter [Exemplarische Vorgehensweise: Server-Explorer erweitern, um die Anzeige von Webparts](../sharepoint/walkthrough-extending-server-explorer-to-display-web-parts.md).  
  
## <a name="compile-the-code"></a>Kompilieren des Codes  
 Dieses Beispiel erfordert Verweise auf die folgenden Assemblys:  
  
-   Microsoft.VisualStudio.SharePoint  
  
-   Microsoft.VisualStudio.SharePoint.Explorer.Extensions  
  
-   System.ComponentModel.Composition  
  
-   System.Windows.Forms  
  
## <a name="deploy-the-extension"></a>Bereitstellen der Erweiterung  
 Zum Bereitstellen der **Server-Explorer** -Erweiterung erstellen Sie eine [!include[vsprvs](../sharepoint/includes/vsprvs-md.md)] -Erweiterung (VSIX) Verpacken, für die Assembly und alle anderen Dateien, die Sie mit der Erweiterung verteilen möchten. Weitere Informationen finden Sie unter [Bereitstellen von Erweiterungen für SharePoint-Tools in Visual Studio](../sharepoint/deploying-extensions-for-the-sharepoint-tools-in-visual-studio.md).  
  
## <a name="see-also"></a>Siehe auch
 [Gewusst wie: Hinzufügen ein benutzerdefiniertes SharePoint-Knotens zum Server-Explorer](../sharepoint/how-to-add-a-custom-sharepoint-node-to-server-explorer.md)   
 [Erweitern des SharePoint-Verbindungsknotens im Server-Explorer](../sharepoint/extending-the-sharepoint-connections-node-in-server-explorer.md)   
 [Exemplarische Vorgehensweise: Erweitern Sie Server-Explorer, um die Anzeige von Webparts](../sharepoint/walkthrough-extending-server-explorer-to-display-web-parts.md)   
 [Zuordnen von benutzerdefinierten Daten zu SharePoint-Tools-Erweiterungen](../sharepoint/associating-custom-data-with-sharepoint-tools-extensions.md)  
  
