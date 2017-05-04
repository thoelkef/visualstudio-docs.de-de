---
title: "Gewusst wie: &#196;ndern der Gr&#246;&#223;e von NamedRange-Steuerelementen | Microsoft Docs"
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
  - "NamedRange-Steuerelement, Größenänderung"
  - "Bereiche, Größenänderung in Excel"
ms.assetid: 7d6f0b2f-be46-49b7-9f38-b4c8849683f7
caps.latest.revision: 48
author: "kempb"
ms.author: "kempb"
manager: "ghogen"
caps.handback.revision: 44
---
# Gewusst wie: &#196;ndern der Gr&#246;&#223;e von NamedRange-Steuerelementen
  Sie können die Größe eines <xref:Microsoft.Office.Tools.Excel.NamedRange>\-Steuerelements festlegen, wenn Sie es zu einem Microsoft Office Excel\-Dokument hinzufügen. Möglicherweise möchten Sie jedoch zu einem späteren Zeitpunkt die Größe ändern.  
  
 [!INCLUDE[appliesto_xlalldocapp](../vsto/includes/appliesto-xlalldocapp-md.md)]  
  
 Sie können einen benannten Bereich in Projekten auf Dokumentebene zur Entwurfszeit oder zur Laufzeit ändern. Sie können benannte Bereiche in VSTO\-Add\-Ins auf Anwendungsebene auch zur Laufzeit ändern.  
  
 In diesem Thema werden die folgenden Aufgaben beschrieben:  
  
-   [Ändern der Größe von NamedRange\-Steuerelementen zur Entwurfszeit](#designtime)  
  
-   [Ändern der Größe von NamedRange\-Steuerelementen zur Laufzeit in einem Projekt auf Dokumentebene](#runtimedoclevel)  
  
-   [Ändern der Größe von NamedRange\-Steuerelementen zur Laufzeit in einem VSTO\-Add\-In\-Projekt](#runtimeaddin)  
  
##  <a name="designtime"></a> Ändern der Größe von NamedRange\-Steuerelementen zur Entwurfszeit  
 Sie können die Größe eines benannten Bereichs ändern, indem Sie die Größe im Dialogfeld **Namen definieren** neu definieren.  
  
#### So ändern Sie die Größe eines benannten Bereichs unter Verwendung des Dialogfelds „Namen definieren“  
  
1.  Klicken Sie mit der rechten Maustaste auf ein <xref:Microsoft.Office.Tools.Excel.NamedRange>\-Steuerelement.  
  
2.  Klicken Sie im Kontextmenü auf **Benannte Bereiche verwalten**.  
  
     Das Dialogfeld **Namen definieren** wird geöffnet.  
  
3.  Wählen Sie den benannten Bereich aus, dessen Größe Sie ändern möchten.  
  
4.  Deaktivieren Sie das Feld **Bezieht sich auf**.  
  
5.  Wählen Sie die Zellen aus, anhand derer Sie die Größe des benannten Bereichs definieren möchten.  
  
6.  Klicken Sie auf **OK**.  
  
##  <a name="runtimedoclevel"></a> Ändern der Größe von NamedRange\-Steuerelementen zur Laufzeit in einem Projekt auf Dokumentebene  
 Sie können die Größe eines benannten Bereichs programmgesteuert ändern, indem Sie die <xref:Microsoft.Office.Tools.Excel.NamedRange.RefersTo%2A>\-Eigenschaft verwenden.  
  
> [!NOTE]  
>  Im Fenster **Eigenschaften** ist die <xref:Microsoft.Office.Tools.Excel.NamedRange.RefersTo%2A>\-Eigenschaft als schreibgeschützt markiert.  
  
#### So ändern Sie die Größe eines benannten Bereichs programmgesteuert  
  
1.  Erstellen Sie in der Zelle **A1** von `Sheet1` ein <xref:Microsoft.Office.Tools.Excel.NamedRange>\-Steuerelement.  
  
     [!code-csharp[Trin_VstcoreHostControlsExcel#4](../snippets/csharp/VS_Snippets_OfficeSP/Trin_VstcoreHostControlsExcel/CS/Sheet1.cs#4)]
     [!code-vb[Trin_VstcoreHostControlsExcel#4](../snippets/visualbasic/VS_Snippets_OfficeSP/Trin_VstcoreHostControlsExcel/VB/Sheet1.vb#4)]  
  
2.  Ändern Sie die Größe des benannten Bereichs, sodass er auch Zelle **B1** umfasst.  
  
     [!code-csharp[Trin_VstcoreHostControlsExcel#5](../snippets/csharp/VS_Snippets_OfficeSP/Trin_VstcoreHostControlsExcel/CS/Sheet1.cs#5)]
     [!code-vb[Trin_VstcoreHostControlsExcel#5](../snippets/visualbasic/VS_Snippets_OfficeSP/Trin_VstcoreHostControlsExcel/VB/Sheet1.vb#5)]  
  
##  <a name="runtimeaddin"></a> Ändern der Größe von NamedRange\-Steuerelementen zur Laufzeit in einem VSTO\-Add\-In\-Projekt  
 Sie können die Größe eines <xref:Microsoft.Office.Tools.Excel.NamedRange>\-Steuerelements in jedem beliebigen geöffneten Arbeitsblatt zur Laufzeit ändern. Weitere Informationen zum Hinzufügen eines <xref:Microsoft.Office.Tools.Excel.NamedRange>\-Steuerelements zu einem Arbeitsblatt mit einem VSTO\-Add\-In finden Sie unter [Gewusst wie: Hinzufügen von NamedRange-Steuerelementen zu Arbeitsblättern](../vsto/how-to-add-namedrange-controls-to-worksheets.md).  
  
#### So ändern Sie die Größe eines benannten Bereichs programmgesteuert  
  
1.  Erstellen Sie in der Zelle **A1** von `Sheet1` ein <xref:Microsoft.Office.Tools.Excel.NamedRange>\-Steuerelement.  
  
     [!code-csharp[Trin_Excel_Dynamic_Controls#10](../snippets/csharp/VS_Snippets_OfficeSP/Trin_Excel_Dynamic_Controls/CS/ThisAddIn.cs#10)]
     [!code-vb[Trin_Excel_Dynamic_Controls#10](../snippets/visualbasic/VS_Snippets_OfficeSP/Trin_Excel_Dynamic_Controls/VB/ThisAddIn.vb#10)]  
  
2.  Ändern Sie die Größe des benannten Bereichs, sodass er auch Zelle **B1** umfasst.  
  
     [!code-csharp[Trin_Excel_Dynamic_Controls#11](../snippets/csharp/VS_Snippets_OfficeSP/Trin_Excel_Dynamic_Controls/CS/ThisAddIn.cs#11)]
     [!code-vb[Trin_Excel_Dynamic_Controls#11](../snippets/visualbasic/VS_Snippets_OfficeSP/Trin_Excel_Dynamic_Controls/VB/ThisAddIn.vb#11)]  
  
## Siehe auch  
 [Erweitern von Word-Dokumenten und Excel-Arbeitsmappen in VSTO-Add-Ins zur Laufzeit](../vsto/extending-word-documents-and-excel-workbooks-in-vsto-add-ins-at-run-time.md)   
 [Hinzufügen von Steuerelementen zu Office-Dokumenten zur Laufzeit](../vsto/adding-controls-to-office-documents-at-run-time.md)   
 [Steuerelemente für Office-Dokumente](../vsto/controls-on-office-documents.md)   
 [Übersicht über Hostelemente und Hoststeuerelemente](../vsto/host-items-and-host-controls-overview.md)   
 [Automatisieren von Excel mithilfe von erweiterten Objekten](../vsto/automating-excel-by-using-extended-objects.md)   
 [NamedRange-Steuerelement](../vsto/namedrange-control.md)   
 [Gewusst wie: Hinzufügen von NamedRange-Steuerelementen zu Arbeitsblättern](../vsto/how-to-add-namedrange-controls-to-worksheets.md)   
 [Gewusst wie: Ändern der Größe von Bookmark-Steuerelementen](../vsto/how-to-resize-bookmark-controls.md)   
 [Gewusst wie: Ändern der Größe von ListObject-Steuerelementen](../vsto/how-to-resize-listobject-controls.md)  
  
  