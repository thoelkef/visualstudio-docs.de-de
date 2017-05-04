---
title: "Gewusst wie: Programmgesteuertes Hinzuf&#252;gen von Text und Formatierungen zu Zellen in Word-Tabellen | Microsoft Docs"
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
  - "Zellen, Hinzufügen von Text und Formatierungen"
  - "Formatieren [Office-Entwicklung in Visual Studio]"
  - "Tabellen [Office-Entwicklung in Visual Studio], Hinzufügen von Text und Formatierungen"
  - "Text [Office-Entwicklung in Visual Studio], Hinzufügen zu Word-Tabellen"
ms.assetid: 3df6492a-dc9c-43ac-8fc3-0f944edd88b2
caps.latest.revision: 40
author: "kempb"
ms.author: "kempb"
manager: "ghogen"
caps.handback.revision: 39
---
# Gewusst wie: Programmgesteuertes Hinzuf&#252;gen von Text und Formatierungen zu Zellen in Word-Tabellen
  Jede Tabelle besteht aus einer Auflistung von Zellen.  Jedes einzelne <xref:Microsoft.Office.Interop.Word.Cell>\-Objekt stellt eine Zelle in der Tabelle dar.  Auf die einzelnen Zellen wird anhand ihrer Position in der Tabelle verwiesen.  In diesem Beispiel wird auf die Zelle in der ersten Zeile und der ersten Spalte der Tabelle verwiesen, der Zelle Text hinzugefügt und Formatierung angewendet.  
  
 [!INCLUDE[appliesto_wdalldocapp](../vsto/includes/appliesto-wdalldocapp-md.md)]  
  
### So fügen Sie Zellen Text und Formatierung hinzu  
  
1.  Verweisen Sie anhand der Position in der Tabelle auf die Zelle, fügen Sie der Zelle Text hinzu, und wenden Sie die Formatierung an.  
  
     Das folgende Codebeispiel kann in einer Anpassung auf Dokumentebene verwendet werden.  Wenn Sie dieses Beispiel verwenden möchten, führen Sie es von der `ThisDocument`\-Klasse Ihres Projekts aus.  
  
     [!code-csharp[Trin_VstcoreWordAutomation#97](../snippets/csharp/VS_Snippets_OfficeSP/Trin_VstcoreWordAutomation/CS/ThisDocument.cs#97)]
     [!code-vb[Trin_VstcoreWordAutomation#97](../snippets/visualbasic/VS_Snippets_OfficeSP/Trin_VstcoreWordAutomation/VB/ThisDocument.vb#97)]  
  
     Das folgende Codebeispiel kann in einem VSTO\-Add\-In verwendet werden.  In diesem Beispiel wird das aktive Dokument verwendet.  Wenn Sie dieses Beispiel verwenden möchten, führen Sie es von der `ThisAddIn`\-Klasse Ihres Projekts aus.  
  
     [!code-csharp[Trin_VstcoreWordAutomationAddIn#97](../snippets/csharp/VS_Snippets_OfficeSP/Trin_VstcoreWordAutomationAddIn/CS/ThisAddIn.cs#97)]
     [!code-vb[Trin_VstcoreWordAutomationAddIn#97](../snippets/visualbasic/VS_Snippets_OfficeSP/Trin_VstcoreWordAutomationAddIn/VB/ThisAddIn.vb#97)]  
  
## Siehe auch  
 [Gewusst wie: Programmgesteuertes Erstellen von Word-Tabellen](../vsto/how-to-programmatically-create-word-tables.md)   
 [Gewusst wie: Programmgesteuertes Hinzufügen von Zeilen und Spalten zu Word-Tabellen](../vsto/how-to-programmatically-add-rows-and-columns-to-word-tables.md)   
 [Gewusst wie: Programmgesteuertes Auffüllen von Word-Tabellen mit Dokumenteigenschaften](../vsto/how-to-programmatically-populate-word-tables-with-document-properties.md)  
  
  