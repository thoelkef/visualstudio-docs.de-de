---
title: 'Vorgehensweise: Programmgesteuertes Hinzufügen neuer Arbeitsblätter zu Arbeitsmappen | Microsoft Docs'
ms.custom: ''
ms.date: 02/02/2017
ms.technology:
- office-development
ms.topic: conceptual
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- workbooks, adding worksheets
- workbooks, creating worksheets
- worksheets, creating
- worksheets, adding to workbooks
author: TerryGLee
ms.author: tglee
manager: douge
ms.workload:
- office
ms.openlocfilehash: 934b3cb9b333c1cd9c551346eb7ac30edcd5e368
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/16/2018
---
# <a name="how-to-programmatically-add-new-worksheets-to-workbooks"></a>Gewusst wie: Programmgesteuertes Hinzufügen neuer Arbeitsblätter zu Arbeitsmappen
  Sie können ein Arbeitsblatt programmgesteuert erstellen und das Arbeitsblatt dann zur Auflistung der Arbeitsblätter in der Arbeitsmappe hinzufügen.  
  
 [!INCLUDE[appliesto_xlalldocapp](../vsto/includes/appliesto-xlalldocapp-md.md)]  
  
### <a name="to-add-a-new-worksheet-to-a-workbook-in-a-document-level-customization"></a>So fügen Sie einer Arbeitsmappe in einer Anpassung auf Dokumentebene ein neues Arbeitsblatt hinzu  
  
1.  Verwenden Sie die <xref:Microsoft.Office.Interop.Excel.Worksheets.Add%2A> -Methode der <xref:Microsoft.Office.Interop.Excel.Sheets> -Auflistung.  
  
     [!code-csharp[Trin_VstcoreExcelAutomation#15](../vsto/codesnippet/CSharp/Trin_VstcoreExcelAutomationCS/Sheet1.cs#15)]
     [!code-vb[Trin_VstcoreExcelAutomation#15](../vsto/codesnippet/VisualBasic/Trin_VstcoreExcelAutomation/Sheet1.vb#15)]  
  
     Das neue Arbeitsblatt ist ein systemeigenes <xref:Microsoft.Office.Interop.Excel.Worksheet> -Objekt und kein Hostelement. Wenn Sie ein <xref:Microsoft.Office.Tools.Excel.Worksheet> -Hostelement hinzufügen möchten, sollten Sie das Arbeitsblatt zur Entwurfszeit hinzufügen.  
  
### <a name="to-add-a-new-worksheet-to-a-workbook-in-a-vsto-add-in"></a>So fügen Sie einer Arbeitsmappe ein neues Arbeitsblatt in einem VSTO-Add-In hinzu  
  
1.  Verwenden Sie die <xref:Microsoft.Office.Interop.Excel.Worksheets.Add%2A> -Methode der <xref:Microsoft.Office.Interop.Excel.Sheets> -Auflistung.  
  
     [!code-csharp[Trin_VstcoreExcelAutomationAddIn#11](../vsto/codesnippet/CSharp/trin_vstcoreexcelautomationaddin/ThisAddIn.cs#11)]
     [!code-vb[Trin_VstcoreExcelAutomationAddIn#11](../vsto/codesnippet/VisualBasic/trin_vstcoreexcelautomationaddin/ThisAddIn.vb#11)]  
  
     Das neue Arbeitsblatt ist ein systemeigenes <xref:Microsoft.Office.Interop.Excel.Worksheet> -Objekt und kein Hostelement. Sie können auch ein <xref:Microsoft.Office.Tools.Excel.Worksheet> -Hostelement vom systemeigenen <xref:Microsoft.Office.Interop.Excel.Worksheet> -Objekt generieren. Weitere Informationen finden Sie unter [Erweitern von Word-Dokumenten und Excel-Arbeitsmappen in VSTO-Add-Ins zur Laufzeit](../vsto/extending-word-documents-and-excel-workbooks-in-vsto-add-ins-at-run-time.md).  
  
## <a name="see-also"></a>Siehe auch  
 [Arbeiten mit Arbeitsblättern](../vsto/working-with-worksheets.md)   
 [Übersicht über Hostelemente und Hoststeuerelemente](../vsto/host-items-and-host-controls-overview.md)   
 [Vorgehensweise: Programmgesteuertes Löschen von Arbeitsblättern aus Arbeitsmappen](../vsto/how-to-programmatically-delete-worksheets-from-workbooks.md)   
 [Vorgehensweise: Programmgesteuertes auswählen von Arbeitsblättern](../vsto/how-to-programmatically-select-worksheets.md)   
 [Automatisieren von Excel mithilfe von erweiterten Objekten](../vsto/automating-excel-by-using-extended-objects.md)   
 [Globaler Zugriff auf Objekte in Office-Projekten](../vsto/global-access-to-objects-in-office-projects.md)   
 [Optionale Parameter in Office-Projektmappen](../vsto/optional-parameters-in-office-solutions.md)  
  
  