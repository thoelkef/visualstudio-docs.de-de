---
title: 'Vorgehensweise: Zuletzt verwendeter Arbeitsmappendateien programmgesteuert Liste'
ms.date: 02/02/2017
ms.topic: conceptual
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- workbooks, listing recently used
- RecentFiles property
- Excel [Office development in Visual Studio], recently used files listing
- recent file list, Excel
author: John-Hart
ms.author: johnhart
manager: jillfra
ms.workload:
- office
ms.openlocfilehash: 6451aa5427799f0905d19b7b90e87f8cca3d0bbd
ms.sourcegitcommit: c0202a77d4dc562cdc55dc2e6223c062281d9749
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 01/24/2019
ms.locfileid: "54863187"
---
# <a name="how-to-programmatically-list-recently-used-workbook-files"></a>Vorgehensweise: Zuletzt verwendeter Arbeitsmappendateien programmgesteuert Liste
  Die <xref:Microsoft.Office.Interop.Excel._Application.RecentFiles%2A> -Eigenschaft gibt eine Auflistung, die die Namen aller Dateien enthält, die in der Microsoft Office Excel-Liste der zuletzt geöffneten Dateien angezeigt werden. Die Länge der Liste variiert abhängig von der Anzahl der Dateien, die der Benutzer ausgewählt hat, beibehalten werden sollen. Sie können die Ergebnisse in einem Bereich anzeigen.  
  
 [!INCLUDE[appliesto_xlalldocapp](../vsto/includes/appliesto-xlalldocapp-md.md)]  
  
## <a name="to-list-recently-used-workbooks-in-a-range-object"></a>Auf die Liste der zuletzt verwendete Arbeitsmappen eines Range-Objekts  
  
1.  Durchlaufen Sie die Liste der zuletzt verwendeten Dateien und die Anzeigenamen in den Zellen relativ zu einem <xref:Microsoft.Office.Interop.Excel.Range> Objekt.  
  
     [!code-csharp[Trin_VstcoreExcelAutomationAddIn#9](../vsto/codesnippet/CSharp/trin_vstcoreexcelautomationaddin/ThisAddIn.cs#9)]
     [!code-vb[Trin_VstcoreExcelAutomationAddIn#9](../vsto/codesnippet/VisualBasic/trin_vstcoreexcelautomationaddin/ThisAddIn.vb#9)]  
  
## <a name="see-also"></a>Siehe auch  
 [Arbeiten mit Arbeitsmappen](../vsto/working-with-workbooks.md)   
 [NamedRange-Steuerelement](../vsto/namedrange-control.md)   
 [Optionaler Parameter in Office-Projektmappen](../vsto/optional-parameters-in-office-solutions.md)  
