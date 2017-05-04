---
title: "Gewusst wie: Programmgesteuertes Sch&#252;tzen von Dokumenten und Dokumentteilen | Microsoft Docs"
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
  - "Dokumentschutz"
  - "Dokumente [Office-Entwicklung in Visual Studio], Dokumentschutz"
  - "Word-Dokumente, Schutz"
ms.assetid: af8390fc-c4c7-48c7-94b8-4fedbaac0757
caps.latest.revision: 25
author: "kempb"
ms.author: "kempb"
manager: "ghogen"
caps.handback.revision: 24
---
# Gewusst wie: Programmgesteuertes Sch&#252;tzen von Dokumenten und Dokumentteilen
  Sie können Schutz zu einem Microsoft Office Word\-Dokument hinzufügen, um zu verhindern, dass Benutzer irgendwelche Änderungen an dem Dokument vornehmen können.  
  
 [!INCLUDE[appliesto_wdalldocapp](../vsto/includes/appliesto-wdalldocapp-md.md)]  
  
 Sie können auch bestimmte Bereiche des Dokuments als Ausnahmen markieren, sodass angegebene Benutzer lediglich diese Bereiche des Dokuments bearbeiten können. Beispielsweise könnten Sie ein gesamtes Dokument mit Ausnahme eines bestimmten Lesezeichens schützen. Optional können Sie ein Kennwort hinzufügen, sodass Benutzer den Dokumentschutz nur aufheben können, wenn ihnen das Kennwort bekannt ist.  
  
> [!NOTE]  
>  Im folgenden Beispiel wird kein Kennwortschutz verwendet. Wenn Sie Dokumentschutz hinzufügen, empfiehlt es sich aber, ein Kennwort zu verwenden.  Weitere Informationen finden Sie im Dokumentschutz\-Beispiel unter [Beispiele und exemplarische Vorgehensweisen für die Programmierung mit Office](../vsto/office-development-samples-and-walkthroughs.md).  
  
 Sie können auch Inhaltssteuerelemente verwenden, um Teile von Dokumenten zu schützen.  Weitere Informationen finden Sie unter [Gewusst wie: Schützen von Teilen von Dokumenten mithilfe von Inhaltssteuerelementen](../vsto/how-to-protect-parts-of-documents-by-using-content-controls.md).  
  
## Schützen eines Dokuments, das Bestandteil einer Anpassung auf Dokumentebene ist  
  
#### So schützen Sie ein Dokument, das Bestandteil einer Anpassung auf Dokumentebene ist  
  
1.  Rufen Sie in Ihrem Projekt die <xref:Microsoft.Office.Tools.Word.Document.Protect%2A>\-Methode der `ThisDocument`\-Klasse auf.  
  
     [!code-csharp[Trin_VstcoreWordAutomation#111](../snippets/csharp/VS_Snippets_OfficeSP/Trin_VstcoreWordAutomation/CS/ThisDocument.cs#111)]
     [!code-vb[Trin_VstcoreWordAutomation#111](../snippets/visualbasic/VS_Snippets_OfficeSP/Trin_VstcoreWordAutomation/VB/ThisDocument.vb#111)]  
  
#### So schließen Sie ein Lesezeichen\-Steuerelement vom Dokumentschutz aus  
  
1.  Schützen Sie das gesamte Dokument mit der <xref:Microsoft.Office.Tools.Word.Document.Protect%2A>\-Methode.  
  
     [!code-csharp[Trin_VstcoreWordAutomation#111](../snippets/csharp/VS_Snippets_OfficeSP/Trin_VstcoreWordAutomation/CS/ThisDocument.cs#111)]
     [!code-vb[Trin_VstcoreWordAutomation#111](../snippets/visualbasic/VS_Snippets_OfficeSP/Trin_VstcoreWordAutomation/VB/ThisDocument.vb#111)]  
  
2.  Schließen Sie `Bookmark1` vom Dokumentschutz aus.  
  
     [!code-csharp[Trin_VstcoreWordAutomation#112](../snippets/csharp/VS_Snippets_OfficeSP/Trin_VstcoreWordAutomation/CS/ThisDocument.cs#112)]
     [!code-vb[Trin_VstcoreWordAutomation#112](../snippets/visualbasic/VS_Snippets_OfficeSP/Trin_VstcoreWordAutomation/VB/ThisDocument.vb#112)]  
  
### Kompilieren des Codes  
 Wenn Sie diese Codebeispiele verwenden möchten, führen Sie sie in Ihrem Projekt aus der `ThisDocument`\-Klasse aus. Für diese Codebeispiele wird davon ausgegangen, dass ein <xref:Microsoft.Office.Tools.Word.Bookmark>\-Steuerelement namens `Bookmark1` im Dokument vorhanden ist, in dem sich dieser Code befindet.  
  
## Schützen eines Dokuments mithilfe eines VSTO\-Add\-Ins  
  
#### So schützen Sie ein Dokument mithilfe eines VSTO\-Add\-Ins auf Anwendungsebene  
  
1.  Rufen Sie die <xref:Microsoft.Office.Interop.Word._Document.Protect%2A>\-Methode des <xref:Microsoft.Office.Interop.Word.Document>\-Objekts auf, das Sie schützen möchten.  
  
     Im folgenden Codebeispiel wird das aktive Dokument geschützt. Wenn Sie dieses Codebeispiel verwenden möchten, führen Sie es von der `ThisAddIn`\-Klasse im Projekt aus.  
  
     [!code-csharp[Trin_VstcoreWordAutomationAddIn#111](../snippets/csharp/VS_Snippets_OfficeSP/Trin_VstcoreWordAutomationAddIn/CS/ThisAddIn.cs#111)]
     [!code-vb[Trin_VstcoreWordAutomationAddIn#111](../snippets/visualbasic/VS_Snippets_OfficeSP/Trin_VstcoreWordAutomationAddIn/VB/ThisAddIn.vb#111)]  
  
## Siehe auch  
 [Dokumentschutz in Projektmappen auf Dokumentebene](../vsto/document-protection-in-document-level-solutions.md)   
 [Kennwortschutz für Office-Dokumente](../vsto/password-protection-on-office-documents.md)   
 [Gewusst wie: Zulassen der Ausführung von Code im Hintergrund von Dokumenten mit eingeschränkten Berechtigungen](../vsto/how-to-permit-code-to-run-behind-documents-with-restricted-permissions.md)   
 [Gewusst wie: Hinzufügen von Bookmark-Steuerelementen zu Word-Dokumenten](../vsto/how-to-add-bookmark-controls-to-word-documents.md)   
 [Entwerfen und Erstellen von Office-Lösungen](../vsto/designing-and-creating-office-solutions.md)  
  
  