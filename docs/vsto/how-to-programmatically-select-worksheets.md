---
title: 'Vorgehensweise: Programmgesteuertes auswählen von Arbeitsblättern'
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
ms.openlocfilehash: 0b56df406049f3f4076f6e4d1efebcf0eb2abb18
ms.sourcegitcommit: 1fc6ee928733e61a1f42782f832ead9f7946d00c
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/22/2019
ms.locfileid: "60081410"
---
# <a name="how-to-programmatically-select-worksheets"></a>Vorgehensweise: Programmgesteuertes auswählen von Arbeitsblättern
  Die Methode <xref:Microsoft.Office.Tools.Excel.Worksheet.Select%2A> wählt das angegebene Objekt aus. Die Auswahl des Benutzers wird in das neue Objekt verschoben. Verwenden Sie die Methode <xref:Microsoft.Office.Tools.Excel.Worksheet.Activate%2A>, wenn Sie den Fokus auf das Objekt verschieben möchten, ohne die Benutzerauswahl zu ändern.

 [!INCLUDE[appliesto_xlalldocapp](../vsto/includes/appliesto-xlalldocapp-md.md)]

 Wenn Sie ein vorhandenes Arbeitsblatt in einem VSTO-Add-in auswählen möchten oder wenn das Arbeitsblatt zur Laufzeit in einer Anpassung auf Dokumentebene erstellt wurde, Sie darauf zugreifen müssen, mit der Excel <xref:Microsoft.Office.Interop.Excel.Sheets> Auflistung der Excel-Arbeitsmappe; andernfalls können Sie die zugreifen<xref:Microsoft.Office.Tools.Excel.Worksheet>Hostelement direkt.

## <a name="use-the-worksheet-host-item"></a>Verwenden Sie das Arbeitsblatt-Hostelement
 Fügen Sie den folgenden Code hinzu, in einer Anpassung auf Dokumentebene *Sheet1.vb* oder *Sheet1.cs*.

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
- [Vorgehensweise: Programmgesteuertes Drucken von Arbeitsblättern](../vsto/how-to-programmatically-print-worksheets.md)
- [Vorgehensweise: Programmgesteuertes Löschen von Arbeitsblättern aus Arbeitsmappen](../vsto/how-to-programmatically-delete-worksheets-from-workbooks.md)
- [Vorgehensweise: Programmgesteuertes Ausblenden von Arbeitsblättern](../vsto/how-to-programmatically-hide-worksheets.md)
- [Vorgehensweise: Programmgesteuertes Schützen von Arbeitsblättern](../vsto/how-to-programmatically-protect-worksheets.md)
- [Arbeitsblatthostelement](../vsto/worksheet-host-item.md)
- [Globaler Zugriff auf Objekte in Office-Projekten](../vsto/global-access-to-objects-in-office-projects.md)
- [Einschränkungen für programmgesteuerte Aufgaben von Hostelementen und Hoststeuerelementen](../vsto/programmatic-limitations-of-host-items-and-host-controls.md)
- [Optionaler Parameter in Office-Projektmappen](../vsto/optional-parameters-in-office-solutions.md)
- [Hostelemente und Host-Steuerelementen (Übersicht)](../vsto/host-items-and-host-controls-overview.md)
