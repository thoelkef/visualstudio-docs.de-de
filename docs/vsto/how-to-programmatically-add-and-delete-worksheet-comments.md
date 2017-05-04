---
title: "Gewusst wie: Programmgesteuertes Hinzuf&#252;gen und L&#246;schen von Arbeitsblattkommentaren | Microsoft Docs"
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
  - "Bereiche, Kommentare"
  - "Arbeitsblätter, Kommentare"
  - "Kommentare, Arbeitsblätter"
ms.assetid: 3408ce22-a7b7-4e2b-bfc1-dc24d679ee73
caps.latest.revision: 53
author: "kempb"
ms.author: "kempb"
manager: "ghogen"
caps.handback.revision: 52
---
# Gewusst wie: Programmgesteuertes Hinzuf&#252;gen und L&#246;schen von Arbeitsblattkommentaren
  Sie können Kommentare in Microsoft Office Excel\-Arbeitsblättern programmgesteuert hinzufügen und löschen. Kommentare können nur einzelnen Zellen, nicht Bereichen mit mehreren Zellen hinzugefügt werden.  
  
 [!INCLUDE[appliesto_xlalldocapp](../vsto/includes/appliesto-xlalldocapp-md.md)]  
  
## Hinzufügen und Löschen eines Kommentars in einem Projekt auf Dokumentebene  
 Im folgendem Beispiel wird davon ausgegangen, dass sich ein in einer Zelle befindliches <xref:Microsoft.Office.Tools.Excel.NamedRange>\-Steuerelement namens `dateComment` auf dem Arbeitsblatt `Sheet1` befindet.  
  
#### So fügen Sie einem benannten Bereich einen neuen Kommentar hinzu  
  
1.  Rufen Sie die <xref:Microsoft.Office.Tools.Excel.NamedRange.AddComment%2A>\-Methode des <xref:Microsoft.Office.Tools.Excel.NamedRange>\-Steuerelements auf, und geben Sie den Kommentartext an. Dieser Code muss in die `Sheet1`\-Klasse eingefügt werden.  
  
     [!code-csharp[Trin_VstcoreExcelAutomation#30](../snippets/csharp/VS_Snippets_OfficeSP/Trin_VstcoreExcelAutomation/CS/Sheet1.cs#30)]
     [!code-vb[Trin_VstcoreExcelAutomation#30](../snippets/visualbasic/VS_Snippets_OfficeSP/Trin_VstcoreExcelAutomation/VB/Sheet1.vb#30)]  
  
#### So löschen Sie einen Kommentar aus einem benannten Bereich  
  
1.  Stellen Sie sicher, dass im Bereich ein Kommentar vorhanden ist, und löschen Sie ihn. Dieser Code muss in die `Sheet1`\-Klasse eingefügt werden.  
  
     [!code-csharp[Trin_VstcoreExcelAutomation#29](../snippets/csharp/VS_Snippets_OfficeSP/Trin_VstcoreExcelAutomation/CS/Sheet1.cs#29)]
     [!code-vb[Trin_VstcoreExcelAutomation#29](../snippets/visualbasic/VS_Snippets_OfficeSP/Trin_VstcoreExcelAutomation/VB/Sheet1.vb#29)]  
  
## Hinzufügen und Löschen eines Kommentars in einem VSTO\-Add\-In\-Projekt  
 Im folgendem Beispiel wird davon ausgegangen, dass sich ein in einer Zelle befindliches <xref:Microsoft.Office.Interop.Excel.Range>\-Steuerelement namens `dateComment` auf dem aktiven Arbeitsblatt befindet.  
  
#### So fügen Sie einem Excel\-Bereich einen neuen Kommentar hinzu  
  
1.  Rufen Sie die <xref:Microsoft.Office.Interop.Excel.Range.AddComment%2A>\-Methode des <xref:Microsoft.Office.Interop.Excel.Range>\-Steuerelements auf, und stellen Sie den Kommentartext bereit.  
  
     [!code-csharp[Trin_VstcoreExcelAutomationAddIn#20](../snippets/csharp/VS_Snippets_OfficeSP/Trin_VstcoreExcelAutomationAddIn/CS/ThisAddIn.cs#20)]
     [!code-vb[Trin_VstcoreExcelAutomationAddIn#20](../snippets/visualbasic/VS_Snippets_OfficeSP/Trin_VstcoreExcelAutomationAddIn/VB/ThisAddIn.vb#20)]  
  
#### So löschen Sie einen Kommentar aus einem Excel\-Bereich  
  
1.  Stellen Sie sicher, dass im Bereich ein Kommentar vorhanden ist, und löschen Sie ihn.  
  
     [!code-csharp[Trin_VstcoreExcelAutomationAddIn#19](../snippets/csharp/VS_Snippets_OfficeSP/Trin_VstcoreExcelAutomationAddIn/CS/ThisAddIn.cs#19)]
     [!code-vb[Trin_VstcoreExcelAutomationAddIn#19](../snippets/visualbasic/VS_Snippets_OfficeSP/Trin_VstcoreExcelAutomationAddIn/VB/ThisAddIn.vb#19)]  
  
## Siehe auch  
 [Arbeiten mit Arbeitsblättern](../vsto/working-with-worksheets.md)   
 [Gewusst wie: Programmgesteuertes Anzeigen von Arbeitsblattkommentaren](../vsto/how-to-programmatically-display-worksheet-comments.md)   
 [NamedRange-Steuerelement](../vsto/namedrange-control.md)  
  
  