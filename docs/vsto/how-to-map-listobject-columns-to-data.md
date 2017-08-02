---
title: "Gewusst wie: Zuordnung von ListObject-Spalten zu Daten"
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
  - "Daten [Office-Entwicklung in Visual Studio], Zuordnen zu ListObject-Spalte"
  - "ListObject-Steuerelement, Zuordnen von Daten"
ms.assetid: 2108d0c3-d595-410e-a0ae-3dd53bf6bcc7
caps.latest.revision: 36
author: "kempb"
ms.author: "kempb"
manager: "ghogen"
caps.handback.revision: 35
---
# Gewusst wie: Zuordnung von ListObject-Spalten zu Daten
  Beim Binden eines <xref:Microsoft.Office.Tools.Excel.ListObject>\-Steuerelements an <xref:System.Data.DataTable> sollen möglicherweise nicht alle Spalten in einer Liste angezeigt werden, oder Sie verfügen u. U. über bestimmte Spalten, die nicht an Daten gebunden sind. Durch den Aufruf der <xref:Microsoft.Office.Tools.Excel.ListObject.SetDataBinding%2A>\-Methode können Sie die Spalten zuordnen, die in <xref:Microsoft.Office.Tools.Excel.ListObject> angezeigt werden sollen.  
  
 [!INCLUDE[appliesto_xlalldocapp](../vsto/includes/appliesto-xlalldocapp-md.md)]  
  
 ![Link zu Video](~/docs/data-tools/media/playvideo.gif "Link zu Video") Eine entsprechende Videodemo finden Sie unter [Wie erstelle ich eine Liste in Excel, die mit einer SharePoint\-Liste verbunden ist?](http://go.microsoft.com/fwlink/?LinkID=130263).  
  
## Zuordnen von Spalten  
  
#### So ordnen Sie eine Datentabelle Spalten in einer Liste zu  
  
1.  Erstellen Sie <xref:System.Data.DataTable> auf Klassenebene.  
  
     [!code-csharp[Trin_VstcoreHostControlsExcel#16](../snippets/csharp/VS_Snippets_OfficeSP/Trin_VstcoreHostControlsExcel/CS/Sheet3.cs#16)]
     [!code-vb[Trin_VstcoreHostControlsExcel#16](../snippets/visualbasic/VS_Snippets_OfficeSP/Trin_VstcoreHostControlsExcel/VB/Sheet3.vb#16)]  
  
2.  Fügen Sie Beispielspalten und Daten im `Startup`\-Ereignishandler der `Sheet1`\-Klasse \(in einem Projekt auf Dokumentebene\) oder der `ThisAddIn`\-Klasse \(in einem VSTO\-Add\-in\-Projekt\) hinzu.  
  
     [!code-csharp[Trin_VstcoreHostControlsExcel#17](../snippets/csharp/VS_Snippets_OfficeSP/Trin_VstcoreHostControlsExcel/CS/Sheet3.cs#17)]
     [!code-vb[Trin_VstcoreHostControlsExcel#17](../snippets/visualbasic/VS_Snippets_OfficeSP/Trin_VstcoreHostControlsExcel/VB/Sheet3.vb#17)]  
  
3.  Rufen Sie die <xref:Microsoft.Office.Tools.Excel.ListObject.SetDataBinding%2A>\-Methode auf, und übergeben Sie die Spaltennamen in der Reihenfolge, in der sie angezeigt werden sollen. Das Listenobjekt wird an die neu erstellte <xref:System.Data.DataTable> gebunden, die Reihenfolge der Spalten im Listenobjekt unterscheidet sich aber von der Reihenfolge, in der Sie in <xref:System.Data.DataTable> angezeigt werden.  
  
     [!code-csharp[Trin_VstcoreHostControlsExcel#18](../snippets/csharp/VS_Snippets_OfficeSP/Trin_VstcoreHostControlsExcel/CS/Sheet3.cs#18)]
     [!code-vb[Trin_VstcoreHostControlsExcel#18](../snippets/visualbasic/VS_Snippets_OfficeSP/Trin_VstcoreHostControlsExcel/VB/Sheet3.vb#18)]  
  
## Angeben von nicht zugeordneten Spalten  
 Beim Zuordnen von Spalten zu <xref:System.Data.DataTable> können Sie auch angeben, dass bestimmte Spalten nicht an Daten gebunden werden sollen, indem Sie eine leere Zeichenfolge übergeben. In diesem Fall wird dem <xref:Microsoft.Office.Tools.Excel.ListObject>\-Steuerelement eine neue Spalte hinzugefügt, die nicht an Daten gebunden ist.  
  
#### So geben Sie beim Zuordnen von ListObject\-Spalten eine nicht zugeordnete Spalte an  
  
1.  Rufen Sie die <xref:Microsoft.Office.Tools.Excel.ListObject.SetDataBinding%2A>\-Methode auf, und übergeben Sie die Spaltennamen in der Reihenfolge, in der sie angezeigt werden sollen. Verwenden Sie eine leere Zeichenfolge, um anzugeben, wo eine nicht zugeordnete Spalte hinzugefügt wird: in diesem Fall zwischen der Spalte für den Titel und der Spalte für den Nachnamen.  
  
     [!code-csharp[Trin_VstcoreHostControlsExcel#19](../snippets/csharp/VS_Snippets_OfficeSP/Trin_VstcoreHostControlsExcel/CS/Sheet3.cs#19)]
     [!code-vb[Trin_VstcoreHostControlsExcel#19](../snippets/visualbasic/VS_Snippets_OfficeSP/Trin_VstcoreHostControlsExcel/VB/Sheet3.vb#19)]  
  
## Kompilieren des Codes  
 In diesem Codebeispiel wird davon ausgegangen, dass Sie in dem Arbeitsblatt, in dem dieser Code angezeigt wird, über ein <xref:Microsoft.Office.Tools.Excel.ListObject> namens `list1` verfügen.  
  
## Siehe auch  
 [Erweitern von Word-Dokumenten und Excel-Arbeitsmappen in VSTO-Add-Ins zur Laufzeit](../vsto/extending-word-documents-and-excel-workbooks-in-vsto-add-ins-at-run-time.md)   
 [Steuerelemente für Office-Dokumente](../vsto/controls-on-office-documents.md)   
 [Hinzufügen von Steuerelementen zu Office-Dokumenten zur Laufzeit](../vsto/adding-controls-to-office-documents-at-run-time.md)   
 [Gewusst wie: Füllen eines ListObject-Steuerelements mit Daten](../vsto/how-to-fill-listobject-controls-with-data.md)   
 [Automatisieren von Excel mithilfe von erweiterten Objekten](../vsto/automating-excel-by-using-extended-objects.md)   
 [ListObject-Steuerelement](../vsto/listobject-control.md)  
  
  