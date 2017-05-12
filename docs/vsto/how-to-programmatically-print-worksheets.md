---
title: "Gewusst wie: Programmgesteuertes Drucken von Arbeitsbl&#228;ttern"
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
  - "Seitenansicht, Arbeitsblätter"
  - "Drucken [Office-Entwicklung in Visual Studio], Arbeitsblätter"
  - "Arbeitsblätter, Drucken"
ms.assetid: 312bfcd7-0a74-421c-b42e-df71a06b7bdf
caps.latest.revision: 46
author: "kempb"
ms.author: "kempb"
manager: "ghogen"
caps.handback.revision: 45
---
# Gewusst wie: Programmgesteuertes Drucken von Arbeitsbl&#228;ttern
  Sie können beliebige Arbeitsblätter aus einer Arbeitsmappe drucken.  
  
 [!INCLUDE[appliesto_xlalldocapp](../vsto/includes/appliesto-xlalldocapp-md.md)]  
  
## Drucken eines Arbeitsblatts in einer Anpassung auf Dokumentebene  
  
#### So drucken Sie ein Arbeitsblatt  
  
1.  Rufen Sie die <xref:Microsoft.Office.Tools.Excel.Worksheet.PrintOut%2A>\-Methode von `Sheet1` auf, fordern Sie zwei Exemplare an, und lassen Sie das Dokument vor dem Druck in der Vorschau anzeigen.  
  
     [!code-csharp[Trin_VstcoreExcelAutomation#22](../snippets/csharp/VS_Snippets_OfficeSP/Trin_VstcoreExcelAutomation/CS/Sheet1.cs#22)]
     [!code-vb[Trin_VstcoreExcelAutomation#22](../snippets/visualbasic/VS_Snippets_OfficeSP/Trin_VstcoreExcelAutomation/VB/Sheet1.vb#22)]  
  
 Mit der <xref:Microsoft.Office.Tools.Excel.Worksheet.PrintPreview%2A>\-Methode können Sie das angegebene Objekt im Fenster **Druckvorschau** anzeigen.  Der folgende Code setzt voraus, dass Sie über ein <xref:Microsoft.Office.Tools.Excel.Worksheet>\-Hostelement namens `Sheet1` verfügen.  
  
#### So zeigen Sie eine Vorschau der Seite vor dem Druck an  
  
1.  Rufen Sie die <xref:Microsoft.Office.Tools.Excel.Worksheet.PrintPreview%2A>\-Methode des Arbeitsblatts auf.  
  
     [!code-csharp[Trin_VstcoreExcelAutomation#23](../snippets/csharp/VS_Snippets_OfficeSP/Trin_VstcoreExcelAutomation/CS/Sheet1.cs#23)]
     [!code-vb[Trin_VstcoreExcelAutomation#23](../snippets/visualbasic/VS_Snippets_OfficeSP/Trin_VstcoreExcelAutomation/VB/Sheet1.vb#23)]  
  
## Drucken eines Arbeitsblatts in einem VSTO\-Add\-In  
  
#### So drucken Sie ein Arbeitsblatt  
  
1.  Rufen Sie die <xref:Microsoft.Office.Interop.Excel._Worksheet.PrintOut%2A>\-Methode des aktiven Arbeitsblatts auf, fordern Sie zwei Exemplare an, und lassen Sie das Dokument vor dem Druck in der Vorschau anzeigen.  
  
     [!code-csharp[Trin_VstcoreExcelAutomationAddIn#14](../snippets/csharp/VS_Snippets_OfficeSP/Trin_VstcoreExcelAutomationAddIn/CS/ThisAddIn.cs#14)]
     [!code-vb[Trin_VstcoreExcelAutomationAddIn#14](../snippets/visualbasic/VS_Snippets_OfficeSP/Trin_VstcoreExcelAutomationAddIn/VB/ThisAddIn.vb#14)]  
  
 Mit der <xref:Microsoft.Office.Interop.Excel._Worksheet.PrintPreview%2A>\-Methode können Sie das angegebene Objekt im Fenster **Druckvorschau** anzeigen.  
  
#### So zeigen Sie eine Vorschau der Seite vor dem Druck an  
  
1.  Rufen Sie die <xref:Microsoft.Office.Interop.Excel._Worksheet.PrintPreview%2A>\-Methode des aktiven Arbeitsblatts auf.  
  
     [!code-csharp[Trin_VstcoreExcelAutomationAddIn#15](../snippets/csharp/VS_Snippets_OfficeSP/Trin_VstcoreExcelAutomationAddIn/CS/ThisAddIn.cs#15)]
     [!code-vb[Trin_VstcoreExcelAutomationAddIn#15](../snippets/visualbasic/VS_Snippets_OfficeSP/Trin_VstcoreExcelAutomationAddIn/VB/ThisAddIn.vb#15)]  
  
## Siehe auch  
 [Arbeiten mit Arbeitsblättern](../vsto/working-with-worksheets.md)   
 [Gewusst wie: Programmgesteuertes Überprüfen der Rechtschreibung in Arbeitsblättern](../vsto/how-to-programmatically-check-spelling-in-worksheets.md)   
 [Arbeitsblatthostelement](../vsto/worksheet-host-item.md)   
 [Globaler Zugriff auf Objekte in Office-Projekten](../vsto/global-access-to-objects-in-office-projects.md)   
 [Optionale Parameter in Office-Lösungen](../vsto/optional-parameters-in-office-solutions.md)  
  
  