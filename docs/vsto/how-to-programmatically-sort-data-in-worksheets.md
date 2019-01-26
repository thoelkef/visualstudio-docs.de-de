---
title: 'Vorgehensweise: Programmgesteuertes Sortieren von Daten in Arbeitsblättern'
ms.date: 02/02/2017
ms.topic: conceptual
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- data sorting, worksheets
- data [Office development in Visual Studio], sorting in worksheets
- worksheets, sorting data
- sorting data, in worksheets
author: John-Hart
ms.author: johnhart
manager: jillfra
ms.workload:
- office
ms.openlocfilehash: 10280b9d95892ceb8cb0445a46f1cfd51ea49f48
ms.sourcegitcommit: c0202a77d4dc562cdc55dc2e6223c062281d9749
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 01/24/2019
ms.locfileid: "54870505"
---
# <a name="how-to-programmatically-sort-data-in-worksheets"></a>Vorgehensweise: Programmgesteuertes Sortieren von Daten in Arbeitsblättern
  Sie können Daten sortieren, die zur Laufzeit in Arbeitsblattbereichen und -listen enthalten sind. Der folgende Code sortiert einen mehrspaltigen Bereich namens `Fruits` nach den Daten in der ersten Spalte und anschließend nach den Daten in der zweiten Spalte.  
  
 [!INCLUDE[appliesto_xlalldocapp](../vsto/includes/appliesto-xlalldocapp-md.md)]  
  
## <a name="sort-data-in-a-document-level-customization"></a>Sortieren von Daten in einer Anpassung auf Dokumentebene  
  
### <a name="to-sort-data-in-a-namedrange-control"></a>So sortieren Sie Daten in einem NamedRange-Steuerelement  
  
1. Rufen Sie die <xref:Microsoft.Office.Tools.Excel.NamedRange.Sort%2A>-Methode des <xref:Microsoft.Office.Tools.Excel.NamedRange>-Steuerelements auf. Das folgende Beispiel erfordert ein <xref:Microsoft.Office.Tools.Excel.NamedRange>-Steuerelement namens `Fruits` in einem Arbeitsblatt. Dieser Code muss in einer Sheet-Klasse platziert werden und nicht in der `ThisWorkbook` -Klasse.  
  
    [!code-csharp[Trin_VstcoreExcelAutomation#78](../vsto/codesnippet/CSharp/Trin_VstcoreExcelAutomationCS/Sheet1.cs#78)]
    [!code-vb[Trin_VstcoreExcelAutomation#78](../vsto/codesnippet/VisualBasic/Trin_VstcoreExcelAutomation/Sheet1.vb#78)]  
  
   Platzieren Sie den folgenden Code in *Sheet1.vb* oder *Sheet1.cs* zum Sortieren von Daten in einem <xref:Microsoft.Office.Tools.Excel.ListObject> Steuerelement. Der Code setzt voraus, dass Sie über ein <xref:Microsoft.Office.Tools.Excel.ListObject>-Steuerelement namens `fruitList`in einem Arbeitsblatt namens `Sheet1` verfügen.  
  
### <a name="to-sort-data-in-a-listobject-control"></a>So sortieren Sie Daten in einem ListObject-Steuerelement  
  
1.  Rufen Sie die <xref:Microsoft.Office.Interop.Excel.Range.Sort%2A>-Methode der <xref:Microsoft.Office.Tools.Excel.ListObject.Range%2A>-Eigenschaft des <xref:Microsoft.Office.Tools.Excel.ListObject>-Hoststeuerelements auf.  
  
     [!code-csharp[Trin_VstcoreExcelAutomation#79](../vsto/codesnippet/CSharp/Trin_VstcoreExcelAutomationCS/Sheet1.cs#79)]
     [!code-vb[Trin_VstcoreExcelAutomation#79](../vsto/codesnippet/VisualBasic/Trin_VstcoreExcelAutomation/Sheet1.vb#79)]  
  
## <a name="sort-data-in-a-vsto-add-in"></a>Sortieren von Daten in einem VSTO-Add-in  
  
### <a name="to-sort-data-in-a-native-range"></a>So sortieren Sie Daten in einem systemeigenen Bereich  
  
1.  Rufen Sie die <xref:Microsoft.Office.Interop.Excel.Range.Sort%2A>-Methode des systemeigenen Excel-<xref:Microsoft.Office.Interop.Excel.Range>-Steuerelements auf. Das folgende Beispiel erfordert ein systemeigenes Excel-Steuerelement namens `Fruits` in einem Arbeitsblatt.  
  
     [!code-csharp[Trin_VstcoreExcelAutomationAddIn#23](../vsto/codesnippet/CSharp/trin_vstcoreexcelautomationaddin/ThisAddIn.cs#23)]
     [!code-vb[Trin_VstcoreExcelAutomationAddIn#23](../vsto/codesnippet/VisualBasic/trin_vstcoreexcelautomationaddin/ThisAddIn.vb#23)]  
  
### <a name="to-sort-data-in-a-listobject-control"></a>So sortieren Sie Daten in einem ListObject-Steuerelement  
  
1.  Rufen Sie die <xref:Microsoft.Office.Interop.Excel.Range.Sort%2A>-Methode der <xref:Microsoft.Office.Tools.Excel.ListObject.Range%2A>-Eigenschaft des systemeigenen Excel-<xref:Microsoft.Office.Interop.Excel.ListObject>-Steuerelements auf. Im folgenden Beispiel wird vorausgesetzt, dass Sie über ein systemeigenes Excel-<xref:Microsoft.Office.Interop.Excel.ListObject>-Steuerelement namens `fruitList` im aktiven Arbeitsblatt verfügen.  
  
     [!code-csharp[Trin_VstcoreExcelAutomationAddIn#24](../vsto/codesnippet/CSharp/trin_vstcoreexcelautomationaddin/ThisAddIn.cs#24)]
     [!code-vb[Trin_VstcoreExcelAutomationAddIn#24](../vsto/codesnippet/VisualBasic/trin_vstcoreexcelautomationaddin/ThisAddIn.vb#24)]  
  
## <a name="see-also"></a>Siehe auch  
 [Arbeiten mit Arbeitsblättern](../vsto/working-with-worksheets.md)   
 [Vorgehensweise: Programmgesteuertes Automatisches Füllen von Bereichen mit inkrementellen Daten](../vsto/how-to-programmatically-automatically-fill-ranges-with-incrementally-changing-data.md)   
 [Vorgehensweise: Programmgesteuertes Verweisen Sie auf Arbeitsblattbereiche im code](../vsto/how-to-programmatically-refer-to-worksheet-ranges-in-code.md)   
 [Vorgehensweise: Programmgesteuertes Anwenden von Formaten auf Bereiche in Arbeitsmappen](../vsto/how-to-programmatically-apply-styles-to-ranges-in-workbooks.md)   
 [NamedRange-Steuerelement](../vsto/namedrange-control.md)   
 [ListObject-Steuerelement](../vsto/listobject-control.md)   
 [Optionaler Parameter in Office-Projektmappen](../vsto/optional-parameters-in-office-solutions.md)  
