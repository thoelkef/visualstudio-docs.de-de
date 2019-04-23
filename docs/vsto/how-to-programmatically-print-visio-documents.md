---
title: 'Vorgehensweise: Programmgesteuertes Drucken von Visio-Dokumenten'
ms.date: 02/02/2017
ms.topic: conceptual
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- Visio [Office development in Visual Studio], printing Visio documents
- documents [Office development in Visual Studio], printing Visio documents
author: John-Hart
ms.author: johnhart
manager: jillfra
ms.workload:
- office
ms.openlocfilehash: 4bf492c866a43a0098fbcad5660a19c57fc90a3a
ms.sourcegitcommit: 1fc6ee928733e61a1f42782f832ead9f7946d00c
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/22/2019
ms.locfileid: "60071541"
---
# <a name="how-to-programmatically-print-visio-documents"></a>Vorgehensweise: Programmgesteuertes Drucken von Visio-Dokumenten
  Sie können ein vollständiges Microsoft Office Visio-Dokument oder nur eine bestimmte Seite drucken.

 Ausführliche Informationen zu den Druckmethoden finden Sie in der VBA-Referenzdokumentation für die [Microsoft.Office.Interop.Visio.Document.Print](/office/vba/api/Visio.Document.Print) -Methode und [Microsoft.Office.Interop.Visio.Page.Print](/office/vba/api/Visio.Page.Print) -Methode.

## <a name="print-a-visio-document"></a>Drucken von Visio-Dokumenten

### <a name="to-print-a-complete-document"></a>So drucken Sie ein vollständiges Dokument

- Rufen Sie die `Microsoft.Office.Interop.Visio.Document.Print` -Methode des `Microsoft.Office.Interop.Visio.Document` -Objekts auf, das Sie drucken möchten.

     Im folgenden Codebeispiel wird das aktive Dokument gedruckt. Wenn Sie dieses Beispiel verwenden möchten, führen Sie den Code von der `ThisAddIn` -Klasse im Projekt aus.

     [!code-csharp[Trin_VstcoreVisioAutomationAddIn#8](../vsto/codesnippet/CSharp/trin_vstcorevisioautomationaddin/ThisAddIn.cs#8)]
     [!code-vb[Trin_VstcoreVisioAutomationAddIn#8](../vsto/codesnippet/VisualBasic/trin_vstcorevisioautomationaddin/ThisAddIn.vb#8)]

## <a name="print-a-page-of-a-visio-document"></a>Drucken Sie eine Seite eines Visio-Dokuments

### <a name="to-print-a-page-of-a-document"></a>So drucken Sie eine Seite eines Dokuments

- Rufen Sie die `Microsoft.Office.Interop.Visio.Pages.Print` -Methode des `Microsoft.Office.Interop.Visio.Pages` -Objekts auf, das Sie drucken möchten.

     Im folgenden Codebeispiel wird die erste Seite des aktiven Dokuments gedruckt. Wenn Sie dieses Beispiel verwenden möchten, führen Sie den Code von der `ThisAddIn` -Klasse im Projekt aus.

     [!code-csharp[Trin_VstcoreVisioAutomationAddIn#9](../vsto/codesnippet/CSharp/trin_vstcorevisioautomationaddin/ThisAddIn.cs#9)]
     [!code-vb[Trin_VstcoreVisioAutomationAddIn#9](../vsto/codesnippet/VisualBasic/trin_vstcorevisioautomationaddin/ThisAddIn.vb#9)]

## <a name="see-also"></a>Siehe auch
- [Visio-Projektmappen](../vsto/visio-solutions.md)
- [Übersicht über das Visio-Objektmodell](../vsto/visio-object-model-overview.md)
- [Vorgehensweise: Programmgesteuertes Erstellen Sie Neuer Visio-Dokumente](../vsto/how-to-programmatically-create-new-visio-documents.md)
- [Vorgehensweise: Programmgesteuertes Öffnen von Visio-Dokumenten](../vsto/how-to-programmatically-open-visio-documents.md)
- [Vorgehensweise: Programmgesteuertes Schließen von Visio-Dokumenten](../vsto/how-to-programmatically-close-visio-documents.md)
- [Vorgehensweise: Programmgesteuertes Speichern von Visio-Dokumenten](../vsto/how-to-programmatically-save-visio-documents.md)
