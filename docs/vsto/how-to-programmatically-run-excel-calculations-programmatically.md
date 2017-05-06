---
title: "Gewusst wie: Programmgesteuertes Ausf&#252;hren von Excel-Berechnungen"
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
  - "Berechnungen, Ausführen in Excel"
  - "Excel [Office-Entwicklung in Visual Studio], Programmgesteuertes Ausführen von Berechnungen"
  - "Bereiche, Ausführen von Berechnungen"
  - "Arbeitsmappen, Ausführen von Berechnungen"
ms.assetid: 0bf30d93-8620-43ad-bfb8-f45bf3b5461f
caps.latest.revision: 38
author: "kempb"
ms.author: "kempb"
manager: "ghogen"
caps.handback.revision: 38
---
# Gewusst wie: Programmgesteuertes Ausf&#252;hren von Excel-Berechnungen
  Mit einem ähnlichen Prozess können Sie Berechnungen in einem <xref:Microsoft.Office.Tools.Excel.NamedRange>\-Steuerelement oder einem systemeigenen Excel\-Bereichsobjekt ausführen.  
  
 [!INCLUDE[appliesto_xlalldocapp](../vsto/includes/appliesto-xlalldocapp-md.md)]  
  
## Ausführen von Berechnungen in einem NamedRange\-Steuerelement  
 Im folgenden Beispiel wird in Zelle A1 ein <xref:Microsoft.Office.Tools.Excel.NamedRange> erstellt, und daraufhin wird die Zelle berechnet.  Dieser Code muss in eine Sheet\-Klasse, nicht in die `ThisWorkbook`\-Klasse eingefügt werden.  
  
#### So führen Sie Berechnungen in einem NamedRange\-Steuerelement aus  
  
1.  Erstellen Sie den benannten Bereich.  
  
     [!code-csharp[Trin_VstcoreExcelAutomation#75](../snippets/csharp/VS_Snippets_OfficeSP/Trin_VstcoreExcelAutomation/CS/Sheet1.cs#75)]
     [!code-vb[Trin_VstcoreExcelAutomation#75](../snippets/visualbasic/VS_Snippets_OfficeSP/Trin_VstcoreExcelAutomation/VB/Sheet1.vb#75)]  
  
2.  Rufen Sie die <xref:Microsoft.Office.Tools.Excel.NamedRange.Calculate%2A>\-Methode des angegebenen Bereichs auf.  
  
     [!code-csharp[Trin_VstcoreExcelAutomation#76](../snippets/csharp/VS_Snippets_OfficeSP/Trin_VstcoreExcelAutomation/CS/Sheet1.cs#76)]
     [!code-vb[Trin_VstcoreExcelAutomation#76](../snippets/visualbasic/VS_Snippets_OfficeSP/Trin_VstcoreExcelAutomation/VB/Sheet1.vb#76)]  
  
## Ausführen von Berechnungen in einem systemeigenen Excel\-Bereich  
  
#### So führen Sie Berechnungen in einem systemeigenen Excel\-Bereich aus  
  
1.  Erstellen Sie den benannten Bereich.  
  
     [!code-csharp[Trin_VstcoreExcelAutomationAddIn#30](../snippets/csharp/VS_Snippets_OfficeSP/Trin_VstcoreExcelAutomationAddIn/CS/ThisAddIn.cs#30)]
     [!code-vb[Trin_VstcoreExcelAutomationAddIn#30](../snippets/visualbasic/VS_Snippets_OfficeSP/Trin_VstcoreExcelAutomationAddIn/VB/ThisAddIn.vb#30)]  
  
2.  Rufen Sie die <xref:Microsoft.Office.Interop.Excel.Range.Calculate%2A>\-Methode des angegebenen Bereichs auf.  
  
     [!code-csharp[Trin_VstcoreExcelAutomationAddIn#31](../snippets/csharp/VS_Snippets_OfficeSP/Trin_VstcoreExcelAutomationAddIn/CS/ThisAddIn.cs#31)]
     [!code-vb[Trin_VstcoreExcelAutomationAddIn#31](../snippets/visualbasic/VS_Snippets_OfficeSP/Trin_VstcoreExcelAutomationAddIn/VB/ThisAddIn.vb#31)]  
  
## Siehe auch  
 [Arbeiten mit Bereichen](../vsto/working-with-ranges.md)   
 [NamedRange-Steuerelement](../vsto/namedrange-control.md)   
 [Optionale Parameter in Office-Lösungen](../vsto/optional-parameters-in-office-solutions.md)  
  
  