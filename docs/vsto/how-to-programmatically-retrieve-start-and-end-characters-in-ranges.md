---
title: 'Vorgehensweise: Programmgesteuertes Abrufen von Start- und Endzeichen in Bereichen | Microsoft Docs'
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
- ranges, retrieving start and end characters
- end characters
- start characters
- documents [Office development in Visual Studio], retrieving ranges
author: TerryGLee
ms.author: tglee
manager: ghogen
ms.workload: office
ms.openlocfilehash: 51f88435a5dff346e3de793b408f67e2837478e8
ms.sourcegitcommit: f9fbf1f55f9ac14e4e5c6ae58c30dc1800ca6cda
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 01/10/2018
---
# <a name="how-to-programmatically-retrieve-start-and-end-characters-in-ranges"></a>Gewusst wie: Programmgesteuertes Abrufen von Start- und Endzeichen in Bereichen
  In diesem Beispiel wird veranschaulicht, wie Sie die Zeichenpositionen der Anfangs- und Endposition eines Bereichs abrufen können.  
  
 [!INCLUDE[appliesto_wdalldocapp](../vsto/includes/appliesto-wdalldocapp-md.md)]  
  
### <a name="to-retrieve-start-and-end-characters-of-a-range-in-a-document-level-customization"></a>So rufen Sie Start- und Endzeichen eines Bereichs in einer Anpassung auf Dokumentebene ab  
  
1.  Rufen Sie die Werte der <xref:Microsoft.Office.Interop.Word.Range.Start%2A> -Eigenschaft und der <xref:Microsoft.Office.Interop.Word.Range.End%2A> -Eigenschaft des <xref:Microsoft.Office.Interop.Word.Range> -Objekts ab. Im folgenden Codebeispiel werden die Start- und Endposition des zweiten Satzes im Dokument abgerufen. Wenn Sie dieses Codebeispiel verwenden möchten, führen Sie es von der `ThisDocument` -Klasse im Projekt aus.  
  
     [!code-vb[Trin_VstcoreWordAutomation#25](../vsto/codesnippet/VisualBasic/Trin_VstcoreWordAutomationVB/ThisDocument.vb#25)]
     [!code-csharp[Trin_VstcoreWordAutomation#25](../vsto/codesnippet/CSharp/Trin_VstcoreWordAutomationCS/ThisDocument.cs#25)]  
  
### <a name="to-retrieve-start-and-end-characters-of-a-range-by-using-an-vsto-add-in"></a>So rufen Sie Start- und Endzeichen eines Bereichs mit einem VSTO-Add-Ins ab  
  
1.  Rufen Sie die Werte der <xref:Microsoft.Office.Interop.Word.Range.Start%2A> -Eigenschaft und der <xref:Microsoft.Office.Interop.Word.Range.End%2A> -Eigenschaft des <xref:Microsoft.Office.Interop.Word.Range> -Objekts ab. Im folgenden Codebeispiel werden die Start- und Endposition des zweiten Satzes im aktiven Dokument abgerufen. Wenn Sie dieses Codebeispiel verwenden möchten, führen Sie es von der `ThisAddIn` -Klasse im Projekt aus.  
  
     [!code-vb[Trin_VstcoreWordAutomationAddIn#25](../vsto/codesnippet/VisualBasic/Trin_VstcoreWordAutomationAddIn/ThisAddIn.vb#25)]
     [!code-csharp[Trin_VstcoreWordAutomationAddIn#25](../vsto/codesnippet/CSharp/Trin_VstcoreWordAutomationAddIn/ThisAddIn.cs#25)]  
  
## <a name="see-also"></a>Siehe auch  
 [Vorgehensweise: Programmgesteuertes definieren und Markieren von Bereichen in Dokumenten](../vsto/how-to-programmatically-define-and-select-ranges-in-documents.md)   
 [Vorgehensweise: Programmgesteuertes Erweitern von Bereichen in Dokumenten](../vsto/how-to-programmatically-extend-ranges-in-documents.md)   
 [Vorgehensweise: Programmgesteuertes Zurücksetzen von Bereichen in Word-Dokumenten](../vsto/how-to-programmatically-reset-ranges-in-word-documents.md)   
 [Vorgehensweise: Programmgesteuertes Reduzieren von Bereichen oder Markierungen in Dokumenten](../vsto/how-to-programmatically-collapse-ranges-or-selections-in-documents.md)   
 [Vorgehensweise: Programmgesteuertes Ausschließen von Absatzmarken beim Erstellen von Bereichen](../vsto/how-to-programmatically-exclude-paragraph-marks-when-creating-ranges.md)   
 [Vorgehensweise: Programmgesteuertes Zählen von Zeichen in Dokumenten](../vsto/how-to-programmatically-count-characters-in-documents.md)  
  
  