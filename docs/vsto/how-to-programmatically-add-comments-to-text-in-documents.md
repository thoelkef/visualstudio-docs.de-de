---
title: "Vorgehensweise: Programmgesteuertes Hinzufügen von Kommentaren zu Text in Dokumenten | Microsoft Docs"
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
- comments, adding to documents
- documents [Office development in Visual Studio], adding comments
author: TerryGLee
ms.author: tglee
manager: ghogen
ms.workload: office
ms.openlocfilehash: 2702d8aed4dce16a2dde1c42b2b1410ebded14e3
ms.sourcegitcommit: f9fbf1f55f9ac14e4e5c6ae58c30dc1800ca6cda
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 01/10/2018
---
# <a name="how-to-programmatically-add-comments-to-text-in-documents"></a>Gewusst wie: Programmgesteuertes Hinzufügen von Kommentaren zu Text in Dokumenten
  Die Eigenschaft "Kommentare" der Dokumentklasse hinzugefügt einen Textbereich in einem Microsoft Office Word-Dokument ein Kommentar.  
  
 [!INCLUDE[appliesto_wdalldocapp](../vsto/includes/appliesto-wdalldocapp-md.md)]  
  
 Mit dem folgenden Beispiel wird dem ersten Absatz im Dokument ein Kommentar hinzugefügt.  
  
### <a name="to-add-a-new-comment-to-text-in-a-document-level-customization"></a>So fügen Sie einen neuen Kommentar zu Text in einer Anpassung auf Dokumentebene hinzu  
  
1.  Rufen Sie die Methode <xref:Microsoft.Office.Interop.Word.Comments.Add%2A> der Eigenschaft <xref:Microsoft.Office.Tools.Word.Document.Comments%2A> auf, und geben Sie einen Bereich sowie den Kommentartext ein. Wenn Sie das folgende Codebeispiel verwenden möchten, führen Sie es aus der Klasse `ThisDocument` in Ihrem Projekt aus.  
  
     [!code-vb[Trin_VstcoreWordAutomation#118](../vsto/codesnippet/VisualBasic/Trin_VstcoreWordAutomationVB/ThisDocument.vb#118)]
     [!code-csharp[Trin_VstcoreWordAutomation#118](../vsto/codesnippet/CSharp/Trin_VstcoreWordAutomationCS/ThisDocument.cs#118)]  
  
### <a name="to-add-a-new-comment-to-text-in-an-vsto-add-in"></a>So fügen Sie einen neuen Kommentar zu Text in einem VSTO-Add-In hinzu  
  
1.  Rufen Sie die Methode <xref:Microsoft.Office.Interop.Word.Comments.Add%2A> der Eigenschaft <xref:Microsoft.Office.Interop.Word._Document.Comments%2A> auf, und geben Sie einen Bereich sowie den Kommentartext ein.  
  
     Im folgenden Codebeispiel wird dem aktiven Dokument ein Kommentar hinzugefügt. Wenn Sie dieses Beispiel verwenden möchten, führen Sie es von der `ThisAddIn` -Klasse Ihres Projekts aus.  
  
     [!code-vb[Trin_VstcoreWordAutomationAddIn#118](../vsto/codesnippet/VisualBasic/Trin_VstcoreWordAutomationAddIn/ThisAddIn.vb#118)]
     [!code-csharp[Trin_VstcoreWordAutomationAddIn#118](../vsto/codesnippet/CSharp/Trin_VstcoreWordAutomationAddIn/ThisAddIn.cs#118)]  
  
## <a name="robust-programming"></a>Stabile Programmierung  
 Zum Ändern der Benutzerinitialen, die Word Kommentaren hinzufügt, verwenden Sie die Eigenschaft <xref:Microsoft.Office.Interop.Word._Application.UserInitials%2A> .  
  
## <a name="see-also"></a>Siehe auch  
 [Vorgehensweise: Programmgesteuertes Entfernen aller Kommentare aus Dokumenten](../vsto/how-to-programmatically-remove-all-comments-from-documents.md)   
 [Dokumenthostelement](../vsto/document-host-item.md)  
  
  