---
title: "Gewusst wie: Programmgesteuertes Ausschlie&#223;en von Absatzmarken beim Erstellen von Bereichen"
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
  - "Dokumente [Office-Entwicklung in Visual Studio], Ausschließen von Absätzen"
  - "Bereiche, Ausschließen von Absatzmarken in Word"
  - "Dokumente [Office-Entwicklung in Visual Studio], Absatzmarken"
  - "Absätze, Steuern der Struktur"
ms.assetid: 6d563834-34bd-4462-a556-4339d9277eee
caps.latest.revision: 50
author: "kempb"
ms.author: "kempb"
manager: "ghogen"
caps.handback.revision: 49
---
# Gewusst wie: Programmgesteuertes Ausschlie&#223;en von Absatzmarken beim Erstellen von Bereichen
  Immer dann, wenn Sie ein <xref:Microsoft.Office.Interop.Word.Range>\-Objekt auf Grundlage eines Absatzes erstellen, umfasst der Bereich \(das Objekt\) alle nicht druckbaren Zeichen, etwa Absatzmarken. Möglicherweise möchten Sie den Text aus einem Quellabsatz in einen Zielabsatz einfügen. Soll der Zielabsatz dabei nicht in mehrere Absätze aufgeteilt werden, müssen Sie zunächst die Absatzmarke aus dem Quellabsatz entfernen. Außerdem kann es sein, dass Sie die Absatzmarke, weil Absatzformatierungsinformationen in ihr gespeichert sind, nicht einbeziehen möchten, wenn Sie den Bereich in einen vorhandenen Absatz einfügen.  
  
 [!INCLUDE[appliesto_wdalldocapp](../vsto/includes/appliesto-wdalldocapp-md.md)]  
  
 In der folgenden Beispielprozedur werden zwei Zeichenfolgenvariablen deklariert, die Inhalte des ersten und des zweiten Absatzes im aktiven Dokument abgerufen und anschließend deren Inhalte getauscht. Das Beispiel veranschaulicht Entfernen der Absatzmarke aus dem Bereich durch Verwenden der <xref:Microsoft.Office.Interop.Word.Range.MoveEnd%2A>\-Methode und Einfügen des Texts in den Absatz.  
  
### So steuern Sie die Absatzstruktur beim Einfügen von Text  
  
1.  Erstellen Sie für den ersten und den zweiten Absatz je eine Bereichsvariable, und rufen Sie deren Inhalte über die <xref:Microsoft.Office.Interop.Word.Range.Text%2A>\-Eigenschaft ab.  
  
     Das folgende Codebeispiel kann in einer Anpassung auf Dokumentebene verwendet werden.  
  
     [!code-csharp[Trin_VstcoreWordAutomation#27](../snippets/csharp/VS_Snippets_OfficeSP/Trin_VstcoreWordAutomation/CS/ThisDocument.cs#27)]
     [!code-vb[Trin_VstcoreWordAutomation#27](../snippets/visualbasic/VS_Snippets_OfficeSP/Trin_VstcoreWordAutomation/VB/ThisDocument.vb#27)]  
  
     Das folgende Codebeispiel kann in einem VSTO\-Add\-In auf Anwendungsebene verwendet werden. In diesem Code wird das aktive Dokument verwendet.  
  
     [!code-csharp[Trin_VstcoreWordAutomationAddIn#27](../snippets/csharp/VS_Snippets_OfficeSP/Trin_VstcoreWordAutomationAddIn/CS/ThisAddIn.cs#27)]
     [!code-vb[Trin_VstcoreWordAutomationAddIn#27](../snippets/visualbasic/VS_Snippets_OfficeSP/Trin_VstcoreWordAutomationAddIn/VB/ThisAddIn.vb#27)]  
  
2.  Ordnen Sie die <xref:Microsoft.Office.Interop.Word.Range.Text%2A>\-Eigenschaft zu, wobei Sie die Texte der beiden Absätze tauschen.  
  
     [!code-csharp[Trin_VstcoreWordAutomation#28](../snippets/csharp/VS_Snippets_OfficeSP/Trin_VstcoreWordAutomation/CS/ThisDocument.cs#28)]
     [!code-vb[Trin_VstcoreWordAutomation#28](../snippets/visualbasic/VS_Snippets_OfficeSP/Trin_VstcoreWordAutomation/VB/ThisDocument.vb#28)]  
  
3.  Wählen Sie nacheinander jeden Bereich aus, und zeigen Sie das jeweilige Ergebnis in einem Meldungsfeld an.  
  
     [!code-csharp[Trin_VstcoreWordAutomation#29](../snippets/csharp/VS_Snippets_OfficeSP/Trin_VstcoreWordAutomation/CS/ThisDocument.cs#29)]
     [!code-vb[Trin_VstcoreWordAutomation#29](../snippets/visualbasic/VS_Snippets_OfficeSP/Trin_VstcoreWordAutomation/VB/ThisDocument.vb#29)]  
  
4.  Passen Sie `firstRange` durch Verwenden der <xref:Microsoft.Office.Interop.Word.Range.MoveEnd%2A>\-Methode so an, dass die Absatzmarke nicht mehr Bestandteil von `firstRange` ist.  
  
     [!code-csharp[Trin_VstcoreWordAutomation#30](../snippets/csharp/VS_Snippets_OfficeSP/Trin_VstcoreWordAutomation/CS/ThisDocument.cs#30)]
     [!code-vb[Trin_VstcoreWordAutomation#30](../snippets/visualbasic/VS_Snippets_OfficeSP/Trin_VstcoreWordAutomation/VB/ThisDocument.vb#30)]  
  
5.  Ersetzen Sie den restlichen Text im ersten Absatz, indem Sie der <xref:Microsoft.Office.Interop.Word.Range.Text%2A>\-Eigenschaft des Bereichs eine neue Zeichenfolge zuweisen.  
  
     [!code-csharp[Trin_VstcoreWordAutomation#31](../snippets/csharp/VS_Snippets_OfficeSP/Trin_VstcoreWordAutomation/CS/ThisDocument.cs#31)]
     [!code-vb[Trin_VstcoreWordAutomation#31](../snippets/visualbasic/VS_Snippets_OfficeSP/Trin_VstcoreWordAutomation/VB/ThisDocument.vb#31)]  
  
6.  Ersetzen Sie den Text in `secondRange` einschließlich der Absatzmarke.  
  
     [!code-csharp[Trin_VstcoreWordAutomation#32](../snippets/csharp/VS_Snippets_OfficeSP/Trin_VstcoreWordAutomation/CS/ThisDocument.cs#32)]
     [!code-vb[Trin_VstcoreWordAutomation#32](../snippets/visualbasic/VS_Snippets_OfficeSP/Trin_VstcoreWordAutomation/VB/ThisDocument.vb#32)]  
  
7.  Markieren Sie `firstRange`, und zeigen Sie das Ergebnis in einem Meldungsfeld an. Führen Sie dann den gleichen Vorgang für `secondRange` aus.  
  
     Weil `firstRange` neu definiert wurde, um die Absatzmarke auszuschließen, wird die ursprüngliche Formatierung des Absatzes beibehalten. Es wurde jedoch über der Absatzmarke in `secondRange` ein Satz eingefügt, wodurch der separate Absatz entfernt wurde.  
  
     [!code-csharp[Trin_VstcoreWordAutomation#33](../snippets/csharp/VS_Snippets_OfficeSP/Trin_VstcoreWordAutomation/CS/ThisDocument.cs#33)]
     [!code-vb[Trin_VstcoreWordAutomation#33](../snippets/visualbasic/VS_Snippets_OfficeSP/Trin_VstcoreWordAutomation/VB/ThisDocument.vb#33)]  
  
     Die ursprünglichen Inhalte beider Bereiche wurden als Zeichenfolgen gespeichert, sodass Sie das Dokument in seinem ursprünglichen Zustand wiederherstellen können.  
  
8.  Passen Sie `firstRange` neu an, sodass die Absatzmarke wieder enthalten ist. Verwenden Sie dazu die <xref:Microsoft.Office.Interop.Word.Range.MoveEnd%2A>\-Methode für eine Zeichenposition.  
  
     [!code-csharp[Trin_VstcoreWordAutomation#34](../snippets/csharp/VS_Snippets_OfficeSP/Trin_VstcoreWordAutomation/CS/ThisDocument.cs#34)]
     [!code-vb[Trin_VstcoreWordAutomation#34](../snippets/visualbasic/VS_Snippets_OfficeSP/Trin_VstcoreWordAutomation/VB/ThisDocument.vb#34)]  
  
9. Löschen Sie `secondRange`. Dadurch wird der dritte Absatz an seiner ursprünglichen Position wiederhergestellt.  
  
     [!code-csharp[Trin_VstcoreWordAutomation#35](../snippets/csharp/VS_Snippets_OfficeSP/Trin_VstcoreWordAutomation/CS/ThisDocument.cs#35)]
     [!code-vb[Trin_VstcoreWordAutomation#35](../snippets/visualbasic/VS_Snippets_OfficeSP/Trin_VstcoreWordAutomation/VB/ThisDocument.vb#35)]  
  
10. Stellen Sie in `firstRange` den ursprünglichen Text des Absatzes wieder her.  
  
     [!code-csharp[Trin_VstcoreWordAutomation#36](../snippets/csharp/VS_Snippets_OfficeSP/Trin_VstcoreWordAutomation/CS/ThisDocument.cs#36)]
     [!code-vb[Trin_VstcoreWordAutomation#36](../snippets/visualbasic/VS_Snippets_OfficeSP/Trin_VstcoreWordAutomation/VB/ThisDocument.vb#36)]  
  
11. Verwenden Sie die <xref:Microsoft.Office.Interop.Word.Range.InsertAfter%2A>\-Methode des <xref:Microsoft.Office.Interop.Word.Range>\-Objekts, um den ursprünglichen Inhalt des zweiten Absatzes nach `firstRange` einzufügen, und markieren Sie dann `firstRange`.  
  
     [!code-csharp[Trin_VstcoreWordAutomation#37](../snippets/csharp/VS_Snippets_OfficeSP/Trin_VstcoreWordAutomation/CS/ThisDocument.cs#37)]
     [!code-vb[Trin_VstcoreWordAutomation#37](../snippets/visualbasic/VS_Snippets_OfficeSP/Trin_VstcoreWordAutomation/VB/ThisDocument.vb#37)]  
  
## Beispiel für die Anpassung auf Dokumentebene  
  
#### So steuern Sie die Absatzstruktur beim Einfügen von Text in Anpassungen auf Dokumentebene  
  
1.  Das folgende Beispiel zeigt die vollständige Methode für eine Anpassung auf Dokumentebene. Wenn Sie diesen Code verwenden möchten, führen Sie ihn von der `ThisDocument`\-Klasse im Projekt aus.  
  
     [!code-csharp[Trin_VstcoreWordAutomation#26](../snippets/csharp/VS_Snippets_OfficeSP/Trin_VstcoreWordAutomation/CS/ThisDocument.cs#26)]
     [!code-vb[Trin_VstcoreWordAutomation#26](../snippets/visualbasic/VS_Snippets_OfficeSP/Trin_VstcoreWordAutomation/VB/ThisDocument.vb#26)]  
  
## Beispiel für ein VSTO\-Add\-In  
  
#### So steuern Sie die Absatzstruktur beim Einfügen von Text in einem VSTO\-Add\-In  
  
1.  Das folgende Beispiel zeigt die vollständige Methode für ein VSTO\-Add\-In. Wenn Sie diesen Code verwenden möchten, führen Sie ihn von der `ThisAddIn`\-Klasse im Projekt aus.  
  
     [!code-csharp[Trin_VstcoreWordAutomationAddIn#26](../snippets/csharp/VS_Snippets_OfficeSP/Trin_VstcoreWordAutomationAddIn/CS/ThisAddIn.cs#26)]
     [!code-vb[Trin_VstcoreWordAutomationAddIn#26](../snippets/visualbasic/VS_Snippets_OfficeSP/Trin_VstcoreWordAutomationAddIn/VB/ThisAddIn.vb#26)]  
  
## Siehe auch  
 [Gewusst wie: Programmgesteuertes Erweitern von Bereichen in Dokumenten](../vsto/how-to-programmatically-extend-ranges-in-documents.md)   
 [Gewusst wie: Programmgesteuertes Reduzieren von Bereichen oder Markierungen in Dokumenten](../vsto/how-to-programmatically-collapse-ranges-or-selections-in-documents.md)   
 [Gewusst wie: Programmgesteuertes Einfügen von Text in Word-Dokumente](../vsto/how-to-programmatically-insert-text-into-word-documents.md)   
 [Gewusst wie: Programmgesteuertes Zurücksetzen von Bereichen in Word-Dokumenten](../vsto/how-to-programmatically-reset-ranges-in-word-documents.md)   
 [Gewusst wie: Programmgesteuertes Definieren und Markieren von Bereichen in Dokumenten](../vsto/how-to-programmatically-define-and-select-ranges-in-documents.md)   
 [Optionale Parameter in Office-Lösungen](../vsto/optional-parameters-in-office-solutions.md)  
  
  