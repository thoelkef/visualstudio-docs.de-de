---
title: 'Vorgehensweise: Hinzufügen eines benutzerdefinierten SharePoint-Knotens zu Server-Explorer | Microsoft Docs'
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
ms.openlocfilehash: 47b51070a3f3368dbff636858c9a2e1ebf2e9f80
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/16/2018
---
# <a name="how-to-add-a-custom-sharepoint-node-to-server-explorer"></a>Gewusst wie: Hinzufügen eines benutzerdefinierten SharePoint-Knotens im Server-Explorer
  Sie können benutzerdefinierte Knoten hinzufügen der **SharePoint-Verbindungen** Knoten **Server-Explorer**. Dies ist hilfreich, wenn zusätzliche SharePoint-Komponenten angezeigt, die nicht in angezeigt werden sollen **Server-Explorer** standardmäßig. Weitere Informationen finden Sie unter [Erweitern des SharePoint-Verbindungsknotens im Server-Explorer](../sharepoint/extending-the-sharepoint-connections-node-in-server-explorer.md).  
  
 Um einen benutzerdefinierten Knoten hinzuzufügen, erstellen Sie zuerst eine Klasse, die den neuen Knoten definiert. Dann erstellen Sie eine Erweiterung, die den Knoten als untergeordnetes Element von einem vorhandenen Knoten hinzufügt.  
  
### <a name="to-define-the-new-node"></a>Um den neuen Knoten zu definieren.  
  
1.  Erstellen Sie ein Klassenbibliotheksprojekt.  
  
2.  Fügen Sie Verweise auf die folgenden Assemblys hinzu:  
  
    -   Microsoft.VisualStudio.SharePoint  
  
    -   Microsoft.VisualStudio.SharePoint.Explorer.Extensions  
  
    -   System.ComponentModel.Composition  
  
    -   System.Drawing  
  
3.  Erstellen Sie eine Klasse, die die <xref:Microsoft.VisualStudio.SharePoint.Explorer.IExplorerNodeTypeProvider>-Schnittstelle implementiert.  
  
4.  Fügen Sie der Klasse die folgenden Attribute hinzu:  
  
    -   <xref:System.ComponentModel.Composition.ExportAttribute> Mit diesem Attribut können Sie Visual Studio erkennt und lädt die <xref:Microsoft.VisualStudio.SharePoint.Explorer.IExplorerNodeTypeProvider> Implementierung. Übergeben Sie die <xref:Microsoft.VisualStudio.SharePoint.Explorer.IExplorerNodeTypeProvider> Typ an den Attributkonstruktor.  
  
    -   <xref:Microsoft.VisualStudio.SharePoint.Explorer.ExplorerNodeTypeAttribute> Dieses Attribut gibt den Zeichenfolgenbezeichner für den neuen Knoten an, in der Knotendefinition eines. Es wird empfohlen, dass Sie das Format verwenden *Firmenname*.* Knotenname* um sicherzustellen, dass alle Knoten einen eindeutigen Bezeichner verfügen.  
  
5.  In der Implementierung von der <xref:Microsoft.VisualStudio.SharePoint.Explorer.IExplorerNodeTypeProvider.InitializeType%2A> Methode verwenden, Mitglied der *TypeDefinition* Parameter so konfigurieren Sie das Verhalten des neuen Knotens. Dieser Parameter ist ein <xref:Microsoft.VisualStudio.SharePoint.Explorer.IExplorerNodeTypeDefinition> -Objekt, das Zugriff auf die in definierten Ereignisse ermöglicht die <xref:Microsoft.VisualStudio.SharePoint.Explorer.IExplorerNodeEvents> Schnittstelle.  
  
     Im folgenden Codebeispiel wird veranschaulicht, wie einen neuen Knoten definiert. In diesem Beispiel wird davon ausgegangen, dass das Projekt ein Symbol mit dem Namen CustomChildNodeIcon als eingebettete Ressource enthält.  
  
     [!code-vb[SPExtensibility.ProjectSystemExtension.General#6](../sharepoint/codesnippet/VisualBasic/projectsystemexamples/extension/serverexplorernode.vb#6)]
     [!code-csharp[SPExtensibility.ProjectSystemExtension.General#6](../sharepoint/codesnippet/CSharp/projectsystemexamples/extension/serverexplorernode.cs#6)]  
  
### <a name="to-add-the-new-node-as-a-child-of-an-existing-node"></a>So fügen Sie den neuen Knoten als untergeordnetes Element von einem vorhandenen Knoten hinzu  
  
1.  Im selben Projekt Knotendefinition, erstellen Sie eine Klasse, implementiert die <xref:Microsoft.VisualStudio.SharePoint.Explorer.IExplorerNodeTypeExtension> Schnittstelle.  
  
2.  Hinzufügen der <xref:System.ComponentModel.Composition.ExportAttribute> -Attribut der Klasse. Mit diesem Attribut können Sie Visual Studio erkennt und lädt die <xref:Microsoft.VisualStudio.SharePoint.Explorer.IExplorerNodeTypeExtension> Implementierung. Übergeben Sie die <xref:Microsoft.VisualStudio.SharePoint.Explorer.IExplorerNodeTypeExtension> Typ an den Attributkonstruktor.  
  
3.  Hinzufügen der <xref:Microsoft.VisualStudio.SharePoint.Explorer.ExplorerNodeTypeAttribute> -Attribut der Klasse. In einer Erweiterung des Knotens gibt dieses Attribut den Zeichenfolgenbezeichner für den Typ des Knotens, die Sie erweitern möchten.  
  
     Um integrierte Knotentypen aufgeführt, die von Visual Studio bereitgestellten anzugeben, übergeben Sie einen der folgenden Enumerationswerte an den Attributkonstruktor aus:  
  
    -   <xref:Microsoft.VisualStudio.SharePoint.Explorer.ExplorerNodeTypes>: Wird verwendet, diese Werte an der Website-Verbindungsknoten (die Knoten, die URLs der Website anzeigen), Standort, Knoten oder alle anderen übergeordneten Knoten im **Server-Explorer**.  
  
    -   <xref:Microsoft.VisualStudio.SharePoint.Explorer.Extensions.ExtensionNodeTypes>: Verwenden Sie diese Werte, um einen der integrierten Knoten anzugeben, die auf einer SharePoint-Website, z. B. ein Knoten eine einzelne Komponente darstellen, die Liste, ein Feld oder einen Inhaltstyp darstellt.  
  
4.  In der Implementierung von der <xref:Microsoft.VisualStudio.SharePoint.Explorer.IExplorerNodeTypeExtension.Initialize%2A> -Methode, das Handle der <xref:Microsoft.VisualStudio.SharePoint.Explorer.IExplorerNodeEvents.NodeChildrenRequested> -Ereignis für die <xref:Microsoft.VisualStudio.SharePoint.Explorer.IExplorerNodeType> Parameter.  
  
5.  In der <xref:Microsoft.VisualStudio.SharePoint.Explorer.IExplorerNodeEvents.NodeChildrenRequested> Ereignishandler, d. h. die Auflistung der untergeordneten Knoten von den neuen Knoten hinzufügen der <xref:Microsoft.VisualStudio.SharePoint.Explorer.ExplorerNodeEventArgs.Node%2A> -Objekt, das durch die Ereignisparameter Argumente verfügbar gemacht wird.  
  
     Im folgenden Codebeispiel wird veranschaulicht, wie zum Hinzufügen des neuen Knotens als untergeordnetes Element des SharePoint-Website-Knotens im **Server-Explorer**.  
  
     [!code-vb[SPExtensibility.ProjectSystemExtension.General#7](../sharepoint/codesnippet/VisualBasic/projectsystemexamples/extension/serverexplorernode.vb#7)]
     [!code-csharp[SPExtensibility.ProjectSystemExtension.General#7](../sharepoint/codesnippet/CSharp/projectsystemexamples/extension/serverexplorernode.cs#7)]  
  
## <a name="complete-example"></a>Vollständiges Beispiel  
 Das folgende Codebeispiel stellt den vollständigen Code zum Definieren eines einfachen Knotens und fügen es als untergeordnetes Element des SharePoint-Website-Knotens im **Server-Explorer**.  
  
 [!code-vb[SPExtensibility.ProjectSystemExtension.General#5](../sharepoint/codesnippet/VisualBasic/projectsystemexamples/extension/serverexplorernode.vb#5)]
 [!code-csharp[SPExtensibility.ProjectSystemExtension.General#5](../sharepoint/codesnippet/CSharp/projectsystemexamples/extension/serverexplorernode.cs#5)]  
  
## <a name="compiling-the-code"></a>Kompilieren des Codes  
 In diesem Beispiel wird davon ausgegangen, dass das Projekt ein Symbol mit dem Namen CustomChildNodeIcon als eingebettete Ressource enthält. Dieses Beispiel benötigen Sie auch Verweise auf die folgenden Assemblys:  
  
-   Microsoft.VisualStudio.SharePoint  
  
-   System.ComponentModel.Composition  
  
-   System.Drawing  
  
## <a name="deploying-the-extension"></a>Bereitstellen der Erweiterung  
 Bereitstellen der **Server-Explorer** Erweiterung erstellen Sie eine [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] Erweiterung (VSIX) Verpacken, für die Assembly und alle anderen Dateien, die Sie mit der Erweiterung verteilen möchten. Weitere Informationen finden Sie unter [Bereitstellen von Erweiterungen für SharePoint-Tools in Visual Studio](../sharepoint/deploying-extensions-for-the-sharepoint-tools-in-visual-studio.md).  
  
## <a name="see-also"></a>Siehe auch  
 [Erweitern des SharePoint-Verbindungsknotens im Server-Explorer](../sharepoint/extending-the-sharepoint-connections-node-in-server-explorer.md)   
 [Vorgehensweise: Erweitern eines SharePoint-Knotens im Server-Explorer](../sharepoint/how-to-extend-a-sharepoint-node-in-server-explorer.md)   
 [Exemplarische Vorgehensweise: Erweitern des Server-Explorers für die Anzeige von Webparts](../sharepoint/walkthrough-extending-server-explorer-to-display-web-parts.md)  
  
  