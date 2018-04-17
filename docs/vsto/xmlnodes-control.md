---
title: XMLNodes-Steuerelement | Microsoft Docs
ms.custom: ''
ms.date: 02/02/2017
ms.technology:
- office-development
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
ms.openlocfilehash: 0bb3451f491e4a663a99488f4b2099d58f0018eb
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/16/2018
---
# <a name="xmlnodes-control"></a>XMLNodes-Steuerelement
  **Wichtige** die Informationen in diesem Thema nach Microsoft Word wird dargestellten ausschließlich für die Vorteile und die Verwendung von Einzelpersonen und Organisationen, die außerhalb der Vereinigten Staaten und seine Gebiete befinden, oder verwenden, oder entwickeln Programme, die unter ausgeführt, im Zusammenhang mit benutzerdefinierten XML-Code von Microsoft Word Microsoft Word-Produkte, die von Microsoft vor Januar 2010 lizenziert wurden, wenn eine Implementierung der einzelnen Funktionen von Microsoft entfernt. Diese Informationen bezüglich Microsoft Word kann nicht gelesen oder von Einzelpersonen oder Organisationen aus, in den Vereinigten Staaten oder die Vertriebsgebiete, denen der verwenden, oder entwickeln Programme, die auf Microsoft Word-Produkte ausgeführt, die von Microsoft nach dem 10. Januar 2010 lizenziert wurden verwendet werden ; Diese Produkte verhält sich nicht wie Produkte, die vor diesem Datum lizenziert oder erworben und lizenziert für die Verwendung außerhalb der Vereinigten Staaten.  
  
 [!INCLUDE[appliesto_wdalldoc](../vsto/includes/appliesto-wdalldoc-md.md)]  
  
 Die <xref:Microsoft.Office.Tools.Word.XMLNodes> -Steuerelement ist eine Auflistung von zugeordneten XML-Knoten-Objekten, das Ereignisse verfügbar macht. Die <xref:Microsoft.Office.Tools.Word.XMLNodes> Steuerelement wird nur erstellt, wenn ein sich wiederholendes Schemaelement in Microsoft Office Word-Dokument zugeordnet ist. Wenn sich wiederholende Element untergeordnete Elemente enthält, wird jedes untergeordnete Element auch erstellt als ein <xref:Microsoft.Office.Tools.Word.XMLNodes> Steuerelement.  
  
 Nachdem Visual Studio die Auflistung von XML-Knoten erstellt hat, können Sie das Steuerelement programmieren, ohne das Word-Objektmodell durchlaufen. Die <xref:Microsoft.Office.Tools.Word.XMLNodes> Steuerelement kann nur durch Entfernen der elementzuordnung aus dem Dokument gelöscht werden.  
  
> [!NOTE]  
>  Wenn Sie ein untergeordnetes Element des Zugriff auf die <xref:Microsoft.Office.Tools.Word.XMLNodes> steuern, über die <xref:Microsoft.Office.Tools.Word.XMLNodes.Item%2A> -Eigenschaft, es gibt eine <xref:Microsoft.Office.Interop.Word.XMLNode> Objekt anstelle eines <xref:Microsoft.Office.Tools.Word.XMLNode> Steuerelement. Weitere Informationen finden Sie unter [Programmgesteuerte Einschränkungen von Hostelementen und Hoststeuerelementen](../vsto/programmatic-limitations-of-host-items-and-host-controls.md).  
  
## <a name="binding-data-to-the-control"></a>Binden von Daten an das Steuerelement  
 Ein <xref:Microsoft.Office.Tools.Word.XMLNodes> Steuerelement unterstützt keine Datenbindung. Grund hierfür ist die <xref:Microsoft.Office.Tools.Word.XMLNodes> Steuerelement enthält keine Funktionen für die komplexe Datenbindung und das einfache Datenbindung nicht darstellen kann sich wiederholenden Daten.  
  
## <a name="formatting"></a>Formatierung  
 Keine Formatierung anwenden, die auf Text in das Dokument angewendet werden können kann angewendet werden, um eine <xref:Microsoft.Office.Tools.Word.XMLNodes> Steuerelement.  
  
## <a name="events"></a>Ereignisse  
 Die Ereignisse, die für die <xref:Microsoft.Office.Tools.Word.XMLNodes> Steuerelement sind:  
  
-   <xref:Microsoft.Office.Tools.Word.XMLNodes.AfterInsert>  
  
-   <xref:Microsoft.Office.Tools.Word.XMLNodes.BeforeDelete>  
  
-   <xref:Microsoft.Office.Tools.Word.XMLNodes.ContextEnter>  
  
-   <xref:Microsoft.Office.Tools.Word.XMLNodes.ContextLeave>  
  
-   <xref:Microsoft.Office.Tools.Word.XMLNodes.Deselect>  
  
-   <xref:System.ComponentModel.IComponent.Disposed>  
  
-   <xref:Microsoft.Office.Tools.Word.XMLNodes.Select>  
  
-   <xref:Microsoft.Office.Tools.Word.XMLNodes.ValidationError>  
  
## <a name="comparing-events"></a>Vergleichen von Ereignissen  
 Sie können ein Ereignis, wenn der Benutzer den Cursor innerhalb des Kontexts eines bestimmten bewegt erfassen <xref:Microsoft.Office.Tools.Word.XMLNodes> Steuerelement. Angenommen, Sie haben ein <xref:Microsoft.Office.Tools.Word.XMLNodes> Steuerelement namens `Customer` , besitzt ein untergeordnetes Element <xref:Microsoft.Office.Tools.Word.XMLNodes> Steuerelement namens `Company`, und `Company` verfügt über zwei untergeordnete <xref:Microsoft.Office.Tools.Word.XMLNodes> -Steuerelemente namens `CompanyName` und `CompanyRegion` wie folgt:  
  
```  
<Customer>  
    <Company>  
        <CompanyName>  
        <CompanyRegion>  
```  
  
 Wenn Sie ein Steuerelement im Aktionsbereich anzeigen möchten bei jedem bewegt sich der Cursor in die `Company` Knoten, es sollte nicht ausschlaggebend, ob in der sich der Cursor befindet `CompanyName` oder `CompanyRegion` , da beide im Kontext der `Company`. In diesem Fall können Sie Code schreiben, der <xref:Microsoft.Office.Tools.Word.XMLNodes.ContextEnter> -Ereignis `Company`.  
  
 In den meisten Fällen, wenn der Cursor wechselt ein <xref:Microsoft.Office.Tools.Word.XMLNodes> steuern, sowohl die <xref:Microsoft.Office.Tools.Word.XMLNodes.Select> und <xref:Microsoft.Office.Tools.Word.XMLNodes.ContextEnter> Ereignisse ausgelöst werden. Die folgende Tabelle zeigt die Unterschiede zwischen diesen Ereignissen.  
  
|Select-Ereignis|ContextEnter-Ereignis|  
|------------------|------------------------|  
|Tritt auf, wenn der Cursor sich in einem der Knoten von befindet der <xref:Microsoft.Office.Tools.Word.XMLNodes> Auflistung.|Tritt auf, wenn der Cursor in einem der Knoten oder untergeordneten Knoten des platziert ist die <xref:Microsoft.Office.Tools.Word.XMLNodes> Auflistung, aus einem Bereich außerhalb des Kontexts des Knotens. Heißt, es wird nur ausgelöst, wenn der Kontext geändert wird, und kann für mehrere geschachtelte ausgelöst werden <xref:Microsoft.Office.Tools.Word.XMLNodes> Steuerelemente.|  
  
 Wenn Sie beispielsweise den Cursor außerhalb von verschieben `Customer` in `CompanyName`, die <xref:Microsoft.Office.Tools.Word.XMLNodes.ContextEnter> Ereignisse für `Customer`, `Company`, und `CompanyName` ausgelöst werden. Wenn Sie dann den Cursor bewegen `CompanyName` auf `CompanyRegion`, die <xref:Microsoft.Office.Tools.Word.XMLNodes.ContextEnter> Ereignis nur für `CompanyRegion` ausgelöst wird, da der Kontext sowohl für ist `Company` und `Customer`. Sie können mehrere `Company` Knoten im Dokument. Wenn Sie den Cursor Verschieben der `CompanyName` Knoten von einem `Company` auf der `CompanyName` Knoten eines anderen `Company`, Kontext gleich ist, sodass nur die <xref:Microsoft.Office.Tools.Word.XMLNodes.Select> Ereignis wird ausgelöst.  
  
 Die gleichen Unterschiede bestehen zwischen dem <xref:Microsoft.Office.Tools.Word.XMLNodes.ContextLeave> Ereignis und die <xref:Microsoft.Office.Tools.Word.XMLNodes.Deselect> Ereignis.  
  
## <a name="see-also"></a>Siehe auch  
 [Übersicht über Hostelemente und Hoststeuerelemente](../vsto/host-items-and-host-controls-overview.md)   
 [Automatisieren von Word mithilfe von erweiterten Objekten](../vsto/automating-word-by-using-extended-objects.md)   
 [XMLNode-Steuerelement](../vsto/xmlnode-control.md)   
 [Vorgehensweise: Hinzufügen von XMLNodes-Steuerelementen zu Word-Dokumenten](../vsto/how-to-add-xmlnodes-controls-to-word-documents.md)   
 [Vorgehensweise: Zuordnen von Schemas zu Word-Dokumenten in Visual Studio](../vsto/how-to-map-schemas-to-word-documents-inside-visual-studio.md)   
 [Programmgesteuerte Einschränkungen von Hostelementen und Hoststeuerelementen](../vsto/programmatic-limitations-of-host-items-and-host-controls.md)  
  
  