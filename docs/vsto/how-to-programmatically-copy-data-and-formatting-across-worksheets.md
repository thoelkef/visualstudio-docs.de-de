---
title: "Gewusst wie: Programmgesteuertes Kopieren von Daten und Formatierungen zwischen Arbeitsbl&#228;ttern | Microsoft Docs"
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
  - "Kopieren von Daten, Office-Entwicklung in Visual Studio"
  - "Daten [Office-Entwicklung in Visual Studio], Kopieren zwischen Arbeitsblättern"
  - "Formatieren [Office-Entwicklung in Visual Studio]"
  - "Arbeitsblätter, Kopieren von Daten"
ms.assetid: eed7dbaf-bdb5-4330-ba2e-5f3d50817eca
caps.latest.revision: 37
author: "kempb"
ms.author: "kempb"
manager: "ghogen"
caps.handback.revision: 37
---
# Gewusst wie: Programmgesteuertes Kopieren von Daten und Formatierungen zwischen Arbeitsbl&#228;ttern
  Mit der <xref:Microsoft.Office.Interop.Excel.Worksheets.FillAcrossSheets%2A>\-Methode können Sie Daten von einem Bereich eines Blatts in alle anderen Blätter einer Arbeitsmappe kopieren.  Geben Sie einen Bereich an, und legen Sie fest, ob Daten, Formatierungsinformationen oder beides kopiert werden sollen.  
  
 [!INCLUDE[appliesto_xlalldocapp](../vsto/includes/appliesto-xlalldocapp-md.md)]  
  
## Beispiel  
 [!code-csharp[Trin_VstcoreExcelAutomation#44](../snippets/csharp/VS_Snippets_OfficeSP/Trin_VstcoreExcelAutomation/CS/Sheet1.cs#44)]
 [!code-vb[Trin_VstcoreExcelAutomation#44](../snippets/visualbasic/VS_Snippets_OfficeSP/Trin_VstcoreExcelAutomation/VB/Sheet1.vb#44)]  
  
## Kompilieren des Codes  
 In diesem Beispiel wird ein Bereich mit der Bezeichnung `rangeData` in einem Arbeitsblatt vorausgesetzt.  
  
## Siehe auch  
 [Arbeiten mit Arbeitsblättern](../vsto/working-with-worksheets.md)   
 [Gewusst wie: Programmgesteuertes Hinzufügen neuer Arbeitsblätter zu Arbeitsmappen](../vsto/how-to-programmatically-add-new-worksheets-to-workbooks.md)   
 [Gewusst wie: Programmgesteuertes Ändern der Formatierung in Arbeitsblattzeilen, die ausgewählte Zellen enthalten](../vsto/how-to-programmatically-change-formatting-in-worksheet-rows-containing-selected-cells.md)   
 [Optionale Parameter in Office-Lösungen](../vsto/optional-parameters-in-office-solutions.md)  
  
  