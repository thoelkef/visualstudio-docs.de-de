---
title: 'Vorgehensweise: Programmgesteuertes suchen Sie nach Text in Arbeitsblattbereichen'
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
ms.openlocfilehash: 37f59f2888fc5a572029f4c21116281df008706e
ms.sourcegitcommit: c0202a77d4dc562cdc55dc2e6223c062281d9749
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 01/24/2019
ms.locfileid: "54868588"
---
# <a name="how-to-programmatically-search-for-text-in-worksheet-ranges"></a>Vorgehensweise: Programmgesteuertes suchen Sie nach Text in Arbeitsblattbereichen
  Die <xref:Microsoft.Office.Interop.Excel.Range.Find%2A> Methode der <xref:Microsoft.Office.Interop.Excel.Range> -Objekt ermöglicht es Ihnen, um nach Text innerhalb des Bereichs zu suchen. Dieser Text kann auch sein, eine der Fehlerzeichenfolgen, die in einer Arbeitsblattzelle, wie z. B. auftreten können `#NULL!` oder `#VALUE!`. Weitere Informationen zu den Fehlerzeichenfolgen finden Sie unter [Zelle Fehlerwerte](/office/vba/excel/Concepts/Cells-and-Ranges/cell-error-values).  
  
 [!INCLUDE[appliesto_xlalldocapp](../vsto/includes/appliesto-xlalldocapp-md.md)]  
  
 Im folgende Beispiel durchsucht einen Bereich, der mit dem Namen `Fruits` und ändert die Schriftart für die Zellen, die das Wort "Apples" enthalten. Dieses Verfahren verwendet auch die <xref:Microsoft.Office.Interop.Excel.Range.FindNext%2A> Methode, die die zuvor festgelegten verwendet Suchen Sie die Einstellungen für die Suche wiederholen. Sie geben die Zelle nach der gesucht werden soll, und die <xref:Microsoft.Office.Interop.Excel.Range.FindNext%2A> -Methode übernimmt den Rest.  
  
> [!NOTE]  
>  Die <xref:Microsoft.Office.Interop.Excel.Range.FindNext%2A> Methode Suche zurück zum Anfang des Suchbereichs umschließt, das Ende des Bereichs erreicht wurde. Ihr Code muss stellen Sie sicher, dass die Suche in einer Endlosschleife nicht um umbrochen wird. Die Beispielprozedur zeigt eine Möglichkeit, mithilfe der <xref:Microsoft.Office.Interop.Excel.Range.Address%2A> Eigenschaft.  
  
 ![Link zum Video](../vsto/media/playvideo.gif "Link zum Video") eine entsprechende Videodemo finden Sie unter [Gewusst wie: Verwenden die Find-Methode in einem Excel-Add-in? ](http://go.microsoft.com/fwlink/?LinkID=130294).  
  
## <a name="to-search-for-text-in-a-worksheet-range"></a>Zum Suchen nach Text in einem Arbeitsblattbereich  
  
1. Deklarieren Sie Variablen für die nachverfolgung der gesamte Bereich, den ersten gefundenen Bereich und aktuellen Bereich gefunden.  
  
    [!code-csharp[Trin_VstcoreExcelAutomation#58](../vsto/codesnippet/CSharp/Trin_VstcoreExcelAutomationCS/Sheet1.cs#58)]
    [!code-vb[Trin_VstcoreExcelAutomation#58](../vsto/codesnippet/VisualBasic/Trin_VstcoreExcelAutomation/Sheet1.vb#58)]  
  
2. Suchen Sie nach Angabe aller Parameter mit Ausnahme der Zelle, suchen Sie nach der die erste Übereinstimmung.  
  
    [!code-csharp[Trin_VstcoreExcelAutomation#59](../vsto/codesnippet/CSharp/Trin_VstcoreExcelAutomationCS/Sheet1.cs#59)]
    [!code-vb[Trin_VstcoreExcelAutomation#59](../vsto/codesnippet/VisualBasic/Trin_VstcoreExcelAutomation/Sheet1.vb#59)]  
  
3. Fortsetzen Sie, suchen als Übereinstimmungen vorhanden sind.  
  
    [!code-csharp[Trin_VstcoreExcelAutomation#60](../vsto/codesnippet/CSharp/Trin_VstcoreExcelAutomationCS/Sheet1.cs#60)]
    [!code-vb[Trin_VstcoreExcelAutomation#60](../vsto/codesnippet/VisualBasic/Trin_VstcoreExcelAutomation/Sheet1.vb#60)]  
  
4. Vergleichen der ersten gefundenen Bereich (`firstFind`) zu **nichts**. Wenn `firstFind` enthält keinen Wert, den Code gespeichert, das den gefundenen Bereich (`currentFind`).  
  
    [!code-csharp[Trin_VstcoreExcelAutomation#61](../vsto/codesnippet/CSharp/Trin_VstcoreExcelAutomationCS/Sheet1.cs#61)]
    [!code-vb[Trin_VstcoreExcelAutomation#61](../vsto/codesnippet/VisualBasic/Trin_VstcoreExcelAutomation/Sheet1.vb#61)]  
  
5. Beenden Sie die Schleife aus, wenn die Adresse des Bereichs gefunden, die Adresse des ersten gefundenen Bereichs entspricht.  
  
    [!code-csharp[Trin_VstcoreExcelAutomation#62](../vsto/codesnippet/CSharp/Trin_VstcoreExcelAutomationCS/Sheet1.cs#62)]
    [!code-vb[Trin_VstcoreExcelAutomation#62](../vsto/codesnippet/VisualBasic/Trin_VstcoreExcelAutomation/Sheet1.vb#62)]  
  
6. Legen Sie die Darstellung des Bereichs gefunden.  
  
    [!code-csharp[Trin_VstcoreExcelAutomation#63](../vsto/codesnippet/CSharp/Trin_VstcoreExcelAutomationCS/Sheet1.cs#63)]
    [!code-vb[Trin_VstcoreExcelAutomation#63](../vsto/codesnippet/VisualBasic/Trin_VstcoreExcelAutomation/Sheet1.vb#63)]  
  
7. Durchführen Sie eine neue Suche.  
  
    [!code-csharp[Trin_VstcoreExcelAutomation#64](../vsto/codesnippet/CSharp/Trin_VstcoreExcelAutomationCS/Sheet1.cs#64)]
    [!code-vb[Trin_VstcoreExcelAutomation#64](../vsto/codesnippet/VisualBasic/Trin_VstcoreExcelAutomation/Sheet1.vb#64)]  
  
   Das folgende Beispiel zeigt die vollständige Methode.  
  
## <a name="example"></a>Beispiel  
 [!code-csharp[Trin_VstcoreExcelAutomation#57](../vsto/codesnippet/CSharp/Trin_VstcoreExcelAutomationCS/Sheet1.cs#57)]
 [!code-vb[Trin_VstcoreExcelAutomation#57](../vsto/codesnippet/VisualBasic/Trin_VstcoreExcelAutomation/Sheet1.vb#57)]  
  
## <a name="see-also"></a>Siehe auch  
 [Arbeiten mit Bereichen](../vsto/working-with-ranges.md)   
 [Vorgehensweise: Programmgesteuertes Anwenden von Formaten auf Bereiche in Arbeitsmappen](../vsto/how-to-programmatically-apply-styles-to-ranges-in-workbooks.md)   
 [Vorgehensweise: Programmgesteuertes Verweisen Sie auf Arbeitsblattbereiche im code](../vsto/how-to-programmatically-refer-to-worksheet-ranges-in-code.md)   
 [Optionaler Parameter in Office-Projektmappen](../vsto/optional-parameters-in-office-solutions.md)  
