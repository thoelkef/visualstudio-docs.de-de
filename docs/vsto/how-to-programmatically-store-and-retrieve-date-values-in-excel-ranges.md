---
title: 'Vorgehensweise: Programmgesteuertes speichern und Abrufen von Datumswerten in Excel-Bereichen'
ms.date: 02/02/2017
ms.topic: conceptual
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- Excel [Office development in Visual Studio], retrieving date values from ranges
- ranges, retrieving data values
- dates, retrieving from Excel ranges
- Excel [Office development in Visual Studio], storing date values in ranges
- date values, storing in Excel ranges
- dates, storing in Excel ranges
- ranges, storing date values
- date values
author: John-Hart
ms.author: johnhart
manager: jillfra
ms.workload:
- office
ms.openlocfilehash: 89c4a4598b92096d968225f7420d46244aeca3dc
ms.sourcegitcommit: 1fc6ee928733e61a1f42782f832ead9f7946d00c
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/22/2019
ms.locfileid: "60082905"
---
# <a name="how-to-programmatically-store-and-retrieve-date-values-in-excel-ranges"></a>Vorgehensweise: Programmgesteuertes speichern und Abrufen von Datumswerten in Excel-Bereichen
  Sie können das Speichern und Abrufen von Werten in einer <xref:Microsoft.Office.Tools.Excel.NamedRange> Steuerelement oder ein systemeigenes Excel-Bereich-Objekt.

 [!INCLUDE[appliesto_xlalldocapp](../vsto/includes/appliesto-xlalldocapp-md.md)]

 Wenn Sie einen Datumswert, der am oder nach dem in einem Bereich mit der Office-Entwicklungstools in Visual Studio die 1/1/1900 liegt speichern, wird es in OLE Automation (OA)-Format gespeichert. Verwenden Sie die <xref:System.DateTime.FromOADate%2A> Methode zum Abrufen des Werts von OLE Automation (OA) Datumsangaben. Wenn das Datum älter als 1/1/1900 liegt, wird es als Zeichenfolge gespeichert.

> [!NOTE]
>  Excel-Daten unterscheiden sich von OLE-Automatisierung Datumsangaben für die ersten zwei Monate 1900. Es gibt auch Unterschiede Wenn die **1904-Datumswerte** Option aktiviert ist. In den folgenden Codebeispielen werden diese Unterschiede nicht berücksichtigt.

## <a name="use-a-namedrange-control"></a>Verwenden Sie ein NamedRange-Steuerelement

- In diesem Beispiel ist für Anpassungen auf Dokumentebene. Der folgende Code muss in einer Sheet-Klasse platziert werden, nicht in der `ThisWorkbook` Klasse.

### <a name="to-store-a-date-value-in-a-named-range"></a>Um einen Date-Wert in einem benannten Bereich zu speichern.

1. Erstellen Sie eine <xref:Microsoft.Office.Tools.Excel.NamedRange> -Steuerelement zur Zelle **A1**.

     [!code-csharp[Trin_VstcoreExcelAutomation#50](../vsto/codesnippet/CSharp/Trin_VstcoreExcelAutomationCS/Sheet1.cs#50)]
     [!code-vb[Trin_VstcoreExcelAutomation#50](../vsto/codesnippet/VisualBasic/Trin_VstcoreExcelAutomation/Sheet1.vb#50)]

2. Festlegen des heutigen Datums als Wert für `NamedRange1`.

     [!code-csharp[Trin_VstcoreExcelAutomation#51](../vsto/codesnippet/CSharp/Trin_VstcoreExcelAutomationCS/Sheet1.cs#51)]
     [!code-vb[Trin_VstcoreExcelAutomation#51](../vsto/codesnippet/VisualBasic/Trin_VstcoreExcelAutomation/Sheet1.vb#51)]

### <a name="to-retrieve-a-date-value-from-a-named-range"></a>Einen Date-Wert aus einem benannten Bereich abrufen

1. Abrufen den Datumswert von `NamedRange1`.

     [!code-csharp[Trin_VstcoreExcelAutomation#52](../vsto/codesnippet/CSharp/Trin_VstcoreExcelAutomationCS/Sheet1.cs#52)]
     [!code-vb[Trin_VstcoreExcelAutomation#52](../vsto/codesnippet/VisualBasic/Trin_VstcoreExcelAutomation/Sheet1.vb#52)]

## <a name="use-native-excel-ranges"></a>Verwenden Sie systemeigene Excel-Bereiche

### <a name="to-store-a-date-value-in-a-native-excel-range-object"></a>Einen Date-Wert in ein systemeigenes Excel-Bereich-Objekt zu speichern

1. Erstellen Sie eine <xref:Microsoft.Office.Interop.Excel.Range> , die Zelle darstellt **A1**.

     [!code-csharp[Trin_VstcoreExcelAutomationAddIn#25](../vsto/codesnippet/CSharp/trin_vstcoreexcelautomationaddin/ThisAddIn.cs#25)]
     [!code-vb[Trin_VstcoreExcelAutomationAddIn#25](../vsto/codesnippet/VisualBasic/trin_vstcoreexcelautomationaddin/ThisAddIn.vb#25)]

2. Festlegen des heutigen Datums als Wert für `rng`.

     [!code-csharp[Trin_VstcoreExcelAutomationAddIn#26](../vsto/codesnippet/CSharp/trin_vstcoreexcelautomationaddin/ThisAddIn.cs#26)]
     [!code-vb[Trin_VstcoreExcelAutomationAddIn#26](../vsto/codesnippet/VisualBasic/trin_vstcoreexcelautomationaddin/ThisAddIn.vb#26)]

### <a name="to-retrieve-a-date-value-from-a-native-excel-range-object"></a>Einen Date-Wert aus einer systemeigenen Excel-Range-Objekts abrufen

1. Abrufen den Datumswert von `rng`.

     [!code-csharp[Trin_VstcoreExcelAutomationAddIn#27](../vsto/codesnippet/CSharp/trin_vstcoreexcelautomationaddin/ThisAddIn.cs#27)]
     [!code-vb[Trin_VstcoreExcelAutomationAddIn#27](../vsto/codesnippet/VisualBasic/trin_vstcoreexcelautomationaddin/ThisAddIn.vb#27)]

## <a name="see-also"></a>Siehe auch
- [Arbeiten mit Bereichen](../vsto/working-with-ranges.md)
- [Übersicht über Excel-Objektmodell](../vsto/excel-object-model-overview.md)
- [NamedRange-Steuerelement](../vsto/namedrange-control.md)
- [Vorgehensweise: Programmgesteuertes Verweisen Sie auf Arbeitsblattbereiche im code](../vsto/how-to-programmatically-refer-to-worksheet-ranges-in-code.md)
- [Vorgehensweise: Hinzufügen von NamedRange-Steuerelementen zu Arbeitsblättern](../vsto/how-to-add-namedrange-controls-to-worksheets.md)
- [Optionaler Parameter in Office-Projektmappen](../vsto/optional-parameters-in-office-solutions.md)
