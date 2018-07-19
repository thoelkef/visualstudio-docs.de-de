---
title: 'Vorgehensweise: Hinzufügen eines benutzerdefinierten SharePoint-Knotens zu Server-Explorer | Microsoft-Dokumentation'
ms.custom: ''
ms.date: 02/02/2017
ms.technology:
- office-development
ms.topic: conceptual
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- SharePoint development in Visual Studio, extending SharePoint Connections node in Server Explorer
- SharePoint Connections [SharePoint development in Visual Studio], creating a new node type
author: TerryGLee
ms.author: tglee
manager: douge
ms.workload:
- office
ms.openlocfilehash: bb0ba7f09ae564a794792ad6f7a60f53f6f6422e
ms.sourcegitcommit: 30f653d9625ba763f6b58f02fb74a24204d064ea
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 06/25/2018
ms.locfileid: "36755640"
---
# <a name="how-to-add-a-custom-sharepoint-node-to-server-explorer"></a>Gewusst wie: Hinzufügen ein benutzerdefiniertes SharePoint-Knotens zum Server-Explorer
  Sie können benutzerdefinierte Knoten hinzufügen der **SharePoint-Verbindungen** Knoten **Server-Explorer**. Dies ist nützlich, wenn Sie zusätzliche SharePoint-Komponenten angezeigt, die nicht im angezeigt werden soll **Server-Explorer** standardmäßig. Weitere Informationen finden Sie unter [Erweitern des SharePoint-Verbindungsknotens im Server-Explorer](../sharepoint/extending-the-sharepoint-connections-node-in-server-explorer.md).  
  
 Um einen benutzerdefinierten Knoten hinzuzufügen, erstellen Sie zuerst eine Klasse, die den neuen Knoten definiert. Anschließend erstellen Sie eine Erweiterung, die den Knoten als untergeordnetes Element eines vorhandenen Knotens hinzufügt.  
  
### <a name="to-define-the-new-node"></a>Um den neuen Knoten zu definieren.  
  
1.  Erstellen Sie ein Klassenbibliotheksprojekt.  
  
2.  Fügen Sie Verweise auf die folgenden Assemblys hinzu:  
  
    -   Microsoft.VisualStudio.SharePoint  
  
    -   Microsoft.VisualStudio.SharePoint.Explorer.Extensions  
  
    -   System.ComponentModel.Composition  
  
    -   System.Drawing  
  
3.  Erstellen Sie eine Klasse, die die <xref:Microsoft.VisualStudio.SharePoint.Explorer.IExplorerNodeTypeProvider>-Schnittstelle implementiert.  
  
4.  Fügen Sie die folgenden Attribute zur Klasse hinzu:  
  
    -   <xref:System.ComponentModel.Composition.ExportAttribute> Mit diesem Attribut können Sie Visual Studio zum Ermitteln und Laden Ihre <xref:Microsoft.VisualStudio.SharePoint.Explorer.IExplorerNodeTypeProvider> Implementierung. Übergeben Sie die <xref:Microsoft.VisualStudio.SharePoint.Explorer.IExplorerNodeTypeProvider> Typ an den Attributkonstruktor.  
  
    -   <xref:Microsoft.VisualStudio.SharePoint.Explorer.ExplorerNodeTypeAttribute> In der Knotendefinition eines gibt dieses Attribut den Zeichenfolgenbezeichner für den neuen Knoten an. Es wird empfohlen, dass Sie das Format verwenden *Firmenname*. *Knotenname* um sicherzustellen, dass alle Knoten einen eindeutigen Bezeichner verfügen.  
  
5.  In der Implementierung von der <xref:Microsoft.VisualStudio.SharePoint.Explorer.IExplorerNodeTypeProvider.InitializeType%2A> Methode verwenden, Mitglied der *TypeDefinition* Parameter, um das Verhalten des neuen Knotens zu konfigurieren. Dieser Parameter ist ein <xref:Microsoft.VisualStudio.SharePoint.Explorer.IExplorerNodeTypeDefinition> -Objekt, das Zugriff auf die in definierten Ereignisse ermöglicht die <xref:Microsoft.VisualStudio.SharePoint.Explorer.IExplorerNodeEvents> Schnittstelle.  
  
     Im folgenden Codebeispiel wird veranschaulicht, wie Sie einen neuen Knoten zu definieren. In diesem Beispiel wird davon ausgegangen, dass Ihr Projekt ein Symbol mit dem Namen CustomChildNodeIcon als eingebettete Ressource enthält.  
  
     [!code-vb[SPExtensibility.ProjectSystemExtension.General#6](../sharepoint/codesnippet/VisualBasic/projectsystemexamples/extension/serverexplorernode.vb#6)]
     [!code-csharp[SPExtensibility.ProjectSystemExtension.General#6](../sharepoint/codesnippet/CSharp/projectsystemexamples/extension/serverexplorernode.cs#6)]  
  
### <a name="to-add-the-new-node-as-a-child-of-an-existing-node"></a>Den neuen Knoten als untergeordnetes Element von einem vorhandenen Knoten hinzufügen  
  
1.  Im selben Projekt Knotendefinition, erstellen Sie eine Klasse, implementiert die <xref:Microsoft.VisualStudio.SharePoint.Explorer.IExplorerNodeTypeExtension> Schnittstelle.  
  
2.  Hinzufügen der <xref:System.ComponentModel.Composition.ExportAttribute> -Attribut der Klasse. Mit diesem Attribut können Sie Visual Studio zum Ermitteln und Laden Ihre <xref:Microsoft.VisualStudio.SharePoint.Explorer.IExplorerNodeTypeExtension> Implementierung. Übergeben Sie die <xref:Microsoft.VisualStudio.SharePoint.Explorer.IExplorerNodeTypeExtension> Typ an den Attributkonstruktor.  
  
3.  Hinzufügen der <xref:Microsoft.VisualStudio.SharePoint.Explorer.ExplorerNodeTypeAttribute> -Attribut der Klasse. In einer knotenerweiterung gibt dieses Attribut den Zeichenfolgenbezeichner für den Typ des Knotens, die Sie erweitern möchten.  
  
     Um integrierte Knotentypen, die von Visual Studio bereitgestellten anzugeben, übergeben Sie eine der folgenden Enumerationswerte an den Attributkonstruktor:  
  
    -   <xref:Microsoft.VisualStudio.SharePoint.Explorer.ExplorerNodeTypes>: Wird verwendet, diese Werte an der Website-Verbindungsknoten (die Knoten, die Website-URLs anzeigen), Standort, Knoten und alle anderen übergeordneten Knoten in **Server-Explorer**.  
  
    -   <xref:Microsoft.VisualStudio.SharePoint.Explorer.Extensions.ExtensionNodeTypes>: Verwenden Sie diese Werte, um eine der integrierten Knoten anzugeben, die auf einer SharePoint-Website, z. B. ein Knoten eine einzelne Komponente darstellen, die eine Liste, ein Feld oder Inhaltstyp darstellt.  
  
4.  In der Implementierung von der <xref:Microsoft.VisualStudio.SharePoint.Explorer.IExplorerNodeTypeExtension.Initialize%2A> -Methode, das Handle der <xref:Microsoft.VisualStudio.SharePoint.Explorer.IExplorerNodeEvents.NodeChildrenRequested> Ereignis die <xref:Microsoft.VisualStudio.SharePoint.Explorer.IExplorerNodeType> Parameter.  
  
5.  In der <xref:Microsoft.VisualStudio.SharePoint.Explorer.IExplorerNodeEvents.NodeChildrenRequested> -Ereignishandler die Auflistung der untergeordneten Knoten des neuen Knotens hinzugefügt der <xref:Microsoft.VisualStudio.SharePoint.Explorer.ExplorerNodeEventArgs.Node%2A> -Objekt, das von dem Ereignis Arguments-Parameter verfügbar gemacht wird.  
  
     Im folgenden Codebeispiel wird veranschaulicht, wie Sie den neuen Knoten als ein untergeordnetes Element des SharePoint-Websiteknoten im hinzufügen **Server-Explorer**.  
  
     [!code-vb[SPExtensibility.ProjectSystemExtension.General#7](../sharepoint/codesnippet/VisualBasic/projectsystemexamples/extension/serverexplorernode.vb#7)]
     [!code-csharp[SPExtensibility.ProjectSystemExtension.General#7](../sharepoint/codesnippet/CSharp/projectsystemexamples/extension/serverexplorernode.cs#7)]  
  
## <a name="complete-example"></a>Vollständiges Beispiel
 Das folgende Codebeispiel enthält den vollständigen Code zum Definieren eines einfachen Knotens, und fügen Sie es als untergeordnetes Element des SharePoint-Websiteknoten im **Server-Explorer**.  
  
 [!code-vb[SPExtensibility.ProjectSystemExtension.General#5](../sharepoint/codesnippet/VisualBasic/projectsystemexamples/extension/serverexplorernode.vb#5)]
 [!code-csharp[SPExtensibility.ProjectSystemExtension.General#5](../sharepoint/codesnippet/CSharp/projectsystemexamples/extension/serverexplorernode.cs#5)]  
  
## <a name="compiling-the-code"></a>Kompilieren des Codes  
 In diesem Beispiel wird davon ausgegangen, dass Ihr Projekt ein Symbol mit dem Namen CustomChildNodeIcon als eingebettete Ressource enthält. Dieses Beispiel erfordert auch Verweise auf die folgenden Assemblys:  
  
-   Microsoft.VisualStudio.SharePoint  
  
-   System.ComponentModel.Composition  
  
-   System.Drawing  
  
## <a name="deploy-the-extension"></a>Bereitstellen der Erweiterung  
 Zum Bereitstellen der **Server-Explorer** -Erweiterung erstellen Sie eine [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] -Erweiterung (VSIX) Verpacken, für die Assembly und alle anderen Dateien, die Sie mit der Erweiterung verteilen möchten. Weitere Informationen finden Sie unter [Bereitstellen von Erweiterungen für SharePoint-Tools in Visual Studio](../sharepoint/deploying-extensions-for-the-sharepoint-tools-in-visual-studio.md).  
  
## <a name="see-also"></a>Siehe auch
 [Erweitern des SharePoint-Verbindungsknotens im Server-Explorer](../sharepoint/extending-the-sharepoint-connections-node-in-server-explorer.md)   
 [Gewusst wie: Erweitern eines SharePoint-Knotens im Server-Explorer](../sharepoint/how-to-extend-a-sharepoint-node-in-server-explorer.md)   
 [Exemplarische Vorgehensweise: Erweitern Sie Server-Explorer, um die Anzeige von Webparts](../sharepoint/walkthrough-extending-server-explorer-to-display-web-parts.md)  
  
  
