---
title: 'Gewusst wie: Programmgesteuertes Speichern von Visio-Dokumenten'
ms.custom: ''
ms.date: 02/02/2017
ms.technology:
- office-development
ms.topic: conceptual
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- documents [Office development in Visual Studio], saving Visio documents
- Visio [Office development in Visual Studio], saving Visio documents
author: TerryGLee
ms.author: tglee
manager: douge
ms.workload:
- office
ms.openlocfilehash: 4171f0237b7735748da567bd9482856c013759bc
ms.sourcegitcommit: 6944ceb7193d410a2a913ecee6f40c6e87e8a54b
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 09/06/2018
ms.locfileid: "35673193"
---
# <a name="how-to-programmatically-save-visio-documents"></a>Gewusst wie: Programmgesteuertes Speichern von Visio-Dokumenten
  Es gibt mehrere Methoden zum Speichern von Microsoft Office Visio-Dokumenten:  
  
-   Speichern von Änderungen in einem vorhandenen Dokument  
  
-   Speichern eines neuen Dokuments oder Speichern eines Dokuments unter einem neuen Namen  
  
-   Speichern eines Dokuments mit angegebenen Argumenten  
  
 Weitere Informationen finden Sie in der VBA-Referenzdokumentation für die Methoden [Microsoft.Office.Interop.Visio.Document.Save](https://msdn.microsoft.com/library/office/ff766478.aspx) , [Microsoft.Office.Interop.Visio.Document.SaveAs](https://msdn.microsoft.com/library/office/ff765824.aspx) und [Microsoft.Office.Interop.Visio.Document.SaveAsEx](https://msdn.microsoft.com/library/office/ff768149.aspx) .  
  
## <a name="save-an-existing-document"></a>Speichern Sie ein vorhandenes Dokument  
  
### <a name="to-save-a-document"></a>So speichern Sie einen Dokument  
  
-   Rufen Sie die `Microsoft.Office.Interop.Visio.Document.Save` Methode der `Microsoft.Office.Tools.Visio.Document` Klasse eines Dokuments, das zuvor gespeichert wurde.  
  
     Wenn Sie dieses Codebeispiel verwenden möchten, führen Sie es von der `ThisAddIn` -Klasse im Projekt aus.  
  
    > [!NOTE]  
    >  Die `Microsoft.Office.Interop.Visio.Document.Save` Methode löst eine Ausnahme aus, wenn ein neues Visio-Dokument noch nicht gespeichert wurde.  
  
     [!code-csharp[Trin_VstcoreVisioAutomationAddIn#11](../vsto/codesnippet/CSharp/trin_vstcorevisioautomationaddin/ThisAddIn.cs#11)]
     [!code-vb[Trin_VstcoreVisioAutomationAddIn#11](../vsto/codesnippet/VisualBasic/trin_vstcorevisioautomationaddin/ThisAddIn.vb#11)]  
  
## <a name="save-a-document-with-a-new-name"></a>Speichern Sie ein Dokument mit einem neuen Namen.  
 Verwenden der `Microsoft.Office.Interop.Visio.Document.SaveAs` Methode, um ein neues Dokument oder ein Dokument, das einem neuen Namen zu speichern. Diese Methode erfordert, dass Sie den neuen Dateinamen angeben.  
  
### <a name="to-save-the-active-visio-document-with-a-new-name"></a>So speichern Sie das aktive Visio-Dokument unter einem neuen Namen  
  
-   Rufen Sie die `Microsoft.Office.Interop.Visio.Document.SaveAs` Methode der `Microsoft.Office.Tools.Visio.Document` speichern, indem Sie einen vollqualifizierten Pfad einschließlich eines Dateinamens, möchten. Wenn der Ordner bereits eine Datei dieses Namens enthält, wird die Datei automatisch überschrieben.  
  
     Wenn Sie dieses Codebeispiel verwenden möchten, führen Sie es von der `ThisAddIn` -Klasse im Projekt aus.  
  
     [!code-csharp[Trin_VstcoreVisioAutomationAddIn#10](../vsto/codesnippet/CSharp/trin_vstcorevisioautomationaddin/ThisAddIn.cs#10)]
     [!code-vb[Trin_VstcoreVisioAutomationAddIn#10](../vsto/codesnippet/VisualBasic/trin_vstcorevisioautomationaddin/ThisAddIn.vb#10)]  
  
## <a name="save-a-document-with-a-new-name-and-specified-arguments"></a>Speichern eines Dokuments unter einem neuen Namen und den angegebenen Argumenten  
 Verwenden der `Microsoft.Office.Interop.Visio.Document.SaveAsEx` Methode, um ein Dokument mit einem neuen Namen speichern, und geben Argumente für das Dokument angewendet.  
  
### <a name="to-save-document-with-a-new-name-and-specified-arguments"></a>So speichern Sie ein Dokument unter einem neuen Namen und mit angegebenen Argumenten  
  
-   Rufen Sie die `Microsoft.Office.Interop.Visio.Document.SaveAsEx` Methode der `Microsoft.Office.Tools.Visio.Document` speichern, indem Sie einen vollqualifizierten Pfad einschließlich eines Dateinamens, möchten. Wenn der Ordner bereits eine Datei dieses Namens enthält, wird eine Ausnahme ausgelöst.  
  
     Im folgenden Codebeispiel wird das aktive Dokument unter einem neuen Namen gespeichert, das Dokument als schreibgeschützt markiert und in der Liste zuletzt verwendeter Dokumente angezeigt. Wenn Sie dieses Codebeispiel verwenden möchten, führen Sie es von der `ThisAddIn` -Klasse im Projekt aus.  
  
     [!code-csharp[Trin_VstcoreVisioAutomationAddIn#12](../vsto/codesnippet/CSharp/trin_vstcorevisioautomationaddin/ThisAddIn.cs#12)]
     [!code-vb[Trin_VstcoreVisioAutomationAddIn#12](../vsto/codesnippet/VisualBasic/trin_vstcorevisioautomationaddin/ThisAddIn.vb#12)]  
  
## <a name="compile-the-code"></a>Kompilieren des Codes  
 Für dieses Codebeispiel benötigen Sie Folgendes:  
  
-   Zum Speichern eines Dokuments, das einen neuen Namen verfügt, ein Verzeichnis namens `Test` Wohnsitz in die *eigene* Ordner (für Windows XP und früher) oder die *Dokumente* Ordner (für Windows Vista).  
  
## <a name="see-also"></a>Siehe auch  
 [Visio-Projektmappen](../vsto/visio-solutions.md)   
 [Übersicht über das Visio-Objektmodell](../vsto/visio-object-model-overview.md)   
 [Gewusst wie: Programmgesteuertes Erstellen neuer Visio-Dokumente](../vsto/how-to-programmatically-create-new-visio-documents.md)   
 [Gewusst wie: Programmgesteuertes Öffnen von Visio-Dokumenten](../vsto/how-to-programmatically-open-visio-documents.md)   
 [Gewusst wie: Programmgesteuertes Schließen von Visio-Dokumenten](../vsto/how-to-programmatically-close-visio-documents.md)   
 [Gewusst wie: Programmgesteuertes Drucken von Visio-Dokumenten](../vsto/how-to-programmatically-print-visio-documents.md)  
  
  