---
title: "Vorgehensweise: Programmgesteuertes Überprüfen der Rechtschreibung in Arbeitsblättern | Microsoft Docs"
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
- spellchecking
- spelling checker, worksheets
- worksheets, checking spelling
- spelling, checking in worksheets
ms.assetid: 16367c5d-2075-4174-bb87-dfc59f02c84c
caps.latest.revision: "53"
author: gewarren
ms.author: gewarren
manager: ghogen
ms.workload: office
ms.openlocfilehash: 96527061e6cd738cbfc6a1aee53ea598f238aebd
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 12/22/2017
---
# <a name="how-to-programmatically-check-spelling-in-worksheets"></a>Gewusst wie: Programmgesteuertes Überprüfen der Rechtschreibung in Arbeitsblättern
  Sie können die Rechtschreibung von Wörtern in einem Arbeitsblatt programmgesteuert überprüfen. Das Dialogfeld **Rechtschreibung** wird automatisch angezeigt wird, wenn das Arbeitsblatt falsch geschriebene Wörter enthält.  
  
 [!INCLUDE[appliesto_xlalldocapp](../vsto/includes/appliesto-xlalldocapp-md.md)]  
  
### <a name="to-check-spelling-in-a-worksheet-in-a-document-level-customization"></a>So führen Sie die Rechtschreibprüfung in einer Anpassung auf Dokumentebene aus  
  
1.  Rufen Sie die <xref:Microsoft.Office.Tools.Excel.Worksheet.CheckSpelling%2A> -Methode des Arbeitsblatts auf.  
  
     [!code-csharp[Trin_VstcoreExcelAutomation#45](../vsto/codesnippet/CSharp/Trin_VstcoreExcelAutomationCS/Sheet1.cs#45)]
     [!code-vb[Trin_VstcoreExcelAutomation#45](../vsto/codesnippet/VisualBasic/Trin_VstcoreExcelAutomation/Sheet1.vb#45)]  
  
### <a name="to-check-spelling-in-a-worksheet-in-an-vsto-add-in"></a>So führen Sie die Rechtschreibprüfung in einem Arbeitsblatt in einem VSTO-Add-In aus  
  
1.  Rufen Sie die <xref:Microsoft.Office.Interop.Excel._Worksheet.CheckSpelling%2A> -Methode des aktiven Arbeitsblatts auf.  
  
     [!code-csharp[Trin_VstcoreExcelAutomationAddIn#22](../vsto/codesnippet/CSharp/trin_vstcoreexcelautomationaddin/ThisAddIn.cs#22)]
     [!code-vb[Trin_VstcoreExcelAutomationAddIn#22](../vsto/codesnippet/VisualBasic/trin_vstcoreexcelautomationaddin/ThisAddIn.vb#22)]  
  
## <a name="see-also"></a>Siehe auch  
 [Arbeiten mit Arbeitsblättern](../vsto/working-with-worksheets.md)   
 [Vorgehensweise: Ausführen von Excel-Berechnungen programmgesteuert](../vsto/how-to-programmatically-run-excel-calculations-programmatically.md)   
 [NamedRange-Steuerelement](../vsto/namedrange-control.md)   
 [Optionale Parameter in Office-Projektmappen](../vsto/optional-parameters-in-office-solutions.md)  
  
  