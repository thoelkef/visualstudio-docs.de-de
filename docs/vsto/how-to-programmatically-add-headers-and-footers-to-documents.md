---
title: "Gewusst wie: Programmgesteuertes Hinzuf&#252;gen von Kopf- und Fu&#223;zeilen zu Dokumenten"
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
  - "Dokumente [Office-Entwicklung in Visual Studio], Hinzufügen von Fußzeilen"
  - "Dokumente [Office-Entwicklung in Visual Studio], Hinzufügen von Kopfzeilen"
  - "Fußzeilen, Hinzufügen zu Dokumenten"
  - "Kopfzeilen, Hinzufügen zu Office-Dokumenten"
ms.assetid: c7a5cc8a-d8c0-48e9-81d3-108aa6bfbb74
caps.latest.revision: 24
author: "kempb"
ms.author: "kempb"
manager: "ghogen"
caps.handback.revision: 23
---
# Gewusst wie: Programmgesteuertes Hinzuf&#252;gen von Kopf- und Fu&#223;zeilen zu Dokumenten
  Sie können Kopf\- und Fußzeilen in Ihrem Dokument Text hinzufügen, indem Sie die Eigenschaft <xref:Microsoft.Office.Interop.Word.Section.Headers%2A> und die Eigenschaft <xref:Microsoft.Office.Interop.Word.Section.Footers%2A> von der<xref:Microsoft.Office.Interop.Word.Section> verwenden.  Jeder Abschnitt eines Dokuments enthält drei Kopf\- und Fußzeilen:  
  
-   <xref:Microsoft.Office.Interop.Word.WdHeaderFooterIndex.wdHeaderFooterPrimary>  
  
-   <xref:Microsoft.Office.Interop.Word.WdHeaderFooterIndex.wdHeaderFooterEvenPages>  
  
-   <xref:Microsoft.Office.Interop.Word.WdHeaderFooterIndex.wdHeaderFooterFirstPage>  
  
 Die Verfahren unterscheiden sich für Anpassungen auf Dokumentebene und VSTO\-Add\-Ins.  
  
 [!INCLUDE[appliesto_wdalldocapp](../vsto/includes/appliesto-wdalldocapp-md.md)]  
  
## Anpassungen auf Dokumentebene  
 Wenn Sie die folgenden Codebeispiele verwenden möchten, führen Sie sie aus der Klasse `ThisDocument` in Ihrem Projekt aus.  
  
#### So fügen Sie Fußzeilen im Dokument Text hinzu  
  
1.  Im folgenden Codebeispiel wird die Schriftart des Texts festgelegt, der in die primäre Fußzeile jedes Abschnitts des Dokuments eingefügt werden soll, und anschließend Text in die Fußzeile eingefügt.  
  
     [!code-csharp[Trin_VstcoreWordAutomation#114](../snippets/csharp/VS_Snippets_OfficeSP/Trin_VstcoreWordAutomation/CS/ThisDocument.cs#114)]
     [!code-vb[Trin_VstcoreWordAutomation#114](../snippets/visualbasic/VS_Snippets_OfficeSP/Trin_VstcoreWordAutomation/VB/ThisDocument.vb#114)]  
  
#### So fügen Sie Kopfzeilen im Dokument Text hinzu  
  
1.  Das folgende Codebeispiel fügt ein Feld hinzu, um die Seitenzahl in jeder Kopfzeile des Dokuments anzuzeigen, und legt dann die Absatzausrichtung fest, sodass der Text rechts am Header ausgerichtet wird.  
  
     [!code-csharp[Trin_VstcoreWordAutomation#116](../snippets/csharp/VS_Snippets_OfficeSP/Trin_VstcoreWordAutomation/CS/ThisDocument.cs#116)]
     [!code-vb[Trin_VstcoreWordAutomation#116](../snippets/visualbasic/VS_Snippets_OfficeSP/Trin_VstcoreWordAutomation/VB/ThisDocument.vb#116)]  
  
## VSTO\-Add\-Ins  
 Wenn Sie die folgenden Codebeispiele verwenden möchten, führen Sie sie aus der Klasse `ThisAddIn` in Ihrem Projekt aus.  
  
#### So fügen Sie Fußzeilen in einem Dokument Text hinzu  
  
1.  Im folgenden Codebeispiel wird die Schriftart des Texts festgelegt, der in die primäre Fußzeile jedes Abschnitts des Dokuments eingefügt werden soll, und anschließend Text in die Fußzeile eingefügt.  In diesem Codebeispiel wird das aktive Dokument verwendet.  
  
     [!code-csharp[Trin_VstcoreWordAutomationAddIn#114](../snippets/csharp/VS_Snippets_OfficeSP/Trin_VstcoreWordAutomationAddIn/CS/ThisAddIn.cs#114)]
     [!code-vb[Trin_VstcoreWordAutomationAddIn#114](../snippets/visualbasic/VS_Snippets_OfficeSP/Trin_VstcoreWordAutomationAddIn/VB/ThisAddIn.vb#114)]  
  
#### So fügen Sie Kopfzeilen im Dokument Text hinzu  
  
1.  Das folgende Codebeispiel fügt ein Feld hinzu, um die Seitenzahl in jeder Kopfzeile des Dokuments anzuzeigen, und legt dann die Absatzausrichtung fest, sodass der Text rechts am Header ausgerichtet wird.  In diesem Codebeispiel wird das aktive Dokument verwendet.  
  
     [!code-csharp[Trin_VstcoreWordAutomationAddIn#116](../snippets/csharp/VS_Snippets_OfficeSP/Trin_VstcoreWordAutomationAddIn/CS/ThisAddIn.cs#116)]
     [!code-vb[Trin_VstcoreWordAutomationAddIn#116](../snippets/visualbasic/VS_Snippets_OfficeSP/Trin_VstcoreWordAutomationAddIn/VB/ThisAddIn.vb#116)]  
  
## Siehe auch  
 [Gewusst wie: Programmgesteuertes Erstellen neuer Dokumente](../vsto/how-to-programmatically-create-new-documents.md)   
 [Gewusst wie: Programmgesteuertes Erweitern von Bereichen in Dokumenten](../vsto/how-to-programmatically-extend-ranges-in-documents.md)   
 [Gewusst wie: Programmgesteuertes Durchlaufen gefundener Elemente in Dokumenten](../vsto/how-to-programmatically-loop-through-found-items-in-documents.md)  
  
  