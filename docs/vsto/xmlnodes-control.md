---
title: XMLNodes-Steuerelement
ms.date: 02/02/2017
ms.topic: conceptual
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- XMLNodes control, events
- XMLNodes control
author: TerryGLee
ms.author: tglee
manager: douge
ms.workload:
- office
ms.openlocfilehash: 227c7b72e8574556cfb18635b6fa329229c4bea6
ms.sourcegitcommit: 37fb7075b0a65d2add3b137a5230767aa3266c74
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 01/02/2019
ms.locfileid: "53865426"
---
# <a name="xmlnodes-control"></a>XMLNodes-Steuerelement
  **Wichtige** die Informationen in diesem Thema nach Microsoft Word festgelegt ist, ausschließlich für die Vorteile und die Verwendung von Einzelpersonen und Organisationen, die außerhalb der Vereinigten Staaten und seine Gebiete befinden oder mit, dargestellten oder entwickeln Programme, auf denen ausgeführt wird, im Zusammenhang mit benutzerdefinierten XML-Code aus Microsoft Word Microsoft Word-Produkte, die von Microsoft vor Januar 2010 lizenziert wurden, wenn Microsoft eine Implementierung von bestimmten Funktionen entfernt. Diese Informationen in Bezug auf Microsoft Word kann nicht gelesen oder durch Einzelpersonen oder Organisationen, die in den Vereinigten Staaten oder der Gebiete, die mithilfe von, oder Entwickeln von Anwendungen, die Microsoft Word-Produkte ausgeführt werden, die von Microsoft, nach dem 10. Januar 2010 lizenziert wurden verwendet werden ; Diese Produkte verhält nicht als Produkte, die vor diesem Datum lizenziert oder erworben und für die Verwendung außerhalb der USA lizenziert.  
  
 [!INCLUDE[appliesto_wdalldoc](../vsto/includes/appliesto-wdalldoc-md.md)]  
  
 Die <xref:Microsoft.Office.Tools.Word.XMLNodes> Steuerelement ist eine Auflistung von zugeordneten XML-Knoten-Objekten, das Ereignisse verfügbar macht. Die <xref:Microsoft.Office.Tools.Word.XMLNodes> Steuerelement erstellt, nur, wenn ein sich wiederholendes Schemaelement auf Microsoft Office Word-Dokument zugeordnet ist. Wenn sich wiederholenden Elements untergeordnete Elemente enthält, wird jede der untergeordneten Elemente auch erstellt als ein <xref:Microsoft.Office.Tools.Word.XMLNodes> Steuerelement.  
  
 Nachdem Visual Studio die Auflistung von XML-Knoten erstellt wurde, können Sie das Steuerelement direkt ohne Durchlaufen von Word-Objektmodell programmieren. Die <xref:Microsoft.Office.Tools.Word.XMLNodes> Steuerelement kann nur durch das Entfernen der elementzuordnung aus dem Dokument gelöscht werden.  
  
> [!NOTE]  
>  Wenn Sie ein untergeordnetes Element des zugreifen der <xref:Microsoft.Office.Tools.Word.XMLNodes> steuern, über die <xref:Microsoft.Office.Tools.Word.XMLNodes.Item%2A> -Eigenschaft wird ein <xref:Microsoft.Office.Interop.Word.XMLNode> Objekt anstelle eines <xref:Microsoft.Office.Tools.Word.XMLNode> Steuerelement. Weitere Informationen finden Sie unter [programmgesteuerte Einschränkungen von Hostelementen und Hoststeuerelementen](../vsto/programmatic-limitations-of-host-items-and-host-controls.md).  
  
## <a name="bind-data-to-the-control"></a>Binden von Daten an das Steuerelement  
 Ein <xref:Microsoft.Office.Tools.Word.XMLNodes> -Steuerelement die Datenbindung nicht unterstützt. Grund hierfür ist die <xref:Microsoft.Office.Tools.Word.XMLNodes> Steuerelement enthält keine Funktionen für die komplexe Datenbindung und einfache Datenbindung nicht darstellen kann sich wiederholende Daten.  
  
## <a name="formatting"></a>Formatierung  
 Keine Formatierung anwenden, die Sie Text in das Dokument angewendet werden können kann angewendet werden, um eine <xref:Microsoft.Office.Tools.Word.XMLNodes> Steuerelement.  
  
## <a name="events"></a>Ereignisse  
 Die Ereignisse, die für die <xref:Microsoft.Office.Tools.Word.XMLNodes> sind:  
  
-   <xref:Microsoft.Office.Tools.Word.XMLNodes.AfterInsert>  
  
-   <xref:Microsoft.Office.Tools.Word.XMLNodes.BeforeDelete>  
  
-   <xref:Microsoft.Office.Tools.Word.XMLNodes.ContextEnter>  
  
-   <xref:Microsoft.Office.Tools.Word.XMLNodes.ContextLeave>  
  
-   <xref:Microsoft.Office.Tools.Word.XMLNodes.Deselect>  
  
-   <xref:System.ComponentModel.IComponent.Disposed>  
  
-   <xref:Microsoft.Office.Tools.Word.XMLNodes.Select>  
  
-   <xref:Microsoft.Office.Tools.Word.XMLNodes.ValidationError>  
  
## <a name="compare-events"></a>Vergleichen von Ereignissen  
 Sie können ein Ereignis, wenn der Benutzer den Cursor innerhalb des Kontexts eines bestimmten bewegt erfassen <xref:Microsoft.Office.Tools.Word.XMLNodes> Steuerelement. Angenommen, Sie haben eine <xref:Microsoft.Office.Tools.Word.XMLNodes> Steuerelement mit dem Namen `Customer` , die über ein untergeordnetes Element verfügt <xref:Microsoft.Office.Tools.Word.XMLNodes> Steuerelement mit dem Namen `Company`, und `Company` zwei untergeordnete <xref:Microsoft.Office.Tools.Word.XMLNodes> -Steuerelemente namens `CompanyName` und `CompanyRegion` wie folgt:  
  
```xml  
<Customer>  
    <Company>  
        <CompanyName>  
        <CompanyRegion>  
```  
  
 Sollten Sie ein Steuerelement im Aktionsbereich anzeigen jedes Mal, wenn bewegt sich der Cursor in die `Company` Knoten, es sollte keine Rolle, ob der Cursor platziert ist `CompanyName` oder `CompanyRegion` da beide als innerhalb des Kontexts `Company`. In diesem Fall können Sie Ihren Code schreiben, der <xref:Microsoft.Office.Tools.Word.XMLNodes.ContextEnter> Ereignis `Company`.  
  
 In den meisten Fällen, wenn der Cursor wechselt ein <xref:Microsoft.Office.Tools.Word.XMLNodes> zu steuern, sowohl die <xref:Microsoft.Office.Tools.Word.XMLNodes.Select> und <xref:Microsoft.Office.Tools.Word.XMLNodes.ContextEnter> Ereignisse ausgelöst werden. Die folgende Tabelle zeigt die Unterschiede zwischen diesen Ereignissen.  
  
|Ereignis auswählen|ContextEnter-Ereignis|  
|------------------|------------------------|  
|Tritt auf, wenn der Cursor sich in einem der Knoten von befindet der <xref:Microsoft.Office.Tools.Word.XMLNodes> Auflistung.|Tritt auf, wenn der Cursor sich in einem Knoten oder einem Nachfolgerknoten befindet der <xref:Microsoft.Office.Tools.Word.XMLNodes> -Auflistung einen Bereich außerhalb des Kontexts des Knotens. Das heißt, es ist nur ausgelöst, wenn der Kontext geändert wird, und ausgelöst werden kann, für mehrere geschachtelte <xref:Microsoft.Office.Tools.Word.XMLNodes> Steuerelemente.|  
  
 Wenn Sie z. B. den Cursor außerhalb von verschieben `Customer` in `CompanyName`, <xref:Microsoft.Office.Tools.Word.XMLNodes.ContextEnter> Ereignisse für `Customer`, `Company`, und `CompanyName` ausgelöst werden. Wenn Sie dann den Cursor verschieben `CompanyName` zu `CompanyRegion`, wird die <xref:Microsoft.Office.Tools.Word.XMLNodes.ContextEnter> Ereignis nur für `CompanyRegion` ausgelöst wird, da der Kontext gilt für beide ist `Company` und `Customer`. Sie haben mehrere `Company` Knoten im Dokument. Wenn Sie den Cursor Verschieben der `CompanyName` Knoten eines `Company` auf die `CompanyName` Knoten eines anderen `Company`, der Kontext ist identisch, sodass nur die <xref:Microsoft.Office.Tools.Word.XMLNodes.Select> Ereignis wird ausgelöst.  
  
 Die gleichen Unterschiede bestehen zwischen dem <xref:Microsoft.Office.Tools.Word.XMLNodes.ContextLeave> Ereignis und die <xref:Microsoft.Office.Tools.Word.XMLNodes.Deselect> Ereignis.  
  
## <a name="see-also"></a>Siehe auch  
 [Hostelemente und Host-Steuerelementen (Übersicht)](../vsto/host-items-and-host-controls-overview.md)   
 [Automatisieren von Word mithilfe von erweiterten Objekten](../vsto/automating-word-by-using-extended-objects.md)   
 [XMLNode-Steuerelement](../vsto/xmlnode-control.md)   
 [Vorgehensweise: Hinzufügen von XMLNodes-Steuerelementen zu Word-Dokumenten](../vsto/how-to-add-xmlnodes-controls-to-word-documents.md)   
 [Vorgehensweise: Zuordnen von Schemas zu Word-Dokumenten in Visual Studio](../vsto/how-to-map-schemas-to-word-documents-inside-visual-studio.md)   
 [Einschränkungen für programmgesteuerte Aufgaben von Hostelementen und Hoststeuerelementen](../vsto/programmatic-limitations-of-host-items-and-host-controls.md)  
