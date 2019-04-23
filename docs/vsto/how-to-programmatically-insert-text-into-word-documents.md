---
title: 'Vorgehensweise: Programmgesteuertes Einfügen von Text in Word-Dokumente'
ms.date: 02/02/2017
ms.topic: conceptual
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- ranges, inserting text in documents
- text [Office development in Visual Studio], inserting in documents
- ranges, replacing text in documents
- documents [Office development in Visual Studio], inserting text
- text [Office development in Visual Studio], replacing
author: John-Hart
ms.author: johnhart
manager: jillfra
ms.workload:
- office
ms.openlocfilehash: a24fde5f04a88de7eec34836df38bc1cca8669ab
ms.sourcegitcommit: 1fc6ee928733e61a1f42782f832ead9f7946d00c
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/22/2019
ms.locfileid: "60060630"
---
# <a name="how-to-programmatically-insert-text-into-word-documents"></a>Vorgehensweise: Programmgesteuertes Einfügen von Text in Word-Dokumente
  Es gibt drei Hauptmethoden zum Einfügen von Text in Microsoft Office Word-Dokumente:

- Fügen Sie Text in einen Bereich ein.

- Ersetzen Sie Text in einem Bereich durch neuen Text.

- Verwenden Sie die <xref:Microsoft.Office.Interop.Word.Selection.TypeText%2A> -Methode eines <xref:Microsoft.Office.Interop.Word.Selection> -Objekts, um Text an der Cursor- oder Auswahlposition einzufügen.

> [!NOTE]
>  Sie können auch Text in Inhaltssteuerelemente und Lesezeichen einfügen. Weitere Informationen finden Sie unter [Inhaltssteuerelemente](../vsto/content-controls.md) und [Bookmark-Steuerelement](../vsto/bookmark-control.md).

 [!INCLUDE[appliesto_wdalldocapp](../vsto/includes/appliesto-wdalldocapp-md.md)]

## <a name="insert-text-in-a-range"></a>Fügen Sie Text in einem Bereich
 Verwenden Sie die <xref:Microsoft.Office.Interop.Word.Range.Text%2A> -Eigenschaft eines <xref:Microsoft.Office.Interop.Word.Range> -Objekts, um Text in ein Dokument einzufügen.

### <a name="to-insert-text-in-a-range"></a>So fügen Sie Text in einen Bereich ein

1. Geben Sie einen Bereich am Anfang eines Dokuments an, und fügen Sie den Text **New Text**ein.

     Das folgende Codebeispiel kann in einer Anpassung auf Dokumentebene verwendet werden.

     [!code-vb[Trin_VstcoreWordAutomation#51](../vsto/codesnippet/VisualBasic/Trin_VstcoreWordAutomationVB/ThisDocument.vb#51)]
     [!code-csharp[Trin_VstcoreWordAutomation#51](../vsto/codesnippet/CSharp/Trin_VstcoreWordAutomationCS/ThisDocument.cs#51)]

     Das folgende Codebeispiel kann in einem VSTO-Add-In verwendet werden. In diesem Code wird das aktive Dokument verwendet.

     [!code-vb[Trin_VstcoreWordAutomationAddIn#51](../vsto/codesnippet/VisualBasic/Trin_VstcoreWordAutomationAddIn/ThisAddIn.vb#51)]
     [!code-csharp[Trin_VstcoreWordAutomationAddIn#51](../vsto/codesnippet/CSharp/Trin_VstcoreWordAutomationAddIn/ThisAddIn.cs#51)]

2. Wählen Sie das <xref:Microsoft.Office.Interop.Word.Range> -Objekt aus, das von einem Zeichen auf die Länge des eingefügten Texts erweitert wurde.

     [!code-vb[Trin_VstcoreWordAutomation#52](../vsto/codesnippet/VisualBasic/Trin_VstcoreWordAutomationVB/ThisDocument.vb#52)]
     [!code-csharp[Trin_VstcoreWordAutomation#52](../vsto/codesnippet/CSharp/Trin_VstcoreWordAutomationCS/ThisDocument.cs#52)]

## <a name="replace-text-in-a-range"></a>Ersetzen von Text in einem Bereich
 Wenn der angegebene Bereich Text enthält, wird der gesamte Text im Bereich durch den eingefügten Text ersetzt.

### <a name="to-replace-text-in-a-range"></a>So ersetzen Sie Text in einem Bereich

1. Erstellen Sie ein <xref:Microsoft.Office.Interop.Word.Range> -Objekt, das aus den ersten 12 Zeichen des Dokuments besteht.

     Das folgende Codebeispiel kann in einer Anpassung auf Dokumentebene verwendet werden.

     [!code-vb[Trin_VstcoreWordAutomation#53](../vsto/codesnippet/VisualBasic/Trin_VstcoreWordAutomationVB/ThisDocument.vb#53)]
     [!code-csharp[Trin_VstcoreWordAutomation#53](../vsto/codesnippet/CSharp/Trin_VstcoreWordAutomationCS/ThisDocument.cs#53)]

     Das folgende Codebeispiel kann in einem VSTO-Add-In verwendet werden. In diesem Code wird das aktive Dokument verwendet.

     [!code-vb[Trin_VstcoreWordAutomationAddIn#53](../vsto/codesnippet/VisualBasic/Trin_VstcoreWordAutomationAddIn/ThisAddIn.vb#53)]
     [!code-csharp[Trin_VstcoreWordAutomationAddIn#53](../vsto/codesnippet/CSharp/Trin_VstcoreWordAutomationAddIn/ThisAddIn.cs#53)]

2. Ersetzen Sie diese Zeichen durch die Zeichenfolge **New Text**.

     [!code-vb[Trin_VstcoreWordAutomation#54](../vsto/codesnippet/VisualBasic/Trin_VstcoreWordAutomationVB/ThisDocument.vb#54)]
     [!code-csharp[Trin_VstcoreWordAutomation#54](../vsto/codesnippet/CSharp/Trin_VstcoreWordAutomationCS/ThisDocument.cs#54)]

3. Wählen Sie den Bereich aus.

     [!code-vb[Trin_VstcoreWordAutomation#55](../vsto/codesnippet/VisualBasic/Trin_VstcoreWordAutomationVB/ThisDocument.vb#55)]
     [!code-csharp[Trin_VstcoreWordAutomation#55](../vsto/codesnippet/CSharp/Trin_VstcoreWordAutomationCS/ThisDocument.cs#55)]

## <a name="insert-text-using-typetext"></a>Fügen Sie Text mithilfe von TypeText
 Durch die <xref:Microsoft.Office.Interop.Word.Selection.TypeText%2A> -Methode wird Text an der Auswahlposition eingefügt. Je nach den auf dem Benutzercomputer festgelegten Optionen verhält sich<xref:Microsoft.Office.Interop.Word.Selection.TypeText%2A> unterschiedlich. Durch den Code in der folgenden Prozedur wird eine <xref:Microsoft.Office.Interop.Word.Selection> -Objektvariable deklariert und die **Overtype** -Option deaktiviert, sofern sie aktiviert war. Wenn die **Overtype** -Option aktiviert ist, wird sämtlicher Text neben dem Cursor überschrieben.

### <a name="to-insert-text-using-the-typetext-method"></a>So fügen Sie Text mithilfe der TypeText-Methode ein

1. Deklarieren Sie eine <xref:Microsoft.Office.Interop.Word.Selection> -Objektvariable.

    [!code-vb[Trin_VstcoreWordAutomation#57](../vsto/codesnippet/VisualBasic/Trin_VstcoreWordAutomationVB/ThisDocument.vb#57)]
    [!code-csharp[Trin_VstcoreWordAutomation#57](../vsto/codesnippet/CSharp/Trin_VstcoreWordAutomationCS/ThisDocument.cs#57)]

2. Deaktivieren Sie die **Overtype** -Option, falls sie eingeschaltet ist.

    [!code-vb[Trin_VstcoreWordAutomation#58](../vsto/codesnippet/VisualBasic/Trin_VstcoreWordAutomationVB/ThisDocument.vb#58)]
    [!code-csharp[Trin_VstcoreWordAutomation#58](../vsto/codesnippet/CSharp/Trin_VstcoreWordAutomationCS/ThisDocument.cs#58)]

3. Überprüfen Sie, ob es sich bei der aktuellen Auswahl um eine Einfügemarke handelt.

    Falls ja, fügt der Code einen Satz mithilfe von <xref:Microsoft.Office.Interop.Word.Selection.TypeText%2A>und dann eine Absatzmarke mithilfe der <xref:Microsoft.Office.Interop.Word.Selection.TypeParagraph%2A> -Methode ein.

    [!code-vb[Trin_VstcoreWordAutomation#59](../vsto/codesnippet/VisualBasic/Trin_VstcoreWordAutomationVB/ThisDocument.vb#59)]
    [!code-csharp[Trin_VstcoreWordAutomation#59](../vsto/codesnippet/CSharp/Trin_VstcoreWordAutomationCS/ThisDocument.cs#59)]

4. Durch den Code im **ElseIf** -Block wird überprüft, ob die Auswahl eine normale Auswahl ist. Falls ja, wird durch einen anderen **If** -Block überprüft, ob die **ReplaceSelection** -Option aktiviert ist. Wenn dies der Fall ist, verwendet der Code die <xref:Microsoft.Office.Interop.Word.Selection.Collapse%2A> -Methode, um die Auswahl auf eine Einfügemarke am Anfang des ausgewählten Textblocks zu reduzieren. Fügen Sie den Text und eine Absatzmarke ein.

    [!code-vb[Trin_VstcoreWordAutomation#60](../vsto/codesnippet/VisualBasic/Trin_VstcoreWordAutomationVB/ThisDocument.vb#60)]
    [!code-csharp[Trin_VstcoreWordAutomation#60](../vsto/codesnippet/CSharp/Trin_VstcoreWordAutomationCS/ThisDocument.cs#60)]

5. Wenn die Auswahl keine Einfügemarke oder kein Block mit markierten Text ist, wird vom Code im **Else** -Block keine Aktion ausgeführt.

    [!code-vb[Trin_VstcoreWordAutomation#61](../vsto/codesnippet/VisualBasic/Trin_VstcoreWordAutomationVB/ThisDocument.vb#61)]
    [!code-csharp[Trin_VstcoreWordAutomation#61](../vsto/codesnippet/CSharp/Trin_VstcoreWordAutomationCS/ThisDocument.cs#61)]

   Können Sie auch die <xref:Microsoft.Office.Interop.Word.Selection.TypeBackspace%2A> Methode der <xref:Microsoft.Office.Interop.Word.Selection> -Objekt, das die Funktionalität von imitiert die **RÜCKTASTE** auf der Tastatur die Taste. Wenn es jedoch um das Einfügen und Bearbeiten von Text geht, bietet Ihnen das <xref:Microsoft.Office.Interop.Word.Range> -Objekt mehr Steuerungsmöglichkeiten.

   Das folgende Beispiel enthält den vollständigen Code. Wenn Sie dieses Beispiel verwenden möchten, führen Sie den Code von der `ThisDocument` -Klasse oder `ThisAddIn` -Klasse im Projekt aus.

   [!code-vb[Trin_VstcoreWordAutomation#56](../vsto/codesnippet/VisualBasic/Trin_VstcoreWordAutomationVB/ThisDocument.vb#56)]
   [!code-csharp[Trin_VstcoreWordAutomation#56](../vsto/codesnippet/CSharp/Trin_VstcoreWordAutomationCS/ThisDocument.cs#56)]

## <a name="see-also"></a>Siehe auch
- [Vorgehensweise: Programmgesteuertes Formatieren von Text in Dokumenten](../vsto/how-to-programmatically-format-text-in-documents.md)
- [Vorgehensweise: Programmgesteuertes definieren und Markieren von Bereichen in Dokumenten](../vsto/how-to-programmatically-define-and-select-ranges-in-documents.md)
- [Vorgehensweise: Programmgesteuertes Erweitern von Bereichen in Dokumenten](../vsto/how-to-programmatically-extend-ranges-in-documents.md)
