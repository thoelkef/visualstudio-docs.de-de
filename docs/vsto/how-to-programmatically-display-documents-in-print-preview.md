---
title: "Gewusst wie: Programmgesteuertes Anzeigen von Dokumenten in der Seitenansicht"
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
  - "Word [Office-Entwicklung in Visual Studio], Anzeigen von Dokumenten in der Seitenansicht"
  - "Dokumente [Office-Entwicklung in Visual Studio], Anzeigen in der Seitenansicht"
ms.assetid: 96c7faea-9c5c-42b4-a009-08894a6d15c9
caps.latest.revision: 39
author: "kempb"
ms.author: "kempb"
manager: "ghogen"
caps.handback.revision: 38
---
# Gewusst wie: Programmgesteuertes Anzeigen von Dokumenten in der Seitenansicht
  Wenn Ihre Projektmappe einen Bericht generiert, können Sie dem Benutzer den Bericht im Seitenansichtsmodus anzeigen.  
  
 [!INCLUDE[appliesto_wdalldocapp](../vsto/includes/appliesto-wdalldocapp-md.md)]  
  
## Verfahren für Anpassungen auf Dokumentebene  
  
#### So zeigen Sie ein Dokument durch Aufrufen der „PrintPreview“\-Methode in der Seitenansicht an  
  
1.  Rufen Sie die <xref:Microsoft.Office.Tools.Word.Document.PrintPreview%2A>\-Methode der <xref:Microsoft.Office.Tools.Word.Document>\-Klasse auf. Wenn Sie dieses Codebeispiel verwenden möchten, führen Sie es von der `ThisDocument`\-Klasse im Projekt aus.  
  
     [!code-csharp[Trin_VstcoreWordAutomation#13](../snippets/csharp/VS_Snippets_OfficeSP/Trin_VstcoreWordAutomation/CS/ThisDocument.cs#13)]
     [!code-vb[Trin_VstcoreWordAutomation#13](../snippets/visualbasic/VS_Snippets_OfficeSP/Trin_VstcoreWordAutomation/VB/ThisDocument.vb#13)]  
  
#### So zeigen Sie ein Dokument durch Festlegen der „PrintPreview“\-Eigenschaft in der Seitenansicht an  
  
1.  Legen Sie die <xref:Microsoft.Office.Interop.Word._Application.PrintPreview%2A>\-Eigenschaft des <xref:Microsoft.Office.Interop.Word.Application>\-Objekts auf **true** fest.  
  
     [!code-csharp[Trin_VstcoreWordAutomation#14](../snippets/csharp/VS_Snippets_OfficeSP/Trin_VstcoreWordAutomation/CS/ThisDocument.cs#14)]
     [!code-vb[Trin_VstcoreWordAutomation#14](../snippets/visualbasic/VS_Snippets_OfficeSP/Trin_VstcoreWordAutomation/VB/ThisDocument.vb#14)]  
  
## Verfahren für VSTO\-Add\-Ins  
  
#### So zeigen Sie ein Dokument durch Aufrufen der „PrintPreview“\-Methode in der Seitenansicht an  
  
1.  Rufen Sie die <xref:Microsoft.Office.Interop.Word._Document.PrintPreview%2A>\-Methode des <xref:Microsoft.Office.Interop.Word.Document>\-Objekts auf, für das Sie eine Vorschau anzeigen möchten. Wenn Sie dieses Codebeispiel verwenden möchten, führen Sie es von der `ThisAddIn`\-Klasse im Projekt aus.  
  
     [!code-csharp[Trin_VstcoreWordAutomationAddIn#13](../snippets/csharp/VS_Snippets_OfficeSP/Trin_VstcoreWordAutomationAddIn/CS/ThisAddIn.cs#13)]
     [!code-vb[Trin_VstcoreWordAutomationAddIn#13](../snippets/visualbasic/VS_Snippets_OfficeSP/Trin_VstcoreWordAutomationAddIn/VB/ThisAddIn.vb#13)]  
  
#### So zeigen Sie ein Dokument durch Festlegen der „PrintPreview“\-Eigenschaft in der Seitenansicht an  
  
1.  Legen Sie die <xref:Microsoft.Office.Interop.Word._Application.PrintPreview%2A>\-Eigenschaft des <xref:Microsoft.Office.Interop.Word.Application>\-Objekts auf **true** fest.  
  
     [!code-csharp[Trin_VstcoreWordAutomation#14](../snippets/csharp/VS_Snippets_OfficeSP/Trin_VstcoreWordAutomation/CS/ThisDocument.cs#14)]
     [!code-vb[Trin_VstcoreWordAutomation#14](../snippets/visualbasic/VS_Snippets_OfficeSP/Trin_VstcoreWordAutomation/VB/ThisDocument.vb#14)]  
  
## Siehe auch  
 [Gewusst wie: Programmgesteuertes Drucken von Dokumenten](../vsto/how-to-programmatically-print-documents.md)   
 [Gewusst wie: Programmgesteuertes Öffnen vorhandener Dokumente](../vsto/how-to-programmatically-open-existing-documents.md)   
 [Gewusst wie: Programmgesteuertes Erstellen neuer Dokumente](../vsto/how-to-programmatically-create-new-documents.md)  
  
  