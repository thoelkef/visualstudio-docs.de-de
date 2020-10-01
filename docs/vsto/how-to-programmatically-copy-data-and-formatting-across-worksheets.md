---
title: Programm gesteuertes Kopieren von Daten und Formatierungen zwischen Arbeitsblättern
titleSuffix: ''
ms.date: 02/02/2017
ms.topic: how-to
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- worksheets, copying data
- formatting [Office development in Visual Studio]
- data [Office development in Visual Studio], copying across worksheets
- copying data, Office development in Visual Studio
author: John-Hart
ms.author: johnhart
manager: jillfra
ms.workload:
- office
ms.openlocfilehash: e72d7c94068e5fe9ca0bf533d9d8fe4b7f8e8e54
ms.sourcegitcommit: 9d2829dc30b6917e89762d602022915f1ca49089
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 09/30/2020
ms.locfileid: "91585261"
---
# <a name="how-to-programmatically-copy-data-and-formatting-across-worksheets"></a>Gewusst wie: Programm gesteuertes Kopieren von Daten und Formatierungen zwischen Arbeitsblättern
  Mithilfe der-Methode können Sie Daten aus einem Bereich auf einem Blatt in alle anderen Blätter in einer-Arbeitsmappe kopieren <xref:Microsoft.Office.Interop.Excel.Worksheets.FillAcrossSheets%2A> . Geben Sie einen Bereich an, und geben Sie an, ob Sie Daten, Formatierung oder beides kopieren möchten.

 [!INCLUDE[appliesto_xlalldocapp](../vsto/includes/appliesto-xlalldocapp-md.md)]

## <a name="example"></a>Beispiel
 [!code-csharp[Trin_VstcoreExcelAutomation#44](../vsto/codesnippet/CSharp/Trin_VstcoreExcelAutomationCS/Sheet1.cs#44)]
 [!code-vb[Trin_VstcoreExcelAutomation#44](../vsto/codesnippet/VisualBasic/Trin_VstcoreExcelAutomation/Sheet1.vb#44)]

## <a name="compile-the-code"></a>Kompilieren des Codes
 Für dieses Beispiel ist ein Bereich `rangeData` mit dem Namen in einem Arbeitsblatt erforderlich.

## <a name="see-also"></a>Weitere Informationen
- [Arbeiten mit Arbeitsblättern](../vsto/working-with-worksheets.md)
- [Vorgehensweise: Programm gesteuertes Hinzufügen neuer Arbeitsblätter zu Arbeitsmappen](../vsto/how-to-programmatically-add-new-worksheets-to-workbooks.md)
- [Gewusst wie: Programm gesteuertes Ändern der Formatierung in Arbeitsblatt Zeilen, die ausgewählte Zellen enthalten](../vsto/how-to-programmatically-change-formatting-in-worksheet-rows-containing-selected-cells.md)
- [Optionale Parameter in Office-Projektmappen](../vsto/optional-parameters-in-office-solutions.md)
