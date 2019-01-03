---
title: 'Vorgehensweise: Programmgesteuertes definieren und Markieren von Bereichen in Dokumenten'
ms.date: 02/02/2017
ms.topic: conceptual
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- documents [Office development in Visual Studio], selecting sentences
- documents [Office development in Visual Studio], ranges
- sentences, selecting in documents
- ranges, selecting in documents
- ranges, defining in documents
author: TerryGLee
ms.author: tglee
manager: douge
ms.workload:
- office
ms.openlocfilehash: b6922613c7a1493d5b40b807166281ae11eb04d6
ms.sourcegitcommit: 37fb7075b0a65d2add3b137a5230767aa3266c74
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 01/02/2019
ms.locfileid: "53835499"
---
# <a name="how-to-programmatically-define-and-select-ranges-in-documents"></a>Vorgehensweise: Programmgesteuertes definieren und Markieren von Bereichen in Dokumenten
  Sie können einen Bereich in einem Microsoft Office Word-Dokument mithilfe eines <xref:Microsoft.Office.Interop.Word.Range>-Objekts definieren. Sie können das gesamte Dokument in eine Reihe von Möglichkeiten, z. B. auswählen, mit der <xref:Microsoft.Office.Interop.Word.Range.Select%2A> -Methode der der <xref:Microsoft.Office.Interop.Word.Range> -Objekts oder mithilfe der Content-Eigenschaft der <xref:Microsoft.Office.Tools.Word.Document> -Klasse (in einer Anpassung auf Dokumentebene) oder die <xref:Microsoft.Office.Interop.Word.Document> Klasse (in einer VSTO-Add-in).  
  
 [!INCLUDE[appliesto_wdalldocapp](../vsto/includes/appliesto-wdalldocapp-md.md)]  
  
## <a name="define-a-range"></a>Definieren Sie einen Bereich  
 Das folgende Beispiel veranschaulicht das Erstellen eines neuen <xref:Microsoft.Office.Interop.Word.Range>-Objekts, das die ersten sieben Zeichen im aktiven Dokument, einschließlich der nicht druckbaren Zeichen, enthält. Anschließend wird der Text innerhalb des Bereichs ausgewählt.  
  
### <a name="to-define-a-range-in-a-document-level-customization"></a>So definieren Sie einen Bereich in einer Anpassung auf Dokumentebene  
  
1.  Fügen Sie dem Dokument den Bereich hinzu, indem Sie ein Start- und ein Endzeichen an die <xref:Microsoft.Office.Tools.Word.Document.Range%2A>-Methode der <xref:Microsoft.Office.Tools.Word.Document>-Klasse übergeben. Wenn Sie dieses Codebeispiel verwenden möchten, führen Sie es von der `ThisDocument` -Klasse im Projekt aus.  
  
     [!code-vb[Trin_VstcoreWordAutomation#18](../vsto/codesnippet/VisualBasic/Trin_VstcoreWordAutomationVB/ThisDocument.vb#18)]
     [!code-csharp[Trin_VstcoreWordAutomation#18](../vsto/codesnippet/CSharp/Trin_VstcoreWordAutomationCS/ThisDocument.cs#18)]  
  
### <a name="to-define-a-range-by-using-a-vsto-add-in"></a>So definieren Sie einen Bereich mithilfe eines VSTO-Add-Ins  
  
1.  Fügen Sie dem Dokument den Bereich hinzu, indem Sie ein Start- und ein Endzeichen an die <xref:Microsoft.Office.Interop.Word._Document.Range%2A>-Methode der <xref:Microsoft.Office.Interop.Word.Document>-Klasse übergeben. Im folgenden Codebeispiel wird dem aktiven Dokument ein Bereich hinzugefügt. Wenn Sie dieses Codebeispiel verwenden möchten, führen Sie es von der `ThisAddIn` -Klasse im Projekt aus.  
  
     [!code-vb[Trin_VstcoreWordAutomationAddIn#18](../vsto/codesnippet/VisualBasic/Trin_VstcoreWordAutomationAddIn/ThisAddIn.vb#18)]
     [!code-csharp[Trin_VstcoreWordAutomationAddIn#18](../vsto/codesnippet/CSharp/Trin_VstcoreWordAutomationAddIn/ThisAddIn.cs#18)]  
  
## <a name="select-a-range-in-a-document-level-customization"></a>Wählen Sie einen Bereich in einer Anpassung auf Dokumentebene  
 Die folgenden Beispiele zeigen, wie Sie das gesamte Dokument mithilfe der <xref:Microsoft.Office.Interop.Word.Range.Select%2A>-Methode eines <xref:Microsoft.Office.Interop.Word.Range>-Objekts oder mithilfe der <xref:Microsoft.Office.Tools.Word.Document.Content%2A>-Eigenschaft der <xref:Microsoft.Office.Tools.Word.Document>-Klasse auswählen.  
  
### <a name="to-select-the-entire-document-as-a-range-by-using-the-select-method"></a>So wählen Sie das gesamte Dokument als Bereich mithilfe der Select-Methode aus  
  
1.  Verwenden Sie die <xref:Microsoft.Office.Interop.Word.Range.Select%2A>-Methode eines <xref:Microsoft.Office.Interop.Word.Range>, der das gesamte Dokument enthält. Wenn Sie das folgende Codebeispiel verwenden möchten, führen Sie es aus der Klasse `ThisDocument` in Ihrem Projekt aus.  
  
     [!code-vb[Trin_VstcoreWordAutomation#19](../vsto/codesnippet/VisualBasic/Trin_VstcoreWordAutomationVB/ThisDocument.vb#19)]
     [!code-csharp[Trin_VstcoreWordAutomation#19](../vsto/codesnippet/CSharp/Trin_VstcoreWordAutomationCS/ThisDocument.cs#19)]  
  
### <a name="to-select-the-entire-document-as-a-range-by-using-the-content-property"></a>So wählen Sie das gesamte Dokument als Bereich mithilfe der Content-Eigenschaft aus  
  
1. Verwenden Sie die <xref:Microsoft.Office.Tools.Word.Document.Content%2A>-Eigenschaft, um einen Bereich zu definieren, der das gesamte Dokument umfasst.  
  
    [!code-vb[Trin_VstcoreWordAutomation#20](../vsto/codesnippet/VisualBasic/Trin_VstcoreWordAutomationVB/ThisDocument.vb#20)]
    [!code-csharp[Trin_VstcoreWordAutomation#20](../vsto/codesnippet/CSharp/Trin_VstcoreWordAutomationCS/ThisDocument.cs#20)]  
  
   Sie können auch Methoden und Eigenschaften anderer Objekte verwenden, um einen Bereich zu definieren.  
  
### <a name="to-select-a-sentence-in-the-active-document"></a>So wählen Sie einen Satz im aktiven Dokument aus  
  
1. Legen Sie den Bereich mithilfe der <xref:Microsoft.Office.Interop.Word.Sentences>-Auflistung fest. Verwenden Sie den Index des Satzes, den Sie auswählen möchten.  
  
    [!code-vb[Trin_VstcoreWordAutomation#21](../vsto/codesnippet/VisualBasic/Trin_VstcoreWordAutomationVB/ThisDocument.vb#21)]
    [!code-csharp[Trin_VstcoreWordAutomation#21](../vsto/codesnippet/CSharp/Trin_VstcoreWordAutomationCS/ThisDocument.cs#21)]  
  
   Eine andere Möglichkeit zum Auswählen eines Satzes besteht darin, den Start- und Endwert für den Bereich manuell festzulegen.  
  
### <a name="to-select-a-sentence-by-manually-setting-the-start-and-end-values"></a>So wählen Sie einen Satz durch manuelles Festlegen des Start- und Endwerts aus  
  
1.  Erstellen Sie eine Bereichsvariable.  
  
     [!code-vb[Trin_VstcoreWordAutomation#23](../vsto/codesnippet/VisualBasic/Trin_VstcoreWordAutomationVB/ThisDocument.vb#23)]
     [!code-csharp[Trin_VstcoreWordAutomation#23](../vsto/codesnippet/CSharp/Trin_VstcoreWordAutomationCS/ThisDocument.cs#23)]  
  
2.  Überprüfen, ob mindestens zwei Sätze im Dokument stehen. Legen Sie die *starten* und *End* Argumente des Bereichs fest, und wählen Sie dann den Bereich.  
  
     [!code-vb[Trin_VstcoreWordAutomation#24](../vsto/codesnippet/VisualBasic/Trin_VstcoreWordAutomationVB/ThisDocument.vb#24)]
     [!code-csharp[Trin_VstcoreWordAutomation#24](../vsto/codesnippet/CSharp/Trin_VstcoreWordAutomationCS/ThisDocument.cs#24)]  
  
## <a name="select-a-range-by-using-a-vsto-add-in"></a>Wählen Sie einen Bereich mithilfe eines VSTO-Add-Ins  
 Die folgenden Beispiele zeigen, wie Sie das gesamte Dokument mithilfe der <xref:Microsoft.Office.Interop.Word.Range.Select%2A>-Methode eines <xref:Microsoft.Office.Interop.Word.Range>-Objekts oder mithilfe der <xref:Microsoft.Office.Interop.Word._Document.Content%2A>-Eigenschaft der <xref:Microsoft.Office.Interop.Word.Document>-Klasse auswählen.  
  
### <a name="to-select-the-entire-document-as-a-range-by-using-the-select-method"></a>So wählen Sie das gesamte Dokument als Bereich mithilfe der Select-Methode aus  
  
1.  Verwenden Sie die <xref:Microsoft.Office.Interop.Word.Range.Select%2A>-Methode eines <xref:Microsoft.Office.Interop.Word.Range>, der das gesamte Dokument enthält. Im folgenden Codebeispiel wird der Inhalt des aktiven Dokuments ausgewählt. Wenn Sie dieses Codebeispiel verwenden möchten, führen Sie es von der `ThisAddIn` -Klasse im Projekt aus.  
  
     [!code-vb[Trin_VstcoreWordAutomationAddIn#19](../vsto/codesnippet/VisualBasic/Trin_VstcoreWordAutomationAddIn/ThisAddIn.vb#19)]
     [!code-csharp[Trin_VstcoreWordAutomationAddIn#19](../vsto/codesnippet/CSharp/Trin_VstcoreWordAutomationAddIn/ThisAddIn.cs#19)]  
  
### <a name="to-select-the-entire-document-as-a-range-by-using-the-content-property"></a>So wählen Sie das gesamte Dokument als Bereich mithilfe der Content-Eigenschaft aus  
  
1. Verwenden Sie die <xref:Microsoft.Office.Interop.Word._Document.Content%2A>-Eigenschaft, um einen Bereich zu definieren, der das gesamte Dokument umfasst.  
  
    [!code-vb[Trin_VstcoreWordAutomationAddIn#20](../vsto/codesnippet/VisualBasic/Trin_VstcoreWordAutomationAddIn/ThisAddIn.vb#20)]
    [!code-csharp[Trin_VstcoreWordAutomationAddIn#20](../vsto/codesnippet/CSharp/Trin_VstcoreWordAutomationAddIn/ThisAddIn.cs#20)]  
  
   Sie können auch Methoden und Eigenschaften anderer Objekte verwenden, um einen Bereich zu definieren.  
  
### <a name="to-select-a-sentence-in-the-active-document"></a>So wählen Sie einen Satz im aktiven Dokument aus  
  
1. Legen Sie den Bereich mithilfe der <xref:Microsoft.Office.Interop.Word.Sentences>-Auflistung fest. Verwenden Sie den Index des Satzes, den Sie auswählen möchten.  
  
    [!code-vb[Trin_VstcoreWordAutomationAddIn#21](../vsto/codesnippet/VisualBasic/Trin_VstcoreWordAutomationAddIn/ThisAddIn.vb#21)]
    [!code-csharp[Trin_VstcoreWordAutomationAddIn#21](../vsto/codesnippet/CSharp/Trin_VstcoreWordAutomationAddIn/ThisAddIn.cs#21)]  
  
   Eine andere Möglichkeit zum Auswählen eines Satzes besteht darin, den Start- und Endwert für den Bereich manuell festzulegen.  
  
### <a name="to-select-a-sentence-by-manually-setting-the-start-and-end-values"></a>So wählen Sie einen Satz durch manuelles Festlegen des Start- und Endwerts aus  
  
1.  Erstellen Sie eine Bereichsvariable.  
  
     [!code-vb[Trin_VstcoreWordAutomationAddIn#23](../vsto/codesnippet/VisualBasic/Trin_VstcoreWordAutomationAddIn/ThisAddIn.vb#23)]
     [!code-csharp[Trin_VstcoreWordAutomationAddIn#23](../vsto/codesnippet/CSharp/Trin_VstcoreWordAutomationAddIn/ThisAddIn.cs#23)]  
  
2.  Überprüfen, ob mindestens zwei Sätze im Dokument stehen. Legen Sie die *starten* und *End* Argumente des Bereichs fest, und wählen Sie dann den Bereich.  
  
     [!code-vb[Trin_VstcoreWordAutomationAddIn#24](../vsto/codesnippet/VisualBasic/Trin_VstcoreWordAutomationAddIn/ThisAddIn.vb#24)]
     [!code-csharp[Trin_VstcoreWordAutomationAddIn#24](../vsto/codesnippet/CSharp/Trin_VstcoreWordAutomationAddIn/ThisAddIn.cs#24)]  
  
## <a name="see-also"></a>Siehe auch  
 [Übersicht über das Word-Objektmodell](../vsto/word-object-model-overview.md)   
 [Vorgehensweise: Programmgesteuertes Erweitern von Bereichen in Dokumenten](../vsto/how-to-programmatically-extend-ranges-in-documents.md)   
 [Vorgehensweise: Programmgesteuertes Abrufen von Start- und Endzeit von Zeichen in Bereichen](../vsto/how-to-programmatically-retrieve-start-and-end-characters-in-ranges.md)   
 [Vorgehensweise: Programmgesteuertes Erweitern von Bereichen in Dokumenten](../vsto/how-to-programmatically-extend-ranges-in-documents.md)   
 [Vorgehensweise: Programmgesteuertes Zurücksetzen von Bereichen in Word-Dokumenten](../vsto/how-to-programmatically-reset-ranges-in-word-documents.md)   
 [Vorgehensweise: Programmgesteuertes Reduzieren von Bereichen oder Markierungen in Dokumenten](../vsto/how-to-programmatically-collapse-ranges-or-selections-in-documents.md)   
 [Vorgehensweise: Programmgesteuertes ausschließen Absatzmarken beim Erstellen von Bereichen](../vsto/how-to-programmatically-exclude-paragraph-marks-when-creating-ranges.md)  
