---
title: 'Gewusst wie: Programmgesteuertes Verweisen auf Arbeitsblattbereiche im Code'
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
ms.openlocfilehash: 608ce006ccc34330631da8d4c947405b027f1a1f
ms.sourcegitcommit: 6944ceb7193d410a2a913ecee6f40c6e87e8a54b
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 09/06/2018
ms.locfileid: "35672784"
---
# <a name="how-to-programmatically-refer-to-worksheet-ranges-in-code"></a>Gewusst wie: Programmgesteuertes Verweisen auf Arbeitsblattbereiche im Code
  Verwenden Sie einen ähnlichen Prozess, um auf den Inhalt der verweisen eine <xref:Microsoft.Office.Tools.Excel.NamedRange> Steuerelement oder ein systemeigenes Excel-Bereich-Objekt.  
  
 [!INCLUDE[appliesto_xlalldocapp](../vsto/includes/appliesto-xlalldocapp-md.md)]  
  
## <a name="use-a-namedrange-control"></a>Verwenden Sie ein NamedRange-Steuerelement  
 Im folgenden Beispiel wird eine <xref:Microsoft.Office.Tools.Excel.NamedRange> zu einem Arbeitsblatt und fügt Sie dann auf die Zelle im Bereich Text.  
  
### <a name="to-refer-to-a-namedrange-control"></a>Zum Verweisen auf ein NamedRange-Steuerelement  
  
1.  Weisen Sie eine Zeichenfolge, die die <xref:Microsoft.Office.Tools.Excel.NamedRange.Value2%2A> Eigenschaft der <xref:Microsoft.Office.Tools.Excel.NamedRange> Steuerelement. Dieser Code muss in einer Sheet-Klasse platziert werden und nicht in der `ThisWorkbook` -Klasse.  
  
     [!code-csharp[Trin_VstcoreExcelAutomation#46](../vsto/codesnippet/CSharp/Trin_VstcoreExcelAutomationCS/Sheet1.cs#46)]
     [!code-vb[Trin_VstcoreExcelAutomation#46](../vsto/codesnippet/VisualBasic/Trin_VstcoreExcelAutomation/Sheet1.vb#46)]  
  
## <a name="use-native-excel-ranges"></a>Verwenden Sie systemeigene Excel-Bereiche  
 Im folgenden Beispiel fügt einen systemeigenen Excel-Bereich zu einem Arbeitsblatt und dann die Zelle im Bereich von Text hinzugefügt.  
  
### <a name="to-refer-to-a-native-range-object"></a>Zum Verweisen auf einem systemeigenen Bereich-Objekt  
  
1.  Weisen Sie eine Zeichenfolge, die die <xref:Microsoft.Office.Interop.Excel.Range.Value2%2A> -Eigenschaft des Bereichs.  
  
     [!code-csharp[Trin_VstcoreExcelAutomation#47](../vsto/codesnippet/CSharp/Trin_VstcoreExcelAutomationCS/Sheet1.cs#47)]
     [!code-vb[Trin_VstcoreExcelAutomation#47](../vsto/codesnippet/VisualBasic/Trin_VstcoreExcelAutomation/Sheet1.vb#47)]  
  
## <a name="see-also"></a>Siehe auch  
 [Arbeiten mit Bereichen](../vsto/working-with-ranges.md)   
 [Gewusst wie: Programmgesteuertes Überprüfen der Rechtschreibung in Arbeitsblättern](../vsto/how-to-programmatically-check-spelling-in-worksheets.md)   
 [Gewusst wie: Programmgesteuertes Anwenden von Formaten auf Bereiche in Arbeitsmappen](../vsto/how-to-programmatically-apply-styles-to-ranges-in-workbooks.md)   
 [Gewusst wie: Programmgesteuertes Automatisches Füllen von Bereichen mit inkrementellen Daten](../vsto/how-to-programmatically-automatically-fill-ranges-with-incrementally-changing-data.md)   
 [Gewusst wie: Programmgesteuertes Suchen nach Text in Arbeitsblattbereichen](../vsto/how-to-programmatically-search-for-text-in-worksheet-ranges.md)   
 [NamedRange-Steuerelement](../vsto/namedrange-control.md)   
 [Hostelemente und Host-Steuerelementen (Übersicht)](../vsto/host-items-and-host-controls-overview.md)   
 [Einschränkungen für programmgesteuerte Aufgaben von Hostelementen und Hoststeuerelementen](../vsto/programmatic-limitations-of-host-items-and-host-controls.md)   
 [Optionaler Parameter in Office-Projektmappen](../vsto/optional-parameters-in-office-solutions.md)  
  
  