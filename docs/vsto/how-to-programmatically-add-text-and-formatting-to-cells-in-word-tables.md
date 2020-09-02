---
title: Programm gesteuertes Hinzufügen von Text & Formatierung zu Word-Tabellenzellen
ms.date: 02/02/2017
ms.topic: how-to
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- cells, adding text and formatting
- text [Office development in Visual Studio], adding to Word tables
- formatting [Office development in Visual Studio]
- tables [Office development in Visual Studio], adding text and formatting
author: John-Hart
ms.author: johnhart
manager: jillfra
ms.workload:
- office
ms.openlocfilehash: acd43c82c6dae32ef6595b2f63c06fe61f3c6168
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 09/02/2020
ms.locfileid: "85538046"
---
# <a name="how-to-programmatically-add-text-and-formatting-to-cells-in-word-tables"></a>Gewusst wie: Programm gesteuertes Hinzufügen von Text und Formatierung zu Zellen in Word-Tabellen
  Jede Tabelle besteht aus einer Auflistung von Zellen. Jedes einzelne <xref:Microsoft.Office.Interop.Word.Cell>-Objekt stellt eine Zelle in der Tabelle dar. Auf die einzelnen Zellen wird anhand ihrer Position in der Tabelle verwiesen. In diesem Beispiel wird auf die Zelle in der ersten Zeile und der ersten Spalte der Tabelle verwiesen, der Zelle Text hinzugefügt und Formatierung angewendet.

 [!INCLUDE[appliesto_wdalldocapp](../vsto/includes/appliesto-wdalldocapp-md.md)]

## <a name="to-add-text-and-formatting-to-cells"></a>So fügen Sie Zellen Text und Formatierung hinzu

1. Verweisen Sie anhand der Position in der Tabelle auf die Zelle, fügen Sie der Zelle Text hinzu, und wenden Sie die Formatierung an.

     Das folgende Codebeispiel kann in einer Anpassung auf Dokumentebene verwendet werden. Wenn Sie dieses Beispiel verwenden möchten, führen Sie es von der `ThisDocument` -Klasse Ihres Projekts aus.

     [!code-vb[Trin_VstcoreWordAutomation#97](../vsto/codesnippet/VisualBasic/Trin_VstcoreWordAutomationVB/ThisDocument.vb#97)]
     [!code-csharp[Trin_VstcoreWordAutomation#97](../vsto/codesnippet/CSharp/Trin_VstcoreWordAutomationCS/ThisDocument.cs#97)]

     Das folgende Codebeispiel kann in einem VSTO-Add-In verwendet werden. In diesem Beispiel wird das aktive Dokument verwendet. Wenn Sie dieses Beispiel verwenden möchten, führen Sie es von der `ThisAddIn` -Klasse Ihres Projekts aus.

     [!code-vb[Trin_VstcoreWordAutomationAddIn#97](../vsto/codesnippet/VisualBasic/Trin_VstcoreWordAutomationAddIn/ThisAddIn.vb#97)]
     [!code-csharp[Trin_VstcoreWordAutomationAddIn#97](../vsto/codesnippet/CSharp/Trin_VstcoreWordAutomationAddIn/ThisAddIn.cs#97)]

## <a name="see-also"></a>Weitere Informationen
- [Gewusst wie: Programm gesteuertes Erstellen von Word-Tabellen](../vsto/how-to-programmatically-create-word-tables.md)
- [Gewusst wie: Programm gesteuertes Hinzufügen von Zeilen und Spalten zu Word-Tabellen](../vsto/how-to-programmatically-add-rows-and-columns-to-word-tables.md)
- [Gewusst wie: Programm gesteuertes Auffüllen von Word-Tabellen mit Dokumenteigenschaften](../vsto/how-to-programmatically-populate-word-tables-with-document-properties.md)
