---
title: "Gewusst wie: Programmgesteuertes Entfernen aller Kommentare aus einem Dokument"
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
  - "Dokumente [Office-Entwicklung in Visual Studio], Entfernen von Kommentaren"
  - "Kommentare, Entfernen aus Dokumenten"
ms.assetid: 920de39a-3b6d-4682-bca6-f4b4dedda1ac
caps.latest.revision: 24
author: "kempb"
ms.author: "kempb"
manager: "ghogen"
caps.handback.revision: 23
---
# Gewusst wie: Programmgesteuertes Entfernen aller Kommentare aus einem Dokument
  Verwenden Sie die DeleteAllComments\-Methode, um alle Kommentare aus einem Microsoft Office Word\-Dokument zu entfernen.  
  
 [!INCLUDE[appliesto_wdalldocapp](../vsto/includes/appliesto-wdalldocapp-md.md)]  
  
### So entfernen Sie alle Kommentare aus einem Dokument, das Teil einer Anpassung auf Dokumentebene ist  
  
1.  Rufen Sie in Ihrem Projekt die <xref:Microsoft.Office.Tools.Word.Document.DeleteAllComments%2A>\-Methode der `ThisDocument`\-Klasse auf. Wenn Sie dieses Codebeispiel verwenden möchten, führen Sie es über die `ThisDocument`\-Klasse aus.  
  
     [!code-csharp[Trin_VstcoreWordAutomation#119](../snippets/csharp/VS_Snippets_OfficeSP/Trin_VstcoreWordAutomation/CS/ThisDocument.cs#119)]
     [!code-vb[Trin_VstcoreWordAutomation#119](../snippets/visualbasic/VS_Snippets_OfficeSP/Trin_VstcoreWordAutomation/VB/ThisDocument.vb#119)]  
  
### So entfernen Sie mithilfe eines VSTO\-Add\-Ins alle Kommentare aus einem Dokument  
  
1.  Rufen Sie die <xref:Microsoft.Office.Interop.Word._Document.DeleteAllComments%2A>\-Methode der <xref:Microsoft.Office.Interop.Word.Document> auf, aus der Sie Kommentare entfernen möchten.  
  
     Das folgende Codebeispiel entfernt alle Kommentare aus dem aktiven Dokument. Wenn Sie dieses Codebeispiel verwenden möchten, führen Sie es von der `ThisAddIn`\-Klasse im Projekt aus.  
  
     [!code-csharp[Trin_VstcoreWordAutomationAddIn#119](../snippets/csharp/VS_Snippets_OfficeSP/Trin_VstcoreWordAutomationAddIn/CS/ThisAddIn.cs#119)]
     [!code-vb[Trin_VstcoreWordAutomationAddIn#119](../snippets/visualbasic/VS_Snippets_OfficeSP/Trin_VstcoreWordAutomationAddIn/VB/ThisAddIn.vb#119)]  
  
## Siehe auch  
 [Gewusst wie: Programmgesteuertes Hinzufügen von Kommentaren zu Text in Dokumenten](../vsto/how-to-programmatically-add-comments-to-text-in-documents.md)   
 [Dokumenthostelement](../vsto/document-host-item.md)  
  
  