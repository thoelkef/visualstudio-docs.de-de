---
title: 'Gewusst wie: Programm gesteuertes suchen nach Text in Arbeitsblatt Bereichen'
ms.date: 02/02/2017
ms.topic: conceptual
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- worksheets, searching
- text [Office development in Visual Studio], searching in worksheets
- text searches, worksheets
author: John-Hart
ms.author: johnhart
manager: jillfra
ms.workload:
- office
ms.openlocfilehash: 0ffc06c2f50f7a304ef76ac1451ee47419143afb
ms.sourcegitcommit: dcbb876a5dd598f2538e62e1eabd4dc98595b53a
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 10/28/2019
ms.locfileid: "72985819"
---
# <a name="how-to-programmatically-search-for-text-in-worksheet-ranges"></a>Gewusst wie: Programm gesteuertes suchen nach Text in Arbeitsblatt Bereichen
  Mit der <xref:Microsoft.Office.Interop.Excel.Range.Find%2A>-Methode des <xref:Microsoft.Office.Interop.Excel.Range>-Objekts können Sie innerhalb des Bereichs nach Text suchen. Dieser Text kann auch eine beliebige Fehler Zeichenfolge sein, die in einer Arbeitsblatt Zelle angezeigt werden kann, z. b. `#NULL!` oder `#VALUE!`. Weitere Informationen zu Fehler Zeichenfolgen finden Sie unter [Zellen Fehler Werte](/office/vba/excel/Concepts/Cells-and-Ranges/cell-error-values).

 [!INCLUDE[appliesto_xlalldocapp](../vsto/includes/appliesto-xlalldocapp-md.md)]

 Im folgenden Beispiel wird ein Bereich mit dem Namen `Fruits` durchsucht und die Schriftart für Zellen, die das Wort "Äpfel" enthalten, geändert. Dieses Verfahren verwendet auch die <xref:Microsoft.Office.Interop.Excel.Range.FindNext%2A>-Methode, die die zuvor festgelegten Sucheinstellungen verwendet, um die Suche zu wiederholen. Sie geben die Zelle an, nach der gesucht werden soll, und die <xref:Microsoft.Office.Interop.Excel.Range.FindNext%2A> Methode verarbeitet den Rest.

> [!NOTE]
> Die Suche der <xref:Microsoft.Office.Interop.Excel.Range.FindNext%2A> Methode kehrt zum Anfang des Suchbereichs zurück, nachdem das Ende des Bereichs erreicht wurde. Der Code muss sicherstellen, dass die Suche in einer Endlosschleife nicht umbrochen wird. Die Beispiel Prozedur zeigt eine Möglichkeit, dies mit der <xref:Microsoft.Office.Interop.Excel.Range.Address%2A>-Eigenschaft zu verarbeiten.

## <a name="to-search-for-text-in-a-worksheet-range"></a>So suchen Sie nach Text in einem Arbeitsblatt Bereich

1. Deklarieren Sie Variablen für die Nachverfolgung des gesamten Bereichs, den ersten gefundenen Bereich und den aktuellen gefundenen Bereich.

    [!code-csharp[Trin_VstcoreExcelAutomation#58](../vsto/codesnippet/CSharp/Trin_VstcoreExcelAutomationCS/Sheet1.cs#58)]
    [!code-vb[Trin_VstcoreExcelAutomation#58](../vsto/codesnippet/VisualBasic/Trin_VstcoreExcelAutomation/Sheet1.vb#58)]

2. Suchen Sie nach der ersten Entsprechung, und geben Sie alle Parameter Außer der Zelle an, nach der gesucht werden soll.

    [!code-csharp[Trin_VstcoreExcelAutomation#59](../vsto/codesnippet/CSharp/Trin_VstcoreExcelAutomationCS/Sheet1.cs#59)]
    [!code-vb[Trin_VstcoreExcelAutomation#59](../vsto/codesnippet/VisualBasic/Trin_VstcoreExcelAutomation/Sheet1.vb#59)]

3. Die Suche wird fortgesetzt, solange Übereinstimmungen vorhanden sind.

    [!code-csharp[Trin_VstcoreExcelAutomation#60](../vsto/codesnippet/CSharp/Trin_VstcoreExcelAutomationCS/Sheet1.cs#60)]
    [!code-vb[Trin_VstcoreExcelAutomation#60](../vsto/codesnippet/VisualBasic/Trin_VstcoreExcelAutomation/Sheet1.vb#60)]

4. Vergleicht den ersten gefundenen Bereich (`firstFind`) mit " **Nothing**". Wenn `firstFind` keinen Wert enthält, speichert der Code den gefundenen Bereich (`currentFind`).

    [!code-csharp[Trin_VstcoreExcelAutomation#61](../vsto/codesnippet/CSharp/Trin_VstcoreExcelAutomationCS/Sheet1.cs#61)]
    [!code-vb[Trin_VstcoreExcelAutomation#61](../vsto/codesnippet/VisualBasic/Trin_VstcoreExcelAutomation/Sheet1.vb#61)]

5. Beenden Sie die Schleife, wenn die Adresse des gefundenen Bereichs mit der Adresse des ersten gefundenen Bereichs übereinstimmt.

    [!code-csharp[Trin_VstcoreExcelAutomation#62](../vsto/codesnippet/CSharp/Trin_VstcoreExcelAutomationCS/Sheet1.cs#62)]
    [!code-vb[Trin_VstcoreExcelAutomation#62](../vsto/codesnippet/VisualBasic/Trin_VstcoreExcelAutomation/Sheet1.vb#62)]

6. Legen Sie die Darstellung des gefundenen Bereichs fest.

    [!code-csharp[Trin_VstcoreExcelAutomation#63](../vsto/codesnippet/CSharp/Trin_VstcoreExcelAutomationCS/Sheet1.cs#63)]
    [!code-vb[Trin_VstcoreExcelAutomation#63](../vsto/codesnippet/VisualBasic/Trin_VstcoreExcelAutomation/Sheet1.vb#63)]

7. Führen Sie eine weitere Suche aus.

    [!code-csharp[Trin_VstcoreExcelAutomation#64](../vsto/codesnippet/CSharp/Trin_VstcoreExcelAutomationCS/Sheet1.cs#64)]
    [!code-vb[Trin_VstcoreExcelAutomation#64](../vsto/codesnippet/VisualBasic/Trin_VstcoreExcelAutomation/Sheet1.vb#64)]

   Das folgende Beispiel zeigt die vollständige Methode.

## <a name="example"></a>Beispiel
 [!code-csharp[Trin_VstcoreExcelAutomation#57](../vsto/codesnippet/CSharp/Trin_VstcoreExcelAutomationCS/Sheet1.cs#57)]
 [!code-vb[Trin_VstcoreExcelAutomation#57](../vsto/codesnippet/VisualBasic/Trin_VstcoreExcelAutomation/Sheet1.vb#57)]

## <a name="see-also"></a>Siehe auch
- [Arbeiten mit Bereichen](../vsto/working-with-ranges.md)
- [Gewusst wie: Programm gesteuertes Anwenden von Formaten auf Bereiche in Arbeitsmappen](../vsto/how-to-programmatically-apply-styles-to-ranges-in-workbooks.md)
- [Gewusst wie: Programm gesteuertes verweisen auf Arbeitsblatt Bereiche im Code](../vsto/how-to-programmatically-refer-to-worksheet-ranges-in-code.md)
- [Optionale Parameter in Office-Projektmappen](../vsto/optional-parameters-in-office-solutions.md)
