---
title: "Gewusst wie: Programmgesteuertes Anzeigen von Arbeitsblattkommentaren"
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
  - "Arbeitsblätter, Kommentare"
  - "Kommentare, Arbeitsblätter"
ms.assetid: f5ce5e7f-bae4-40b7-951c-0f15b140aaf2
caps.latest.revision: 43
author: "kempb"
ms.author: "kempb"
manager: "ghogen"
caps.handback.revision: 42
---
# Gewusst wie: Programmgesteuertes Anzeigen von Arbeitsblattkommentaren
  Sie können Kommentare in Microsoft Office Excel\-Arbeitsblättern programmgesteuert anzeigen und ausblenden.  
  
 [!INCLUDE[appliesto_xlalldocapp](../vsto/includes/appliesto-xlalldocapp-md.md)]  
  
### So zeigen Sie alle Kommentare auf einem Arbeitsblatt in einer Anpassung auf Dokumentebene an  
  
1.  Legen Sie die <xref:Microsoft.Office.Interop.Excel.Comment.Visible%2A>\-Eigenschaft auf **true** fest, wenn Sie Kommentare anzeigen möchten, andernfalls auf **false**. Dieser Code muss in einer Sheet\-Klasse platziert werden und nicht in der `ThisWorkbook`\-Klasse.  
  
     [!code-csharp[Trin_VstcoreExcelAutomation#31](../snippets/csharp/VS_Snippets_OfficeSP/Trin_VstcoreExcelAutomation/CS/Sheet1.cs#31)]
     [!code-vb[Trin_VstcoreExcelAutomation#31](../snippets/visualbasic/VS_Snippets_OfficeSP/Trin_VstcoreExcelAutomation/VB/Sheet1.vb#31)]  
  
### So zeigen Sie alle Kommentare auf einem Arbeitsblatt in einem VSTO\-Add\-In auf Anwendungsebene an  
  
1.  Legen Sie die <xref:Microsoft.Office.Interop.Excel.Comment.Visible%2A>\-Eigenschaft auf **true** fest, wenn Sie Kommentare anzeigen möchten, andernfalls auf **false**.  
  
     [!code-csharp[Trin_VstcoreExcelAutomationAddIn#21](../snippets/csharp/VS_Snippets_OfficeSP/Trin_VstcoreExcelAutomationAddIn/CS/ThisAddIn.cs#21)]
     [!code-vb[Trin_VstcoreExcelAutomationAddIn#21](../snippets/visualbasic/VS_Snippets_OfficeSP/Trin_VstcoreExcelAutomationAddIn/VB/ThisAddIn.vb#21)]  
  
## Siehe auch  
 [Arbeiten mit Arbeitsblättern](../vsto/working-with-worksheets.md)   
 [Gewusst wie: Programmgesteuertes Hinzufügen und Löschen von Arbeitsblattkommentaren](../vsto/how-to-programmatically-add-and-delete-worksheet-comments.md)   
 [Übersicht über Hostelemente und Hoststeuerelemente](../vsto/host-items-and-host-controls-overview.md)  
  
  