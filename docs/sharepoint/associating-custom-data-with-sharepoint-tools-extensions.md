---
title: Erweiterungen für das Zuordnen von benutzerdefinierten Daten mit SharePoint-Tools | Microsoft-Dokumentation
ms.date: 02/02/2017
ms.topic: conceptual
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- projects [SharePoint development in Visual Studio], associating custom data
- project items [SharePoint development in Visual Studio], associating custom data
- SharePoint project items, associating custom data
- SharePoint projects, associating custom data
- SharePoint development in Visual Studio, extensibility features
author: TerryGLee
ms.author: tglee
manager: douge
ms.workload:
- office
ms.openlocfilehash: c4e3cba7d4b05de4d32f31bd39c0e462174695fe
ms.sourcegitcommit: 37fb7075b0a65d2add3b137a5230767aa3266c74
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 01/02/2019
ms.locfileid: "53951039"
---
# <a name="associate-custom-data-with-sharepoint-tools-extensions"></a>Zuordnen von benutzerdefinierten Daten zu SharePoint-Tools-Erweiterungen
  Sie können benutzerdefinierte Daten auf bestimmte Objekte in der SharePoint-Tools-Erweiterungen hinzufügen. Dies ist nützlich, wenn Daten in einem Teil der Erweiterung, die Sie später von anderem Code in Ihrer Erweiterung zugreifen möchten. Statt eine benutzerdefinierte Weise speichern und Abrufen von Daten zu implementieren, können die Daten in Ihrer Erweiterung mit einem Objekt zuordnen und klicken Sie dann die Daten aus demselben Objekt später abrufen.  
  
 Hinzufügen von benutzerdefinierten Daten zu Objekten ist auch nützlich, wenn Sie möchten, um Daten zu erhalten, die zu einem bestimmten Element in Visual Studio relevant sind. SharePoint-Tools-Erweiterungen werden geladen, nur einmal in Visual Studio, also die Erweiterung mit mehreren anderen Elementen arbeiten kann (z. B. Projekte, Projektelemente oder **Server-Explorer** Knoten) zu einem beliebigen Zeitpunkt. Wenn Sie benutzerdefinierte Daten, die nur für ein bestimmtes Element relevant ist verfügen, können Sie die Daten auf das Objekt hinzufügen, die dieses Element darstellt.  
  
 Wenn Sie benutzerdefinierte Daten für Objekte in der SharePoint-Tools-Erweiterungen hinzufügen, werden die Daten nicht beibehalten. Die Daten sind nur während der Lebensdauer des Objekts verfügbar. Nachdem das Objekt durch die Garbagecollection freigegeben wird, werden die Daten verloren gehen.  
  
 In die Erweiterungen des SharePoint-Projektsystem können Sie auch Zeichenfolgendaten speichern, die erhalten bleibt, nachdem Sie eine Erweiterung entladen wird. Weitere Informationen finden Sie unter [Speichern von Daten in Erweiterungen des SharePoint-Projektsystem](../sharepoint/saving-data-in-extensions-of-the-sharepoint-project-system.md).  
  
## <a name="objects-that-can-contain-custom-data"></a>Objekte, die benutzerdefinierte Daten enthalten können
 Sie können benutzerdefinierte Daten hinzufügen, auf ein beliebiges Objekt in der SharePoint-Tools-Objektmodell, die implementiert die <xref:Microsoft.VisualStudio.SharePoint.IAnnotatedObject> Schnittstelle. Diese Schnittstelle definiert nur eine der Eigenschaften, <xref:Microsoft.VisualStudio.SharePoint.IAnnotatedObject.Annotations%2A>, dies ist eine Auflistung von benutzerdefinierten Datenobjekte. Implementieren Sie die folgenden Typen <xref:Microsoft.VisualStudio.SharePoint.IAnnotatedObject>:  
  
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
  
## <a name="add-and-retrieve-custom-data"></a>Hinzufügen und Abrufen von benutzerdefinierten Daten
 Um benutzerdefinierte Daten auf ein Objekt in einer SharePoint-Tools-Erweiterung hinzuzufügen, rufen die <xref:Microsoft.VisualStudio.SharePoint.IAnnotatedObject.Annotations%2A> -Eigenschaft des Objekts, das Sie verwenden möchten, fügen Sie die Daten auf, und verwenden Sie dann die <xref:Microsoft.VisualStudio.SharePoint.IAnnotationDictionary.Add%2A> Methode, um die Daten auf das Objekt hinzuzufügen.  
  
 Um benutzerdefinierte Daten aus einem Objekt in einer SharePoint-Tools-Erweiterung abzurufen, rufen die <xref:Microsoft.VisualStudio.SharePoint.IAnnotatedObject.Annotations%2A> Eigenschaft des Objekts, und klicken Sie dann verwenden Sie eine der folgenden Methoden:  
  
- <xref:Microsoft.VisualStudio.SharePoint.IAnnotationDictionary.TryGetValue%2A>. Diese Methode gibt **"true"** Wenn das Datenobjekt vorhanden ist, oder **"false"** ist es nicht vorhanden. Sie können diese Methode verwenden, zum Abrufen von Instanzen von Werttypen oder Verweistypen.  
  
- <xref:Microsoft.VisualStudio.SharePoint.IAnnotationDictionary.GetValue%2A>. Diese Methode gibt zurück, die Daten-Objekt, wenn er beendet wird, oder **null** ist es nicht vorhanden. Sie können diese Methode verwenden, nur für Instanzen von Verweistypen abzurufen.  
  
  Im folgenden Codebeispiel wird bestimmt, ob ein bestimmtes Datenobjekt bereits ein Projektelement zugeordnet ist. Wenn das Datenobjekt, das nicht bereits das Projektelement zugeordnet, wird der Code das Objekt, das fügt die <xref:Microsoft.VisualStudio.SharePoint.IAnnotatedObject.Annotations%2A> Eigenschaft des Projektelements. Dieses Beispiel im Kontext eines größeren Beispiels, finden Sie unter [Vorgehensweise: Hinzufügen einer Eigenschaft zu einer benutzerdefinierten SharePoint-Projektelementtyp](../sharepoint/how-to-add-a-property-to-a-custom-sharepoint-project-item-type.md).  
  
  [!code-vb[SPExtensibility.ProjectItemExtension.MenuAndProperty#13](../sharepoint/codesnippet/VisualBasic/projectitemmenuandproperty/extension/projectitemtypeproperty.vb#13)]
  [!code-csharp[SPExtensibility.ProjectItemExtension.MenuAndProperty#13](../sharepoint/codesnippet/CSharp/projectitemmenuandproperty/extension/projectitemtypeproperty.cs#13)]  
  
## <a name="see-also"></a>Siehe auch
 [Programmierkonzepte und Funktionen für die SharePoint-Tools-Erweiterungen](../sharepoint/programming-concepts-and-features-for-sharepoint-tools-extensions.md)   
 [Exemplarische Vorgehensweise: Erstellen eines Projektelements benutzerdefinierte Aktion mit einer Elementvorlage, Teil 1](../sharepoint/walkthrough-creating-a-custom-action-project-item-with-an-item-template-part-1.md)   
 [Exemplarische Vorgehensweise: Erweitern Sie Server-Explorer, um die Anzeige von Webparts](../sharepoint/walkthrough-extending-server-explorer-to-display-web-parts.md)   
 [Vorgehensweise: Hinzufügen einer Eigenschaft zu SharePoint-Projekte](../sharepoint/how-to-add-a-property-to-sharepoint-projects.md)   
 [Vorgehensweise: Hinzufügen einer Eigenschaft zu einer benutzerdefinierten SharePoint-Projektelementtyp](../sharepoint/how-to-add-a-property-to-a-custom-sharepoint-project-item-type.md)
