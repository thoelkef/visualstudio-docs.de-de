---
title: Erweitern von SharePoint-Projektelementen | Microsoft Docs
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
- project items [SharePoint development in Visual Studio], extending
- SharePoint project items, extending
- SharePoint development in Visual Studio, extending project items
author: TerryGLee
ms.author: tglee
manager: ghogen
ms.workload: office
ms.openlocfilehash: e990896720916048ab449c7ccb5a927577861256
ms.sourcegitcommit: f9fbf1f55f9ac14e4e5c6ae58c30dc1800ca6cda
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 01/10/2018
---
# <a name="extending-sharepoint-project-items"></a>Erweitern von SharePoint-Projektelementen
  Erstellen Sie eine projektelementerweiterung, wenn Sie möchten einen Typ von SharePoint-Projektelement Funktionen hinzu, die in Visual Studio bereits installiert ist. Sie können z. B. eine Erweiterung für das integrierte erstellen **Ereignisempfänger** oder **Listendefinition** Projektelemente in Visual Studio, oder Sie können eine Erweiterung für einen benutzerdefinierten Projektelementtyp erstellen. Sie können auch eine Erweiterung für alle Typen von SharePoint-Projektelementtypen erstellen.  
  
## <a name="tasks-for-extending-sharepoint-project-items"></a>Aufgaben zum Erweitern der SharePoint-Projektelemente  
 Um ein Projektelement zu erweitern, erstellen Sie eine Assembly der Visual Studio-Erweiterung, die implementiert die <xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectItemTypeExtension> Schnittstelle. Weitere Informationen finden Sie unter [Vorgehensweise: Erstellen einer SharePoint-Projektelementerweiterung](../sharepoint/how-to-create-a-sharepoint-project-item-extension.md).  
  
 Wenn Sie ein Projektelement erweitern, können Sie auch die folgende Funktionen, die im Projektelement hinzufügen:  
  
-   Das Projektelement ein Kontextmenüelement hinzugefügt. Das Menüelement wird angezeigt, wenn Sie das Kontextmenü für das Projektelement in öffnen **Projektmappen-Explorer**. Öffnen Sie das Kontextmenü, indem Sie mit der rechten Maustaste des Projektelements, oder indem Sie ihn auswählen, und drücken Sie dann UMSCHALT + F10-Schlüsseln. Weitere Informationen finden Sie unter [wie: Hinzufügen eines Kontextmenüelements zu einer SharePoint-Projektelementerweiterung](../sharepoint/how-to-add-a-shortcut-menu-item-to-a-sharepoint-project-item-extension.md).  
  
-   Fügen Sie dem Projektelement eine benutzerdefinierte Eigenschaft hinzu. Die Eigenschaft wird in der **Eigenschaften** Fenster bei der Auswahl des Projektelements im **Projektmappen-Explorer**. Weitere Informationen finden Sie unter [wie: Hinzufügen einer Eigenschaft zu einer SharePoint-Projektelementerweiterung](../sharepoint/how-to-add-a-property-to-a-sharepoint-project-item-extension.md).  
  
 Eine exemplarische Vorgehensweise, die zum Erstellen, bereitstellen und testen eine projektelementerweiterung veranschaulicht, finden Sie unter [Exemplarische Vorgehensweise: Erweitern eines SharePoint-Projektelementtyps](../sharepoint/walkthrough-extending-a-sharepoint-project-item-type.md).  
  
## <a name="understanding-the-relationship-between-project-item-extensions-and-project-item-instances"></a>Grundlegendes zur Beziehung zwischen Project Item Extensions und Instanzen von Project-Element  
 Wenn Sie eine projektelementerweiterung erstellen, lädt Visual Studio die Erweiterung aus, wenn ein SharePoint-Projekt ein Projektelement des zugeordneten Typs hinzugefügt wird. Z. B. eine Erweiterung für **Ereignisempfänger** -Projektelemente, wenn ein Benutzer hinzufügt, lädt Visual Studio die Erweiterung ein **Ereignisempfänger** Projektelement zu einem Projekt. Visual Studio verwendet dieselbe Instanz der Erweiterung für alle Instanzen des Elementtyps zugeordnete-Projekt. Im vorherigen Beispiel, wenn der Benutzer ein zweites fügt **Ereignisempfänger** Projektelementdateien auf das Projekt, dieselbe Instanz der Erweiterung wird verwendet, um das zweite Projektelement anzupassen.  
  
 Um eine bestimmte Instanz des Projektelementtyps zuzugreifen, Sie erweitern, behandeln Sie eines der der <xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectItemEvents> Ereignisse der *ProjectItemType* Parameter in der Implementierung von der <xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectItemTypeExtension.Initialize%2A> Methode. Um zu bestimmen, wann ein Projektelement des Typs, die Sie erweitern zu einem Projekt hinzugefügt wird, z. B. Behandeln der <xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectItemEvents.ProjectItemAdded> Ereignis. Weitere Informationen finden Sie unter [Vorgehensweise: Erstellen einer SharePoint-Projektelementerweiterung](../sharepoint/how-to-create-a-sharepoint-project-item-extension.md).  
  
## <a name="identifiers-for-sharepoint-project-items"></a>Der Bezeichner für die SharePoint-Projektelemente  
 Jede SharePoint-Projektelement verfügt über einen entsprechenden Zeichenfolgenbezeichner. Sie müssen den Bezeichner für ein Projektelement kennen, wenn Sie die folgenden Aufgaben ausführen möchten:  
  
-   Erstellen Sie eine Erweiterung für das Projektelement. In diesem Fall müssen Sie den Bezeichner für das Projektelement, die Sie erweitern, an den Konstruktor des möchten übergeben der <xref:Microsoft.VisualStudio.SharePoint.SharePointProjectItemTypeAttribute>. Um eine Erweiterung für alle Typen Projektelement zu erstellen, übergeben die  **\***  string-Wert.  
  
-   Das Projektelement programmgesteuert zu einem Projekt hinzufügen. In diesem Fall müssen Sie den Bezeichner für das Projektelement zum Übergeben der <xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectItemCollection.Add%2A> Methode.  
  
 Die folgende Tabelle enthält die Bezeichner für die SharePoint-Projektelemente, die in Visual Studio enthalten sind.  
  
|Name des Projektelements|Die Zeichenfolgen-ID|  
|-----------------------|-----------------------|  
|Business Data Catalog-Modell|Microsoft.VisualStudio.SharePoint.BusinessDataConnectivity|  
|Inhaltstyp|Microsoft.VisualStudio.SharePoint.ContentType|  
|Ereignisempfänger|Microsoft.VisualStudio.SharePoint.EventHandler|  
|Leeres Element|Microsoft.VisualStudio.SharePoint.GenericElement|  
|Listendefinition<br /><br /> Listendefinition auf Basis eines Inhaltstyps|Microsoft.VisualStudio.SharePoint.ListDefinition|  
|Listeninstanz|Microsoft.VisualStudio.SharePoint.ListInstance|  
|Modul|Microsoft.VisualStudio.SharePoint.Module|  
|Sequenzieller Workflow<br /><br /> Zustandsautomat-Workflow|Microsoft.VisualStudio.SharePoint.Workflow|  
|Sitedefinition|Microsoft.VisualStudio.SharePoint.SiteDefinition|  
|Visuelles Webpart|Microsoft.VisualStudio.SharePoint.VisualWebPart|  
|Webpart|Microsoft.VisualStudio.SharePoint.WebPart|  
|Formular für Workflow-Zuordnung|Microsoft.VisualStudio.SharePoint.WorkflowAssociation|  
  
## <a name="see-also"></a>Siehe auch  
 [Vorgehensweise: erstellen eine SharePoint-Projektelementerweiterung](../sharepoint/how-to-create-a-sharepoint-project-item-extension.md)   
 [Vorgehensweise: Hinzufügen ein Kontextmenüelements zu einer SharePoint-Projektelementerweiterung](../sharepoint/how-to-add-a-shortcut-menu-item-to-a-sharepoint-project-item-extension.md)   
 [Vorgehensweise: Hinzufügen einer Eigenschaft zu einer SharePoint-Projektelementerweiterung](../sharepoint/how-to-add-a-property-to-a-sharepoint-project-item-extension.md)   
 [Exemplarische Vorgehensweise: Erweitern eines SharePoint-Projektelementtyps](../sharepoint/walkthrough-extending-a-sharepoint-project-item-type.md)   
 [Erweitern des SharePoint-Projektsystems](../sharepoint/extending-the-sharepoint-project-system.md)  
  