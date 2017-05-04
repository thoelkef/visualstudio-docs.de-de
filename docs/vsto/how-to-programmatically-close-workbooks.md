---
title: "Gewusst wie: Programmgesteuertes Schlie&#223;en von Arbeitsmappen | Microsoft Docs"
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
  - "Arbeitsmappen, schließen"
  - "Excel [Office-Entwicklung in Visual Studio], Schließen von Arbeitsmappen"
ms.assetid: 50709caf-2ad8-4843-987c-9a34c8c1e4fe
caps.latest.revision: 52
author: "kempb"
ms.author: "kempb"
manager: "ghogen"
caps.handback.revision: 51
---
# Gewusst wie: Programmgesteuertes Schlie&#223;en von Arbeitsmappen
  Sie können die aktive Arbeitsmappe schließen, oder eine Arbeitsmappe angeben, die geschlossen werden soll.  
  
 [!INCLUDE[appliesto_xlalldocapp](../vsto/includes/appliesto-xlalldocapp-md.md)]  
  
## Schließen der aktiven Arbeitsmappe  
 Es gibt zwei Verfahren zum Schließen der aktiven Arbeitsmappe: eine für Anpassungen auf Dokumentebene und eine für VSTO\-Add\-Ins.  
  
#### So schließen Sie die aktive Arbeitsmappe in einer Anpassung auf Dokumentebene  
  
1.  Rufen Sie die <xref:Microsoft.Office.Tools.Excel.Workbook.Close%2A>\-Methode auf, um die der Anpassung zugeordnete Arbeitsmappe zu schließen. Um das folgende Codebeispiel zu verwenden, führen sie es in der `Sheet1`\-Klasse in einem Projekt auf Dokumentebene für Excel aus.  
  
     [!code-csharp[Trin_VstcoreExcelAutomation#3](../snippets/csharp/VS_Snippets_OfficeSP/Trin_VstcoreExcelAutomation/CS/Sheet1.cs#3)]
     [!code-vb[Trin_VstcoreExcelAutomation#3](../snippets/visualbasic/VS_Snippets_OfficeSP/Trin_VstcoreExcelAutomation/VB/Sheet1.vb#3)]  
  
#### So schließen Sie die aktive Arbeitsmappe in einem VSTO\-Add\-In  
  
1.  Rufen Sie die <xref:Microsoft.Office.Interop.Excel._Workbook.Close%2A>\-Methode auf, um die aktive Arbeitsmappe zu schließen. Um das folgende Codebeispiel zu verwenden, führen sie es in der `ThisAddIn`\-Klasse in einem VSTO\-Add\-In\-Projekt für Excel aus.  
  
     [!code-csharp[Trin_VstcoreExcelAutomationAddIn#1](../snippets/csharp/VS_Snippets_OfficeSP/Trin_VstcoreExcelAutomationAddIn/CS/ThisAddIn.cs#1)]
     [!code-vb[Trin_VstcoreExcelAutomationAddIn#1](../snippets/visualbasic/VS_Snippets_OfficeSP/Trin_VstcoreExcelAutomationAddIn/VB/ThisAddIn.vb#1)]  
  
## Schließen einer namentlich angegebenen Arbeitsmappe  
 Das Schließen einer namentlich angegebenen Arbeitsmappe erfolgt bei VSTO\-Add\-Ins und Anpassungen auf Dokumentebene auf die gleiche Weise.  
  
#### So schließen Sie eine namentlich angegebene Arbeitsmappe  
  
1.  Geben Sie den Namen der Arbeitsmappe als Argument für die <xref:Microsoft.Office.Interop.Excel.Workbooks>\-Auflistung an. Im folgenden Codebeispiel wird davon ausgegangen, dass eine Arbeitsmappe mit dem Namen **NewWorkbook** in Excel geöffnet ist.  
  
     [!code-csharp[Trin_VstcoreExcelAutomationAddIn#2](../snippets/csharp/VS_Snippets_OfficeSP/Trin_VstcoreExcelAutomationAddIn/CS/ThisAddIn.cs#2)]
     [!code-vb[Trin_VstcoreExcelAutomationAddIn#2](../snippets/visualbasic/VS_Snippets_OfficeSP/Trin_VstcoreExcelAutomationAddIn/VB/ThisAddIn.vb#2)]  
  
## Siehe auch  
 [Arbeiten mit Arbeitsmappen](../vsto/working-with-workbooks.md)   
 [Gewusst wie: Programmgesteuertes Speichern von Arbeitsmappen](../vsto/how-to-programmatically-save-workbooks.md)   
 [Gewusst wie: Programmgesteuertes Öffnen von Arbeitsmappen](../vsto/how-to-programmatically-open-workbooks.md)   
 [Programmgesteuerte Einschränkungen von Hostelementen und Hoststeuerelementen](../vsto/programmatic-limitations-of-host-items-and-host-controls.md)   
 [Optionale Parameter in Office-Lösungen](../vsto/optional-parameters-in-office-solutions.md)   
 [Übersicht über Hostelemente und Hoststeuerelemente](../vsto/host-items-and-host-controls-overview.md)  
  
  