---
title: 'Vorgehensweise: Programmgesteuertes Löschen von Arbeitsblättern aus Arbeitsmappen'
ms.date: 02/02/2017
ms.topic: conceptual
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- workbooks, deleting worksheets
- worksheets, deleting
author: John-Hart
ms.author: johnhart
manager: jillfra
ms.workload:
- office
ms.openlocfilehash: 9ecc39e72a336c390c85f1caf2c80c6643acbb61
ms.sourcegitcommit: 47eeeeadd84c879636e9d48747b615de69384356
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 04/23/2019
ms.locfileid: "63412536"
---
# <a name="how-to-programmatically-delete-worksheets-from-workbooks"></a>Vorgehensweise: Programmgesteuertes Löschen von Arbeitsblättern aus Arbeitsmappen
  Sie können jedes beliebige Arbeitsblatt in einer Arbeitsmappe löschen. Verwenden Sie zum Löschen eines Arbeitsblatts das Arbeitsblatt-Hostelement, oder greifen Sie auf das Arbeitsblatt mithilfe der Sheets-Auflistung der Arbeitsmappe zu.

 [!INCLUDE[appliesto_xlalldocapp](../vsto/includes/appliesto-xlalldocapp-md.md)]

## <a name="use-the-worksheet-host-item"></a>Verwenden Sie das Arbeitsblatt-Hostelement
 Wenn das Arbeitsblatt zur Entwurfszeit in einer Anpassung auf Dokumentebene hinzugefügt wurde, verwenden Sie die Methode <xref:Microsoft.Office.Tools.Excel.Worksheet.Delete%2A>, um ein angegebenes Arbeitsblatt zu löschen. Der folgende Code löscht ein Arbeitsblatt aus einer Arbeitsmappe durch direktes Verweisen auf das Arbeitsblatt-Hostelement.

> [!IMPORTANT]
> Dieser Code wird nur in Projekten ausgeführt, die Sie mithilfe einer der folgenden Projektvorlagen erstellen:
>
> - Excel 2013-Arbeitsmappe
> - Excel 2013-Vorlage
> - Excel 2010-Arbeitsmappe
> - Excel 2010-Vorlage
>
>   Wenn Sie einen anderen Typ von Projekt diese Aufgabe ausführen möchten, müssen Sie hinzufügen, einen Verweis auf die **Microsoft.Office.Interop.Excel** Assembly vorliegt und Sie müssen Klassen aus dieser Assembly verwenden, um eine Arbeitsmappe öffnen und Löschen eines Arbeitsblatts. Weitere Informationen finden Sie unter [Vorgehensweise: Verweisen auf Office-Anwendungen durch primäre Interopassemblys](../vsto/how-to-target-office-applications-through-primary-interop-assemblies.md) und [Referenz für die primäre interop-Assembly von Excel 2010](http://go.microsoft.com/fwlink/?LinkId=189585).

### <a name="to-delete-a-worksheet-by-using-a-worksheet-host-item"></a>So löschen Sie ein Arbeitsblatt mithilfe eines Arbeitsblatt-Hostelements

1. Rufen Sie die <xref:Microsoft.Office.Tools.Excel.Worksheet.Delete%2A> -Methode von `Sheet1`auf.

     [!code-csharp[Trin_VstcoreExcelAutomation#17](../vsto/codesnippet/CSharp/Trin_VstcoreExcelAutomationCS/Sheet1.cs#17)]
     [!code-vb[Trin_VstcoreExcelAutomation#17](../vsto/codesnippet/VisualBasic/Trin_VstcoreExcelAutomation/Sheet1.vb#17)]

## <a name="use-the-sheets-collection-of-the-excel-workbook"></a>Verwenden der Sheets-Auflistung der Excel-Arbeitsmappe
 Greifen Sie auf Arbeitsblätter über die Microsoft Office Excel-Auflistung <xref:Microsoft.Office.Interop.Excel.Sheets> in den folgenden Fällen zu:

- Sie möchten ein Arbeitsblatt in einem VSTO-Add-In löschen.

- Das Arbeitsblatt, das Sie löschen möchten, wurde zur Laufzeit in einer Anpassung auf Dokumentebene erstellt.

  Der folgende Code Löscht ein Arbeitsblatt aus einer Arbeitsmappe durch Verweisen auf das Blatt über die Indexnummer des der **Blätter** Auflistung. Dieser Code geht davon aus, dass ein neues Arbeitsblatt programmgesteuert erstellt wurde.

> [!IMPORTANT]
> Wenn Sie einen anderen Typ von Projekt diese Aufgabe ausführen möchten, müssen Sie hinzufügen, einen Verweis auf die **Microsoft.Office.Interop.Excel** Assembly vorliegt und Sie müssen Klassen aus dieser Assembly verwenden, um eine Arbeitsmappe öffnen und Löschen eines Arbeitsblatts. Weitere Informationen finden Sie unter [Vorgehensweise: Verweisen auf Office-Anwendungen durch primäre Interopassemblys](../vsto/how-to-target-office-applications-through-primary-interop-assemblies.md) und [Referenz für die primäre interop-Assembly von Excel 2010](http://go.microsoft.com/fwlink/?LinkId=189585).

### <a name="to-delete-a-worksheet-by-using-the-sheets-collection-of-the-excel-workbook"></a>So löschen Sie ein Arbeitsblatt mithilfe der Sheets-Auflistung der Excel-Arbeitsmappe

1. Rufen Sie die Methode <xref:Microsoft.Office.Interop.Excel._Worksheet.Delete%2A> der Auflistung <xref:Microsoft.Office.Interop.Excel.Sheets> auf.

     [!code-csharp[Trin_VstcoreExcelAutomation#18](../vsto/codesnippet/CSharp/Trin_VstcoreExcelAutomationCS/Sheet1.cs#18)]
     [!code-vb[Trin_VstcoreExcelAutomation#18](../vsto/codesnippet/VisualBasic/Trin_VstcoreExcelAutomation/Sheet1.vb#18)]

## <a name="see-also"></a>Siehe auch
- [Arbeiten mit Arbeitsblättern](../vsto/working-with-worksheets.md)
- [Vorgehensweise: Programmgesteuertes Ausblenden von Arbeitsblättern](../vsto/how-to-programmatically-hide-worksheets.md)
- [Vorgehensweise: Programmgesteuertes Verschieben von Arbeitsblättern in Arbeitsmappen](../vsto/how-to-programmatically-move-worksheets-within-workbooks.md)
- [Vorgehensweise: Programmgesteuertes auswählen von Arbeitsblättern](../vsto/how-to-programmatically-select-worksheets.md)
- [Vorgehensweise: Programmgesteuertes fügen Sie neuer Arbeitsblätter zu Arbeitsmappen hinzu](../vsto/how-to-programmatically-add-new-worksheets-to-workbooks.md)
- [Arbeitsblatthostelement](../vsto/worksheet-host-item.md)
- [Globaler Zugriff auf Objekte in Office-Projekten](../vsto/global-access-to-objects-in-office-projects.md)
- [Einschränkungen für programmgesteuerte Aufgaben von Hostelementen und Hoststeuerelementen](../vsto/programmatic-limitations-of-host-items-and-host-controls.md)
