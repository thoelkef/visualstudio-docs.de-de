---
title: 'Vorgehensweise: Programm gesteuertes schützen von Arbeitsmappen'
ms.date: 02/02/2017
ms.topic: how-to
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- workbooks, passwords
- documents [Office development in Visual Studio], document protection
- workbooks, unprotecting
- document protection, removing from workbooks
- document protection, adding to workbooks
- workbooks, protecting
author: John-Hart
ms.author: johnhart
manager: jillfra
ms.workload:
- office
ms.openlocfilehash: ee7444c63c2d774e9b22ea612049f09429729c79
ms.sourcegitcommit: b885f26e015d03eafe7c885040644a52bb071fae
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 06/30/2020
ms.locfileid: "85537630"
---
# <a name="how-to-programmatically-protect-workbooks"></a>Vorgehensweise: Programm gesteuertes schützen von Arbeitsmappen
  Sie können eine Microsoft Office Excel-Arbeitsmappe schützen, sodass Benutzer keine Arbeitsblätter hinzufügen oder löschen können, und den Schutz der Arbeitsmappe auch Programm gesteuert aufheben. Optional können Sie ein Kennwort angeben. Geben Sie an, ob die Struktur geschützt werden soll (sodass Benutzer keine Blätter verschieben können), und geben Sie an, ob die Windows-Arbeitsmappe geschützt werden soll.

 [!INCLUDE[appliesto_xlalldocapp](../vsto/includes/appliesto-xlalldocapp-md.md)]

 Durch den Schutz einer-Arbeitsmappe wird verhindert, dass Benutzer Zellen bearbeiten. Um die Daten zu schützen, müssen Sie die Arbeitsblätter schützen. Weitere Informationen finden Sie unter Vorgehens [Weise: Programm gesteuertes schützen von Arbeitsblättern](../vsto/how-to-programmatically-protect-worksheets.md).

 In den folgenden Codebeispielen wird eine Variable verwendet, um ein Kennwort zu enthalten, das vom Benutzer abgerufen wird.

## <a name="protect-a-workbook-that-is-part-of-a-document-level-customization"></a>Schützen einer Arbeitsmappe, die Bestandteil einer Anpassung auf Dokument Ebene ist

### <a name="to-protect-a-workbook"></a>So schützen Sie eine Arbeitsmappe

1. Ruft die <xref:Microsoft.Office.Tools.Excel.Workbook.Protect%2A> -Methode der Arbeitsmappe auf und schließt ein Kennwort ein. Um das folgende Codebeispiel zu verwenden, führen Sie es in der- `ThisWorkbook` Klasse und nicht in einer Sheet-Klasse aus.

     [!code-csharp[Trin_VstcoreExcelAutomation#10](../vsto/codesnippet/CSharp/Trin_VstcoreExcelAutomationCS/ThisWorkbook.cs#10)]
     [!code-vb[Trin_VstcoreExcelAutomation#10](../vsto/codesnippet/VisualBasic/Trin_VstcoreExcelAutomation/ThisWorkbook.vb#10)]

### <a name="to-unprotect-a-workbook"></a>So heben Sie den Schutz für eine Arbeitsmappe auf

1. Wenden Sie die- <xref:Microsoft.Office.Tools.Excel.Workbook.Unprotect%2A> Methode an, und übergeben Sie ggf. ein Kennwort. Um das folgende Codebeispiel zu verwenden, führen Sie es in der- `ThisWorkbook` Klasse und nicht in einer Sheet-Klasse aus.

     [!code-csharp[Trin_VstcoreExcelAutomation#11](../vsto/codesnippet/CSharp/Trin_VstcoreExcelAutomationCS/ThisWorkbook.cs#11)]
     [!code-vb[Trin_VstcoreExcelAutomation#11](../vsto/codesnippet/VisualBasic/Trin_VstcoreExcelAutomation/ThisWorkbook.vb#11)]

## <a name="protect-a-workbook-by-using-an-application-level-add-in"></a>Schützen einer Arbeitsmappe mithilfe eines Add-Ins auf Anwendungsebene

### <a name="to-protect-a-workbook"></a>So schützen Sie eine Arbeitsmappe

1. Ruft die <xref:Microsoft.Office.Interop.Excel._Workbook.Protect%2A> -Methode der Arbeitsmappe auf und schließt ein Kennwort ein. In diesem Codebeispiel wird die aktive Arbeitsmappe verwendet. Wenn Sie dieses Beispiel verwenden möchten, führen Sie den Code von der `ThisAddIn` -Klasse im Projekt aus.

     [!code-csharp[Trin_VstcoreExcelAutomationAddIn#6](../vsto/codesnippet/CSharp/trin_vstcoreexcelautomationaddin/ThisAddIn.cs#6)]
     [!code-vb[Trin_VstcoreExcelAutomationAddIn#6](../vsto/codesnippet/VisualBasic/trin_vstcoreexcelautomationaddin/ThisAddIn.vb#6)]

### <a name="to-unprotect-a-workbook"></a>So heben Sie den Schutz für eine Arbeitsmappe auf

1. Wenden Sie die- <xref:Microsoft.Office.Interop.Excel._Workbook.Unprotect%2A> Methode der aktiven Arbeitsmappe an, und übergeben Sie ggf. ein Kennwort. Wenn Sie dieses Beispiel verwenden möchten, führen Sie den Code von der `ThisAddIn` -Klasse im Projekt aus.

     [!code-csharp[Trin_VstcoreExcelAutomationAddIn#7](../vsto/codesnippet/CSharp/trin_vstcoreexcelautomationaddin/ThisAddIn.cs#7)]
     [!code-vb[Trin_VstcoreExcelAutomationAddIn#7](../vsto/codesnippet/VisualBasic/trin_vstcoreexcelautomationaddin/ThisAddIn.vb#7)]

## <a name="see-also"></a>Weitere Informationen
- [Arbeiten mit Arbeitsmappen](../vsto/working-with-workbooks.md)
- [Vorgehensweise: Programm gesteuertes schützen von Arbeitsblättern](../vsto/how-to-programmatically-protect-worksheets.md)
- [Gewusst wie: Programm gesteuertes Ausblenden von Arbeitsblättern](../vsto/how-to-programmatically-hide-worksheets.md)
- [Optionale Parameter in Office-Projektmappen](../vsto/optional-parameters-in-office-solutions.md)
