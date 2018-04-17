---
title: 'Vorgehensweise: Programmgesteuertes Verweisen auf Arbeitsblattbereiche im Code | Microsoft Docs'
ms.custom: ''
ms.date: 02/02/2017
ms.technology:
- office-development
ms.topic: conceptual
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- ranges, referring to
- worksheets, referring to ranges
- referring to worksheet ranges
- Excel [Office development in Visual Studio], referring to worksheet ranges
author: TerryGLee
ms.author: tglee
manager: douge
ms.workload:
- office
ms.openlocfilehash: 68845904a349a94df6ee09c05ca262434b847bbc
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/16/2018
---
# <a name="how-to-programmatically-refer-to-worksheet-ranges-in-code"></a>Gewusst wie: Programmgesteuertes Verweisen auf Arbeitsblattbereiche im Code
  Sie verwenden ein ähnliches Verfahren zum Verweisen auf den Inhalt des ein <xref:Microsoft.Office.Tools.Excel.NamedRange> Steuerelement oder ein systemeigenes Excel-Range-Objekt.  
  
 [!INCLUDE[appliesto_xlalldocapp](../vsto/includes/appliesto-xlalldocapp-md.md)]  
  
## <a name="using-a-namedrange-control"></a>Verwenden ein NamedRange-Steuerelement  
 Im folgenden Beispiel wird eine <xref:Microsoft.Office.Tools.Excel.NamedRange> zu einem Arbeitsblatt und die Zelle im Bereich Text hinzugefügt.  
  
#### <a name="to-refer-to-a-namedrange-control"></a>Zum Verweisen auf ein NamedRange-Steuerelement  
  
1.  Weisen Sie eine Zeichenfolge, die die <xref:Microsoft.Office.Tools.Excel.NamedRange.Value2%2A> Eigenschaft von der <xref:Microsoft.Office.Tools.Excel.NamedRange> Steuerelement. Dieser Code muss in einer Sheet-Klasse platziert werden und nicht in der `ThisWorkbook` -Klasse.  
  
     [!code-csharp[Trin_VstcoreExcelAutomation#46](../vsto/codesnippet/CSharp/Trin_VstcoreExcelAutomationCS/Sheet1.cs#46)]
     [!code-vb[Trin_VstcoreExcelAutomation#46](../vsto/codesnippet/VisualBasic/Trin_VstcoreExcelAutomation/Sheet1.vb#46)]  
  
## <a name="using-native-excel-ranges"></a>Verwenden von systemeigenen Excel-Bereichen  
 Im folgenden Beispiel fügt einen systemeigenen Excel-Bereich zu einem Arbeitsblatt und die Zelle im Bereich Text hinzugefügt.  
  
#### <a name="to-refer-to-a-native-range-object"></a>Zum Verweisen auf ein systemeigenes Bereichsobjekt  
  
1.  Weisen Sie eine Zeichenfolge, die die <xref:Microsoft.Office.Interop.Excel.Range.Value2%2A> Eigenschaft des Bereichs.  
  
     [!code-csharp[Trin_VstcoreExcelAutomation#47](../vsto/codesnippet/CSharp/Trin_VstcoreExcelAutomationCS/Sheet1.cs#47)]
     [!code-vb[Trin_VstcoreExcelAutomation#47](../vsto/codesnippet/VisualBasic/Trin_VstcoreExcelAutomation/Sheet1.vb#47)]  
  
## <a name="see-also"></a>Siehe auch  
 [Arbeiten mit Bereichen](../vsto/working-with-ranges.md)   
 [Vorgehensweise: Programmgesteuertes Überprüfen der Rechtschreibung in Arbeitsblättern](../vsto/how-to-programmatically-check-spelling-in-worksheets.md)   
 [Vorgehensweise: Programmgesteuertes Anwenden von Formaten auf Bereiche in Arbeitsmappen](../vsto/how-to-programmatically-apply-styles-to-ranges-in-workbooks.md)   
 [Vorgehensweise: Programmgesteuertes Automatisches Füllen von Bereichen mit inkrementellen Daten](../vsto/how-to-programmatically-automatically-fill-ranges-with-incrementally-changing-data.md)   
 [Vorgehensweise: Programmgesteuertes Suchen nach Text in Arbeitsblattbereichen](../vsto/how-to-programmatically-search-for-text-in-worksheet-ranges.md)   
 [NamedRange-Steuerelement](../vsto/namedrange-control.md)   
 [Übersicht über Hostelemente und Hoststeuerelemente](../vsto/host-items-and-host-controls-overview.md)   
 [Programmgesteuerte Einschränkungen von Hostelementen und Hoststeuerelementen](../vsto/programmatic-limitations-of-host-items-and-host-controls.md)   
 [Optionale Parameter in Office-Projektmappen](../vsto/optional-parameters-in-office-solutions.md)  
  
  