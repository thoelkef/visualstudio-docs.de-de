---
title: "Gewusst wie: Erstellen und &#196;ndern von benutzerdefinierten Dokumenteigenschaften"
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
  - "Benutzerdefinierte Dokumenteigenschaften"
  - "Dokumente [Office-Entwicklung in Visual Studio], Eigenschaften"
  - "Dokumenteigenschaften [Office-Entwicklung in Visual Studio]"
ms.assetid: 99d9dfaf-891f-4f3b-a580-67362afdaf34
caps.latest.revision: 47
author: "kempb"
ms.author: "kempb"
manager: "ghogen"
caps.handback.revision: 46
---
# Gewusst wie: Erstellen und &#196;ndern von benutzerdefinierten Dokumenteigenschaften
  Die oben aufgeführten Microsoft Office\-Anwendung bieten integrierte Eigenschaften, die mit Dokumenten gespeichert werden. Darüber hinaus können Sie benutzerdefinierte Dokumenteigenschaften erstellen und ändern, falls Sie zusätzliche Informationen mit dem Dokument speichern möchten.  
  
 [!INCLUDE[appliesto_docprops](../vsto/includes/appliesto-docprops-md.md)]  
  
 Verwenden Sie die CustomDocumentProperties\-Eigenschaft eines Dokuments, um mit benutzerdefinierten Eigenschaften zu arbeiten. Verwenden Sie in einem Projekt auf Dokumentebene für Microsoft Office Excel z. B. die <xref:Microsoft.Office.Tools.Excel.Workbook.CustomDocumentProperties%2A>\-Eigenschaft der `ThisWorkbook`\-Klasse. Verwenden Sie in einem VSTO\-Add\-In\-Projekt für Excel die <xref:Microsoft.Office.Interop.Excel._Workbook.CustomDocumentProperties%2A>\-Eigenschaft eines <xref:Microsoft.Office.Interop.Excel.Workbook>\-Objekts. Diese Eigenschaften geben ein <xref:Microsoft.Office.Core.DocumentProperties>\-Objekt zurück, das eine Auflistung von <xref:Microsoft.Office.Core.DocumentProperty>\-Objekten ist. Sie können die `Item`\-Eigenschaft der Auflistung verwenden, um eine bestimmte Eigenschaft nach Namen oder Index in der Auflistung abzurufen.  
  
 Das folgende Beispiel veranschaulicht, wie eine benutzerdefinierte Eigenschaft in einer Anpassung auf Dokumentebene für Excel hinzugefügt und ihr ein Wert zugewiesen wird.  
  
 ![Link zu Video](~/docs/data-tools/media/playvideo.gif "Link zu Video") [Gewusst wie: Zugreifen auf und Bearbeiten von benutzerdefinierten Dokumenteigenschaften in Microsoft Word](http://go.microsoft.com/fwlink/?LinkId=136772).  
  
## Beispiel  
 [!code-csharp[Trin_VstcoreProgramming#6](../snippets/csharp/VS_Snippets_OfficeSP/Trin_VstcoreProgramming/CS/ThisWorkbook.cs#6)]
 [!code-vb[Trin_VstcoreProgramming#6](../snippets/visualbasic/VS_Snippets_OfficeSP/Trin_VstcoreProgramming/VB/ThisWorkbook.vb#6)]  
  
## Robuste Programmierung  
 Beim Versuch, auf die `Value`\-Eigenschaft für nicht definierte Eigenschaften zuzugreifen, wird eine Ausnahme ausgelöst.  
  
## Siehe auch  
 [Programmieren von VSTO-Add-Ins](../vsto/programming-vsto-add-ins.md)   
 [Programmieren von Anpassungen auf Dokumentebene](../vsto/programming-document-level-customizations.md)   
 [Gewusst wie: Lesen von und Schreiben in Dokumenteigenschaften](../vsto/how-to-read-from-and-write-to-document-properties.md)  
  
  