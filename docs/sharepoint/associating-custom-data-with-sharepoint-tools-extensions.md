---
title: Zuordnen von benutzerdefinierten Daten zu SharePoint-Tools-Erweiterungen | Microsoft Docs
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
- projects [SharePoint development in Visual Studio], associating custom data
- project items [SharePoint development in Visual Studio], associating custom data
- SharePoint project items, associating custom data
- SharePoint projects, associating custom data
- SharePoint development in Visual Studio, extensibility features
ms.assetid: cfc87272-85a1-4c36-89e4-2662417d59ea
caps.latest.revision: "27"
author: gewarren
ms.author: gewarren
manager: ghogen
ms.openlocfilehash: 3a37551f56159aaa3cda03edb6ec964a79d56da9
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 10/31/2017
---
# <a name="associating-custom-data-with-sharepoint-tools-extensions"></a>Zuordnen von benutzerdefinierten Daten zu SharePoint-Tools-Erweiterungen
  Sie können benutzerdefinierte Daten an bestimmte Objekte in der SharePoint-Tools-Erweiterungen hinzufügen. Dies ist hilfreich, wenn Daten in einem Teil der Erweiterung, die Sie später aus anderem Code in der Erweiterung zugreifen möchten. Anstatt zu implementieren eine benutzerdefinierte Methode zum Speichern und den Zugriff auf Daten, können die Daten mit einem Objekt in der Erweiterung zuordnen und klicken Sie dann die Daten aus dem gleichen Objekt später abrufen.  
  
 Hinzufügen von benutzerdefinierten Daten zu Objekten ist auch nützlich, wenn die Daten, die für ein bestimmtes Element in Visual Studio relevant ist, erhalten bleiben sollen. SharePoint-Tools-Erweiterungen werden geladen, nur einmal in Visual Studio, also die Erweiterung mit mehreren anderen Elementen funktionieren (z. B. Projekte, Projektelemente oder **Server-Explorer** Knoten) zu einem beliebigen Zeitpunkt. Wenn Sie benutzerdefinierte Daten, die nur für ein bestimmtes Element relevant ist verfügen, können Sie auf das Objekt, die dieses Element darstellt, die die Daten hinzufügen.  
  
 Wenn Sie benutzerdefinierte Daten an Objekten im SharePoint-Tools-Erweiterungen hinzufügen, behält keine Daten. Die Daten sind nur während der Lebensdauer des Objekts verfügbar. Nachdem das Objekt von der Garbagecollection wieder zugänglich gemacht wird, sind die Daten verloren gehen.  
  
 In die Erweiterungen des SharePoint-Projektsystem können Sie auch Zeichenfolgendaten speichern, die erhalten bleibt, nachdem eine Erweiterung entladen wird. Weitere Informationen finden Sie unter [speichern Daten in Erweiterungen des SharePoint-Projektsystem](../sharepoint/saving-data-in-extensions-of-the-sharepoint-project-system.md).  
  
## <a name="objects-that-can-contain-custom-data"></a>Objekte, die benutzerdefinierte Daten enthalten kann  
 Sie können benutzerdefinierte Daten hinzufügen, auf ein beliebiges Objekt in der SharePoint-Tools-Objektmodell, das implementiert die <xref:Microsoft.VisualStudio.SharePoint.IAnnotatedObject> Schnittstelle. Diese Schnittstelle definiert nur eine der Eigenschaften <xref:Microsoft.VisualStudio.SharePoint.IAnnotatedObject.Annotations%2A>, dies ist eine Auflistung von benutzerdefinierten Datenobjekte. Die folgenden Typen implementieren <xref:Microsoft.VisualStudio.SharePoint.IAnnotatedObject>:  
  
-   <xref:Microsoft.VisualStudio.SharePoint.IMappedFolder>  
  
-   <xref:Microsoft.VisualStudio.SharePoint.IMenuItem>  
  
-   <xref:Microsoft.VisualStudio.SharePoint.ISharePointProject>  
  
-   <xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectFeature>  
  
-   <xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectFeatureResourceFile>  
  
-   <xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectItem>  
  
-   <xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectItemFile>  
  
-   <xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectItemType>  
  
-   <xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectItemTypeDefinition>  
  
-   <xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectMember>  
  
-   <xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectPackage>  
  
-   <xref:Microsoft.VisualStudio.SharePoint.Deployment.IDeploymentContext>  
  
-   <xref:Microsoft.VisualStudio.SharePoint.Explorer.IExplorerNode>  
  
-   <xref:Microsoft.VisualStudio.SharePoint.Explorer.IExplorerNodeType>  
  
-   <xref:Microsoft.VisualStudio.SharePoint.Explorer.IExplorerNodeTypeDefinition>  
  
## <a name="adding-and-retrieving-custom-data"></a>Hinzufügen und Abrufen von benutzerdefinierten Daten  
 Um benutzerdefinierte Daten zu einem Objekt in einer SharePoint-Tools-Erweiterung hinzufügen, erhalten die <xref:Microsoft.VisualStudio.SharePoint.IAnnotatedObject.Annotations%2A> -Eigenschaft des Objekts, das Sie verwenden möchten, fügen Sie die Daten auf, und verwenden Sie dann die <xref:Microsoft.VisualStudio.SharePoint.IAnnotationDictionary.Add%2A> Methode, um die Daten auf das Objekt hinzuzufügen.  
  
 Um benutzerdefinierte Daten aus einem Objekt in einer SharePoint-Tools-Erweiterung abzurufen, rufen die <xref:Microsoft.VisualStudio.SharePoint.IAnnotatedObject.Annotations%2A> Eigenschaft des Objekts und verwenden Sie dann eine der folgenden Methoden:  
  
-   <xref:Microsoft.VisualStudio.SharePoint.IAnnotationDictionary.TryGetValue%2A>. Diese Methode gibt **"true"** Wenn das Objekt vorhanden ist, oder **"false"** ist nicht vorhanden. Sie können diese Methode verwenden, beim Abrufen von Instanzen von Werttypen oder Referenztypen.  
  
-   <xref:Microsoft.VisualStudio.SharePoint.IAnnotationDictionary.GetValue%2A>. Diese Methode gibt die Daten-Objekt, wenn er beendet wird, oder **null** ist nicht vorhanden. Sie können diese Methode verwenden, nur für das Abrufen von Instanzen von Verweistypen.  
  
 Im folgenden Codebeispiel wird bestimmt, ob ein bestimmtes Datenobjekt bereits ein Projektelement zugeordnet ist. Wenn das Datenobjekt nicht bereits das Projektelement zugeordnet, wird der Code das Objekt, das fügt die <xref:Microsoft.VisualStudio.SharePoint.IAnnotatedObject.Annotations%2A> Eigenschaft des Projektelements. Dieses Beispiel im Kontext eines umfangreicheren Beispiels finden Sie unter [wie: Hinzufügen einer Eigenschaft zu einem benutzerdefinierten SharePoint-Projektelementtyp](../sharepoint/how-to-add-a-property-to-a-custom-sharepoint-project-item-type.md).  
  
 [!code-vb[SPExtensibility.ProjectItemExtension.MenuAndProperty#13](../sharepoint/codesnippet/VisualBasic/projectitemmenuandproperty/extension/projectitemtypeproperty.vb#13)]
 [!code-csharp[SPExtensibility.ProjectItemExtension.MenuAndProperty#13](../sharepoint/codesnippet/CSharp/projectitemmenuandproperty/extension/projectitemtypeproperty.cs#13)]  
  
## <a name="see-also"></a>Siehe auch  
 [Programmierkonzepte und Features für SharePoint-Tools-Erweiterungen](../sharepoint/programming-concepts-and-features-for-sharepoint-tools-extensions.md)   
 [Exemplarische Vorgehensweise: Erstellen eines Projektelements für die benutzerdefinierte Aktion mit einer Elementvorlage, Teil 1](../sharepoint/walkthrough-creating-a-custom-action-project-item-with-an-item-template-part-1.md)   
 [Exemplarische Vorgehensweise: Erweitern von Server-Explorer zum Anzeigen von Webparts](../sharepoint/walkthrough-extending-server-explorer-to-display-web-parts.md)   
 [Vorgehensweise: Hinzufügen einer Eigenschaft zu SharePoint-Projekte](../sharepoint/how-to-add-a-property-to-sharepoint-projects.md)   
 [Wie: Hinzufügen einer Eigenschaft zu einem benutzerdefinierten SharePoint-Projektelementtyp] (.. /SharePoint/How-to-Add-a-Property-to-a-Custom-SharePoint-Project-Item-Type.MD   
  