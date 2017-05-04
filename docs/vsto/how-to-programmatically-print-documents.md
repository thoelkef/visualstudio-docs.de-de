---
title: "Gewusst wie: Programmgesteuertes Drucken von Dokumenten | Microsoft Docs"
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
  - "Word [Office-Entwicklung in Visual Studio], Drucken von Dokumenten"
  - "Dokumente [Office-Entwicklung in Visual Studio], drucken"
ms.assetid: 99285d98-1bb7-4ccb-83d9-e917b0a9ea42
caps.latest.revision: 53
author: "kempb"
ms.author: "kempb"
manager: "ghogen"
caps.handback.revision: 52
---
# Gewusst wie: Programmgesteuertes Drucken von Dokumenten
  Sie können ein ganzes Microsoft Office Word\-Dokument oder einen Teil eines Dokuments auf dem Standarddrucker drucken.  
  
 [!INCLUDE[appliesto_wdalldocapp](../vsto/includes/appliesto-wdalldocapp-md.md)]  
  
## Drucken eines Dokuments, das ein Teil einer Anpassung auf Dokumentebene ist  
  
#### So drucken Sie das ganze Dokument  
  
1.  Rufen Sie die <xref:Microsoft.Office.Tools.Word.Document.PrintOut%2A>\-Methode der `ThisDocument`\-Klasse im Projekt auf, um das gesamte Dokument zu drucken. Um dieses Codebeispiel verwenden zu können, müssen Sie den Code in der `ThisDocument`\-Klasse ausführen.  
  
     [!code-csharp[Trin_VstcoreWordAutomation#11](../snippets/csharp/VS_Snippets_OfficeSP/Trin_VstcoreWordAutomation/CS/ThisDocument.cs#11)]
     [!code-vb[Trin_VstcoreWordAutomation#11](../snippets/visualbasic/VS_Snippets_OfficeSP/Trin_VstcoreWordAutomation/VB/ThisDocument.vb#11)]  
  
#### So drucken Sie die aktuelle Seite des Dokuments  
  
1.  Rufen Sie die <xref:Microsoft.Office.Tools.Word.Document.PrintOut%2A>\-Methode der `ThisDocument`\-Klasse im Projekt auf, und geben Sie an, dass eine Kopie der aktuellen Seite gedruckt werden soll. Um dieses Codebeispiel verwenden zu können, müssen Sie den Code in der `ThisDocument`\-Klasse ausführen.  
  
     [!code-csharp[Trin_VstcoreWordAutomation#12](../snippets/csharp/VS_Snippets_OfficeSP/Trin_VstcoreWordAutomation/CS/ThisDocument.cs#12)]
     [!code-vb[Trin_VstcoreWordAutomation#12](../snippets/visualbasic/VS_Snippets_OfficeSP/Trin_VstcoreWordAutomation/VB/ThisDocument.vb#12)]  
  
## Drucken eines Dokuments mithilfe eines VSTO\-Add\-Ins  
  
#### So drucken Sie ein ganzes Dokument  
  
1.  Rufen Sie die <xref:Microsoft.Office.Interop.Word._Document.PrintOut%2A>\-Methode des <xref:Microsoft.Office.Interop.Word.Document>\-Objekts auf, das Sie drucken möchten. Im folgenden Codebeispiel wird das aktive Dokument gedruckt. Wenn Sie dieses Beispiel verwenden möchten, führen Sie den Code von der `ThisAddIn`\-Klasse im Projekt aus.  
  
     [!code-csharp[Trin_VstcoreWordAutomationAddIn#11](../snippets/csharp/VS_Snippets_OfficeSP/Trin_VstcoreWordAutomationAddIn/CS/ThisAddIn.cs#11)]
     [!code-vb[Trin_VstcoreWordAutomationAddIn#11](../snippets/visualbasic/VS_Snippets_OfficeSP/Trin_VstcoreWordAutomationAddIn/VB/ThisAddIn.vb#11)]  
  
#### So drucken Sie die aktuelle Seite eines Dokuments  
  
1.  Rufen Sie die <xref:Microsoft.Office.Interop.Word._Document.PrintOut%2A>\-Methode des <xref:Microsoft.Office.Interop.Word.Document>\-Objekts auf, das Sie drucken möchten, und geben Sie an, dass eine Kopie der aktuellen Seite gedruckt werden soll. Im folgenden Codebeispiel wird das aktive Dokument gedruckt. Wenn Sie dieses Beispiel verwenden möchten, führen Sie den Code von der `ThisAddIn`\-Klasse im Projekt aus.  
  
     [!code-csharp[Trin_VstcoreWordAutomationAddIn#12](../snippets/csharp/VS_Snippets_OfficeSP/Trin_VstcoreWordAutomationAddIn/CS/ThisAddIn.cs#12)]
     [!code-vb[Trin_VstcoreWordAutomationAddIn#12](../snippets/visualbasic/VS_Snippets_OfficeSP/Trin_VstcoreWordAutomationAddIn/VB/ThisAddIn.vb#12)]  
  
## Siehe auch  
 [Optionale Parameter in Office-Lösungen](../vsto/optional-parameters-in-office-solutions.md)  
  
  