---
title: "Gewusst wie: Programmgesteuertes Einf&#252;gen von Text in Word-Dokumente | Microsoft Docs"
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
  - "Bereiche, Einfügen von Text in Dokumente"
  - "Text [Office-Entwicklung in Visual Studio], Einfügen in Dokumente"
  - "Bereiche, Ersetzen von Text in Dokumenten"
  - "Dokumente [Office-Entwicklung in Visual Studio], Einfügen von Text"
  - "Text [Office-Entwicklung in Visual Studio], ersetzen"
ms.assetid: 405d7442-8ba3-4fcc-b17e-7b289ffd3967
caps.latest.revision: 41
author: "kempb"
ms.author: "kempb"
manager: "ghogen"
caps.handback.revision: 40
---
# Gewusst wie: Programmgesteuertes Einf&#252;gen von Text in Word-Dokumente
  Es gibt drei Hauptmethoden zum Einfügen von Text in Microsoft Office Word\-Dokumente:  
  
-   Fügen Sie Text in einen Bereich ein.  
  
-   Ersetzen Sie Text in einem Bereich durch neuen Text.  
  
-   Verwenden Sie die <xref:Microsoft.Office.Interop.Word.Selection.TypeText%2A>\-Methode eines <xref:Microsoft.Office.Interop.Word.Selection>\-Objekts, um Text an der Cursor\- oder Auswahlposition einzufügen.  
  
> [!NOTE]  
>  Sie können auch Text in Inhaltssteuerelemente und Lesezeichen einfügen. Weitere Informationen finden Sie unter [Inhaltssteuerelemente](../vsto/content-controls.md) und [Bookmark-Steuerelement](../vsto/bookmark-control.md).  
  
 [!INCLUDE[appliesto_wdalldocapp](../vsto/includes/appliesto-wdalldocapp-md.md)]  
  
## Einfügen von Text in einen Bereich  
 Verwenden Sie die <xref:Microsoft.Office.Interop.Word.Range.Text%2A>\-Eigenschaft eines <xref:Microsoft.Office.Interop.Word.Range>\-Objekts, um Text in ein Dokument einzufügen.  
  
#### So fügen Sie Text in einen Bereich ein  
  
1.  Geben Sie einen Bereich am Anfang eines Dokuments an, und fügen Sie den Text **New Text** ein.  
  
     Das folgende Codebeispiel kann in einer Anpassung auf Dokumentebene verwendet werden.  
  
     [!code-csharp[Trin_VstcoreWordAutomation#51](../snippets/csharp/VS_Snippets_OfficeSP/Trin_VstcoreWordAutomation/CS/ThisDocument.cs#51)]
     [!code-vb[Trin_VstcoreWordAutomation#51](../snippets/visualbasic/VS_Snippets_OfficeSP/Trin_VstcoreWordAutomation/VB/ThisDocument.vb#51)]  
  
     Das folgende Codebeispiel kann in einem VSTO\-Add\-In verwendet werden. In diesem Code wird das aktive Dokument verwendet.  
  
     [!code-csharp[Trin_VstcoreWordAutomationAddIn#51](../snippets/csharp/VS_Snippets_OfficeSP/Trin_VstcoreWordAutomationAddIn/CS/ThisAddIn.cs#51)]
     [!code-vb[Trin_VstcoreWordAutomationAddIn#51](../snippets/visualbasic/VS_Snippets_OfficeSP/Trin_VstcoreWordAutomationAddIn/VB/ThisAddIn.vb#51)]  
  
2.  Wählen Sie das <xref:Microsoft.Office.Interop.Word.Range>\-Objekt aus, das von einem Zeichen auf die Länge des eingefügten Texts erweitert wurde.  
  
     [!code-csharp[Trin_VstcoreWordAutomation#52](../snippets/csharp/VS_Snippets_OfficeSP/Trin_VstcoreWordAutomation/CS/ThisDocument.cs#52)]
     [!code-vb[Trin_VstcoreWordAutomation#52](../snippets/visualbasic/VS_Snippets_OfficeSP/Trin_VstcoreWordAutomation/VB/ThisDocument.vb#52)]  
  
## Ersetzen von Text in einem Bereich  
 Wenn der angegebene Bereich Text enthält, wird der gesamte Text im Bereich durch den eingefügten Text ersetzt.  
  
#### So ersetzen Sie Text in einem Bereich  
  
1.  Erstellen Sie ein <xref:Microsoft.Office.Interop.Word.Range>\-Objekt, das aus den ersten 12 Zeichen des Dokuments besteht.  
  
     Das folgende Codebeispiel kann in einer Anpassung auf Dokumentebene verwendet werden.  
  
     [!code-csharp[Trin_VstcoreWordAutomation#53](../snippets/csharp/VS_Snippets_OfficeSP/Trin_VstcoreWordAutomation/CS/ThisDocument.cs#53)]
     [!code-vb[Trin_VstcoreWordAutomation#53](../snippets/visualbasic/VS_Snippets_OfficeSP/Trin_VstcoreWordAutomation/VB/ThisDocument.vb#53)]  
  
     Das folgende Codebeispiel kann in einem VSTO\-Add\-In verwendet werden. In diesem Code wird das aktive Dokument verwendet.  
  
     [!code-csharp[Trin_VstcoreWordAutomationAddIn#53](../snippets/csharp/VS_Snippets_OfficeSP/Trin_VstcoreWordAutomationAddIn/CS/ThisAddIn.cs#53)]
     [!code-vb[Trin_VstcoreWordAutomationAddIn#53](../snippets/visualbasic/VS_Snippets_OfficeSP/Trin_VstcoreWordAutomationAddIn/VB/ThisAddIn.vb#53)]  
  
2.  Ersetzen Sie diese Zeichen durch die Zeichenfolge **New Text**.  
  
     [!code-csharp[Trin_VstcoreWordAutomation#54](../snippets/csharp/VS_Snippets_OfficeSP/Trin_VstcoreWordAutomation/CS/ThisDocument.cs#54)]
     [!code-vb[Trin_VstcoreWordAutomation#54](../snippets/visualbasic/VS_Snippets_OfficeSP/Trin_VstcoreWordAutomation/VB/ThisDocument.vb#54)]  
  
3.  Wählen Sie den Bereich aus.  
  
     [!code-csharp[Trin_VstcoreWordAutomation#55](../snippets/csharp/VS_Snippets_OfficeSP/Trin_VstcoreWordAutomation/CS/ThisDocument.cs#55)]
     [!code-vb[Trin_VstcoreWordAutomation#55](../snippets/visualbasic/VS_Snippets_OfficeSP/Trin_VstcoreWordAutomation/VB/ThisDocument.vb#55)]  
  
## Einfügen von Text mithilfe von TypeText  
 Durch die <xref:Microsoft.Office.Interop.Word.Selection.TypeText%2A>\-Methode wird Text an der Auswahlposition eingefügt. Je nach den auf dem Benutzercomputer festgelegten Optionen verhält sich <xref:Microsoft.Office.Interop.Word.Selection.TypeText%2A> unterschiedlich. Durch den Code in der folgenden Prozedur wird eine <xref:Microsoft.Office.Interop.Word.Selection>\-Objektvariable deklariert und die **Overtype**\-Option deaktiviert, sofern sie aktiviert war. Wenn die **Overtype**\-Option aktiviert ist, wird sämtlicher Text neben dem Cursor überschrieben.  
  
#### So fügen Sie Text mithilfe der TypeText\-Methode ein  
  
1.  Deklarieren Sie eine <xref:Microsoft.Office.Interop.Word.Selection>\-Objektvariable.  
  
     [!code-csharp[Trin_VstcoreWordAutomation#57](../snippets/csharp/VS_Snippets_OfficeSP/Trin_VstcoreWordAutomation/CS/ThisDocument.cs#57)]
     [!code-vb[Trin_VstcoreWordAutomation#57](../snippets/visualbasic/VS_Snippets_OfficeSP/Trin_VstcoreWordAutomation/VB/ThisDocument.vb#57)]  
  
2.  Deaktivieren Sie die **Overtype**\-Option, falls sie eingeschaltet ist.  
  
     [!code-csharp[Trin_VstcoreWordAutomation#58](../snippets/csharp/VS_Snippets_OfficeSP/Trin_VstcoreWordAutomation/CS/ThisDocument.cs#58)]
     [!code-vb[Trin_VstcoreWordAutomation#58](../snippets/visualbasic/VS_Snippets_OfficeSP/Trin_VstcoreWordAutomation/VB/ThisDocument.vb#58)]  
  
3.  Überprüfen Sie, ob es sich bei der aktuellen Auswahl um eine Einfügemarke handelt.  
  
     Falls ja, fügt der Code einen Satz mithilfe von <xref:Microsoft.Office.Interop.Word.Selection.TypeText%2A> und dann eine Absatzmarke mithilfe der <xref:Microsoft.Office.Interop.Word.Selection.TypeParagraph%2A>\-Methode ein.  
  
     [!code-csharp[Trin_VstcoreWordAutomation#59](../snippets/csharp/VS_Snippets_OfficeSP/Trin_VstcoreWordAutomation/CS/ThisDocument.cs#59)]
     [!code-vb[Trin_VstcoreWordAutomation#59](../snippets/visualbasic/VS_Snippets_OfficeSP/Trin_VstcoreWordAutomation/VB/ThisDocument.vb#59)]  
  
4.  Durch den Code im **ElseIf**\-Block wird überprüft, ob die Auswahl eine normale Auswahl ist. Falls ja, wird durch einen anderen **If**\-Block überprüft, ob die **ReplaceSelection**\-Option aktiviert ist. Wenn dies der Fall ist, verwendet der Code die <xref:Microsoft.Office.Interop.Word.Selection.Collapse%2A>\-Methode, um die Auswahl auf eine Einfügemarke am Anfang des ausgewählten Textblocks zu reduzieren. Fügen Sie den Text und eine Absatzmarke ein.  
  
     [!code-csharp[Trin_VstcoreWordAutomation#60](../snippets/csharp/VS_Snippets_OfficeSP/Trin_VstcoreWordAutomation/CS/ThisDocument.cs#60)]
     [!code-vb[Trin_VstcoreWordAutomation#60](../snippets/visualbasic/VS_Snippets_OfficeSP/Trin_VstcoreWordAutomation/VB/ThisDocument.vb#60)]  
  
5.  Wenn die Auswahl keine Einfügemarke oder kein Block mit markierten Text ist, wird vom Code im **Else**\-Block keine Aktion ausgeführt.  
  
     [!code-csharp[Trin_VstcoreWordAutomation#61](../snippets/csharp/VS_Snippets_OfficeSP/Trin_VstcoreWordAutomation/CS/ThisDocument.cs#61)]
     [!code-vb[Trin_VstcoreWordAutomation#61](../snippets/visualbasic/VS_Snippets_OfficeSP/Trin_VstcoreWordAutomation/VB/ThisDocument.vb#61)]  
  
 Sie können auch die <xref:Microsoft.Office.Interop.Word.Selection.TypeBackspace%2A>\-Methode des <xref:Microsoft.Office.Interop.Word.Selection>\-Objekts verwenden, die die Funktionalität der RÜCKTASTE auf der Tastatur imitiert. Wenn es jedoch um das Einfügen und Bearbeiten von Text geht, bietet Ihnen das <xref:Microsoft.Office.Interop.Word.Range>\-Objekt mehr Steuerungsmöglichkeiten.  
  
 Das folgende Beispiel enthält den vollständigen Code. Wenn Sie dieses Beispiel verwenden möchten, führen Sie den Code von der `ThisDocument`\-Klasse oder `ThisAddIn`\-Klasse im Projekt aus.  
  
 [!code-csharp[Trin_VstcoreWordAutomation#56](../snippets/csharp/VS_Snippets_OfficeSP/Trin_VstcoreWordAutomation/CS/ThisDocument.cs#56)]
 [!code-vb[Trin_VstcoreWordAutomation#56](../snippets/visualbasic/VS_Snippets_OfficeSP/Trin_VstcoreWordAutomation/VB/ThisDocument.vb#56)]  
  
## Siehe auch  
 [Gewusst wie: Programmgesteuertes Formatieren von Text in Dokumenten](../vsto/how-to-programmatically-format-text-in-documents.md)   
 [Gewusst wie: Programmgesteuertes Definieren und Markieren von Bereichen in Dokumenten](../vsto/how-to-programmatically-define-and-select-ranges-in-documents.md)   
 [Gewusst wie: Programmgesteuertes Erweitern von Bereichen in Dokumenten](../vsto/how-to-programmatically-extend-ranges-in-documents.md)  
  
  