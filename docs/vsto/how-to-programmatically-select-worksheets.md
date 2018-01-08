---
title: "Vorgehensweise: Programmgesteuertes auswählen von Arbeitsblättern | Microsoft Docs"
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
- worksheets, selecting
- Excel projects, selecting worksheets
ms.assetid: 9e7cdb11-e825-4c9f-abcd-d46fd20dc5e0
caps.latest.revision: "44"
author: gewarren
ms.author: gewarren
manager: ghogen
ms.workload: office
ms.openlocfilehash: dd84ad38955620ad09ab9fab5fc178241e682948
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 12/22/2017
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
 [Programmatic Limitations of Host Items and Host Controls](../vsto/programmatic-limitations-of-host-items-and-host-controls.md)   
 [Optionale Parameter in Office-Projektmappen](../vsto/optional-parameters-in-office-solutions.md)   
 [Übersicht über Hostelemente und Hoststeuerelemente](../vsto/host-items-and-host-controls-overview.md)  
  
  