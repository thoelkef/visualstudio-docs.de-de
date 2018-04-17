---
title: 'Vorgehensweise: Programmgesteuertes Erstellen neuer Visio-Dokumente | Microsoft Docs'
ms.custom: ''
ms.date: 02/02/2017
ms.technology:
- office-development
ms.topic: conceptual
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- Visio [Office development in Visual Studio], creating Visio documents
- documents [Office development in Visual Studio], creating Visio documents
author: TerryGLee
ms.author: tglee
manager: douge
ms.workload:
- office
ms.openlocfilehash: e2dd64b2996df4ed75cd45cd741619658f9b3654
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/16/2018
---
# <a name="how-to-programmatically-create-new-visio-documents"></a>Gewusst wie: Programmgesteuertes Erstellen neuer Visio-Dokumente
  Wenn Sie eine neue Microsoft Office Visio-Zeichnungsdatei Dokument erstellen, fügen Sie sie der Microsoft.Office.Interop.Visio.Documents-Auflistung geöffneter Visio-Dokumente hinzu. Daher wird die Microsoft.Office.Interop.Visio.Documents.Add-Methode ein neues Visio-Zeichnungsdokument erstellt. Weitere Informationen finden Sie in der VBA-Referenzdokumentation für die [Microsoft.Office.Interop.Visio.Documents.Add](http://msdn.microsoft.com/library/office/ff766868.aspx) -Methode.  
  
## <a name="creating-new-blank-documents"></a>Erstellen neuer leerer Dokumente  
  
#### <a name="to-create-a-new-document"></a>So erstellen Sie ein neues Dokument  
  
-   Verwenden Sie die Microsoft.Office.Interop.Visio.Documents.Add-Methode, um ein neues leeres Dokument zu erstellen, das nicht in einer Vorlage basiert.  
  
     [!code-csharp[Trin_VstcoreVisioAutomationAddIn#1](../vsto/codesnippet/CSharp/trin_vstcorevisioautomationaddin/ThisAddIn.cs#1)]
     [!code-vb[Trin_VstcoreVisioAutomationAddIn#1](../vsto/codesnippet/VisualBasic/trin_vstcorevisioautomationaddin/ThisAddIn.vb#1)]  
  
## <a name="creating-documents-copied-from-existing-documents"></a>Erstellen von aus vorhandenen Dokumenten kopierten Dokumenten  
 Die Microsoft.Office.Interop.Visio.Documents.Add-Methode kann ein neues Dokument erstellen, das eine Kopie einer vorhandenen Visio-Dokument ist. Sie müssen den Dateinamen und den vollqualifizierten Pfad des Diagramms angeben.  
  
#### <a name="to-create-a-new-document-that-is-copied-from-an-existing-document"></a>So erstellen Sie ein neues Dokument, das aus einem vorhandenen Dokument kopiert wird  
  
-   Rufen Sie die Microsoft.Office.Interop.Visio.Documents.Add-Methode, und geben Sie den Pfad des Visio-Diagramms.  
  
     [!code-csharp[Trin_VstcoreVisioAutomationAddIn#2](../vsto/codesnippet/CSharp/trin_vstcorevisioautomationaddin/ThisAddIn.cs#2)]
     [!code-vb[Trin_VstcoreVisioAutomationAddIn#2](../vsto/codesnippet/VisualBasic/trin_vstcorevisioautomationaddin/ThisAddIn.vb#2)]  
  
## <a name="creating-stencils-copied-from-existing-stencils"></a>Erstellen von aus vorhandenen Schablonen kopierten Schablonen  
 Mit der [Microsoft.Office.Interop.Visio.Documents.Add](http://msdn.microsoft.com/library/office/ff766868.aspx) -Methode können Sie eine neue Schablone erstellen, die eine Kopie einer vorhandenen Visio-Schablone ist. Sie müssen den Dateinamen und den vollqualifizierten Pfad der Schablone angeben.  
  
#### <a name="to-create-a-new-stencil-that-is-copied-from-an-existing-stencil"></a>So erstellen Sie eine neue Schablone, die aus einer vorhandenen Schablone kopiert wird  
  
-   Rufen Sie die Microsoft.Office.Interop.Visio.Documents.Add-Methode, und geben Sie den Pfad der Schablone.  
  
     [!code-csharp[Trin_VstcoreVisioAutomationAddIn#3](../vsto/codesnippet/CSharp/trin_vstcorevisioautomationaddin/ThisAddIn.cs#3)]
     [!code-vb[Trin_VstcoreVisioAutomationAddIn#3](../vsto/codesnippet/VisualBasic/trin_vstcorevisioautomationaddin/ThisAddIn.vb#3)]  
  
## <a name="creating-documents-based-on-existing-templates"></a>Erstellen von Dokumenten auf Grundlage vorhandener Vorlagen  
 Die Methode Microsoft.Office.Interop.Visio.Documents.Add kann ein neues Dokument (eine VSD-Datei) erstellen, das auf einer vorhandenen Visio-Vorlage (einer VST-Datei) basiert. Diese Methode kopiert die Schablonen, Formate und Einstellungen, die Bestandteile des Vorlagenarbeitsbereichs sind. Sie müssen den Dateinamen und den vollqualifizierten Pfad der Vorlage angeben.  
  
#### <a name="to-create-a-new-document-that-is-based-on-an-existing-template"></a>So erstellen Sie ein neues Dokument, das auf einer vorhandenen Vorlage basiert  
  
-   Rufen Sie die Microsoft.Office.Interop.Visio.Documents.Add-Methode, und geben Sie den Pfad der Vorlage.  
  
     [!code-csharp[Trin_VstcoreVisioAutomationAddIn#4](../vsto/codesnippet/CSharp/trin_vstcorevisioautomationaddin/ThisAddIn.cs#4)]
     [!code-vb[Trin_VstcoreVisioAutomationAddIn#4](../vsto/codesnippet/VisualBasic/trin_vstcorevisioautomationaddin/ThisAddIn.vb#4)]  
  
## <a name="compiling-the-code"></a>Kompilieren des Codes  
 Für dieses Codebeispiel benötigen Sie Folgendes:  
  
-   Ein Visio-Dokument namens `myDrawing.vsd` muss sich in einem Verzeichnis namens `Test` im Ordner „Eigene Dateien“ (Windows XP und ältere Versionen) bzw. im Ordner „Dokumente“ (Windows Vista) befinden.  
  
-   Ein Visio-Dokument namens `myStencil.vss` muss sich in einem Verzeichnis namens `Test` im Ordner „Eigene Dateien“ (Windows XP und ältere Versionen) bzw. im Ordner „Dokumente“ (Windows Vista) befinden.  
  
-   Ein Visio-Dokument namens `myTemplate.vst` muss sich in einem Verzeichnis namens `Test` im Ordner „Eigene Dateien“ (Windows XP und ältere Versionen) bzw. im Ordner „Dokumente“ (Windows Vista) befinden.  
  
## <a name="see-also"></a>Siehe auch  
 [Visio-Projektmappen](../vsto/visio-solutions.md)   
 [Visio-Objektmodellübersicht](../vsto/visio-object-model-overview.md)   
 [Vorgehensweise: Programmgesteuertes Öffnen von Visio-Dokumenten](../vsto/how-to-programmatically-open-visio-documents.md)   
 [Vorgehensweise: Programmgesteuertes Schließen von Visio-Dokumenten](../vsto/how-to-programmatically-close-visio-documents.md)   
 [Vorgehensweise: Programmgesteuertes Speichern von Visio-Dokumenten](../vsto/how-to-programmatically-save-visio-documents.md)   
 [Vorgehensweise: Programmgesteuertes Drucken von Visio-Dokumenten](../vsto/how-to-programmatically-print-visio-documents.md)  
  
  