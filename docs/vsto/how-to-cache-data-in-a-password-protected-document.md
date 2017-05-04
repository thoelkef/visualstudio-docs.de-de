---
title: "Gewusst wie: Zwischenspeichern von Daten in einem kennwortgesch&#252;tzten Dokument | Microsoft Docs"
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
  - "Daten [Office-Entwicklung in Visual Studio], Zwischenspeichern"
  - "Zwischenspeichern von Daten [Office-Entwicklung in Visual Studio], Geschützte Dokumente"
  - "Datasets [Office-Entwicklung in Visual Studio], Zwischenspeichern"
ms.assetid: 91b865fc-bd01-438f-ac63-2fe3175bc2e8
caps.latest.revision: 23
author: "kempb"
ms.author: "kempb"
manager: "ghogen"
caps.handback.revision: 23
---
# Gewusst wie: Zwischenspeichern von Daten in einem kennwortgesch&#252;tzten Dokument
  Wenn Sie dem Datencache in einem kennwortgeschützten Dokument oder einer kennwortgeschützten Arbeitsmappe Daten hinzufügen, werden Änderungen an den zwischengespeicherten Daten nicht automatisch gespeichert.  Sie können Änderungen an den zwischengespeicherten Daten speichern, indem Sie zwei Methoden im Projekt überschreiben.  
  
 [!INCLUDE[appliesto_alldoc](../vsto/includes/appliesto-alldoc-md.md)]  
  
## Zwischenspeichern in Word\-Dokumenten  
  
#### So speichern Sie Daten in einem kennwortgeschützten Word\-Dokument zwischen  
  
1.  Markieren Sie in der `ThisDocument`\-Klasse ein öffentliches Feld oder eine Eigenschaft, die zwischengespeichert werden soll.  Weitere Informationen finden Sie unter [Zwischenspeichern von Daten](../vsto/caching-data.md).  
  
2.  Überschreiben Sie die <xref:Microsoft.Office.Tools.Word.DocumentBase.UnprotectDocument%2A>\-Methode in der `ThisDocument`\-Klasse, und entfernen Sie den Schutz des Dokuments.  
  
     Beim Speichern des Dokuments ruft die [!INCLUDE[vsto_runtime](../vsto/includes/vsto-runtime-md.md)] diese Methode auf, damit der Schutz des Dokuments aufgehoben werden kann.  So können Änderungen an den zwischengespeicherten Daten gespeichert werden.  
  
3.  Überschreiben Sie die <xref:Microsoft.Office.Tools.Word.DocumentBase.ProtectDocument%2A>\-Methode in der `ThisDocument`\-Klasse, und aktivieren Sie den Schutz des Dokuments erneut.  
  
     Nach dem Speichern des Dokuments ruft die [!INCLUDE[vsto_runtime](../vsto/includes/vsto-runtime-md.md)] diese Methode auf, damit der Schutz des Dokuments wieder aktiviert werden kann.  
  
### Beispiel  
 Im folgenden Codebeispiel wird gezeigt, wie Daten in einem kennwortgeschützten Word\-Dokument zwischengespeichert werden.  Bevor der Schutz mit der <xref:Microsoft.Office.Tools.Word.DocumentBase.UnprotectDocument%2A>\-Methode aufgehoben wird, wird der aktuelle <xref:Microsoft.Office.Tools.Word.Document.ProtectionType%2A>\-Wert gespeichert, sodass in der <xref:Microsoft.Office.Tools.Word.DocumentBase.ProtectDocument%2A>\-Methode der gleiche Schutztyp verwendet werden kann.  
  
 [!code-csharp[Trin_CachedDataProtectedDocument#1](../snippets/csharp/VS_Snippets_OfficeSP/Trin_CachedDataProtectedDocument/CS/ThisDocument.cs#1)]
 [!code-vb[Trin_CachedDataProtectedDocument#1](../snippets/visualbasic/VS_Snippets_OfficeSP/Trin_CachedDataProtectedDocument/VB/ThisDocument.vb#1)]  
  
### Kompilieren des Codes  
 Fügen Sie diesen Code der `ThisDocument`\-Klasse im Projekt hinzu.  Im Code wird davon ausgegangen, dass das Kennwort in einem Feld mit dem Namen `securelyStoredPassword` gespeichert wird.  
  
## Zwischenspeichern in Excel\-Arbeitsmappen  
 In Excel\-Projekten ist dieses Verfahren nur dann erforderlich, wenn die gesamte Arbeitsmappe mithilfe der <xref:Microsoft.Office.Tools.Excel.Workbook.Protect%2A>\-Methode mit einem Kennwort geschützt wird.  Dieses Verfahren ist nicht erforderlich, wenn nur eine bestimmte Arbeitsmappe mithilfe der <xref:Microsoft.Office.Tools.Excel.Worksheet.Protect%2A>\-Methode mit einem Kennwort geschützt wird.  
  
#### So speichern Sie Daten in einer kennwortgeschützten Excel\-Arbeitsmappe zwischen  
  
1.  Markieren Sie in der `ThisWorkbook`\-Klasse oder einer der `Sheet`*n*\-Klassen ein öffentliches Feld oder eine Eigenschaft, die zwischengespeichert werden soll.  Weitere Informationen finden Sie unter [Zwischenspeichern von Daten](../vsto/caching-data.md).  
  
2.  Überschreiben Sie die <xref:Microsoft.Office.Tools.Excel.WorkbookBase.UnprotectDocument%2A>\-Methode in der `ThisWorkbook`\-Klasse, und entfernen Sie den Schutz der Arbeitsmappe.  
  
     Beim Speichern der Arbeitsmappe ruft die [!INCLUDE[vsto_runtime](../vsto/includes/vsto-runtime-md.md)] diese Methode auf, damit der Schutz der Arbeitsmappe aufgehoben werden kann.  So können Änderungen an den zwischengespeicherten Daten gespeichert werden.  
  
3.  Überschreiben Sie die <xref:Microsoft.Office.Tools.Excel.WorkbookBase.ProtectDocument%2A>\-Methode in der `ThisWorkbook`\-Klasse, und aktivieren Sie den Schutz des Dokuments erneut.  
  
     Nach dem Speichern der Arbeitsmappe ruft die [!INCLUDE[vsto_runtime](../vsto/includes/vsto-runtime-md.md)] diese Methode auf, damit der Schutz der Arbeitsmappe wieder aktiviert werden kann.  
  
### Beispiel  
 Im folgenden Codebeispiel wird gezeigt, wie Daten in einer kennwortgeschützten Excel\-Arbeitsmappe zwischengespeichert werden.  Bevor der Schutz mit der <xref:Microsoft.Office.Tools.Excel.WorkbookBase.UnprotectDocument%2A>\-Methode aufgehoben wird, werden die aktuellen <xref:Microsoft.Office.Tools.Excel.Workbook.ProtectStructure%2A>\- und <xref:Microsoft.Office.Tools.Excel.Workbook.ProtectWindows%2A>\-Werte gespeichert, sodass dieselbe Art von Schutz später in der <xref:Microsoft.Office.Tools.Excel.WorkbookBase.ProtectDocument%2A>\-Methode verwendet werden kann.  
  
 [!code-csharp[Trin_CachedDataProtectedWorkbook#1](../snippets/csharp/VS_Snippets_OfficeSP/Trin_CachedDataProtectedWorkbook/CS/ThisWorkbook.cs#1)]
 [!code-vb[Trin_CachedDataProtectedWorkbook#1](../snippets/visualbasic/VS_Snippets_OfficeSP/Trin_CachedDataProtectedWorkbook/VB/ThisWorkbook.vb#1)]  
  
### Kompilieren des Codes  
 Fügen Sie diesen Code der `ThisWorkbook`\-Klasse im Projekt hinzu.  Im Code wird davon ausgegangen, dass das Kennwort in einem Feld mit dem Namen `securelyStoredPassword` gespeichert wird.  
  
## Siehe auch  
 [Zwischenspeichern von Daten](../vsto/caching-data.md)   
 [Gewusst wie: Zwischenspeichern von Daten zur Offlineverwendung oder zur Verwendung auf einem Server](../vsto/how-to-cache-data-for-use-offline-or-on-a-server.md)   
 [Gewusst wie: Programmgesteuertes Zwischenspeichern von Datenquellen in einem Office-Dokument](../vsto/how-to-programmatically-cache-a-data-source-in-an-office-document.md)  
  
  