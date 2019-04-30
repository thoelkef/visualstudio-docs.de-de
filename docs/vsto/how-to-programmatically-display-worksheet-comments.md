---
title: 'Vorgehensweise: Programmgesteuertes Anzeigen von Arbeitsblattkommentaren'
ms.date: 02/02/2017
ms.topic: conceptual
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
ms.openlocfilehash: cc030fed25409f5c034abfd07f1f9358bfea593b
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/23/2019
ms.locfileid: "62812695"
---
# <a name="how-to-programmatically-display-worksheet-comments"></a>Vorgehensweise: Programmgesteuertes Anzeigen von Arbeitsblattkommentaren
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

## <a name="see-also"></a>Siehe auch
- [Arbeiten mit Arbeitsblättern](../vsto/working-with-worksheets.md)
- [Vorgehensweise: Programmgesteuertes Hinzufügen und Löschen von Arbeitsblattkommentaren](../vsto/how-to-programmatically-add-and-delete-worksheet-comments.md)
- [Hostelemente und Host-Steuerelementen (Übersicht)](../vsto/host-items-and-host-controls-overview.md)
