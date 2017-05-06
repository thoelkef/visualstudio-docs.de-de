---
title: "Gewusst wie: Programmgesteuertes Aktualisieren von Lesezeichentext"
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
  - "Bookmark-Steuerelement, Aktualisieren des Inhalts"
  - "Lesezeichen, Aktualisieren von Text"
  - "Text [Office-Entwicklung in Visual Studio], Aktualisieren in Lesezeichen"
ms.assetid: 2324164d-2538-4695-9aaf-7285ce403be3
caps.latest.revision: 46
author: "kempb"
ms.author: "kempb"
manager: "ghogen"
caps.handback.revision: 45
---
# Gewusst wie: Programmgesteuertes Aktualisieren von Lesezeichentext
  Sie können Text in ein Platzhalterlesezeichen in einem Microsoft Office Word\-Dokument einfügen, um den Text zu einem späteren Zeitpunkt abzurufen oder Text in einem Lesezeichen zu ersetzen.  Wenn Sie eine Anpassung auf Dokumentebene entwickeln, können Sie auch Text in einem an Daten gebundenen <xref:Microsoft.Office.Tools.Word.Bookmark>\-Steuerelement aktualisieren.  Weitere Informationen finden Sie unter [Binden von Daten an Steuerelemente in Office-Projektmappen](../vsto/binding-data-to-controls-in-office-solutions.md).  
  
 [!INCLUDE[appliesto_wdalldocapp](../vsto/includes/appliesto-wdalldocapp-md.md)]  
  
 Das Lesezeichenobjekt kann einem von zwei Typen entsprechen:  
  
-   Einem <xref:Microsoft.Office.Tools.Word.Bookmark>\-Hoststeuerelement.  
  
     <xref:Microsoft.Office.Tools.Word.Bookmark>\-Steuerelemente erweitern systemeigene <xref:Microsoft.Office.Interop.Word.Bookmark>\-Objekte, indem sie die Datenbindung aktivieren und Ereignisse verfügbar machen.  Weitere Informationen zu Hoststeuerelementen finden Sie unter [Übersicht über Hostelemente und Hoststeuerelemente](../vsto/host-items-and-host-controls-overview.md).  
  
-   Einem systemeigene <xref:Microsoft.Office.Interop.Word.Bookmark>\-Objekt.  
  
     <xref:Microsoft.Office.Interop.Word.Bookmark>\-Objekte verfügen über keine Ereignisse oder Datenbindungsfunktionen.  
  
 Wenn Sie einem Lesezeichen Text zuordnen, unterscheidet sich das Verhalten zwischen <xref:Microsoft.Office.Interop.Word.Bookmark> und <xref:Microsoft.Office.Tools.Word.Bookmark>.  Weitere Informationen finden Sie unter [Bookmark-Steuerelement](../vsto/bookmark-control.md).  
  
## Verwenden von Hoststeuerelementen  
  
#### So aktualisieren Lesezeicheninhalte mithilfe des Lesezeichen\-Steuerelements  
  
1.  Erstellen Sie eine Prozedur, die ein `bookmark`\-Argument für den Namen des Lesezeichens akzeptiert, und ein`newText`\-Argument für die Zeichenfolge zum Zuweisen der <xref:Microsoft.Office.Tools.Word.Bookmark.Text%2A>\-Eigenschaft.  
  
    > [!NOTE]  
    >  Die Zuweisung von Text zu den Eigenschaften <xref:Microsoft.Office.Tools.Word.Bookmark.Text%2A> oder <xref:Microsoft.Office.Tools.Word.Bookmark.FormattedText%2A> eines <xref:Microsoft.Office.Tools.Word.Bookmark>\-Steuerelements führt nicht dazu, dass das Lesezeichen gelöscht wird.  
  
     [!code-csharp[Trin_VstcoreWordAutomation#63](../snippets/csharp/VS_Snippets_OfficeSP/Trin_VstcoreWordAutomation/CS/ThisDocument.cs#63)]
     [!code-vb[Trin_VstcoreWordAutomation#63](../snippets/visualbasic/VS_Snippets_OfficeSP/Trin_VstcoreWordAutomation/VB/ThisDocument.vb#63)]  
  
2.  Weisen Sie der <xref:Microsoft.Office.Tools.Word.Bookmark.Text%2A>\-Eigenschaft von <xref:Microsoft.Office.Tools.Word.Bookmark> die *newText*\-Zeichenfolge zu.  
  
     [!code-csharp[Trin_VstcoreWordAutomation#64](../snippets/csharp/VS_Snippets_OfficeSP/Trin_VstcoreWordAutomation/CS/ThisDocument.cs#64)]
     [!code-vb[Trin_VstcoreWordAutomation#64](../snippets/visualbasic/VS_Snippets_OfficeSP/Trin_VstcoreWordAutomation/VB/ThisDocument.vb#64)]  
  
## Verwenden von Word\-Objekten  
  
#### So aktualisieren Lesezeicheninhalte mithilfe eines Word\-Lesezeichenobjekts  
  
1.  Erstellen Sie eine Prozedur, die ein `bookmark`\-Argument für den Namen von <xref:Microsoft.Office.Interop.Word.Bookmark> und ein `newText`\-Argument für die Zeichenfolge zur Zuweisung zur <xref:Microsoft.Office.Interop.Word.Range.Text%2A>\-Eigenschaft des Lesezeichens enthält.  
  
    > [!NOTE]  
    >  Die Zuweisung von Text zu einem systemeigenen Word\-<xref:Microsoft.Office.Interop.Word.Bookmark>\-Objekt führt nicht dazu, dass das Lesezeichen gelöscht wird.  
  
     [!code-csharp[Trin_VstcoreWordAutomation#65](../snippets/csharp/VS_Snippets_OfficeSP/Trin_VstcoreWordAutomation/CS/ThisDocument.cs#65)]
     [!code-vb[Trin_VstcoreWordAutomation#65](../snippets/visualbasic/VS_Snippets_OfficeSP/Trin_VstcoreWordAutomation/VB/ThisDocument.vb#65)]  
  
2.  Weisen Sie die *newText*\-Zeichenfolge der <xref:Microsoft.Office.Interop.Word.Range.Text%2A>\-Eigenschaft des Lesezeichens zu, wodurch das Lesezeichen automatisch gelöscht wird.  Fügen Sie das Lesezeichen der <xref:Microsoft.Office.Interop.Word.Bookmarks>\-Auflistung dann erneut hinzu.  
  
     Das folgende Codebeispiel kann in einer Anpassung auf Dokumentebene verwendet werden.  
  
     [!code-csharp[Trin_VstcoreWordAutomation#66](../snippets/csharp/VS_Snippets_OfficeSP/Trin_VstcoreWordAutomation/CS/ThisDocument.cs#66)]
     [!code-vb[Trin_VstcoreWordAutomation#66](../snippets/visualbasic/VS_Snippets_OfficeSP/Trin_VstcoreWordAutomation/VB/ThisDocument.vb#66)]  
  
     Das folgende Codebeispiel kann in einem VSTO\-Add\-In verwendet werden.  In diesem Beispiel wird das aktive Dokument verwendet.  
  
     [!code-csharp[Trin_VstcoreWordAutomationAddIn#66](../snippets/csharp/VS_Snippets_OfficeSP/Trin_VstcoreWordAutomationAddIn/CS/ThisAddIn.cs#66)]
     [!code-vb[Trin_VstcoreWordAutomationAddIn#66](../snippets/visualbasic/VS_Snippets_OfficeSP/Trin_VstcoreWordAutomationAddIn/VB/ThisAddIn.vb#66)]  
  
## Siehe auch  
 [Gewusst wie: Programmgesteuertes Einfügen von Text in Word-Dokumente](../vsto/how-to-programmatically-insert-text-into-word-documents.md)   
 [Übersicht über das Word-Objektmodell](../vsto/word-object-model-overview.md)   
 [Bookmark-Steuerelement](../vsto/bookmark-control.md)  
  
  