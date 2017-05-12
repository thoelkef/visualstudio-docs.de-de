---
title: "Gewusst wie: Programmgesteuertes &#214;ffnen von Visio-Dokumenten"
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
  - "Dokumente [Office-Entwicklung in Visual Studio], Öffnen von Visio-Dokumenten"
  - "Visio [Office-Entwicklung in Visual Studio], Öffnen von Visio-Dokumenten"
ms.assetid: bddb820c-bde7-4d21-a0b3-6d1968baccab
caps.latest.revision: 20
author: "kempb"
ms.author: "kempb"
manager: "ghogen"
caps.handback.revision: 19
---
# Gewusst wie: Programmgesteuertes &#214;ffnen von Visio-Dokumenten
  Es gibt zwei Methoden zum Öffnen vorhandener Microsoft Office Visio\-Dokumente: Open und OpenEx. Die OpenEx\-Methode ist identisch mit der Open\-Methode, mit der Ausnahme, dass sie Argumente bereitstellt, in denen der Aufrufer angeben kann, wie das Dokument geöffnet wird.  
  
 Ausführliche Informationen zum Objektmodell finden Sie in der VBA\-Referenzdokumentation für die [Microsoft.Office.Interop.Visio.Documents.Open](HV10070351)\- und [Microsoft.Office.Interop.Visio.Documents.OpenEx](HV10071456)\-Methode.  
  
## Öffnen von Visio\-Dokumenten  
  
#### So öffnen Sie ein Visio\-Dokument  
  
-   Rufen Sie die Microsoft.Office.Interop.Visio.Documents.Open\-Methode auf, und übergeben Sie den vollqualifizierten Pfad des Visio\-Dokuments.  
  
     [!code-csharp[Trin_VstcoreVisioAutomationAddIn#5](../snippets/csharp/VS_Snippets_OfficeSP/Trin_VstcoreVisioAutomationAddIn/CS/ThisAddIn.cs#5)]
     [!code-vb[Trin_VstcoreVisioAutomationAddIn#5](../snippets/visualbasic/VS_Snippets_OfficeSP/Trin_VstcoreVisioAutomationAddIn/VB/ThisAddIn.vb#5)]  
  
## Öffnen eines Visio\-Dokuments mit angegebenen Argumenten  
  
#### So öffnen Sie ein Visio\-Dokument schreibgeschützt und angedockt  
  
-   Rufen Sie die Microsoft.Office.Interop.Visio.Documents.OpenEx\-Methode auf, geben Sie den vollqualifizierten Pfad des Visio\-Dokuments an, und schließen Sie die zu verwendenden Argumente ein, in diesem Fall „Gedockt“ und „Schreibgeschützt“.  
  
     [!code-csharp[Trin_VstcoreVisioAutomationAddIn#6](../snippets/csharp/VS_Snippets_OfficeSP/Trin_VstcoreVisioAutomationAddIn/CS/ThisAddIn.cs#6)]
     [!code-vb[Trin_VstcoreVisioAutomationAddIn#6](../snippets/visualbasic/VS_Snippets_OfficeSP/Trin_VstcoreVisioAutomationAddIn/VB/ThisAddIn.vb#6)]  
  
## Kompilieren des Codes  
 Für dieses Codebeispiel benötigen Sie Folgendes:  
  
-   Ein Visio\-Dokument namens `myDrawing.vsd` muss sich in einem Verzeichnis namens `Test` im Ordner „Eigene Dateien“ \(Windows XP und ältere Versionen\) bzw. im Ordner „Dokumente“ \(Windows Vista\) befinden.  
  
## Siehe auch  
 [Visio-Projektmappen](../vsto/visio-solutions.md)   
 [Übersicht über das Visio-Objektmodell](../vsto/visio-object-model-overview.md)   
 [Gewusst wie: Programmgesteuertes Erstellen neuer Visio-Dokumente](../vsto/how-to-programmatically-create-new-visio-documents.md)   
 [Gewusst wie: Programmgesteuertes Schließen von Visio-Dokumenten](../vsto/how-to-programmatically-close-visio-documents.md)   
 [Gewusst wie: Programmgesteuertes Speichern von Visio-Dokumenten](../vsto/how-to-programmatically-save-visio-documents.md)   
 [Gewusst wie: Programmgesteuertes Drucken von Visio-Dokumenten](../vsto/how-to-programmatically-print-visio-documents.md)  
  
  