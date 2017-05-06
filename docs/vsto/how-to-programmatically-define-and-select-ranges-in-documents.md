---
title: "Gewusst wie: Programmgesteuertes Definieren und Markieren von Bereichen in Dokumenten"
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
  - "Dokumente [Office-Entwicklung in Visual Studio], Bereiche"
  - "Dokumente [Office-Entwicklung in Visual Studio], Auswählen von Sätzen"
  - "Bereiche, Definieren in Dokumenten"
  - "Bereiche, Auswählen in Dokumenten"
  - "Sätze, Auswählen in Dokumenten"
ms.assetid: 0727c1cb-d44c-4f1c-a699-4365dd13be5d
caps.latest.revision: 46
author: "kempb"
ms.author: "kempb"
manager: "ghogen"
caps.handback.revision: 45
---
# Gewusst wie: Programmgesteuertes Definieren und Markieren von Bereichen in Dokumenten
  Sie können einen Bereich in einem Microsoft Office Word\-Dokument mithilfe eines <xref:Microsoft.Office.Interop.Word.Range>\-Objekts definieren.  Das gesamte Dokument lässt sich auf verschiedene Weisen auswählen, z. B. durch Verwendung der <xref:Microsoft.Office.Interop.Word.Range.Select%2A>\-Methode des <xref:Microsoft.Office.Interop.Word.Range>\-Objekts oder mithilfe der Content\-Eigenschaft der <xref:Microsoft.Office.Tools.Word.Document>\-Klasse \(in einer Anpassung auf Dokumentebene\) oder der <xref:Microsoft.Office.Interop.Word.Document>\-Klasse \(in einem VSTO\-Add\-In\).  
  
 [!INCLUDE[appliesto_wdalldocapp](../vsto/includes/appliesto-wdalldocapp-md.md)]  
  
## Definieren eines Bereichs  
 Das folgende Beispiel veranschaulicht das Erstellen eines neuen <xref:Microsoft.Office.Interop.Word.Range>\-Objekts, das die ersten sieben Zeichen im aktiven Dokument, einschließlich der nicht druckbaren Zeichen, enthält.  Anschließend wird der Text innerhalb des Bereichs ausgewählt.  
  
#### So definieren Sie einen Bereich in einer Anpassung auf Dokumentebene  
  
1.  Fügen Sie dem Dokument den Bereich hinzu, indem Sie ein Start\- und ein Endzeichen an die <xref:Microsoft.Office.Tools.Word.Document.Range%2A>\-Methode der <xref:Microsoft.Office.Tools.Word.Document>\-Klasse übergeben.  Wenn Sie dieses Codebeispiel verwenden möchten, führen Sie es von der `ThisDocument`\-Klasse im Projekt aus.  
  
     [!code-csharp[Trin_VstcoreWordAutomation#18](../snippets/csharp/VS_Snippets_OfficeSP/Trin_VstcoreWordAutomation/CS/ThisDocument.cs#18)]
     [!code-vb[Trin_VstcoreWordAutomation#18](../snippets/visualbasic/VS_Snippets_OfficeSP/Trin_VstcoreWordAutomation/VB/ThisDocument.vb#18)]  
  
#### So definieren Sie einen Bereich mithilfe eines VSTO\-Add\-Ins  
  
1.  Fügen Sie dem Dokument den Bereich hinzu, indem Sie ein Start\- und ein Endzeichen an die <xref:Microsoft.Office.Interop.Word._Document.Range%2A>\-Methode der <xref:Microsoft.Office.Interop.Word.Document>\-Klasse übergeben.  Im folgenden Codebeispiel wird dem aktiven Dokument ein Bereich hinzugefügt.  Wenn Sie dieses Codebeispiel verwenden möchten, führen Sie es von der `ThisAddIn`\-Klasse im Projekt aus.  
  
     [!code-csharp[Trin_VstcoreWordAutomationAddIn#18](../snippets/csharp/VS_Snippets_OfficeSP/Trin_VstcoreWordAutomationAddIn/CS/ThisAddIn.cs#18)]
     [!code-vb[Trin_VstcoreWordAutomationAddIn#18](../snippets/visualbasic/VS_Snippets_OfficeSP/Trin_VstcoreWordAutomationAddIn/VB/ThisAddIn.vb#18)]  
  
## Auswahl eines Bereich in einer Anpassung auf Dokumentebene  
 Die folgenden Beispiele zeigen, wie Sie das gesamte Dokument mithilfe der <xref:Microsoft.Office.Interop.Word.Range.Select%2A>\-Methode eines <xref:Microsoft.Office.Interop.Word.Range>\-Objekts oder mithilfe der <xref:Microsoft.Office.Tools.Word.Document.Content%2A>\-Eigenschaft der <xref:Microsoft.Office.Tools.Word.Document>\-Klasse auswählen.  
  
#### So wählen Sie das gesamte Dokument als Bereich mithilfe der Select\-Methode aus  
  
1.  Verwenden Sie die <xref:Microsoft.Office.Interop.Word.Range.Select%2A>\-Methode eines <xref:Microsoft.Office.Interop.Word.Range>, der das gesamte Dokument enthält.  Wenn Sie das folgende Codebeispiel verwenden möchten, führen Sie es von der `ThisDocument`\-Klasse im Projekt aus.  
  
     [!code-csharp[Trin_VstcoreWordAutomation#19](../snippets/csharp/VS_Snippets_OfficeSP/Trin_VstcoreWordAutomation/CS/ThisDocument.cs#19)]
     [!code-vb[Trin_VstcoreWordAutomation#19](../snippets/visualbasic/VS_Snippets_OfficeSP/Trin_VstcoreWordAutomation/VB/ThisDocument.vb#19)]  
  
#### So wählen Sie das gesamte Dokument als Bereich mithilfe der Content\-Eigenschaft aus  
  
1.  Verwenden Sie die <xref:Microsoft.Office.Tools.Word.Document.Content%2A>\-Eigenschaft, um einen Bereich zu definieren, der das gesamte Dokument umfasst.  
  
     [!code-csharp[Trin_VstcoreWordAutomation#20](../snippets/csharp/VS_Snippets_OfficeSP/Trin_VstcoreWordAutomation/CS/ThisDocument.cs#20)]
     [!code-vb[Trin_VstcoreWordAutomation#20](../snippets/visualbasic/VS_Snippets_OfficeSP/Trin_VstcoreWordAutomation/VB/ThisDocument.vb#20)]  
  
 Sie können auch Methoden und Eigenschaften anderer Objekte verwenden, um einen Bereich zu definieren.  
  
#### So wählen Sie einen Satz im aktiven Dokument aus  
  
1.  Legen Sie den Bereich mithilfe der <xref:Microsoft.Office.Interop.Word.Sentences>\-Auflistung fest.  Verwenden Sie den Index des Satzes, den Sie auswählen möchten.  
  
     [!code-csharp[Trin_VstcoreWordAutomation#21](../snippets/csharp/VS_Snippets_OfficeSP/Trin_VstcoreWordAutomation/CS/ThisDocument.cs#21)]
     [!code-vb[Trin_VstcoreWordAutomation#21](../snippets/visualbasic/VS_Snippets_OfficeSP/Trin_VstcoreWordAutomation/VB/ThisDocument.vb#21)]  
  
 Eine andere Möglichkeit zum Auswählen eines Satzes besteht darin, den Start\- und Endwert für den Bereich manuell festzulegen.  
  
#### So wählen Sie einen Satz durch manuelles Festlegen des Start\- und Endwerts aus  
  
1.  Erstellen Sie eine Bereichsvariable.  
  
     [!code-csharp[Trin_VstcoreWordAutomation#23](../snippets/csharp/VS_Snippets_OfficeSP/Trin_VstcoreWordAutomation/CS/ThisDocument.cs#23)]
     [!code-vb[Trin_VstcoreWordAutomation#23](../snippets/visualbasic/VS_Snippets_OfficeSP/Trin_VstcoreWordAutomation/VB/ThisDocument.vb#23)]  
  
2.  Überprüfen Sie, ob mindestens zwei Sätze im Dokument vorhanden sind, legen Sie das *Start*\-Argument und das *End*\-Argument des Bereichs fest, und wählen Sie dann den Bereich aus.  
  
     [!code-csharp[Trin_VstcoreWordAutomation#24](../snippets/csharp/VS_Snippets_OfficeSP/Trin_VstcoreWordAutomation/CS/ThisDocument.cs#24)]
     [!code-vb[Trin_VstcoreWordAutomation#24](../snippets/visualbasic/VS_Snippets_OfficeSP/Trin_VstcoreWordAutomation/VB/ThisDocument.vb#24)]  
  
## Auswählen eines Bereichs mithilfe eines VSTO\-Add\-Ins  
 Die folgenden Beispiele zeigen, wie Sie das gesamte Dokument mithilfe der <xref:Microsoft.Office.Interop.Word.Range.Select%2A>\-Methode eines <xref:Microsoft.Office.Interop.Word.Range>\-Objekts oder mithilfe der <xref:Microsoft.Office.Interop.Word._Document.Content%2A>\-Eigenschaft der <xref:Microsoft.Office.Interop.Word.Document>\-Klasse auswählen.  
  
#### So wählen Sie das gesamte Dokument als Bereich mithilfe der Select\-Methode aus  
  
1.  Verwenden Sie die <xref:Microsoft.Office.Interop.Word.Range.Select%2A>\-Methode eines <xref:Microsoft.Office.Interop.Word.Range>, der das gesamte Dokument enthält.  Im folgenden Codebeispiel wird der Inhalt des aktiven Dokuments ausgewählt.  Wenn Sie dieses Codebeispiel verwenden möchten, führen Sie es von der `ThisAddIn`\-Klasse im Projekt aus.  
  
     [!code-csharp[Trin_VstcoreWordAutomationAddIn#19](../snippets/csharp/VS_Snippets_OfficeSP/Trin_VstcoreWordAutomationAddIn/CS/ThisAddIn.cs#19)]
     [!code-vb[Trin_VstcoreWordAutomationAddIn#19](../snippets/visualbasic/VS_Snippets_OfficeSP/Trin_VstcoreWordAutomationAddIn/VB/ThisAddIn.vb#19)]  
  
#### So wählen Sie das gesamte Dokument als Bereich mithilfe der Content\-Eigenschaft aus  
  
1.  Verwenden Sie die <xref:Microsoft.Office.Interop.Word._Document.Content%2A>\-Eigenschaft, um einen Bereich zu definieren, der das gesamte Dokument umfasst.  
  
     [!code-csharp[Trin_VstcoreWordAutomationAddIn#20](../snippets/csharp/VS_Snippets_OfficeSP/Trin_VstcoreWordAutomationAddIn/CS/ThisAddIn.cs#20)]
     [!code-vb[Trin_VstcoreWordAutomationAddIn#20](../snippets/visualbasic/VS_Snippets_OfficeSP/Trin_VstcoreWordAutomationAddIn/VB/ThisAddIn.vb#20)]  
  
 Sie können auch Methoden und Eigenschaften anderer Objekte verwenden, um einen Bereich zu definieren.  
  
#### So wählen Sie einen Satz im aktiven Dokument aus  
  
1.  Legen Sie den Bereich mithilfe der <xref:Microsoft.Office.Interop.Word.Sentences>\-Auflistung fest.  Verwenden Sie den Index des Satzes, den Sie auswählen möchten.  
  
     [!code-csharp[Trin_VstcoreWordAutomationAddIn#21](../snippets/csharp/VS_Snippets_OfficeSP/Trin_VstcoreWordAutomationAddIn/CS/ThisAddIn.cs#21)]
     [!code-vb[Trin_VstcoreWordAutomationAddIn#21](../snippets/visualbasic/VS_Snippets_OfficeSP/Trin_VstcoreWordAutomationAddIn/VB/ThisAddIn.vb#21)]  
  
 Eine andere Möglichkeit zum Auswählen eines Satzes besteht darin, den Start\- und Endwert für den Bereich manuell festzulegen.  
  
#### So wählen Sie einen Satz durch manuelles Festlegen des Start\- und Endwerts aus  
  
1.  Erstellen Sie eine Bereichsvariable.  
  
     [!code-csharp[Trin_VstcoreWordAutomationAddIn#23](../snippets/csharp/VS_Snippets_OfficeSP/Trin_VstcoreWordAutomationAddIn/CS/ThisAddIn.cs#23)]
     [!code-vb[Trin_VstcoreWordAutomationAddIn#23](../snippets/visualbasic/VS_Snippets_OfficeSP/Trin_VstcoreWordAutomationAddIn/VB/ThisAddIn.vb#23)]  
  
2.  Überprüfen Sie, ob mindestens zwei Sätze im Dokument vorhanden sind, legen Sie das *Start*\-Argument und das *End*\-Argument des Bereichs fest, und wählen Sie dann den Bereich aus.  
  
     [!code-csharp[Trin_VstcoreWordAutomationAddIn#24](../snippets/csharp/VS_Snippets_OfficeSP/Trin_VstcoreWordAutomationAddIn/CS/ThisAddIn.cs#24)]
     [!code-vb[Trin_VstcoreWordAutomationAddIn#24](../snippets/visualbasic/VS_Snippets_OfficeSP/Trin_VstcoreWordAutomationAddIn/VB/ThisAddIn.vb#24)]  
  
## Siehe auch  
 [Übersicht über das Word-Objektmodell](../vsto/word-object-model-overview.md)   
 [Gewusst wie: Programmgesteuertes Erweitern von Bereichen in Dokumenten](../vsto/how-to-programmatically-extend-ranges-in-documents.md)   
 [Gewusst wie: Programmgesteuertes Abrufen von Start- und Endzeichen in Bereichen](../vsto/how-to-programmatically-retrieve-start-and-end-characters-in-ranges.md)   
 [Gewusst wie: Programmgesteuertes Erweitern von Bereichen in Dokumenten](../vsto/how-to-programmatically-extend-ranges-in-documents.md)   
 [Gewusst wie: Programmgesteuertes Zurücksetzen von Bereichen in Word-Dokumenten](../vsto/how-to-programmatically-reset-ranges-in-word-documents.md)   
 [Gewusst wie: Programmgesteuertes Reduzieren von Bereichen oder Markierungen in Dokumenten](../vsto/how-to-programmatically-collapse-ranges-or-selections-in-documents.md)   
 [Gewusst wie: Programmgesteuertes Ausschließen von Absatzmarken beim Erstellen von Bereichen](../vsto/how-to-programmatically-exclude-paragraph-marks-when-creating-ranges.md)  
  
  