---
title: 'Vorgehensweise: Programm gesteuertes auswählen von Arbeitsblättern'
ms.date: 02/02/2017
ms.topic: conceptual
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- worksheets, selecting
- Excel projects, selecting worksheets
author: John-Hart
ms.author: johnhart
manager: jillfra
ms.workload:
- office
ms.openlocfilehash: 20ebc8fea14b3dc52c802543f97318ec7fae7529
ms.sourcegitcommit: e98db44f3a33529b0ba188d24390efd09e548191
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 09/25/2019
ms.locfileid: "71255628"
---
# <a name="how-to-programmatically-select-worksheets"></a>Vorgehensweise: Programm gesteuertes auswählen von Arbeitsblättern
  Die Methode <xref:Microsoft.Office.Tools.Excel.Worksheet.Select%2A> wählt das angegebene Objekt aus. Die Auswahl des Benutzers wird in das neue Objekt verschoben. Verwenden Sie die Methode <xref:Microsoft.Office.Tools.Excel.Worksheet.Activate%2A>, wenn Sie den Fokus auf das Objekt verschieben möchten, ohne die Benutzerauswahl zu ändern.

 [!INCLUDE[appliesto_xlalldocapp](../vsto/includes/appliesto-xlalldocapp-md.md)]

 Wenn Sie ein vorhandenes Arbeitsblatt in einem VSTO-Add-In auswählen möchten oder wenn das Arbeitsblatt zur Laufzeit in einer Anpassung auf Dokumentebene erstellt wurde, müssen Sie mit der Excel-Auflistung <xref:Microsoft.Office.Interop.Excel.Sheets> der Excel-Arbeitsmappe darauf zugreifen. Andernfalls können Sie direkt auf das <xref:Microsoft.Office.Tools.Excel.Worksheet>-Hostelement zugreifen.

## <a name="use-the-worksheet-host-item"></a>Arbeitsblatt-Host Element verwenden
 Fügen Sie in einer Anpassung auf Dokument Ebene den folgenden Code zu *Sheet1. vb* oder *Sheet1.cs*hinzu.

### <a name="to-select-the-first-worksheet-in-a-workbook-using-a-host-item"></a>So wählen Sie das erste Arbeitsblatt in einer Arbeitsmappe mithilfe eines Hostelements aus

1. Rufen Sie die <xref:Microsoft.Office.Tools.Excel.Worksheet.Select%2A> -Methode von `Sheet1`auf.

     [!code-csharp[Trin_VstcoreExcelAutomation#19](../vsto/codesnippet/CSharp/Trin_VstcoreExcelAutomationCS/Sheet1.cs#19)]
     [!code-vb[Trin_VstcoreExcelAutomation#19](../vsto/codesnippet/VisualBasic/Trin_VstcoreExcelAutomation/Sheet1.vb#19)]

## <a name="use-the-sheets-collection-of-the-excel-workbook"></a>Verwenden der Sheets-Auflistung der Excel-Arbeitsmappe
 Greifen Sie auf das Arbeitsblatt mithilfe der Excel-Auflistung <xref:Microsoft.Office.Interop.Excel.Sheets> zu.

### <a name="to-select-the-first-worksheet-in-a-workbook-using-the-sheets-collection-of-the-excel-workbook"></a>So wählen Sie das erste Arbeitsblatt in einer Arbeitsmappe mithilfe der Sheets-Auflistung der Excel-Arbeitsmappe aus

1. Rufen Sie die Methode <xref:Microsoft.Office.Interop.Excel.Sheets.Select%2A> der Auflistung <xref:Microsoft.Office.Interop.Excel.Sheets> auf, um das erste Arbeitsblatt der aktiven Arbeitsmappe auszuwählen.

     [!code-csharp[Trin_VstcoreExcelAutomation#20](../vsto/codesnippet/CSharp/Trin_VstcoreExcelAutomationCS/Sheet1.cs#20)]
     [!code-vb[Trin_VstcoreExcelAutomation#20](../vsto/codesnippet/VisualBasic/Trin_VstcoreExcelAutomation/Sheet1.vb#20)]

## <a name="see-also"></a>Siehe auch
- [Arbeiten mit Arbeitsblättern](../vsto/working-with-worksheets.md)
- [Vorgehensweise: Programm gesteuertes Drucken von Arbeitsblättern](../vsto/how-to-programmatically-print-worksheets.md)
- [Vorgehensweise: Programm gesteuertes Löschen von Arbeitsblättern aus Arbeitsmappen](../vsto/how-to-programmatically-delete-worksheets-from-workbooks.md)
- [Vorgehensweise: Arbeitsblätter Programm gesteuert ausblenden](../vsto/how-to-programmatically-hide-worksheets.md)
- [Vorgehensweise: Programm gesteuertes schützen von Arbeitsblättern](../vsto/how-to-programmatically-protect-worksheets.md)
- [Arbeitsblatt-Host Element](../vsto/worksheet-host-item.md)
- [Globaler Zugriff auf Objekte in Office-Projekten](../vsto/global-access-to-objects-in-office-projects.md)
- [Programmgesteuerte Einschränkungen von Host Elementen und Host Steuerelementen](../vsto/programmatic-limitations-of-host-items-and-host-controls.md)
- [Optionale Parameter in Office-Projektmappen](../vsto/optional-parameters-in-office-solutions.md)
- [Übersicht über Host Elemente und Host Steuerelemente](../vsto/host-items-and-host-controls-overview.md)
