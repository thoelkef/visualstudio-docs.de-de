---
title: "Gewusst wie: Programmgesteuertes Hinzuf&#252;gen neuer Arbeitsbl&#228;tter zu Arbeitsmappen | Microsoft Docs"
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
  - "Arbeitsmappen, Hinzufügen von Arbeitsblättern"
  - "Arbeitsmappen, Erstellen von Arbeitsblättern"
  - "Arbeitsblätter, erstellen"
  - "Arbeitsblätter, Hinzufügen zu Arbeitsmappen"
ms.assetid: 19f0d815-51b2-406c-9f36-34aa0ec16b4a
caps.latest.revision: 52
author: "kempb"
ms.author: "kempb"
manager: "ghogen"
caps.handback.revision: 51
---
# Gewusst wie: Programmgesteuertes Hinzuf&#252;gen neuer Arbeitsbl&#228;tter zu Arbeitsmappen
  Sie können ein Arbeitsblatt programmgesteuert erstellen und das Arbeitsblatt dann zur Auflistung der Arbeitsblätter in der Arbeitsmappe hinzufügen.  
  
 [!INCLUDE[appliesto_xlalldocapp](../vsto/includes/appliesto-xlalldocapp-md.md)]  
  
### So fügen Sie einer Arbeitsmappe in einer Anpassung auf Dokumentebene ein neues Arbeitsblatt hinzu  
  
1.  Verwenden Sie die <xref:Microsoft.Office.Interop.Excel.Worksheets.Add%2A>\-Methode der <xref:Microsoft.Office.Interop.Excel.Sheets>\-Auflistung.  
  
     [!code-csharp[Trin_VstcoreExcelAutomation#15](../snippets/csharp/VS_Snippets_OfficeSP/Trin_VstcoreExcelAutomation/CS/Sheet1.cs#15)]
     [!code-vb[Trin_VstcoreExcelAutomation#15](../snippets/visualbasic/VS_Snippets_OfficeSP/Trin_VstcoreExcelAutomation/VB/Sheet1.vb#15)]  
  
     Das neue Arbeitsblatt ist ein systemeigenes <xref:Microsoft.Office.Interop.Excel.Worksheet>\-Objekt und kein Hostelement. Wenn Sie ein <xref:Microsoft.Office.Tools.Excel.Worksheet>\-Hostelement hinzufügen möchten, sollten Sie das Arbeitsblatt zur Entwurfszeit hinzufügen.  
  
### So fügen Sie einer Arbeitsmappe ein neues Arbeitsblatt in einem VSTO\-Add\-In hinzu  
  
1.  Verwenden Sie die <xref:Microsoft.Office.Interop.Excel.Worksheets.Add%2A>\-Methode der <xref:Microsoft.Office.Interop.Excel.Sheets>\-Auflistung.  
  
     [!code-csharp[Trin_VstcoreExcelAutomationAddIn#11](../snippets/csharp/VS_Snippets_OfficeSP/Trin_VstcoreExcelAutomationAddIn/CS/ThisAddIn.cs#11)]
     [!code-vb[Trin_VstcoreExcelAutomationAddIn#11](../snippets/visualbasic/VS_Snippets_OfficeSP/Trin_VstcoreExcelAutomationAddIn/VB/ThisAddIn.vb#11)]  
  
     Das neue Arbeitsblatt ist ein systemeigenes <xref:Microsoft.Office.Interop.Excel.Worksheet>\-Objekt und kein Hostelement. Sie können auch ein <xref:Microsoft.Office.Tools.Excel.Worksheet>\-Hostelement vom systemeigenen <xref:Microsoft.Office.Interop.Excel.Worksheet>\-Objekt generieren. Weitere Informationen finden Sie unter [Erweitern von Word-Dokumenten und Excel-Arbeitsmappen in VSTO-Add-Ins zur Laufzeit](../vsto/extending-word-documents-and-excel-workbooks-in-vsto-add-ins-at-run-time.md).  
  
## Siehe auch  
 [Arbeiten mit Arbeitsblättern](../vsto/working-with-worksheets.md)   
 [Übersicht über Hostelemente und Hoststeuerelemente](../vsto/host-items-and-host-controls-overview.md)   
 [Gewusst wie: Programmgesteuertes Löschen von Arbeitsblättern aus Arbeitsmappen](../vsto/how-to-programmatically-delete-worksheets-from-workbooks.md)   
 [Gewusst wie: Programmgesteuertes Auswählen von Arbeitsblättern](../vsto/how-to-programmatically-select-worksheets.md)   
 [Automatisieren von Excel mithilfe von erweiterten Objekten](../vsto/automating-excel-by-using-extended-objects.md)   
 [Globaler Zugriff auf Objekte in Office-Projekten](../vsto/global-access-to-objects-in-office-projects.md)   
 [Optionale Parameter in Office-Lösungen](../vsto/optional-parameters-in-office-solutions.md)  
  
  