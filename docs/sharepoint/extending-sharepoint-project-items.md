---
title: Erweitern von SharePoint-Projektelementen | Microsoft-Dokumentation
ms.date: 02/02/2017
ms.topic: conceptual
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- project items [SharePoint development in Visual Studio], extending
- SharePoint project items, extending
- SharePoint development in Visual Studio, extending project items
author: John-Hart
ms.author: johnhart
manager: jillfra
ms.workload:
- office
ms.openlocfilehash: ecb6df8b7d6207336404d5e2f7562a88a18895bc
ms.sourcegitcommit: c0202a77d4dc562cdc55dc2e6223c062281d9749
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 01/24/2019
ms.locfileid: "54872585"
---
# <a name="extend-sharepoint-project-items"></a>Erweitern von SharePoint-Projektelemente
  Erstellen Sie eine projektelementerweiterung, wenn Sie möchten eine Art von SharePoint-Projektelement Funktionen hinzu, die in Visual Studio bereits installiert ist. Sie können z. B. erstellen eine Erweiterung für die integrierte **Ereignisempfänger** oder **Listendefinition** Projektelemente in Visual Studio, oder Sie können eine Erweiterung für einen benutzerdefinierten Projektelementtyp erstellen. Sie können auch eine Erweiterung für alle Arten von SharePoint-Projektelemente erstellen.  
  
## <a name="tasks-for-extending-sharepoint-project-items"></a>Aufgaben zum Erweitern der SharePoint-Projektelemente
 Um ein Projektelement erweitern möchten, erstellen Sie eine Visual Studio-Erweiterungsassembly, implementiert die <xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectItemTypeExtension> Schnittstelle. Weitere Informationen finden Sie unter [Vorgehensweise: Erstellen eine SharePoint-projektelementerweiterung](../sharepoint/how-to-create-a-sharepoint-project-item-extension.md).  
  
 Wenn Sie ein Projektelement erweitern, können Sie auch die folgende Funktionen auf das Projektelement hinzufügen:  
  
- Hinzufügen eines Kontextmenüelements auf das Projektelement. Das Menüelement angezeigt wird, wenn Sie das Kontextmenü für das Projektelement in öffnen **Projektmappen-Explorer**. Öffnen Sie das Kontextmenü per Rechtsklick auf das Projektelement, oder indem Sie ihn auswählen und dann auf die **UMSCHALT**+**F10** Schlüssel. Weitere Informationen finden Sie unter [Vorgehensweise: Hinzufügen ein Kontextmenüelements zu einer SharePoint-projektelementerweiterung](../sharepoint/how-to-add-a-shortcut-menu-item-to-a-sharepoint-project-item-extension.md).  
  
- Fügen Sie eine benutzerdefinierte Eigenschaft, auf das Projektelement. Die Eigenschaft wird in der **Eigenschaften** Fenster bei der Auswahl des Projektelement im **Projektmappen-Explorer**. Weitere Informationen finden Sie unter [Vorgehensweise: Hinzufügen einer Eigenschaft zu einer SharePoint-projektelementerweiterung](../sharepoint/how-to-add-a-property-to-a-sharepoint-project-item-extension.md).  
  
  Eine exemplarische Vorgehensweise, die veranschaulicht, wie erstellen, bereitstellen und testen eine projektelementerweiterung, finden Sie unter [Exemplarische Vorgehensweise: Erweitern ein SharePoint-Projektelementtyps](../sharepoint/walkthrough-extending-a-sharepoint-project-item-type.md).  
  
## <a name="understand-the-relationship-between-project-item-extensions-and-project-item-instances"></a>Verstehen Sie die Beziehung zwischen projektelementerweiterungen und Instanzen von Project-Element
 Wenn Sie eine projektelementerweiterung erstellen, lädt Visual Studio die Erweiterung aus, wenn ein SharePoint-Projekt ein Projektelement des zugeordneten Typs hinzugefügt wird. Angenommen, Sie erstellen Sie eine Erweiterung für **Ereignisempfänger** -Projektelemente, wenn ein Benutzer hinzufügt, lädt Visual Studio die Erweiterung einer **Ereignisempfänger** Projektelements, das ein Projekt. Visual Studio verwendet die gleiche Instanz der Erweiterung für alle Instanzen der zugeordneten Projektelementtyps. Im vorherigen Beispiel, wenn der Benutzer eine zweite Befehl fügt der **Ereignisempfänger** Projektelement für das Projekt, die gleiche Instanz der Erweiterung wird verwendet, um das zweite Projektelement anpassen.  
  
 Um eine bestimmte Instanz des Projektelementtyps zuzugreifen, Sie erweitern, behandeln Sie eines der der <xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectItemEvents> Ereignisse der *ProjectItemType* Parameter in der Implementierung von der <xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectItemTypeExtension.Initialize%2A> Methode. Um zu bestimmen, wenn ein Projektelement, der den Typ Sie erweitern ein Projekt hinzugefügt wird, z. B. Behandeln der <xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectItemEvents.ProjectItemAdded> Ereignis. Weitere Informationen finden Sie unter [Vorgehensweise: Erstellen eine SharePoint-projektelementerweiterung](../sharepoint/how-to-create-a-sharepoint-project-item-extension.md).  
  
## <a name="identifiers-for-sharepoint-project-items"></a>Bezeichner für die SharePoint-Projektelemente
 Jede SharePoint-Projektelement weist einen entsprechenden Zeichenfolgenbezeichner. Sie müssen den Bezeichner für ein Projektelement kennen, sollten Sie die folgenden Aufgaben ausführen:  
  
- Erstellen Sie eine Erweiterung für das Projektelement. In diesem Fall müssen Sie den Bezeichner für das Projektelement, die Sie erweitern, an den Konstruktor der möchten übergeben der <xref:Microsoft.VisualStudio.SharePoint.SharePointProjectItemTypeAttribute>. Um eine Erweiterung für alle Element Projekttypen zu erstellen, übergeben die **\\*** string-Wert.  
  
- Fügen Sie das Projektelement in ein Projekt programmgesteuert. In diesem Fall müssen Sie den Bezeichner für das Projektelement, übergeben die <xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectItemCollection.Add%2A> Methode.  
  
  Die folgende Tabelle enthält die Bezeichner für die SharePoint-Projektelemente, die mit Visual Studio enthalten sind.  
  
|Name des Projektelements|Die Zeichenfolgen-ID|  
|-----------------------|-----------------------|  
|Business Data Catalog-Modell|Microsoft.VisualStudio.SharePoint.BusinessDataConnectivity|  
|Inhaltstyp|Microsoft.VisualStudio.SharePoint.ContentType|  
|Ereignisempfänger|Microsoft.VisualStudio.SharePoint.EventHandler|  
|Leeres Element|Microsoft.VisualStudio.SharePoint.GenericElement|  
|Listendefinition<br /><br /> Listendefinition von Inhaltstyp|Microsoft.VisualStudio.SharePoint.ListDefinition|  
|Listeninstanz|Microsoft.VisualStudio.SharePoint.ListInstance|  
|Modul|Microsoft.VisualStudio.SharePoint.Module|  
|Sequenzieller Workflow<br /><br /> Zustandsautomat-Workflow|Microsoft.VisualStudio.SharePoint.Workflow|  
|Sitedefinition|Microsoft.VisualStudio.SharePoint.SiteDefinition|  
|Visuelles Webpart|Microsoft.VisualStudio.SharePoint.VisualWebPart|  
|Webpart|Microsoft.VisualStudio.SharePoint.WebPart|  
|Workflowzuordnungsformular|Microsoft.VisualStudio.SharePoint.WorkflowAssociation|  
  
## <a name="see-also"></a>Siehe auch
 [Vorgehensweise: Erstellen einer SharePoint-projektelementerweiterung](../sharepoint/how-to-create-a-sharepoint-project-item-extension.md)   
 [Vorgehensweise: Hinzufügen eines Kontextmenüelements zu einer SharePoint-projektelementerweiterung](../sharepoint/how-to-add-a-shortcut-menu-item-to-a-sharepoint-project-item-extension.md)   
 [Vorgehensweise: Hinzufügen einer Eigenschaft zu einer SharePoint-projektelementerweiterung](../sharepoint/how-to-add-a-property-to-a-sharepoint-project-item-extension.md)   
 [Exemplarische Vorgehensweise: Erweitern eines SharePoint-Projektelementtyps](../sharepoint/walkthrough-extending-a-sharepoint-project-item-type.md)   
 [Erweitern von SharePoint-Projektsystem](../sharepoint/extending-the-sharepoint-project-system.md)  
