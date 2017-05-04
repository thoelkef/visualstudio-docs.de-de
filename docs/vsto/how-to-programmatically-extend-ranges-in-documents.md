---
title: "Gewusst wie: Programmgesteuertes Erweitern von Bereichen in Dokumenten | Microsoft Docs"
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
  - "Bereiche, erweitern"
  - "Dokumente [Office-Entwicklung in Visual Studio], Erweitern von Bereichen"
ms.assetid: 055af7a4-13d5-4236-b5fb-a112721482c5
caps.latest.revision: 41
author: "kempb"
ms.author: "kempb"
manager: "ghogen"
caps.handback.revision: 40
---
# Gewusst wie: Programmgesteuertes Erweitern von Bereichen in Dokumenten
  Nachdem Sie ein <xref:Microsoft.Office.Interop.Word.Range>\-Objekt in einem Microsoft Office Word\-Dokument definiert haben, ändern Sie dessen Start\- und Endpunkt mithilfe der Methoden <xref:Microsoft.Office.Interop.Word.Range.MoveStart%2A> und <xref:Microsoft.Office.Interop.Word.Range.MoveEnd%2A>. Die Methoden <xref:Microsoft.Office.Interop.Word.Range.MoveStart%2A> und <xref:Microsoft.Office.Interop.Word.Range.MoveEnd%2A> akzeptieren dieselben beiden Argumente *Unit* und *Count*. Das *Count*\-Argument entspricht der Anzahl zu verschiebender Einheiten, und das *Unit*\-Argument kann einer der folgenden <xref:Microsoft.Office.Interop.Word.WdUnits>\-Werte sein:  
  
-   <xref:Microsoft.Office.Interop.Word.WdUnits.wdCharacter>  
  
-   <xref:Microsoft.Office.Interop.Word.WdUnits.wdWord>  
  
-   <xref:Microsoft.Office.Interop.Word.WdUnits.wdSentence>  
  
-   <xref:Microsoft.Office.Interop.Word.WdUnits.wdParagraph>  
  
-   <xref:Microsoft.Office.Interop.Word.WdUnits.wdSection>  
  
-   <xref:Microsoft.Office.Interop.Word.WdUnits.wdStory>  
  
-   <xref:Microsoft.Office.Interop.Word.WdUnits.wdCell>  
  
-   <xref:Microsoft.Office.Interop.Word.WdUnits.wdColumn>  
  
-   <xref:Microsoft.Office.Interop.Word.WdUnits.wdRow>  
  
-   <xref:Microsoft.Office.Interop.Word.WdUnits.wdTable>  
  
 [!INCLUDE[appliesto_wdalldocapp](../vsto/includes/appliesto-wdalldocapp-md.md)]  
  
 Im folgenden Beispiel wird ein aus sieben Zeichen bestehender Bereich definiert. Anschließend wird die Startposition des Bereichs von der ursprünglichen Startposition aus um sieben Zeichen verschoben. Da die Endposition des Bereichs ebenfalls sieben Zeichen von der Startposition entfernt war, umfasst der resultierende Bereich 0 Zeichen. Durch den Code wird die Endposition dann von der aktuellen Endposition um sieben Zeichen verschoben.  
  
### So erweitern Sie einen Bereich  
  
1.  Definieren Sie einen Bereich von Zeichen. Weitere Informationen finden Sie unter [Gewusst wie: Programmgesteuertes Definieren und Markieren von Bereichen in Dokumenten](../vsto/how-to-programmatically-define-and-select-ranges-in-documents.md).  
  
     Das folgende Codebeispiel kann in einer Anpassung auf Dokumentebene verwendet werden.  
  
     [!code-csharp[Trin_VstcoreWordAutomation#39](../snippets/csharp/VS_Snippets_OfficeSP/Trin_VstcoreWordAutomation/CS/ThisDocument.cs#39)]
     [!code-vb[Trin_VstcoreWordAutomation#39](../snippets/visualbasic/VS_Snippets_OfficeSP/Trin_VstcoreWordAutomation/VB/ThisDocument.vb#39)]  
  
     Das folgende Codebeispiel kann in einem VSTO\-Add\-In verwendet werden. In diesem Beispiel wird das aktive Dokument verwendet.  
  
     [!code-csharp[Trin_VstcoreWordAutomationAddIn#39](../snippets/csharp/VS_Snippets_OfficeSP/Trin_VstcoreWordAutomationAddIn/CS/ThisAddIn.cs#39)]
     [!code-vb[Trin_VstcoreWordAutomationAddIn#39](../snippets/visualbasic/VS_Snippets_OfficeSP/Trin_VstcoreWordAutomationAddIn/VB/ThisAddIn.vb#39)]  
  
2.  Verwenden Sie die <xref:Microsoft.Office.Interop.Word.Range.MoveStart%2A>\-Methode des <xref:Microsoft.Office.Interop.Word.Range>\-Objekts, um die Startposition des Bereichs zu verschieben.  
  
     [!code-csharp[Trin_VstcoreWordAutomation#40](../snippets/csharp/VS_Snippets_OfficeSP/Trin_VstcoreWordAutomation/CS/ThisDocument.cs#40)]
     [!code-vb[Trin_VstcoreWordAutomation#40](../snippets/visualbasic/VS_Snippets_OfficeSP/Trin_VstcoreWordAutomation/VB/ThisDocument.vb#40)]  
  
3.  Verwenden Sie die <xref:Microsoft.Office.Interop.Word.Range.MoveEnd%2A>\-Methode des <xref:Microsoft.Office.Interop.Word.Range>\-Objekts, um die Endposition des Bereichs zu verschieben.  
  
     [!code-csharp[Trin_VstcoreWordAutomation#41](../snippets/csharp/VS_Snippets_OfficeSP/Trin_VstcoreWordAutomation/CS/ThisDocument.cs#41)]
     [!code-vb[Trin_VstcoreWordAutomation#41](../snippets/visualbasic/VS_Snippets_OfficeSP/Trin_VstcoreWordAutomation/VB/ThisDocument.vb#41)]  
  
## Code für die Anpassung auf Dokumentebene  
  
#### So erweitern Sie einen Bereich in einer Anpassung auf Dokumentebene  
  
1.  Das folgende Beispiel zeigt den vollständigen Code für eine Anpassung auf Dokumentebene. Wenn Sie diesen Code verwenden möchten, führen Sie ihn von der `ThisDocument`\-Klasse im Projekt aus.  
  
     [!code-csharp[Trin_VstcoreWordAutomation#38](../snippets/csharp/VS_Snippets_OfficeSP/Trin_VstcoreWordAutomation/CS/ThisDocument.cs#38)]
     [!code-vb[Trin_VstcoreWordAutomation#38](../snippets/visualbasic/VS_Snippets_OfficeSP/Trin_VstcoreWordAutomation/VB/ThisDocument.vb#38)]  
  
## VSTO\-Add\-In\-Code  
  
#### So erweitern Sie einen Bereich in einem VSTO\-Add\-In auf Anwendungsebene  
  
1.  Das folgende Beispiel zeigt den vollständigen Code eines VSTO\-Add\-Ins. Wenn Sie diesen Code verwenden möchten, führen Sie ihn von der `ThisAddIn`\-Klasse im Projekt aus.  
  
     [!code-csharp[Trin_VstcoreWordAutomationAddIn#38](../snippets/csharp/VS_Snippets_OfficeSP/Trin_VstcoreWordAutomationAddIn/CS/ThisAddIn.cs#38)]
     [!code-vb[Trin_VstcoreWordAutomationAddIn#38](../snippets/visualbasic/VS_Snippets_OfficeSP/Trin_VstcoreWordAutomationAddIn/VB/ThisAddIn.vb#38)]  
  
## Siehe auch  
 [Gewusst wie: Programmgesteuertes Zurücksetzen von Bereichen in Word-Dokumenten](../vsto/how-to-programmatically-reset-ranges-in-word-documents.md)   
 [Gewusst wie: Programmgesteuertes Reduzieren von Bereichen oder Markierungen in Dokumenten](../vsto/how-to-programmatically-collapse-ranges-or-selections-in-documents.md)   
 [Gewusst wie: Programmgesteuertes Definieren und Markieren von Bereichen in Dokumenten](../vsto/how-to-programmatically-define-and-select-ranges-in-documents.md)   
 [Gewusst wie: Programmgesteuertes Abrufen von Start- und Endzeichen in Bereichen](../vsto/how-to-programmatically-retrieve-start-and-end-characters-in-ranges.md)   
 [Gewusst wie: Programmgesteuertes Ausschließen von Absatzmarken beim Erstellen von Bereichen](../vsto/how-to-programmatically-exclude-paragraph-marks-when-creating-ranges.md)  
  
  