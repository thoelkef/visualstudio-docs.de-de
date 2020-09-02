---
title: 'Gewusst wie: Programm gesteuertes schließen von Visio-Dokumenten'
ms.date: 02/02/2017
ms.topic: how-to
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- documents [Office development in Visual Studio], closing Visio documents
- Visio [Office development in Visual Studio], closing Visio documents
author: John-Hart
ms.author: johnhart
manager: jillfra
ms.workload:
- office
ms.openlocfilehash: 478905a8ba4dacd2102c4b19fe091016a7409773
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 09/02/2020
ms.locfileid: "85547484"
---
# <a name="how-to-programmatically-close-visio-documents"></a>Gewusst wie: Programm gesteuertes schließen von Visio-Dokumenten
  Sie können das aktive Microsoft Office Visio-Dokument schließen, indem Sie die `Microsoft.Office.Interop.Visio.Document.Close`-Methode verwenden.

 Ausführliche Informationen zu dieser Methode finden Sie in der VBA-Referenzdokumentation für die [Microsoft.Office.Interop.Visio.Document.Close](/office/vba/api/Visio.Document.Close) -Methode.

## <a name="close-the-active-document"></a>Schließt das aktive Dokument

### <a name="to-close-the-active-document"></a>So schließen Sie das aktive Dokument

- Rufen Sie die `Microsoft.Office.Interop.Visio.Document.Close`-Methode auf, um das aktive Dokument zu schließen.

     Um das folgende Codebeispiel zu verwenden, führen Sie es in der- `ThisAddIn` Klasse in einem VSTO-Add-in-Projekt für Visio aus.

     [!code-csharp[Trin_VstcoreVisioAutomationAddIn#7](../vsto/codesnippet/CSharp/trin_vstcorevisioautomationaddin/ThisAddIn.cs#7)]
     [!code-vb[Trin_VstcoreVisioAutomationAddIn#7](../vsto/codesnippet/VisualBasic/trin_vstcorevisioautomationaddin/ThisAddIn.vb#7)]

## <a name="see-also"></a>Weitere Informationen
- [Visio-Lösungen](../vsto/visio-solutions.md)
- [Übersicht über das Visio-Objektmodell](../vsto/visio-object-model-overview.md)
- [Gewusst wie: Programm gesteuertes Erstellen neuer Visio-Dokumente](../vsto/how-to-programmatically-create-new-visio-documents.md)
- [Gewusst wie: Programm gesteuertes Öffnen von Visio-Dokumenten](../vsto/how-to-programmatically-open-visio-documents.md)
- [Gewusst wie: Programm gesteuertes Speichern von Visio-Dokumenten](../vsto/how-to-programmatically-save-visio-documents.md)
- [Gewusst wie: Programm gesteuertes Drucken von Visio-Dokumenten](../vsto/how-to-programmatically-print-visio-documents.md)
