---
title: 'Vorgehensweise: Programmgesteuertes Ausblenden von Arbeitsblättern | Microsoft Docs'
ms.custom: ''
ms.date: 02/02/2017
ms.technology:
- office-development
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
ms.openlocfilehash: c66e787d8e1e660f320ab390787c7ebf13d3ef7f
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/16/2018
---
# <a name="how-to-programmatically-hide-worksheets"></a>Gewusst wie: Programmgesteuertes Ausblenden von Arbeitsblättern
  Sie können jedes Arbeitsblatt in einer Arbeitsmappe anzeigen oder ausblenden. Wenn Sie ein Arbeitsblatt ausblenden möchten, verwenden Sie das Arbeitsblatt-Hostelement, oder greifen Sie auf das Arbeitsblatt mithilfe der Sheets-Auflistung der Arbeitsmappe zu.  
  
 [!INCLUDE[appliesto_xlalldocapp](../vsto/includes/appliesto-xlalldocapp-md.md)]  
  
## <a name="using-the-worksheet-host-item"></a>Verwenden das Arbeitsblatt-Hostelements  
 Wenn das Arbeitsblatt zur Entwurfszeit in einer Anpassung auf Dokumentebene hinzugefügt wurde, verwenden Sie die <xref:Microsoft.Office.Tools.Excel.Worksheet.Visible%2A> -Eigenschaft, um das angegebene Arbeitsblatt auszublenden.  
  
#### <a name="to-hide-a-worksheet-using-a-worksheet-host-item"></a>So blenden Sie ein Arbeitsblatt mit einem Worksheet-Hostelement aus  
  
1.  Legen Sie die <xref:Microsoft.Office.Tools.Excel.Worksheet.Visible%2A> -Eigenschaft des `Sheet1` -Hostelements auf den <xref:Microsoft.Office.Interop.Excel.XlSheetVisibility.xlSheetHidden> -Enumerationswert fest.  
  
     [!code-csharp[Trin_VstcoreExcelAutomation#25](../vsto/codesnippet/CSharp/Trin_VstcoreExcelAutomationCS/Sheet1.cs#25)]
     [!code-vb[Trin_VstcoreExcelAutomation#25](../vsto/codesnippet/VisualBasic/Trin_VstcoreExcelAutomation/Sheet1.vb#25)]  
  
## <a name="using-the-sheets-collection-of-the-excel-workbook"></a>Verwenden der Sheets-Auflistung der Excel-Arbeitsmappe  
 Greifen Sie auf Arbeitsblätter über die Microsoft Office Excel-Auflistung <xref:Microsoft.Office.Interop.Excel.Sheets> in den folgenden Fällen zu:  
  
-   Sie möchten ein Arbeitsblatt in einem VSTO-Add-In ausblenden.  
  
-   Das Arbeitsblatt, das Sie ausblenden möchten, wurde zur Laufzeit in einer Anpassung auf Dokumentebene erstellt.  
  
#### <a name="to-hide-a-worksheet-using-the-sheets-collection-of-the-excel-workbook"></a>So blenden Sie ein Arbeitsblatt mit der Sheets-Auflistung der Excel-Arbeitsmappe aus  
  
1.  Legen Sie die <xref:Microsoft.Office.Interop.Excel.Worksheets.Visible%2A> -Eigenschaft des Arbeitsblatts auf den <xref:Microsoft.Office.Interop.Excel.XlSheetVisibility.xlSheetHidden> -Enumerationswert fest.  
  
     [!code-csharp[Trin_VstcoreExcelAutomation#26](../vsto/codesnippet/CSharp/Trin_VstcoreExcelAutomationCS/Sheet1.cs#26)]
     [!code-vb[Trin_VstcoreExcelAutomation#26](../vsto/codesnippet/VisualBasic/Trin_VstcoreExcelAutomation/Sheet1.vb#26)]  
  
## <a name="see-also"></a>Siehe auch  
 [Arbeiten mit Arbeitsblättern](../vsto/working-with-worksheets.md)   
 [Vorgehensweise: Programmgesteuertes Löschen von Arbeitsblättern aus Arbeitsmappen](../vsto/how-to-programmatically-delete-worksheets-from-workbooks.md)   
 [Vorgehensweise: Programmgesteuertes Verschieben von Arbeitsblättern in Arbeitsmappen](../vsto/how-to-programmatically-move-worksheets-within-workbooks.md)   
 [Vorgehensweise: Programmgesteuertes Schützen von Arbeitsblättern](../vsto/how-to-programmatically-protect-worksheets.md)   
 [Übersicht über Hostelemente und Hoststeuerelemente](../vsto/host-items-and-host-controls-overview.md)   
 [Globaler Zugriff auf Objekte in Office-Projekten](../vsto/global-access-to-objects-in-office-projects.md)  
  