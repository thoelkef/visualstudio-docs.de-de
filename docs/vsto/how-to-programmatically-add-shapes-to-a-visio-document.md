---
title: "Gewusst wie: Programmgesteuertes Hinzuf&#252;gen von Shapes zu Visio-Dokumenten | Microsoft Docs"
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
  - "Visio [Office-Entwicklung in Visual Studio], Hinzufügen von Visio-Shapes"
  - "Shapes [Office-Entwicklung in Visual Studio], Hinzufügen von Visio-Shapes"
ms.assetid: 29613237-88f5-41a7-9e13-cfa177f41221
caps.latest.revision: 17
author: "kempb"
ms.author: "kempb"
manager: "ghogen"
caps.handback.revision: 17
---
# Gewusst wie: Programmgesteuertes Hinzuf&#252;gen von Shapes zu Visio-Dokumenten
  Sie können einem Microsoft Office Visio\-Dokument Shapes hinzufügen, indem Sie die Master\-Shapes aus einer Schablone abrufen und auf der aktiven Seite ablegen.  
  
 Weitere Informationen finden Sie in der VBA\-Referenzdokumentation für die [Microsoft.Office.Interop.Visio.Documents.Add](HV10069241)\-Methode, [Microsoft.Office.Interop.Visio.Application.ActivePage](HV10069528)\-Eigenschaft und [Microsoft.Office.Interop.Visio.Page.Drop](HV10070273)\-Methode.  
  
## Hinzufügen von Shapes zu einem Visio\-Dokument  
  
#### So fügen Sie einem Visio\-Dokument Shapes hinzu  
  
-   Rufen Sie bei einem aktiven Dokument die Master\-Shapes aus der Documents.Masters\-Auflistung ab, und legen Sie sie im aktiven Dokument ab. Sie können einen Master mit dem Index oder Masternamen abrufen.  
  
     Im folgenden Codebeispiel wird ein leeres Visio\-Dokument erstellt und anschließend geöffnet, während die Schablone **Standard\-Shapes** angedockt ist. Anschließend werden vom Code verschiedene Shapes abgerufen und auf der aktiven Seite abgelegt.  
  
     [!code-csharp[Trin_VstcoreVisioAutomationAddIn#13](../snippets/csharp/VS_Snippets_OfficeSP/Trin_VstcoreVisioAutomationAddIn/CS/ThisAddIn.cs#13)]
     [!code-vb[Trin_VstcoreVisioAutomationAddIn#13](../snippets/visualbasic/VS_Snippets_OfficeSP/Trin_VstcoreVisioAutomationAddIn/VB/ThisAddIn.vb#13)]  
  
## Siehe auch  
 [Visio-Projektmappen](../vsto/visio-solutions.md)   
 [Übersicht über das Visio-Objektmodell](../vsto/visio-object-model-overview.md)   
 [Arbeiten mit Visio-Shapes](../vsto/working-with-visio-shapes.md)   
 [Gewusst wie: Programmgesteuertes Kopieren und Einfügen von Shapes in ein Visio-Dokument](../vsto/how-to-programmatically-copy-and-paste-shapes-in-a-visio-document.md)  
  
  