---
title: 'Vorgehensweise: Programmgesteuertes Abrufen von Start- und Endzeit von Zeichen in Bereichen'
ms.date: 02/02/2017
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
ms.openlocfilehash: 9891e54986cd829c92ab3f5a5ad3a81590cf1474
ms.sourcegitcommit: 37fb7075b0a65d2add3b137a5230767aa3266c74
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 01/02/2019
ms.locfileid: "53871199"
---
# <a name="how-to-programmatically-retrieve-start-and-end-characters-in-ranges"></a>Vorgehensweise: Programmgesteuertes Abrufen von Start- und Endzeit von Zeichen in Bereichen
  In diesem Beispiel wird veranschaulicht, wie Sie die Zeichenpositionen der Anfangs- und Endposition eines Bereichs abrufen können.  
  
 [!INCLUDE[appliesto_wdalldocapp](../vsto/includes/appliesto-wdalldocapp-md.md)]  
  
## <a name="to-retrieve-start-and-end-characters-of-a-range-in-a-document-level-customization"></a>So rufen Sie Start- und Endzeichen eines Bereichs in einer Anpassung auf Dokumentebene ab  
  
1.  Rufen Sie die Werte der <xref:Microsoft.Office.Interop.Word.Range.Start%2A>-Eigenschaft und der <xref:Microsoft.Office.Interop.Word.Range.End%2A>-Eigenschaft des <xref:Microsoft.Office.Interop.Word.Range>-Objekts ab. Im folgenden Codebeispiel werden die Start- und Endposition des zweiten Satzes im Dokument abgerufen. Wenn Sie dieses Codebeispiel verwenden möchten, führen Sie es von der `ThisDocument` -Klasse im Projekt aus.  
  
     [!code-vb[Trin_VstcoreWordAutomation#25](../vsto/codesnippet/VisualBasic/Trin_VstcoreWordAutomationVB/ThisDocument.vb#25)]
     [!code-csharp[Trin_VstcoreWordAutomation#25](../vsto/codesnippet/CSharp/Trin_VstcoreWordAutomationCS/ThisDocument.cs#25)]  
  
## <a name="to-retrieve-start-and-end-characters-of-a-range-by-using-a-vsto-add-in"></a>Zum Abrufen von Start- und Endzeit Zeichen eines Bereichs mithilfe eines VSTO-Add-Ins  
  
1.  Rufen Sie die Werte der <xref:Microsoft.Office.Interop.Word.Range.Start%2A> -Eigenschaft und der <xref:Microsoft.Office.Interop.Word.Range.End%2A> -Eigenschaft des <xref:Microsoft.Office.Interop.Word.Range> -Objekts ab. Im folgenden Codebeispiel werden die Start- und Endposition des zweiten Satzes im aktiven Dokument abgerufen. Wenn Sie dieses Codebeispiel verwenden möchten, führen Sie es von der `ThisAddIn` -Klasse im Projekt aus.  
  
     [!code-vb[Trin_VstcoreWordAutomationAddIn#25](../vsto/codesnippet/VisualBasic/Trin_VstcoreWordAutomationAddIn/ThisAddIn.vb#25)]
     [!code-csharp[Trin_VstcoreWordAutomationAddIn#25](../vsto/codesnippet/CSharp/Trin_VstcoreWordAutomationAddIn/ThisAddIn.cs#25)]  
  
## <a name="see-also"></a>Siehe auch  
 [Vorgehensweise: Programmgesteuertes definieren und Markieren von Bereichen in Dokumenten](../vsto/how-to-programmatically-define-and-select-ranges-in-documents.md)   
 [Vorgehensweise: Programmgesteuertes Erweitern von Bereichen in Dokumenten](../vsto/how-to-programmatically-extend-ranges-in-documents.md)   
 [Vorgehensweise: Programmgesteuertes Zurücksetzen von Bereichen in Word-Dokumenten](../vsto/how-to-programmatically-reset-ranges-in-word-documents.md)   
 [Vorgehensweise: Programmgesteuertes Reduzieren von Bereichen oder Markierungen in Dokumenten](../vsto/how-to-programmatically-collapse-ranges-or-selections-in-documents.md)   
 [Vorgehensweise: Programmgesteuertes ausschließen Absatzmarken beim Erstellen von Bereichen](../vsto/how-to-programmatically-exclude-paragraph-marks-when-creating-ranges.md)   
 [Vorgehensweise: Programmgesteuertes zählen von Zeichen in Dokumenten](../vsto/how-to-programmatically-count-characters-in-documents.md)  
