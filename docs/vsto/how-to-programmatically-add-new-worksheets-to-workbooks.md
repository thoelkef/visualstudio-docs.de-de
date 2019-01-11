---
title: 'Vorgehensweise: Programmgesteuertes fügen Sie neuer Arbeitsblätter zu Arbeitsmappen hinzu'
ms.date: 02/02/2017
ms.topic: conceptual
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- workbooks, adding worksheets
- workbooks, creating worksheets
- worksheets, creating
- worksheets, adding to workbooks
author: John-Hart
ms.author: johnhart
manager: douge
ms.workload:
- office
ms.openlocfilehash: 0c5cfd48cf65ea8eed18606377cde2092ddaf302
ms.sourcegitcommit: 37fb7075b0a65d2add3b137a5230767aa3266c74
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 01/02/2019
ms.locfileid: "53867669"
---
# <a name="how-to-programmatically-add-new-worksheets-to-workbooks"></a>Vorgehensweise: Programmgesteuertes fügen Sie neuer Arbeitsblätter zu Arbeitsmappen hinzu
  Sie können ein Arbeitsblatt programmgesteuert erstellen und das Arbeitsblatt dann zur Auflistung der Arbeitsblätter in der Arbeitsmappe hinzufügen.  
  
 [!INCLUDE[appliesto_xlalldocapp](../vsto/includes/appliesto-xlalldocapp-md.md)]  
  
## <a name="to-add-a-new-worksheet-to-a-workbook-in-a-document-level-customization"></a>So fügen Sie einer Arbeitsmappe in einer Anpassung auf Dokumentebene ein neues Arbeitsblatt hinzu  
  
1.  Verwenden Sie die <xref:Microsoft.Office.Interop.Excel.Worksheets.Add%2A>-Methode der <xref:Microsoft.Office.Interop.Excel.Sheets>-Auflistung.  
  
     [!code-csharp[Trin_VstcoreExcelAutomation#15](../vsto/codesnippet/CSharp/Trin_VstcoreExcelAutomationCS/Sheet1.cs#15)]
     [!code-vb[Trin_VstcoreExcelAutomation#15](../vsto/codesnippet/VisualBasic/Trin_VstcoreExcelAutomation/Sheet1.vb#15)]  
  
     Das neue Arbeitsblatt ist ein systemeigenes <xref:Microsoft.Office.Interop.Excel.Worksheet> -Objekt und kein Hostelement. Wenn Sie ein <xref:Microsoft.Office.Tools.Excel.Worksheet> -Hostelement hinzufügen möchten, sollten Sie das Arbeitsblatt zur Entwurfszeit hinzufügen.  
  
## <a name="to-add-a-new-worksheet-to-a-workbook-in-a-vsto-add-in"></a>So fügen Sie einer Arbeitsmappe ein neues Arbeitsblatt in einem VSTO-Add-In hinzu  
  
1.  Verwenden Sie die <xref:Microsoft.Office.Interop.Excel.Worksheets.Add%2A> -Methode der <xref:Microsoft.Office.Interop.Excel.Sheets> -Auflistung.  
  
     [!code-csharp[Trin_VstcoreExcelAutomationAddIn#11](../vsto/codesnippet/CSharp/trin_vstcoreexcelautomationaddin/ThisAddIn.cs#11)]
     [!code-vb[Trin_VstcoreExcelAutomationAddIn#11](../vsto/codesnippet/VisualBasic/trin_vstcoreexcelautomationaddin/ThisAddIn.vb#11)]  
  
     Das neue Arbeitsblatt ist ein systemeigenes <xref:Microsoft.Office.Interop.Excel.Worksheet> -Objekt und kein Hostelement. Sie können auch ein <xref:Microsoft.Office.Tools.Excel.Worksheet> -Hostelement vom systemeigenen <xref:Microsoft.Office.Interop.Excel.Worksheet> -Objekt generieren. Weitere Informationen finden Sie unter [Erweitern von Word-Dokumenten und Excel-Arbeitsmappen in VSTO-Add-Ins zur Laufzeit](../vsto/extending-word-documents-and-excel-workbooks-in-vsto-add-ins-at-run-time.md).  
  
## <a name="see-also"></a>Siehe auch  
 [Arbeiten mit Arbeitsblättern](../vsto/working-with-worksheets.md)   
 [Hostelemente und Host-Steuerelementen (Übersicht)](../vsto/host-items-and-host-controls-overview.md)   
 [Vorgehensweise: Programmgesteuertes Löschen von Arbeitsblättern aus Arbeitsmappen](../vsto/how-to-programmatically-delete-worksheets-from-workbooks.md)   
 [Vorgehensweise: Programmgesteuertes auswählen von Arbeitsblättern](../vsto/how-to-programmatically-select-worksheets.md)   
 [Automatisieren von Excel mithilfe von erweiterten Objekten](../vsto/automating-excel-by-using-extended-objects.md)   
 [Globaler Zugriff auf Objekte in Office-Projekten](../vsto/global-access-to-objects-in-office-projects.md)   
 [Optionaler Parameter in Office-Projektmappen](../vsto/optional-parameters-in-office-solutions.md)  
