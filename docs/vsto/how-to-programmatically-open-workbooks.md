---
title: 'Gewusst wie: Programm gesteuertes Öffnen von Arbeitsmappen'
ms.date: 02/02/2017
ms.topic: how-to
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- workbooks, opening
- Excel [Office development in Visual Studio], opening workbooks
author: John-Hart
ms.author: johnhart
manager: jillfra
ms.workload:
- office
ms.openlocfilehash: 10a849d8545565e450cd099b32a9e3e8f7f11b56
ms.sourcegitcommit: b885f26e015d03eafe7c885040644a52bb071fae
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 06/30/2020
ms.locfileid: "85537903"
---
# <a name="how-to-programmatically-open-workbooks"></a>Gewusst wie: Programm gesteuertes Öffnen von Arbeitsmappen
  Die <xref:Microsoft.Office.Interop.Excel.Workbooks> -Auflistung in Microsoft Office Excel ermöglicht das Arbeiten mit allen geöffneten Arbeitsmappen und das Öffnen von-Arbeitsmappen.

 [!INCLUDE[appliesto_xlalldocapp](../vsto/includes/appliesto-xlalldocapp-md.md)]

## <a name="to-open-an-existing-workbook"></a>So öffnen Sie eine vorhandene Arbeitsmappe

1. Verwenden Sie die- <xref:Microsoft.Office.Interop.Excel.Workbooks.Open%2A> Methode der-Auflistung <xref:Microsoft.Office.Interop.Excel.Workbooks> , und übergeben Sie den Pfad zur Arbeitsmappe.

     [!code-csharp[Trin_VstcoreExcelAutomation#2](../vsto/codesnippet/CSharp/Trin_VstcoreExcelAutomationCS/Sheet1.cs#2)]
     [!code-vb[Trin_VstcoreExcelAutomation#2](../vsto/codesnippet/VisualBasic/Trin_VstcoreExcelAutomation/Sheet1.vb#2)]

## <a name="compile-the-code"></a>Kompilieren des Codes
 Für dieses Codebeispiel benötigen Sie Folgendes:

- Eine Arbeitsmappe mit dem Namen `YourWorkbook.xls` muss in einem Verzeichnis `Test` mit dem Namen auf Laufwerk C vorhanden sein.

## <a name="see-also"></a>Siehe auch
- [Arbeiten mit Arbeitsmappen](../vsto/working-with-workbooks.md)
- [Gewusst wie: Programm gesteuertes Öffnen von Textdateien als Arbeitsmappen](../vsto/how-to-programmatically-open-text-files-as-workbooks.md)
- [Vorgehensweise: Programm gesteuertes Erstellen neuer Arbeitsmappen](../vsto/how-to-programmatically-create-new-workbooks.md)
- [Vorgehensweise: Programm gesteuertes Speichern von Arbeitsmappen](../vsto/how-to-programmatically-save-workbooks.md)
- [Vorgehensweise: Programm gesteuertes schließen von Arbeitsmappen](../vsto/how-to-programmatically-close-workbooks.md)
- [Programmgesteuerte Einschränkungen von Host Elementen und Host Steuerelementen](../vsto/programmatic-limitations-of-host-items-and-host-controls.md)
- [Optionale Parameter in Office-Projektmappen](../vsto/optional-parameters-in-office-solutions.md)
- [Übersicht über Host Elemente und Host Steuerelemente](../vsto/host-items-and-host-controls-overview.md)
