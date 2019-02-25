---
title: 'Vorgehensweise: Programmgesteuertes Schließen von Visio-Dokumenten'
ms.date: 02/02/2017
ms.topic: conceptual
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
ms.openlocfilehash: 9059e0f066cbd1dc6ced5f11f1139d7687afacf3
ms.sourcegitcommit: d0425b6b7d4b99e17ca6ac0671282bc718f80910
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 02/21/2019
ms.locfileid: "56597206"
---
# <a name="how-to-programmatically-close-visio-documents"></a>Vorgehensweise: Programmgesteuertes Schließen von Visio-Dokumenten
  Sie können das aktive Microsoft Office Visio-Dokument schließen, indem Sie die `Microsoft.Office.Interop.Visio.Document.Close`-Methode verwenden.

 Ausführliche Informationen zu dieser Methode finden Sie in der VBA-Referenzdokumentation für die [Microsoft.Office.Interop.Visio.Document.Close](/office/vba/api/Visio.Document.Close) -Methode.

## <a name="close-the-active-document"></a>Schließt das aktive Dokument

### <a name="to-close-the-active-document"></a>So schließen Sie das aktive Dokument

-   Rufen Sie die `Microsoft.Office.Interop.Visio.Document.Close`-Methode auf, um das aktive Dokument zu schließen.

     Um das folgende Codebeispiel verwenden möchten, führen Sie es der `ThisAddIn` Klasse in einem VSTO-Add-in-Projekt für Visio.

     [!code-csharp[Trin_VstcoreVisioAutomationAddIn#7](../vsto/codesnippet/CSharp/trin_vstcorevisioautomationaddin/ThisAddIn.cs#7)]
     [!code-vb[Trin_VstcoreVisioAutomationAddIn#7](../vsto/codesnippet/VisualBasic/trin_vstcorevisioautomationaddin/ThisAddIn.vb#7)]

## <a name="see-also"></a>Siehe auch
- [Visio-Projektmappen](../vsto/visio-solutions.md)
- [Übersicht über das Visio-Objektmodell](../vsto/visio-object-model-overview.md)
- [Vorgehensweise: Programmgesteuertes Erstellen Sie Neuer Visio-Dokumente](../vsto/how-to-programmatically-create-new-visio-documents.md)
- [Vorgehensweise: Programmgesteuertes Öffnen von Visio-Dokumenten](../vsto/how-to-programmatically-open-visio-documents.md)
- [Vorgehensweise: Programmgesteuertes Speichern von Visio-Dokumenten](../vsto/how-to-programmatically-save-visio-documents.md)
- [Vorgehensweise: Programmgesteuertes Drucken von Visio-Dokumenten](../vsto/how-to-programmatically-print-visio-documents.md)
