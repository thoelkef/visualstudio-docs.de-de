---
title: XMLNode-Steuerelement | Microsoft Docs
ms.custom: 
ms.date: 02/02/2017
ms.reviewer: 
ms.suite: 
ms.technology:
- office-development
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- XMLNode control
author: TerryGLee
ms.author: tglee
manager: ghogen
ms.workload:
- office
ms.openlocfilehash: f89c80850c5f91cdc6d147d733d2626f8641dab6
ms.sourcegitcommit: f9fbf1f55f9ac14e4e5c6ae58c30dc1800ca6cda
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 01/10/2018
---
# <a name="xmlnode-control"></a>XMLNode-Steuerelement
  **Wichtige** die Informationen in diesem Thema nach Microsoft Word wird dargestellten ausschließlich für die Vorteile und die Verwendung von Einzelpersonen und Organisationen, die außerhalb der Vereinigten Staaten und seine Gebiete befinden, oder verwenden, oder entwickeln Programme, die unter ausgeführt, im Zusammenhang mit benutzerdefinierten XML-Code von Microsoft Word Microsoft Word-Produkte, die von Microsoft vor Januar 2010 lizenziert wurden, wenn eine Implementierung der einzelnen Funktionen von Microsoft entfernt. Diese Informationen bezüglich Microsoft Word kann nicht gelesen oder von Einzelpersonen oder Organisationen aus, in den Vereinigten Staaten oder die Vertriebsgebiete, denen der verwenden, oder entwickeln Programme, die auf Microsoft Word-Produkte ausgeführt, die von Microsoft nach dem 10. Januar 2010 lizenziert wurden verwendet werden ; Diese Produkte verhält sich nicht wie Produkte, die vor diesem Datum lizenziert oder erworben und lizenziert für die Verwendung außerhalb der Vereinigten Staaten.  
  
 [!INCLUDE[appliesto_wdalldoc](../vsto/includes/appliesto-wdalldoc-md.md)]  
  
 Die <xref:Microsoft.Office.Tools.Word.XMLNode> -Steuerelement ist ein zugeordnetes XML-Knoten-Objekt, das Ereignisse verfügbar macht und an Daten gebunden werden kann. Die <xref:Microsoft.Office.Tools.Word.XMLNode> Steuerelement wird nur erstellt, wenn ein nicht wiederholendes Schemaelement in Microsoft Office Word-Dokument zugeordnet ist. Nachdem Visual Studio den XML-Knoten erstellt hat, können Sie es Programmieren ohne das Word-Objektmodell durchlaufen.  
  
 Die <xref:Microsoft.Office.Tools.Word.XMLNode> Steuerelement kann nur durch Entfernen der elementzuordnung in Word gelöscht werden.  
  
## <a name="binding-data-to-the-control"></a>Binden von Daten an das Steuerelement  
 Ein <xref:Microsoft.Office.Tools.Word.XMLNode> -Steuerelement unterstützt die einfache Datenbindung. Der XML-Knoten sollten mit einer Datenquelle gebunden werden, mithilfe der <xref:System.Windows.Forms.IBindableComponent.DataBindings%2A> Eigenschaft. Wenn die Daten im gebundenen Dataset aktualisiert werden, die <xref:Microsoft.Office.Tools.Word.XMLNode> -Steuerelement wiedergibt, die Änderungen.  
  
## <a name="formatting"></a>Formatierung  
 Formatierung aus, die angewendet werden kann ein <xref:Microsoft.Office.Interop.Word.XMLNode> Objekt kann angewendet werden, um eine <xref:Microsoft.Office.Tools.Word.XMLNode> Steuerelement. Dies schließt Schriftarten, unterstreichen und Zeichenformate.  
  
## <a name="events"></a>Ereignisse  
 Die folgenden Ereignisse sind für das <xref:Microsoft.Office.Tools.Word.XMLNode>-Steuerelement verfügbar:  
  
-   <xref:Microsoft.Office.Tools.Word.XMLNode.AfterInsert>  
  
-   <xref:Microsoft.Office.Tools.Word.XMLNode.BeforeDelete>  
  
-   <xref:Microsoft.Office.Tools.Word.XMLNode.BindingContextChanged>  
  
-   <xref:Microsoft.Office.Tools.Word.XMLNode.ContextEnter>  
  
-   <xref:Microsoft.Office.Tools.Word.XMLNode.ContextLeave>  
  
-   <xref:Microsoft.Office.Tools.Word.XMLNode.Deselect>  
  
-   <xref:System.ComponentModel.IComponent.Disposed>  
  
-   <xref:Microsoft.Office.Tools.Word.XMLNode.Select>  
  
-   <xref:Microsoft.Office.Tools.Word.XMLNode.ValidationError>  
  
## <a name="comparing-events"></a>Vergleichen von Ereignissen  
 Sie können ein Ereignis, wenn der Benutzer den Cursor innerhalb des Kontexts eines bestimmten bewegt erfassen <xref:Microsoft.Office.Tools.Word.XMLNode> Steuerelement. Angenommen, Sie haben ein <xref:Microsoft.Office.Tools.Word.XMLNode> Steuerelement namens `Customer` , besitzt ein untergeordnetes Element <xref:Microsoft.Office.Tools.Word.XMLNode> Steuerelement namens `Company`, und `Company` verfügt über zwei untergeordnete <xref:Microsoft.Office.Tools.Word.XMLNode> -Steuerelemente namens `CompanyName` und `CompanyRegion` wie folgt:  
  
```  
<Customer>  
    <Company>  
        <CompanyName>  
        <CompanyRegion>  
```  
  
 Wenn Sie ein Steuerelement im Aktionsbereich anzeigen möchten bei jedem bewegt sich der Cursor in die `Company` Knoten, es sollte nicht ausschlaggebend, ob in der sich der Cursor befindet `CompanyName` oder `CompanyRegion` , da beide im Kontext der `Company`. In diesem Fall können Sie Code schreiben, der <xref:Microsoft.Office.Tools.Word.XMLNode.ContextEnter> -Ereignis `Company`.  
  
 In den meisten Fällen, wenn der Cursor wechselt ein <xref:Microsoft.Office.Tools.Word.XMLNode> steuern, sowohl die <xref:Microsoft.Office.Tools.Word.XMLNode.Select> und <xref:Microsoft.Office.Tools.Word.XMLNode.ContextEnter> Ereignisse ausgelöst werden. In der folgenden Tabelle werden die Unterschiede zwischen diesen Ereignissen dargestellt.  
  
|Wählen Sie Ereignis|ContextEnter-Ereignis|  
|------------------|------------------------|  
|Tritt auf, wenn der Cursor sich innerhalb befindet einer <xref:Microsoft.Office.Tools.Word.XMLNode>.|Tritt auf, wenn der Cursor sich innerhalb befindet einer <xref:Microsoft.Office.Tools.Word.XMLNode> oder eines seiner untergeordneten Knoten aus einem Bereich außerhalb des Kontexts des Knotens. Das heißt, er nur ausgelöst, wenn der Kontext geändert wird.|  
  
 Wenn Sie beispielsweise den Cursor außerhalb von verschieben `Customer` in `CompanyName`, die <xref:Microsoft.Office.Tools.Word.XMLNode.ContextEnter> -Ereignis für `Customer`, `Company`, und `CompanyName` ausgelöst wird. Wenn Sie dann den Cursor bewegen `CompanyName` auf `CompanyRegion`, nur die <xref:Microsoft.Office.Tools.Word.XMLNode.ContextEnter> -Ereignis für `CompanyRegion` wird ausgelöst, da Sie immer noch innerhalb des Kontexts beider `Company` und `Customer`.  
  
 Die gleichen Unterschiede bestehen zwischen dem <xref:Microsoft.Office.Tools.Word.XMLNode.ContextLeave> Ereignis und <xref:Microsoft.Office.Tools.Word.XMLNode.Deselect> Ereignis.  
  
## <a name="see-also"></a>Siehe auch  
 [Host Items and Host Controls Overview](../vsto/host-items-and-host-controls-overview.md)   
 [Automatisieren von Word mithilfe von erweiterten Objekten](../vsto/automating-word-by-using-extended-objects.md)   
 [XMLNodes-Steuerelement](../vsto/xmlnodes-control.md)   
 [Vorgehensweise: Hinzufügen von XMLNode-Steuerelementen zu Word-Dokumenten](../vsto/how-to-add-xmlnode-controls-to-word-documents.md)   
 [Vorgehensweise: Zuordnen von Schemas zu Word-Dokumenten in Visual Studio](../vsto/how-to-map-schemas-to-word-documents-inside-visual-studio.md)   
 [Programmgesteuerte Einschränkungen von Hostelementen und Hoststeuerelementen](../vsto/programmatic-limitations-of-host-items-and-host-controls.md)  
  
  