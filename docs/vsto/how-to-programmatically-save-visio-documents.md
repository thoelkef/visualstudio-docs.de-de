---
title: "Gewusst wie: Programmgesteuertes Speichern von Visio-Dokumenten"
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
  - "Dokumente [Office-Entwicklung in Visual Studio], Speichern von Visio-Dokumenten"
  - "Visio [Office-Entwicklung in Visual Studio], Speichern von Visio-Dokumenten"
ms.assetid: 1a29ac7e-1da4-4c7a-87a5-d3d16897fe7c
caps.latest.revision: 20
author: "kempb"
ms.author: "kempb"
manager: "ghogen"
caps.handback.revision: 19
---
# Gewusst wie: Programmgesteuertes Speichern von Visio-Dokumenten
  Es gibt mehrere Methoden zum Speichern von Microsoft Office Visio\-Dokumenten:  
  
-   Speichern von Änderungen in einem vorhandenen Dokument  
  
-   Speichern eines neuen Dokuments oder Speichern eines Dokuments unter einem neuen Namen  
  
-   Speichern eines Dokuments mit angegebenen Argumenten  
  
 Weitere Informationen finden Sie in der VBA\-Referenzdokumentation für die Methoden [Microsoft.Office.Interop.Visio.Document.Save](HV10071468), [Microsoft.Office.Interop.Visio.Document.SaveAs](HV10071469) und [Microsoft.Office.Interop.Visio.Document.SaveAsEx](HV10071470).  
  
## Speichern eines vorhandenen Dokuments  
  
#### So speichern Sie einen Dokument  
  
-   Rufen Sie die Microsoft.Office.Interop.Visio.Document.Save\-Methode der Microsoft.Office.Tools.Visio.Document\-Klasse eines zuvor gespeicherten Dokuments auf.  
  
     Wenn Sie dieses Codebeispiel verwenden möchten, führen Sie es von der `ThisAddIn`\-Klasse im Projekt aus.  
  
    > [!NOTE]  
    >  Die Microsoft.Office.Interop.Visio.Document.Save\-Methode löst eine Ausnahme aus, falls ein neues Visio\-Dokument noch nicht gespeichert wurde.  
  
     [!code-csharp[Trin_VstcoreVisioAutomationAddIn#11](../snippets/csharp/VS_Snippets_OfficeSP/Trin_VstcoreVisioAutomationAddIn/CS/ThisAddIn.cs#11)]
     [!code-vb[Trin_VstcoreVisioAutomationAddIn#11](../snippets/visualbasic/VS_Snippets_OfficeSP/Trin_VstcoreVisioAutomationAddIn/VB/ThisAddIn.vb#11)]  
  
## Speichern eines Dokuments unter einem neuen Namen  
 Verwenden Sie die Microsoft.Office.Interop.Visio.Document.SaveAs\-Methode, um ein neues Dokument oder ein Dokument unter einem neuen Namen zu speichern. Diese Methode erfordert, dass Sie den neuen Dateinamen angeben.  
  
#### So speichern Sie das aktive Visio\-Dokument unter einem neuen Namen  
  
-   Rufen Sie die Microsoft.Office.Interop.Visio.Document.SaveAs\-Methode des zu speichernden Microsoft.Office.Tools.Visio.Document aus, indem Sie einen vollqualifizierten Pfad einschließlich eines Dateinamens verwenden. Wenn der Ordner bereits eine Datei dieses Namens enthält, wird die Datei automatisch überschrieben.  
  
     Wenn Sie dieses Codebeispiel verwenden möchten, führen Sie es von der `ThisAddIn`\-Klasse im Projekt aus.  
  
     [!code-csharp[Trin_VstcoreVisioAutomationAddIn#10](../snippets/csharp/VS_Snippets_OfficeSP/Trin_VstcoreVisioAutomationAddIn/CS/ThisAddIn.cs#10)]
     [!code-vb[Trin_VstcoreVisioAutomationAddIn#10](../snippets/visualbasic/VS_Snippets_OfficeSP/Trin_VstcoreVisioAutomationAddIn/VB/ThisAddIn.vb#10)]  
  
## Speichern eines Dokuments unter einem neuen Namen und mit angegebenen Argumenten  
 Verwenden Sie die Microsoft.Office.Interop.Visio.Document.SaveAsEx\-Methode, um ein Dokument unter einem neuen Namen zu speichern, und geben Sie ggf. auf das Dokument anwendbare Argumente an.  
  
#### So speichern Sie ein Dokument unter einem neuen Namen und mit angegebenen Argumenten  
  
-   Rufen Sie die Microsoft.Office.Interop.Visio.Document.SaveAsEx\-Methode des zu speichernden Microsoft.Office.Tools.Visio.Document aus, indem Sie einen vollqualifizierten Pfad einschließlich eines Dateinamens verwenden. Wenn der Ordner bereits eine Datei dieses Namens enthält, wird eine Ausnahme ausgelöst.  
  
     Im folgenden Codebeispiel wird das aktive Dokument unter einem neuen Namen gespeichert, das Dokument als schreibgeschützt markiert und in der Liste zuletzt verwendeter Dokumente angezeigt. Wenn Sie dieses Codebeispiel verwenden möchten, führen Sie es von der `ThisAddIn`\-Klasse im Projekt aus.  
  
     [!code-csharp[Trin_VstcoreVisioAutomationAddIn#12](../snippets/csharp/VS_Snippets_OfficeSP/Trin_VstcoreVisioAutomationAddIn/CS/ThisAddIn.cs#12)]
     [!code-vb[Trin_VstcoreVisioAutomationAddIn#12](../snippets/visualbasic/VS_Snippets_OfficeSP/Trin_VstcoreVisioAutomationAddIn/VB/ThisAddIn.vb#12)]  
  
## Kompilieren des Codes  
 Für dieses Codebeispiel benötigen Sie Folgendes:  
  
-   Wenn Sie ein Dokument unter einem neuen Namen speichern möchten, muss sich ein Verzeichnis namens `Test` im Ordner "Eigene Dateien" \(Windows XP und ältere Versionen\) bzw. im Ordner "Dokumente" \(Windows Vista\) befinden.  
  
## Siehe auch  
 [Visio-Projektmappen](../vsto/visio-solutions.md)   
 [Übersicht über das Visio-Objektmodell](../vsto/visio-object-model-overview.md)   
 [Gewusst wie: Programmgesteuertes Erstellen neuer Visio-Dokumente](../vsto/how-to-programmatically-create-new-visio-documents.md)   
 [Gewusst wie: Programmgesteuertes Öffnen von Visio-Dokumenten](../vsto/how-to-programmatically-open-visio-documents.md)   
 [Gewusst wie: Programmgesteuertes Schließen von Visio-Dokumenten](../vsto/how-to-programmatically-close-visio-documents.md)   
 [Gewusst wie: Programmgesteuertes Drucken von Visio-Dokumenten](../vsto/how-to-programmatically-print-visio-documents.md)  
  
  