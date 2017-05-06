---
title: "Gewusst wie: Programmgesteuertes Durchlaufen gefundener Elemente in Dokumenten"
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
  - "Schleifen, Durchlaufen gefundener Elemente in Dokumenten"
  - "Dokumente [Office-Entwicklung in Visual Studio], Durchsuchen"
  - "Text [Office-Entwicklung in Visual Studio], Suchen in Dokumenten"
ms.assetid: 68dc41b1-eb96-4697-ac93-1a88c862ebad
caps.latest.revision: 44
author: "kempb"
ms.author: "kempb"
manager: "ghogen"
caps.handback.revision: 43
---
# Gewusst wie: Programmgesteuertes Durchlaufen gefundener Elemente in Dokumenten
  Die <xref:Microsoft.Office.Interop.Word.Find>\-Klasse hat eine <xref:Microsoft.Office.Interop.Word.Find.Found%2A>\-Eigenschaft, die jedes Mal **true** zurückgibt, wenn ein gesuchtes Element gefunden wurde. Sie können alle in einem <xref:Microsoft.Office.Interop.Word.Range>\-Objekt gefundenen Instanzen mit der <xref:Microsoft.Office.Interop.Word.Find.Execute%2A>\-Methode durchlaufen.  
  
 [!INCLUDE[appliesto_wdalldocapp](../vsto/includes/appliesto-wdalldocapp-md.md)]  
  
### So durchlaufen Sie gefundene Elemente  
  
1.  Deklarieren Sie ein <xref:Microsoft.Office.Interop.Word.Range>\-Objekt.  
  
     Das folgende Codebeispiel kann in einer Anpassung auf Dokumentebene verwendet werden.  
  
     [!code-csharp[Trin_VstcoreWordAutomation#79](../snippets/csharp/VS_Snippets_OfficeSP/Trin_VstcoreWordAutomation/CS/ThisDocument.cs#79)]
     [!code-vb[Trin_VstcoreWordAutomation#79](../snippets/visualbasic/VS_Snippets_OfficeSP/Trin_VstcoreWordAutomation/VB/ThisDocument.vb#79)]  
  
     Das folgende Codebeispiel kann in einem VSTO\-Add\-In verwendet werden. In diesem Beispiel wird das aktive Dokument verwendet.  
  
     [!code-csharp[Trin_VstcoreWordAutomationAddIn#79](../snippets/csharp/VS_Snippets_OfficeSP/Trin_VstcoreWordAutomationAddIn/CS/ThisAddIn.cs#79)]
     [!code-vb[Trin_VstcoreWordAutomationAddIn#79](../snippets/visualbasic/VS_Snippets_OfficeSP/Trin_VstcoreWordAutomationAddIn/VB/ThisAddIn.vb#79)]  
  
2.  Verwenden Sie die <xref:Microsoft.Office.Interop.Word.Find.Found%2A>\-Eigenschaft in einer Schleife, um nach allen Vorkommen der Zeichenfolge im Dokument zu suchen, und erhöhen Sie eine ganzzahlige Variable jedes Mal um 1, wenn die Zeichenfolge gefunden wurde.  
  
     [!code-csharp[Trin_VstcoreWordAutomation#80](../snippets/csharp/VS_Snippets_OfficeSP/Trin_VstcoreWordAutomation/CS/ThisDocument.cs#80)]
     [!code-vb[Trin_VstcoreWordAutomation#80](../snippets/visualbasic/VS_Snippets_OfficeSP/Trin_VstcoreWordAutomation/VB/ThisDocument.vb#80)]  
  
3.  Zeigen Sie in einem Meldungsfeld an, wie oft die Zeichenfolge gefunden wurde.  
  
     [!code-csharp[Trin_VstcoreWordAutomation#81](../snippets/csharp/VS_Snippets_OfficeSP/Trin_VstcoreWordAutomation/CS/ThisDocument.cs#81)]
     [!code-vb[Trin_VstcoreWordAutomation#81](../snippets/visualbasic/VS_Snippets_OfficeSP/Trin_VstcoreWordAutomation/VB/ThisDocument.vb#81)]  
  
 Die folgenden Beispiele zeigen die vollständige Methode.  
  
## Beispiel für die Anpassung auf Dokumentebene  
  
#### So durchlaufen Sie Elemente in einer Anpassung auf Dokumentebene  
  
1.  Das folgende Beispiel zeigt den vollständigen Code für eine Anpassung auf Dokumentebene. Wenn Sie diesen Code verwenden möchten, führen Sie ihn von der `ThisDocument`\-Klasse im Projekt aus.  
  
     [!code-csharp[Trin_VstcoreWordAutomation#78](../snippets/csharp/VS_Snippets_OfficeSP/Trin_VstcoreWordAutomation/CS/ThisDocument.cs#78)]
     [!code-vb[Trin_VstcoreWordAutomation#78](../snippets/visualbasic/VS_Snippets_OfficeSP/Trin_VstcoreWordAutomation/VB/ThisDocument.vb#78)]  
  
## Beispiel für ein VSTO\-Add\-In  
  
#### So durchlaufen Sie Elemente in einem VSTO\-Add\-In  
  
1.  Das folgende Beispiel zeigt den vollständigen Code eines VSTO\-Add\-Ins. Wenn Sie diesen Code verwenden möchten, führen Sie ihn von der `ThisAddIn`\-Klasse im Projekt aus.  
  
     [!code-csharp[Trin_VstcoreWordAutomationAddIn#78](../snippets/csharp/VS_Snippets_OfficeSP/Trin_VstcoreWordAutomationAddIn/CS/ThisAddIn.cs#78)]
     [!code-vb[Trin_VstcoreWordAutomationAddIn#78](../snippets/visualbasic/VS_Snippets_OfficeSP/Trin_VstcoreWordAutomationAddIn/VB/ThisAddIn.vb#78)]  
  
## Siehe auch  
 [Gewusst wie: Programmgesteuertes Suchen und Ersetzen von Text in Dokumenten](../vsto/how-to-programmatically-search-for-and-replace-text-in-documents.md)   
 [Gewusst wie: Programmgesteuertes Festlegen von Suchoptionen in Word](../vsto/how-to-programmatically-set-search-options-in-word.md)   
 [Gewusst wie: Programmgesteuertes Definieren und Markieren von Bereichen in Dokumenten](../vsto/how-to-programmatically-define-and-select-ranges-in-documents.md)   
 [Gewusst wie: Programmgesteuertes Wiederherstellen der Auswahl nach Suchvorgängen](../vsto/how-to-programmatically-restore-selections-after-searches.md)   
 [Optionale Parameter in Office-Lösungen](../vsto/optional-parameters-in-office-solutions.md)  
  
  