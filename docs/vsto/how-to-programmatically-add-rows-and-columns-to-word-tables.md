---
title: "Gewusst wie: Programmgesteuertes Hinzuf&#252;gen von Zeilen und Spalten zu Word-Tabellen | Microsoft Docs"
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
  - "Spalten [Office-Entwicklung in Visual Studio], Hinzufügen zu Word-Tabellen"
  - "Zeilen [Office-Entwicklung in Visual Studio], Hinzufügen zu Word-Tabellen"
  - "Tabellen [Office-Entwicklung in Visual Studio], Hinzufügen von Zeilen und Spalten"
ms.assetid: 01a9b6ca-1373-4a6e-b9e6-2225a1321daf
caps.latest.revision: 42
author: "kempb"
ms.author: "kempb"
manager: "ghogen"
caps.handback.revision: 41
---
# Gewusst wie: Programmgesteuertes Hinzuf&#252;gen von Zeilen und Spalten zu Word-Tabellen
  In einer Microsoft Office Word\-Tabelle werden die Zellen in Zeilen und Spalten angeordnet.  Sie können die <xref:Microsoft.Office.Interop.Word.Rows.Add%2A>\-Methode des <xref:Microsoft.Office.Interop.Word.Rows>\-Objekts verwenden, um der Tabelle Zeilen hinzuzufügen, und die <xref:Microsoft.Office.Interop.Word.Columns.Add%2A>\-Methode des <xref:Microsoft.Office.Interop.Word.Columns>\-Objekts, um Spalten hinzuzufügen.  
  
 [!INCLUDE[appliesto_wdalldocapp](../vsto/includes/appliesto-wdalldocapp-md.md)]  
  
## Beispiele für die Anpassung auf Dokumentebene  
 Die folgenden Codebeispiele können in einer Anpassung auf Dokumentebene verwendet werden.  Wenn Sie diese Beispiele verwenden möchten, führen Sie den Code von der `ThisDocument`\-Klasse im Projekt aus.  In diesen Beispielen wird davon ausgegangen, dass das mit der Anpassung verknüpfte Dokument bereits über mindestens eine Tabelle verfügt.  
  
> [!IMPORTANT]  
>  Dieser Code wird nur in Projekten ausgeführt, die Sie mithilfe einer der folgenden Projektvorlagen erstellen:  
>   
>  -   Word 2013\-Dokument  
> -   Word 2013\-Vorlage  
> -   Word 2010\-Dokument  
> -   Word 2010\-Vorlage  
>   
>  Wenn Sie diese Aufgabe mit einem anderen Projekttyp ausführen möchten, müssen Sie einen Verweis auf die **Microsoft.Office.Interop.Word**\-Assembly hinzufügen und dann die Klassen aus dieser Assembly verwenden, um den Tabellen Zeilen und Spalten hinzuzufügen.  Weitere Informationen finden Sie unter [Verweisen auf Office-Anwendungen durch primäre Interopassemblys](../vsto/how-to-target-office-applications-through-primary-interop-assemblies.md) und [Referenz für primäre Interopassemblys für Word 2010](http://go.microsoft.com/fwlink/?LinkId=189588).  
  
#### So fügen Sie einer Tabelle eine Zeile hinzu  
  
1.  Verwenden Sie die <xref:Microsoft.Office.Interop.Word.Rows.Add%2A>\-Methode, um der Tabelle eine Zeile hinzuzufügen.  
  
     [!code-csharp[Trin_VstcoreWordAutomation#95](../snippets/csharp/VS_Snippets_OfficeSP/Trin_VstcoreWordAutomation/CS/ThisDocument.cs#95)]
     [!code-vb[Trin_VstcoreWordAutomation#95](../snippets/visualbasic/VS_Snippets_OfficeSP/Trin_VstcoreWordAutomation/VB/ThisDocument.vb#95)]  
  
#### So fügen Sie einer Tabelle eine Spalte hinzu  
  
1.  Verwenden Sie erst die <xref:Microsoft.Office.Interop.Word.Columns.Add%2A>\-Methode und dann die <xref:Microsoft.Office.Interop.Word.Columns.DistributeWidth%2A>\-Methode, um alle Spalten mit der gleichen Breite zu formatieren.  
  
     [!code-csharp[Trin_VstcoreWordAutomation#96](../snippets/csharp/VS_Snippets_OfficeSP/Trin_VstcoreWordAutomation/CS/ThisDocument.cs#96)]
     [!code-vb[Trin_VstcoreWordAutomation#96](../snippets/visualbasic/VS_Snippets_OfficeSP/Trin_VstcoreWordAutomation/VB/ThisDocument.vb#96)]  
  
## Beispiele für das VSTO\-Add\-In  
 Die folgenden Codebeispiele können in einem VSTO\-Add\-In verwendet werden.  Wenn Sie diese Beispiele verwenden möchten, führen Sie sie von der `ThisAddIn`\-Klasse im Projekt aus.  In diesen Beispielen wird davon ausgegangen, dass das aktive Dokument bereits über mindestens eine Tabelle verfügt.  
  
> [!IMPORTANT]  
>  Dieser Code wird nur in Projekten ausgeführt, die Sie mithilfe der VSTO\-Add\-In\-Vorlagen für Word erstellen.  
>   
>  Wenn Sie diese Aufgabe mit einem anderen Projekttyp ausführen möchten, müssen Sie einen Verweis auf die **Microsoft.Office.Interop.Word**\-Assembly hinzufügen und dann die Klassen aus dieser Assembly verwenden, um den Tabellen Zeilen und Spalten hinzuzufügen.  Weitere Informationen finden Sie unter [Verweisen auf Office-Anwendungen durch primäre Interopassemblys](../vsto/how-to-target-office-applications-through-primary-interop-assemblies.md) und [Referenz für primäre Interopassemblys für Word 2010](http://go.microsoft.com/fwlink/?LinkId=189588).  
  
#### So fügen Sie einer Tabelle eine Zeile hinzu  
  
1.  Verwenden Sie die <xref:Microsoft.Office.Interop.Word.Rows.Add%2A>\-Methode, um der Tabelle eine Zeile hinzuzufügen.  
  
     [!code-csharp[Trin_VstcoreWordAutomationAddIn#95](../snippets/csharp/VS_Snippets_OfficeSP/Trin_VstcoreWordAutomationAddIn/CS/ThisAddIn.cs#95)]
     [!code-vb[Trin_VstcoreWordAutomationAddIn#95](../snippets/visualbasic/VS_Snippets_OfficeSP/Trin_VstcoreWordAutomationAddIn/VB/ThisAddIn.vb#95)]  
  
#### So fügen Sie einer Tabelle eine Spalte hinzu  
  
1.  Verwenden Sie erst die <xref:Microsoft.Office.Interop.Word.Columns.Add%2A>\-Methode und dann die <xref:Microsoft.Office.Interop.Word.Columns.DistributeWidth%2A>\-Methode, um alle Spalten mit der gleichen Breite zu formatieren.  
  
     [!code-csharp[Trin_VstcoreWordAutomationAddIn#96](../snippets/csharp/VS_Snippets_OfficeSP/Trin_VstcoreWordAutomationAddIn/CS/ThisAddIn.cs#96)]
     [!code-vb[Trin_VstcoreWordAutomationAddIn#96](../snippets/visualbasic/VS_Snippets_OfficeSP/Trin_VstcoreWordAutomationAddIn/VB/ThisAddIn.vb#96)]  
  
## Siehe auch  
 [Gewusst wie: Programmgesteuertes Erstellen von Word-Tabellen](../vsto/how-to-programmatically-create-word-tables.md)   
 [Gewusst wie: Programmgesteuertes Hinzufügen von Text und Formatierungen zu Zellen in Word-Tabellen](../vsto/how-to-programmatically-add-text-and-formatting-to-cells-in-word-tables.md)   
 [Gewusst wie: Programmgesteuertes Auffüllen von Word-Tabellen mit Dokumenteigenschaften](../vsto/how-to-programmatically-populate-word-tables-with-document-properties.md)  
  
  