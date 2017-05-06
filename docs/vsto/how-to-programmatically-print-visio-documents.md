---
title: "Gewusst wie: Programmgesteuertes Drucken von Visio-Dokumenten"
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
  - "Visio [Office-Entwicklung in Visual Studio], Drucken von Visio-Dokumenten"
  - "Dokumente [Office-Entwicklung in Visual Studio], Drucken von Visio-Dokumenten"
ms.assetid: 606a2678-5eb8-40b2-a50a-305cecb1b3d4
caps.latest.revision: 17
author: "kempb"
ms.author: "kempb"
manager: "ghogen"
caps.handback.revision: 17
---
# Gewusst wie: Programmgesteuertes Drucken von Visio-Dokumenten
  Sie können ein vollständiges Microsoft Office Visio\-Dokument oder nur eine bestimmte Seite drucken.  
  
 Ausführliche Informationen zu den Druckmethoden finden Sie in der VBA\-Referenzdokumentation für die [Microsoft.Office.Interop.Visio.Document.Print](HV10070345)\-Methode und [Microsoft.Office.Interop.Visio.Page.Print](HV10070404)\-Methode.  
  
## Drucken eines Visio\-Dokuments  
  
#### So drucken Sie ein vollständiges Dokument  
  
-   Rufen Sie die Microsoft.Office.Interop.Visio.Document.Print\-Methode des Microsoft.Office.Interop.Visio.Document\-Objekts auf, das Sie drucken möchten.  
  
     Im folgenden Codebeispiel wird das aktive Dokument gedruckt. Wenn Sie dieses Beispiel verwenden möchten, führen Sie den Code von der `ThisAddIn`\-Klasse im Projekt aus.  
  
     [!code-csharp[Trin_VstcoreVisioAutomationAddIn#8](../snippets/csharp/VS_Snippets_OfficeSP/Trin_VstcoreVisioAutomationAddIn/CS/ThisAddIn.cs#8)]
     [!code-vb[Trin_VstcoreVisioAutomationAddIn#8](../snippets/visualbasic/VS_Snippets_OfficeSP/Trin_VstcoreVisioAutomationAddIn/VB/ThisAddIn.vb#8)]  
  
## Drucken einer Seite eines Visio\-Dokuments  
  
#### So drucken Sie eine Seite eines Dokuments  
  
-   Rufen Sie die Microsoft.Office.Interop.Visio.Pages.Print\-Methode des Microsoft.Office.Interop.Visio.Pages\-Objekts auf, das Sie drucken möchten.  
  
     Im folgenden Codebeispiel wird die erste Seite des aktiven Dokuments gedruckt. Wenn Sie dieses Beispiel verwenden möchten, führen Sie den Code von der `ThisAddIn`\-Klasse im Projekt aus.  
  
     [!code-csharp[Trin_VstcoreVisioAutomationAddIn#9](../snippets/csharp/VS_Snippets_OfficeSP/Trin_VstcoreVisioAutomationAddIn/CS/ThisAddIn.cs#9)]
     [!code-vb[Trin_VstcoreVisioAutomationAddIn#9](../snippets/visualbasic/VS_Snippets_OfficeSP/Trin_VstcoreVisioAutomationAddIn/VB/ThisAddIn.vb#9)]  
  
## Siehe auch  
 [Visio-Projektmappen](../vsto/visio-solutions.md)   
 [Übersicht über das Visio-Objektmodell](../vsto/visio-object-model-overview.md)   
 [Gewusst wie: Programmgesteuertes Erstellen neuer Visio-Dokumente](../vsto/how-to-programmatically-create-new-visio-documents.md)   
 [Gewusst wie: Programmgesteuertes Öffnen von Visio-Dokumenten](../vsto/how-to-programmatically-open-visio-documents.md)   
 [Gewusst wie: Programmgesteuertes Schließen von Visio-Dokumenten](../vsto/how-to-programmatically-close-visio-documents.md)   
 [Gewusst wie: Programmgesteuertes Speichern von Visio-Dokumenten](../vsto/how-to-programmatically-save-visio-documents.md)  
  
  