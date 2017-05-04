---
title: "Gewusst wie: Programmgesteuertes Kopieren und Einf&#252;gen von Shapes in ein Visio-Dokument | Microsoft Docs"
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
  - "Shapes [Office-Entwicklung in Visual Studio], Kopieren und Einfügen von Visio-Shapes"
  - "Visio [Office-Entwicklung in Visual Studio], Kopieren und Einfügen von Visio-Shapes"
ms.assetid: 762d95cf-2d5c-4dea-988b-8f4da88fa1f1
caps.latest.revision: 15
author: "kempb"
ms.author: "kempb"
manager: "ghogen"
caps.handback.revision: 14
---
# Gewusst wie: Programmgesteuertes Kopieren und Einf&#252;gen von Shapes in ein Visio-Dokument
  Sie können programmgesteuert Shapes auf einer Seite eines Dokuments kopieren und in eine neue Seite im selben Dokument einfügen. Sie können die Shapes wahlweise an der Standardposition \(in der Mitte des aktiven Fensters\) oder an der gleichen Koordinatenpositionen wie auf der ursprünglichen Seite einfügen.  
  
## Kopieren und Einfügen von Shapes  
 Ausführliche Informationen zum Objektmodell finden Sie in der VBA\-Referenzdokumentation für die Methoden [Microsoft.Office.Interop.Visio.Shape.DrawRectangle](HV10070304), [Microsoft.Office.Interop.Visio.Shape.DrawOval](HV10070300), [Microsoft.Office.Interop.Visio.Shape.Copy](HV10070291) und [Microsoft.Office.Interop.Visio.Shape.Paste](HV10070437) sowie das Flag [Microsoft.Office.Interop.Visio.VisCutCopyPasteCodes.visCopyPasteNormal](HV10071835).  
  
#### So kopieren Sie Shapes in die Mitte einer anderen Seite  
  
-   Im folgenden Beispiel wird veranschaulicht, wie Sie die Shapes auf der ersten Seite kopieren und in der Mitte der zweiten Seite einfügen.  
  
     [!code-csharp[Trin_VstcoreVisioAutomationAddIn#14](../snippets/csharp/VS_Snippets_OfficeSP/Trin_VstcoreVisioAutomationAddIn/CS/ThisAddIn.cs#14)]
     [!code-vb[Trin_VstcoreVisioAutomationAddIn#14](../snippets/visualbasic/VS_Snippets_OfficeSP/Trin_VstcoreVisioAutomationAddIn/VB/ThisAddIn.vb#14)]  
  
## Kopieren und Einfügen von Shapes an der gleichen Position  
 Ausführliche Informationen zum Objektmodell finden Sie in der VBA\-Referenzdokumentation für die Methoden [Microsoft.Office.Interop.Visio.Shape.DrawRectangle](HV10070304), [Microsoft.Office.Interop.Visio.Shape.DrawOval](HV10070300), [Microsoft.Office.Interop.Visio.Shape.Copy](HV10070291) und [Microsoft.Office.Interop.Visio.Shape.Paste](HV10070437) sowie das Flag [Microsoft.Office.Interop.Visio.VisCutCopyPasteCodes.visCopyPasteNoTranslate](HV10071835).  
  
 Wenn Sie das Format der eingefügten Informationen steuern und \(optional\) eine Verknüpfung zur Quelldatei \(z. B. zu einem Microsoft Office Word\-Dokument\) herstellen müssen, verwenden Sie die Methode PasteSpecial.  
  
#### So kopieren Sie Shapes und ihre Positionen auf eine andere Seite  
  
-   Im folgenden Beispiel wird veranschaulicht, wie Sie die Shapes auf der ersten Seite kopieren und auf der zweiten Seite an ihren ursprünglichen Koordinatenpositionen einfügen.  
  
     [!code-csharp[Trin_VstcoreVisioAutomationAddIn#15](../snippets/csharp/VS_Snippets_OfficeSP/Trin_VstcoreVisioAutomationAddIn/CS/ThisAddIn.cs#15)]
     [!code-vb[Trin_VstcoreVisioAutomationAddIn#15](../snippets/visualbasic/VS_Snippets_OfficeSP/Trin_VstcoreVisioAutomationAddIn/VB/ThisAddIn.vb#15)]  
  
## Siehe auch  
 [Visio-Projektmappen](../vsto/visio-solutions.md)   
 [Übersicht über das Visio-Objektmodell](../vsto/visio-object-model-overview.md)   
 [Arbeiten mit Visio-Shapes](../vsto/working-with-visio-shapes.md)   
 [Gewusst wie: Programmgesteuertes Hinzufügen von Shapes zu Visio-Dokumenten](../vsto/how-to-programmatically-add-shapes-to-a-visio-document.md)  
  
  