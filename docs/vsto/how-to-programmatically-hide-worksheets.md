---
title: 'Vorgehensweise: Programmgesteuertes Ausblenden von Arbeitsblättern'
ms.date: 02/02/2017
ms.topic: conceptual
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- hidden worksheets
- worksheets, hiding
author: TerryGLee
ms.author: tglee
manager: douge
ms.workload:
- office
ms.openlocfilehash: c8e03ce17e41c81a6d3cfda4f66d1ecee1946fa3
ms.sourcegitcommit: 37fb7075b0a65d2add3b137a5230767aa3266c74
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 01/02/2019
ms.locfileid: "53821447"
---
# <a name="how-to-programmatically-hide-worksheets"></a>Vorgehensweise: Programmgesteuertes Ausblenden von Arbeitsblättern
  Sie können jedes Arbeitsblatt in einer Arbeitsmappe anzeigen oder ausblenden. Wenn Sie ein Arbeitsblatt ausblenden möchten, verwenden Sie das Arbeitsblatt-Hostelement, oder greifen Sie auf das Arbeitsblatt mithilfe der Sheets-Auflistung der Arbeitsmappe zu.  
  
 [!INCLUDE[appliesto_xlalldocapp](../vsto/includes/appliesto-xlalldocapp-md.md)]  
  
## <a name="use-the-worksheet-host-item"></a>Verwenden Sie das Arbeitsblatt-Hostelement  
 Wenn das Arbeitsblatt zur Entwurfszeit in einer Anpassung auf Dokumentebene hinzugefügt wurde, verwenden Sie die <xref:Microsoft.Office.Tools.Excel.Worksheet.Visible%2A> -Eigenschaft, um das angegebene Arbeitsblatt auszublenden.  
  
### <a name="to-hide-a-worksheet-using-a-worksheet-host-item"></a>So blenden Sie ein Arbeitsblatt mit einem Worksheet-Hostelement aus  
  
1.  Legen Sie die <xref:Microsoft.Office.Tools.Excel.Worksheet.Visible%2A> -Eigenschaft des `Sheet1` -Hostelements auf den <xref:Microsoft.Office.Interop.Excel.XlSheetVisibility.xlSheetHidden> -Enumerationswert fest.  
  
     [!code-csharp[Trin_VstcoreExcelAutomation#25](../vsto/codesnippet/CSharp/Trin_VstcoreExcelAutomationCS/Sheet1.cs#25)]
     [!code-vb[Trin_VstcoreExcelAutomation#25](../vsto/codesnippet/VisualBasic/Trin_VstcoreExcelAutomation/Sheet1.vb#25)]  
  
## <a name="use-the-sheets-collection-of-the-excel-workbook"></a>Verwenden der Sheets-Auflistung der Excel-Arbeitsmappe  
 Greifen Sie auf Arbeitsblätter über die Microsoft Office Excel-Auflistung <xref:Microsoft.Office.Interop.Excel.Sheets> in den folgenden Fällen zu:  
  
-   Sie möchten ein Arbeitsblatt in einem VSTO-Add-in ausblenden.  
  
-   Das Arbeitsblatt, das Sie ausblenden möchten, wurde zur Laufzeit in einer Anpassung auf Dokumentebene erstellt.  
  
### <a name="to-hide-a-worksheet-using-the-sheets-collection-of-the-excel-workbook"></a>So blenden Sie ein Arbeitsblatt mit der Sheets-Auflistung der Excel-Arbeitsmappe aus  
  
1.  Legen Sie die <xref:Microsoft.Office.Interop.Excel.Worksheets.Visible%2A> -Eigenschaft des Arbeitsblatts auf den <xref:Microsoft.Office.Interop.Excel.XlSheetVisibility.xlSheetHidden> -Enumerationswert fest.  
  
     [!code-csharp[Trin_VstcoreExcelAutomation#26](../vsto/codesnippet/CSharp/Trin_VstcoreExcelAutomationCS/Sheet1.cs#26)]
     [!code-vb[Trin_VstcoreExcelAutomation#26](../vsto/codesnippet/VisualBasic/Trin_VstcoreExcelAutomation/Sheet1.vb#26)]  
  
## <a name="see-also"></a>Siehe auch  
 [Arbeiten mit Arbeitsblättern](../vsto/working-with-worksheets.md)   
 [Vorgehensweise: Programmgesteuertes Löschen von Arbeitsblättern aus Arbeitsmappen](../vsto/how-to-programmatically-delete-worksheets-from-workbooks.md)   
 [Vorgehensweise: Programmgesteuertes Verschieben von Arbeitsblättern in Arbeitsmappen](../vsto/how-to-programmatically-move-worksheets-within-workbooks.md)   
 [Vorgehensweise: Programmgesteuertes Schützen von Arbeitsblättern](../vsto/how-to-programmatically-protect-worksheets.md)   
 [Hostelemente und Host-Steuerelementen (Übersicht)](../vsto/host-items-and-host-controls-overview.md)   
 [Globaler Zugriff auf Objekte in Office-Projekten](../vsto/global-access-to-objects-in-office-projects.md)  
