---
title: "Gewusst wie: Programmgesteuertes Erstellen neuer Arbeitsmappen | Microsoft Docs"
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
  - "Excel [Office-Entwicklung in Visual Studio], Erstellen von Arbeitsmappen"
  - "Arbeitsmappen, Erstellen"
ms.assetid: be0196fe-7dc5-4811-b0cd-3c219731a3ff
caps.latest.revision: 48
author: "kempb"
ms.author: "kempb"
manager: "ghogen"
caps.handback.revision: 47
---
# Gewusst wie: Programmgesteuertes Erstellen neuer Arbeitsmappen
  Wenn Sie eine Arbeitsmappe programmgesteuert erstellen, ist diese ein systemeigenes <xref:Microsoft.Office.Interop.Excel.Workbook>\-Objekt und kein <xref:Microsoft.Office.Tools.Excel.Workbook>\-Hostelement.  
  
 [!INCLUDE[appliesto_xlalldocapp](../vsto/includes/appliesto-xlalldocapp-md.md)]  
  
 Sie können ein <xref:Microsoft.Office.Tools.Excel.Workbook>\-Hostelement für ein <xref:Microsoft.Office.Interop.Excel.Workbook>\-Objekt im VSTO\-Add\-In\-Projekt generieren.  Weitere Informationen finden Sie unter [Erweitern von Word-Dokumenten und Excel-Arbeitsmappen in VSTO-Add-Ins zur Laufzeit](../vsto/extending-word-documents-and-excel-workbooks-in-vsto-add-ins-at-run-time.md).  
  
### So erstellen Sie eine neue Arbeitsmappe  
  
1.  Verwenden Sie die <xref:Microsoft.Office.Interop.Excel.Workbooks.Add%2A> Methode der Auflistung <xref:Microsoft.Office.Interop.Excel.Workbooks>.  
  
     [!code-csharp[Trin_VstcoreExcelAutomation#1](../snippets/csharp/VS_Snippets_OfficeSP/Trin_VstcoreExcelAutomation/CS/Sheet1.cs#1)]
     [!code-vb[Trin_VstcoreExcelAutomation#1](../snippets/visualbasic/VS_Snippets_OfficeSP/Trin_VstcoreExcelAutomation/VB/Sheet1.vb#1)]  
  
    > [!NOTE]  
    >  Sie können eine Arbeitsmappe auf der Grundlage einer anderen Vorlage als der Standardvorlage erstellen: Übergeben Sie die Vorlage, die Sie verwenden möchten, als Parameter an die Methode <xref:Microsoft.Office.Interop.Excel.Workbooks.Add%2A>.  
  
## Siehe auch  
 [Erweitern von Word-Dokumenten und Excel-Arbeitsmappen in VSTO-Add-Ins zur Laufzeit](../vsto/extending-word-documents-and-excel-workbooks-in-vsto-add-ins-at-run-time.md)   
 [Hinzufügen von Steuerelementen zu Office-Dokumenten zur Laufzeit](../vsto/adding-controls-to-office-documents-at-run-time.md)   
 [Arbeiten mit Arbeitsmappen](../vsto/working-with-workbooks.md)   
 [Gewusst wie: Programmgesteuertes Öffnen von Arbeitsmappen](../vsto/how-to-programmatically-open-workbooks.md)   
 [Gewusst wie: Programmgesteuertes Speichern von Arbeitsmappen](../vsto/how-to-programmatically-save-workbooks.md)   
 [Gewusst wie: Programmgesteuertes Schließen von Arbeitsmappen](../vsto/how-to-programmatically-close-workbooks.md)   
 [Programmgesteuerte Einschränkungen von Hostelementen und Hoststeuerelementen](../vsto/programmatic-limitations-of-host-items-and-host-controls.md)   
 [Optionale Parameter in Office-Lösungen](../vsto/optional-parameters-in-office-solutions.md)   
 [Übersicht über Hostelemente und Hoststeuerelemente](../vsto/host-items-and-host-controls-overview.md)  
  
  