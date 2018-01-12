---
title: 'Vorgehensweise: Programmgesteuertes speichern und Abrufen von Datumswerten in Excel-Bereichen | Microsoft Docs'
ms.custom: 
ms.date: 02/02/2017
ms.reviewer: 
ms.suite: 
ms.technology: office-development
ms.tgt_pltfrm: 
ms.topic: article
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
author: TerryGLee
ms.author: tglee
manager: ghogen
ms.workload: office
ms.openlocfilehash: 589079a593400549a69940fc42d1cf25fcab8826
ms.sourcegitcommit: f9fbf1f55f9ac14e4e5c6ae58c30dc1800ca6cda
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 01/10/2018
---
# <a name="how-to-programmatically-store-and-retrieve-date-values-in-excel-ranges"></a>Gewusst wie: Programmgesteuertes Speichern und Abrufen von Datumswerten in Excel-Bereichen
  Sie können das Speichern und Abrufen von Werten in einer <xref:Microsoft.Office.Tools.Excel.NamedRange> Steuerelement oder ein systemeigenes Excel-Range-Objekt.  
  
 [!INCLUDE[appliesto_xlalldocapp](../vsto/includes/appliesto-xlalldocapp-md.md)]  
  
 Wenn Sie einen Datumswert, der am oder nach dem 1/1/1900 in einem Bereich mit der Office-Entwicklungstools in Visual Studio liegt speichern, wird er in OLE Automation (OA)-Format gespeichert. Verwenden Sie die <xref:System.DateTime.FromOADate%2A> Methode zum Abrufen des Werts von Datumsangaben OLE Automation (OA). Wenn das Datum als 1/1/1900 liegt, wird er als Zeichenfolge gespeichert.  
  
> [!NOTE]  
>  Datumsangaben in Excel unterscheiden sich von OLE-Automatisierung Datumsangaben für die ersten zwei Monate des 1900. Es gibt auch Unterschiede Wenn die **1904-Datumswerte** Option aktiviert ist. In den folgenden Codebeispielen werden diese Unterschiede nicht behandelt.  
  
## <a name="using-a-namedrange-control"></a>Verwenden ein NamedRange-Steuerelement  
  
-   Dieses Beispiel gilt für Anpassungen auf Dokumentebene. Der folgende Code muss in einer Sheet-Klasse platziert werden, nicht in der `ThisWorkbook` Klasse.  
  
#### <a name="to-store-a-date-value-in-a-named-range"></a>Um einen Date-Wert in einen benannten Bereich speichern  
  
1.  Erstellen einer <xref:Microsoft.Office.Tools.Excel.NamedRange> -Steuerelement zur Zelle **A1**.  
  
     [!code-csharp[Trin_VstcoreExcelAutomation#50](../vsto/codesnippet/CSharp/Trin_VstcoreExcelAutomationCS/Sheet1.cs#50)]
     [!code-vb[Trin_VstcoreExcelAutomation#50](../vsto/codesnippet/VisualBasic/Trin_VstcoreExcelAutomation/Sheet1.vb#50)]  
  
2.  Festlegen des heutigen Datums als Wert für `NamedRange1`.  
  
     [!code-csharp[Trin_VstcoreExcelAutomation#51](../vsto/codesnippet/CSharp/Trin_VstcoreExcelAutomationCS/Sheet1.cs#51)]
     [!code-vb[Trin_VstcoreExcelAutomation#51](../vsto/codesnippet/VisualBasic/Trin_VstcoreExcelAutomation/Sheet1.vb#51)]  
  
#### <a name="to-retrieve-a-date-value-from-a-named-range"></a>Einen Date-Wert aus einem benannten Bereich abrufen  
  
1.  Abrufen der Date-Wert von `NamedRange1`.  
  
     [!code-csharp[Trin_VstcoreExcelAutomation#52](../vsto/codesnippet/CSharp/Trin_VstcoreExcelAutomationCS/Sheet1.cs#52)]
     [!code-vb[Trin_VstcoreExcelAutomation#52](../vsto/codesnippet/VisualBasic/Trin_VstcoreExcelAutomation/Sheet1.vb#52)]  
  
## <a name="using-native-excel-ranges"></a>Verwenden von systemeigenen Excel-Bereichen  
  
#### <a name="to-store-a-date-value-in-a-native-excel-range-object"></a>Zum Speichern eines Datumswerts in ein systemeigenes Excel-Range-Objekt  
  
1.  Erstellen einer <xref:Microsoft.Office.Interop.Excel.Range> , Zelle darstellt **A1**.  
  
     [!code-csharp[Trin_VstcoreExcelAutomationAddIn#25](../vsto/codesnippet/CSharp/trin_vstcoreexcelautomationaddin/ThisAddIn.cs#25)]
     [!code-vb[Trin_VstcoreExcelAutomationAddIn#25](../vsto/codesnippet/VisualBasic/trin_vstcoreexcelautomationaddin/ThisAddIn.vb#25)]  
  
2.  Festlegen des heutigen Datums als Wert für `rng`.  
  
     [!code-csharp[Trin_VstcoreExcelAutomationAddIn#26](../vsto/codesnippet/CSharp/trin_vstcoreexcelautomationaddin/ThisAddIn.cs#26)]
     [!code-vb[Trin_VstcoreExcelAutomationAddIn#26](../vsto/codesnippet/VisualBasic/trin_vstcoreexcelautomationaddin/ThisAddIn.vb#26)]  
  
#### <a name="to-retrieve-a-date-value-from-a-native-excel-range-object"></a>Zum Abrufen eines Datumswerts aus einem systemeigenen Excel-Range-Objekt  
  
1.  Abrufen der Date-Wert von `rng`.  
  
     [!code-csharp[Trin_VstcoreExcelAutomationAddIn#27](../vsto/codesnippet/CSharp/trin_vstcoreexcelautomationaddin/ThisAddIn.cs#27)]
     [!code-vb[Trin_VstcoreExcelAutomationAddIn#27](../vsto/codesnippet/VisualBasic/trin_vstcoreexcelautomationaddin/ThisAddIn.vb#27)]  
  
## <a name="see-also"></a>Siehe auch  
 [Arbeiten mit Bereichen](../vsto/working-with-ranges.md)   
 [Übersicht über das Excel-Objektmodell](../vsto/excel-object-model-overview.md)   
 [NamedRange-Steuerelement](../vsto/namedrange-control.md)   
 [Vorgehensweise: Programmgesteuertes Verweisen auf Arbeitsblattbereiche im Code](../vsto/how-to-programmatically-refer-to-worksheet-ranges-in-code.md)   
 [Vorgehensweise: Hinzufügen von NamedRange-Steuerelementen zu Arbeitsblättern](../vsto/how-to-add-namedrange-controls-to-worksheets.md)   
 [Optionale Parameter in Office-Projektmappen](../vsto/optional-parameters-in-office-solutions.md)  
  
  