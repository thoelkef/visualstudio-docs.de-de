---
title: "Gewusst wie: Programmgesteuertes Kopieren von Arbeitsbl&#228;ttern"
ms.custom: ""
ms.date: "02/02/2017"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "office-development"
ms.tgt_pltfrm: ""
ms.topic: "article"
dev_langs: 
  - "VB"
  - "CSharp"
helpviewer_keywords: 
  - "Excel [Office-Entwicklung in Visual Studio], Kopieren von Arbeitsblättern"
  - "Arbeitsblätter, Kopieren"
ms.assetid: e49e03f5-7b2f-416b-b5fe-0965336c47e1
caps.latest.revision: 31
author: "kempb"
ms.author: "kempb"
manager: "ghogen"
caps.handback.revision: 30
---
# Gewusst wie: Programmgesteuertes Kopieren von Arbeitsbl&#228;ttern
  Sie können eine Kopie eines Arbeitsblatts erstellen und dieses Arbeitsblatt vor oder hinter einem vorhandenen Arbeitsblatt in der Arbeitsmappe einfügen.  Wenn Sie nicht angeben, wo das Arbeitsblatt eingefügt werden soll, erstellt Excel eine neue Arbeitsmappe, die das neue Arbeitsblatt enthält.  
  
 [!INCLUDE[appliesto_xlalldocapp](../vsto/includes/appliesto-xlalldocapp-md.md)]  
  
> [!NOTE]  
>  Unabhängig davon, ob das Arbeitsblatt programmgesteuert oder vom Endbenutzer manuell kopiert wird, ist kein Code hinter dem neuen Arbeitsblatt vorhanden, und Steuerelemente im neuen Arbeitsblatt funktionieren nicht.  Dies liegt daran, dass es sich bei dem neu kopierten Arbeitsblatt um ein <xref:Microsoft.Office.Interop.Excel.Worksheet>\-Objekt und kein <xref:Microsoft.Office.Tools.Excel.Worksheet>\-Hostelement handelt.  Windows Forms\-Steuerelemente und \-Hoststeuerelemente können nur Hostelementen hinzugefügt werden.  Weitere Informationen finden Sie unter [Programmgesteuerte Einschränkungen von Hostelementen und Hoststeuerelementen](../vsto/programmatic-limitations-of-host-items-and-host-controls.md).  
  
### So fügen Sie ein kopiertes Arbeitsblatt einer Arbeitsmappe in einer Anpassung auf Dokumentebene hinzu  
  
1.  Verwenden Sie die Methode <xref:Microsoft.Office.Interop.Excel.Worksheets.Copy%2A>, um das erste Arbeitsblatt in der aktuellen Arbeitsmappe zu kopieren, und platzieren Sie die Kopie hinter dem dritten Blatt.  
  
     [!code-csharp[Trin_VstcoreExcelAutomation#16](../snippets/csharp/VS_Snippets_OfficeSP/Trin_VstcoreExcelAutomation/CS/Sheet1.cs#16)]
     [!code-vb[Trin_VstcoreExcelAutomation#16](../snippets/visualbasic/VS_Snippets_OfficeSP/Trin_VstcoreExcelAutomation/VB/Sheet1.vb#16)]  
  
### So fügen Sie ein kopiertes Arbeitsblatt einer Arbeitsmappe in einem VSTO\-Add\-In hinzu  
  
1.  Verwenden Sie die Methode <xref:Microsoft.Office.Interop.Excel.Worksheets.Copy%2A>, um das erste Arbeitsblatt in der aktuellen Arbeitsmappe zu kopieren, und platzieren Sie die Kopie hinter dem dritten Blatt.  
  
     [!code-csharp[Trin_VstcoreExcelAutomationAddIn#12](../snippets/csharp/VS_Snippets_OfficeSP/Trin_VstcoreExcelAutomationAddIn/CS/ThisAddIn.cs#12)]
     [!code-vb[Trin_VstcoreExcelAutomationAddIn#12](../snippets/visualbasic/VS_Snippets_OfficeSP/Trin_VstcoreExcelAutomationAddIn/VB/ThisAddIn.vb#12)]  
  
## Siehe auch  
 [Arbeiten mit Arbeitsblättern](../vsto/working-with-worksheets.md)   
 [Übersicht über Hostelemente und Hoststeuerelemente](../vsto/host-items-and-host-controls-overview.md)   
 [Gewusst wie: Programmgesteuertes Hinzufügen neuer Arbeitsblätter zu Arbeitsmappen](../vsto/how-to-programmatically-add-new-worksheets-to-workbooks.md)   
 [Gewusst wie: Programmgesteuertes Löschen von Arbeitsblättern aus Arbeitsmappen](../vsto/how-to-programmatically-delete-worksheets-from-workbooks.md)   
 [Gewusst wie: Programmgesteuertes Auswählen von Arbeitsblättern](../vsto/how-to-programmatically-select-worksheets.md)   
 [Automatisieren von Excel mithilfe von erweiterten Objekten](../vsto/automating-excel-by-using-extended-objects.md)   
 [Globaler Zugriff auf Objekte in Office-Projekten](../vsto/global-access-to-objects-in-office-projects.md)   
 [Programmgesteuerte Einschränkungen von Hostelementen und Hoststeuerelementen](../vsto/programmatic-limitations-of-host-items-and-host-controls.md)   
 [Optionale Parameter in Office-Lösungen](../vsto/optional-parameters-in-office-solutions.md)  
  
  