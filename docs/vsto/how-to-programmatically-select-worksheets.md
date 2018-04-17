---
title: 'Vorgehensweise: Programmgesteuertes auswählen von Arbeitsblättern | Microsoft Docs'
ms.custom: ''
ms.date: 02/02/2017
ms.technology:
- office-development
ms.topic: conceptual
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- worksheets, selecting
- Excel projects, selecting worksheets
author: TerryGLee
ms.author: tglee
manager: douge
ms.workload:
- office
ms.openlocfilehash: 5d0862f83d77365e07df1e61b7063a9e5ecd4f37
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/16/2018
---
# <a name="how-to-programmatically-select-worksheets"></a>Gewusst wie: Programmgesteuertes Auswählen von Arbeitsblättern
  Die Methode <xref:Microsoft.Office.Tools.Excel.Worksheet.Select%2A> wählt das angegebene Objekt aus. Die Auswahl des Benutzers wird in das neue Objekt verschoben. Verwenden Sie die Methode <xref:Microsoft.Office.Tools.Excel.Worksheet.Activate%2A>, wenn Sie den Fokus auf das Objekt verschieben möchten, ohne die Benutzerauswahl zu ändern.  
  
 [!INCLUDE[appliesto_xlalldocapp](../vsto/includes/appliesto-xlalldocapp-md.md)]  
  
 Wenn Sie ein vorhandenes Arbeitsblatt in einem VSTO-Add-In auswählen möchten oder wenn das Arbeitsblatt zur Laufzeit in einer Anpassung auf Dokumentebene erstellt wurde, müssen Sie mit der Excel-Auflistung <xref:Microsoft.Office.Interop.Excel.Sheets> der Excel-Arbeitsmappe darauf zugreifen. Andernfalls können Sie direkt auf das <xref:Microsoft.Office.Tools.Excel.Worksheet>-Hostelement zugreifen.  
  
## <a name="using-the-worksheet-host-item"></a>Verwenden das Arbeitsblatt-Hostelements  
 In einer Anpassung auf Dokumentebene fügen Sie den folgenden Code zum **Sheet1.vb** oder **Sheet1.cs**.  
  
#### <a name="to-select-the-first-worksheet-in-a-workbook-using-a-host-item"></a>So wählen Sie das erste Arbeitsblatt in einer Arbeitsmappe mithilfe eines Hostelements aus  
  
1.  Rufen Sie die <xref:Microsoft.Office.Tools.Excel.Worksheet.Select%2A>-Methode von `Sheet1` auf.  
  
     [!code-csharp[Trin_VstcoreExcelAutomation#19](../vsto/codesnippet/CSharp/Trin_VstcoreExcelAutomationCS/Sheet1.cs#19)]
     [!code-vb[Trin_VstcoreExcelAutomation#19](../vsto/codesnippet/VisualBasic/Trin_VstcoreExcelAutomation/Sheet1.vb#19)]  
  
## <a name="using-the-sheets-collection-of-the-excel-workbook"></a>Verwenden der Sheets-Auflistung der Excel-Arbeitsmappe  
 Greifen Sie auf das Arbeitsblatt mithilfe der Excel-Auflistung <xref:Microsoft.Office.Interop.Excel.Sheets> zu.  
  
#### <a name="to-select-the-first-worksheet-in-a-workbook-using-the-sheets-collection-of-the-excel-workbook"></a>So wählen Sie das erste Arbeitsblatt in einer Arbeitsmappe mithilfe der Sheets-Auflistung der Excel-Arbeitsmappe aus  
  
1.  Rufen Sie die Methode <xref:Microsoft.Office.Interop.Excel.Sheets.Select%2A> der Auflistung <xref:Microsoft.Office.Interop.Excel.Sheets> auf, um das erste Arbeitsblatt der aktiven Arbeitsmappe auszuwählen.  
  
     [!code-csharp[Trin_VstcoreExcelAutomation#20](../vsto/codesnippet/CSharp/Trin_VstcoreExcelAutomationCS/Sheet1.cs#20)]
     [!code-vb[Trin_VstcoreExcelAutomation#20](../vsto/codesnippet/VisualBasic/Trin_VstcoreExcelAutomation/Sheet1.vb#20)]  
  
## <a name="see-also"></a>Siehe auch  
 [Arbeiten mit Arbeitsblättern](../vsto/working-with-worksheets.md)   
 [Vorgehensweise: Programmgesteuertes Drucken von Arbeitsblättern](../vsto/how-to-programmatically-print-worksheets.md)   
 [Vorgehensweise: Programmgesteuertes Löschen von Arbeitsblättern aus Arbeitsmappen](../vsto/how-to-programmatically-delete-worksheets-from-workbooks.md)   
 [Vorgehensweise: Programmgesteuertes Ausblenden von Arbeitsblättern](../vsto/how-to-programmatically-hide-worksheets.md)   
 [Vorgehensweise: Programmgesteuertes Schützen von Arbeitsblättern](../vsto/how-to-programmatically-protect-worksheets.md)   
 [Arbeitsblatt-Hostelements](../vsto/worksheet-host-item.md)   
 [Globaler Zugriff auf Objekte in Office-Projekten](../vsto/global-access-to-objects-in-office-projects.md)   
 [Programmgesteuerte Einschränkungen von Hostelementen und Hoststeuerelementen](../vsto/programmatic-limitations-of-host-items-and-host-controls.md)   
 [Optionale Parameter in Office-Projektmappen](../vsto/optional-parameters-in-office-solutions.md)   
 [Übersicht über Hostelemente und Hoststeuerelemente](../vsto/host-items-and-host-controls-overview.md)  
  
  