---
title: 'Vorgehensweise: Programmgesteuertes Kopieren von Arbeitsblättern'
ms.date: 02/02/2017
ms.topic: conceptual
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- worksheets, copying
- Excel [Office development in Visual Studio], copying worksheets
author: John-Hart
ms.author: johnhart
manager: jillfra
ms.workload:
- office
ms.openlocfilehash: 64121ffcb69eb4bc3cdaa901ffe3d52014630779
ms.sourcegitcommit: c0202a77d4dc562cdc55dc2e6223c062281d9749
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 01/24/2019
ms.locfileid: "54865384"
---
# <a name="how-to-programmatically-copy-worksheets"></a>Vorgehensweise: Programmgesteuertes Kopieren von Arbeitsblättern
  Sie können eine Kopie eines Arbeitsblatts erstellen und dieses Arbeitsblatt vor oder hinter einem vorhandenen Arbeitsblatt in der Arbeitsmappe einfügen. Wenn Sie nicht angeben, wo das Arbeitsblatt eingefügt werden soll, erstellt Excel eine neue Arbeitsmappe, die das neue Arbeitsblatt enthält.  
  
 [!INCLUDE[appliesto_xlalldocapp](../vsto/includes/appliesto-xlalldocapp-md.md)]  
  
> [!NOTE]  
>  Unabhängig davon, ob das Arbeitsblatt programmgesteuert oder vom Endbenutzer manuell kopiert wird, ist kein Code hinter dem neuen Arbeitsblatt vorhanden, und Steuerelemente im neuen Arbeitsblatt funktionieren nicht. Dies liegt daran, dass es sich bei dem neu kopierten Arbeitsblatt um ein <xref:Microsoft.Office.Interop.Excel.Worksheet>-Objekt und kein <xref:Microsoft.Office.Tools.Excel.Worksheet>-Hostelement handelt. Windows Forms-Steuerelemente und -Hoststeuerelemente können nur Hostelementen hinzugefügt werden. Weitere Informationen finden Sie unter [programmgesteuerte Einschränkungen von Hostelementen und Hoststeuerelementen](../vsto/programmatic-limitations-of-host-items-and-host-controls.md).  
  
## <a name="to-add-a-copied-worksheet-to-a-workbook-in-a-document-level-customization"></a>So fügen Sie ein kopiertes Arbeitsblatt einer Arbeitsmappe in einer Anpassung auf Dokumentebene hinzu  
  
1.  Verwenden Sie die Methode <xref:Microsoft.Office.Interop.Excel.Worksheets.Copy%2A>, um das erste Arbeitsblatt in der aktuellen Arbeitsmappe zu kopieren, und platzieren Sie die Kopie hinter dem dritten Blatt.  
  
     [!code-csharp[Trin_VstcoreExcelAutomation#16](../vsto/codesnippet/CSharp/Trin_VstcoreExcelAutomationCS/Sheet1.cs#16)]
     [!code-vb[Trin_VstcoreExcelAutomation#16](../vsto/codesnippet/VisualBasic/Trin_VstcoreExcelAutomation/Sheet1.vb#16)]  
  
## <a name="to-add-a-copied-worksheet-to-a-workbook-in-a-vsto-add-in"></a>So fügen Sie ein kopiertes Arbeitsblatt einer Arbeitsmappe in einem VSTO-Add-In hinzu  
  
1.  Verwenden Sie die Methode <xref:Microsoft.Office.Interop.Excel.Worksheets.Copy%2A>, um das erste Arbeitsblatt in der aktuellen Arbeitsmappe zu kopieren, und platzieren Sie die Kopie hinter dem dritten Blatt.  
  
     [!code-csharp[Trin_VstcoreExcelAutomationAddIn#12](../vsto/codesnippet/CSharp/trin_vstcoreexcelautomationaddin/ThisAddIn.cs#12)]
     [!code-vb[Trin_VstcoreExcelAutomationAddIn#12](../vsto/codesnippet/VisualBasic/trin_vstcoreexcelautomationaddin/ThisAddIn.vb#12)]  
  
## <a name="see-also"></a>Siehe auch  
 [Arbeiten mit Arbeitsblättern](../vsto/working-with-worksheets.md)   
 [Hostelemente und Host-Steuerelementen (Übersicht)](../vsto/host-items-and-host-controls-overview.md)   
 [Vorgehensweise: Programmgesteuertes fügen Sie neuer Arbeitsblätter zu Arbeitsmappen hinzu](../vsto/how-to-programmatically-add-new-worksheets-to-workbooks.md)   
 [Vorgehensweise: Programmgesteuertes Löschen von Arbeitsblättern aus Arbeitsmappen](../vsto/how-to-programmatically-delete-worksheets-from-workbooks.md)   
 [Vorgehensweise: Programmgesteuertes auswählen von Arbeitsblättern](../vsto/how-to-programmatically-select-worksheets.md)   
 [Automatisieren von Excel mithilfe von erweiterten Objekten](../vsto/automating-excel-by-using-extended-objects.md)   
 [Globaler Zugriff auf Objekte in Office-Projekten](../vsto/global-access-to-objects-in-office-projects.md)   
 [Einschränkungen für programmgesteuerte Aufgaben von Hostelementen und Hoststeuerelementen](../vsto/programmatic-limitations-of-host-items-and-host-controls.md)   
 [Optionaler Parameter in Office-Projektmappen](../vsto/optional-parameters-in-office-solutions.md)  
