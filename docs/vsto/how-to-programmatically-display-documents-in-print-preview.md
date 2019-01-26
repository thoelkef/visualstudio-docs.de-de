---
title: 'Vorgehensweise: Programmgesteuertes Anzeigen von Dokumenten in der Seitenansicht'
ms.date: 02/02/2017
ms.topic: conceptual
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- Word [Office development in Visual Studio], displaying documents in print preview
- documents [Office development in Visual Studio], displaying in print preview
author: John-Hart
ms.author: johnhart
manager: jillfra
ms.workload:
- office
ms.openlocfilehash: 0907db7e616f0b342f2810c32af8e06d6bc730f7
ms.sourcegitcommit: c0202a77d4dc562cdc55dc2e6223c062281d9749
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 01/24/2019
ms.locfileid: "54873937"
---
# <a name="how-to-programmatically-display-documents-in-print-preview"></a>Vorgehensweise: Programmgesteuertes Anzeigen von Dokumenten in der Seitenansicht
  Wenn Ihre Projektmappe einen Bericht generiert, können Sie dem Benutzer den Bericht im Seitenansichtsmodus anzeigen.  
  
 [!INCLUDE[appliesto_wdalldocapp](../vsto/includes/appliesto-wdalldocapp-md.md)]  
  
## <a name="procedures-for-document-level-customizations"></a>Verfahren für Anpassungen auf Dokumentebene  
  
### <a name="to-display-a-document-in-print-preview-by-calling-the-printpreview-method"></a>So zeigen Sie ein Dokument durch Aufrufen der „PrintPreview“-Methode in der Seitenansicht an  
  
1.  Rufen Sie die <xref:Microsoft.Office.Tools.Word.Document.PrintPreview%2A> -Methode der <xref:Microsoft.Office.Tools.Word.Document> -Klasse auf. Wenn Sie dieses Codebeispiel verwenden möchten, führen Sie es von der `ThisDocument` -Klasse im Projekt aus.  
  
     [!code-vb[Trin_VstcoreWordAutomation#13](../vsto/codesnippet/VisualBasic/Trin_VstcoreWordAutomationVB/ThisDocument.vb#13)]
     [!code-csharp[Trin_VstcoreWordAutomation#13](../vsto/codesnippet/CSharp/Trin_VstcoreWordAutomationCS/ThisDocument.cs#13)]  
  
### <a name="to-display-a-document-in-print-preview-by-setting-the-printpreview-property"></a>So zeigen Sie ein Dokument durch Festlegen der „PrintPreview“-Eigenschaft in der Seitenansicht an  
  
1.  Legen Sie die <xref:Microsoft.Office.Interop.Word._Application.PrintPreview%2A> -Eigenschaft des <xref:Microsoft.Office.Interop.Word.Application> -Objekts auf **true**fest.  
  
     [!code-vb[Trin_VstcoreWordAutomation#14](../vsto/codesnippet/VisualBasic/Trin_VstcoreWordAutomationVB/ThisDocument.vb#14)]
     [!code-csharp[Trin_VstcoreWordAutomation#14](../vsto/codesnippet/CSharp/Trin_VstcoreWordAutomationCS/ThisDocument.cs#14)]  
  
## <a name="procedures-for-vsto-add-ins"></a>Verfahren für VSTO-Add-Ins  
  
### <a name="to-display-a-document-in-print-preview-by-calling-the-printpreview-method"></a>So zeigen Sie ein Dokument durch Aufrufen der „PrintPreview“-Methode in der Seitenansicht an  
  
1.  Rufen Sie die <xref:Microsoft.Office.Interop.Word._Document.PrintPreview%2A> -Methode des <xref:Microsoft.Office.Interop.Word.Document> -Objekts auf, für das Sie eine Vorschau anzeigen möchten. Wenn Sie dieses Codebeispiel verwenden möchten, führen Sie es von der `ThisAddIn` -Klasse im Projekt aus.  
  
     [!code-vb[Trin_VstcoreWordAutomationAddIn#13](../vsto/codesnippet/VisualBasic/Trin_VstcoreWordAutomationAddIn/ThisAddIn.vb#13)]
     [!code-csharp[Trin_VstcoreWordAutomationAddIn#13](../vsto/codesnippet/CSharp/Trin_VstcoreWordAutomationAddIn/ThisAddIn.cs#13)]  
  
### <a name="to-display-a-document-in-print-preview-by-setting-the-printpreview-property"></a>So zeigen Sie ein Dokument durch Festlegen der „PrintPreview“-Eigenschaft in der Seitenansicht an  
  
1.  Legen Sie die <xref:Microsoft.Office.Interop.Word._Application.PrintPreview%2A> -Eigenschaft des <xref:Microsoft.Office.Interop.Word.Application> -Objekts auf **true**fest.  
  
     [!code-vb[Trin_VstcoreWordAutomation#14](../vsto/codesnippet/VisualBasic/Trin_VstcoreWordAutomationVB/ThisDocument.vb#14)]
     [!code-csharp[Trin_VstcoreWordAutomation#14](../vsto/codesnippet/CSharp/Trin_VstcoreWordAutomationCS/ThisDocument.cs#14)]  
  
## <a name="see-also"></a>Siehe auch  
 [Vorgehensweise: Programmgesteuertes Drucken von Dokumenten](../vsto/how-to-programmatically-print-documents.md)   
 [Vorgehensweise: Programmgesteuertes Öffnen vorhandener Dokumente](../vsto/how-to-programmatically-open-existing-documents.md)   
 [Vorgehensweise: Programmgesteuertes Erstellen neuer Dokumente](../vsto/how-to-programmatically-create-new-documents.md)  
