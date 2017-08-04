---
title: "XmlMappedRange-Steuerelement"
ms.custom: ""
ms.date: "02/02/2017"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "office-development"
ms.tgt_pltfrm: ""
ms.topic: "article"
dev_langs: 
  - "VB"
  - "CSharp"
helpviewer_keywords: 
  - "XMLMappedRange-Steuerelement"
  - "XMLMappedRange-Steuerelement, Datenbindung"
  - "XMLMappedRange-Steuerelement, Ereignisse"
ms.assetid: af1ae1b7-6cbe-4d6b-bc22-d9a3c8740665
caps.latest.revision: 40
author: "kempb"
ms.author: "kempb"
manager: "ghogen"
caps.handback.revision: 39
---
# XmlMappedRange-Steuerelement
  Das <xref:Microsoft.Office.Tools.Excel.XmlMappedRange>\-Steuerelement ist ein Bereich, der nur erstellt wird, wenn ein sich nicht wiederholendes Schemaelement einer Zelle in Microsoft Office Excel zugeordnet wird.  Beispielsweise, wenn das `maxOccurs`\-Attribut eines Schemaelements 1 entspricht.  Nachdem Visual Studio den zugeordneten XML\-Bereich erstellt hat, können Sie beim Programmieren direkt darauf zugreifen, ohne das Excel\-Objektmodell durchlaufen zu müssen.  Sie können ein <xref:Microsoft.Office.Tools.Excel.XmlMappedRange>\-Steuerelement in Excel nur löschen, wenn die Elementzuordnung entfernt wurde.  
  
 [!INCLUDE[appliesto_xlalldoc](../vsto/includes/appliesto-xlalldoc-md.md)]  
  
 ![Link zu Video](~/data-tools/media/playvideo.gif "Link zu Video") Eine entsprechende Videodemo finden Sie im Thema zur [Verwendung der XML\-Zuordnung in Excel](http://go.microsoft.com/fwlink/?LinkID=130288) \(möglicherweise in englischer Sprache\).  
  
## Binden von Daten an das Steuerelement  
 Ein <xref:Microsoft.Office.Tools.Excel.XmlMappedRange>\-Steuerelement unterstützt das Binden an ein einzelnes Datenfeld \(einfache Datenbindung\).  Das <xref:Microsoft.Office.Tools.Excel.ListObject>\-Steuerelement unterstützt komplexe Datenbindung und wird automatisch erstellt, wenn einer Zelle ein wiederholtes Schemaelement zugewiesen wird.  Weitere Informationen finden Sie unter [ListObject-Steuerelement](../vsto/listobject-control.md).  
  
 Das <xref:Microsoft.Office.Tools.Excel.XmlMappedRange>\-Steuerelement wird mithilfe der <xref:System.Windows.Forms.Control.DataBindings%2A>\-Eigenschaft an eine Datenquelle gebunden.  Wenn einer Zelle in einem Arbeitsblatt ein <xref:Microsoft.Office.Tools.Excel.XmlMappedRange> hinzugefügt wird, generiert Visual Studio automatisch ein Dataset aus den Daten in den zugeordneten Zellen und bindet das Steuerelement an das Dataset.  Die Datenbindungs\-Standardeigenschaft von <xref:Microsoft.Office.Tools.Excel.XmlMappedRange> ist <xref:Microsoft.Office.Tools.Excel.XmlMappedRange.Value2%2A>.  
  
 Wenn die Daten im gebundenen Dataset auf beliebige Weise aktualisiert werden, werden diese Änderungen vom <xref:Microsoft.Office.Tools.Excel.XmlMappedRange>\-Steuerelement nachvollzogen.  
  
## Formatierung  
 Die auf ein <xref:Microsoft.Office.Interop.Excel.Range>\-Steuerelement angewendete Formatierung kann auch auf ein <xref:Microsoft.Office.Tools.Excel.XmlMappedRange>\-Steuerelement angewendet werden.  Dies gilt für Rahmen, Schriftarten, Zahlenformat und Stile.  
  
## Ereignisse  
 Die folgenden Ereignisse sind für das <xref:Microsoft.Office.Tools.Excel.XmlMappedRange>\-Steuerelement verfügbar:  
  
-   <xref:Microsoft.Office.Tools.Excel.XmlMappedRange.BeforeDoubleClick>  
  
-   <xref:Microsoft.Office.Tools.Excel.XmlMappedRange.BeforeRightClick>  
  
-   <xref:Microsoft.Office.Tools.Excel.XmlMappedRange.BindingContextChanged>  
  
-   <xref:Microsoft.Office.Tools.Excel.XmlMappedRange.Change>  
  
-   <xref:Microsoft.Office.Tools.Excel.XmlMappedRange.Selected>  
  
-   <xref:Microsoft.Office.Tools.Excel.XmlMappedRange.Deselected>  
  
-   <xref:System.ComponentModel.Component.Disposed>  
  
-   <xref:Microsoft.Office.Tools.Excel.XmlMappedRange.SelectionChange>  
  
## Siehe auch  
 [Automatisieren von Excel mithilfe von erweiterten Objekten](../vsto/automating-excel-by-using-extended-objects.md)   
 [Gewusst wie: Hinzufügen von XMLMappedRange-Steuerelementen zu Arbeitsblättern](../vsto/how-to-add-xmlmappedrange-controls-to-worksheets.md)   
 [Binden von Daten an Steuerelemente in Office-Projektmappen](../vsto/binding-data-to-controls-in-office-solutions.md)   
 [Gewusst wie: Zuordnen von Schemas zu Arbeitsblättern in Visual Studio](../vsto/how-to-map-schemas-to-worksheets-inside-visual-studio.md)   
 [Programmgesteuerte Einschränkungen von Hostelementen und Hoststeuerelementen](../vsto/programmatic-limitations-of-host-items-and-host-controls.md)  
  
  