---
title: XmlMappedRange-Steuerelement | Microsoft Docs
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
- XMLMappedRange control, data binding
- XMLMappedRange control
- XMLMappedRange control, events
ms.assetid: af1ae1b7-6cbe-4d6b-bc22-d9a3c8740665
caps.latest.revision: "40"
author: gewarren
ms.author: gewarren
manager: ghogen
ms.workload: office
ms.openlocfilehash: 27cd0f62c7670d56143180d24074e5c6002051f7
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 12/22/2017
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
  
  