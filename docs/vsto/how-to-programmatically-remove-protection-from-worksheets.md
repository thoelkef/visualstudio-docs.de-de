---
title: "Gewusst wie: Programmgesteuertes Aufheben des Schutzes von Arbeitsbl&#228;ttern"
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
  - "Arbeitsblätter, Aufheben des Schutzes"
  - "Dokumente [Office-Entwicklung in Visual Studio], Dokumentschutz"
  - "Dokumentschutz, Entfernen von Arbeitsblättern"
  - "Unprotect-Methode"
ms.assetid: 034688d2-eda7-4b4a-bcc2-d0999ff879a4
caps.latest.revision: 48
author: "kempb"
ms.author: "kempb"
manager: "ghogen"
caps.handback.revision: 47
---
# Gewusst wie: Programmgesteuertes Aufheben des Schutzes von Arbeitsbl&#228;ttern
  Sie können den Schutz programmgesteuert aus einem Microsoft Office Excel\-Arbeitsblatt entfernen.  
  
 [!INCLUDE[appliesto_xlalldocapp](../vsto/includes/appliesto-xlalldocapp-md.md)]  
  
 Im folgenden Beispiel wird die Variable `getPasswordFromUser` befindet, die ein vom Benutzer erhaltenes Kennwort enthält.  
  
### So heben Sie den Schutz eines Arbeitsblatts bei der Anpassung auf Dokumentebene auf  
  
1.  Rufen Sie die <xref:Microsoft.Office.Tools.Excel.Worksheet.Unprotect%2A>\-Methode des Arbeitsblatts auf, und übergeben Sie bei Bedarf das Kennwort. In diesem Beispiel wird davon ausgegangen, dass Sie mit einem Arbeitsblatt namens `Sheet1` arbeiten.  
  
     [!code-csharp[Trin_VstcoreExcelAutomation#28](../snippets/csharp/VS_Snippets_OfficeSP/Trin_VstcoreExcelAutomation/CS/Sheet1.cs#28)]
     [!code-vb[Trin_VstcoreExcelAutomation#28](../snippets/visualbasic/VS_Snippets_OfficeSP/Trin_VstcoreExcelAutomation/VB/Sheet1.vb#28)]  
  
### So heben Sie den Schutz für ein Arbeitsblatt in einem VSTO\-Add\-In auf  
  
1.  Rufen Sie die <xref:Microsoft.Office.Interop.Excel._Worksheet.Unprotect%2A>\-Methode des aktiven Arbeitsblatts auf, und übergeben Sie bei Bedarf das Kennwort.  
  
     [!code-csharp[Trin_VstcoreExcelAutomationAddIn#18](../snippets/csharp/VS_Snippets_OfficeSP/Trin_VstcoreExcelAutomationAddIn/CS/ThisAddIn.cs#18)]
     [!code-vb[Trin_VstcoreExcelAutomationAddIn#18](../snippets/visualbasic/VS_Snippets_OfficeSP/Trin_VstcoreExcelAutomationAddIn/VB/ThisAddIn.vb#18)]  
  
## Siehe auch  
 [Arbeiten mit Arbeitsblättern](../vsto/working-with-worksheets.md)   
 [Gewusst wie: Programmgesteuertes Schützen von Arbeitsblättern](../vsto/how-to-programmatically-protect-worksheets.md)   
 [Gewusst wie: Programmgesteuertes Schützen von Arbeitsmappen](../vsto/how-to-programmatically-protect-workbooks.md)   
 [Gewusst wie: Programmgesteuertes Ausblenden von Arbeitsblättern](../vsto/how-to-programmatically-hide-worksheets.md)   
 [Globaler Zugriff auf Objekte in Office-Projekten](../vsto/global-access-to-objects-in-office-projects.md)  
  
  