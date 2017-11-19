---
title: 'Vorgehensweise: Programmgesteuertes Speichern von Visio-Dokumenten | Microsoft Docs'
ms.custom: 
ms.date: 02/02/2017
ms.reviewer: 
ms.suite: 
ms.technology: office-development
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- documents [Office development in Visual Studio], saving Visio documents
- Visio [Office development in Visual Studio], saving Visio documents
ms.assetid: 1a29ac7e-1da4-4c7a-87a5-d3d16897fe7c
caps.latest.revision: "20"
author: gewarren
ms.author: gewarren
manager: ghogen
ms.openlocfilehash: a100a573f26a774c58083cb82b07c50792908f45
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 10/31/2017
---
# <a name="how-to-programmatically-save-visio-documents"></a>Gewusst wie: Programmgesteuertes Speichern von Visio-Dokumenten
  Es gibt mehrere Methoden zum Speichern von Microsoft Office Visio-Dokumenten:  
  
-   Speichern von Änderungen in einem vorhandenen Dokument  
  
-   Speichern eines neuen Dokuments oder Speichern eines Dokuments unter einem neuen Namen  
  
-   Speichern eines Dokuments mit angegebenen Argumenten  
  
 Weitere Informationen finden Sie in der VBA-Referenzdokumentation für die Methoden [Microsoft.Office.Interop.Visio.Document.Save](https://msdn.microsoft.com/library/office/ff766478.aspx) , [Microsoft.Office.Interop.Visio.Document.SaveAs](https://msdn.microsoft.com/library/office/ff765824.aspx) und [Microsoft.Office.Interop.Visio.Document.SaveAsEx](https://msdn.microsoft.com/library/office/ff768149.aspx) .  
  
## <a name="saving-an-existing-document"></a>Speichern eines vorhandenen Dokuments  
  
#### <a name="to-save-a-document"></a>So speichern Sie einen Dokument  
  
-   Rufen Sie die Microsoft.Office.Interop.Visio.Document.Save-Methode der Klasse Microsoft.Office.Tools.Visio.Document eines Dokuments, das zuvor gespeichert wurde.  
  
     Wenn Sie dieses Codebeispiel verwenden möchten, führen Sie es von der `ThisAddIn` -Klasse im Projekt aus.  
  
    > [!NOTE]  
    >  Die Microsoft.Office.Interop.Visio.Document.Save Methode löst eine Ausnahme aus, wenn ein neues Visio-Dokument noch nicht gespeichert wurde.  
  
     [!code-csharp[Trin_VstcoreVisioAutomationAddIn#11](../vsto/codesnippet/CSharp/trin_vstcorevisioautomationaddin/ThisAddIn.cs#11)]
     [!code-vb[Trin_VstcoreVisioAutomationAddIn#11](../vsto/codesnippet/VisualBasic/trin_vstcorevisioautomationaddin/ThisAddIn.vb#11)]  
  
## <a name="saving-a-document-with-a-new-name"></a>Speichern eines Dokuments unter einem neuen Namen  
 Verwenden Sie die Microsoft.Office.Interop.Visio.Document.SaveAs-Methode, um ein neues Dokument oder ein Dokument, das einem neuen Namen zu speichern. Diese Methode erfordert, dass Sie den neuen Dateinamen angeben.  
  
#### <a name="to-save-the-active-visio-document-with-a-new-name"></a>So speichern Sie das aktive Visio-Dokument unter einem neuen Namen  
  
-   Rufen Sie die Microsoft.Office.Interop.Visio.Document.SaveAs-Methode, der die Microsoft.Office.Tools.Visio.Document, die Sie speichern, indem Sie einen vollqualifizierten Pfad einschließlich eines Dateinamens möchten. Wenn der Ordner bereits eine Datei dieses Namens enthält, wird die Datei automatisch überschrieben.  
  
     Wenn Sie dieses Codebeispiel verwenden möchten, führen Sie es von der `ThisAddIn` -Klasse im Projekt aus.  
  
     [!code-csharp[Trin_VstcoreVisioAutomationAddIn#10](../vsto/codesnippet/CSharp/trin_vstcorevisioautomationaddin/ThisAddIn.cs#10)]
     [!code-vb[Trin_VstcoreVisioAutomationAddIn#10](../vsto/codesnippet/VisualBasic/trin_vstcorevisioautomationaddin/ThisAddIn.vb#10)]  
  
## <a name="saving-a-document-with-a-new-name-and-specified-arguments"></a>Speichern eines Dokuments unter einem neuen Namen und mit angegebenen Argumenten  
 Verwenden der Microsoft.Office.Interop.Visio.Document.SaveAsEx-Methode, um ein Dokument unter einem neuen Namen speichern, und geben Sie ggf. anwendbare Argumente an, auf das Dokument angewendet.  
  
#### <a name="to-save-document-with-a-new-name-and-specified-arguments"></a>So speichern Sie ein Dokument unter einem neuen Namen und mit angegebenen Argumenten  
  
-   Rufen Sie die Microsoft.Office.Interop.Visio.Document.SaveAsEx-Methode, der die Microsoft.Office.Tools.Visio.Document, die Sie speichern, indem Sie einen vollqualifizierten Pfad einschließlich eines Dateinamens möchten. Wenn der Ordner bereits eine Datei dieses Namens enthält, wird eine Ausnahme ausgelöst.  
  
     Im folgenden Codebeispiel wird das aktive Dokument unter einem neuen Namen gespeichert, das Dokument als schreibgeschützt markiert und in der Liste zuletzt verwendeter Dokumente angezeigt. Wenn Sie dieses Codebeispiel verwenden möchten, führen Sie es von der `ThisAddIn` -Klasse im Projekt aus.  
  
     [!code-csharp[Trin_VstcoreVisioAutomationAddIn#12](../vsto/codesnippet/CSharp/trin_vstcorevisioautomationaddin/ThisAddIn.cs#12)]
     [!code-vb[Trin_VstcoreVisioAutomationAddIn#12](../vsto/codesnippet/VisualBasic/trin_vstcorevisioautomationaddin/ThisAddIn.vb#12)]  
  
## <a name="compiling-the-code"></a>Kompilieren des Codes  
 Für dieses Codebeispiel benötigen Sie Folgendes:  
  
-   Wenn Sie ein Dokument unter einem neuen Namen speichern möchten, muss sich ein Verzeichnis namens `Test` im Ordner "Eigene Dateien" (Windows XP und ältere Versionen) bzw. im Ordner "Dokumente" (Windows Vista) befinden.  
  
## <a name="see-also"></a>Siehe auch  
 [Visio-Projektmappen](../vsto/visio-solutions.md)   
 [Visio-Objektmodellübersicht](../vsto/visio-object-model-overview.md)   
 [Vorgehensweise: Programmgesteuertes Erstellen neuer Visio-Dokumente](../vsto/how-to-programmatically-create-new-visio-documents.md)   
 [Vorgehensweise: Programmgesteuertes Öffnen von Visio-Dokumenten](../vsto/how-to-programmatically-open-visio-documents.md)   
 [Vorgehensweise: Programmgesteuertes Schließen von Visio-Dokumenten](../vsto/how-to-programmatically-close-visio-documents.md)   
 [Vorgehensweise: Programmgesteuertes Drucken von Visio-Dokumenten](../vsto/how-to-programmatically-print-visio-documents.md)  
  
  