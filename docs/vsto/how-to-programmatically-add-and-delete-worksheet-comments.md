---
title: "Vorgehensweise: Programmgesteuertes Hinzufügen und Löschen von Arbeitsblattkommentaren | Microsoft Docs"
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
- ranges, comments
- worksheets, comments
- comments, worksheets
ms.assetid: 3408ce22-a7b7-4e2b-bfc1-dc24d679ee73
caps.latest.revision: "53"
author: gewarren
ms.author: gewarren
manager: ghogen
ms.openlocfilehash: c2c9e2111e02bb9669b7e915bb170e4607932978
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 10/31/2017
---
# <a name="how-to-programmatically-add-and-delete-worksheet-comments"></a>Gewusst wie: Programmgesteuertes Hinzufügen und Löschen von Arbeitsblattkommentaren
  Sie können Kommentare in Microsoft Office Excel-Arbeitsblättern programmgesteuert hinzufügen und löschen. Kommentare können nur einzelnen Zellen, nicht Bereichen mit mehreren Zellen hinzugefügt werden.  
  
 [!INCLUDE[appliesto_xlalldocapp](../vsto/includes/appliesto-xlalldocapp-md.md)]  
  
## <a name="adding-and-deleting-a-comment-in-a-document-level-project"></a>Hinzufügen und Löschen eines Kommentars in einem Projekt auf Dokumentebene  
 Im folgendem Beispiel wird davon ausgegangen, dass sich ein in einer Zelle befindliches <xref:Microsoft.Office.Tools.Excel.NamedRange> -Steuerelement namens `dateComment` auf dem Arbeitsblatt `Sheet1`befindet.  
  
#### <a name="to-add-a-new-comment-to-a-named-range"></a>So fügen Sie einem benannten Bereich einen neuen Kommentar hinzu  
  
1.  Rufen Sie die <xref:Microsoft.Office.Tools.Excel.NamedRange.AddComment%2A> -Methode des <xref:Microsoft.Office.Tools.Excel.NamedRange> -Steuerelements auf, und geben Sie den Kommentartext an. Dieser Code muss in die `Sheet1` -Klasse eingefügt werden.  
  
     [!code-csharp[Trin_VstcoreExcelAutomation#30](../vsto/codesnippet/CSharp/Trin_VstcoreExcelAutomationCS/Sheet1.cs#30)]
     [!code-vb[Trin_VstcoreExcelAutomation#30](../vsto/codesnippet/VisualBasic/Trin_VstcoreExcelAutomation/Sheet1.vb#30)]  
  
#### <a name="to-delete-a-comment-from-a-named-range"></a>So löschen Sie einen Kommentar aus einem benannten Bereich  
  
1.  Stellen Sie sicher, dass im Bereich ein Kommentar vorhanden ist, und löschen Sie ihn. Dieser Code muss in die `Sheet1` -Klasse eingefügt werden.  
  
     [!code-csharp[Trin_VstcoreExcelAutomation#29](../vsto/codesnippet/CSharp/Trin_VstcoreExcelAutomationCS/Sheet1.cs#29)]
     [!code-vb[Trin_VstcoreExcelAutomation#29](../vsto/codesnippet/VisualBasic/Trin_VstcoreExcelAutomation/Sheet1.vb#29)]  
  
## <a name="adding-and-deleting-a-comment-in-an-vsto-add-in-project"></a>Hinzufügen und Löschen eines Kommentars in einem VSTO-Add-In-Projekt  
 Im folgendem Beispiel wird davon ausgegangen, dass sich ein in einer Zelle befindliches <xref:Microsoft.Office.Interop.Excel.Range> -Steuerelement namens `dateComment` auf dem aktiven Arbeitsblatt befindet.  
  
#### <a name="to-add-a-new-comment-to-an-excel-range"></a>So fügen Sie einem Excel-Bereich einen neuen Kommentar hinzu  
  
1.  Rufen Sie die <xref:Microsoft.Office.Interop.Excel.Range.AddComment%2A> -Methode des <xref:Microsoft.Office.Interop.Excel.Range> -Steuerelements auf, und stellen Sie den Kommentartext bereit.  
  
     [!code-csharp[Trin_VstcoreExcelAutomationAddIn#20](../vsto/codesnippet/CSharp/trin_vstcoreexcelautomationaddin/ThisAddIn.cs#20)]
     [!code-vb[Trin_VstcoreExcelAutomationAddIn#20](../vsto/codesnippet/VisualBasic/trin_vstcoreexcelautomationaddin/ThisAddIn.vb#20)]  
  
#### <a name="to-delete-a-comment-from-an-excel-range"></a>So löschen Sie einen Kommentar aus einem Excel-Bereich  
  
1.  Stellen Sie sicher, dass im Bereich ein Kommentar vorhanden ist, und löschen Sie ihn.  
  
     [!code-csharp[Trin_VstcoreExcelAutomationAddIn#19](../vsto/codesnippet/CSharp/trin_vstcoreexcelautomationaddin/ThisAddIn.cs#19)]
     [!code-vb[Trin_VstcoreExcelAutomationAddIn#19](../vsto/codesnippet/VisualBasic/trin_vstcoreexcelautomationaddin/ThisAddIn.vb#19)]  
  
## <a name="see-also"></a>Siehe auch  
 [Arbeiten mit Arbeitsblättern](../vsto/working-with-worksheets.md)   
 [Vorgehensweise: Programmgesteuertes Anzeigen von Arbeitsblattkommentaren](../vsto/how-to-programmatically-display-worksheet-comments.md)   
 [NamedRange-Steuerelement](../vsto/namedrange-control.md)  
  
  