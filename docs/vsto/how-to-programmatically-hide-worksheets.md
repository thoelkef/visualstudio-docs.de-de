---
title: "Gewusst wie: Programmgesteuertes Ausblenden von Arbeitsbl&#228;ttern | Microsoft Docs"
ms.custom: ""
ms.date: "02/02/2017"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "office-development"
ms.tgt_pltfrm: ""
ms.topic: "article"
dev_langs: 
  - "VB"
  - "CSharp"
helpviewer_keywords: 
  - "Ausgeblendete Arbeitsblätter"
  - "Arbeitsblätter, Ausblenden"
ms.assetid: 3208f633-137f-47f9-9c9c-2cf8e3c72096
caps.latest.revision: 44
author: "kempb"
ms.author: "kempb"
manager: "ghogen"
caps.handback.revision: 43
---
# Gewusst wie: Programmgesteuertes Ausblenden von Arbeitsbl&#228;ttern
  Sie können jedes Arbeitsblatt in einer Arbeitsmappe anzeigen oder ausblenden. Wenn Sie ein Arbeitsblatt ausblenden möchten, verwenden Sie das Arbeitsblatt\-Hostelement, oder greifen Sie auf das Arbeitsblatt mithilfe der Sheets\-Auflistung der Arbeitsmappe zu.  
  
 [!INCLUDE[appliesto_xlalldocapp](../vsto/includes/appliesto-xlalldocapp-md.md)]  
  
## Verwenden das Arbeitsblatt\-Hostelements  
 Wenn das Arbeitsblatt zur Entwurfszeit in einer Anpassung auf Dokumentebene hinzugefügt wurde, verwenden Sie die <xref:Microsoft.Office.Tools.Excel.Worksheet.Visible%2A>\-Eigenschaft, um das angegebene Arbeitsblatt auszublenden.  
  
#### So blenden Sie ein Arbeitsblatt mit einem Worksheet\-Hostelement aus  
  
1.  Legen Sie die <xref:Microsoft.Office.Tools.Excel.Worksheet.Visible%2A>\-Eigenschaft des `Sheet1`\-Hostelements auf den <xref:Microsoft.Office.Interop.Excel.XlSheetVisibility.xlSheetHidden>\-Enumerationswert fest.  
  
     [!code-csharp[Trin_VstcoreExcelAutomation#25](../snippets/csharp/VS_Snippets_OfficeSP/Trin_VstcoreExcelAutomation/CS/Sheet1.cs#25)]
     [!code-vb[Trin_VstcoreExcelAutomation#25](../snippets/visualbasic/VS_Snippets_OfficeSP/Trin_VstcoreExcelAutomation/VB/Sheet1.vb#25)]  
  
## Verwenden der Sheets\-Auflistung der Excel\-Arbeitsmappe  
 Greifen Sie auf Arbeitsblätter über die Microsoft Office Excel\-Auflistung <xref:Microsoft.Office.Interop.Excel.Sheets> in den folgenden Fällen zu:  
  
-   Sie möchten ein Arbeitsblatt in einem VSTO\-Add\-In ausblenden.  
  
-   Das Arbeitsblatt, das Sie ausblenden möchten, wurde zur Laufzeit in einer Anpassung auf Dokumentebene erstellt.  
  
#### So blenden Sie ein Arbeitsblatt mit der Sheets\-Auflistung der Excel\-Arbeitsmappe aus  
  
1.  Legen Sie die <xref:Microsoft.Office.Interop.Excel.Worksheets.Visible%2A>\-Eigenschaft des Arbeitsblatts auf den <xref:Microsoft.Office.Interop.Excel.XlSheetVisibility.xlSheetHidden>\-Enumerationswert fest.  
  
     [!code-csharp[Trin_VstcoreExcelAutomation#26](../snippets/csharp/VS_Snippets_OfficeSP/Trin_VstcoreExcelAutomation/CS/Sheet1.cs#26)]
     [!code-vb[Trin_VstcoreExcelAutomation#26](../snippets/visualbasic/VS_Snippets_OfficeSP/Trin_VstcoreExcelAutomation/VB/Sheet1.vb#26)]  
  
## Siehe auch  
 [Arbeiten mit Arbeitsblättern](../vsto/working-with-worksheets.md)   
 [Gewusst wie: Programmgesteuertes Löschen von Arbeitsblättern aus Arbeitsmappen](../vsto/how-to-programmatically-delete-worksheets-from-workbooks.md)   
 [Gewusst wie: Programmgesteuertes Verschieben von Arbeitsblättern in Arbeitsmappen](../vsto/how-to-programmatically-move-worksheets-within-workbooks.md)   
 [Gewusst wie: Programmgesteuertes Schützen von Arbeitsblättern](../vsto/how-to-programmatically-protect-worksheets.md)   
 [Übersicht über Hostelemente und Hoststeuerelemente](../vsto/host-items-and-host-controls-overview.md)   
 [Globaler Zugriff auf Objekte in Office-Projekten](../vsto/global-access-to-objects-in-office-projects.md)  
  
  