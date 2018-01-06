---
title: "Vorgehensweise: Programmgesteuertes kopieren und Einfügen von Shapes in Visio-Dokumenten | Microsoft Docs"
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
- shapes [Office development in Visual Studio], copying and pasting Visio shapes
- Visio [Office development in Visual Studio], copying and pasting Visio shapes
ms.assetid: 762d95cf-2d5c-4dea-988b-8f4da88fa1f1
caps.latest.revision: "15"
author: gewarren
ms.author: gewarren
manager: ghogen
ms.workload: office
ms.openlocfilehash: 5b1f3a402d4f39b3648bbcf577ff48a130625b50
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 12/22/2017
---
# <a name="how-to-programmatically-copy-and-paste-shapes-in-a-visio-document"></a>Gewusst wie: Programmgesteuertes Kopieren und Einfügen von Shapes in ein Visio-Dokument
  Sie können programmgesteuert Shapes auf einer Seite eines Dokuments kopieren und in eine neue Seite im selben Dokument einfügen. Sie können die Shapes wahlweise an der Standardposition (in der Mitte des aktiven Fensters) oder an der gleichen Koordinatenpositionen wie auf der ursprünglichen Seite einfügen.  
  
## <a name="copying-and-pasting-shapes"></a>Kopieren und Einfügen von Shapes  
 Ausführliche Informationen zum Objektmodell finden Sie in der VBA-Referenzdokumentation für die Methoden [Microsoft.Office.Interop.Visio.Shape.DrawRectangle](https://msdn.microsoft.com/library/office/ff765757.aspx), [Microsoft.Office.Interop.Visio.Shape.DrawOval](https://msdn.microsoft.com/library/office/ff767121.aspx), [Microsoft.Office.Interop.Visio.Shape.Copy](https://msdn.microsoft.com/library/office/ff765638.aspx)und [Microsoft.Office.Interop.Visio.Shape.Paste](https://msdn.microsoft.com/library/office/ff768361.aspx) sowie das Flag [Microsoft.Office.Interop.Visio.VisCutCopyPasteCodes.visCopyPasteNormal](https://msdn.microsoft.com/library/office/ff765187.aspx) .  
  
#### <a name="to-copy-shapes-to-the-center-of-another-page"></a>So kopieren Sie Shapes in die Mitte einer anderen Seite  
  
-   Im folgenden Beispiel wird veranschaulicht, wie Sie die Shapes auf der ersten Seite kopieren und in der Mitte der zweiten Seite einfügen.  
  
     [!code-csharp[Trin_VstcoreVisioAutomationAddIn#14](../vsto/codesnippet/CSharp/trin_vstcorevisioautomationaddin/ThisAddIn.cs#14)]
     [!code-vb[Trin_VstcoreVisioAutomationAddIn#14](../vsto/codesnippet/VisualBasic/trin_vstcorevisioautomationaddin/ThisAddIn.vb#14)]  
  
## <a name="copying-and-pasting-shapes-with-the-same-positions"></a>Kopieren und Einfügen von Shapes an der gleichen Position  
 Ausführliche Informationen zum Objektmodell finden Sie in der VBA-Referenzdokumentation für die Methoden [Microsoft.Office.Interop.Visio.Shape.DrawRectangle](https://msdn.microsoft.com/library/office/ff765757.aspx), [Microsoft.Office.Interop.Visio.Shape.DrawOval](https://msdn.microsoft.com/library/office/ff767121.aspx), [Microsoft.Office.Interop.Visio.Shape.Copy](https://msdn.microsoft.com/library/office/ff765638.aspx)und [Microsoft.Office.Interop.Visio.Shape.Paste](https://msdn.microsoft.com/library/office/ff768361.aspx) sowie das Flag [Microsoft.Office.Interop.Visio.VisCutCopyPasteCodes.visCopyPasteNoTranslate](https://msdn.microsoft.com/library/office/ff765187.aspx) .  
  
 Wenn Sie das Format der eingefügten Informationen steuern und (optional) eine Verknüpfung zur Quelldatei (z. B. Microsoft Office Word-Dokument) herstellen müssen, verwenden Sie die PasteSpecial-Methode.  
  
#### <a name="to-copy-shapes-and-shape-locations-to-another-page"></a>So kopieren Sie Shapes und ihre Positionen auf eine andere Seite  
  
-   Im folgenden Beispiel wird veranschaulicht, wie Sie die Shapes auf der ersten Seite kopieren und auf der zweiten Seite an ihren ursprünglichen Koordinatenpositionen einfügen.  
  
     [!code-csharp[Trin_VstcoreVisioAutomationAddIn#15](../vsto/codesnippet/CSharp/trin_vstcorevisioautomationaddin/ThisAddIn.cs#15)]
     [!code-vb[Trin_VstcoreVisioAutomationAddIn#15](../vsto/codesnippet/VisualBasic/trin_vstcorevisioautomationaddin/ThisAddIn.vb#15)]  
  
## <a name="see-also"></a>Siehe auch  
 [Visio-Projektmappen](../vsto/visio-solutions.md)   
 [Visio-Objektmodellübersicht](../vsto/visio-object-model-overview.md)   
 [Arbeiten mit Visio-Shapes](../vsto/working-with-visio-shapes.md)   
 [Vorgehensweise: Programmgesteuertes Hinzufügen von Shapes zu Visio-Dokumenten](../vsto/how-to-programmatically-add-shapes-to-a-visio-document.md)  
  
  