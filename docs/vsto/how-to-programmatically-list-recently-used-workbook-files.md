---
title: 'Gewusst wie: Programm gesteuertes Auflisten zuletzt verwendeter Arbeitsmappendateien'
titleSuffix: ''
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
ms.openlocfilehash: 5e3d6b57251bb19cfb02849defb157c949f4ce35
ms.sourcegitcommit: 9d2829dc30b6917e89762d602022915f1ca49089
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 09/30/2020
ms.locfileid: "91585157"
---
# <a name="how-to-programmatically-list-recently-used-workbook-files"></a>Gewusst wie: Programm gesteuertes Auflisten zuletzt verwendeter Arbeitsmappendateien
  Die- <xref:Microsoft.Office.Interop.Excel._Application.RecentFiles%2A> Eigenschaft gibt eine Auflistung zurück, die die Namen aller Dateien enthält, die in der Microsoft Office Excel-Liste der zuletzt verwendeten Dateien angezeigt werden. Die Länge der Liste variiert je nach der Anzahl der Dateien, die der Benutzer für die Beibehaltung ausgewählt hat. Die Ergebnisse können in einem Bereich angezeigt werden.

 [!INCLUDE[appliesto_xlalldocapp](../vsto/includes/appliesto-xlalldocapp-md.md)]

## <a name="to-list-recently-used-workbooks-in-a-range-object"></a>So Listen Sie zuletzt verwendete Arbeitsmappen in einem Bereichs Objekt auf

1. Durchlaufen Sie die Liste der zuletzt geöffneten Dateien, und zeigen Sie die Namen in Zellen relativ zu einem- <xref:Microsoft.Office.Interop.Excel.Range> Objekt an.

     [!code-csharp[Trin_VstcoreExcelAutomationAddIn#9](../vsto/codesnippet/CSharp/trin_vstcoreexcelautomationaddin/ThisAddIn.cs#9)]
     [!code-vb[Trin_VstcoreExcelAutomationAddIn#9](../vsto/codesnippet/VisualBasic/trin_vstcoreexcelautomationaddin/ThisAddIn.vb#9)]

## <a name="see-also"></a>Weitere Informationen
- [Arbeiten mit Arbeitsmappen](../vsto/working-with-workbooks.md)
- [Name Drange-Steuerelement](../vsto/namedrange-control.md)
- [Optionale Parameter in Office-Projektmappen](../vsto/optional-parameters-in-office-solutions.md)
