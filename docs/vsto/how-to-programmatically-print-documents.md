---
title: 'Vorgehensweise: Programmgesteuertes Drucken von Dokumenten | Microsoft Docs'
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
- Word [Office development in Visual Studio], printing documents
- documents [Office development in Visual Studio], printing
ms.assetid: 99285d98-1bb7-4ccb-83d9-e917b0a9ea42
caps.latest.revision: "53"
author: gewarren
ms.author: gewarren
manager: ghogen
ms.workload: office
ms.openlocfilehash: ec4808adeb38d0ee8cf13d28e181260fbbae95bc
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 12/22/2017
---
# <a name="how-to-programmatically-print-documents"></a>Gewusst wie: Programmgesteuertes Drucken von Dokumenten
  Sie können ein ganzes Microsoft Office Word-Dokument oder einen Teil eines Dokuments auf dem Standarddrucker drucken.  
  
 [!INCLUDE[appliesto_wdalldocapp](../vsto/includes/appliesto-wdalldocapp-md.md)]  
  
## <a name="printing-a-document-that-is-part-of-a-document-level-customization"></a>Drucken eines Dokuments, das ein Teil einer Anpassung auf Dokumentebene ist  
  
#### <a name="to-print-the-entire-document"></a>So drucken Sie das ganze Dokument  
  
1.  Rufen Sie die <xref:Microsoft.Office.Tools.Word.Document.PrintOut%2A> -Methode der `ThisDocument` -Klasse im Projekt auf, um das gesamte Dokument zu drucken. Um dieses Codebeispiel verwenden zu können, müssen Sie den Code in der `ThisDocument` -Klasse ausführen.  
  
     [!code-vb[Trin_VstcoreWordAutomation#11](../vsto/codesnippet/VisualBasic/Trin_VstcoreWordAutomationVB/ThisDocument.vb#11)]
     [!code-csharp[Trin_VstcoreWordAutomation#11](../vsto/codesnippet/CSharp/Trin_VstcoreWordAutomationCS/ThisDocument.cs#11)]  
  
#### <a name="to-print-the-current-page-of-the-document"></a>So drucken Sie die aktuelle Seite des Dokuments  
  
1.  Rufen Sie die <xref:Microsoft.Office.Tools.Word.Document.PrintOut%2A> -Methode der `ThisDocument` -Klasse im Projekt auf, und geben Sie an, dass eine Kopie der aktuellen Seite gedruckt werden soll. Um dieses Codebeispiel verwenden zu können, müssen Sie den Code in der `ThisDocument` -Klasse ausführen.  
  
     [!code-vb[Trin_VstcoreWordAutomation#12](../vsto/codesnippet/VisualBasic/Trin_VstcoreWordAutomationVB/ThisDocument.vb#12)]
     [!code-csharp[Trin_VstcoreWordAutomation#12](../vsto/codesnippet/CSharp/Trin_VstcoreWordAutomationCS/ThisDocument.cs#12)]  
  
## <a name="printing-a-document-by-using-an-vsto-add-in"></a>Drucken eines Dokuments mithilfe eines VSTO-Add-Ins  
  
#### <a name="to-print-an-entire-document"></a>So drucken Sie ein ganzes Dokument  
  
1.  Rufen Sie die <xref:Microsoft.Office.Interop.Word._Document.PrintOut%2A> -Methode des <xref:Microsoft.Office.Interop.Word.Document> -Objekts auf, das Sie drucken möchten. Im folgenden Codebeispiel wird das aktive Dokument gedruckt. Wenn Sie dieses Beispiel verwenden möchten, führen Sie den Code von der `ThisAddIn` -Klasse im Projekt aus.  
  
     [!code-vb[Trin_VstcoreWordAutomationAddIn#11](../vsto/codesnippet/VisualBasic/Trin_VstcoreWordAutomationAddIn/ThisAddIn.vb#11)]
     [!code-csharp[Trin_VstcoreWordAutomationAddIn#11](../vsto/codesnippet/CSharp/Trin_VstcoreWordAutomationAddIn/ThisAddIn.cs#11)]  
  
#### <a name="to-print-the-current-page-of-a-document"></a>So drucken Sie die aktuelle Seite eines Dokuments  
  
1.  Rufen Sie die <xref:Microsoft.Office.Interop.Word._Document.PrintOut%2A> -Methode des <xref:Microsoft.Office.Interop.Word.Document> -Objekts auf, das Sie drucken möchten, und geben Sie an, dass eine Kopie der aktuellen Seite gedruckt werden soll. Im folgenden Codebeispiel wird das aktive Dokument gedruckt. Wenn Sie dieses Beispiel verwenden möchten, führen Sie den Code von der `ThisAddIn` -Klasse im Projekt aus.  
  
     [!code-vb[Trin_VstcoreWordAutomationAddIn#12](../vsto/codesnippet/VisualBasic/Trin_VstcoreWordAutomationAddIn/ThisAddIn.vb#12)]
     [!code-csharp[Trin_VstcoreWordAutomationAddIn#12](../vsto/codesnippet/CSharp/Trin_VstcoreWordAutomationAddIn/ThisAddIn.cs#12)]  
  
## <a name="see-also"></a>Siehe auch  
 [Optionale Parameter in Office-Projektmappen](../vsto/optional-parameters-in-office-solutions.md)  
  
  