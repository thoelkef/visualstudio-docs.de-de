---
title: "Gewusst wie: Programmgesteuertes Ausblenden von Text in Dokumenten"
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
  - "Dokumente [Office-Entwicklung in Visual Studio], Ausblenden von Text"
  - "Text [Office-Entwicklung in Visual Studio], Ausblenden in Dokumenten"
ms.assetid: f5ced4ec-22ca-463b-b963-d34ce631b486
caps.latest.revision: 28
author: "kempb"
ms.author: "kempb"
manager: "ghogen"
caps.handback.revision: 27
---
# Gewusst wie: Programmgesteuertes Ausblenden von Text in Dokumenten
  Sie können Text in einem Dokument ausblenden, indem Sie die <xref:Microsoft.Office.Interop.Word._Font.Hidden%2A>\-Eigenschaft der <xref:Microsoft.Office.Interop.Word.Range.Font%2A> für einen bestimmten Textbereich festlegen.  
  
 Sie können z. B. den Text in einer <xref:Microsoft.Office.Tools.Word.Bookmark> \(in einer Anpassung auf Dokumentebene\) oder in einer <xref:Microsoft.Office.Interop.Word.Bookmark> \(in einem VSTO\-Add\-In\) vorübergehend ausblenden, bevor Sie das Dokument an einen Drucker senden.  
  
 [!INCLUDE[appliesto_wdalldocapp](../vsto/includes/appliesto-wdalldocapp-md.md)]  
  
### So blenden Sie Text in einem Bookmark\-Steuerelement beim Drucken des Dokuments aus  
  
1.  Erstellen Sie eine Prozedur, die sämtlichen Text in einem angegebenen Bereich ausblendet.  
  
     [!code-csharp[Trin_VstcoreWordAutomation#105](../snippets/csharp/VS_Snippets_OfficeSP/Trin_VstcoreWordAutomation/CS/ThisDocument.cs#105)]
     [!code-vb[Trin_VstcoreWordAutomation#105](../snippets/visualbasic/VS_Snippets_OfficeSP/Trin_VstcoreWordAutomation/VB/ThisDocument.vb#105)]  
  
2.  Erstellen Sie eine Prozedur, die sämtlichen Text in einem angegebenen Bereich anzeigt.  
  
     [!code-csharp[Trin_VstcoreWordAutomation#106](../snippets/csharp/VS_Snippets_OfficeSP/Trin_VstcoreWordAutomation/CS/ThisDocument.cs#106)]
     [!code-vb[Trin_VstcoreWordAutomation#106](../snippets/visualbasic/VS_Snippets_OfficeSP/Trin_VstcoreWordAutomation/VB/ThisDocument.vb#106)]  
  
3.  Übergeben Sie den Bereich einer Textmarke an die `HideText`\-Methode, drucken Sie das Dokument, und übergeben Sie dann denselben Bereich an die `UnhideText`\-Methode.  
  
     Das folgende Codebeispiel kann in einer Anpassung auf Dokumentebene verwendet werden. Wenn Sie dieses Beispiel verwenden möchten, führen Sie es von der `ThisDocument`\-Klasse Ihres Projekts aus.  
  
     [!code-csharp[Trin_VstcoreWordAutomation#107](../snippets/csharp/VS_Snippets_OfficeSP/Trin_VstcoreWordAutomation/CS/ThisDocument.cs#107)]
     [!code-vb[Trin_VstcoreWordAutomation#107](../snippets/visualbasic/VS_Snippets_OfficeSP/Trin_VstcoreWordAutomation/VB/ThisDocument.vb#107)]  
  
     Das folgende Codebeispiel kann in einem VSTO\-Add\-In verwendet werden. In diesem Beispiel wird das aktive Dokument verwendet. Wenn Sie dieses Beispiel verwenden möchten, führen Sie es von der `ThisAddIn`\-Klasse Ihres Projekts aus.  
  
     [!code-csharp[Trin_VstcoreWordAutomationAddIn#107](../snippets/csharp/VS_Snippets_OfficeSP/Trin_VstcoreWordAutomationAddIn/CS/ThisAddIn.cs#107)]
     [!code-vb[Trin_VstcoreWordAutomationAddIn#107](../snippets/visualbasic/VS_Snippets_OfficeSP/Trin_VstcoreWordAutomationAddIn/VB/ThisAddIn.vb#107)]  
  
## Kompilieren des Codes  
 In diesem Codebeispiel wird davon ausgegangen, dass das Dokument ein <xref:Microsoft.Office.Tools.Word.Bookmark>\-Steuerelement \(in einer Anpassung auf Dokumentebene\) oder <xref:Microsoft.Office.Interop.Word.Bookmark>\-Steuerelement \(in einem VSTO\-Add\-In\) namens `bookmark1` enthält.  
  
## Siehe auch  
 [Gewusst wie: Programmgesteuertes Drucken von Dokumenten](../vsto/how-to-programmatically-print-documents.md)   
 [Gewusst wie: Programmgesteuertes Definieren und Markieren von Bereichen in Dokumenten](../vsto/how-to-programmatically-define-and-select-ranges-in-documents.md)   
 [Gewusst wie: Programmgesteuertes Zurücksetzen von Bereichen in Word-Dokumenten](../vsto/how-to-programmatically-reset-ranges-in-word-documents.md)   
 [Gewusst wie: Programmgesteuertes Aktualisieren von Lesezeichentext](../vsto/how-to-programmatically-update-bookmark-text.md)   
 [Optionale Parameter in Office-Lösungen](../vsto/optional-parameters-in-office-solutions.md)  
  
  