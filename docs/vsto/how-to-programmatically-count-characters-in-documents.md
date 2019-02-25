---
title: 'Vorgehensweise: Programmgesteuertes zählen von Zeichen in Dokumenten'
ms.date: 02/02/2017
ms.topic: conceptual
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- characters, counting in documents
- counting characters in documents
- documents [Office development in Visual Studio], counting characters
author: John-Hart
ms.author: johnhart
manager: jillfra
ms.workload:
- office
ms.openlocfilehash: c9e5dd79465301e5d2e6362daf70ef3e5b7c54ee
ms.sourcegitcommit: d0425b6b7d4b99e17ca6ac0671282bc718f80910
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 02/21/2019
ms.locfileid: "56646316"
---
# <a name="how-to-programmatically-count-characters-in-documents"></a>Vorgehensweise: Programmgesteuertes zählen von Zeichen in Dokumenten
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
- [Vorgehensweise: Programmgesteuertes Abrufen von Start- und Endzeit von Zeichen in Bereichen](../vsto/how-to-programmatically-retrieve-start-and-end-characters-in-ranges.md)
- [Vorgehensweise: Programmgesteuertes definieren und Markieren von Bereichen in Dokumenten](../vsto/how-to-programmatically-define-and-select-ranges-in-documents.md)
