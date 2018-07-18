---
title: 'Gewusst wie: Programmgesteuertes kopieren und Einfügen von Shapes in Visio-Dokumenten'
ms.custom: ''
ms.date: 02/02/2017
ms.technology:
- office-development
ms.topic: conceptual
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- shapes [Office development in Visual Studio], copying and pasting Visio shapes
- Visio [Office development in Visual Studio], copying and pasting Visio shapes
author: TerryGLee
ms.author: tglee
manager: douge
ms.workload:
- office
ms.openlocfilehash: 29dada62bb1e51c9cafb41d4eae08ce10e9a930c
ms.sourcegitcommit: 34f7d23ce3bd140dcae875b602d5719bb4363ed1
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 06/11/2018
ms.locfileid: "35257084"
---
# <a name="how-to-programmatically-copy-and-paste-shapes-in-a-visio-document"></a>Gewusst wie: Programmgesteuertes kopieren und Einfügen von Shapes in Visio-Dokumenten
  Sie können programmgesteuert Shapes auf einer Seite eines Dokuments kopieren und in eine neue Seite im selben Dokument einfügen. Sie können die Shapes wahlweise an der Standardposition (in der Mitte des aktiven Fensters) oder an der gleichen Koordinatenpositionen wie auf der ursprünglichen Seite einfügen.  
  
## <a name="copy-and-paste-shapes"></a>Kopieren und Einfügen von shapes  
 Ausführliche Informationen zum Objektmodell finden Sie in der VBA-Referenzdokumentation für die Methoden [Microsoft.Office.Interop.Visio.Shape.DrawRectangle](https://msdn.microsoft.com/library/office/ff765757.aspx), [Microsoft.Office.Interop.Visio.Shape.DrawOval](https://msdn.microsoft.com/library/office/ff767121.aspx), [Microsoft.Office.Interop.Visio.Shape.Copy](https://msdn.microsoft.com/library/office/ff765638.aspx)und [Microsoft.Office.Interop.Visio.Shape.Paste](https://msdn.microsoft.com/library/office/ff768361.aspx) sowie das Flag [Microsoft.Office.Interop.Visio.VisCutCopyPasteCodes.visCopyPasteNormal](https://msdn.microsoft.com/library/office/ff765187.aspx) .  
  
### <a name="to-copy-shapes-to-the-center-of-another-page"></a>So kopieren Sie Shapes in die Mitte einer anderen Seite  
  
-   Im folgenden Beispiel wird veranschaulicht, wie Sie die Shapes auf der ersten Seite kopieren und in der Mitte der zweiten Seite einfügen.  
  
     [!code-csharp[Trin_VstcoreVisioAutomationAddIn#14](../vsto/codesnippet/CSharp/trin_vstcorevisioautomationaddin/ThisAddIn.cs#14)]
     [!code-vb[Trin_VstcoreVisioAutomationAddIn#14](../vsto/codesnippet/VisualBasic/trin_vstcorevisioautomationaddin/ThisAddIn.vb#14)]  
  
## <a name="copy-and-paste-shapes-with-the-same-positions"></a>Kopieren und Einfügen von Shapes an der gleichen Position  
 Ausführliche Informationen zum Objektmodell finden Sie in der VBA-Referenzdokumentation für die Methoden [Microsoft.Office.Interop.Visio.Shape.DrawRectangle](https://msdn.microsoft.com/library/office/ff765757.aspx), [Microsoft.Office.Interop.Visio.Shape.DrawOval](https://msdn.microsoft.com/library/office/ff767121.aspx), [Microsoft.Office.Interop.Visio.Shape.Copy](https://msdn.microsoft.com/library/office/ff765638.aspx)und [Microsoft.Office.Interop.Visio.Shape.Paste](https://msdn.microsoft.com/library/office/ff768361.aspx) sowie das Flag [Microsoft.Office.Interop.Visio.VisCutCopyPasteCodes.visCopyPasteNoTranslate](https://msdn.microsoft.com/library/office/ff765187.aspx) .  
  
 Wenn Sie das Format der eingefügten Informationen steuern und (optional) eine Verknüpfung zu einer Quelldatei (z. B. Microsoft Office Word-Dokument) herstellen möchten, verwenden Sie die PasteSpecial-Methode.  
  
### <a name="to-copy-shapes-and-shape-locations-to-another-page"></a>So kopieren Sie Shapes und ihre Positionen auf eine andere Seite  
  
-   Im folgenden Beispiel wird veranschaulicht, wie Sie die Shapes auf der ersten Seite kopieren und auf der zweiten Seite an ihren ursprünglichen Koordinatenpositionen einfügen.  
  
     [!code-csharp[Trin_VstcoreVisioAutomationAddIn#15](../vsto/codesnippet/CSharp/trin_vstcorevisioautomationaddin/ThisAddIn.cs#15)]
     [!code-vb[Trin_VstcoreVisioAutomationAddIn#15](../vsto/codesnippet/VisualBasic/trin_vstcorevisioautomationaddin/ThisAddIn.vb#15)]  
  
## <a name="see-also"></a>Siehe auch  
 [Visio-Projektmappen](../vsto/visio-solutions.md)   
 [Übersicht über das Visio-Objektmodell](../vsto/visio-object-model-overview.md)   
 [Arbeiten mit Visio-shapes](../vsto/working-with-visio-shapes.md)   
 [Gewusst wie: Programmgesteuertes Hinzufügen von Shapes zu Visio-Dokumenten](../vsto/how-to-programmatically-add-shapes-to-a-visio-document.md)  
  
  