---
title: 'Vorgehensweise: Programmgesteuertes Ausblenden von Text in Dokumenten'
ms.date: 02/02/2017
ms.topic: conceptual
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- documents [Office development in Visual Studio], hiding text
- text [Office development in Visual Studio], hiding in documents
author: John-Hart
ms.author: johnhart
manager: jillfra
ms.workload:
- office
ms.openlocfilehash: 1da471ff1911cdda4a62ef9c150236b3a225342f
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/23/2019
ms.locfileid: "62812767"
---
# <a name="how-to-programmatically-hide-text-in-documents"></a>Vorgehensweise: Programmgesteuertes Ausblenden von Text in Dokumenten
  Sie können Text in einem Dokument ausblenden, indem Sie die <xref:Microsoft.Office.Interop.Word._Font.Hidden%2A> -Eigenschaft der <xref:Microsoft.Office.Interop.Word.Range.Font%2A> für einen bestimmten Textbereich festlegen.

 Können beispielsweise den Text in zeitweise ausblenden einer <xref:Microsoft.Office.Tools.Word.Bookmark> (in einer Anpassung auf Dokumentebene) oder ein <xref:Microsoft.Office.Interop.Word.Bookmark> (in einem VSTO-Add-in), bevor Sie ein Dokument an einen Drucker senden.

 [!INCLUDE[appliesto_wdalldocapp](../vsto/includes/appliesto-wdalldocapp-md.md)]

## <a name="to-hide-text-in-a-bookmark-control-while-printing-the-document"></a>So blenden Sie Text in einem Bookmark-Steuerelement beim Drucken des Dokuments aus

1. Erstellen Sie eine Prozedur, die sämtlichen Text in einem angegebenen Bereich ausblendet.

     [!code-vb[Trin_VstcoreWordAutomation#105](../vsto/codesnippet/VisualBasic/Trin_VstcoreWordAutomationVB/ThisDocument.vb#105)]
     [!code-csharp[Trin_VstcoreWordAutomation#105](../vsto/codesnippet/CSharp/Trin_VstcoreWordAutomationCS/ThisDocument.cs#105)]

2. Erstellen Sie eine Prozedur, die sämtlichen Text in einem angegebenen Bereich anzeigt.

     [!code-vb[Trin_VstcoreWordAutomation#106](../vsto/codesnippet/VisualBasic/Trin_VstcoreWordAutomationVB/ThisDocument.vb#106)]
     [!code-csharp[Trin_VstcoreWordAutomation#106](../vsto/codesnippet/CSharp/Trin_VstcoreWordAutomationCS/ThisDocument.cs#106)]

3. Übergeben Sie den Bereich einer Textmarke an die `HideText` -Methode, drucken Sie das Dokument, und übergeben Sie dann denselben Bereich an die `UnhideText` -Methode.

     Das folgende Codebeispiel kann in einer Anpassung auf Dokumentebene verwendet werden. Wenn Sie dieses Beispiel verwenden möchten, führen Sie es von der `ThisDocument` -Klasse Ihres Projekts aus.

     [!code-vb[Trin_VstcoreWordAutomation#107](../vsto/codesnippet/VisualBasic/Trin_VstcoreWordAutomationVB/ThisDocument.vb#107)]
     [!code-csharp[Trin_VstcoreWordAutomation#107](../vsto/codesnippet/CSharp/Trin_VstcoreWordAutomationCS/ThisDocument.cs#107)]

     Das folgende Codebeispiel kann in einem VSTO-Add-In verwendet werden. In diesem Beispiel wird das aktive Dokument verwendet. Wenn Sie dieses Beispiel verwenden möchten, führen Sie es von der `ThisAddIn` -Klasse Ihres Projekts aus.

     [!code-vb[Trin_VstcoreWordAutomationAddIn#107](../vsto/codesnippet/VisualBasic/Trin_VstcoreWordAutomationAddIn/ThisAddIn.vb#107)]
     [!code-csharp[Trin_VstcoreWordAutomationAddIn#107](../vsto/codesnippet/CSharp/Trin_VstcoreWordAutomationAddIn/ThisAddIn.cs#107)]

## <a name="compile-the-code"></a>Kompilieren des Codes
 In diesem Codebeispiel wird davon ausgegangen, dass das Dokument enthält eine <xref:Microsoft.Office.Tools.Word.Bookmark> -Steuerelement (in einer Anpassung auf Dokumentebene) oder <xref:Microsoft.Office.Interop.Word.Bookmark> -Steuerelement (in einem VSTO-Add-in) mit dem Namen `bookmark1`.

## <a name="see-also"></a>Siehe auch
- [Vorgehensweise: Programmgesteuertes Drucken von Dokumenten](../vsto/how-to-programmatically-print-documents.md)
- [Vorgehensweise: Programmgesteuertes definieren und Markieren von Bereichen in Dokumenten](../vsto/how-to-programmatically-define-and-select-ranges-in-documents.md)
- [Vorgehensweise: Programmgesteuertes Zurücksetzen von Bereichen in Word-Dokumenten](../vsto/how-to-programmatically-reset-ranges-in-word-documents.md)
- [Vorgehensweise: Programmgesteuertes Aktualisieren von Lesezeichentext](../vsto/how-to-programmatically-update-bookmark-text.md)
- [Optionaler Parameter in Office-Projektmappen](../vsto/optional-parameters-in-office-solutions.md)
