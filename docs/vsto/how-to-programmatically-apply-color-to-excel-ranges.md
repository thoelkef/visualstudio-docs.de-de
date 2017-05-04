---
title: "Gewusst wie: Programmgesteuertes Anwenden von Farben auf Excel-Bereiche | Microsoft Docs"
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
  - "Farbe, Excel-Bereiche"
  - "Formatieren [Office-Entwicklung in Visual Studio]"
  - "Bereiche, Anwenden von Farbe"
ms.assetid: a9c40229-5308-459a-9216-7e13d82c7cb5
caps.latest.revision: 47
author: "kempb"
ms.author: "kempb"
manager: "ghogen"
caps.handback.revision: 46
---
# Gewusst wie: Programmgesteuertes Anwenden von Farben auf Excel-Bereiche
  Zum Anwenden von Textfarbe auf einen Zellenbereich verwenden Sie ein <xref:Microsoft.Office.Tools.Excel.NamedRange>\-Steuerelement oder ein systemeigenes Excel\-Bereichsobjekt.  
  
 [!INCLUDE[appliesto_xlalldocapp](../vsto/includes/appliesto-xlalldocapp-md.md)]  
  
## Verwenden eines NamedRange\-Steuerelements  
 Dieses Beispiel bezieht sich auf Anpassungen auf Dokumentebene.  
  
#### So legen Sie eine Farbe für ein NamedRange\-Steuerelement fest  
  
1.  Erstellen Sie in Zelle A1 ein <xref:Microsoft.Office.Tools.Excel.NamedRange>\-Steuerelement.  
  
     [!code-csharp[Trin_VstcoreExcelAutomation#65](../snippets/csharp/VS_Snippets_OfficeSP/Trin_VstcoreExcelAutomation/CS/Sheet1.cs#65)]
     [!code-vb[Trin_VstcoreExcelAutomation#65](../snippets/visualbasic/VS_Snippets_OfficeSP/Trin_VstcoreExcelAutomation/VB/Sheet1.vb#65)]  
  
2.  Legen Sie die Farbe des Textes im <xref:Microsoft.Office.Tools.Excel.NamedRange>\-Steuerelement fest.  
  
     [!code-csharp[Trin_VstcoreExcelAutomation#66](../snippets/csharp/VS_Snippets_OfficeSP/Trin_VstcoreExcelAutomation/CS/Sheet1.cs#66)]
     [!code-vb[Trin_VstcoreExcelAutomation#66](../snippets/visualbasic/VS_Snippets_OfficeSP/Trin_VstcoreExcelAutomation/VB/Sheet1.vb#66)]  
  
## Verwenden von systemeigenen Excel\-Bereichen  
  
#### So legen Sie eine Farbe für ein systemeigenes Excel\-Bereichsobjekt fest  
  
1.  Erstellen Sie einen Bereich in Zelle A1, und legen Sie dann die Farbe des Texts fest.  
  
     [!code-csharp[Trin_VstcoreExcelAutomation#67](../snippets/csharp/VS_Snippets_OfficeSP/Trin_VstcoreExcelAutomation/CS/Sheet1.cs#67)]
     [!code-vb[Trin_VstcoreExcelAutomation#67](../snippets/visualbasic/VS_Snippets_OfficeSP/Trin_VstcoreExcelAutomation/VB/Sheet1.vb#67)]  
  
## Siehe auch  
 [Arbeiten mit Bereichen](../vsto/working-with-ranges.md)   
 [NamedRange-Steuerelement](../vsto/namedrange-control.md)   
 [Gewusst wie: Programmgesteuertes Anwenden von Formaten auf Bereiche in Arbeitsmappen](../vsto/how-to-programmatically-apply-styles-to-ranges-in-workbooks.md)   
 [Gewusst wie: Programmgesteuertes Verweisen auf Arbeitsblattbereiche im Code](../vsto/how-to-programmatically-refer-to-worksheet-ranges-in-code.md)   
 [Automatisieren von Excel mithilfe von erweiterten Objekten](../vsto/automating-excel-by-using-extended-objects.md)   
 [Optionale Parameter in Office-Lösungen](../vsto/optional-parameters-in-office-solutions.md)  
  
  