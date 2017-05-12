---
title: "Gewusst wie: Programmgesteuertes Suchen und Ersetzen von Text in Dokumenten"
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
  - "Dokumente [Office-Entwicklung in Visual Studio], Suchen"
  - "Text [Office-Entwicklung in Visual Studio], Suchen in Dokumenten"
  - "Text [Office-Entwicklung in Visual Studio], Textsuche"
  - "Textsuche, Dokumente"
  - "Textsuche, Ersetzen von Text"
ms.assetid: a66962f5-eeb9-4dc6-a70f-9039ab437a63
caps.latest.revision: 51
author: "kempb"
ms.author: "kempb"
manager: "ghogen"
caps.handback.revision: 50
---
# Gewusst wie: Programmgesteuertes Suchen und Ersetzen von Text in Dokumenten
  Das <xref:Microsoft.Office.Interop.Word.Find>\-Objekt ist ein Element des <xref:Microsoft.Office.Interop.Word.Selection>\- und des <xref:Microsoft.Office.Interop.Word.Range>\-Objekts, und Sie können eines dieser Objekte verwenden, um in Microsoft Office Word\-Dokumenten nach Text zu suchen.  Der Befehl "Ersetzen" ist eine Erweiterung des Befehls "Suchen".  
  
 Verwenden Sie ein <xref:Microsoft.Office.Interop.Word.Find>\-Objekt, um ein Microsoft Office Word\-Dokument in einer Schleife zu durchlaufen und nach bestimmtem Text, einer Formatierung oder einem Stil zu suchen. Verwenden Sie die Eigenschaft <xref:Microsoft.Office.Interop.Word.Find.Replacement%2A>, um gefundene Elemente zu ersetzen.  
  
 [!INCLUDE[appliesto_wdalldocapp](../vsto/includes/appliesto-wdalldocapp-md.md)]  
  
## Verwenden eines Selection\-Objekts  
 Wenn Sie ein <xref:Microsoft.Office.Interop.Word.Selection>\-Objekt zum Suchen nach Text verwenden, gelten die von Ihnen angegebenen Suchkriterien nur für den zurzeit markierten Text.  Wenn die <xref:Microsoft.Office.Interop.Word.Selection> eine Einfügemarke ist, wird das Dokument durchsucht.  Wenn ein Element gefunden wird, das mit die Suchkriterien übereinstimmt, wird es automatisch ausgewählt.  
  
 Sie müssen unbedingt beachten, dass die <xref:Microsoft.Office.Interop.Word.Find>\-Kriterien kumulativ sind. Dies bedeutet, dass Kriterien früheren Suchkriterien hinzugefügt werden.  Deaktivieren Sie alle Formatierungen aus vorherigen Suchvorgängen mithilfe der Methode <xref:Microsoft.Office.Interop.Word.Find.ClearFormatting%2A>, bevor Sie den Suchvorgang ausführen.  
  
#### So suchen mit einem Selection\-Objekt nach Text  
  
1.  Weisen Sie einer Variablen eine Suchzeichenfolge zu.  
  
     [!code-csharp[Trin_VstcoreWordAutomation#68](../snippets/csharp/VS_Snippets_OfficeSP/Trin_VstcoreWordAutomation/CS/ThisDocument.cs#68)]
     [!code-vb[Trin_VstcoreWordAutomation#68](../snippets/visualbasic/VS_Snippets_OfficeSP/Trin_VstcoreWordAutomation/VB/ThisDocument.vb#68)]  
  
2.  Löschen Sie die Formatierung aus vorherigen Suchvorgängen.  
  
     [!code-csharp[Trin_VstcoreWordAutomation#69](../snippets/csharp/VS_Snippets_OfficeSP/Trin_VstcoreWordAutomation/CS/ThisDocument.cs#69)]
     [!code-vb[Trin_VstcoreWordAutomation#69](../snippets/visualbasic/VS_Snippets_OfficeSP/Trin_VstcoreWordAutomation/VB/ThisDocument.vb#69)]  
  
3.  Führen Sie die Suche aus, und zeigen Sie ein Meldungsfeld mit den Ergebnissen an.  
  
     [!code-csharp[Trin_VstcoreWordAutomation#70](../snippets/csharp/VS_Snippets_OfficeSP/Trin_VstcoreWordAutomation/CS/ThisDocument.cs#70)]
     [!code-vb[Trin_VstcoreWordAutomation#70](../snippets/visualbasic/VS_Snippets_OfficeSP/Trin_VstcoreWordAutomation/VB/ThisDocument.vb#70)]  
  
 Das folgende Beispiel zeigt die vollständige Methode.  
  
 [!code-csharp[Trin_VstcoreWordAutomation#67](../snippets/csharp/VS_Snippets_OfficeSP/Trin_VstcoreWordAutomation/CS/ThisDocument.cs#67)]
 [!code-vb[Trin_VstcoreWordAutomation#67](../snippets/visualbasic/VS_Snippets_OfficeSP/Trin_VstcoreWordAutomation/VB/ThisDocument.vb#67)]  
  
## Verwenden eines Range\-Objekts  
 Mit einem <xref:Microsoft.Office.Interop.Word.Range>\-Objekt können Sie nach Text suchen, ohne dass eine Anzeige in der Benutzeroberfläche erfolgt.  Das<xref:Microsoft.Office.Interop.Word.Find>\-Objekt gibt **True** zurück, wenn Text gefunden wird, die mit den Suchkriterien übereinstimmt. Andernfalls wird **False** zurückgegeben.  Es definiert außerdem das <xref:Microsoft.Office.Interop.Word.Range>\-Objekt so neu, dass es den Suchkriterien entspricht, wenn der Text gefunden wird.  
  
#### So suchen Sie mithilfe eines Range\-Objekts nach Text  
  
1.  Definieren Sie ein <xref:Microsoft.Office.Interop.Word.Range>\-Objekt, das aus dem zweiten Absatz im Dokuments besteht.  
  
     Das folgende Codebeispiel kann in einer Anpassung auf Dokumentebene verwendet werden.  
  
     [!code-csharp[Trin_VstcoreWordAutomation#72](../snippets/csharp/VS_Snippets_OfficeSP/Trin_VstcoreWordAutomation/CS/ThisDocument.cs#72)]
     [!code-vb[Trin_VstcoreWordAutomation#72](../snippets/visualbasic/VS_Snippets_OfficeSP/Trin_VstcoreWordAutomation/VB/ThisDocument.vb#72)]  
  
     Das folgende Codebeispiel kann in einem VSTO\-Add\-In verwendet werden.  In diesem Beispiel wird das aktive Dokument verwendet.  
  
     [!code-csharp[Trin_VstcoreWordAutomationAddIn#72](../snippets/csharp/VS_Snippets_OfficeSP/Trin_VstcoreWordAutomationAddIn/CS/ThisAddIn.cs#72)]
     [!code-vb[Trin_VstcoreWordAutomationAddIn#72](../snippets/visualbasic/VS_Snippets_OfficeSP/Trin_VstcoreWordAutomationAddIn/VB/ThisAddIn.vb#72)]  
  
2.  Deaktivieren Sie zunächst mithilfe der Eigenschaft <xref:Microsoft.Office.Interop.Word.Range.Find%2A> des <xref:Microsoft.Office.Interop.Word.Range>\-Objekts alle vorhandenen Formatierungsoptionen, und suchen Sie dann nach der Zeichenfolge **find me**.  
  
     [!code-csharp[Trin_VstcoreWordAutomation#73](../snippets/csharp/VS_Snippets_OfficeSP/Trin_VstcoreWordAutomation/CS/ThisDocument.cs#73)]
     [!code-vb[Trin_VstcoreWordAutomation#73](../snippets/visualbasic/VS_Snippets_OfficeSP/Trin_VstcoreWordAutomation/VB/ThisDocument.vb#73)]  
  
3.  Zeigen Sie die Ergebnisse der Suche in einem Meldungsfeld an, und wählen Sie den <xref:Microsoft.Office.Interop.Word.Range> aus, um sie sichtbar zu machen.  
  
     [!code-csharp[Trin_VstcoreWordAutomation#74](../snippets/csharp/VS_Snippets_OfficeSP/Trin_VstcoreWordAutomation/CS/ThisDocument.cs#74)]
     [!code-vb[Trin_VstcoreWordAutomation#74](../snippets/visualbasic/VS_Snippets_OfficeSP/Trin_VstcoreWordAutomation/VB/ThisDocument.vb#74)]  
  
     Wenn bei der Suche ein Fehler auftritt, wird der zweite Absatz ausgewählt. Wenn die Suche erfolgreich ist, werden die Suchkriterien angezeigt.  
  
 Das folgende Beispiel zeigt den vollständigen Code für eine Anpassung auf Dokumentebene.  Wenn Sie dieses Beispiel verwenden möchten, führen Sie den Code von der `ThisDocument`\-Klasse im Projekt aus.  
  
 [!code-csharp[Trin_VstcoreWordAutomation#71](../snippets/csharp/VS_Snippets_OfficeSP/Trin_VstcoreWordAutomation/CS/ThisDocument.cs#71)]
 [!code-vb[Trin_VstcoreWordAutomation#71](../snippets/visualbasic/VS_Snippets_OfficeSP/Trin_VstcoreWordAutomation/VB/ThisDocument.vb#71)]  
  
 Das folgende Beispiel zeigt den vollständigen Code für ein VSTO\-Add\-In.  Wenn Sie dieses Beispiel verwenden möchten, führen Sie den Code von der `ThisAddIn`\-Klasse im Projekt aus.  
  
 [!code-csharp[Trin_VstcoreWordAutomationAddIn#71](../snippets/csharp/VS_Snippets_OfficeSP/Trin_VstcoreWordAutomationAddIn/CS/ThisAddIn.cs#71)]
 [!code-vb[Trin_VstcoreWordAutomationAddIn#71](../snippets/visualbasic/VS_Snippets_OfficeSP/Trin_VstcoreWordAutomationAddIn/VB/ThisAddIn.vb#71)]  
  
## Suchen nach und Ersetzen von Text in Dokumenten  
 Der folgende Code durchsucht die aktuelle Auswahl und ersetzt alle Vorkommen der Zeichenfolge **find me** durch die Zeichenfolge **Found**.  
  
#### So suchen Sie nach Text und ersetzen Text in Dokumenten  
  
1.  Fügen Sie den folgenden Beispielcode der Klasse `ThisDocument` oder `ThisAddIn` im Projekt hinzu.  
  
     [!code-csharp[Trin_VstcoreWordAutomation#75](../snippets/csharp/VS_Snippets_OfficeSP/Trin_VstcoreWordAutomation/CS/ThisDocument.cs#75)]
     [!code-vb[Trin_VstcoreWordAutomation#75](../snippets/visualbasic/VS_Snippets_OfficeSP/Trin_VstcoreWordAutomation/VB/ThisDocument.vb#75)]  
  
     Die Klasse <xref:Microsoft.Office.Interop.Word.Find> verfügt über eine Methode <xref:Microsoft.Office.Interop.Word.Find.ClearFormatting%2A>, und die Klasse <xref:Microsoft.Office.Interop.Word.Replacement> verfügt ebenfalls über eine eigene Methode <xref:Microsoft.Office.Interop.Word.Replacement.ClearFormatting%2A>.  Wenn Sie Suchen\-und\-Ersetzen\-Vorgänge ausführen, müssen Sie die Methode ClearFormatting beider Objekte verwenden.  Wenn Sie nur das <xref:Microsoft.Office.Interop.Word.Find>\-Objekt verwenden, erhalten Sie ggf. unerwartete Ergebnisse im Ersetzungstext.  
  
2.  Verwenden Sie die Methode <xref:Microsoft.Office.Interop.Word.Find.Execute%2A> des <xref:Microsoft.Office.Interop.Word.Find>\-Objekts, um jedes gefundene Element zu ersetzen.  Verwenden Sie zum Angeben der zu ersetzenden Elemente den Parameter *Replace*.  Dieser Parameter kann einen der folgenden <xref:Microsoft.Office.Interop.Word.WdReplace>\-Werte aufweisen:  
  
    -   <xref:Microsoft.Office.Interop.Word.WdReplace.wdReplaceAll> ersetzt alle gefundenen Elemente.  
  
    -   <xref:Microsoft.Office.Interop.Word.WdReplace.wdReplaceNone> ersetzt keines der gefundenen Elemente.  
  
    -   <xref:Microsoft.Office.Interop.Word.WdReplace.wdReplaceOne> ersetzt das erste gefundene Element.  
  
## Siehe auch  
 [Gewusst wie: Programmgesteuertes Festlegen von Suchoptionen in Word](../vsto/how-to-programmatically-set-search-options-in-word.md)   
 [Gewusst wie: Programmgesteuertes Durchlaufen gefundener Elemente in Dokumenten](../vsto/how-to-programmatically-loop-through-found-items-in-documents.md)   
 [Gewusst wie: Programmgesteuertes Definieren und Markieren von Bereichen in Dokumenten](../vsto/how-to-programmatically-define-and-select-ranges-in-documents.md)   
 [Gewusst wie: Programmgesteuertes Wiederherstellen der Auswahl nach Suchvorgängen](../vsto/how-to-programmatically-restore-selections-after-searches.md)   
 [Optionale Parameter in Office-Lösungen](../vsto/optional-parameters-in-office-solutions.md)  
  
  