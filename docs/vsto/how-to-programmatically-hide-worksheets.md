---
title: "Vorgehensweise: Programmgesteuertes Ausblenden von Arbeitsblättern | Microsoft Docs"
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
- hidden worksheets
- worksheets, hiding
author: TerryGLee
ms.author: tglee
manager: ghogen
ms.workload: office
ms.openlocfilehash: 1ce83d6cec246a5a232026dff4e11f3dc1ed9e06
ms.sourcegitcommit: f9fbf1f55f9ac14e4e5c6ae58c30dc1800ca6cda
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 01/10/2018
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
 [Host Items and Host Controls Overview](../vsto/host-items-and-host-controls-overview.md)   
 [Globaler Zugriff auf Objekte in Office-Projekten](../vsto/global-access-to-objects-in-office-projects.md)  
  