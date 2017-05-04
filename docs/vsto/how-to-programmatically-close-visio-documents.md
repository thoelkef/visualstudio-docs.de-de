---
title: "Gewusst wie: Programmgesteuertes Schlie&#223;en von Visio-Dokumenten | Microsoft Docs"
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
  - "Dokumente [Office-Entwicklung in Visual Studio], Schließen von Visio-Dokumenten"
  - "Visio [Office-Entwicklung in Visual Studio], Schließen von Visio-Dokumenten"
ms.assetid: 59c0e215-a4c1-4b39-a491-37534f172705
caps.latest.revision: 13
author: "kempb"
ms.author: "kempb"
manager: "ghogen"
caps.handback.revision: 12
---
# Gewusst wie: Programmgesteuertes Schlie&#223;en von Visio-Dokumenten
  Sie können das aktive Microsoft Office Visio\-Dokument schließen, indem Sie die Microsoft.Office.Interop.Visio.Document.Close\-Methode verwenden.  
  
 Ausführliche Informationen zu dieser Methode finden Sie in der VBA\-Referenzdokumentation für die [Microsoft.Office.Interop.Visio.Document.Close](HV10070225)\-Methode.  
  
## Schließen des aktiven Dokuments  
  
#### So schließen Sie das aktive Dokument  
  
-   Rufen Sie die Microsoft.Office.Interop.Visio.Document.Close\-Methode auf, um das aktive Dokument zu schließen.  
  
     Um das folgende Codebeispiel zu verwenden, führen sie es in der `ThisAddIn`\-Klasse in einem VSTO\-Add\-In\-Projekt für Visio aus.  
  
     [!code-csharp[Trin_VstcoreVisioAutomationAddIn#7](../snippets/csharp/VS_Snippets_OfficeSP/Trin_VstcoreVisioAutomationAddIn/CS/ThisAddIn.cs#7)]
     [!code-vb[Trin_VstcoreVisioAutomationAddIn#7](../snippets/visualbasic/VS_Snippets_OfficeSP/Trin_VstcoreVisioAutomationAddIn/VB/ThisAddIn.vb#7)]  
  
## Siehe auch  
 [Visio-Projektmappen](../vsto/visio-solutions.md)   
 [Übersicht über das Visio-Objektmodell](../vsto/visio-object-model-overview.md)   
 [Gewusst wie: Programmgesteuertes Erstellen neuer Visio-Dokumente](../vsto/how-to-programmatically-create-new-visio-documents.md)   
 [Gewusst wie: Programmgesteuertes Öffnen von Visio-Dokumenten](../vsto/how-to-programmatically-open-visio-documents.md)   
 [Gewusst wie: Programmgesteuertes Speichern von Visio-Dokumenten](../vsto/how-to-programmatically-save-visio-documents.md)   
 [Gewusst wie: Programmgesteuertes Drucken von Visio-Dokumenten](../vsto/how-to-programmatically-print-visio-documents.md)  
  
  