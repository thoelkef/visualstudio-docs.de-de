---
title: 'Vorgehensweise: Programmgesteuertes Entfernen aller Kommentare aus Dokumenten | Microsoft Docs'
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
- documents [Office development in Visual Studio], removing comments
- comments, removing from documents
ms.assetid: 920de39a-3b6d-4682-bca6-f4b4dedda1ac
caps.latest.revision: "24"
author: gewarren
ms.author: gewarren
manager: ghogen
ms.openlocfilehash: c85ea6dba57d69c4936ac05687516c0195a1d82f
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 10/31/2017
---
# <a name="how-to-programmatically-remove-all-comments-from-documents"></a>Gewusst wie: Programmgesteuertes Entfernen aller Kommentare aus einem Dokument
  Verwenden Sie die DeleteAllComments-Methode, um alle Kommentare aus einem Microsoft Office Word-Dokument zu entfernen.  
  
 [!INCLUDE[appliesto_wdalldocapp](../vsto/includes/appliesto-wdalldocapp-md.md)]  
  
### <a name="to-remove-all-comments-from-a-document-that-is-part-of-a-document-level-customization"></a>So entfernen Sie alle Kommentare aus einem Dokument, das Teil einer Anpassung auf Dokumentebene ist  
  
1.  Rufen Sie in Ihrem Projekt die <xref:Microsoft.Office.Tools.Word.Document.DeleteAllComments%2A> -Methode der `ThisDocument` -Klasse auf. Wenn Sie dieses Codebeispiel verwenden möchten, führen Sie es über die `ThisDocument` -Klasse aus.  
  
     [!code-vb[Trin_VstcoreWordAutomation#119](../vsto/codesnippet/VisualBasic/Trin_VstcoreWordAutomationVB/ThisDocument.vb#119)]
     [!code-csharp[Trin_VstcoreWordAutomation#119](../vsto/codesnippet/CSharp/Trin_VstcoreWordAutomationCS/ThisDocument.cs#119)]  
  
### <a name="to-remove-all-comments-from-a-document-by-using-an-vsto-add-in"></a>So entfernen Sie mithilfe eines VSTO-Add-Ins alle Kommentare aus einem Dokument  
  
1.  Rufen Sie die <xref:Microsoft.Office.Interop.Word._Document.DeleteAllComments%2A> -Methode der <xref:Microsoft.Office.Interop.Word.Document> auf, aus der Sie Kommentare entfernen möchten.  
  
     Das folgende Codebeispiel entfernt alle Kommentare aus dem aktiven Dokument. Wenn Sie dieses Codebeispiel verwenden möchten, führen Sie es von der `ThisAddIn` -Klasse im Projekt aus.  
  
     [!code-vb[Trin_VstcoreWordAutomationAddIn#119](../vsto/codesnippet/VisualBasic/Trin_VstcoreWordAutomationAddIn/ThisAddIn.vb#119)]
     [!code-csharp[Trin_VstcoreWordAutomationAddIn#119](../vsto/codesnippet/CSharp/Trin_VstcoreWordAutomationAddIn/ThisAddIn.cs#119)]  
  
## <a name="see-also"></a>Siehe auch  
 [Vorgehensweise: Programmgesteuertes Hinzufügen von Kommentaren zu Text in Dokumenten](../vsto/how-to-programmatically-add-comments-to-text-in-documents.md)   
 [Dokumenthostelement](../vsto/document-host-item.md)  
  
  