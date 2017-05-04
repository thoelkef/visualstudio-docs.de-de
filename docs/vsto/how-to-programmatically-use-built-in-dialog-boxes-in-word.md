---
title: "Gewusst wie: Programmgesteuertes Verwenden integrierter Dialogfelder in Word | Microsoft Docs"
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
  - "Word [Office-Entwicklung in Visual Studio], Dialogfelder"
  - "Dialogfelder, Word"
ms.assetid: 0c7e4338-dead-4444-868b-3b0212368455
caps.latest.revision: 54
author: "kempb"
ms.author: "kempb"
manager: "ghogen"
caps.handback.revision: 53
---
# Gewusst wie: Programmgesteuertes Verwenden integrierter Dialogfelder in Word
  Bei der Arbeit mit Microsoft Office Word ist es gelegentlich nötig, Dialogfelder für Benutzereingaben anzuzeigen.  Sie können eigene Dialogfelder erstellen oder aber die in Word integrierten Dialogfelder verwenden, die in der <xref:Microsoft.Office.Interop.Word.Dialogs>\-Auflistung des <xref:Microsoft.Office.Interop.Word.Application>\-Objekts verfügbar sind.  Auf diese Weise können Sie auf mehr als 200 integrierte Dialogfelder zugreifen, die als Enumerationen dargestellt sind.  
  
 [!INCLUDE[appliesto_wdalldocapp](../vsto/includes/appliesto-wdalldocapp-md.md)]  
  
## Anzeigen von Dialogfeldern  
 Verwenden Sie zum Anzeigen eines Dialogfelds einen der Werte der <xref:Microsoft.Office.Interop.Word.WdWordDialog>\-Enumeration, um ein <xref:Microsoft.Office.Interop.Word.Dialog>\-Objekt zu erstellen, das das anzuzeigende Dialogfeld darstellt.  Rufen Sie anschließend die <xref:Microsoft.Office.Interop.Word.Dialog.Show%2A>\-Methode eines <xref:Microsoft.Office.Interop.Word.Dialog>\-Objekts auf.  
  
 Im folgenden Codebeispiel wird veranschaulicht, wie das Dialogfeld **Datei öffnen** angezeigt wird.  Wenn Sie dieses Beispiel verwenden möchten, führen Sie es von der `ThisDocument`\-Klasse oder der `ThisAddIn`\-Klasse im Projekt aus.  
  
 [!code-csharp[Trin_VstcoreWordAutomation#100](../snippets/csharp/VS_Snippets_OfficeSP/Trin_VstcoreWordAutomation/CS/ThisDocument.cs#100)]
 [!code-vb[Trin_VstcoreWordAutomation#100](../snippets/visualbasic/VS_Snippets_OfficeSP/Trin_VstcoreWordAutomation/VB/ThisDocument.vb#100)]  
  
### Zugreifen auf Dialogfeldmember, die durch späte Bindung verfügbar sind  
 Einige Eigenschaften und Methoden von Dialogfeldern in Word sind nur durch späte Bindung verfügbar.  In Visual Basic\-Projekten, in denen **Option Strict** aktiviert ist, müssen Sie Reflektion verwenden, um diese Member zugreifen.  Weitere Informationen finden Sie unter [Späte Bindung in Office-Lösungen](../vsto/late-binding-in-office-solutions.md).  
  
 Weg von das folgende Codebeispiel zeigt, wie die \- Eigenschaft des Dialogfelds **NameDatei öffnen** verwendet in Visual Basic\-Projekten, dem **Option Strict** ist oder Visual C\#, damit das [!INCLUDE[net_v40_short](../sharepoint/includes/net-v40-short-md.md)] oder [!INCLUDE[net_v45](../vsto/includes/net-v45-md.md)] abzielen.  Wenn Sie dieses Beispiel verwenden möchten, führen Sie es von der `ThisDocument`\-Klasse oder der `ThisAddIn`\-Klasse im Projekt aus.  
  
 [!code-csharp[Trin_VstcoreWordAutomation#122](../snippets/csharp/VS_Snippets_OfficeSP/Trin_VstcoreWordAutomation/CS/ThisDocument.cs#122)]
 [!code-vb[Trin_VstcoreWordAutomation#122](../snippets/visualbasic/VS_Snippets_OfficeSP/Trin_VstcoreWordAutomation/VB/ThisDocument.vb#122)]  
  
 Im folgenden Codebeispiel wird veranschaulicht, wie Reflektion verwendet, um auf die **Name**\-Eigenschaft **Datei öffnen** des Dialogfelds in Visual Basic\-Projekten zuzugreifen, in dem **Option Strict** aktiviert ist.  Wenn Sie dieses Beispiel verwenden möchten, führen Sie es von der `ThisDocument`\-Klasse oder der `ThisAddIn`\-Klasse im Projekt aus.  
  
 [!code-vb[Trin_VstcoreWordAutomation#102](../snippets/visualbasic/VS_Snippets_OfficeSP/Trin_VstcoreWordAutomation/VB/ThisDocument.vb#102)]  
  
## Siehe auch  
 [Gewusst wie: Programmgesteuertes Verwenden von Word-Dialogfeldern im ausgeblendeten Modus](../vsto/how-to-programmatically-use-word-dialog-boxes-in-hidden-mode.md)   
 [Übersicht über das Word-Objektmodell](../vsto/word-object-model-overview.md)   
 [Optionale Parameter in Office-Lösungen](../vsto/optional-parameters-in-office-solutions.md)   
 [Option Strict Statement](/dotnet/visual-basic/language-reference/statements/option-strict-statement)   
 [Reflektion &#40;C&#35; und Visual Basic&#41;](../Topic/Reflection%20(C%23%20and%20Visual%20Basic).md)  
  
  