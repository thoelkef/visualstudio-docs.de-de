---
title: "Gewusst wie: &#196;ndern der Gr&#246;&#223;e von ListObject-Steuerelementen"
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
  - "Steuerelemente [Office-Entwicklung in Visual Studio], Größenänderung"
  - "ListObject-Steuerelement, Größenänderung"
ms.assetid: a4c7dceb-7b55-447e-9b88-c3596a2fc361
caps.latest.revision: 50
author: "kempb"
ms.author: "kempb"
manager: "ghogen"
caps.handback.revision: 46
---
# Gewusst wie: &#196;ndern der Gr&#246;&#223;e von ListObject-Steuerelementen
  Sie legen die Größe eines <xref:Microsoft.Office.Tools.Excel.ListObject>\-Steuerelements fest, wenn Sie es einer Microsoft Office Excel\-Arbeitsmappe hinzufügen. Möglicherweise möchten Sie dessen Größe jedoch zu einem späteren Zeitpunkt ändern. Beispielsweise könnte es sein, dass Sie eine zweispaltige Liste in eine dreispaltige Liste ändern möchten.  
  
 [!INCLUDE[appliesto_xlalldocapp](../vsto/includes/appliesto-xlalldocapp-md.md)]  
  
 Sie können die Größe eines <xref:Microsoft.Office.Tools.Excel.ListObject>\-Steuerelements in einem Projekt auf Dokumentebene zur Entwurfszeit oder zur Laufzeit ändern. Sie können die Größe eines <xref:Microsoft.Office.Tools.Excel.ListObject>\-Steuerelements in einem VSTO\-Add\-In\-Projekt zur Laufzeit ändern.  
  
 In diesem Thema werden die folgenden Aufgaben beschrieben:  
  
-   [Ändern der Größe eines ListObject\-Steuerelements zur Entwurfszeit](#designtime)  
  
-   [Ändern der Größe eines ListObject\-Steuerelements zur Laufzeit in einem Projekt auf Dokumentebene](#runtimedoclevel)  
  
-   [Ändern der Größe eines ListObject\-Steuerelements zur Laufzeit in einem VSTO\-Add\-In\-Projekt](#runtimeaddin)  
  
 Weitere Informationen zu <xref:Microsoft.Office.Tools.Excel.ListObject>\-Steuerelementen finden Sie unter [ListObject-Steuerelement](../vsto/listobject-control.md).  
  
 ![Link zu Video](~/docs/data-tools/media/playvideo.gif "Link zu Video") Eine entsprechende Videodemo finden Sie unter [How Do I: Add Columns to a Data\-Bound List Object at RunTime?](http://go.microsoft.com/fwlink/?LinkID=130318).  
  
##  <a name="designtime"></a> Ändern der Größe eines ListObject\-Steuerelements zur Entwurfszeit  
 Sie können die Größe einer Liste ändern, indem Sie auf einen der Ziehpunkte klicken und diesen ziehen oder indem Sie die Größe im Dialogfeld **Größe der Liste ändern** neu definieren.  
  
#### So ändern Sie die Größe einer Liste im Dialogfeld „Größe der Liste ändern“  
  
1.  Klicken Sie mit der rechten Maustaste auf ein <xref:Microsoft.Office.Tools.Excel.ListObject>\-Steuerelement.  
  
2.  Zeigen Sie im Kontextmenü auf **Liste**, und wählen Sie dann **Größe der Liste ändern** aus.  
  
3.  Wählen Sie die Zellen aus, anhand derer Sie die Größe der Liste definieren möchten.  
  
4.  Klicken Sie auf **OK**.  
  
##  <a name="runtimedoclevel"></a> Ändern der Größe eines ListObject\-Steuerelements zur Laufzeit in einem Projekt auf Dokumentebene  
 Sie können die Größe eines <xref:Microsoft.Office.Tools.Excel.ListObject>\-Steuerelements zur Laufzeit ändern, indem Sie die <xref:Microsoft.Office.Tools.Excel.ListObject.Resize%2A>\-Methode verwenden. Mit dieser Methode ist es jedoch nicht möglich, das <xref:Microsoft.Office.Tools.Excel.ListObject>\-Steuerelement auf eine neue Position auf dem Arbeitsblatt zu verschieben. Die Überschriften müssen in derselben Zeile bleiben, und das in der Größe geänderte <xref:Microsoft.Office.Tools.Excel.ListObject>\-Steuerelement muss das ursprüngliche Listenobjekt überlappen. Das in der Größe geänderte <xref:Microsoft.Office.Tools.Excel.ListObject>\-Steuerelement muss eine Überschriftenzeile und mindestens eine Zeile mit Daten enthalten.  
  
#### So ändern Sie die Größe eines Listenobjekts programmgesteuert  
  
1.  Erstellen Sie ein <xref:Microsoft.Office.Tools.Excel.ListObject>\-Steuerelement, das sich auf `Sheet1` über die Zellen **A1** bis **B3** erstreckt.  
  
     [!code-csharp[Trin_VstcoreHostControlsExcel#6](../snippets/csharp/VS_Snippets_OfficeSP/Trin_VstcoreHostControlsExcel/CS/Sheet1.cs#6)]
     [!code-vb[Trin_VstcoreHostControlsExcel#6](../snippets/visualbasic/VS_Snippets_OfficeSP/Trin_VstcoreHostControlsExcel/VB/Sheet1.vb#6)]  
  
2.  Ändern Sie die Größe der Liste, sodass sie die Zellen **A1** bis **C5** umfasst.  
  
     [!code-csharp[Trin_VstcoreHostControlsExcel#7](../snippets/csharp/VS_Snippets_OfficeSP/Trin_VstcoreHostControlsExcel/CS/Sheet1.cs#7)]
     [!code-vb[Trin_VstcoreHostControlsExcel#7](../snippets/visualbasic/VS_Snippets_OfficeSP/Trin_VstcoreHostControlsExcel/VB/Sheet1.vb#7)]  
  
##  <a name="runtimeaddin"></a> Ändern der Größe eines ListObject zur Laufzeit in einem VSTO\-Add\-In\-Projekt  
 Sie können die Größe eines <xref:Microsoft.Office.Tools.Excel.ListObject>\-Steuerelements in jedem beliebigen geöffneten Arbeitsblatt zur Laufzeit ändern. Weitere Informationen zum Hinzufügen eines <xref:Microsoft.Office.Tools.Excel.ListObject>\-Steuerelements zu einem Arbeitsblatt mit einem VSTO\-Add\-In finden Sie unter [Gewusst wie: Hinzufügen von ListObject-Steuerelementen zu Arbeitsblättern](../vsto/how-to-add-listobject-controls-to-worksheets.md).  
  
#### So ändern Sie die Größe eines Listenobjekts programmgesteuert  
  
1.  Erstellen Sie ein <xref:Microsoft.Office.Tools.Excel.ListObject>\-Steuerelement, das sich auf `Sheet1` über die Zellen **A1** bis **B3** erstreckt.  
  
     [!code-csharp[Trin_Excel_Dynamic_Controls#12](../snippets/csharp/VS_Snippets_OfficeSP/Trin_Excel_Dynamic_Controls/CS/ThisAddIn.cs#12)]
     [!code-vb[Trin_Excel_Dynamic_Controls#12](../snippets/visualbasic/VS_Snippets_OfficeSP/Trin_Excel_Dynamic_Controls/VB/ThisAddIn.vb#12)]  
  
2.  Ändern Sie die Größe der Liste, sodass sie die Zellen **A1** bis **C5** umfasst.  
  
     [!code-csharp[Trin_Excel_Dynamic_Controls#13](../snippets/csharp/VS_Snippets_OfficeSP/Trin_Excel_Dynamic_Controls/CS/ThisAddIn.cs#13)]
     [!code-vb[Trin_Excel_Dynamic_Controls#13](../snippets/visualbasic/VS_Snippets_OfficeSP/Trin_Excel_Dynamic_Controls/VB/ThisAddIn.vb#13)]  
  
## Siehe auch  
 [Erweitern von Word-Dokumenten und Excel-Arbeitsmappen in VSTO-Add-Ins zur Laufzeit](../vsto/extending-word-documents-and-excel-workbooks-in-vsto-add-ins-at-run-time.md)   
 [Steuerelemente für Office-Dokumente](../vsto/controls-on-office-documents.md)   
 [Hinzufügen von Steuerelementen zu Office-Dokumenten zur Laufzeit](../vsto/adding-controls-to-office-documents-at-run-time.md)   
 [Übersicht über Hostelemente und Hoststeuerelemente](../vsto/host-items-and-host-controls-overview.md)   
 [Automatisieren von Excel mithilfe von erweiterten Objekten](../vsto/automating-excel-by-using-extended-objects.md)   
 [ListObject-Steuerelement](../vsto/listobject-control.md)   
 [Gewusst wie: Hinzufügen von ListObject-Steuerelementen zu Arbeitsblättern](../vsto/how-to-add-listobject-controls-to-worksheets.md)   
 [Gewusst wie: Ändern der Größe von Bookmark-Steuerelementen](../vsto/how-to-resize-bookmark-controls.md)   
 [Gewusst wie: Ändern der Größe von NamedRange-Steuerelementen](../vsto/how-to-resize-namedrange-controls.md)  
  
  