---
title: 'Gewusst wie: Programm gesteuertes Hinzufügen von Shapes zu einem Visio-Dokument'
ms.date: 02/02/2017
ms.topic: how-to
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- Visio [Office development in Visual Studio], adding Visio shapes
- shapes [Office development in Visual Studio], adding Visio shapes
author: John-Hart
ms.author: johnhart
manager: jillfra
ms.workload:
- office
ms.openlocfilehash: adde20bff07b54a7fb5777bd9e03a995b4fbd7df
ms.sourcegitcommit: b885f26e015d03eafe7c885040644a52bb071fae
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 06/30/2020
ms.locfileid: "85538059"
---
# <a name="how-to-programmatically-add-shapes-to-a-visio-document"></a>Gewusst wie: Programm gesteuertes Hinzufügen von Shapes zu einem Visio-Dokument
  Sie können einem Microsoft Office Visio-Dokument Shapes hinzufügen, indem Sie die Master-Shapes aus einer Schablone abrufen und auf der aktiven Seite ablegen.

 Weitere Informationen finden Sie in der VBA-Referenzdokumentation für die [Microsoft.Office.Interop.Visio.Documents.Add](/office/vba/api/Visio.Documents.Add) -Methode, [Microsoft.Office.Interop.Visio.Application.ActivePage](/office/vba/api/Visio.Application.ActivePage) -Eigenschaft und [Microsoft.Office.Interop.Visio.Page.Drop](/office/vba/api/Visio.Page.Drop) -Methode.

## <a name="add-shapes-to-a-visio-document"></a>Hinzufügen von Shapes zu einem Visio-Dokument

### <a name="to-add-shapes-to-a-visio-document"></a>So fügen Sie einem Visio-Dokument Shapes hinzu

- Rufen Sie bei einem aktiven Dokument die Master-Shapes aus der Documents.Masters-Auflistung ab, und legen Sie sie im aktiven Dokument ab. Sie können einen Master mit dem Index oder Masternamen abrufen.

     Im folgenden Codebeispiel wird ein leeres Visio-Dokument erstellt und anschließend geöffnet, während die Schablone **Standard-Shapes** angedockt ist. Anschließend werden vom Code verschiedene Shapes abgerufen und auf der aktiven Seite abgelegt.

     [!code-csharp[Trin_VstcoreVisioAutomationAddIn#13](../vsto/codesnippet/CSharp/trin_vstcorevisioautomationaddin/ThisAddIn.cs#13)]
     [!code-vb[Trin_VstcoreVisioAutomationAddIn#13](../vsto/codesnippet/VisualBasic/trin_vstcorevisioautomationaddin/ThisAddIn.vb#13)]

## <a name="see-also"></a>Siehe auch
- [Visio-Lösungen](../vsto/visio-solutions.md)
- [Übersicht über das Visio-Objektmodell](../vsto/visio-object-model-overview.md)
- [Arbeiten mit Visio-Shapes](../vsto/working-with-visio-shapes.md)
- [Gewusst wie: Programm gesteuertes kopieren und Einfügen von Shapes in ein Visio-Dokument](../vsto/how-to-programmatically-copy-and-paste-shapes-in-a-visio-document.md)
