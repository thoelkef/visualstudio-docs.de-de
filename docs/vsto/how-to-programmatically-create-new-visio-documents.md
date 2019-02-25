---
title: 'Vorgehensweise: Programmgesteuertes Erstellen Sie Neuer Visio-Dokumente'
ms.date: 02/02/2017
ms.topic: conceptual
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- Visio [Office development in Visual Studio], creating Visio documents
- documents [Office development in Visual Studio], creating Visio documents
author: John-Hart
ms.author: johnhart
manager: jillfra
ms.workload:
- office
ms.openlocfilehash: bfefb49b2dea575a7a99c2531a6f241872cd4704
ms.sourcegitcommit: d0425b6b7d4b99e17ca6ac0671282bc718f80910
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 02/21/2019
ms.locfileid: "56629988"
---
# <a name="how-to-programmatically-create-new-visio-documents"></a>Vorgehensweise: Programmgesteuertes Erstellen Sie Neuer Visio-Dokumente
  Wenn Sie ein neues Microsoft Office Visio-Zeichnungsdokument erstellen, fügen Sie dieses Dokument der `Microsoft.Office.Interop.Visio.Documents`-Auflistung geöffneter Visio-Dokumente hinzu. Daher wird ein neues Visio-Zeichnungsdokument mithilfe der `Microsoft.Office.Interop.Visio.Documents.Add`-Methode erstellt. Weitere Informationen finden Sie in der VBA-Referenzdokumentation für die [Microsoft.Office.Interop.Visio.Documents.Add](/office/vba/api/Visio.Documents.Add) -Methode.

## <a name="create-new-blank-documents"></a>Erstellen neuer leerer Dokumente

### <a name="to-create-a-new-document"></a>So erstellen Sie ein neues Dokument

-   Verwenden Sie die `Microsoft.Office.Interop.Visio.Documents.Add`-Methode, um ein neues leeres Dokument zu erstellen, das nicht auf einer Vorlage basiert.

     [!code-csharp[Trin_VstcoreVisioAutomationAddIn#1](../vsto/codesnippet/CSharp/trin_vstcorevisioautomationaddin/ThisAddIn.cs#1)]
     [!code-vb[Trin_VstcoreVisioAutomationAddIn#1](../vsto/codesnippet/VisualBasic/trin_vstcorevisioautomationaddin/ThisAddIn.vb#1)]

## <a name="create-documents-copied-from-existing-documents"></a>Erstellen von aus vorhandenen Dokumenten kopierten Dokumenten
 Mit der `Microsoft.Office.Interop.Visio.Documents.Add`-Methode können Sie ein neues Dokument erstellen, das eine Kopie eines vorhandenen Visio-Dokuments ist. Sie müssen den Dateinamen und den vollqualifizierten Pfad des Diagramms angeben.

### <a name="to-create-a-new-document-that-is-copied-from-an-existing-document"></a>So erstellen Sie ein neues Dokument, das aus einem vorhandenen Dokument kopiert wird

-   Rufen Sie die `Microsoft.Office.Interop.Visio.Documents.Add`-Methode auf, und geben Sie den Pfad zum Visio-Diagramm an.

     [!code-csharp[Trin_VstcoreVisioAutomationAddIn#2](../vsto/codesnippet/CSharp/trin_vstcorevisioautomationaddin/ThisAddIn.cs#2)]
     [!code-vb[Trin_VstcoreVisioAutomationAddIn#2](../vsto/codesnippet/VisualBasic/trin_vstcorevisioautomationaddin/ThisAddIn.vb#2)]

## <a name="create-stencils-copied-from-existing-stencils"></a>Erstellen Sie aus vorhandenen Schablonen kopierte Schablonen
 Mit der [Microsoft.Office.Interop.Visio.Documents.Add](/office/vba/api/Visio.Documents.Add) -Methode können Sie eine neue Schablone erstellen, die eine Kopie einer vorhandenen Visio-Schablone ist. Sie müssen den Dateinamen und den vollqualifizierten Pfad der Schablone angeben.

### <a name="to-create-a-new-stencil-that-is-copied-from-an-existing-stencil"></a>So erstellen Sie eine neue Schablone, die aus einer vorhandenen Schablone kopiert wird

-   Rufen Sie die `Microsoft.Office.Interop.Visio.Documents.Add`-Methode auf, und geben Sie den Pfad der Schablone an.

     [!code-csharp[Trin_VstcoreVisioAutomationAddIn#3](../vsto/codesnippet/CSharp/trin_vstcorevisioautomationaddin/ThisAddIn.cs#3)]
     [!code-vb[Trin_VstcoreVisioAutomationAddIn#3](../vsto/codesnippet/VisualBasic/trin_vstcorevisioautomationaddin/ThisAddIn.vb#3)]

## <a name="create-documents-based-on-existing-templates"></a>Erstellen von Dokumenten auf Grundlage vorhandener Vorlagen
 Die `Microsoft.Office.Interop.Visio.Documents.Add` -Methode können Sie ein neues Dokument erstellen (eine *.vsd* Datei), basiert auf einer vorhandenen Visio-Vorlage (einer *VST* Datei). Diese Methode kopiert die Schablonen, Formate und Einstellungen, die Bestandteile des Vorlagenarbeitsbereichs sind. Sie müssen den Dateinamen und den vollqualifizierten Pfad der Vorlage angeben.

### <a name="to-create-a-new-document-that-is-based-on-an-existing-template"></a>So erstellen Sie ein neues Dokument, das auf einer vorhandenen Vorlage basiert

-   Rufen Sie die `Microsoft.Office.Interop.Visio.Documents.Add`-Methode auf, und geben Sie den Pfad der Vorlage an.

     [!code-csharp[Trin_VstcoreVisioAutomationAddIn#4](../vsto/codesnippet/CSharp/trin_vstcorevisioautomationaddin/ThisAddIn.cs#4)]
     [!code-vb[Trin_VstcoreVisioAutomationAddIn#4](../vsto/codesnippet/VisualBasic/trin_vstcorevisioautomationaddin/ThisAddIn.vb#4)]

## <a name="compile-the-code"></a>Kompilieren des Codes
 Für dieses Codebeispiel benötigen Sie Folgendes:

-   Ein Visio-Dokument mit dem Namen `myDrawing.vsd` Wohnsitz in einem Verzeichnis namens `Test` in die *eigene* Ordner (für Windows XP und früher) oder die *Dokumente* Ordner (für Windows Vista).

-   Ein Visio-Dokument mit dem Namen `myStencil.vss` Wohnsitz in einem Verzeichnis namens `Test` in die *eigene* Ordner (für Windows XP und früher) oder die *Dokumente* Ordner (für Windows Vista).

-   Ein Visio-Dokument mit dem Namen `myTemplate.vst` Wohnsitz in einem Verzeichnis namens `Test` in die *eigene* Ordner (für Windows XP und früher) oder die *Dokumente* Ordner (für Windows Vista).

## <a name="see-also"></a>Siehe auch
- [Visio-Projektmappen](../vsto/visio-solutions.md)
- [Übersicht über das Visio-Objektmodell](../vsto/visio-object-model-overview.md)
- [Vorgehensweise: Programmgesteuertes Öffnen von Visio-Dokumenten](../vsto/how-to-programmatically-open-visio-documents.md)
- [Vorgehensweise: Programmgesteuertes Schließen von Visio-Dokumenten](../vsto/how-to-programmatically-close-visio-documents.md)
- [Vorgehensweise: Programmgesteuertes Speichern von Visio-Dokumenten](../vsto/how-to-programmatically-save-visio-documents.md)
- [Vorgehensweise: Programmgesteuertes Drucken von Visio-Dokumenten](../vsto/how-to-programmatically-print-visio-documents.md)
