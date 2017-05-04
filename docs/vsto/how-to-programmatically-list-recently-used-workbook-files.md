---
title: "Gewusst wie: Programmgesteuertes Auflisten zuletzt verwendeter Arbeitsmappendateien | Microsoft Docs"
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
  - "Excel [Office-Entwicklung in Visual Studio], Liste der zuletzt verwendeten Dateien"
  - "Liste zuletzt verwendeter Dateien, Excel"
  - "RecentFiles-Eigenschaft"
  - "Arbeitsmappen, Liste der zuletzt verwendeten"
ms.assetid: 210a3753-4845-4875-b34a-a30d3a1299b3
caps.latest.revision: 42
author: "kempb"
ms.author: "kempb"
manager: "ghogen"
caps.handback.revision: 42
---
# Gewusst wie: Programmgesteuertes Auflisten zuletzt verwendeter Arbeitsmappendateien
  Die <xref:Microsoft.Office.Interop.Excel._Application.RecentFiles%2A>\-Eigenschaft gibt eine Auflistung mit den Namen aller Dateien zurück, die in der Microsoft Office Excel\-Liste der zuletzt verwendeten Dateien angezeigt werden.  Die Länge der Liste variiert entsprechend der vom Benutzer ausgewählten Anzahl aufzuführender Dateien.  Sie können sich die Ergebnisse in einem Bereich anzeigen lassen.  
  
 [!INCLUDE[appliesto_xlalldocapp](../vsto/includes/appliesto-xlalldocapp-md.md)]  
  
### So listen Sie zuletzt verwendete Arbeitsmappen in einem Bereichsobjekt auf  
  
1.  Durchlaufen Sie die Liste der zuletzt verwendeten Dateien, und lassen Sie sich die Namen in den Zellen relativ zu einem <xref:Microsoft.Office.Interop.Excel.Range>\-Objekt anzeigen.  
  
     [!code-csharp[Trin_VstcoreExcelAutomationAddIn#9](../snippets/csharp/VS_Snippets_OfficeSP/Trin_VstcoreExcelAutomationAddIn/CS/ThisAddIn.cs#9)]
     [!code-vb[Trin_VstcoreExcelAutomationAddIn#9](../snippets/visualbasic/VS_Snippets_OfficeSP/Trin_VstcoreExcelAutomationAddIn/VB/ThisAddIn.vb#9)]  
  
## Siehe auch  
 [Arbeiten mit Arbeitsmappen](../vsto/working-with-workbooks.md)   
 [NamedRange-Steuerelement](../vsto/namedrange-control.md)   
 [Optionale Parameter in Office-Lösungen](../vsto/optional-parameters-in-office-solutions.md)  
  
  