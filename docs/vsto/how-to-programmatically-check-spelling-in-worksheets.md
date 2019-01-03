---
title: 'Vorgehensweise: Programmgesteuertes Überprüfen der Rechtschreibung in Arbeitsblättern'
ms.date: 02/02/2017
ms.topic: conceptual
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- spellchecking
- spelling checker, worksheets
- worksheets, checking spelling
- spelling, checking in worksheets
author: TerryGLee
ms.author: tglee
manager: douge
ms.workload:
- office
ms.openlocfilehash: ea589f30c026ddf946cb43811818b54d3df9b2e2
ms.sourcegitcommit: 37fb7075b0a65d2add3b137a5230767aa3266c74
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 01/02/2019
ms.locfileid: "53899969"
---
# <a name="how-to-programmatically-check-spelling-in-worksheets"></a>Vorgehensweise: Programmgesteuertes Überprüfen der Rechtschreibung in Arbeitsblättern
  Sie können die Rechtschreibung von Wörtern in einem Arbeitsblatt programmgesteuert überprüfen. Das Dialogfeld **Rechtschreibung** wird automatisch angezeigt wird, wenn das Arbeitsblatt falsch geschriebene Wörter enthält.  
  
 [!INCLUDE[appliesto_xlalldocapp](../vsto/includes/appliesto-xlalldocapp-md.md)]  
  
## <a name="to-check-spelling-in-a-worksheet-in-a-document-level-customization"></a>So führen Sie die Rechtschreibprüfung in einer Anpassung auf Dokumentebene aus  
  
1.  Rufen Sie die <xref:Microsoft.Office.Tools.Excel.Worksheet.CheckSpelling%2A> -Methode des Arbeitsblatts auf.  
  
     [!code-csharp[Trin_VstcoreExcelAutomation#45](../vsto/codesnippet/CSharp/Trin_VstcoreExcelAutomationCS/Sheet1.cs#45)]
     [!code-vb[Trin_VstcoreExcelAutomation#45](../vsto/codesnippet/VisualBasic/Trin_VstcoreExcelAutomation/Sheet1.vb#45)]  
  
## <a name="to-check-spelling-in-a-worksheet-in-a-vsto-add-in"></a>Für die Rechtschreibprüfung in einem Arbeitsblatt in einem VSTO-Add-in  
  
1.  Rufen Sie die <xref:Microsoft.Office.Interop.Excel._Worksheet.CheckSpelling%2A> -Methode des aktiven Arbeitsblatts auf.  
  
     [!code-csharp[Trin_VstcoreExcelAutomationAddIn#22](../vsto/codesnippet/CSharp/trin_vstcoreexcelautomationaddin/ThisAddIn.cs#22)]
     [!code-vb[Trin_VstcoreExcelAutomationAddIn#22](../vsto/codesnippet/VisualBasic/trin_vstcoreexcelautomationaddin/ThisAddIn.vb#22)]  
  
## <a name="see-also"></a>Siehe auch  
 [Arbeiten mit Arbeitsblättern](../vsto/working-with-worksheets.md)   
 [Vorgehensweise: Programmgesteuertes Ausführen von Excel-Berechnungen](../vsto/how-to-programmatically-run-excel-calculations-programmatically.md)   
 [NamedRange-Steuerelement](../vsto/namedrange-control.md)   
 [Optionaler Parameter in Office-Projektmappen](../vsto/optional-parameters-in-office-solutions.md)  
