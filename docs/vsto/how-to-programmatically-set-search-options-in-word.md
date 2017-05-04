---
title: "Gewusst wie: Programmgesteuertes Festlegen von Suchoptionen in Word | Microsoft Docs"
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
  - "Dokumente [Office-Entwicklung in Visual Studio], Suchoptionen"
  - "Suchen, Word-Optionen"
  - "Einstellungen, Word-Suchoptionen"
  - "Word, Suchoptionen"
ms.assetid: 4412b4e8-2868-4afb-a593-983603ef9b02
caps.latest.revision: 46
author: "kempb"
ms.author: "kempb"
manager: "ghogen"
caps.handback.revision: 45
---
# Gewusst wie: Programmgesteuertes Festlegen von Suchoptionen in Word
  Es gibt zwei Möglichkeiten zum Festlegen der Suchoptionen für eine Markierung in Microsoft Office Word\-Dokumenten.  
  
-   Festlegen einzelner Eigenschaften eines <xref:Microsoft.Office.Interop.Word.Find>\-Objekts  
  
-   Verwenden von Argumenten der <xref:Microsoft.Office.Interop.Word.Find.Execute%2A>\-Methode eines <xref:Microsoft.Office.Interop.Word.Find>\-Objekts  
  
 [!INCLUDE[appliesto_wdalldocapp](../vsto/includes/appliesto-wdalldocapp-md.md)]  
  
## Verwenden der Eigenschaften eines Find\-Objekts  
 Im folgenden Code werden Eigenschaften eines <xref:Microsoft.Office.Interop.Word.Find>\-Objekts festgelegt, um in der aktuellen Markierung nach Text zu suchen.  Beachten Sie, dass es sich bei den Suchkriterien \(z. B. Suche vorwärts, Umbruch und dem Suchtext\) um Eigenschaften des <xref:Microsoft.Office.Interop.Word.Find>\-Objekts handelt.  
  
 Wenn Sie C\#\-Code schreiben, ist es nicht nützlich, jede der Eigenschaften des <xref:Microsoft.Office.Interop.Word.Find>\-Objekts festzulegen, da Sie in der <xref:Microsoft.Office.Interop.Word.Find.Execute%2A>\-Methode dieselben Eigenschaften als Parameter angeben müssen.  Deshalb enthält dieses Beispiel nur Visual Basic\-Code.  
  
#### So legen Sie Suchoptionen mithilfe eines Find\-Objekts fest  
  
1.  Legen Sie die Eigenschaften eines <xref:Microsoft.Office.Interop.Word.Find>\-Objekts für die Vorwärtssuche in einer Markierung nach dem Text **find me** fest.  
  
     [!code-vb[Trin_VstcoreWordAutomation#76](../snippets/visualbasic/VS_Snippets_OfficeSP/Trin_VstcoreWordAutomation/VB/ThisDocument.vb#76)]  
  
## Verwenden von Argumenten der Execute\-Methode  
 Im folgenden Code wird mithilfe der <xref:Microsoft.Office.Interop.Word.Find.Execute%2A>\-Methode eines <xref:Microsoft.Office.Interop.Word.Find>\-Objekts in der aktuellen Markierung nach Text gesucht.  Beachten Sie, dass die Suchkriterien \(z. B. Suche vorwärts, Umbruch und der Suchtext\) als Parameter der <xref:Microsoft.Office.Interop.Word.Find.Execute%2A>\-Methode übergeben werden.  
  
#### So legen Sie Suchoptionen mithilfe von Argumenten der Execute\-Methode fest  
  
1.  Übergeben Sie die Suchkriterien als Parameter der <xref:Microsoft.Office.Interop.Word.Find.Execute%2A>\-Methode, um in einer Markierung vorwärts nach dem Text **find me** zu suchen.  
  
     [!code-csharp[Trin_VstcoreWordAutomation#77](../snippets/csharp/VS_Snippets_OfficeSP/Trin_VstcoreWordAutomation/CS/ThisDocument.cs#77)]
     [!code-vb[Trin_VstcoreWordAutomation#77](../snippets/visualbasic/VS_Snippets_OfficeSP/Trin_VstcoreWordAutomation/VB/ThisDocument.vb#77)]  
  
## Siehe auch  
 [Gewusst wie: Programmgesteuertes Suchen und Ersetzen von Text in Dokumenten](../vsto/how-to-programmatically-search-for-and-replace-text-in-documents.md)   
 [Gewusst wie: Programmgesteuertes Durchlaufen gefundener Elemente in Dokumenten](../vsto/how-to-programmatically-loop-through-found-items-in-documents.md)   
 [Gewusst wie: Programmgesteuertes Wiederherstellen der Auswahl nach Suchvorgängen](../vsto/how-to-programmatically-restore-selections-after-searches.md)  
  
  