---
title: 'Gewusst wie: Programm gesteuertes Anzeigen von Arbeitsblatt Kommentaren'
ms.date: 02/02/2017
ms.topic: how-to
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- worksheets, comments
- comments, worksheets
author: John-Hart
ms.author: johnhart
manager: jillfra
ms.workload:
- office
ms.openlocfilehash: 0fc84e2726cd7a70b8fc59b0f1ac2b3377f9c4af
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 09/02/2020
ms.locfileid: "85543363"
---
# <a name="how-to-programmatically-display-worksheet-comments"></a>Gewusst wie: Programm gesteuertes Anzeigen von Arbeitsblatt Kommentaren
  Sie können Kommentare in Microsoft Office Excel-Arbeitsblättern programmgesteuert anzeigen und ausblenden.

 [!INCLUDE[appliesto_xlalldocapp](../vsto/includes/appliesto-xlalldocapp-md.md)]

## <a name="to-display-all-comments-on-a-worksheet-in-a-document-level-customization"></a>So zeigen Sie alle Kommentare auf einem Arbeitsblatt in einer Anpassung auf Dokumentebene an

1. Legen Sie die <xref:Microsoft.Office.Interop.Excel.Comment.Visible%2A> -Eigenschaft auf **true** fest, wenn Sie Kommentare anzeigen möchten, andernfalls auf **false**. Dieser Code muss in einer Sheet-Klasse platziert werden und nicht in der `ThisWorkbook` -Klasse.

     [!code-csharp[Trin_VstcoreExcelAutomation#31](../vsto/codesnippet/CSharp/Trin_VstcoreExcelAutomationCS/Sheet1.cs#31)]
     [!code-vb[Trin_VstcoreExcelAutomation#31](../vsto/codesnippet/VisualBasic/Trin_VstcoreExcelAutomation/Sheet1.vb#31)]

## <a name="to-display-all-comments-on-a-worksheet-in-an-application-level-vsto-add-in"></a>So zeigen Sie alle Kommentare auf einem Arbeitsblatt in einem VSTO-Add-In auf Anwendungsebene an

1. Legen Sie die <xref:Microsoft.Office.Interop.Excel.Comment.Visible%2A> -Eigenschaft auf **true** fest, wenn Sie Kommentare anzeigen möchten, andernfalls auf **false**.

     [!code-csharp[Trin_VstcoreExcelAutomationAddIn#21](../vsto/codesnippet/CSharp/trin_vstcoreexcelautomationaddin/ThisAddIn.cs#21)]
     [!code-vb[Trin_VstcoreExcelAutomationAddIn#21](../vsto/codesnippet/VisualBasic/trin_vstcoreexcelautomationaddin/ThisAddIn.vb#21)]

## <a name="see-also"></a>Weitere Informationen
- [Arbeiten mit Arbeitsblättern](../vsto/working-with-worksheets.md)
- [Gewusst wie: Programm gesteuertes hinzufügen und Löschen von Arbeitsblatt Kommentaren](../vsto/how-to-programmatically-add-and-delete-worksheet-comments.md)
- [Übersicht über Host Elemente und Host Steuerelemente](../vsto/host-items-and-host-controls-overview.md)
