---
title: "Gewusst wie: Programmgesteuertes Verweisen auf Arbeitsblattbereiche im Code | Microsoft Docs"
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
  - "Excel [Office-Entwicklung in Visual Studio], Verweisen auf Arbeitsblattbereiche"
  - "Bereiche, Verweisen auf"
  - "Verweisen auf Arbeitsblattbereiche"
  - "Arbeitsblätter, Verweisen auf Bereiche"
ms.assetid: 113633b8-426a-4d02-b6b8-d459d1f110ea
caps.latest.revision: 46
author: "kempb"
ms.author: "kempb"
manager: "ghogen"
caps.handback.revision: 46
---
# Gewusst wie: Programmgesteuertes Verweisen auf Arbeitsblattbereiche im Code
  Mit einem ähnlichen Prozess können Sie auf den Inhalt eines <xref:Microsoft.Office.Tools.Excel.NamedRange>\-Steuerelements oder eines systemeigenen Excel\-Bereichsobjekts verweisen.  
  
 [!INCLUDE[appliesto_xlalldocapp](../vsto/includes/appliesto-xlalldocapp-md.md)]  
  
## Verwenden eines NamedRange\-Steuerelements  
 Im folgenden Beispiel wird einem Arbeitsblatt ein <xref:Microsoft.Office.Tools.Excel.NamedRange> hinzugefügt, anschließend wird der Zelle im Bereich Text hinzugefügt.  
  
#### So verweisen Sie auf ein NamedRange\-Steuerelement  
  
1.  Weisen Sie der <xref:Microsoft.Office.Tools.Excel.NamedRange.Value2%2A>\-Eigenschaft des <xref:Microsoft.Office.Tools.Excel.NamedRange>\-Steuerelements eine Zeichenfolge zu.  Dieser Code muss in eine Sheet\-Klasse, nicht in die `ThisWorkbook`\-Klasse eingefügt werden.  
  
     [!code-csharp[Trin_VstcoreExcelAutomation#46](../snippets/csharp/VS_Snippets_OfficeSP/Trin_VstcoreExcelAutomation/CS/Sheet1.cs#46)]
     [!code-vb[Trin_VstcoreExcelAutomation#46](../snippets/visualbasic/VS_Snippets_OfficeSP/Trin_VstcoreExcelAutomation/VB/Sheet1.vb#46)]  
  
## Verwenden von systemeigenen Excel\-Bereichen  
 Im folgenden Beispiel wird einem Arbeitsblatt ein systemeigener Excel\-Bereich hinzugefügt, anschließend wird der Zelle im Bereich Text hinzugefügt.  
  
#### So verweisen Sie auf ein systemeigenes Bereichsobjekt  
  
1.  Weisen Sie der <xref:Microsoft.Office.Interop.Excel.Range.Value2%2A>\-Eigenschaft des Bereichs eine Zeichenfolge zu.  
  
     [!code-csharp[Trin_VstcoreExcelAutomation#47](../snippets/csharp/VS_Snippets_OfficeSP/Trin_VstcoreExcelAutomation/CS/Sheet1.cs#47)]
     [!code-vb[Trin_VstcoreExcelAutomation#47](../snippets/visualbasic/VS_Snippets_OfficeSP/Trin_VstcoreExcelAutomation/VB/Sheet1.vb#47)]  
  
## Siehe auch  
 [Arbeiten mit Bereichen](../vsto/working-with-ranges.md)   
 [Gewusst wie: Programmgesteuertes Überprüfen der Rechtschreibung in Arbeitsblättern](../vsto/how-to-programmatically-check-spelling-in-worksheets.md)   
 [Gewusst wie: Programmgesteuertes Anwenden von Formaten auf Bereiche in Arbeitsmappen](../vsto/how-to-programmatically-apply-styles-to-ranges-in-workbooks.md)   
 [Gewusst wie: Programmgesteuertes automatisches Füllen von Bereichen mit inkrementellen Daten](../vsto/how-to-programmatically-automatically-fill-ranges-with-incrementally-changing-data.md)   
 [Gewusst wie: Programmgesteuertes Suchen nach Text in Arbeitsblattbereichen](../vsto/how-to-programmatically-search-for-text-in-worksheet-ranges.md)   
 [NamedRange-Steuerelement](../vsto/namedrange-control.md)   
 [Übersicht über Hostelemente und Hoststeuerelemente](../vsto/host-items-and-host-controls-overview.md)   
 [Programmgesteuerte Einschränkungen von Hostelementen und Hoststeuerelementen](../vsto/programmatic-limitations-of-host-items-and-host-controls.md)   
 [Optionale Parameter in Office-Lösungen](../vsto/optional-parameters-in-office-solutions.md)  
  
  