---
title: "Gewusst wie: Programmgesteuertes Erstellen von Word-Tabellen"
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
  - "Dokumente [Office-Entwicklung in Visual Studio], Hinzufügen von Tabellen"
  - "Tabellen [Office-Entwicklung in Visual Studio], Hinzufügen zu Dokumenten"
ms.assetid: fe1f9143-9622-45e8-b0a5-511336d99ad1
caps.latest.revision: 45
author: "kempb"
ms.author: "kempb"
manager: "ghogen"
caps.handback.revision: 44
---
# Gewusst wie: Programmgesteuertes Erstellen von Word-Tabellen
  Die Auflistung <xref:Microsoft.Office.Interop.Word.Tables> ist ein Element der Klassen <xref:Microsoft.Office.Interop.Word.Document>, <xref:Microsoft.Office.Tools.Word.Document>, <xref:Microsoft.Office.Interop.Word.Selection> und <xref:Microsoft.Office.Interop.Word.Range>. Dies bedeutet, dass Sie in jedem dieser Kontexte eine Tabelle erstellen können.  Verwenden Sie die Methode <xref:Microsoft.Office.Interop.Word.Tables.Add%2A> der Auflistung <xref:Microsoft.Office.Interop.Word.Tables>, um eine Tabelle im angegebenen Bereich hinzuzufügen.  
  
 [!INCLUDE[appliesto_wdalldocapp](../vsto/includes/appliesto-wdalldocapp-md.md)]  
  
## Erstellen von Tabellen in Anpassungen auf Dokumentebene  
  
#### So fügen Sie einem Dokument eine einfache Tabelle hinzu  
  
-   Verwenden Sie die Methode <xref:Microsoft.Office.Interop.Word.Tables.Add%2A>, um eine Tabelle am Anfang des Dokuments hinzufügen, die aus drei Zeilen und vier Spalten besteht.  
  
     Wenn Sie das folgende Codebeispiel verwenden möchten, führen Sie es aus der Klasse `ThisDocument` im Projekt aus.  
  
     [!code-csharp[Trin_VstcoreWordAutomation#86](../snippets/csharp/VS_Snippets_OfficeSP/Trin_VstcoreWordAutomation/CS/ThisDocument.cs#86)]
     [!code-vb[Trin_VstcoreWordAutomation#86](../snippets/visualbasic/VS_Snippets_OfficeSP/Trin_VstcoreWordAutomation/VB/ThisDocument.vb#86)]  
  
 Wenn Sie eine Tabelle erstellen, wird diese der Auflistung <xref:Microsoft.Office.Interop.Word.Tables> des <xref:Microsoft.Office.Tools.Word.Document>\-Hostelements automatisch hinzugefügt .  Sie können dann auf die Tabelle über ihre Elementnummer verweisen, indem Sie die Eigenschaft <xref:Microsoft.Office.Interop.Word.Tables.Item%2A> wie im folgenden Code gezeigt verwenden.  
  
#### So verweisen Sie auf eine Tabelle über die Artikelnummer  
  
1.  Verwenden Sie die Eigenschaft <xref:Microsoft.Office.Interop.Word.Tables.Item%2A>, und stellen Sie die Elementnummer der Tabelle bereit, auf die Sie verweisen möchten.  
  
     Wenn Sie das folgende Codebeispiel verwenden möchten, führen Sie es aus der Klasse `ThisDocument` im Projekt aus.  
  
     [!code-csharp[Trin_VstcoreWordAutomation#87](../snippets/csharp/VS_Snippets_OfficeSP/Trin_VstcoreWordAutomation/CS/ThisDocument.cs#87)]
     [!code-vb[Trin_VstcoreWordAutomation#87](../snippets/visualbasic/VS_Snippets_OfficeSP/Trin_VstcoreWordAutomation/VB/ThisDocument.vb#87)]  
  
 Jedes <xref:Microsoft.Office.Interop.Word.Table>\-Objekt verfügt außerdem über eine Eigenschaft <xref:Microsoft.Office.Interop.Word.Table.Range%2A>, die das Festlegen von Formatierungsattributen ermöglicht.  
  
#### So wenden Sie eine Formatvorlage auf eine Tabelle an  
  
1.  Verwenden Sie die Eigenschaft <xref:Microsoft.Office.Interop.Word.Table.Style%2A>, um eine der integrierten Word\-Formatvorlagen auf eine Tabelle anzuwenden.  
  
     Wenn Sie das folgende Codebeispiel verwenden möchten, führen Sie es aus der Klasse `ThisDocument` im Projekt aus.  
  
     [!code-csharp[Trin_VstcoreWordAutomation#88](../snippets/csharp/VS_Snippets_OfficeSP/Trin_VstcoreWordAutomation/CS/ThisDocument.cs#88)]
     [!code-vb[Trin_VstcoreWordAutomation#88](../snippets/visualbasic/VS_Snippets_OfficeSP/Trin_VstcoreWordAutomation/VB/ThisDocument.vb#88)]  
  
## Erstellen von Tabellen in VSTO\-Add\-Ins  
  
#### So fügen Sie einem Dokument eine einfache Tabelle hinzu  
  
-   Verwenden Sie die Methode <xref:Microsoft.Office.Interop.Word.Tables.Add%2A>, um eine Tabelle am Anfang des Dokuments hinzufügen, die aus drei Zeilen und vier Spalten besteht.  
  
     Im folgenden Codebeispiel wird dem aktiven Dokument eine Tabelle hinzugefügt.  Wenn Sie dieses Beispiel verwenden möchten, führen Sie es aus der Klasse `ThisAddIn` in Ihrem Projekt aus.  
  
     [!code-csharp[Trin_VstcoreWordAutomationAddIn#86](../snippets/csharp/VS_Snippets_OfficeSP/Trin_VstcoreWordAutomationAddIn/CS/ThisAddIn.cs#86)]
     [!code-vb[Trin_VstcoreWordAutomationAddIn#86](../snippets/visualbasic/VS_Snippets_OfficeSP/Trin_VstcoreWordAutomationAddIn/VB/ThisAddIn.vb#86)]  
  
 Wenn Sie eine Tabelle erstellen, wird diese der Auflistung <xref:Microsoft.Office.Interop.Word.Tables> des <xref:Microsoft.Office.Interop.Word.Document>\-Objekts automatisch hinzugefügt .  Sie können dann auf die Tabelle über ihre Elementnummer verweisen, indem Sie die Eigenschaft <xref:Microsoft.Office.Interop.Word.Tables.Item%2A> wie im folgenden Code gezeigt verwenden.  
  
#### So verweisen Sie auf eine Tabelle über die Artikelnummer  
  
1.  Verwenden Sie die Eigenschaft <xref:Microsoft.Office.Interop.Word.Tables.Item%2A>, und stellen Sie die Elementnummer der Tabelle bereit, auf die Sie verweisen möchten.  
  
     Im folgenden Codebeispiel wird das aktive Dokument verwendet.  Wenn Sie dieses Beispiel verwenden möchten, führen Sie es aus der Klasse `ThisAddIn` in Ihrem Projekt aus.  
  
     [!code-csharp[Trin_VstcoreWordAutomationAddIn#87](../snippets/csharp/VS_Snippets_OfficeSP/Trin_VstcoreWordAutomationAddIn/CS/ThisAddIn.cs#87)]
     [!code-vb[Trin_VstcoreWordAutomationAddIn#87](../snippets/visualbasic/VS_Snippets_OfficeSP/Trin_VstcoreWordAutomationAddIn/VB/ThisAddIn.vb#87)]  
  
 Jedes <xref:Microsoft.Office.Interop.Word.Table>\-Objekt verfügt außerdem über eine Eigenschaft <xref:Microsoft.Office.Interop.Word.Table.Range%2A>, die das Festlegen von Formatierungsattributen ermöglicht.  
  
#### So wenden Sie eine Formatvorlage auf eine Tabelle an  
  
1.  Verwenden Sie die Eigenschaft <xref:Microsoft.Office.Interop.Word.Table.Style%2A>, um eine der integrierten Word\-Formatvorlagen auf eine Tabelle anzuwenden.  
  
     Im folgenden Codebeispiel wird das aktive Dokument verwendet.  Wenn Sie dieses Beispiel verwenden möchten, führen Sie es aus der Klasse `ThisAddIn` in Ihrem Projekt aus.  
  
     [!code-csharp[Trin_VstcoreWordAutomationAddIn#88](../snippets/csharp/VS_Snippets_OfficeSP/Trin_VstcoreWordAutomationAddIn/CS/ThisAddIn.cs#88)]
     [!code-vb[Trin_VstcoreWordAutomationAddIn#88](../snippets/visualbasic/VS_Snippets_OfficeSP/Trin_VstcoreWordAutomationAddIn/VB/ThisAddIn.vb#88)]  
  
## Siehe auch  
 [Gewusst wie: Programmgesteuertes Hinzufügen von Text und Formatierungen zu Zellen in Word-Tabellen](../vsto/how-to-programmatically-add-text-and-formatting-to-cells-in-word-tables.md)   
 [Gewusst wie: Programmgesteuertes Hinzufügen von Zeilen und Spalten zu Word-Tabellen](../vsto/how-to-programmatically-add-rows-and-columns-to-word-tables.md)   
 [Gewusst wie: Programmgesteuertes Auffüllen von Word-Tabellen mit Dokumenteigenschaften](../vsto/how-to-programmatically-populate-word-tables-with-document-properties.md)   
 [Optionale Parameter in Office-Lösungen](../vsto/optional-parameters-in-office-solutions.md)  
  
  