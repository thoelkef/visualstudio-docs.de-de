---
title: "Gewusst wie: Programmgesteuertes Abrufen von Start- und Endzeichen in Bereichen | Microsoft Docs"
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
  - "Bereiche, Abrufen von Start- und Endzeichen"
  - "Endzeichen"
  - "Startzeichen"
  - "Dokumente [Office-Entwicklung in Visual Studio], Abrufen von Bereichen"
ms.assetid: 734c630c-abc9-491d-94b6-429d1fc7a4cc
caps.latest.revision: 37
author: "kempb"
ms.author: "kempb"
manager: "ghogen"
caps.handback.revision: 36
---
# Gewusst wie: Programmgesteuertes Abrufen von Start- und Endzeichen in Bereichen
  In diesem Beispiel wird veranschaulicht, wie Sie die Zeichenpositionen der Anfangs\- und Endposition eines Bereichs abrufen können.  
  
 [!INCLUDE[appliesto_wdalldocapp](../vsto/includes/appliesto-wdalldocapp-md.md)]  
  
### So rufen Sie Start\- und Endzeichen eines Bereichs in einer Anpassung auf Dokumentebene ab  
  
1.  Rufen Sie die Werte der <xref:Microsoft.Office.Interop.Word.Range.Start%2A>\-Eigenschaft und der <xref:Microsoft.Office.Interop.Word.Range.End%2A>\-Eigenschaft des <xref:Microsoft.Office.Interop.Word.Range>\-Objekts ab. Im folgenden Codebeispiel werden die Start\- und Endposition des zweiten Satzes im Dokument abgerufen. Wenn Sie dieses Codebeispiel verwenden möchten, führen Sie es von der `ThisDocument`\-Klasse im Projekt aus.  
  
     [!code-csharp[Trin_VstcoreWordAutomation#25](../snippets/csharp/VS_Snippets_OfficeSP/Trin_VstcoreWordAutomation/CS/ThisDocument.cs#25)]
     [!code-vb[Trin_VstcoreWordAutomation#25](../snippets/visualbasic/VS_Snippets_OfficeSP/Trin_VstcoreWordAutomation/VB/ThisDocument.vb#25)]  
  
### So rufen Sie Start\- und Endzeichen eines Bereichs mit einem VSTO\-Add\-Ins ab  
  
1.  Rufen Sie die Werte der <xref:Microsoft.Office.Interop.Word.Range.Start%2A>\-Eigenschaft und der <xref:Microsoft.Office.Interop.Word.Range.End%2A>\-Eigenschaft des <xref:Microsoft.Office.Interop.Word.Range>\-Objekts ab. Im folgenden Codebeispiel werden die Start\- und Endposition des zweiten Satzes im aktiven Dokument abgerufen. Wenn Sie dieses Codebeispiel verwenden möchten, führen Sie es von der `ThisAddIn`\-Klasse im Projekt aus.  
  
     [!code-csharp[Trin_VstcoreWordAutomationAddIn#25](../snippets/csharp/VS_Snippets_OfficeSP/Trin_VstcoreWordAutomationAddIn/CS/ThisAddIn.cs#25)]
     [!code-vb[Trin_VstcoreWordAutomationAddIn#25](../snippets/visualbasic/VS_Snippets_OfficeSP/Trin_VstcoreWordAutomationAddIn/VB/ThisAddIn.vb#25)]  
  
## Siehe auch  
 [Gewusst wie: Programmgesteuertes Definieren und Markieren von Bereichen in Dokumenten](../vsto/how-to-programmatically-define-and-select-ranges-in-documents.md)   
 [Gewusst wie: Programmgesteuertes Erweitern von Bereichen in Dokumenten](../vsto/how-to-programmatically-extend-ranges-in-documents.md)   
 [Gewusst wie: Programmgesteuertes Zurücksetzen von Bereichen in Word-Dokumenten](../vsto/how-to-programmatically-reset-ranges-in-word-documents.md)   
 [Gewusst wie: Programmgesteuertes Reduzieren von Bereichen oder Markierungen in Dokumenten](../vsto/how-to-programmatically-collapse-ranges-or-selections-in-documents.md)   
 [Gewusst wie: Programmgesteuertes Ausschließen von Absatzmarken beim Erstellen von Bereichen](../vsto/how-to-programmatically-exclude-paragraph-marks-when-creating-ranges.md)   
 [Gewusst wie: Programmgesteuertes Zählen von Zeichen in Dokumenten](../vsto/how-to-programmatically-count-characters-in-documents.md)  
  
  