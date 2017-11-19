---
title: "Vorgehensweise: Programmgesteuertes Auflisten aller Arbeitsblätter in einer Arbeitsmappe | Microsoft Docs"
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
- workbooks, listing worksheets
- worksheets, listing
ms.assetid: 38b63d1d-6047-44e8-b089-c576c6179e4a
caps.latest.revision: "46"
author: gewarren
ms.author: gewarren
manager: ghogen
ms.openlocfilehash: 78941e2f1c26b8d8a9a2a4e5ed02c6f4bae7dc0c
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 10/31/2017
---
# <a name="how-to-programmatically-list-all-worksheets-in-a-workbook"></a>Gewusst wie: Programmgesteuertes Auflisten aller Arbeitsblätter in einer Arbeitsmappe
  Die <xref:Microsoft.Office.Interop.Excel.Workbook>-Klasse stellt ein <xref:Microsoft.Office.Interop.Excel.Worksheets>-Objekt bereit. Dieses Objekt enthält eine Auflistung aller <xref:Microsoft.Office.Interop.Excel.Worksheet>-Objekte in der Arbeitsmappe.  
  
 [!INCLUDE[appliesto_xlalldocapp](../vsto/includes/appliesto-xlalldocapp-md.md)]  
  
### <a name="to-list-all-existing-worksheets-in-a-workbook-in-a-document-level-customization"></a>So listen Sie alle vorhandenen Arbeitsblätter einer Arbeitsmappe in einer Anpassung auf Dokumentenebene auf.  
  
1.  Durchlaufen Sie die <xref:Microsoft.Office.Interop.Excel.Worksheets>-Auflistung, und senden Sie mit einem <xref:Microsoft.Office.Tools.Excel.NamedRange>-Steuerelement den Namen jedes Blattes an ein Zellenoffset.  
  
     [!code-csharp[Trin_VstcoreExcelAutomation#21](../vsto/codesnippet/CSharp/Trin_VstcoreExcelAutomationCS/Sheet1.cs#21)]
     [!code-vb[Trin_VstcoreExcelAutomation#21](../vsto/codesnippet/VisualBasic/Trin_VstcoreExcelAutomation/Sheet1.vb#21)]  
  
### <a name="to-list-all-existing-worksheets-in-a-workbook-in-a-vsto-add-in"></a>So listen Sie alle vorhandenen Arbeitsblätter einer Arbeitsmappe in einem VSTO-Add-In auf  
  
1.  Durchlaufen Sie die <xref:Microsoft.Office.Interop.Excel.Worksheets>-Auflistung und senden Sie mit einem <xref:Microsoft.Office.Interop.Excel.Range>-Objekt den Namen jedes Blatts an ein Zellenoffset.  
  
     [!code-csharp[Trin_VstcoreExcelAutomationAddIn#13](../vsto/codesnippet/CSharp/trin_vstcoreexcelautomationaddin/ThisAddIn.cs#13)]
     [!code-vb[Trin_VstcoreExcelAutomationAddIn#13](../vsto/codesnippet/VisualBasic/trin_vstcoreexcelautomationaddin/ThisAddIn.vb#13)]  
  
## <a name="see-also"></a>Siehe auch  
 [Arbeiten mit Arbeitsblättern](../vsto/working-with-worksheets.md)   
 [Vorgehensweise: Programmgesteuertes Hinzufügen neuer Arbeitsblätter zu Arbeitsmappen](../vsto/how-to-programmatically-add-new-worksheets-to-workbooks.md)   
 [Vorgehensweise: Programmgesteuertes Verschieben von Arbeitsblättern in Arbeitsmappen](../vsto/how-to-programmatically-move-worksheets-within-workbooks.md)   
 [Globaler Zugriff auf Objekte in Office-Projekten](../vsto/global-access-to-objects-in-office-projects.md)  
  
  