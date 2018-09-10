---
title: 'Gewusst wie: Programmgesteuertes zählen von Zeichen in Dokumenten'
ms.custom: ''
ms.date: 02/02/2017
ms.technology:
- office-development
ms.topic: conceptual
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- characters, counting in documents
- counting characters in documents
- documents [Office development in Visual Studio], counting characters
author: TerryGLee
ms.author: tglee
manager: douge
ms.workload:
- office
ms.openlocfilehash: 46ead2f1774d779706e8aa6eeb3f1e9c6b1d0ce1
ms.sourcegitcommit: 6944ceb7193d410a2a913ecee6f40c6e87e8a54b
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 09/06/2018
ms.locfileid: "35672728"
---
# <a name="how-to-programmatically-count-characters-in-documents"></a>Gewusst wie: Programmgesteuertes zählen von Zeichen in Dokumenten
  Das erste Zeichen in einem Dokument befindet sich an der Zeichenposition 0, die der Position der Einfügemarke entspricht. Die Position des letzten Zeichens ist gleich der Gesamtanzahl von Zeichen im Dokument. Sie können die Anzahl von Zeichen in einem Dokument mithilfe der <xref:Microsoft.Office.Interop.Word.Characters.Count%2A> -Eigenschaft der <xref:Microsoft.Office.Interop.Word.Characters> -Auflistung ermitteln.  
  
 In einem Dokument werden alle Zeichen gezählt, so auch Leerzeichen, Absatzmarken und andere Zeichen, die normalerweise ausgeblendet sind. Selbst für ein neues leeres Dokument wird eine Anzahl von Zeichen zurückgegeben, weil das Dokument eine Absatzmarke enthält.  
  
 [!INCLUDE[appliesto_wdalldocapp](../vsto/includes/appliesto-wdalldocapp-md.md)]  
  
## <a name="to-display-the-number-of-characters-in-a-document-level-customization"></a>So zeigen Sie die Anzahl von Zeichen in einer Anpassung auf Dokumentebene an  
  
1.  Wählen Sie das gesamte Dokument aus.  
  
     [!code-vb[Trin_VstcoreWordAutomation#98](../vsto/codesnippet/VisualBasic/Trin_VstcoreWordAutomationVB/ThisDocument.vb#98)]
     [!code-csharp[Trin_VstcoreWordAutomation#98](../vsto/codesnippet/CSharp/Trin_VstcoreWordAutomationCS/ThisDocument.cs#98)]  
  
2.  Zeigen Sie die Anzahl von Zeichen im Dokument in einem Meldungsfeld an.  
  
     [!code-vb[Trin_VstcoreWordAutomation#99](../vsto/codesnippet/VisualBasic/Trin_VstcoreWordAutomationVB/ThisDocument.vb#99)]
     [!code-csharp[Trin_VstcoreWordAutomation#99](../vsto/codesnippet/CSharp/Trin_VstcoreWordAutomationCS/ThisDocument.cs#99)]  
  
## <a name="to-display-the-number-of-characters-in-a-vsto-add-in"></a>Die Anzahl der Zeichen in einem VSTO-Add-in angezeigt.  
  
1.  Wählen Sie das gesamte Dokument aus. Im folgenden Beispiel wird das aktive Dokument ausgewählt.  
  
     [!code-vb[Trin_VstcoreWordAutomationAddIn#98](../vsto/codesnippet/VisualBasic/Trin_VstcoreWordAutomationAddIn/ThisAddIn.vb#98)]
     [!code-csharp[Trin_VstcoreWordAutomationAddIn#98](../vsto/codesnippet/CSharp/Trin_VstcoreWordAutomationAddIn/ThisAddIn.cs#98)]  
  
2.  Zeigen Sie die Anzahl von Zeichen im Dokument in einem Meldungsfeld an.  
  
     [!code-vb[Trin_VstcoreWordAutomationAddIn#99](../vsto/codesnippet/VisualBasic/Trin_VstcoreWordAutomationAddIn/ThisAddIn.vb#99)]
     [!code-csharp[Trin_VstcoreWordAutomationAddIn#99](../vsto/codesnippet/CSharp/Trin_VstcoreWordAutomationAddIn/ThisAddIn.cs#99)]  
  
## <a name="see-also"></a>Siehe auch  
 [Gewusst wie: Programmgesteuertes Abrufen von Start- und Endzeit von Zeichen in Bereichen](../vsto/how-to-programmatically-retrieve-start-and-end-characters-in-ranges.md)   
 [Gewusst wie: Programmgesteuertes definieren und Markieren von Bereichen in Dokumenten](../vsto/how-to-programmatically-define-and-select-ranges-in-documents.md)  
  
  