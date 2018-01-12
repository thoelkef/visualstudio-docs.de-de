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
author: TerryGLee
ms.author: tglee
manager: ghogen
ms.workload: office
ms.openlocfilehash: 7909e82b57d9d0d06217bfd252aa923d5aee2b20
ms.sourcegitcommit: f9fbf1f55f9ac14e4e5c6ae58c30dc1800ca6cda
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 01/10/2018
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
  
  