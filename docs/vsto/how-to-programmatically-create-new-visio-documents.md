---
title: "Gewusst wie: Programmgesteuertes Erstellen neuer Visio-Dokumente | Microsoft Docs"
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
  - "Visio [Office-Entwicklung in Visual Studio], Erstellen von Visio-Dokumenten"
  - "Dokumente [Office-Entwicklung in Visual Studio], Erstellen von Visio-Dokumenten"
ms.assetid: a0294d4c-be49-4cd0-b22e-3ec7568f3ec7
caps.latest.revision: 22
author: "kempb"
ms.author: "kempb"
manager: "ghogen"
caps.handback.revision: 21
---
# Gewusst wie: Programmgesteuertes Erstellen neuer Visio-Dokumente
  Wenn Sie ein neues Microsoft Office Visio\-Zeichnungsdokument erstellen, fügen Sie dieses Dokument der Microsoft.Office.Interop.Visio.Documents\-Auflistung geöffneter Visio\-Dokumente hinzu. Daher wird ein neues Visio\-Zeichnungsdokument mithilfe der Microsoft.Office.Interop.Visio.Documents.Add\-Methode erstellt. Weitere Informationen finden Sie in der VBA\-Referenzdokumentation für die [Microsoft.Office.Interop.Visio.Documents.Add](HV10069241)\-Methode.  
  
## Erstellen neuer leerer Dokumente  
  
#### So erstellen Sie ein neues Dokument  
  
-   Verwenden Sie die Microsoft.Office.Interop.Visio.Documents.Add\-Methode, um ein neues leeres Dokument zu erstellen, das nicht auf einer Vorlage basiert.  
  
     [!code-csharp[Trin_VstcoreVisioAutomationAddIn#1](../snippets/csharp/VS_Snippets_OfficeSP/Trin_VstcoreVisioAutomationAddIn/CS/ThisAddIn.cs#1)]
     [!code-vb[Trin_VstcoreVisioAutomationAddIn#1](../snippets/visualbasic/VS_Snippets_OfficeSP/Trin_VstcoreVisioAutomationAddIn/VB/ThisAddIn.vb#1)]  
  
## Erstellen von aus vorhandenen Dokumenten kopierten Dokumenten  
 Mit der Microsoft.Office.Interop.Visio.Documents.Add\-Methode können Sie ein neues Dokument erstellen, das eine Kopie eines vorhandenen Visio\-Dokuments ist. Sie müssen den Dateinamen und den vollqualifizierten Pfad des Diagramms angeben.  
  
#### So erstellen Sie ein neues Dokument, das aus einem vorhandenen Dokument kopiert wird  
  
-   Rufen Sie die Microsoft.Office.Interop.Visio.Documents.Add\-Methode auf, und geben Sie den Pfad zum Visio\-Diagramm an.  
  
     [!code-csharp[Trin_VstcoreVisioAutomationAddIn#2](../snippets/csharp/VS_Snippets_OfficeSP/Trin_VstcoreVisioAutomationAddIn/CS/ThisAddIn.cs#2)]
     [!code-vb[Trin_VstcoreVisioAutomationAddIn#2](../snippets/visualbasic/VS_Snippets_OfficeSP/Trin_VstcoreVisioAutomationAddIn/VB/ThisAddIn.vb#2)]  
  
## Erstellen von aus vorhandenen Schablonen kopierten Schablonen  
 Mit der [Microsoft.Office.Interop.Visio.Documents.Add](HV10069241)\-Methode können Sie eine neue Schablone erstellen, die eine Kopie einer vorhandenen Visio\-Schablone ist. Sie müssen den Dateinamen und den vollqualifizierten Pfad der Schablone angeben.  
  
#### So erstellen Sie eine neue Schablone, die aus einer vorhandenen Schablone kopiert wird  
  
-   Rufen Sie die Microsoft.Office.Interop.Visio.Documents.Add\-Methode auf, und geben Sie den Pfad der Schablone an.  
  
     [!code-csharp[Trin_VstcoreVisioAutomationAddIn#3](../snippets/csharp/VS_Snippets_OfficeSP/Trin_VstcoreVisioAutomationAddIn/CS/ThisAddIn.cs#3)]
     [!code-vb[Trin_VstcoreVisioAutomationAddIn#3](../snippets/visualbasic/VS_Snippets_OfficeSP/Trin_VstcoreVisioAutomationAddIn/VB/ThisAddIn.vb#3)]  
  
## Erstellen von Dokumenten auf Grundlage vorhandener Vorlagen  
 Mit der Microsoft.Office.Interop.Visio.Documents.Add\-Methode können Sie ein neues Dokument \(eine VSD\-Datei\) erstellen, die auf einer vorhandenen Visio\-Vorlage \(einer VST\-Datei\) basiert. Diese Methode kopiert die Schablonen, Formate und Einstellungen, die Bestandteile des Vorlagenarbeitsbereichs sind. Sie müssen den Dateinamen und den vollqualifizierten Pfad der Vorlage angeben.  
  
#### So erstellen Sie ein neues Dokument, das auf einer vorhandenen Vorlage basiert  
  
-   Rufen Sie die Microsoft.Office.Interop.Visio.Documents.Add\-Methode auf, und geben Sie den Pfad der Vorlage an.  
  
     [!code-csharp[Trin_VstcoreVisioAutomationAddIn#4](../snippets/csharp/VS_Snippets_OfficeSP/Trin_VstcoreVisioAutomationAddIn/CS/ThisAddIn.cs#4)]
     [!code-vb[Trin_VstcoreVisioAutomationAddIn#4](../snippets/visualbasic/VS_Snippets_OfficeSP/Trin_VstcoreVisioAutomationAddIn/VB/ThisAddIn.vb#4)]  
  
## Kompilieren des Codes  
 Für dieses Codebeispiel benötigen Sie Folgendes:  
  
-   Ein Visio\-Dokument namens `myDrawing.vsd` muss sich in einem Verzeichnis namens `Test` im Ordner „Eigene Dateien“ \(Windows XP und ältere Versionen\) bzw. im Ordner „Dokumente“ \(Windows Vista\) befinden.  
  
-   Ein Visio\-Dokument namens `myStencil.vss` muss sich in einem Verzeichnis namens `Test` im Ordner „Eigene Dateien“ \(Windows XP und ältere Versionen\) bzw. im Ordner „Dokumente“ \(Windows Vista\) befinden.  
  
-   Ein Visio\-Dokument namens `myTemplate.vst` muss sich in einem Verzeichnis namens `Test` im Ordner „Eigene Dateien“ \(Windows XP und ältere Versionen\) bzw. im Ordner „Dokumente“ \(Windows Vista\) befinden.  
  
## Siehe auch  
 [Visio-Projektmappen](../vsto/visio-solutions.md)   
 [Übersicht über das Visio-Objektmodell](../vsto/visio-object-model-overview.md)   
 [Gewusst wie: Programmgesteuertes Öffnen von Visio-Dokumenten](../vsto/how-to-programmatically-open-visio-documents.md)   
 [Gewusst wie: Programmgesteuertes Schließen von Visio-Dokumenten](../vsto/how-to-programmatically-close-visio-documents.md)   
 [Gewusst wie: Programmgesteuertes Speichern von Visio-Dokumenten](../vsto/how-to-programmatically-save-visio-documents.md)   
 [Gewusst wie: Programmgesteuertes Drucken von Visio-Dokumenten](../vsto/how-to-programmatically-print-visio-documents.md)  
  
  