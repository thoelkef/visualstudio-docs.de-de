---
title: 'Vorgehensweise: Programmgesteuertes Drucken von Arbeitsblättern'
ms.date: 02/02/2017
ms.topic: conceptual
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- printing [Office development in Visual Studio], worksheets
- worksheets, printing
- print preview, worksheets
author: John-Hart
ms.author: johnhart
manager: jillfra
ms.workload:
- office
ms.openlocfilehash: 76315f6cde5bc54385e217a8f234389a7f45e621
ms.sourcegitcommit: 1fc6ee928733e61a1f42782f832ead9f7946d00c
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/22/2019
ms.locfileid: "60084193"
---
# <a name="how-to-programmatically-print-worksheets"></a>Vorgehensweise: Programmgesteuertes Drucken von Arbeitsblättern
  Sie können beliebige Arbeitsblätter aus einer Arbeitsmappe drucken.

 [!INCLUDE[appliesto_xlalldocapp](../vsto/includes/appliesto-xlalldocapp-md.md)]

## <a name="print-a-worksheet-in-a-document-level-customization"></a>Drucken Sie ein Arbeitsblatt in einer Anpassung auf Dokumentebene

### <a name="to-print-a-worksheet"></a>So drucken Sie ein Arbeitsblatt

1. Rufen Sie die <xref:Microsoft.Office.Tools.Excel.Worksheet.PrintOut%2A>-Methode von `Sheet1` auf, fordern Sie zwei Exemplare an, und lassen Sie das Dokument vor dem Druck in der Vorschau anzeigen.

    [!code-csharp[Trin_VstcoreExcelAutomation#22](../vsto/codesnippet/CSharp/Trin_VstcoreExcelAutomationCS/Sheet1.cs#22)]
    [!code-vb[Trin_VstcoreExcelAutomation#22](../vsto/codesnippet/VisualBasic/Trin_VstcoreExcelAutomation/Sheet1.vb#22)]

   Die <xref:Microsoft.Office.Tools.Excel.Worksheet.PrintPreview%2A> Methode können Sie zum Anzeigen des angegebenen Objekts in der **Seitenansicht** Fenster. Der folgende Code setzt voraus, dass Sie über ein <xref:Microsoft.Office.Tools.Excel.Worksheet>-Hostelement namens `Sheet1` verfügen.

### <a name="to-preview-a-page-before-printing"></a>So zeigen Sie eine Vorschau der Seite vor dem Druck an

1. Rufen Sie die <xref:Microsoft.Office.Tools.Excel.Worksheet.PrintPreview%2A> -Methode des Arbeitsblatts auf.

     [!code-csharp[Trin_VstcoreExcelAutomation#23](../vsto/codesnippet/CSharp/Trin_VstcoreExcelAutomationCS/Sheet1.cs#23)]
     [!code-vb[Trin_VstcoreExcelAutomation#23](../vsto/codesnippet/VisualBasic/Trin_VstcoreExcelAutomation/Sheet1.vb#23)]

## <a name="print-a-worksheet-in-a-vsto-add-in"></a>Drucken Sie ein Arbeitsblatt in einem VSTO-Add-in

### <a name="to-print-a-worksheet"></a>So drucken Sie ein Arbeitsblatt

1. Rufen Sie die <xref:Microsoft.Office.Interop.Excel._Worksheet.PrintOut%2A>-Methode des aktiven Arbeitsblatts auf, fordern Sie zwei Exemplare an, und lassen Sie das Dokument vor dem Druck in der Vorschau anzeigen.

    [!code-csharp[Trin_VstcoreExcelAutomationAddIn#14](../vsto/codesnippet/CSharp/trin_vstcoreexcelautomationaddin/ThisAddIn.cs#14)]
    [!code-vb[Trin_VstcoreExcelAutomationAddIn#14](../vsto/codesnippet/VisualBasic/trin_vstcoreexcelautomationaddin/ThisAddIn.vb#14)]

   Die <xref:Microsoft.Office.Interop.Excel._Worksheet.PrintPreview%2A> Methode können Sie zum Anzeigen des angegebenen Objekts in der **Seitenansicht** Fenster.

### <a name="to-preview-a-page-before-printing"></a>So zeigen Sie eine Vorschau der Seite vor dem Druck an

1. Rufen Sie die <xref:Microsoft.Office.Interop.Excel._Worksheet.PrintPreview%2A> -Methode des aktiven Arbeitsblatts auf.

     [!code-csharp[Trin_VstcoreExcelAutomationAddIn#15](../vsto/codesnippet/CSharp/trin_vstcoreexcelautomationaddin/ThisAddIn.cs#15)]
     [!code-vb[Trin_VstcoreExcelAutomationAddIn#15](../vsto/codesnippet/VisualBasic/trin_vstcoreexcelautomationaddin/ThisAddIn.vb#15)]

## <a name="see-also"></a>Siehe auch
- [Arbeiten mit Arbeitsblättern](../vsto/working-with-worksheets.md)
- [Vorgehensweise: Programmgesteuertes Überprüfen der Rechtschreibung in Arbeitsblättern](../vsto/how-to-programmatically-check-spelling-in-worksheets.md)
- [Arbeitsblatthostelement](../vsto/worksheet-host-item.md)
- [Globaler Zugriff auf Objekte in Office-Projekten](../vsto/global-access-to-objects-in-office-projects.md)
- [Optionaler Parameter in Office-Projektmappen](../vsto/optional-parameters-in-office-solutions.md)
