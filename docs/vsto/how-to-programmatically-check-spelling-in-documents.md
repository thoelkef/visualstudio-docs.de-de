---
title: "Gewusst wie: Programmgesteuertes &#220;berpr&#252;fen der Rechtschreibung in Dokumenten"
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
  - "Dokumente [Office-Entwicklung in Visual Studio], Prüfen der Rechtschreibung"
  - "Rechtschreibprüfung, Dokumente"
ms.assetid: 5bbe3a8d-fc65-4f57-bd63-5bb549dbc4bd
caps.latest.revision: 24
author: "kempb"
ms.author: "kempb"
manager: "ghogen"
caps.handback.revision: 24
---
# Gewusst wie: Programmgesteuertes &#220;berpr&#252;fen der Rechtschreibung in Dokumenten
  Um die Rechtschreibung in einem Dokument zu überprüfen, verwenden Sie die <xref:Microsoft.Office.Interop.Word._Application.CheckSpelling%2A>\-Methode.  Diese Methode gibt einen booleschen Wert zurück, der angibt, ob der angegebene Parameter richtig geschrieben wurde.  
  
 [!INCLUDE[appliesto_wdalldocapp](../vsto/includes/appliesto-wdalldocapp-md.md)]  
  
### So führen Sie eine Rechtschreibprüfung durch und zeigen die Ergebnisse in einem Meldungsfeld an  
  
1.  Rufen Sie die <xref:Microsoft.Office.Interop.Word._Application.CheckSpelling%2A>\-Methode auf, und übergeben Sie den Textbereich, der auf Rechtschreibfehler überprüft werden soll.  Wenn Sie dieses Codebeispiel verwenden möchten, führen Sie es von der `ThisDocument`\-Klasse oder der `ThisAddIn`\-Klasse im Projekt aus.  
  
     [!code-csharp[Trin_VstcoreWordAutomation#113](../snippets/csharp/VS_Snippets_OfficeSP/Trin_VstcoreWordAutomation/CS/ThisDocument.cs#113)]
     [!code-vb[Trin_VstcoreWordAutomation#113](../snippets/visualbasic/VS_Snippets_OfficeSP/Trin_VstcoreWordAutomation/VB/ThisDocument.vb#113)]  
  
## Siehe auch  
 [Gewusst wie: Programmgesteuertes Definieren und Markieren von Bereichen in Dokumenten](../vsto/how-to-programmatically-define-and-select-ranges-in-documents.md)   
 [Optionale Parameter in Office-Lösungen](../vsto/optional-parameters-in-office-solutions.md)  
  
  