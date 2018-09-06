---
title: 'Gewusst wie: Programmgesteuertes Abrufen von Start- und Endzeit von Zeichen in Bereichen'
ms.custom: ''
ms.date: 02/02/2017
ms.technology:
- office-development
ms.topic: conceptual
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- ranges, retrieving start and end characters
- end characters
- start characters
- documents [Office development in Visual Studio], retrieving ranges
author: TerryGLee
ms.author: tglee
manager: douge
ms.workload:
- office
ms.openlocfilehash: 1244fb2ba0a9e902d4dd853e7bef25376a205a0e
ms.sourcegitcommit: 6944ceb7193d410a2a913ecee6f40c6e87e8a54b
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 09/06/2018
ms.locfileid: "35672309"
---
# <a name="how-to-programmatically-retrieve-start-and-end-characters-in-ranges"></a>Gewusst wie: Programmgesteuertes Abrufen von Start- und Endzeit von Zeichen in Bereichen
  In diesem Beispiel wird veranschaulicht, wie Sie die Zeichenpositionen der Anfangs- und Endposition eines Bereichs abrufen können.  
  
 [!INCLUDE[appliesto_wdalldocapp](../vsto/includes/appliesto-wdalldocapp-md.md)]  
  
## <a name="to-retrieve-start-and-end-characters-of-a-range-in-a-document-level-customization"></a>So rufen Sie Start- und Endzeichen eines Bereichs in einer Anpassung auf Dokumentebene ab  
  
1.  Rufen Sie die Werte der <xref:Microsoft.Office.Interop.Word.Range.Start%2A> -Eigenschaft und der <xref:Microsoft.Office.Interop.Word.Range.End%2A> -Eigenschaft des <xref:Microsoft.Office.Interop.Word.Range> -Objekts ab. Im folgenden Codebeispiel werden die Start- und Endposition des zweiten Satzes im Dokument abgerufen. Wenn Sie dieses Codebeispiel verwenden möchten, führen Sie es von der `ThisDocument` -Klasse im Projekt aus.  
  
     [!code-vb[Trin_VstcoreWordAutomation#25](../vsto/codesnippet/VisualBasic/Trin_VstcoreWordAutomationVB/ThisDocument.vb#25)]
     [!code-csharp[Trin_VstcoreWordAutomation#25](../vsto/codesnippet/CSharp/Trin_VstcoreWordAutomationCS/ThisDocument.cs#25)]  
  
## <a name="to-retrieve-start-and-end-characters-of-a-range-by-using-a-vsto-add-in"></a>Zum Abrufen von Start- und Endzeit Zeichen eines Bereichs mithilfe eines VSTO-Add-Ins  
  
1.  Rufen Sie die Werte der <xref:Microsoft.Office.Interop.Word.Range.Start%2A> -Eigenschaft und der <xref:Microsoft.Office.Interop.Word.Range.End%2A> -Eigenschaft des <xref:Microsoft.Office.Interop.Word.Range> -Objekts ab. Im folgenden Codebeispiel werden die Start- und Endposition des zweiten Satzes im aktiven Dokument abgerufen. Wenn Sie dieses Codebeispiel verwenden möchten, führen Sie es von der `ThisAddIn` -Klasse im Projekt aus.  
  
     [!code-vb[Trin_VstcoreWordAutomationAddIn#25](../vsto/codesnippet/VisualBasic/Trin_VstcoreWordAutomationAddIn/ThisAddIn.vb#25)]
     [!code-csharp[Trin_VstcoreWordAutomationAddIn#25](../vsto/codesnippet/CSharp/Trin_VstcoreWordAutomationAddIn/ThisAddIn.cs#25)]  
  
## <a name="see-also"></a>Siehe auch  
 [Gewusst wie: Programmgesteuertes definieren und Markieren von Bereichen in Dokumenten](../vsto/how-to-programmatically-define-and-select-ranges-in-documents.md)   
 [Gewusst wie: Programmgesteuertes Erweitern von Bereichen in Dokumenten](../vsto/how-to-programmatically-extend-ranges-in-documents.md)   
 [Gewusst wie: Programmgesteuertes Zurücksetzen von Bereichen in Word-Dokumenten](../vsto/how-to-programmatically-reset-ranges-in-word-documents.md)   
 [Gewusst wie: Programmgesteuertes Reduzieren von Bereichen oder Markierungen in Dokumenten](../vsto/how-to-programmatically-collapse-ranges-or-selections-in-documents.md)   
 [Gewusst wie: Programmgesteuertes Ausschließen von Absatzmarken beim Erstellen von Bereichen](../vsto/how-to-programmatically-exclude-paragraph-marks-when-creating-ranges.md)   
 [Gewusst wie: Programmgesteuertes zählen von Zeichen in Dokumenten](../vsto/how-to-programmatically-count-characters-in-documents.md)  
  
  