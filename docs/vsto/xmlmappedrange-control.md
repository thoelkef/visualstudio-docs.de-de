---
title: XmlMappedRange-Steuerelement | Microsoft Docs
ms.custom: ''
ms.date: 02/02/2017
ms.technology:
- office-development
ms.topic: conceptual
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- XMLMappedRange control, data binding
- XMLMappedRange control
- XMLMappedRange control, events
author: TerryGLee
ms.author: tglee
manager: douge
ms.workload:
- office
ms.openlocfilehash: 1bc4516f0ca14427e5e63a40ae58ddd60436dfd6
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/16/2018
---
# <a name="xmlmappedrange-control"></a>XmlMappedRange-Steuerelement
  Die <xref:Microsoft.Office.Tools.Excel.XmlMappedRange> -Steuerelement ist ein Bereich, der erstellt wird, nur, wenn ein nicht wiederholtes Element des Schemas auf eine Zelle in Microsoft Office Excel zugeordnet ist. Beispielsweise, wenn die `maxOccurs` Attribut eines Schemaelements gleich 1. Nachdem Visual Studio den zugeordneten XML-Bereich erstellt wurde, können Sie es Programmieren ohne das Excel-Objektmodell durchlaufen. Sie können nur Löschen einer <xref:Microsoft.Office.Tools.Excel.XmlMappedRange> Steuerelement innerhalb von Excel, wenn die elementzuordnung entfernt wird.  
  
 [!INCLUDE[appliesto_xlalldoc](../vsto/includes/appliesto-xlalldoc-md.md)]  
  
 ![Link zu Video](../vsto/media/playvideo.gif "Link zu Video") eine entsprechende Videodemo finden Sie unter [wie führen I: verwendet XML-Mapping in Excel?](http://go.microsoft.com/fwlink/?LinkID=130288).  
  
## <a name="binding-data-to-the-control"></a>Binden von Daten an das Steuerelement  
 Ein <xref:Microsoft.Office.Tools.Excel.XmlMappedRange> Steuerelement unterstützt das Binden an ein einzelnes Datenfeld (einfache Datenbindung). Die <xref:Microsoft.Office.Tools.Excel.ListObject> Steuerelement kann komplexe Datenbindung unterstützt, und wird automatisch erstellt, wenn ein sich wiederholendes Schemaelement in einer Zelle zugeordnet ist. Weitere Informationen finden Sie unter [ListObject Control](../vsto/listobject-control.md).  
  
 Die <xref:Microsoft.Office.Tools.Excel.XmlMappedRange> Steuerelement an eine Datenquelle mit gebunden sind die <xref:System.Windows.Forms.Control.DataBindings%2A> Eigenschaft. Wenn ein <xref:Microsoft.Office.Tools.Excel.XmlMappedRange> einer Arbeitsblattzelle Visual Studio generiert automatisch ein Dataset aus den Daten in den zugeordneten Zellen und bindet das Steuerelement an das Dataset hinzugefügt wird. Die Standard-Datenbindungseigenschaft von der <xref:Microsoft.Office.Tools.Excel.XmlMappedRange> ist <xref:Microsoft.Office.Tools.Excel.XmlMappedRange.Value2%2A>.  
  
 Wenn die Daten im gebundenen Dataset auf beliebige Weise aktualisiert werden die <xref:Microsoft.Office.Tools.Excel.XmlMappedRange> -Steuerelement wiedergibt, die Änderungen.  
  
## <a name="formatting"></a>Formatierung  
 Sie können die gleiche Formatierung auf Anwenden eine <xref:Microsoft.Office.Tools.Excel.XmlMappedRange> Steuerelement, das Sie, um anwenden können eine <xref:Microsoft.Office.Interop.Excel.Range>. Dies umfasst, Rahmen, Schriftarten, Zahlenformate und Stile.  
  
## <a name="events"></a>Ereignisse  
 Die Ereignisse, die für die <xref:Microsoft.Office.Tools.Excel.XmlMappedRange> Steuerelement sind:  
  
-   <xref:Microsoft.Office.Tools.Excel.XmlMappedRange.BeforeDoubleClick>  
  
-   <xref:Microsoft.Office.Tools.Excel.XmlMappedRange.BeforeRightClick>  
  
-   <xref:Microsoft.Office.Tools.Excel.XmlMappedRange.BindingContextChanged>  
  
-   <xref:Microsoft.Office.Tools.Excel.XmlMappedRange.Change>  
  
-   <xref:Microsoft.Office.Tools.Excel.XmlMappedRange.Selected>  
  
-   <xref:Microsoft.Office.Tools.Excel.XmlMappedRange.Deselected>  
  
-   <xref:System.ComponentModel.Component.Disposed>  
  
-   <xref:Microsoft.Office.Tools.Excel.XmlMappedRange.SelectionChange>  
  
## <a name="see-also"></a>Siehe auch  
 [Automatisieren von Excel mithilfe von erweiterten Objekten](../vsto/automating-excel-by-using-extended-objects.md)   
 [Vorgehensweise: Hinzufügen von XMLMappedRange-Steuerelementen zu Arbeitsblättern](../vsto/how-to-add-xmlmappedrange-controls-to-worksheets.md)   
 [Binden von Daten an Steuerelemente in Office-Projektmappen](../vsto/binding-data-to-controls-in-office-solutions.md)   
 [Vorgehensweise: Zuordnen von Schemas zu Arbeitsblättern in Visual Studio](../vsto/how-to-map-schemas-to-worksheets-inside-visual-studio.md)   
 [Programmgesteuerte Einschränkungen von Hostelementen und Hoststeuerelementen](../vsto/programmatic-limitations-of-host-items-and-host-controls.md)  
  
  