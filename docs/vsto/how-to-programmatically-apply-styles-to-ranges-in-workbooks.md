---
title: "Gewusst wie: Programmgesteuertes Anwenden von Formaten auf Bereiche in Arbeitsmappen"
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
  - "Bereiche, Formatvorlagen"
  - "Formatvorlagen, Arbeitsmappenbereiche"
  - "Arbeitsmappen, Formatvorlagen"
ms.assetid: c7e781ed-f366-45bb-aeb6-69c10d19d842
caps.latest.revision: 51
author: "kempb"
ms.author: "kempb"
manager: "ghogen"
caps.handback.revision: 50
---
# Gewusst wie: Programmgesteuertes Anwenden von Formaten auf Bereiche in Arbeitsmappen
  Sie können benannte Formatvorlagen auf Bereiche in Arbeitsmappen anwenden. Excel stellt eine Reihe von vordefinierten Formaten bereit.  
  
 [!INCLUDE[appliesto_xlalldocapp](../vsto/includes/appliesto-xlalldocapp-md.md)]  
  
 Das Dialogfeld **Zellen formatieren** zeigt alle Optionen an, die Sie zum Formatieren von Zellen verwenden können, und jede dieser Optionen ist aus Ihrem Code verfügbar. Klicken Sie zum Anzeigen dieses Dialogfelds in Excel im Menü **Format** auf **Zellen**.  
  
### So wenden Sie eine Formatvorlage auf einen benannten Bereich in einer Anpassung auf Dokumentebene an  
  
1.  Erstellen eine neue Formatvorlage, und legen Sie ihre Attribute fest.  
  
     [!code-csharp[Trin_VstcoreExcelAutomation#53](../snippets/csharp/VS_Snippets_OfficeSP/Trin_VstcoreExcelAutomation/CS/Sheet1.cs#53)]
     [!code-vb[Trin_VstcoreExcelAutomation#53](../snippets/visualbasic/VS_Snippets_OfficeSP/Trin_VstcoreExcelAutomation/VB/Sheet1.vb#53)]  
  
2.  Erstellen Sie eine <xref:Microsoft.Office.Tools.Excel.NamedRange>\-Steuerelement, weisen Sie diesem Text zu, und wenden Sie dann die neue Formatvorlage an. Dieser Code muss in einer Sheet\-Klasse platziert werden und nicht in der `ThisWorkbook`\-Klasse.  
  
     [!code-csharp[Trin_VstcoreExcelAutomation#54](../snippets/csharp/VS_Snippets_OfficeSP/Trin_VstcoreExcelAutomation/CS/Sheet1.cs#54)]
     [!code-vb[Trin_VstcoreExcelAutomation#54](../snippets/visualbasic/VS_Snippets_OfficeSP/Trin_VstcoreExcelAutomation/VB/Sheet1.vb#54)]  
  
### So löschen Sie eine Formatvorlage aus einem benannten Bereich in einer Anpassung auf Dokumentebene  
  
1.  Wenden Sie die Formatvorlage "NORMAL.DOT" auf den Bereich an. Dieser Code muss in einer Sheet\-Klasse platziert werden und nicht in der `ThisWorkbook`\-Klasse.  
  
     [!code-csharp[Trin_VstcoreExcelAutomation#55](../snippets/csharp/VS_Snippets_OfficeSP/Trin_VstcoreExcelAutomation/CS/Sheet1.cs#55)]
     [!code-vb[Trin_VstcoreExcelAutomation#55](../snippets/visualbasic/VS_Snippets_OfficeSP/Trin_VstcoreExcelAutomation/VB/Sheet1.vb#55)]  
  
### So wenden Sie eine Formatvorlage auf einen benannten Bereich in einem VSTO\-Add\-In an  
  
1.  Erstellen eine neue Formatvorlage, und legen Sie ihre Attribute fest.  
  
     [!code-csharp[Trin_VstcoreExcelAutomationAddIn#28](../snippets/csharp/VS_Snippets_OfficeSP/Trin_VstcoreExcelAutomationAddIn/CS/ThisAddIn.cs#28)]
     [!code-vb[Trin_VstcoreExcelAutomationAddIn#28](../snippets/visualbasic/VS_Snippets_OfficeSP/Trin_VstcoreExcelAutomationAddIn/VB/ThisAddIn.vb#28)]  
  
2.  Erstellen Sie einen <xref:Microsoft.Office.Interop.Excel.Range>, weisen Sie diesem Text zu, und wenden Sie dann die neue Formatvorlage an.  
  
     [!code-csharp[Trin_VstcoreExcelAutomationAddIn#29](../snippets/csharp/VS_Snippets_OfficeSP/Trin_VstcoreExcelAutomationAddIn/CS/ThisAddIn.cs#29)]
     [!code-vb[Trin_VstcoreExcelAutomationAddIn#29](../snippets/visualbasic/VS_Snippets_OfficeSP/Trin_VstcoreExcelAutomationAddIn/VB/ThisAddIn.vb#29)]  
  
### So löschen Sie eine Formatvorlage aus einem benannten Bereich in einem VSTO\-Add\-In  
  
1.  Wenden Sie die Formatvorlage "NORMAL.DOT" auf den Bereich an.  
  
     [!code-csharp[Trin_VstcoreExcelAutomation#56](../snippets/csharp/VS_Snippets_OfficeSP/Trin_VstcoreExcelAutomation/CS/Sheet1.cs#56)]
     [!code-vb[Trin_VstcoreExcelAutomation#56](../snippets/visualbasic/VS_Snippets_OfficeSP/Trin_VstcoreExcelAutomation/VB/Sheet1.vb#56)]  
  
## Siehe auch  
 [Arbeiten mit Bereichen](../vsto/working-with-ranges.md)   
 [NamedRange-Steuerelement](../vsto/namedrange-control.md)   
 [Globaler Zugriff auf Objekte in Office-Projekten](../vsto/global-access-to-objects-in-office-projects.md)   
 [Optionale Parameter in Office-Lösungen](../vsto/optional-parameters-in-office-solutions.md)  
  
  