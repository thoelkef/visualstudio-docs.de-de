---
title: 'Gewusst wie: Programm gesteuertes Auflisten zuletzt verwendeter Arbeitsmappendateien'
ms.date: 02/02/2017
ms.topic: how-to
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
ms.openlocfilehash: 4f4f34a8ed848d548b2e23d3f9a3cf3c603c7cad
ms.sourcegitcommit: b885f26e015d03eafe7c885040644a52bb071fae
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 06/30/2020
ms.locfileid: "85541361"
---
# <a name="how-to-programmatically-list-recently-used-workbook-files"></a>Gewusst wie: Programm gesteuertes Auflisten zuletzt verwendeter Arbeitsmappendateien
  Die- <xref:Microsoft.Office.Interop.Excel._Application.RecentFiles%2A> Eigenschaft gibt eine Auflistung zurück, die die Namen aller Dateien enthält, die in der Microsoft Office Excel-Liste der zuletzt verwendeten Dateien angezeigt werden. Die Länge der Liste variiert je nach der Anzahl der Dateien, die der Benutzer für die Beibehaltung ausgewählt hat. Die Ergebnisse können in einem Bereich angezeigt werden.

 [!INCLUDE[appliesto_xlalldocapp](../vsto/includes/appliesto-xlalldocapp-md.md)]

## <a name="to-list-recently-used-workbooks-in-a-range-object"></a>So Listen Sie zuletzt verwendete Arbeitsmappen in einem Bereichs Objekt auf

1. Durchlaufen Sie die Liste der zuletzt geöffneten Dateien, und zeigen Sie die Namen in Zellen relativ zu einem- <xref:Microsoft.Office.Interop.Excel.Range> Objekt an.

     [!code-csharp[Trin_VstcoreExcelAutomationAddIn#9](../vsto/codesnippet/CSharp/trin_vstcoreexcelautomationaddin/ThisAddIn.cs#9)]
     [!code-vb[Trin_VstcoreExcelAutomationAddIn#9](../vsto/codesnippet/VisualBasic/trin_vstcoreexcelautomationaddin/ThisAddIn.vb#9)]

## <a name="see-also"></a>Siehe auch
- [Arbeiten mit Arbeitsmappen](../vsto/working-with-workbooks.md)
- [Name Drange-Steuerelement](../vsto/namedrange-control.md)
- [Optionale Parameter in Office-Projektmappen](../vsto/optional-parameters-in-office-solutions.md)
