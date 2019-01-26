---
title: 'Vorgehensweise: Programmgesteuertes kopieren und Einfügen von Shapes in Visio-Dokumenten'
ms.date: 02/02/2017
ms.topic: conceptual
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- shapes [Office development in Visual Studio], copying and pasting Visio shapes
- Visio [Office development in Visual Studio], copying and pasting Visio shapes
author: John-Hart
ms.author: johnhart
manager: jillfra
ms.workload:
- office
ms.openlocfilehash: fe02a88c5213fd67e26dc545af4b18a64473c754
ms.sourcegitcommit: c0202a77d4dc562cdc55dc2e6223c062281d9749
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 01/24/2019
ms.locfileid: "54865177"
---
# <a name="how-to-programmatically-copy-and-paste-shapes-in-a-visio-document"></a>Vorgehensweise: Programmgesteuertes kopieren und Einfügen von Shapes in Visio-Dokumenten
  Sie können programmgesteuert Shapes auf einer Seite eines Dokuments kopieren und in eine neue Seite im selben Dokument einfügen. Sie können die Shapes wahlweise an der Standardposition (in der Mitte des aktiven Fensters) oder an der gleichen Koordinatenpositionen wie auf der ursprünglichen Seite einfügen.  
  
## <a name="copy-and-paste-shapes"></a>Kopieren und Einfügen von shapes  
 Ausführliche Informationen zum Objektmodell finden Sie in der VBA-Referenzdokumentation für die Methoden [Microsoft.Office.Interop.Visio.Shape.DrawRectangle](/office/vba/api/Visio.Shape.DrawRectangle), [Microsoft.Office.Interop.Visio.Shape.DrawOval](/office/vba/api/Visio.Shape.DrawOval), [Microsoft.Office.Interop.Visio.Shape.Copy](/office/vba/api/Visio.Shape.Copy)und [Microsoft.Office.Interop.Visio.Shape.Paste](/office/vba/api/Visio.Shape.Paste) sowie das Flag [Microsoft.Office.Interop.Visio.VisCutCopyPasteCodes.visCopyPasteNormal](/office/vba/api/Visio.viscutcopypastecodes) .  
  
### <a name="to-copy-shapes-to-the-center-of-another-page"></a>So kopieren Sie Shapes in die Mitte einer anderen Seite  
  
-   Im folgenden Beispiel wird veranschaulicht, wie Sie die Shapes auf der ersten Seite kopieren und in der Mitte der zweiten Seite einfügen.  
  
     [!code-csharp[Trin_VstcoreVisioAutomationAddIn#14](../vsto/codesnippet/CSharp/trin_vstcorevisioautomationaddin/ThisAddIn.cs#14)]
     [!code-vb[Trin_VstcoreVisioAutomationAddIn#14](../vsto/codesnippet/VisualBasic/trin_vstcorevisioautomationaddin/ThisAddIn.vb#14)]  
  
## <a name="copy-and-paste-shapes-with-the-same-positions"></a>Kopieren und Einfügen von Shapes an der gleichen Position  
 Ausführliche Informationen zum Objektmodell finden Sie in der VBA-Referenzdokumentation für die Methoden [Microsoft.Office.Interop.Visio.Shape.DrawRectangle](/office/vba/api/Visio.Shape.DrawRectangle), [Microsoft.Office.Interop.Visio.Shape.DrawOval](/office/vba/api/Visio.Shape.DrawOval), [Microsoft.Office.Interop.Visio.Shape.Copy](/office/vba/api/Visio.Shape.Copy)und [Microsoft.Office.Interop.Visio.Shape.Paste](/office/vba/api/Visio.Shape.Paste) sowie das Flag [Microsoft.Office.Interop.Visio.VisCutCopyPasteCodes.visCopyPasteNoTranslate](/office/vba/api/Visio.viscutcopypastecodes) .  
  
 Wenn Sie das Format der eingefügten Informationen steuern und (optional) eine Verknüpfung zu einer Quelldatei (z. B. Microsoft Office Word-Dokument) herstellen möchten, verwenden Sie die PasteSpecial-Methode.  
  
### <a name="to-copy-shapes-and-shape-locations-to-another-page"></a>So kopieren Sie Shapes und ihre Positionen auf eine andere Seite  
  
-   Im folgenden Beispiel wird veranschaulicht, wie Sie die Shapes auf der ersten Seite kopieren und auf der zweiten Seite an ihren ursprünglichen Koordinatenpositionen einfügen.  
  
     [!code-csharp[Trin_VstcoreVisioAutomationAddIn#15](../vsto/codesnippet/CSharp/trin_vstcorevisioautomationaddin/ThisAddIn.cs#15)]
     [!code-vb[Trin_VstcoreVisioAutomationAddIn#15](../vsto/codesnippet/VisualBasic/trin_vstcorevisioautomationaddin/ThisAddIn.vb#15)]  
  
## <a name="see-also"></a>Siehe auch  
 [Visio-Projektmappen](../vsto/visio-solutions.md)   
 [Übersicht über das Visio-Objektmodell](../vsto/visio-object-model-overview.md)   
 [Arbeiten mit Visio-shapes](../vsto/working-with-visio-shapes.md)   
 [Vorgehensweise: Programmgesteuertes Hinzufügen von Shapes zu Visio-Dokumenten](../vsto/how-to-programmatically-add-shapes-to-a-visio-document.md)  
