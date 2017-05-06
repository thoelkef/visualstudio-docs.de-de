---
title: "Gewusst wie: F&#252;llen eines ListObject-Steuerelements mit Daten"
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
  - "Trennen von Datenquellen"
  - "ListObject-Steuerelement, Trennen von einer Datenquelle"
  - "ListObject-Steuerelement, Füllen mit Daten"
  - "Daten [Office-Entwicklung in Visual Studio], Hinzufügen zu Arbeitsblättern"
  - "Datenbindung, ListObject-Steuerelemente"
  - "Arbeitsblätter, Füllen mit Daten"
ms.assetid: bf692c77-f5cc-456a-9a5c-84ed3067d7eb
caps.latest.revision: 27
author: "kempb"
ms.author: "kempb"
manager: "ghogen"
caps.handback.revision: 26
---
# Gewusst wie: F&#252;llen eines ListObject-Steuerelements mit Daten
  Sie können die Datenbindung als Möglichkeit zum schnellen Hinzufügen von Daten zu Ihrem Dokument verwenden. Nach dem Binden der Daten an ein Listenobjekt können Sie das Listenobjekt trennen, damit es die Daten anzeigt, aber nicht länger an die Datenquelle gebunden ist.  
  
 [!INCLUDE[appliesto_xlalldocapp](../vsto/includes/appliesto-xlalldocapp-md.md)]  
  
 ![Link zu Video](../vsto/media/playvideo.png "Link zu Video") Eine entsprechende Videodemo finden Sie unter [Wie erstelle ich eine Liste in Excel, die mit einer SharePoint\-Liste verbunden ist?](http://go.microsoft.com/fwlink/?LinkID=130263).  
  
### So binden Sie Daten an ein ListObject\-Steuerelement  
  
1.  Erstellen Sie eine <xref:System.Data.DataTable> auf Klassenebene.  
  
     [!code-csharp[Trin_VstcoreHostControlsExcel#20](../snippets/csharp/VS_Snippets_OfficeSP/Trin_VstcoreHostControlsExcel/CS/Sheet4.cs#20)]
     [!code-vb[Trin_VstcoreHostControlsExcel#20](../snippets/visualbasic/VS_Snippets_OfficeSP/Trin_VstcoreHostControlsExcel/VB/Sheet4.vb#20)]  
  
2.  Fügen Sie Beispielspalten und Daten im `Startup`\-Ereignishandler der `Sheet1`\-Klasse \(in einem Projekt auf Dokumentebene\) oder der `ThisAddIn`\-Klasse \(in einem Projekt auf Anwendungsebene\) hinzu.  
  
     [!code-csharp[Trin_VstcoreHostControlsExcel#21](../snippets/csharp/VS_Snippets_OfficeSP/Trin_VstcoreHostControlsExcel/CS/Sheet4.cs#21)]
     [!code-vb[Trin_VstcoreHostControlsExcel#21](../snippets/visualbasic/VS_Snippets_OfficeSP/Trin_VstcoreHostControlsExcel/VB/Sheet4.vb#21)]  
  
3.  Rufen Sie die <xref:Microsoft.Office.Tools.Excel.ListObject.SetDataBinding%2A>\-Methode auf, und übergeben Sie die Spaltennamen in der Reihenfolge, in der sie angezeigt werden sollen. Die Reihenfolge der Spalten im Listenobjekt kann von der Reihenfolge abweichen, in der sie in der <xref:System.Data.DataTable> angezeigt werden.  
  
     [!code-csharp[Trin_VstcoreHostControlsExcel#22](../snippets/csharp/VS_Snippets_OfficeSP/Trin_VstcoreHostControlsExcel/CS/Sheet4.cs#22)]
     [!code-vb[Trin_VstcoreHostControlsExcel#22](../snippets/visualbasic/VS_Snippets_OfficeSP/Trin_VstcoreHostControlsExcel/VB/Sheet4.vb#22)]  
  
### So trennen Sie das ListObject\-Steuerelement von der Datenquelle  
  
1.  Rufen Sie die <xref:Microsoft.Office.Tools.Excel.ListObject.Disconnect%2A>\-Methode von `List1` auf.  
  
     [!code-csharp[Trin_VstcoreHostControlsExcel#23](../snippets/csharp/VS_Snippets_OfficeSP/Trin_VstcoreHostControlsExcel/CS/Sheet4.cs#23)]
     [!code-vb[Trin_VstcoreHostControlsExcel#23](../snippets/visualbasic/VS_Snippets_OfficeSP/Trin_VstcoreHostControlsExcel/VB/Sheet4.vb#23)]  
  
## Kompilieren des Codes  
 In diesem Codebeispiel wird davon ausgegangen, dass Sie in dem Arbeitsblatt, in dem dieser Code angezeigt wird, über ein <xref:Microsoft.Office.Tools.Excel.ListObject> namens `list1` verfügen.  
  
## Siehe auch  
 [Erweitern von Word-Dokumenten und Excel-Arbeitsmappen in VSTO-Add-Ins zur Laufzeit](../vsto/extending-word-documents-and-excel-workbooks-in-vsto-add-ins-at-run-time.md)   
 [Steuerelemente für Office-Dokumente](../vsto/controls-on-office-documents.md)   
 [Hinzufügen von Steuerelementen zu Office-Dokumenten zur Laufzeit](../vsto/adding-controls-to-office-documents-at-run-time.md)   
 [Gewusst wie: Zuordnung von ListObject-Spalten zu Daten](../vsto/how-to-map-listobject-columns-to-data.md)   
 [Automatisieren von Excel mithilfe von erweiterten Objekten](../vsto/automating-excel-by-using-extended-objects.md)   
 [ListObject-Steuerelement](../vsto/listobject-control.md)   
 [Binden von Daten an Steuerelemente in Office-Projektmappen](../vsto/binding-data-to-controls-in-office-solutions.md)   
 [Gewusst wie: Auffüllen von Arbeitsblättern mit Daten aus einer Datenbank](../vsto/how-to-populate-worksheets-with-data-from-a-database.md)   
 [Gewusst wie: Auffüllen von Dokumente mit Daten aus Diensten](../vsto/how-to-populate-documents-with-data-from-services.md)  
  
  