---
title: "Gewusst wie: Programmgesteuertes &#214;ffnen von Arbeitsmappen"
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
  - "Excel [Office-Entwicklung in Visual Studio], Öffnen von Arbeitsmappen"
  - "Arbeitsmappen, Öffnen"
ms.assetid: 06c0ac87-a2c6-4cc1-87be-39be0cb81c71
caps.latest.revision: 36
author: "kempb"
ms.author: "kempb"
manager: "ghogen"
caps.handback.revision: 36
---
# Gewusst wie: Programmgesteuertes &#214;ffnen von Arbeitsmappen
  Die <xref:Microsoft.Office.Interop.Excel.Workbooks>\-Auflistung in Microsoft Office Excel ermöglicht die Arbeit mit allen geöffneten Arbeitsmappen sowie das Öffnen von Arbeitsmappen.  
  
 [!INCLUDE[appliesto_xlalldocapp](../vsto/includes/appliesto-xlalldocapp-md.md)]  
  
### So öffnen Sie eine vorhandene Arbeitsmappe  
  
1.  Verwenden Sie die <xref:Microsoft.Office.Interop.Excel.Workbooks.Open%2A>\-Methode der <xref:Microsoft.Office.Interop.Excel.Workbooks>\-Auflistung, wobei Sie den Pfad an die Arbeitsmappe übergeben.  
  
     [!code-csharp[Trin_VstcoreExcelAutomation#2](../snippets/csharp/VS_Snippets_OfficeSP/Trin_VstcoreExcelAutomation/CS/Sheet1.cs#2)]
     [!code-vb[Trin_VstcoreExcelAutomation#2](../snippets/visualbasic/VS_Snippets_OfficeSP/Trin_VstcoreExcelAutomation/VB/Sheet1.vb#2)]  
  
## Kompilieren des Codes  
 Für dieses Codebeispiel benötigen Sie Folgendes:  
  
-   Eine Arbeitsmappe mit dem Namen `YourWorkbook.xls` muss in einem Verzeichnis mit dem Namen `Test` auf Laufwerk C: vorhanden sein.  
  
## Siehe auch  
 [Arbeiten mit Arbeitsmappen](../vsto/working-with-workbooks.md)   
 [Gewusst wie: Programmgesteuertes Öffnen von Textdateien als Arbeitsmappen](../vsto/how-to-programmatically-open-text-files-as-workbooks.md)   
 [Gewusst wie: Programmgesteuertes Erstellen neuer Arbeitsmappen](../vsto/how-to-programmatically-create-new-workbooks.md)   
 [Gewusst wie: Programmgesteuertes Speichern von Arbeitsmappen](../vsto/how-to-programmatically-save-workbooks.md)   
 [Gewusst wie: Programmgesteuertes Schließen von Arbeitsmappen](../vsto/how-to-programmatically-close-workbooks.md)   
 [Programmgesteuerte Einschränkungen von Hostelementen und Hoststeuerelementen](../vsto/programmatic-limitations-of-host-items-and-host-controls.md)   
 [Optionale Parameter in Office-Lösungen](../vsto/optional-parameters-in-office-solutions.md)   
 [Übersicht über Hostelemente und Hoststeuerelemente](../vsto/host-items-and-host-controls-overview.md)  
  
  