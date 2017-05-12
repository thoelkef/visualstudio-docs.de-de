---
title: "Gewusst wie: Programmgesteuertes Ausw&#228;hlen von Arbeitsbl&#228;ttern"
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
  - "Excel-Projekte, Auswählen von Arbeitsblättern"
  - "Arbeitsblätter, Auswählen"
ms.assetid: 9e7cdb11-e825-4c9f-abcd-d46fd20dc5e0
caps.latest.revision: 44
author: "kempb"
ms.author: "kempb"
manager: "ghogen"
caps.handback.revision: 43
---
# Gewusst wie: Programmgesteuertes Ausw&#228;hlen von Arbeitsbl&#228;ttern
  Die Methode <xref:Microsoft.Office.Tools.Excel.Worksheet.Select%2A> wählt das angegebene Objekt aus. Die Auswahl des Benutzers wird in das neue Objekt verschoben.  Verwenden Sie die Methode <xref:Microsoft.Office.Tools.Excel.Worksheet.Activate%2A>, wenn Sie den Fokus auf das Objekt verschieben möchten, ohne die Benutzerauswahl zu ändern.  
  
 [!INCLUDE[appliesto_xlalldocapp](../vsto/includes/appliesto-xlalldocapp-md.md)]  
  
 Wenn Sie ein vorhandenes Arbeitsblatt in einem VSTO\-Add\-In auswählen möchten oder wenn das Arbeitsblatt zur Laufzeit in einer Anpassung auf Dokumentebene erstellt wurde, müssen Sie mit der Excel\-Auflistung <xref:Microsoft.Office.Interop.Excel.Sheets> der Excel\-Arbeitsmappe darauf zugreifen. Andernfalls können Sie direkt auf das <xref:Microsoft.Office.Tools.Excel.Worksheet>\-Hostelement zugreifen.  
  
## Verwenden das Arbeitsblatt\-Hostelements  
 Fügen Sie in einer Anpassung auf Dokumentebene der Datei **Sheet1.vb** oder **Sheet1.cs** den folgenden Code hinzu.  
  
#### So wählen Sie das erste Arbeitsblatt in einer Arbeitsmappe mithilfe eines Hostelements aus  
  
1.  Rufen Sie die <xref:Microsoft.Office.Tools.Excel.Worksheet.Select%2A>\-Methode von `Sheet1` auf.  
  
     [!code-csharp[Trin_VstcoreExcelAutomation#19](../snippets/csharp/VS_Snippets_OfficeSP/Trin_VstcoreExcelAutomation/CS/Sheet1.cs#19)]
     [!code-vb[Trin_VstcoreExcelAutomation#19](../snippets/visualbasic/VS_Snippets_OfficeSP/Trin_VstcoreExcelAutomation/VB/Sheet1.vb#19)]  
  
## Verwenden der Sheets\-Auflistung der Excel\-Arbeitsmappe  
 Greifen Sie auf das Arbeitsblatt mithilfe der Excel\-Auflistung <xref:Microsoft.Office.Interop.Excel.Sheets> zu.  
  
#### So wählen Sie das erste Arbeitsblatt in einer Arbeitsmappe mithilfe der Sheets\-Auflistung der Excel\-Arbeitsmappe aus  
  
1.  Rufen Sie die Methode <xref:Microsoft.Office.Interop.Excel.Sheets.Select%2A> der Auflistung <xref:Microsoft.Office.Interop.Excel.Sheets> auf, um das erste Arbeitsblatt der aktiven Arbeitsmappe auszuwählen.  
  
     [!code-csharp[Trin_VstcoreExcelAutomation#20](../snippets/csharp/VS_Snippets_OfficeSP/Trin_VstcoreExcelAutomation/CS/Sheet1.cs#20)]
     [!code-vb[Trin_VstcoreExcelAutomation#20](../snippets/visualbasic/VS_Snippets_OfficeSP/Trin_VstcoreExcelAutomation/VB/Sheet1.vb#20)]  
  
## Siehe auch  
 [Arbeiten mit Arbeitsblättern](../vsto/working-with-worksheets.md)   
 [Gewusst wie: Programmgesteuertes Drucken von Arbeitsblättern](../vsto/how-to-programmatically-print-worksheets.md)   
 [Gewusst wie: Programmgesteuertes Löschen von Arbeitsblättern aus Arbeitsmappen](../vsto/how-to-programmatically-delete-worksheets-from-workbooks.md)   
 [Gewusst wie: Programmgesteuertes Ausblenden von Arbeitsblättern](../vsto/how-to-programmatically-hide-worksheets.md)   
 [Gewusst wie: Programmgesteuertes Schützen von Arbeitsblättern](../vsto/how-to-programmatically-protect-worksheets.md)   
 [Arbeitsblatthostelement](../vsto/worksheet-host-item.md)   
 [Globaler Zugriff auf Objekte in Office-Projekten](../vsto/global-access-to-objects-in-office-projects.md)   
 [Programmgesteuerte Einschränkungen von Hostelementen und Hoststeuerelementen](../vsto/programmatic-limitations-of-host-items-and-host-controls.md)   
 [Optionale Parameter in Office-Lösungen](../vsto/optional-parameters-in-office-solutions.md)   
 [Übersicht über Hostelemente und Hoststeuerelemente](../vsto/host-items-and-host-controls-overview.md)  
  
  