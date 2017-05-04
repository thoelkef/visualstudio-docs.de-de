---
title: "Gewusst wie: Programmgesteuertes Reduzieren von Bereichen oder Markierungen in Dokumenten | Microsoft Docs"
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
  - "Auswahl, reduzieren"
  - "Dokumente [Office-Entwicklung in Visual Studio], Reduzieren von Bereichen"
  - "Reduzieren der Auswahl"
  - "Bereiche, reduzieren"
  - "Reduzieren von Bereichen"
ms.assetid: 0bd059dd-8606-42ae-a8a9-97f8f3bd5cc5
caps.latest.revision: 42
author: "kempb"
ms.author: "kempb"
manager: "ghogen"
caps.handback.revision: 41
---
# Gewusst wie: Programmgesteuertes Reduzieren von Bereichen oder Markierungen in Dokumenten
  Wenn Sie mit einem <xref:Microsoft.Office.Interop.Word.Range>\- oder <xref:Microsoft.Office.Interop.Word.Selection>\-Objekt arbeiten, möchten Sie die Auswahl vor dem Einfügen von Text möglicherweise auf eine Einfügemarke setzen, um das Überschreiben vorhandenen Texts zu vermeiden. Sowohl das <xref:Microsoft.Office.Interop.Word.Range>\-Objekt als auch das <xref:Microsoft.Office.Interop.Word.Selection>\-Objekt verfügen über eine Collapse\-Methode, die die folgenden <xref:Microsoft.Office.Interop.Word.WdCollapseDirection>\-Enumerationswerte verwendet:  
  
-   <xref:Microsoft.Office.Interop.Word.WdCollapseDirection.wdCollapseStart> reduziert die Auswahl auf den Anfang der Auswahl. Dies ist die Standardeinstellung, wenn Sie keinen Enumerationswert angeben möchten.  
  
-   <xref:Microsoft.Office.Interop.Word.WdCollapseDirection.wdCollapseEnd> reduziert die Auswahl auf das Ende der Auswahl.  
  
 [!INCLUDE[appliesto_wdalldocapp](../vsto/includes/appliesto-wdalldocapp-md.md)]  
  
### So reduzieren Sie einen Bereich und fügen neuen Text ein  
  
1.  Erstellen Sie ein <xref:Microsoft.Office.Interop.Word.Range>\-Objekt, das aus dem ersten Absatz des Dokuments besteht.  
  
     Das folgende Codebeispiel kann in einer Anpassung auf Dokumentebene verwendet werden.  
  
     [!code-csharp[Trin_VstcoreWordAutomation#46](../snippets/csharp/VS_Snippets_OfficeSP/Trin_VstcoreWordAutomation/CS/ThisDocument.cs#46)]
     [!code-vb[Trin_VstcoreWordAutomation#46](../snippets/visualbasic/VS_Snippets_OfficeSP/Trin_VstcoreWordAutomation/VB/ThisDocument.vb#46)]  
  
     Das folgende Codebeispiel kann in einem VSTO\-Add\-In verwendet werden. In diesem Code wird das aktive Dokument verwendet.  
  
     [!code-csharp[Trin_VstcoreWordAutomationAddIn#46](../snippets/csharp/VS_Snippets_OfficeSP/Trin_VstcoreWordAutomationAddIn/CS/ThisAddIn.cs#46)]
     [!code-vb[Trin_VstcoreWordAutomationAddIn#46](../snippets/visualbasic/VS_Snippets_OfficeSP/Trin_VstcoreWordAutomationAddIn/VB/ThisAddIn.vb#46)]  
  
2.  Verwenden Sie den <xref:Microsoft.Office.Interop.Word.WdCollapseDirection.wdCollapseStart>\-Enumerationswert, um den Bereich zu reduzieren.  
  
     [!code-csharp[Trin_VstcoreWordAutomation#47](../snippets/csharp/VS_Snippets_OfficeSP/Trin_VstcoreWordAutomation/CS/ThisDocument.cs#47)]
     [!code-vb[Trin_VstcoreWordAutomation#47](../snippets/visualbasic/VS_Snippets_OfficeSP/Trin_VstcoreWordAutomation/VB/ThisDocument.vb#47)]  
  
3.  Fügen Sie den neuen Text ein.  
  
     [!code-csharp[Trin_VstcoreWordAutomation#48](../snippets/csharp/VS_Snippets_OfficeSP/Trin_VstcoreWordAutomation/CS/ThisDocument.cs#48)]
     [!code-vb[Trin_VstcoreWordAutomation#48](../snippets/visualbasic/VS_Snippets_OfficeSP/Trin_VstcoreWordAutomation/VB/ThisDocument.vb#48)]  
  
4.  Wählen Sie das <xref:Microsoft.Office.Interop.Word.Range>\-Steuerelement aus.  
  
     [!code-csharp[Trin_VstcoreWordAutomation#49](../snippets/csharp/VS_Snippets_OfficeSP/Trin_VstcoreWordAutomation/CS/ThisDocument.cs#49)]
     [!code-vb[Trin_VstcoreWordAutomation#49](../snippets/visualbasic/VS_Snippets_OfficeSP/Trin_VstcoreWordAutomation/VB/ThisDocument.vb#49)]  
  
 Wenn Sie den <xref:Microsoft.Office.Interop.Word.WdCollapseDirection.wdCollapseEnd>\-Enumerationswert verwenden, wird der Text am Anfang des folgenden Absatzes eingefügt.  
  
 [!code-csharp[Trin_VstcoreWordAutomation#50](../snippets/csharp/VS_Snippets_OfficeSP/Trin_VstcoreWordAutomation/CS/ThisDocument.cs#50)]
 [!code-vb[Trin_VstcoreWordAutomation#50](../snippets/visualbasic/VS_Snippets_OfficeSP/Trin_VstcoreWordAutomation/VB/ThisDocument.vb#50)]  
  
 Normalerweise würden Sie davon ausgehen, dass ein eingefügter neuer Satz vor der Absatzmarke eingefügt wird. Dies ist jedoch nicht der Fall, weil die Absatzmarke im ursprünglichen Bereich enthalten ist. Weitere Informationen finden Sie unter [Gewusst wie: Programmgesteuertes Ausschließen von Absatzmarken beim Erstellen von Bereichen](../vsto/how-to-programmatically-exclude-paragraph-marks-when-creating-ranges.md).  
  
## Beispiel für die Anpassung auf Dokumentebene  
  
#### So reduzieren Sie einen Bereich in einer Anpassung auf Dokumentebene  
  
1.  Das folgende Beispiel zeigt die vollständige Methode für eine Anpassung auf Dokumentebene. Wenn Sie diesen Code verwenden möchten, führen Sie ihn von der `ThisDocument`\-Klasse im Projekt aus.  
  
     [!code-csharp[Trin_VstcoreWordAutomation#45](../snippets/csharp/VS_Snippets_OfficeSP/Trin_VstcoreWordAutomation/CS/ThisDocument.cs#45)]
     [!code-vb[Trin_VstcoreWordAutomation#45](../snippets/visualbasic/VS_Snippets_OfficeSP/Trin_VstcoreWordAutomation/VB/ThisDocument.vb#45)]  
  
## Beispiel für ein VSTO\-Add\-In  
  
#### So reduzieren Sie einen Bereich in einem VSTO\-Add\-In  
  
1.  Das folgende Beispiel zeigt die vollständige Methode für ein VSTO\-Add\-In. Wenn Sie diesen Code verwenden möchten, führen Sie ihn von der `ThisAddIn`\-Klasse im Projekt aus.  
  
     [!code-csharp[Trin_VstcoreWordAutomationAddIn#45](../snippets/csharp/VS_Snippets_OfficeSP/Trin_VstcoreWordAutomationAddIn/CS/ThisAddIn.cs#45)]
     [!code-vb[Trin_VstcoreWordAutomationAddIn#45](../snippets/visualbasic/VS_Snippets_OfficeSP/Trin_VstcoreWordAutomationAddIn/VB/ThisAddIn.vb#45)]  
  
## Siehe auch  
 [Gewusst wie: Programmgesteuertes Einfügen von Text in Word-Dokumente](../vsto/how-to-programmatically-insert-text-into-word-documents.md)   
 [Gewusst wie: Programmgesteuertes Definieren und Markieren von Bereichen in Dokumenten](../vsto/how-to-programmatically-define-and-select-ranges-in-documents.md)   
 [Gewusst wie: Programmgesteuertes Abrufen von Start- und Endzeichen in Bereichen](../vsto/how-to-programmatically-retrieve-start-and-end-characters-in-ranges.md)   
 [Gewusst wie: Programmgesteuertes Ausschließen von Absatzmarken beim Erstellen von Bereichen](../vsto/how-to-programmatically-exclude-paragraph-marks-when-creating-ranges.md)   
 [Gewusst wie: Programmgesteuertes Erweitern von Bereichen in Dokumenten](../vsto/how-to-programmatically-extend-ranges-in-documents.md)   
 [Gewusst wie: Programmgesteuertes Zurücksetzen von Bereichen in Word-Dokumenten](../vsto/how-to-programmatically-reset-ranges-in-word-documents.md)  
  
  