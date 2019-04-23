---
title: 'Vorgehensweise: Programmgesteuertes Ausführen von Excel-Berechnungen'
ms.date: 02/02/2017
ms.topic: conceptual
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- ranges, running calculations
- calculations, running in Excel
- Excel [Office development in Visual Studio], running calculations programmatically
- workbooks, running calculations
author: John-Hart
ms.author: johnhart
manager: jillfra
ms.workload:
- office
ms.openlocfilehash: bd6562a48a66c1c73cd281fb4510e2df737f6a04
ms.sourcegitcommit: 1fc6ee928733e61a1f42782f832ead9f7946d00c
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/22/2019
ms.locfileid: "60107267"
---
# <a name="how-to-programmatically-run-excel-calculations"></a>Vorgehensweise: Programmgesteuertes Ausführen von Excel-Berechnungen
  Sie verwenden einen ähnlichen Prozess zum Ausführen von Berechnungen in einer <xref:Microsoft.Office.Tools.Excel.NamedRange> Steuerelement oder ein systemeigenes Excel-Bereich-Objekt.

 [!INCLUDE[appliesto_xlalldocapp](../vsto/includes/appliesto-xlalldocapp-md.md)]

## <a name="run-calculations-in-a-namedrange-control"></a>Ausführen von Berechnungen in einem NamedRange-Steuerelement
 Das folgende Beispiel erstellt eine <xref:Microsoft.Office.Tools.Excel.NamedRange> Zelle A1 und berechnet dann die Zelle. Dieser Code muss in einer Sheet-Klasse platziert werden und nicht in der `ThisWorkbook` -Klasse.

### <a name="to-run-calculations-in-a-namedrange-control"></a>Zum Ausführen von Berechnungen in einem NamedRange-Steuerelement

1. Erstellen des benannten Bereichs an.

     [!code-csharp[Trin_VstcoreExcelAutomation#75](../vsto/codesnippet/CSharp/Trin_VstcoreExcelAutomationCS/Sheet1.cs#75)]
     [!code-vb[Trin_VstcoreExcelAutomation#75](../vsto/codesnippet/VisualBasic/Trin_VstcoreExcelAutomation/Sheet1.vb#75)]

2. Rufen Sie die <xref:Microsoft.Office.Tools.Excel.NamedRange.Calculate%2A> Methode des angegebenen Bereichs.

     [!code-csharp[Trin_VstcoreExcelAutomation#76](../vsto/codesnippet/CSharp/Trin_VstcoreExcelAutomationCS/Sheet1.cs#76)]
     [!code-vb[Trin_VstcoreExcelAutomation#76](../vsto/codesnippet/VisualBasic/Trin_VstcoreExcelAutomation/Sheet1.vb#76)]

## <a name="run-calculations-in-a-native-excel-range"></a>Ausführen von Berechnungen in einem systemeigenen Excel-Bereich

### <a name="to-run-calculations-in-a-native-excel-range"></a>Zum Ausführen von Berechnungen in einem systemeigenen Excel-Bereich

1. Erstellen des benannten Bereichs an.

     [!code-csharp[Trin_VstcoreExcelAutomationAddIn#30](../vsto/codesnippet/CSharp/trin_vstcoreexcelautomationaddin/ThisAddIn.cs#30)]
     [!code-vb[Trin_VstcoreExcelAutomationAddIn#30](../vsto/codesnippet/VisualBasic/trin_vstcoreexcelautomationaddin/ThisAddIn.vb#30)]

2. Rufen Sie die <xref:Microsoft.Office.Interop.Excel.Range.Calculate%2A> Methode des angegebenen Bereichs.

     [!code-csharp[Trin_VstcoreExcelAutomationAddIn#31](../vsto/codesnippet/CSharp/trin_vstcoreexcelautomationaddin/ThisAddIn.cs#31)]
     [!code-vb[Trin_VstcoreExcelAutomationAddIn#31](../vsto/codesnippet/VisualBasic/trin_vstcoreexcelautomationaddin/ThisAddIn.vb#31)]

## <a name="see-also"></a>Siehe auch
- [Arbeiten mit Bereichen](../vsto/working-with-ranges.md)
- [NamedRange-Steuerelement](../vsto/namedrange-control.md)
- [Optionaler Parameter in Office-Projektmappen](../vsto/optional-parameters-in-office-solutions.md)
