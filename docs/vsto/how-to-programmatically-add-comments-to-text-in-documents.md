---
title: 'Vorgehensweise: Programmgesteuertes Hinzufügen von Kommentaren zu Text in Dokumenten'
ms.date: 02/02/2017
ms.topic: conceptual
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- comments, adding to documents
- documents [Office development in Visual Studio], adding comments
author: John-Hart
ms.author: johnhart
manager: jillfra
ms.workload:
- office
ms.openlocfilehash: 6dcb313989b8aa6615a186785297caef92631413
ms.sourcegitcommit: c0202a77d4dc562cdc55dc2e6223c062281d9749
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 01/24/2019
ms.locfileid: "54872078"
---
# <a name="how-to-programmatically-add-comments-to-text-in-documents"></a>Vorgehensweise: Programmgesteuertes Hinzufügen von Kommentaren zu Text in Dokumenten
  Die Comments-Eigenschaft der Document-Klasse hinzugefügt einen Textbereich in einem Microsoft Office Word-Dokument ein Kommentar.  
  
 [!INCLUDE[appliesto_wdalldocapp](../vsto/includes/appliesto-wdalldocapp-md.md)]  
  
 Mit dem folgenden Beispiel wird dem ersten Absatz im Dokument ein Kommentar hinzugefügt.  
  
## <a name="to-add-a-new-comment-to-text-in-a-document-level-customization"></a>So fügen Sie einen neuen Kommentar zu Text in einer Anpassung auf Dokumentebene hinzu  
  
1.  Rufen Sie die Methode <xref:Microsoft.Office.Interop.Word.Comments.Add%2A> der Eigenschaft <xref:Microsoft.Office.Tools.Word.Document.Comments%2A> auf, und geben Sie einen Bereich sowie den Kommentartext ein. Wenn Sie das folgende Codebeispiel verwenden möchten, führen Sie es aus der Klasse `ThisDocument` in Ihrem Projekt aus.  
  
     [!code-vb[Trin_VstcoreWordAutomation#118](../vsto/codesnippet/VisualBasic/Trin_VstcoreWordAutomationVB/ThisDocument.vb#118)]
     [!code-csharp[Trin_VstcoreWordAutomation#118](../vsto/codesnippet/CSharp/Trin_VstcoreWordAutomationCS/ThisDocument.cs#118)]  
  
## <a name="to-add-a-new-comment-to-text-in-a-vsto-add-in"></a>Um einen neuen Kommentar zu Text in einem VSTO-Add-in hinzufügen  
  
1.  Rufen Sie die Methode <xref:Microsoft.Office.Interop.Word.Comments.Add%2A> der Eigenschaft <xref:Microsoft.Office.Interop.Word._Document.Comments%2A> auf, und geben Sie einen Bereich sowie den Kommentartext ein.  
  
     Im folgenden Codebeispiel wird dem aktiven Dokument ein Kommentar hinzugefügt. Wenn Sie dieses Beispiel verwenden möchten, führen Sie es von der `ThisAddIn` -Klasse Ihres Projekts aus.  
  
     [!code-vb[Trin_VstcoreWordAutomationAddIn#118](../vsto/codesnippet/VisualBasic/Trin_VstcoreWordAutomationAddIn/ThisAddIn.vb#118)]
     [!code-csharp[Trin_VstcoreWordAutomationAddIn#118](../vsto/codesnippet/CSharp/Trin_VstcoreWordAutomationAddIn/ThisAddIn.cs#118)]  
  
## <a name="robust-programming"></a>Stabile Programmierung  
 Zum Ändern der Benutzerinitialen, die Word Kommentaren hinzufügt, verwenden Sie die Eigenschaft <xref:Microsoft.Office.Interop.Word._Application.UserInitials%2A> .  
  
## <a name="see-also"></a>Siehe auch  
 [Vorgehensweise: Programmgesteuertes Entfernen Sie aller Kommentare aus Dokumenten](../vsto/how-to-programmatically-remove-all-comments-from-documents.md)   
 [Dokumenthostelement](../vsto/document-host-item.md)  
