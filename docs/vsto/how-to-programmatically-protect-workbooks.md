---
title: 'Vorgehensweise: Programmgesteuertes Schützen von Arbeitsmappen'
ms.date: 02/02/2017
ms.topic: conceptual
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
ms.openlocfilehash: 12391f16e2797941cf83177aa1c83ed0dd2c0045
ms.sourcegitcommit: d0425b6b7d4b99e17ca6ac0671282bc718f80910
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 02/21/2019
ms.locfileid: "56644600"
---
# <a name="how-to-programmatically-protect-workbooks"></a>Vorgehensweise: Programmgesteuertes Schützen von Arbeitsmappen
  Sie können eine Microsoft Office Excel-Arbeitsmappe schützen, sodass Benutzer hinzufügen oder Löschen von Arbeitsblättern und Schutz für die Arbeitsmappe auch programmgesteuert aufheben können nicht. Optional können Sie ein Kennwort angeben, gibt an, ob die Struktur (Benutzer können keine Tabellen verschieben) werden soll, und gibt an, ob die Fenster der Arbeitsmappe geschützt werden sollen.

 [!INCLUDE[appliesto_xlalldocapp](../vsto/includes/appliesto-xlalldocapp-md.md)]

 Schützen einer Arbeitsmappe wird Benutzern durch die Bearbeitung von Zellen nicht beendet werden. Um die Daten zu schützen, müssen Sie die Arbeitsblätter schützen. Weitere Informationen finden Sie unter [Vorgehensweise: Programmgesteuertes Schützen von Arbeitsblättern](../vsto/how-to-programmatically-protect-worksheets.md).

 Die folgenden Codebeispiele verwenden Sie eine Variable, ein Kennwort enthalten, die vom Benutzer abgerufen werden.

## <a name="protect-a-workbook-that-is-part-of-a-document-level-customization"></a>Schützen Sie eine Arbeitsmappe, die Teil einer Anpassung auf Dokumentebene ist

### <a name="to-protect-a-workbook"></a>Eine Arbeitsmappe schützen

1.  Rufen Sie die <xref:Microsoft.Office.Tools.Excel.Workbook.Protect%2A> Methode der Arbeitsmappe und ein Kennwort enthalten. Um das folgende Codebeispiel verwenden möchten, führen Sie es der `ThisWorkbook` -Klasse, nicht in einer Sheet-Klasse.

     [!code-csharp[Trin_VstcoreExcelAutomation#10](../vsto/codesnippet/CSharp/Trin_VstcoreExcelAutomationCS/ThisWorkbook.cs#10)]
     [!code-vb[Trin_VstcoreExcelAutomation#10](../vsto/codesnippet/VisualBasic/Trin_VstcoreExcelAutomation/ThisWorkbook.vb#10)]

### <a name="to-unprotect-a-workbook"></a>Zum Aufheben des Schutzes von einer Arbeitsmappe

1.  Rufen Sie die <xref:Microsoft.Office.Tools.Excel.Workbook.Unprotect%2A> Methode und übergeben ein Kennwort ein, wenn dies erforderlich ist. Um das folgende Codebeispiel verwenden möchten, führen Sie es der `ThisWorkbook` -Klasse, nicht in einer Sheet-Klasse.

     [!code-csharp[Trin_VstcoreExcelAutomation#11](../vsto/codesnippet/CSharp/Trin_VstcoreExcelAutomationCS/ThisWorkbook.cs#11)]
     [!code-vb[Trin_VstcoreExcelAutomation#11](../vsto/codesnippet/VisualBasic/Trin_VstcoreExcelAutomation/ThisWorkbook.vb#11)]

## <a name="protect-a-workbook-by-using-an-application-level-add-in"></a>Schützen einer Arbeitsmappe mithilfe eines Add-Ins auf Anwendungsebene

### <a name="to-protect-a-workbook"></a>Eine Arbeitsmappe schützen

1.  Rufen Sie die <xref:Microsoft.Office.Interop.Excel._Workbook.Protect%2A> Methode der Arbeitsmappe und ein Kennwort enthalten. Dieses Codebeispiel verwendet die aktive Arbeitsmappe. Wenn Sie dieses Beispiel verwenden möchten, führen Sie den Code von der `ThisAddIn` -Klasse im Projekt aus.

     [!code-csharp[Trin_VstcoreExcelAutomationAddIn#6](../vsto/codesnippet/CSharp/trin_vstcoreexcelautomationaddin/ThisAddIn.cs#6)]
     [!code-vb[Trin_VstcoreExcelAutomationAddIn#6](../vsto/codesnippet/VisualBasic/trin_vstcoreexcelautomationaddin/ThisAddIn.vb#6)]

### <a name="to-unprotect-a-workbook"></a>Zum Aufheben des Schutzes von einer Arbeitsmappe

1.  Rufen Sie die <xref:Microsoft.Office.Interop.Excel._Workbook.Unprotect%2A> Methode der aktiven Arbeitsmappe, und übergeben Sie ein Kennwort erforderlich. Wenn Sie dieses Beispiel verwenden möchten, führen Sie den Code von der `ThisAddIn` -Klasse im Projekt aus.

     [!code-csharp[Trin_VstcoreExcelAutomationAddIn#7](../vsto/codesnippet/CSharp/trin_vstcoreexcelautomationaddin/ThisAddIn.cs#7)]
     [!code-vb[Trin_VstcoreExcelAutomationAddIn#7](../vsto/codesnippet/VisualBasic/trin_vstcoreexcelautomationaddin/ThisAddIn.vb#7)]

## <a name="see-also"></a>Siehe auch
- [Arbeiten mit Arbeitsmappen](../vsto/working-with-workbooks.md)
- [Vorgehensweise: Programmgesteuertes Schützen von Arbeitsblättern](../vsto/how-to-programmatically-protect-worksheets.md)
- [Vorgehensweise: Programmgesteuertes Ausblenden von Arbeitsblättern](../vsto/how-to-programmatically-hide-worksheets.md)
- [Optionaler Parameter in Office-Projektmappen](../vsto/optional-parameters-in-office-solutions.md)
