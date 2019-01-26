---
title: 'Vorgehensweise: Programmgesteuertes Erweitern von Bereichen in Dokumenten'
ms.date: 02/02/2017
ms.topic: conceptual
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- ranges, extending
- documents [Office development in Visual Studio], extending ranges
author: John-Hart
ms.author: johnhart
manager: jillfra
ms.workload:
- office
ms.openlocfilehash: ed2df2d844383ab0cfc26d67104d03644e1db671
ms.sourcegitcommit: c0202a77d4dc562cdc55dc2e6223c062281d9749
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 01/24/2019
ms.locfileid: "54868861"
---
# <a name="how-to-programmatically-extend-ranges-in-documents"></a>Vorgehensweise: Programmgesteuertes Erweitern von Bereichen in Dokumenten
  Nachdem Sie ein <xref:Microsoft.Office.Interop.Word.Range> -Objekt in einem Microsoft Office Word-Dokument definiert haben, ändern Sie dessen Start- und Endpunkt mithilfe der Methoden <xref:Microsoft.Office.Interop.Word.Range.MoveStart%2A> und <xref:Microsoft.Office.Interop.Word.Range.MoveEnd%2A> . Die Methoden <xref:Microsoft.Office.Interop.Word.Range.MoveStart%2A> und <xref:Microsoft.Office.Interop.Word.Range.MoveEnd%2A> akzeptieren dieselben beiden Argumente *Unit* und *Count*. Die Methoden *Count* -Argument entspricht der Anzahl zu verschiebender Einheiten, und das *Unit* -Argument kann einer der folgenden <xref:Microsoft.Office.Interop.Word.WdUnits> -Werte sein:  
  
- <xref:Microsoft.Office.Interop.Word.WdUnits.wdCharacter>  
  
- <xref:Microsoft.Office.Interop.Word.WdUnits.wdWord>  
  
- <xref:Microsoft.Office.Interop.Word.WdUnits.wdSentence>  
  
- <xref:Microsoft.Office.Interop.Word.WdUnits.wdParagraph>  
  
- <xref:Microsoft.Office.Interop.Word.WdUnits.wdSection>  
  
- <xref:Microsoft.Office.Interop.Word.WdUnits.wdStory>  
  
- <xref:Microsoft.Office.Interop.Word.WdUnits.wdCell>  
  
- <xref:Microsoft.Office.Interop.Word.WdUnits.wdColumn>  
  
- <xref:Microsoft.Office.Interop.Word.WdUnits.wdRow>  
  
- <xref:Microsoft.Office.Interop.Word.WdUnits.wdTable>  
  
  [!INCLUDE[appliesto_wdalldocapp](../vsto/includes/appliesto-wdalldocapp-md.md)]  
  
  Im folgenden Beispiel wird ein aus sieben Zeichen bestehender Bereich definiert. Anschließend wird die Startposition des Bereichs von der ursprünglichen Startposition aus um sieben Zeichen verschoben. Da die Endposition des Bereichs ebenfalls sieben Zeichen von der Startposition entfernt war, umfasst der resultierende Bereich 0 Zeichen. Durch den Code wird die Endposition dann von der aktuellen Endposition um sieben Zeichen verschoben.  
  
## <a name="to-extend-a-range"></a>So erweitern Sie einen Bereich  
  
1.  Definieren Sie einen Bereich von Zeichen. Weitere Informationen finden Sie unter [Vorgehensweise: Programmgesteuertes definieren und Markieren von Bereichen in Dokumenten](../vsto/how-to-programmatically-define-and-select-ranges-in-documents.md).  
  
     Das folgende Codebeispiel kann in einer Anpassung auf Dokumentebene verwendet werden.  
  
     [!code-vb[Trin_VstcoreWordAutomation#39](../vsto/codesnippet/VisualBasic/Trin_VstcoreWordAutomationVB/ThisDocument.vb#39)]
     [!code-csharp[Trin_VstcoreWordAutomation#39](../vsto/codesnippet/CSharp/Trin_VstcoreWordAutomationCS/ThisDocument.cs#39)]  
  
     Das folgende Codebeispiel kann in einem VSTO-Add-In verwendet werden. In diesem Beispiel wird das aktive Dokument verwendet.  
  
     [!code-vb[Trin_VstcoreWordAutomationAddIn#39](../vsto/codesnippet/VisualBasic/Trin_VstcoreWordAutomationAddIn/ThisAddIn.vb#39)]
     [!code-csharp[Trin_VstcoreWordAutomationAddIn#39](../vsto/codesnippet/CSharp/Trin_VstcoreWordAutomationAddIn/ThisAddIn.cs#39)]  
  
2.  Verwenden Sie die <xref:Microsoft.Office.Interop.Word.Range.MoveStart%2A> -Methode des <xref:Microsoft.Office.Interop.Word.Range> -Objekts, um die Startposition des Bereichs zu verschieben.  
  
     [!code-vb[Trin_VstcoreWordAutomation#40](../vsto/codesnippet/VisualBasic/Trin_VstcoreWordAutomationVB/ThisDocument.vb#40)]
     [!code-csharp[Trin_VstcoreWordAutomation#40](../vsto/codesnippet/CSharp/Trin_VstcoreWordAutomationCS/ThisDocument.cs#40)]  
  
3.  Verwenden Sie die <xref:Microsoft.Office.Interop.Word.Range.MoveEnd%2A> -Methode des <xref:Microsoft.Office.Interop.Word.Range> -Objekts, um die Endposition des Bereichs zu verschieben.  
  
     [!code-vb[Trin_VstcoreWordAutomation#41](../vsto/codesnippet/VisualBasic/Trin_VstcoreWordAutomationVB/ThisDocument.vb#41)]
     [!code-csharp[Trin_VstcoreWordAutomation#41](../vsto/codesnippet/CSharp/Trin_VstcoreWordAutomationCS/ThisDocument.cs#41)]  
  
## <a name="document-level-customization-code"></a>Code der Anpassung auf Dokumentebene  
  
### <a name="to-extend-a-range-in-a-document-level-customization"></a>So erweitern Sie einen Bereich in einer Anpassung auf Dokumentebene  
  
1.  Das folgende Beispiel zeigt den vollständigen Code für eine Anpassung auf Dokumentebene. Wenn Sie diesen Code verwenden möchten, führen Sie ihn von der `ThisDocument` -Klasse im Projekt aus.  
  
     [!code-vb[Trin_VstcoreWordAutomation#38](../vsto/codesnippet/VisualBasic/Trin_VstcoreWordAutomationVB/ThisDocument.vb#38)]
     [!code-csharp[Trin_VstcoreWordAutomation#38](../vsto/codesnippet/CSharp/Trin_VstcoreWordAutomationCS/ThisDocument.cs#38)]  
  
## <a name="vsto-add-in-code"></a>VSTO-Add-In-Code  
  
### <a name="to-extend-a-range-in-an-application-level-vsto-add-in"></a>So erweitern Sie einen Bereich in einem VSTO-Add-In auf Anwendungsebene  
  
1.  Das folgende Beispiel zeigt den vollständigen Code für ein VSTO-Add-In. Wenn Sie diesen Code verwenden möchten, führen Sie ihn von der `ThisAddIn` -Klasse im Projekt aus.  
  
     [!code-vb[Trin_VstcoreWordAutomationAddIn#38](../vsto/codesnippet/VisualBasic/Trin_VstcoreWordAutomationAddIn/ThisAddIn.vb#38)]
     [!code-csharp[Trin_VstcoreWordAutomationAddIn#38](../vsto/codesnippet/CSharp/Trin_VstcoreWordAutomationAddIn/ThisAddIn.cs#38)]  
  
## <a name="see-also"></a>Siehe auch  
 [Vorgehensweise: Programmgesteuertes Zurücksetzen von Bereichen in Word-Dokumenten](../vsto/how-to-programmatically-reset-ranges-in-word-documents.md)   
 [Vorgehensweise: Programmgesteuertes Reduzieren von Bereichen oder Markierungen in Dokumenten](../vsto/how-to-programmatically-collapse-ranges-or-selections-in-documents.md)   
 [Vorgehensweise: Programmgesteuertes definieren und Markieren von Bereichen in Dokumenten](../vsto/how-to-programmatically-define-and-select-ranges-in-documents.md)   
 [Vorgehensweise: Programmgesteuertes Abrufen von Start- und Endzeit von Zeichen in Bereichen](../vsto/how-to-programmatically-retrieve-start-and-end-characters-in-ranges.md)   
 [Vorgehensweise: Programmgesteuertes ausschließen Absatzmarken beim Erstellen von Bereichen](../vsto/how-to-programmatically-exclude-paragraph-marks-when-creating-ranges.md)  
