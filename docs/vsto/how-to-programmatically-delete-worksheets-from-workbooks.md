---
title: "Vorgehensweise: Programmgesteuertes Löschen von Arbeitsblättern aus Arbeitsmappen | Microsoft Docs"
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
- workbooks, deleting worksheets
- worksheets, deleting
ms.assetid: c5ae99f0-806d-4320-a29c-75ad444fb996
caps.latest.revision: "48"
author: gewarren
ms.author: gewarren
manager: ghogen
ms.openlocfilehash: efa5c68555fbd9e309335d8c985c4f14f1b07b18
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 10/31/2017
---
# <a name="how-to-programmatically-delete-worksheets-from-workbooks"></a>Gewusst wie: Programmgesteuertes Löschen von Arbeitsblättern aus Arbeitsmappen
  Sie können jedes beliebige Arbeitsblatt in einer Arbeitsmappe löschen. Verwenden Sie zum Löschen eines Arbeitsblatts das Arbeitsblatt-Hostelement, oder greifen Sie auf das Arbeitsblatt mithilfe der Sheets-Auflistung der Arbeitsmappe zu.  
  
 [!INCLUDE[appliesto_xlalldocapp](../vsto/includes/appliesto-xlalldocapp-md.md)]  
  
## <a name="using-the-worksheet-host-item"></a>Verwenden das Arbeitsblatt-Hostelements  
 Wenn das Arbeitsblatt zur Entwurfszeit in einer Anpassung auf Dokumentebene hinzugefügt wurde, verwenden Sie die Methode <xref:Microsoft.Office.Tools.Excel.Worksheet.Delete%2A>, um ein angegebenes Arbeitsblatt zu löschen. Der folgende Code löscht ein Arbeitsblatt aus einer Arbeitsmappe durch direktes Verweisen auf das Arbeitsblatt-Hostelement.  
  
> [!IMPORTANT]  
>  Dieser Code wird nur in Projekten ausgeführt, die Sie mithilfe einer der folgenden Projektvorlagen erstellen:  
>   
>  -   Excel 2013-Arbeitsmappe  
> -   Excel 2013-Vorlage  
> -   Excel 2010-Arbeitsmappe  
> -   Excel 2010-Vorlage  
>   
>  Wenn Sie diese Aufgabe einem anderen Typ von Projekt ausführen möchten, müssen Sie hinzufügen, einen Verweis auf die **Microsoft.Office.Interop.Excel** Assembly vorliegt und Sie müssen Klassen aus dieser Assembly verwenden, um eine Arbeitsmappe öffnen und das Arbeitsblatt zu löschen. Weitere Informationen finden Sie unter [wie: Ziel Office-Anwendungen durch primäre Interopassemblys](../vsto/how-to-target-office-applications-through-primary-interop-assemblies.md) und [Excel 2010 Referenz für primäre Interopassemblys](http://go.microsoft.com/fwlink/?LinkId=189585).  
  
#### <a name="to-delete-a-worksheet-by-using-a-worksheet-host-item"></a>So löschen Sie ein Arbeitsblatt mithilfe eines Arbeitsblatt-Hostelements  
  
1.  Rufen Sie die <xref:Microsoft.Office.Tools.Excel.Worksheet.Delete%2A>-Methode von `Sheet1` auf.  
  
     [!code-csharp[Trin_VstcoreExcelAutomation#17](../vsto/codesnippet/CSharp/Trin_VstcoreExcelAutomationCS/Sheet1.cs#17)]
     [!code-vb[Trin_VstcoreExcelAutomation#17](../vsto/codesnippet/VisualBasic/Trin_VstcoreExcelAutomation/Sheet1.vb#17)]  
  
## <a name="using-the-sheets-collection-of-the-excel-workbook"></a>Verwenden der Sheets-Auflistung der Excel-Arbeitsmappe  
 Greifen Sie auf Arbeitsblätter über die Microsoft Office Excel-Auflistung <xref:Microsoft.Office.Interop.Excel.Sheets> in den folgenden Fällen zu:  
  
-   Sie möchten ein Arbeitsblatt in einem VSTO-Add-In löschen.  
  
-   Das Arbeitsblatt, das Sie löschen möchten, wurde zur Laufzeit in einer Anpassung auf Dokumentebene erstellt.  
  
 Der folgende Code Löscht ein Arbeitsblatt aus einer Arbeitsmappe durch Verweisen auf das Blatt über die Indexnummer der **Blätter** Auflistung. Dieser Code geht davon aus, dass ein neues Arbeitsblatt programmgesteuert erstellt wurde.  
  
> [!IMPORTANT]  
>  Wenn Sie diese Aufgabe einem anderen Typ von Projekt ausführen möchten, müssen Sie hinzufügen, einen Verweis auf die **Microsoft.Office.Interop.Excel** Assembly vorliegt und Sie müssen Klassen aus dieser Assembly verwenden, um eine Arbeitsmappe öffnen und das Arbeitsblatt zu löschen. Weitere Informationen finden Sie unter [wie: Ziel Office-Anwendungen durch primäre Interopassemblys](../vsto/how-to-target-office-applications-through-primary-interop-assemblies.md) und [Excel 2010 Referenz für primäre Interopassemblys](http://go.microsoft.com/fwlink/?LinkId=189585).  
  
#### <a name="to-delete-a-worksheet-by-using-the-sheets-collection-of-the-excel-workbook"></a>So löschen Sie ein Arbeitsblatt mithilfe der Sheets-Auflistung der Excel-Arbeitsmappe  
  
1.  Rufen Sie die Methode <xref:Microsoft.Office.Interop.Excel._Worksheet.Delete%2A> der Auflistung <xref:Microsoft.Office.Interop.Excel.Sheets> auf.  
  
     [!code-csharp[Trin_VstcoreExcelAutomation#18](../vsto/codesnippet/CSharp/Trin_VstcoreExcelAutomationCS/Sheet1.cs#18)]
     [!code-vb[Trin_VstcoreExcelAutomation#18](../vsto/codesnippet/VisualBasic/Trin_VstcoreExcelAutomation/Sheet1.vb#18)]  
  
## <a name="see-also"></a>Siehe auch  
 [Arbeiten mit Arbeitsblättern](../vsto/working-with-worksheets.md)   
 [Vorgehensweise: Programmgesteuertes Ausblenden von Arbeitsblättern](../vsto/how-to-programmatically-hide-worksheets.md)   
 [Vorgehensweise: Programmgesteuertes Verschieben von Arbeitsblättern in Arbeitsmappen](../vsto/how-to-programmatically-move-worksheets-within-workbooks.md)   
 [Vorgehensweise: Programmgesteuertes auswählen von Arbeitsblättern](../vsto/how-to-programmatically-select-worksheets.md)   
 [Vorgehensweise: Programmgesteuertes Hinzufügen neuer Arbeitsblätter zu Arbeitsmappen](../vsto/how-to-programmatically-add-new-worksheets-to-workbooks.md)   
 [Arbeitsblatt-Hostelements](../vsto/worksheet-host-item.md)   
 [Globaler Zugriff auf Objekte in Office-Projekten](../vsto/global-access-to-objects-in-office-projects.md)   
 [Programmgesteuerte Einschränkungen von Hostelementen und Hoststeuerelementen](../vsto/programmatic-limitations-of-host-items-and-host-controls.md)  
  
  