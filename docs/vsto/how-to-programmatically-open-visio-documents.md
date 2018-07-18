---
title: 'Gewusst wie: Programmgesteuertes Öffnen von Visio-Dokumenten'
ms.custom: ''
ms.date: 02/02/2017
ms.technology:
- office-development
ms.topic: conceptual
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- documents [Office development in Visual Studio], opening Visio documents
- Visio [Office development in Visual Studio], opening Visio documents
author: TerryGLee
ms.author: tglee
manager: douge
ms.workload:
- office
ms.openlocfilehash: a3a7d2a9855abef0415661798c8a213eb748e22f
ms.sourcegitcommit: 34f7d23ce3bd140dcae875b602d5719bb4363ed1
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 06/11/2018
ms.locfileid: "35257851"
---
# <a name="how-to-programmatically-open-visio-documents"></a>Gewusst wie: Programmgesteuertes Öffnen von Visio-Dokumenten
  Es gibt zwei Methoden zum Öffnen vorhandener Microsoft Office Visio-Dokumente: Öffnen und OpenEx. Die OpenEx-Methode ist identisch mit der Open-Methode, außer dass sie Argumente bereitstellt, in denen der Aufrufer angeben kann, wie das Dokument geöffnet wird.  
  
 Ausführliche Informationen zum Objektmodell finden Sie in der VBA-Referenzdokumentation für die [Microsoft.Office.Interop.Visio.Documents.Open](https://msdn.microsoft.com/library/office/ff765240.aspx) - und [Microsoft.Office.Interop.Visio.Documents.OpenEx](https://msdn.microsoft.com/library/office/ff767229.aspx) -Methode.  
  
## <a name="open-a-visio-document"></a>Öffnen Sie ein Visio-Dokument  
  
### <a name="to-open-a-visio-document"></a>So öffnen Sie ein Visio-Dokument  
  
-   Rufen Sie die `Microsoft.Office.Interop.Visio.Documents.Open` -Methode, und geben Sie den vollqualifizierten Pfad des Visio-Dokuments.  
  
     [!code-csharp[Trin_VstcoreVisioAutomationAddIn#5](../vsto/codesnippet/CSharp/trin_vstcorevisioautomationaddin/ThisAddIn.cs#5)]
     [!code-vb[Trin_VstcoreVisioAutomationAddIn#5](../vsto/codesnippet/VisualBasic/trin_vstcorevisioautomationaddin/ThisAddIn.vb#5)]  
  
## <a name="open-a-visio-document-with-specified-arguments"></a>Öffnen Sie ein Visio-Dokument mit angegebenen Argumenten  
  
### <a name="to-open-a-visio-document-as-read-only-and-docked"></a>So öffnen Sie ein Visio-Dokument schreibgeschützt und angedockt  
  
-   Rufen Sie die `Microsoft.Office.Interop.Visio.Documents.OpenEx` Methode, geben Sie den vollqualifizierten Pfad des Visio-Dokuments, und schließen Sie die Argumente, die Sie verwenden möchten – in diesem Fall angedockten und schreibgeschützt.  
  
     [!code-csharp[Trin_VstcoreVisioAutomationAddIn#6](../vsto/codesnippet/CSharp/trin_vstcorevisioautomationaddin/ThisAddIn.cs#6)]
     [!code-vb[Trin_VstcoreVisioAutomationAddIn#6](../vsto/codesnippet/VisualBasic/trin_vstcorevisioautomationaddin/ThisAddIn.vb#6)]  
  
## <a name="compile-the-code"></a>Kompilieren des Codes  
 Für dieses Codebeispiel benötigen Sie Folgendes:  
  
-   Ein Visio-Dokument mit dem Namen `myDrawing.vsd` Wohnsitz in einem Verzeichnis namens `Test` in die *eigene* Ordner (für Windows XP und früher) oder die *Dokumente* Ordner (für Windows Vista).  
  
## <a name="see-also"></a>Siehe auch  
 [Visio-Projektmappen](../vsto/visio-solutions.md)   
 [Übersicht über das Visio-Objektmodell](../vsto/visio-object-model-overview.md)   
 [Gewusst wie: Programmgesteuertes Erstellen neuer Visio-Dokumente](../vsto/how-to-programmatically-create-new-visio-documents.md)   
 [Gewusst wie: Programmgesteuertes Schließen von Visio-Dokumenten](../vsto/how-to-programmatically-close-visio-documents.md)   
 [Gewusst wie: Programmgesteuertes Speichern von Visio-Dokumenten](../vsto/how-to-programmatically-save-visio-documents.md)   
 [Gewusst wie: Programmgesteuertes Drucken von Visio-Dokumenten](../vsto/how-to-programmatically-print-visio-documents.md)  
  
  