---
title: 'Vorgehensweise: Programmgesteuertes Hinzufügen und Löschen von Arbeitsblattkommentaren'
ms.custom: ''
ms.date: 02/02/2017
ms.technology:
- office-development
ms.topic: conceptual
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- ranges, comments
- worksheets, comments
- comments, worksheets
author: John-Hart
ms.author: johnhart
manager: douge
ms.workload:
- office
ms.openlocfilehash: 06097d72693e0b7a00c7af48609523d5e7dfc5a0
ms.sourcegitcommit: f6dd17b0864419083d0a1bf54910023045526437
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 12/27/2018
ms.locfileid: "53804194"
---
# <a name="how-to-programmatically-add-and-delete-worksheet-comments"></a>Vorgehensweise: Programmgesteuertes Hinzufügen und Löschen von Arbeitsblattkommentaren
  Sie können Kommentare in Microsoft Office Excel-Arbeitsblättern programmgesteuert hinzufügen und löschen. Kommentare können nur einzelnen Zellen, nicht Bereichen mit mehreren Zellen hinzugefügt werden.  
  
 [!INCLUDE[appliesto_xlalldocapp](../vsto/includes/appliesto-xlalldocapp-md.md)]  
  
## <a name="add-and-delete-a-comment-in-a-document-level-project"></a>Fügen Sie hinzu und löschen Sie einen Kommentar in einem Projekt auf Dokumentebene  
 Im folgendem Beispiel wird davon ausgegangen, dass sich ein in einer Zelle befindliches <xref:Microsoft.Office.Tools.Excel.NamedRange> -Steuerelement namens `dateComment` auf dem Arbeitsblatt `Sheet1`befindet.  
  
### <a name="to-add-a-new-comment-to-a-named-range"></a>So fügen Sie einem benannten Bereich einen neuen Kommentar hinzu  
  
1.  Rufen Sie die <xref:Microsoft.Office.Tools.Excel.NamedRange.AddComment%2A> -Methode des <xref:Microsoft.Office.Tools.Excel.NamedRange> -Steuerelements auf, und geben Sie den Kommentartext an. Dieser Code muss in die `Sheet1` -Klasse eingefügt werden.  
  
     [!code-csharp[Trin_VstcoreExcelAutomation#30](../vsto/codesnippet/CSharp/Trin_VstcoreExcelAutomationCS/Sheet1.cs#30)]
     [!code-vb[Trin_VstcoreExcelAutomation#30](../vsto/codesnippet/VisualBasic/Trin_VstcoreExcelAutomation/Sheet1.vb#30)]  
  
#### <a name="to-delete-a-comment-from-a-named-range"></a>So löschen Sie einen Kommentar aus einem benannten Bereich  
  
1.  Stellen Sie sicher, dass im Bereich ein Kommentar vorhanden ist, und löschen Sie ihn. Dieser Code muss in die `Sheet1` -Klasse eingefügt werden.  
  
     [!code-csharp[Trin_VstcoreExcelAutomation#29](../vsto/codesnippet/CSharp/Trin_VstcoreExcelAutomationCS/Sheet1.cs#29)]
     [!code-vb[Trin_VstcoreExcelAutomation#29](../vsto/codesnippet/VisualBasic/Trin_VstcoreExcelAutomation/Sheet1.vb#29)]  
  
## <a name="add-and-delete-a-comment-in-a-vsto-add-in-project"></a>Fügen Sie hinzu und löschen Sie einen Kommentar in einem VSTO-Add-in-Projekt  
 Im folgendem Beispiel wird davon ausgegangen, dass sich ein in einer Zelle befindliches <xref:Microsoft.Office.Interop.Excel.Range> -Steuerelement namens `dateComment` auf dem aktiven Arbeitsblatt befindet.  
  
### <a name="to-add-a-new-comment-to-an-excel-range"></a>So fügen Sie einem Excel-Bereich einen neuen Kommentar hinzu  
  
1.  Rufen Sie die <xref:Microsoft.Office.Interop.Excel.Range.AddComment%2A> -Methode des <xref:Microsoft.Office.Interop.Excel.Range> -Steuerelements auf, und stellen Sie den Kommentartext bereit.  
  
     [!code-csharp[Trin_VstcoreExcelAutomationAddIn#20](../vsto/codesnippet/CSharp/trin_vstcoreexcelautomationaddin/ThisAddIn.cs#20)]
     [!code-vb[Trin_VstcoreExcelAutomationAddIn#20](../vsto/codesnippet/VisualBasic/trin_vstcoreexcelautomationaddin/ThisAddIn.vb#20)]  
  
### <a name="to-delete-a-comment-from-an-excel-range"></a>So löschen Sie einen Kommentar aus einem Excel-Bereich  
  
1.  Stellen Sie sicher, dass im Bereich ein Kommentar vorhanden ist, und löschen Sie ihn.  
  
     [!code-csharp[Trin_VstcoreExcelAutomationAddIn#19](../vsto/codesnippet/CSharp/trin_vstcoreexcelautomationaddin/ThisAddIn.cs#19)]
     [!code-vb[Trin_VstcoreExcelAutomationAddIn#19](../vsto/codesnippet/VisualBasic/trin_vstcoreexcelautomationaddin/ThisAddIn.vb#19)]  
  
## <a name="see-also"></a>Siehe auch  
 [Arbeiten mit Arbeitsblättern](../vsto/working-with-worksheets.md)   
 [Vorgehensweise: Programmgesteuertes Anzeigen von Arbeitsblattkommentaren](../vsto/how-to-programmatically-display-worksheet-comments.md)   
 [NamedRange-Steuerelement](../vsto/namedrange-control.md)  
  
  