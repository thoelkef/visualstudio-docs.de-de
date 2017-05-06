---
title: "Gewusst wie: Programmgesteuertes Auflisten aller Arbeitsbl&#228;tter in einer Arbeitsmappe"
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
  - "Arbeitsmappen, Auflisten von Arbeitsblättern"
  - "Arbeitsblätter, Auflisten"
ms.assetid: 38b63d1d-6047-44e8-b089-c576c6179e4a
caps.latest.revision: 46
author: "kempb"
ms.author: "kempb"
manager: "ghogen"
caps.handback.revision: 45
---
# Gewusst wie: Programmgesteuertes Auflisten aller Arbeitsbl&#228;tter in einer Arbeitsmappe
  Die <xref:Microsoft.Office.Interop.Excel.Workbook>\-Klasse stellt ein <xref:Microsoft.Office.Interop.Excel.Worksheets>\-Objekt bereit.  Dieses Objekt enthält eine Auflistung aller <xref:Microsoft.Office.Interop.Excel.Worksheet>\-Objekte in der Arbeitsmappe.  
  
 [!INCLUDE[appliesto_xlalldocapp](../vsto/includes/appliesto-xlalldocapp-md.md)]  
  
### So listen Sie alle vorhandenen Arbeitsblätter einer Arbeitsmappe in einer Anpassung auf Dokumentenebene auf.  
  
1.  Durchlaufen Sie die <xref:Microsoft.Office.Interop.Excel.Worksheets>\-Auflistung, und senden Sie mit einem <xref:Microsoft.Office.Tools.Excel.NamedRange>\-Steuerelement den Namen jedes Blattes an ein Zellenoffset.  
  
     [!code-csharp[Trin_VstcoreExcelAutomation#21](../snippets/csharp/VS_Snippets_OfficeSP/Trin_VstcoreExcelAutomation/CS/Sheet1.cs#21)]
     [!code-vb[Trin_VstcoreExcelAutomation#21](../snippets/visualbasic/VS_Snippets_OfficeSP/Trin_VstcoreExcelAutomation/VB/Sheet1.vb#21)]  
  
### So listen Sie alle vorhandenen Arbeitsblätter einer Arbeitsmappe in einem VSTO\-Add\-In auf  
  
1.  Durchlaufen Sie die <xref:Microsoft.Office.Interop.Excel.Worksheets>\-Auflistung und senden Sie mit einem <xref:Microsoft.Office.Interop.Excel.Range>\-Objekt den Namen jedes Blatts an ein Zellenoffset.  
  
     [!code-csharp[Trin_VstcoreExcelAutomationAddIn#13](../snippets/csharp/VS_Snippets_OfficeSP/Trin_VstcoreExcelAutomationAddIn/CS/ThisAddIn.cs#13)]
     [!code-vb[Trin_VstcoreExcelAutomationAddIn#13](../snippets/visualbasic/VS_Snippets_OfficeSP/Trin_VstcoreExcelAutomationAddIn/VB/ThisAddIn.vb#13)]  
  
## Siehe auch  
 [Arbeiten mit Arbeitsblättern](../vsto/working-with-worksheets.md)   
 [Gewusst wie: Programmgesteuertes Hinzufügen neuer Arbeitsblätter zu Arbeitsmappen](../vsto/how-to-programmatically-add-new-worksheets-to-workbooks.md)   
 [Gewusst wie: Programmgesteuertes Verschieben von Arbeitsblättern in Arbeitsmappen](../vsto/how-to-programmatically-move-worksheets-within-workbooks.md)   
 [Globaler Zugriff auf Objekte in Office-Projekten](../vsto/global-access-to-objects-in-office-projects.md)  
  
  