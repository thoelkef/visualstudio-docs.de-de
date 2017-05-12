---
title: "Gewusst wie: Programmgesteuertes &#196;ndern der Formatierung in Arbeitsblattzeilen, die ausgew&#228;hlte Zellen enthalten | Microsoft Docs"
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
  - "Formatieren [Office-Entwicklung in Visual Studio]"
  - "Zeilen [Office-Entwicklung in Visual Studio]"
  - "Arbeitsblätter, Ändern der Formatierung"
ms.assetid: c55cd488-98d1-46c6-9715-0e9212d178de
caps.latest.revision: 38
author: "kempb"
ms.author: "kempb"
manager: "ghogen"
caps.handback.revision: 37
---
# Gewusst wie: Programmgesteuertes &#196;ndern der Formatierung in Arbeitsblattzeilen, die ausgew&#228;hlte Zellen enthalten
  Sie können die Schriftart einer gesamten Zeile mit einer ausgewählten Zelle so ändern, dass der Text fett formatiert ist.  
  
 [!INCLUDE[appliesto_xlalldocapp](../vsto/includes/appliesto-xlalldocapp-md.md)]  
  
### So formatieren Sie die aktuelle Zeile fett und heben die Fettformatierung der Zeile wieder auf  
  
1.  Deklarieren Sie eine statische Variable, um die zuvor ausgewählte Zeile zu verfolgen.  
  
     [!code-csharp[Trin_VstcoreExcelAutomation#37](../snippets/csharp/VS_Snippets_OfficeSP/Trin_VstcoreExcelAutomation/CS/Sheet1.cs#37)]
     [!code-vb[Trin_VstcoreExcelAutomation#37](../snippets/visualbasic/VS_Snippets_OfficeSP/Trin_VstcoreExcelAutomation/VB/Sheet1.vb#37)]  
  
2.  Rufen Sie mithilfe der <xref:Microsoft.Office.Interop.Excel._Application.ActiveCell%2A>\-Eigenschaft einen Verweis auf die aktuelle Zelle ab.  
  
     [!code-csharp[Trin_VstcoreExcelAutomation#38](../snippets/csharp/VS_Snippets_OfficeSP/Trin_VstcoreExcelAutomation/CS/Sheet1.cs#38)]
     [!code-vb[Trin_VstcoreExcelAutomation#38](../snippets/visualbasic/VS_Snippets_OfficeSP/Trin_VstcoreExcelAutomation/VB/Sheet1.vb#38)]  
  
3.  Formatieren Sie mithilfe der <xref:Microsoft.Office.Interop.Excel.Range.EntireRow%2A>\-Eigenschaft der aktiven Zelle die aktuelle Zeile fett.  
  
     [!code-csharp[Trin_VstcoreExcelAutomation#39](../snippets/csharp/VS_Snippets_OfficeSP/Trin_VstcoreExcelAutomation/CS/Sheet1.cs#39)]
     [!code-vb[Trin_VstcoreExcelAutomation#39](../snippets/visualbasic/VS_Snippets_OfficeSP/Trin_VstcoreExcelAutomation/VB/Sheet1.vb#39)]  
  
4.  Vergewissern Sie sich, dass der aktuelle Wert von `previousRow` nicht 0 \(null\) ist.  Mit einem Wert von 0 \(null\) wird angegeben, dass dieser Code erstmalig durchlaufen wird.  
  
     [!code-csharp[Trin_VstcoreExcelAutomation#40](../snippets/csharp/VS_Snippets_OfficeSP/Trin_VstcoreExcelAutomation/CS/Sheet1.cs#40)]
     [!code-vb[Trin_VstcoreExcelAutomation#40](../snippets/visualbasic/VS_Snippets_OfficeSP/Trin_VstcoreExcelAutomation/VB/Sheet1.vb#40)]  
  
5.  Stellen Sie sicher, dass sich die aktuelle Zeile von der vorherigen Zeile unterscheidet.  
  
     [!code-csharp[Trin_VstcoreExcelAutomation#41](../snippets/csharp/VS_Snippets_OfficeSP/Trin_VstcoreExcelAutomation/CS/Sheet1.cs#41)]
     [!code-vb[Trin_VstcoreExcelAutomation#41](../snippets/visualbasic/VS_Snippets_OfficeSP/Trin_VstcoreExcelAutomation/VB/Sheet1.vb#41)]  
  
6.  Rufen Sie einen Verweis auf einen Bereich ab, der die zuvor ausgewählte Zeile darstellt, und legen Sie fest, dass diese Zeile nicht fett formatiert sein soll.  
  
     [!code-csharp[Trin_VstcoreExcelAutomation#42](../snippets/csharp/VS_Snippets_OfficeSP/Trin_VstcoreExcelAutomation/CS/Sheet1.cs#42)]
     [!code-vb[Trin_VstcoreExcelAutomation#42](../snippets/visualbasic/VS_Snippets_OfficeSP/Trin_VstcoreExcelAutomation/VB/Sheet1.vb#42)]  
  
7.  Speichern Sie die aktuelle Zeile, damit diese beim nächsten Durchlaufen die vorherige Zeile werden kann.  
  
     [!code-csharp[Trin_VstcoreExcelAutomation#43](../snippets/csharp/VS_Snippets_OfficeSP/Trin_VstcoreExcelAutomation/CS/Sheet1.cs#43)]
     [!code-vb[Trin_VstcoreExcelAutomation#43](../snippets/visualbasic/VS_Snippets_OfficeSP/Trin_VstcoreExcelAutomation/VB/Sheet1.vb#43)]  
  
 Im folgenden Beispiel wird die vollständige Methode veranschaulicht.  
  
## Beispiel  
 [!code-csharp[Trin_VstcoreExcelAutomation#36](../snippets/csharp/VS_Snippets_OfficeSP/Trin_VstcoreExcelAutomation/CS/Sheet1.cs#36)]
 [!code-vb[Trin_VstcoreExcelAutomation#36](../snippets/visualbasic/VS_Snippets_OfficeSP/Trin_VstcoreExcelAutomation/VB/Sheet1.vb#36)]  
  
## Siehe auch  
 [Arbeiten mit Arbeitsblättern](../vsto/working-with-worksheets.md)   
 [Gewusst wie: Programmgesteuertes Anwenden von Formaten auf Bereiche in Arbeitsmappen](../vsto/how-to-programmatically-apply-styles-to-ranges-in-workbooks.md)   
 [Gewusst wie: Programmgesteuertes Kopieren von Daten und Formatierungen zwischen Arbeitsblättern](../vsto/how-to-programmatically-copy-data-and-formatting-across-worksheets.md)   
 [Optionale Parameter in Office-Lösungen](../vsto/optional-parameters-in-office-solutions.md)  
  
  