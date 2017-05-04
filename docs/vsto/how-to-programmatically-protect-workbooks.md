---
title: "Gewusst wie: Programmgesteuertes Sch&#252;tzen von Arbeitsmappen | Microsoft Docs"
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
  - "Dokumentschutz, Hinzufügen zu Arbeitsmappen"
  - "Dokumentschutz, Entfernen von Arbeitsmappen"
  - "Dokumente [Office-Entwicklung in Visual Studio], Dokumentschutz"
  - "Arbeitsmappen, Kennwörter"
  - "Arbeitsmappen, Schutz"
  - "Arbeitsmappen, Aufheben des Schutzes"
ms.assetid: 553c67b9-e2a4-46b6-878c-5b4b4efa4589
caps.latest.revision: 43
author: "kempb"
ms.author: "kempb"
manager: "ghogen"
caps.handback.revision: 42
---
# Gewusst wie: Programmgesteuertes Sch&#252;tzen von Arbeitsmappen
  Sie können eine Arbeitsmappe in Microsoft Office Excel schützen, sodass Benutzer Arbeitsblätter weder hinzufügen noch löschen können. Der Schutz für die Arbeitsmappe kann programmgesteuert wieder aufgehoben werden.  Optional können Sie ein Kennwort angeben und festlegen, ob die Struktur \(Benutzer können keine Arbeitsblätter verschieben\) und die Fenster der Arbeitsmappe geschützt werden sollen.  
  
 [!INCLUDE[appliesto_xlalldocapp](../vsto/includes/appliesto-xlalldocapp-md.md)]  
  
 Das Schützen einer Arbeitsmappe verhindert nicht das Bearbeiten der Zellen durch Benutzer.  Zum Schützen der Daten müssen Sie die Arbeitsblätter schützen.  Weitere Informationen finden Sie unter [Gewusst wie: Programmgesteuertes Schützen von Arbeitsblättern](../vsto/how-to-programmatically-protect-worksheets.md).  
  
 In folgenden Codebeispielen wird eine Variable verwendet, die ein vom Benutzer angegebenes Kennwort enthält.  
  
## Schützen einer Arbeitsmappe, die ein Teil einer Anpassung auf Dokumentebene ist  
  
#### So schützen Sie eine Arbeitsmappe  
  
1.  Rufen Sie die <xref:Microsoft.Office.Tools.Excel.Workbook.Protect%2A>\-Methode der Arbeitsmappe auf, und geben Sie ein Kennwort an.  Um folgendes Codebeispiel zu verwenden, muss es in der `ThisWorkbook`\-Klasse statt in der Arbeitsblattklasse ausgeführt werden.  
  
     [!code-csharp[Trin_VstcoreExcelAutomation#10](../snippets/csharp/VS_Snippets_OfficeSP/Trin_VstcoreExcelAutomation/CS/ThisWorkbook.cs#10)]
     [!code-vb[Trin_VstcoreExcelAutomation#10](../snippets/visualbasic/VS_Snippets_OfficeSP/Trin_VstcoreExcelAutomation/VB/ThisWorkbook.vb#10)]  
  
#### So heben Sie den Schutz einer Arbeitsmappe auf  
  
1.  Rufen Sie die <xref:Microsoft.Office.Tools.Excel.Workbook.Unprotect%2A>\-Methode auf, und übergeben Sie ggf. ein Kennwort.  Um folgendes Codebeispiel zu verwenden, muss es in der `ThisWorkbook`\-Klasse statt in der Arbeitsblattklasse ausgeführt werden.  
  
     [!code-csharp[Trin_VstcoreExcelAutomation#11](../snippets/csharp/VS_Snippets_OfficeSP/Trin_VstcoreExcelAutomation/CS/ThisWorkbook.cs#11)]
     [!code-vb[Trin_VstcoreExcelAutomation#11](../snippets/visualbasic/VS_Snippets_OfficeSP/Trin_VstcoreExcelAutomation/VB/ThisWorkbook.vb#11)]  
  
## Schützen einer Arbeitsmappe mithilfe eines Add\-Ins auf Anwendungsebene  
  
#### So schützen Sie eine Arbeitsmappe  
  
1.  Rufen Sie die <xref:Microsoft.Office.Interop.Excel._Workbook.Protect%2A>\-Methode der Arbeitsmappe auf, und geben Sie ein Kennwort an.  In diesem Codebeispiel wird die aktive Projektmappe verwendet.  Wenn Sie dieses Beispiel verwenden möchten, führen Sie den Code von der `ThisAddIn`\-Klasse im Projekt aus.  
  
     [!code-csharp[Trin_VstcoreExcelAutomationAddIn#6](../snippets/csharp/VS_Snippets_OfficeSP/Trin_VstcoreExcelAutomationAddIn/CS/ThisAddIn.cs#6)]
     [!code-vb[Trin_VstcoreExcelAutomationAddIn#6](../snippets/visualbasic/VS_Snippets_OfficeSP/Trin_VstcoreExcelAutomationAddIn/VB/ThisAddIn.vb#6)]  
  
#### So heben Sie den Schutz einer Arbeitsmappe auf  
  
1.  Rufen Sie die <xref:Microsoft.Office.Interop.Excel._Workbook.Unprotect%2A>\-Methode der aktiven Arbeitsmappe auf, und übergeben Sie gegebenenfalls ein Kennwort.  Wenn Sie dieses Beispiel verwenden möchten, führen Sie den Code von der `ThisAddIn`\-Klasse im Projekt aus.  
  
     [!code-csharp[Trin_VstcoreExcelAutomationAddIn#7](../snippets/csharp/VS_Snippets_OfficeSP/Trin_VstcoreExcelAutomationAddIn/CS/ThisAddIn.cs#7)]
     [!code-vb[Trin_VstcoreExcelAutomationAddIn#7](../snippets/visualbasic/VS_Snippets_OfficeSP/Trin_VstcoreExcelAutomationAddIn/VB/ThisAddIn.vb#7)]  
  
## Siehe auch  
 [Arbeiten mit Arbeitsmappen](../vsto/working-with-workbooks.md)   
 [Gewusst wie: Programmgesteuertes Schützen von Arbeitsblättern](../vsto/how-to-programmatically-protect-worksheets.md)   
 [Gewusst wie: Programmgesteuertes Ausblenden von Arbeitsblättern](../vsto/how-to-programmatically-hide-worksheets.md)   
 [Optionale Parameter in Office-Lösungen](../vsto/optional-parameters-in-office-solutions.md)  
  
  