---
title: "Gewusst wie: Programmgesteuertes Sortieren von Daten in Arbeitsbl&#228;ttern | Microsoft Docs"
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
  - "Daten [Office-Entwicklung in Visual Studio], Sortieren in Arbeitsblättern"
  - "Datensortierung, Arbeitsblätter"
  - "Sortieren von Daten, In Arbeitsblättern"
  - "Arbeitsblätter, Sortieren von Daten"
ms.assetid: 2fbc6e63-02ea-4624-8d6f-bed60e06c61e
caps.latest.revision: 56
author: "kempb"
ms.author: "kempb"
manager: "ghogen"
caps.handback.revision: 55
---
# Gewusst wie: Programmgesteuertes Sortieren von Daten in Arbeitsbl&#228;ttern
  Sie können Daten sortieren, die zur Laufzeit in Arbeitsblattbereichen und \-listen enthalten sind.  Der folgende Code sortiert einen mehrspaltigen Bereich namens `Fruits` nach den Daten in der ersten Spalte und anschließend nach den Daten in der zweiten Spalte.  
  
 [!INCLUDE[appliesto_xlalldocapp](../vsto/includes/appliesto-xlalldocapp-md.md)]  
  
## Sortieren von Daten in einer Anpassung auf Dokumentebene  
  
#### So sortieren Sie Daten in einem NamedRange\-Steuerelement  
  
1.  Rufen Sie die <xref:Microsoft.Office.Tools.Excel.NamedRange.Sort%2A>\-Methode des <xref:Microsoft.Office.Tools.Excel.NamedRange>\-Steuerelements auf.  Das folgende Beispiel erfordert ein <xref:Microsoft.Office.Tools.Excel.NamedRange>\-Steuerelement namens `Fruits` in einem Arbeitsblatt.  Dieser Code muss in einer Sheet\-Klasse platziert werden und nicht in der `ThisWorkbook`\-Klasse.  
  
     [!code-csharp[Trin_VstcoreExcelAutomation#78](../snippets/csharp/VS_Snippets_OfficeSP/Trin_VstcoreExcelAutomation/CS/Sheet1.cs#78)]
     [!code-vb[Trin_VstcoreExcelAutomation#78](../snippets/visualbasic/VS_Snippets_OfficeSP/Trin_VstcoreExcelAutomation/VB/Sheet1.vb#78)]  
  
 Fügen Sie folgenden Code in Sheet1.vb oder Sheet1.cs ein, um Daten in einem <xref:Microsoft.Office.Tools.Excel.ListObject>\-Steuerelement zu sortieren.  Der Code setzt voraus, dass Sie über ein <xref:Microsoft.Office.Tools.Excel.ListObject>\-Steuerelement namens `fruitList`in einem Arbeitsblatt namens `Sheet1` verfügen.  
  
#### So sortieren Sie Daten in einem ListObject\-Steuerelement  
  
1.  Rufen Sie die <xref:Microsoft.Office.Interop.Excel.Range.Sort%2A>\-Methode der <xref:Microsoft.Office.Tools.Excel.ListObject.Range%2A>\-Eigenschaft des <xref:Microsoft.Office.Tools.Excel.ListObject>\-Hoststeuerelements auf.  
  
     [!code-csharp[Trin_VstcoreExcelAutomation#79](../snippets/csharp/VS_Snippets_OfficeSP/Trin_VstcoreExcelAutomation/CS/Sheet1.cs#79)]
     [!code-vb[Trin_VstcoreExcelAutomation#79](../snippets/visualbasic/VS_Snippets_OfficeSP/Trin_VstcoreExcelAutomation/VB/Sheet1.vb#79)]  
  
## Sortieren von Daten in einem VSTO\-Add\-In  
  
#### So sortieren Sie Daten in einem systemeigenen Bereich  
  
1.  Rufen Sie die <xref:Microsoft.Office.Interop.Excel.Range.Sort%2A>\-Methode des systemeigenen Excel\-<xref:Microsoft.Office.Interop.Excel.Range>\-Steuerelements auf.  Das folgende Beispiel erfordert ein systemeigenes Excel\-Steuerelement namens `Fruits` in einem Arbeitsblatt.  
  
     [!code-csharp[Trin_VstcoreExcelAutomationAddIn#23](../snippets/csharp/VS_Snippets_OfficeSP/Trin_VstcoreExcelAutomationAddIn/CS/ThisAddIn.cs#23)]
     [!code-vb[Trin_VstcoreExcelAutomationAddIn#23](../snippets/visualbasic/VS_Snippets_OfficeSP/Trin_VstcoreExcelAutomationAddIn/VB/ThisAddIn.vb#23)]  
  
#### So sortieren Sie Daten in einem ListObject\-Steuerelement  
  
1.  Rufen Sie die <xref:Microsoft.Office.Interop.Excel.Range.Sort%2A>\-Methode der <xref:Microsoft.Office.Tools.Excel.ListObject.Range%2A>\-Eigenschaft des systemeigenen Excel\-<xref:Microsoft.Office.Interop.Excel.ListObject>\-Steuerelements auf.  Im folgenden Beispiel wird vorausgesetzt, dass Sie über ein systemeigenes Excel\-<xref:Microsoft.Office.Interop.Excel.ListObject>\-Steuerelement namens `fruitList` im aktiven Arbeitsblatt verfügen.  
  
     [!code-csharp[Trin_VstcoreExcelAutomationAddIn#24](../snippets/csharp/VS_Snippets_OfficeSP/Trin_VstcoreExcelAutomationAddIn/CS/ThisAddIn.cs#24)]
     [!code-vb[Trin_VstcoreExcelAutomationAddIn#24](../snippets/visualbasic/VS_Snippets_OfficeSP/Trin_VstcoreExcelAutomationAddIn/VB/ThisAddIn.vb#24)]  
  
## Siehe auch  
 [Arbeiten mit Arbeitsblättern](../vsto/working-with-worksheets.md)   
 [Gewusst wie: Programmgesteuertes automatisches Füllen von Bereichen mit inkrementellen Daten](../vsto/how-to-programmatically-automatically-fill-ranges-with-incrementally-changing-data.md)   
 [Gewusst wie: Programmgesteuertes Verweisen auf Arbeitsblattbereiche im Code](../vsto/how-to-programmatically-refer-to-worksheet-ranges-in-code.md)   
 [Gewusst wie: Programmgesteuertes Anwenden von Formaten auf Bereiche in Arbeitsmappen](../vsto/how-to-programmatically-apply-styles-to-ranges-in-workbooks.md)   
 [NamedRange-Steuerelement](../vsto/namedrange-control.md)   
 [ListObject-Steuerelement](../vsto/listobject-control.md)   
 [Optionale Parameter in Office-Lösungen](../vsto/optional-parameters-in-office-solutions.md)  
  
  