---
title: 'Gewusst wie: Programmgesteuertes Kopieren von Daten und Formatierungen zwischen Arbeitsblättern'
ms.custom: ''
ms.date: 02/02/2017
ms.technology:
- office-development
ms.topic: conceptual
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- worksheets, copying data
- formatting [Office development in Visual Studio]
- data [Office development in Visual Studio], copying across worksheets
- copying data, Office development in Visual Studio
author: TerryGLee
ms.author: tglee
manager: douge
ms.workload:
- office
ms.openlocfilehash: 4a4cce083bee8b57ff37276ae909799a9a6791d7
ms.sourcegitcommit: 34f7d23ce3bd140dcae875b602d5719bb4363ed1
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 06/11/2018
ms.locfileid: "35256681"
---
# <a name="how-to-programmatically-copy-data-and-formatting-across-worksheets"></a>Gewusst wie: Programmgesteuertes Kopieren von Daten und Formatierungen zwischen Arbeitsblättern
  Sie können Kopieren von Daten aus einem Bereich auf einem Blatt in alle übrigen Arbeitsblätter in einer Arbeitsmappe mithilfe der <xref:Microsoft.Office.Interop.Excel.Worksheets.FillAcrossSheets%2A> Methode. Geben Sie einen Bereich, und Kopieren von Daten, formatieren oder beides werden sollen.  
  
 [!INCLUDE[appliesto_xlalldocapp](../vsto/includes/appliesto-xlalldocapp-md.md)]  
  
## <a name="example"></a>Beispiel  
 [!code-csharp[Trin_VstcoreExcelAutomation#44](../vsto/codesnippet/CSharp/Trin_VstcoreExcelAutomationCS/Sheet1.cs#44)]
 [!code-vb[Trin_VstcoreExcelAutomation#44](../vsto/codesnippet/VisualBasic/Trin_VstcoreExcelAutomation/Sheet1.vb#44)]  
  
## <a name="compile-the-code"></a>Kompilieren des Codes  
 Dieses Beispiel erfordert einen Bereich mit dem Namen `rangeData` in einem Arbeitsblatt.  
  
## <a name="see-also"></a>Siehe auch  
 [Arbeiten mit Arbeitsblättern](../vsto/working-with-worksheets.md)   
 [Gewusst wie: Programmgesteuertes Hinzufügen neuer Arbeitsblätter zu Arbeitsmappen](../vsto/how-to-programmatically-add-new-worksheets-to-workbooks.md)   
 [Gewusst wie: Programmgesteuertes Ändern der Formatierung in Arbeitsblattzeilen, die ausgewählte Zellen enthalten](../vsto/how-to-programmatically-change-formatting-in-worksheet-rows-containing-selected-cells.md)   
 [Optionaler Parameter in Office-Projektmappen](../vsto/optional-parameters-in-office-solutions.md)  
  
  