---
title: 'Vorgehensweise: Programmgesteuertes Zurücksetzen von Bereichen in Word-Dokumenten'
ms.date: 02/02/2017
ms.topic: conceptual
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- documents [Office development in Visual Studio], resetting ranges
- ranges, resetting in documents
author: John-Hart
ms.author: johnhart
manager: jillfra
ms.workload:
- office
ms.openlocfilehash: 8643f7d10593ee2bcf51245d05edcd153db6b19d
ms.sourcegitcommit: d0425b6b7d4b99e17ca6ac0671282bc718f80910
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 02/21/2019
ms.locfileid: "56609812"
---
# <a name="how-to-programmatically-reset-ranges-in-word-documents"></a>Vorgehensweise: Programmgesteuertes Zurücksetzen von Bereichen in Word-Dokumenten
  Verwenden Sie die Methode <xref:Microsoft.Office.Interop.Word.Range.SetRange%2A> , um die Größe eines vorhandenen Bereichs in einem Microsoft Office Word-Dokument zu ändern.

 [!INCLUDE[appliesto_wdalldocapp](../vsto/includes/appliesto-wdalldocapp-md.md)]

## <a name="to-reset-an-existing-range"></a>So setzen Sie einen vorhandenen Bereich zurück

1.  Legen Sie einen Anfangsbereich fest, beginnend mit den ersten sieben Zeichen im Dokument.

     Das folgende Codebeispiel kann in einer Anpassung auf Dokumentebene verwendet werden.

     [!code-vb[Trin_VstcoreWordAutomation#43](../vsto/codesnippet/VisualBasic/Trin_VstcoreWordAutomationVB/ThisDocument.vb#43)]
     [!code-csharp[Trin_VstcoreWordAutomation#43](../vsto/codesnippet/CSharp/Trin_VstcoreWordAutomationCS/ThisDocument.cs#43)]

     Das folgende Codebeispiel kann in einem VSTO-Add-In verwendet werden. In diesem Code wird das aktive Dokument verwendet.

     [!code-vb[Trin_VstcoreWordAutomationAddIn#43](../vsto/codesnippet/VisualBasic/Trin_VstcoreWordAutomationAddIn/ThisAddIn.vb#43)]
     [!code-csharp[Trin_VstcoreWordAutomationAddIn#43](../vsto/codesnippet/CSharp/Trin_VstcoreWordAutomationAddIn/ThisAddIn.cs#43)]

2.  Verwenden Sie <xref:Microsoft.Office.Interop.Word.Range.SetRange%2A> , den Bereich mit dem zweiten Satz zu beginnen und nach dem fünften Satz zu beenden.

     [!code-vb[Trin_VstcoreWordAutomation#44](../vsto/codesnippet/VisualBasic/Trin_VstcoreWordAutomationVB/ThisDocument.vb#44)]
     [!code-csharp[Trin_VstcoreWordAutomation#44](../vsto/codesnippet/CSharp/Trin_VstcoreWordAutomationCS/ThisDocument.cs#44)]

## <a name="document-level-customization-example"></a>Beispiel für die Anpassung auf Dokumentebene

### <a name="to-reset-an-existing-range-in-a-document-level-customization"></a>So setzen Sie einen vorhandenen Bereich in einer Anpassung auf Dokumentebene zurück

1.  Das folgende Beispiel zeigt den vollständigen Code für eine Anpassung auf Dokumentebene. Wenn Sie diesen Code verwenden möchten, führen Sie ihn von der `ThisDocument`-Klasse im Projekt aus.

     [!code-vb[Trin_VstcoreWordAutomation#42](../vsto/codesnippet/VisualBasic/Trin_VstcoreWordAutomationVB/ThisDocument.vb#42)]
     [!code-csharp[Trin_VstcoreWordAutomation#42](../vsto/codesnippet/CSharp/Trin_VstcoreWordAutomationCS/ThisDocument.cs#42)]

## <a name="vsto-add-in-example"></a>Beispiel für VSTO-Add-in

### <a name="to-reset-an-existing-range-in-a-vsto-add-in"></a>Zurücksetzen ein vorhandenes Bereichs in einem VSTO-Add-in

1.  Das folgende Beispiel zeigt das vollständige Beispiel für ein VSTO-Add-in. Wenn Sie diesen Code verwenden möchten, führen Sie ihn von der `ThisAddIn`-Klasse im Projekt aus.

     [!code-vb[Trin_VstcoreWordAutomationAddIn#42](../vsto/codesnippet/VisualBasic/Trin_VstcoreWordAutomationAddIn/ThisAddIn.vb#42)]
     [!code-csharp[Trin_VstcoreWordAutomationAddIn#42](../vsto/codesnippet/CSharp/Trin_VstcoreWordAutomationAddIn/ThisAddIn.cs#42)]

## <a name="see-also"></a>Siehe auch
- [Vorgehensweise: Programmgesteuertes Erweitern von Bereichen in Dokumenten](../vsto/how-to-programmatically-extend-ranges-in-documents.md)
- [Vorgehensweise: Programmgesteuertes definieren und Markieren von Bereichen in Dokumenten](../vsto/how-to-programmatically-define-and-select-ranges-in-documents.md)
- [Vorgehensweise: Programmgesteuertes Abrufen von Start- und Endzeit von Zeichen in Bereichen](../vsto/how-to-programmatically-retrieve-start-and-end-characters-in-ranges.md)
- [Vorgehensweise: Programmgesteuertes Reduzieren von Bereichen oder Markierungen in Dokumenten](../vsto/how-to-programmatically-collapse-ranges-or-selections-in-documents.md)
