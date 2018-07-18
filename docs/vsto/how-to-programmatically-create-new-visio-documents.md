---
title: 'Gewusst wie: Programmgesteuertes Erstellen neuer Visio-Dokumente'
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
ms.openlocfilehash: 9b5b66690d3856a2bf1fc6df417b60ab5e293127
ms.sourcegitcommit: 34f7d23ce3bd140dcae875b602d5719bb4363ed1
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 06/11/2018
ms.locfileid: "35256743"
---
# <a name="how-to-programmatically-create-new-visio-documents"></a>Gewusst wie: Programmgesteuertes Erstellen neuer Visio-Dokumente
  Wenn Sie eine neue Microsoft Office Visio-Zeichnung Dokument erstellen, Sie hinzufügen, damit die `Microsoft.Office.Interop.Visio.Documents` -Auflistung geöffneter Visio-Dokumente. Daher die `Microsoft.Office.Interop.Visio.Documents.Add` Methode erstellt ein neues Visio-Zeichnungsdokument. Weitere Informationen finden Sie in der VBA-Referenzdokumentation für die [Microsoft.Office.Interop.Visio.Documents.Add](http://msdn.microsoft.com/library/office/ff766868.aspx) -Methode.  
  
## <a name="create-new-blank-documents"></a>Erstellen neuer leerer Dokumente  
  
### <a name="to-create-a-new-document"></a>So erstellen Sie ein neues Dokument  
  
-   Verwenden der `Microsoft.Office.Interop.Visio.Documents.Add` Methode, um ein neues leeres Dokument zu erstellen, die nicht in einer Vorlage basiert.  
  
     [!code-csharp[Trin_VstcoreVisioAutomationAddIn#1](../vsto/codesnippet/CSharp/trin_vstcorevisioautomationaddin/ThisAddIn.cs#1)]
     [!code-vb[Trin_VstcoreVisioAutomationAddIn#1](../vsto/codesnippet/VisualBasic/trin_vstcorevisioautomationaddin/ThisAddIn.vb#1)]  
  
## <a name="create-documents-copied-from-existing-documents"></a>Erstellen von aus vorhandenen Dokumenten kopierten Dokumenten  
 Die `Microsoft.Office.Interop.Visio.Documents.Add` -Methode können Sie ein neues Dokument, das eine Kopie des vorhandenen Visio-Dokuments erstellen. Sie müssen den Dateinamen und den vollqualifizierten Pfad des Diagramms angeben.  
  
### <a name="to-create-a-new-document-that-is-copied-from-an-existing-document"></a>So erstellen Sie ein neues Dokument, das aus einem vorhandenen Dokument kopiert wird  
  
-   Rufen Sie die `Microsoft.Office.Interop.Visio.Documents.Add` Methode, und geben Sie den Pfad des Visio-Diagramm.  
  
     [!code-csharp[Trin_VstcoreVisioAutomationAddIn#2](../vsto/codesnippet/CSharp/trin_vstcorevisioautomationaddin/ThisAddIn.cs#2)]
     [!code-vb[Trin_VstcoreVisioAutomationAddIn#2](../vsto/codesnippet/VisualBasic/trin_vstcorevisioautomationaddin/ThisAddIn.vb#2)]  
  
## <a name="create-stencils-copied-from-existing-stencils"></a>Erstellen Sie aus vorhandenen Schablonen kopierte Schablonen  
 Mit der [Microsoft.Office.Interop.Visio.Documents.Add](http://msdn.microsoft.com/library/office/ff766868.aspx) -Methode können Sie eine neue Schablone erstellen, die eine Kopie einer vorhandenen Visio-Schablone ist. Sie müssen den Dateinamen und den vollqualifizierten Pfad der Schablone angeben.  
  
### <a name="to-create-a-new-stencil-that-is-copied-from-an-existing-stencil"></a>So erstellen Sie eine neue Schablone, die aus einer vorhandenen Schablone kopiert wird  
  
-   Rufen Sie die `Microsoft.Office.Interop.Visio.Documents.Add` Methode und den Pfad der Schablone angeben.  
  
     [!code-csharp[Trin_VstcoreVisioAutomationAddIn#3](../vsto/codesnippet/CSharp/trin_vstcorevisioautomationaddin/ThisAddIn.cs#3)]
     [!code-vb[Trin_VstcoreVisioAutomationAddIn#3](../vsto/codesnippet/VisualBasic/trin_vstcorevisioautomationaddin/ThisAddIn.vb#3)]  
  
## <a name="create-documents-based-on-existing-templates"></a>Erstellen von Dokumenten auf Grundlage vorhandener Vorlagen  
 Die `Microsoft.Office.Interop.Visio.Documents.Add` -Methode können Sie ein neues Dokument erstellen (eine *.vsd* Datei), basiert auf einer vorhandenen Visio-Vorlage (einer *VST* Datei). Diese Methode kopiert die Schablonen, Formate und Einstellungen, die Bestandteile des Vorlagenarbeitsbereichs sind. Sie müssen den Dateinamen und den vollqualifizierten Pfad der Vorlage angeben.  
  
### <a name="to-create-a-new-document-that-is-based-on-an-existing-template"></a>So erstellen Sie ein neues Dokument, das auf einer vorhandenen Vorlage basiert  
  
-   Rufen Sie die `Microsoft.Office.Interop.Visio.Documents.Add` Methode und den Pfad der Vorlage angeben.  
  
     [!code-csharp[Trin_VstcoreVisioAutomationAddIn#4](../vsto/codesnippet/CSharp/trin_vstcorevisioautomationaddin/ThisAddIn.cs#4)]
     [!code-vb[Trin_VstcoreVisioAutomationAddIn#4](../vsto/codesnippet/VisualBasic/trin_vstcorevisioautomationaddin/ThisAddIn.vb#4)]  
  
## <a name="compile-the-code"></a>Kompilieren des Codes  
 Für dieses Codebeispiel benötigen Sie Folgendes:  
  
-   Ein Visio-Dokument mit dem Namen `myDrawing.vsd` Wohnsitz in einem Verzeichnis namens `Test` in die *eigene* Ordner (für Windows XP und früher) oder die *Dokumente* Ordner (für Windows Vista).  
  
-   Ein Visio-Dokument mit dem Namen `myStencil.vss` Wohnsitz in einem Verzeichnis namens `Test` in die *eigene* Ordner (für Windows XP und früher) oder die *Dokumente* Ordner (für Windows Vista).  
  
-   Ein Visio-Dokument mit dem Namen `myTemplate.vst` Wohnsitz in einem Verzeichnis namens `Test` in die *eigene* Ordner (für Windows XP und früher) oder die *Dokumente* Ordner (für Windows Vista).  
  
## <a name="see-also"></a>Siehe auch  
 [Visio-Projektmappen](../vsto/visio-solutions.md)   
 [Übersicht über das Visio-Objektmodell](../vsto/visio-object-model-overview.md)   
 [Gewusst wie: Programmgesteuertes Öffnen von Visio-Dokumenten](../vsto/how-to-programmatically-open-visio-documents.md)   
 [Gewusst wie: Programmgesteuertes Schließen von Visio-Dokumenten](../vsto/how-to-programmatically-close-visio-documents.md)   
 [Gewusst wie: Programmgesteuertes Speichern von Visio-Dokumenten](../vsto/how-to-programmatically-save-visio-documents.md)   
 [Gewusst wie: Programmgesteuertes Drucken von Visio-Dokumenten](../vsto/how-to-programmatically-print-visio-documents.md)  
  
  