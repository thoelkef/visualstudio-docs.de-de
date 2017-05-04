---
title: "Gewusst wie: Programmgesteuertes Formatieren von Text in Dokumenten | Microsoft Docs"
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
  - "Formatieren [Office-Entwicklung in Visual Studio]"
  - "Dokumente [Office-Entwicklung in Visual Studio], Formatieren von Text"
  - "Text [Office-Entwicklung in Visual Studio], Formatieren in Dokumenten"
ms.assetid: 0a84893b-5ccc-4515-a2dc-95773ee8eaba
caps.latest.revision: 42
author: "kempb"
ms.author: "kempb"
manager: "ghogen"
caps.handback.revision: 41
---
# Gewusst wie: Programmgesteuertes Formatieren von Text in Dokumenten
  Sie können mit dem <xref:Microsoft.Office.Interop.Word.Range>\-Objekt Text in einem Microsoft Office Word\-Dokument formatieren.  
  
 [!INCLUDE[appliesto_wdalldocapp](../vsto/includes/appliesto-wdalldocapp-md.md)]  
  
 Im folgenden Beispiel wird der erste Absatz des Dokuments markiert, und der Schriftgrad, der Schriftartname und die Ausrichtung werden geändert. Anschließend wird der Bereich markiert und ein Meldungsfeld angezeigt, um die Ausführung des Codes vor dem nächsten Abschnitt zu unterbrechen. Im nächsten Abschnitt wird die Undo\-Methode des <xref:Microsoft.Office.Tools.Word.Document>\-Hostelements \(bei einer Anpassung auf Dokumentebene\) bzw. die <xref:Microsoft.Office.Interop.Word.Document>\-Klasse \(bei einem VSTO\-Add\-In\) dreimal aufgerufen. Das Format Standardeinzug wird zugewiesen, und ein Meldungsfeld wird angezeigt, um die Codeausführung zu unterbrechen. Anschließend ruft der Code einmal die <xref:Microsoft.Office.Tools.Word.Document.Undo%2A>\-Methode auf und zeigt ein Meldungsfeld an.  
  
## Beispiel für die Anpassung auf Dokumentebene  
  
#### So formatieren Sie Text mit einer Anpassung auf Dokumentebene  
  
1.  Das folgende Beispiel kann in einer Anpassung auf Dokumentebene verwendet werden. Wenn Sie diesen Code verwenden möchten, führen Sie ihn von der `ThisDocument`\-Klasse im Projekt aus.  
  
     [!code-csharp[Trin_VstcoreWordAutomation#62](../snippets/csharp/VS_Snippets_OfficeSP/Trin_VstcoreWordAutomation/CS/ThisDocument.cs#62)]
     [!code-vb[Trin_VstcoreWordAutomation#62](../snippets/visualbasic/VS_Snippets_OfficeSP/Trin_VstcoreWordAutomation/VB/ThisDocument.vb#62)]  
  
## Beispiel für ein VSTO\-Add\-In  
  
#### So formatieren Sie Text mithilfe eines VSTO\-Add\-Ins  
  
1.  Das folgende Beispiel kann in einem VSTO\-Add\-In verwendet werden. In diesem Beispiel wird das aktive Dokument verwendet. Wenn Sie diesen Code verwenden möchten, führen Sie ihn von der `ThisAddIn`\-Klasse im Projekt aus.  
  
     [!code-csharp[Trin_VstcoreWordAutomationAddIn#62](../snippets/csharp/VS_Snippets_OfficeSP/Trin_VstcoreWordAutomationAddIn/CS/ThisAddIn.cs#62)]
     [!code-vb[Trin_VstcoreWordAutomationAddIn#62](../snippets/visualbasic/VS_Snippets_OfficeSP/Trin_VstcoreWordAutomationAddIn/VB/ThisAddIn.vb#62)]  
  
## Siehe auch  
 [Gewusst wie: Programmgesteuertes Definieren und Markieren von Bereichen in Dokumenten](../vsto/how-to-programmatically-define-and-select-ranges-in-documents.md)   
 [Gewusst wie: Programmgesteuertes Einfügen von Text in Word-Dokumente](../vsto/how-to-programmatically-insert-text-into-word-documents.md)   
 [Gewusst wie: Programmgesteuertes Suchen und Ersetzen von Text in Dokumenten](../vsto/how-to-programmatically-search-for-and-replace-text-in-documents.md)  
  
  