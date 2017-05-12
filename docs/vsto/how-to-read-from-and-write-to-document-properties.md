---
title: "Gewusst wie: Lesen von und Schreiben in Dokumenteigenschaften"
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
  - "Word [Office-Entwicklung in Visual Studio], Dokumenteigenschaften"
  - "Dokumente [Office-Entwicklung in Visual Studio], Eigenschaften"
  - "Dokumenteigenschaften [Office-Entwicklung in Visual Studio]"
  - "Excel [Office-Entwicklung in Visual Studio], Dokumenteigenschaften"
ms.assetid: e9ef9fa3-36b9-48fb-8148-f5152463c03c
caps.latest.revision: 54
author: "kempb"
ms.author: "kempb"
manager: "ghogen"
caps.handback.revision: 53
---
# Gewusst wie: Lesen von und Schreiben in Dokumenteigenschaften
  Sie können Dokumenteigenschaften zusammen mit einem Dokument speichern. Office\-Anwendungen stellen eine Reihe integrierter Eigenschaften \(z. B. Autor, Titel und Betreff\) bereit. In diesem Thema wird gezeigt, wie Dokumenteigenschaften in Microsoft Office Excel und Microsoft Office Word festgelegt werden.  
  
 ![Link zu Video](../vsto/media/playvideo.png "Link zu Video") Eine entsprechende Videodemo finden Sie unter [Gewusst wie: Zugreifen auf und Bearbeiten von benutzerdefinierten Dokumenteigenschaften in Microsoft Word](http://go.microsoft.com/fwlink/?LinkId=136772).  
  
 [!INCLUDE[appliesto_docprops](../vsto/includes/appliesto-docprops-md.md)]  
  
## Festlegen von Dokumenteigenschaften in Excel  
 Verwenden Sie die folgenden Eigenschaften, um in Excel mit integrierten Eigenschaften zu arbeiten:  
  
-   In einem Projekt auf Dokumentebene verwenden Sie die Eigenschaft <xref:Microsoft.Office.Tools.Excel.Workbook.BuiltinDocumentProperties%2A> der Klasse `ThisWorkbook`.  
  
-   Verwenden Sie in einem VSTO\-Add\-In\-Projekt die Eigenschaft <xref:Microsoft.Office.Interop.Excel._Workbook.BuiltinDocumentProperties%2A> eines <xref:Microsoft.Office.Interop.Excel.Workbook>\-Objekts.  
  
 Diese Eigenschaften geben eine <xref:Microsoft.Office.Core.DocumentProperties>\-Objekt zurück, das eine Auflistung von <xref:Microsoft.Office.Core.DocumentProperty>\-Objekten ist. Sie können die Eigenschaft `Item` der Auflistung verwenden, um eine bestimmte Eigenschaft nach Name oder Index in der Auflistung abzurufen.  
  
 Im folgenden Codebeispiel wird veranschaulicht, wie die integrierte Eigenschaft **Revision Number** in einem Projekt auf Dokumentebene geändert wird.  
  
#### So ändern Sie die Eigenschaft "Revisionsnummer" in Excel  
  
1.  Weisen Sie die integrierten Eigenschaften einer Variablen zu.  
  
     [!code-csharp[Trin_VstcoreProgramming#7](../snippets/csharp/VS_Snippets_OfficeSP/Trin_VstcoreProgramming/CS/ThisWorkbook.cs#7)]
     [!code-vb[Trin_VstcoreProgramming#7](../snippets/visualbasic/VS_Snippets_OfficeSP/Trin_VstcoreProgramming/VB/ThisWorkbook.vb#7)]  
  
2.  Inkrementieren Sie die Eigenschaft `Revision Number` um eins.  
  
     [!code-csharp[Trin_VstcoreProgramming#8](../snippets/csharp/VS_Snippets_OfficeSP/Trin_VstcoreProgramming/CS/ThisWorkbook.cs#8)]
     [!code-vb[Trin_VstcoreProgramming#8](../snippets/visualbasic/VS_Snippets_OfficeSP/Trin_VstcoreProgramming/VB/ThisWorkbook.vb#8)]  
  
## Festlegen von Dokumenteigenschaften in Word  
 Verwenden Sie die folgenden Eigenschaften, um in Word mit integrierten Eigenschaften zu arbeiten:  
  
-   In einem Projekt auf Dokumentebene verwenden Sie die Eigenschaft <xref:Microsoft.Office.Tools.Word.Document.BuiltInDocumentProperties%2A> der Klasse `ThisDocument`.  
  
-   Verwenden Sie in einem VSTO\-Add\-In\-Projekt die Eigenschaft <xref:Microsoft.Office.Interop.Word._Document.BuiltInDocumentProperties%2A> eines <xref:Microsoft.Office.Interop.Word.Document>\-Objekts.  
  
 Diese Eigenschaften geben eine <xref:Microsoft.Office.Core.DocumentProperties>\-Objekt zurück, das eine Auflistung von <xref:Microsoft.Office.Core.DocumentProperty>\-Objekten ist. Sie können die Eigenschaft `Item` der Auflistung verwenden, um eine bestimmte Eigenschaft nach Name oder Index in der Auflistung abzurufen.  
  
 Im folgenden Codebeispiel wird veranschaulicht, wie die integrierte Eigenschaft **Subject** in einem Projekt auf Dokumentebene geändert wird.  
  
#### So ändern Sie die Eigenschaft "Subject"  
  
1.  Weisen Sie die integrierten Eigenschaften einer Variablen zu.  
  
     [!code-csharp[Trin_VstcoreProgrammingWord#1](../snippets/csharp/VS_Snippets_OfficeSP/Trin_VstcoreProgrammingWord/CS/ThisDocument.cs#1)]
     [!code-vb[Trin_VstcoreProgrammingWord#1](../snippets/visualbasic/VS_Snippets_OfficeSP/Trin_VstcoreProgrammingWord/VB/ThisDocument.vb#1)]  
  
2.  Ändern Sie die Eigenschaft `Subject` in "Whitepaper".  
  
     [!code-csharp[Trin_VstcoreProgrammingWord#2](../snippets/csharp/VS_Snippets_OfficeSP/Trin_VstcoreProgrammingWord/CS/ThisDocument.cs#2)]
     [!code-vb[Trin_VstcoreProgrammingWord#2](../snippets/visualbasic/VS_Snippets_OfficeSP/Trin_VstcoreProgrammingWord/VB/ThisDocument.vb#2)]  
  
## Robuste Programmierung  
 In den Beispielen wird davon ausgegangen, dass Sie den Code in der Klasse `ThisWorkbook` in einem Projekt auf Dokumentebene für Excel und in der Klasse `ThisDocument` in einem Projekt auf Dokumentebene für Word geschrieben haben.  
  
 Auch wenn Sie mit Word und Excel und deren Objekten arbeiten, stellt Microsoft Office die Liste der verfügbaren integrierten Dokumenteigenschaften zur Verfügung. Wenn versucht wird, auf eine nicht definierte Eigenschaft zuzugreifen, wird eine Ausnahme ausgelöst.  
  
## Siehe auch  
 [Programmieren von VSTO-Add-Ins](../vsto/programming-vsto-add-ins.md)   
 [Programmieren von Anpassungen auf Dokumentebene](../vsto/programming-document-level-customizations.md)   
 [Gewusst wie: Erstellen und Ändern von benutzerdefinierten Dokumenteigenschaften](../vsto/how-to-create-and-modify-custom-document-properties.md)  
  
  