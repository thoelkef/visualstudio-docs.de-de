---
title: "Gewusst wie: Programmgesteuertes Verwenden von Word-Dialogfeldern im ausgeblendeten Modus"
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
  - "Dialogfelder, Ausgeblendeter Modus in Word"
  - "Ausgeblendete Dialogfelder"
  - "Word [Office-Entwicklung in Visual Studio], Dialogfelder"
ms.assetid: a5619325-8b54-41f1-becb-3f6eae7e4a6b
caps.latest.revision: 48
author: "kempb"
ms.author: "kempb"
manager: "ghogen"
caps.handback.revision: 47
---
# Gewusst wie: Programmgesteuertes Verwenden von Word-Dialogfeldern im ausgeblendeten Modus
  Sie können mit einem Methodenaufruf komplexe Vorgänge ausführen, indem Sie die integrierten Dialogfelder von Microsoft Office Word aufrufen und sie den Benutzern nicht anzeigen.  Zu diesem Zweck können Sie die <xref:Microsoft.Office.Interop.Word.Dialog.Execute%2A>\-Methode des <xref:Microsoft.Office.Interop.Word.Dialog>\-Objekts verwenden, ohne die <xref:Microsoft.Office.Interop.Word.Dialog.Display%2A>\-Methode aufzurufen.  
  
 [!INCLUDE[appliesto_wdalldocapp](../vsto/includes/appliesto-wdalldocapp-md.md)]  
  
## Beispiele  
 In den folgenden Codebeispielen wird veranschaulicht, wie das Dialogfeld **Seite einrichten** im ausgeblendeten Modus verwendet wird, um mehrere Seiteneinrichtungseigenschaften ohne Benutzereingabe festzulegen.  Im Beispiel wird eine benutzerdefinierte Seitengröße mithilfe eines <xref:Microsoft.Office.Interop.Word.Dialog>\-Objekts konfiguriert.  Die speziellen Einstellungen für die Seiteneinrichtung, wie zum Beispiel der obere und der untere Seitenrand sind als spät gebundene Eigenschaften des <xref:Microsoft.Office.Interop.Word.Dialog>\-Objekts verfügbar.  Diese Eigenschaften werden zur Laufzeit dynamisch von Word erstellt.  
  
 Im folgenden Beispiel wird veranschaulicht, wie diese Aufgabe in Visual Basic\-Projekten ausgeführt wird, in denen sich **Option Strict** außerhalb und innerhalb von Visual C\#\-Projekten befindet, für die als Zielversion [!INCLUDE[net_v40_short](../sharepoint/includes/net-v40-short-md.md)] festgelegt wurde.  In diesen Projekten können Sie Funktionen für späte Bindung in den Visual Basic\- und Visual C\#\-Compilern verwenden.  Wenn Sie dieses Beispiel verwenden möchten, führen Sie es von der `ThisDocument`\-Klasse oder der `ThisAddIn`\-Klasse im Projekt aus.  
  
 [!code-csharp[Trin_VstcoreWordAutomation#123](../snippets/csharp/VS_Snippets_OfficeSP/Trin_VstcoreWordAutomation/CS/ThisDocument.cs#123)]
 [!code-vb[Trin_VstcoreWordAutomation#123](../snippets/visualbasic/VS_Snippets_OfficeSP/Trin_VstcoreWordAutomation/VB/ThisDocument.vb#123)]  
  
 Im folgenden Beispiel wird veranschaulicht, wie diese Aufgabe in Visual Basic\-Projekten ausgeführt wird, in denen **Option Strict** aktiviert ist.  In diesen Projekten müssen Sie auf die spät gebundenen Eigenschaften mithilfe von Reflektion zugreifen.  Wenn Sie dieses Beispiel verwenden möchten, führen Sie es von der `ThisDocument`\-Klasse oder der `ThisAddIn`\-Klasse im Projekt aus.  
  
 [!code-vb[Trin_VstcoreWordAutomation#104](../snippets/visualbasic/VS_Snippets_OfficeSP/Trin_VstcoreWordAutomation/VB/ThisDocument.vb#104)]  
  
## Siehe auch  
 [Gewusst wie: Programmgesteuertes Verwenden integrierter Dialogfelder in Word](../vsto/how-to-programmatically-use-built-in-dialog-boxes-in-word.md)   
 [Übersicht über das Word-Objektmodell](../vsto/word-object-model-overview.md)   
 [Späte Bindung in Office-Lösungen](../vsto/late-binding-in-office-solutions.md)   
 [Reflektion &#40;C&#35; und Visual Basic&#41;](http://msdn.microsoft.com/library/5d1d1bcf-08de-4d0b-97a8-912d17c00f26)  
  
  