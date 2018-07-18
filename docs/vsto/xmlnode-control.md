---
title: XMLNode-Steuerelement
ms.custom: ''
ms.date: 02/02/2017
ms.technology:
- office-development
ms.topic: conceptual
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- XMLNode control
author: TerryGLee
ms.author: tglee
manager: douge
ms.workload:
- office
ms.openlocfilehash: cd047814f11b5fddad868bd65b84deba369facd5
ms.sourcegitcommit: 34f7d23ce3bd140dcae875b602d5719bb4363ed1
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 06/11/2018
ms.locfileid: "35258888"
---
# <a name="xmlnode-control"></a>XMLNode-Steuerelement
  **Wichtige** die Informationen in diesem Thema nach Microsoft Word festgelegt ist, ausschließlich für die Vorteile und die Verwendung von Einzelpersonen und Organisationen, die außerhalb der Vereinigten Staaten und seine Gebiete befinden oder mit, dargestellten oder entwickeln Programme, auf denen ausgeführt wird, im Zusammenhang mit benutzerdefinierten XML-Code aus Microsoft Word Microsoft Word-Produkte, die von Microsoft vor Januar 2010 lizenziert wurden, wenn Microsoft eine Implementierung von bestimmten Funktionen entfernt. Diese Informationen in Bezug auf Microsoft Word kann nicht gelesen oder durch Einzelpersonen oder Organisationen, die in den Vereinigten Staaten oder der Gebiete, die mithilfe von, oder Entwickeln von Anwendungen, die Microsoft Word-Produkte ausgeführt werden, die von Microsoft, nach dem 10. Januar 2010 lizenziert wurden verwendet werden ; Diese Produkte verhält nicht als Produkte, die vor diesem Datum lizenziert oder erworben und für die Verwendung außerhalb der USA lizenziert.  
  
 [!INCLUDE[appliesto_wdalldoc](../vsto/includes/appliesto-wdalldoc-md.md)]  
  
 Die <xref:Microsoft.Office.Tools.Word.XMLNode> Steuerelement ist ein zugeordnete XML-Knoten-Objekt, das Ereignisse verfügbar macht und an Daten gebunden werden kann. Die <xref:Microsoft.Office.Tools.Word.XMLNode> Steuerelement erstellt, nur, wenn ein nicht wiederholtes Element des Schemas in Microsoft Office Word-Dokument zugeordnet ist. Nachdem Visual Studio den XML-Knoten erstellt wurde, können Sie dafür programmieren, ohne das Word-Objektmodell durchlaufen.  
  
 Die <xref:Microsoft.Office.Tools.Word.XMLNode> Steuerelement kann nur durch das Entfernen der elementzuordnung in Word gelöscht werden.  
  
## <a name="bind-data-to-the-control"></a>Binden von Daten an das Steuerelement  
 Ein <xref:Microsoft.Office.Tools.Word.XMLNode> -Steuerelement unterstützt die einfache Datenbindung. Der XML-Knoten sollten mit einer Datenquelle gebunden werden, mithilfe der <xref:System.Windows.Forms.IBindableComponent.DataBindings%2A> Eigenschaft. Wenn die Daten im gebundenen Dataset aktualisiert werden, die <xref:Microsoft.Office.Tools.Word.XMLNode> -Steuerelement die Änderungen wider.  
  
## <a name="formatting"></a>Formatierung  
 Formatierung, die angewendet werden kann eine <xref:Microsoft.Office.Interop.Word.XMLNode> Objekt kann angewendet werden, um eine <xref:Microsoft.Office.Tools.Word.XMLNode> Steuerelement. Dies schließt Schriftarten, unterstrichen und Zeichenformate.  
  
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
  
## <a name="compare-events"></a>Vergleichen von Ereignissen  
 Sie können ein Ereignis, wenn der Benutzer den Cursor innerhalb des Kontexts eines bestimmten bewegt erfassen <xref:Microsoft.Office.Tools.Word.XMLNode> Steuerelement. Angenommen, Sie haben eine <xref:Microsoft.Office.Tools.Word.XMLNode> Steuerelement mit dem Namen `Customer` , die über ein untergeordnetes Element verfügt <xref:Microsoft.Office.Tools.Word.XMLNode> Steuerelement mit dem Namen `Company`, und `Company` zwei untergeordnete <xref:Microsoft.Office.Tools.Word.XMLNode> -Steuerelemente namens `CompanyName` und `CompanyRegion` wie folgt:  
  
```xml  
<Customer>  
    <Company>  
        <CompanyName>  
        <CompanyRegion>  
```  
  
 Sollten Sie ein Steuerelement im Aktionsbereich anzeigen jedes Mal, wenn bewegt sich der Cursor in die `Company` Knoten, es sollte keine Rolle, ob der Cursor platziert ist `CompanyName` oder `CompanyRegion` da beide als innerhalb des Kontexts `Company`. In diesem Fall können Sie Ihren Code schreiben, der <xref:Microsoft.Office.Tools.Word.XMLNode.ContextEnter> Ereignis `Company`.  
  
 In den meisten Fällen, wenn der Cursor wechselt ein <xref:Microsoft.Office.Tools.Word.XMLNode> zu steuern, sowohl die <xref:Microsoft.Office.Tools.Word.XMLNode.Select> und <xref:Microsoft.Office.Tools.Word.XMLNode.ContextEnter> Ereignisse ausgelöst werden. Die folgende Tabelle zeigt die Unterschiede zwischen diesen Ereignissen.  
  
|Ereignis auswählen|ContextEnter-Ereignis|  
|------------------|------------------------|  
|Tritt auf, wenn der Cursor sich in befindet einem <xref:Microsoft.Office.Tools.Word.XMLNode>.|Tritt auf, wenn der Cursor sich in befindet einem <xref:Microsoft.Office.Tools.Word.XMLNode> oder eines seiner untergeordneten Knoten aus einem Bereich außerhalb des Kontexts des Knotens. Das heißt, sie nur ausgelöst, wenn der Kontext geändert wird.|  
  
 Z. B. Wenn Sie den Cursor außerhalb von verschieben `Customer` in `CompanyName`, <xref:Microsoft.Office.Tools.Word.XMLNode.ContextEnter> -Ereignis für `Customer`, `Company`, und `CompanyName` ausgelöst wird. Wenn Sie dann den Cursor bewegen `CompanyName` zu `CompanyRegion`, wird nur die <xref:Microsoft.Office.Tools.Word.XMLNode.ContextEnter> -Ereignis für `CompanyRegion` wird ausgelöst, da Sie immer noch innerhalb des Kontexts der `Company` und `Customer`.  
  
 Die gleichen Unterschiede bestehen zwischen dem <xref:Microsoft.Office.Tools.Word.XMLNode.ContextLeave> Ereignis und <xref:Microsoft.Office.Tools.Word.XMLNode.Deselect> Ereignis.  
  
## <a name="see-also"></a>Siehe auch  
 [Hostelemente und Host-Steuerelementen (Übersicht)](../vsto/host-items-and-host-controls-overview.md)   
 [Automatisieren von Word mithilfe von erweiterten Objekten](../vsto/automating-word-by-using-extended-objects.md)   
 [XMLNodes-Steuerelement](../vsto/xmlnodes-control.md)   
 [Gewusst wie: Hinzufügen von XMLNode-Steuerelementen zu Word-Dokumenten](../vsto/how-to-add-xmlnode-controls-to-word-documents.md)   
 [Gewusst wie: Zuordnen von Schemas zu Word-Dokumenten in Visual Studio](../vsto/how-to-map-schemas-to-word-documents-inside-visual-studio.md)   
 [Einschränkungen für programmgesteuerte Aufgaben von Hostelementen und Hoststeuerelementen](../vsto/programmatic-limitations-of-host-items-and-host-controls.md)  
  
  