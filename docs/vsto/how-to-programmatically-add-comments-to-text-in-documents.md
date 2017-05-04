---
title: "Gewusst wie: Programmgesteuertes Hinzuf&#252;gen von Kommentaren zu Text in Dokumenten | Microsoft Docs"
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
  - "Kommentare, Hinzufügen zu Dokumenten"
  - "Dokumente [Office-Entwicklung in Visual Studio], Hinzufügen von Kommentaren"
ms.assetid: 4e396e31-01bf-424c-be6b-9a1806bcd572
caps.latest.revision: 26
author: "kempb"
ms.author: "kempb"
manager: "ghogen"
caps.handback.revision: 25
---
# Gewusst wie: Programmgesteuertes Hinzuf&#252;gen von Kommentaren zu Text in Dokumenten
  Die Eigenschaft Comments der Klasse Document fügt einen Kommentar zu einem Textbereich in einem Microsoft Office Word\-Dokument hinzu.  
  
 [!INCLUDE[appliesto_wdalldocapp](../vsto/includes/appliesto-wdalldocapp-md.md)]  
  
 Mit dem folgenden Beispiel wird dem ersten Absatz im Dokument ein Kommentar hinzugefügt.  
  
### So fügen Sie einen neuen Kommentar zu Text in einer Anpassung auf Dokumentebene hinzu  
  
1.  Rufen Sie die Methode <xref:Microsoft.Office.Interop.Word.Comments.Add%2A> der Eigenschaft <xref:Microsoft.Office.Tools.Word.Document.Comments%2A> auf, und geben Sie einen Bereich sowie den Kommentartext ein. Wenn Sie das folgende Codebeispiel verwenden möchten, führen Sie es aus der Klasse `ThisDocument` in Ihrem Projekt aus.  
  
     [!code-csharp[Trin_VstcoreWordAutomation#118](../snippets/csharp/VS_Snippets_OfficeSP/Trin_VstcoreWordAutomation/CS/ThisDocument.cs#118)]
     [!code-vb[Trin_VstcoreWordAutomation#118](../snippets/visualbasic/VS_Snippets_OfficeSP/Trin_VstcoreWordAutomation/VB/ThisDocument.vb#118)]  
  
### So fügen Sie einen neuen Kommentar zu Text in einem VSTO\-Add\-In hinzu  
  
1.  Rufen Sie die Methode <xref:Microsoft.Office.Interop.Word.Comments.Add%2A> der Eigenschaft <xref:Microsoft.Office.Interop.Word._Document.Comments%2A> auf, und geben Sie einen Bereich sowie den Kommentartext ein.  
  
     Im folgenden Codebeispiel wird dem aktiven Dokument ein Kommentar hinzugefügt. Wenn Sie dieses Beispiel verwenden möchten, führen Sie es von der `ThisAddIn`\-Klasse Ihres Projekts aus.  
  
     [!code-csharp[Trin_VstcoreWordAutomationAddIn#118](../snippets/csharp/VS_Snippets_OfficeSP/Trin_VstcoreWordAutomationAddIn/CS/ThisAddIn.cs#118)]
     [!code-vb[Trin_VstcoreWordAutomationAddIn#118](../snippets/visualbasic/VS_Snippets_OfficeSP/Trin_VstcoreWordAutomationAddIn/VB/ThisAddIn.vb#118)]  
  
## Robuste Programmierung  
 Zum Ändern der Benutzerinitialen, die Word Kommentaren hinzufügt, verwenden Sie die Eigenschaft <xref:Microsoft.Office.Interop.Word._Application.UserInitials%2A>.  
  
## Siehe auch  
 [Gewusst wie: Programmgesteuertes Entfernen aller Kommentare aus einem Dokument](../vsto/how-to-programmatically-remove-all-comments-from-documents.md)   
 [Dokumenthostelement](../vsto/document-host-item.md)  
  
  