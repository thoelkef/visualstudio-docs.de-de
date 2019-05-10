---
title: 'Vorgehensweise: Programmgesteuertes Verweisen Sie auf Arbeitsblattbereiche im code'
ms.date: 02/02/2017
ms.topic: conceptual
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- ranges, referring to
- worksheets, referring to ranges
- referring to worksheet ranges
- Excel [Office development in Visual Studio], referring to worksheet ranges
author: John-Hart
ms.author: johnhart
manager: jillfra
ms.workload:
- office
ms.openlocfilehash: 2e82b884965c5c7362951c7d94199f90c93fbfc3
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/23/2019
ms.locfileid: "62955957"
---
# <a name="how-to-programmatically-refer-to-worksheet-ranges-in-code"></a>Vorgehensweise: Programmgesteuertes Verweisen Sie auf Arbeitsblattbereiche im code
  Verwenden Sie einen ähnlichen Prozess, um auf den Inhalt der verweisen eine <xref:Microsoft.Office.Tools.Excel.NamedRange> Steuerelement oder ein systemeigenes Excel-Bereich-Objekt.

 [!INCLUDE[appliesto_xlalldocapp](../vsto/includes/appliesto-xlalldocapp-md.md)]

## <a name="use-a-namedrange-control"></a>Verwenden Sie ein NamedRange-Steuerelement
 Im folgenden Beispiel wird eine <xref:Microsoft.Office.Tools.Excel.NamedRange> zu einem Arbeitsblatt und fügt Sie dann auf die Zelle im Bereich Text.

### <a name="to-refer-to-a-namedrange-control"></a>Zum Verweisen auf ein NamedRange-Steuerelement

1. Weisen Sie eine Zeichenfolge, die die <xref:Microsoft.Office.Tools.Excel.NamedRange.Value2%2A> Eigenschaft der <xref:Microsoft.Office.Tools.Excel.NamedRange> Steuerelement. Dieser Code muss in einer Sheet-Klasse platziert werden und nicht in der `ThisWorkbook` -Klasse.

     [!code-csharp[Trin_VstcoreExcelAutomation#46](../vsto/codesnippet/CSharp/Trin_VstcoreExcelAutomationCS/Sheet1.cs#46)]
     [!code-vb[Trin_VstcoreExcelAutomation#46](../vsto/codesnippet/VisualBasic/Trin_VstcoreExcelAutomation/Sheet1.vb#46)]

## <a name="use-native-excel-ranges"></a>Verwenden Sie systemeigene Excel-Bereiche
 Im folgenden Beispiel fügt einen systemeigenen Excel-Bereich zu einem Arbeitsblatt und dann die Zelle im Bereich von Text hinzugefügt.

### <a name="to-refer-to-a-native-range-object"></a>Zum Verweisen auf einem systemeigenen Bereich-Objekt

1. Weisen Sie eine Zeichenfolge, die die <xref:Microsoft.Office.Interop.Excel.Range.Value2%2A> -Eigenschaft des Bereichs.

     [!code-csharp[Trin_VstcoreExcelAutomation#47](../vsto/codesnippet/CSharp/Trin_VstcoreExcelAutomationCS/Sheet1.cs#47)]
     [!code-vb[Trin_VstcoreExcelAutomation#47](../vsto/codesnippet/VisualBasic/Trin_VstcoreExcelAutomation/Sheet1.vb#47)]

## <a name="see-also"></a>Siehe auch
- [Arbeiten mit Bereichen](../vsto/working-with-ranges.md)
- [Vorgehensweise: Programmgesteuertes Überprüfen der Rechtschreibung in Arbeitsblättern](../vsto/how-to-programmatically-check-spelling-in-worksheets.md)
- [Vorgehensweise: Programmgesteuertes Anwenden von Formaten auf Bereiche in Arbeitsmappen](../vsto/how-to-programmatically-apply-styles-to-ranges-in-workbooks.md)
- [Vorgehensweise: Programmgesteuertes Automatisches Füllen von Bereichen mit inkrementellen Daten](../vsto/how-to-programmatically-automatically-fill-ranges-with-incrementally-changing-data.md)
- [Vorgehensweise: Programmgesteuertes suchen Sie nach Text in Arbeitsblattbereichen](../vsto/how-to-programmatically-search-for-text-in-worksheet-ranges.md)
- [NamedRange-Steuerelement](../vsto/namedrange-control.md)
- [Hostelemente und Host-Steuerelementen (Übersicht)](../vsto/host-items-and-host-controls-overview.md)
- [Einschränkungen für programmgesteuerte Aufgaben von Hostelementen und Hoststeuerelementen](../vsto/programmatic-limitations-of-host-items-and-host-controls.md)
- [Optionaler Parameter in Office-Projektmappen](../vsto/optional-parameters-in-office-solutions.md)
