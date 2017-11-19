---
title: 'Vorgehensweise: Programmgesteuertes Liste zuletzt verwendeter Arbeitsmappendateien | Microsoft Docs'
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
- workbooks, listing recently used
- RecentFiles property
- Excel [Office development in Visual Studio], recently used files listing
- recent file list, Excel
ms.assetid: 210a3753-4845-4875-b34a-a30d3a1299b3
caps.latest.revision: "42"
author: gewarren
ms.author: gewarren
manager: ghogen
ms.openlocfilehash: 85a555280224d6c8ef853a081698530516052539
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 10/31/2017
---
# <a name="how-to-programmatically-list-recently-used-workbook-files"></a>Gewusst wie: Programmgesteuertes Auflisten zuletzt verwendeter Arbeitsmappendateien
  Die <xref:Microsoft.Office.Interop.Excel._Application.RecentFiles%2A> -Eigenschaft gibt eine Auflistung, die die Namen aller Dateien enthält, die in der Microsoft Office Excel-Liste der zuletzt verwendeten Dateien angezeigt werden. Die Länge der Liste variiert abhängig von der Anzahl der Dateien an, die der Benutzer ausgewählt hat, beibehalten werden sollen. Sie können die Ergebnisse in einem Bereich angezeigt.  
  
 [!INCLUDE[appliesto_xlalldocapp](../vsto/includes/appliesto-xlalldocapp-md.md)]  
  
### <a name="to-list-recently-used-workbooks-in-a-range-object"></a>Auf die Liste zuletzt verwendete Arbeitsmappen eines Range-Objekts  
  
1.  Durchlaufen Sie die Liste der zuletzt verwendeten Dateien und die Anzeigenamen in den Zellen relativ zu einem <xref:Microsoft.Office.Interop.Excel.Range> Objekt.  
  
     [!code-csharp[Trin_VstcoreExcelAutomationAddIn#9](../vsto/codesnippet/CSharp/trin_vstcoreexcelautomationaddin/ThisAddIn.cs#9)]
     [!code-vb[Trin_VstcoreExcelAutomationAddIn#9](../vsto/codesnippet/VisualBasic/trin_vstcoreexcelautomationaddin/ThisAddIn.vb#9)]  
  
## <a name="see-also"></a>Siehe auch  
 [Arbeiten mit Arbeitsmappen](../vsto/working-with-workbooks.md)   
 [NamedRange-Steuerelement](../vsto/namedrange-control.md)   
 [Optionale Parameter in Office-Projektmappen](../vsto/optional-parameters-in-office-solutions.md)  
  
  