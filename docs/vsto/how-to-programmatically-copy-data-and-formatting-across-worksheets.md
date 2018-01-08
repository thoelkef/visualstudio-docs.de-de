---
title: "Vorgehensweise: Programmgesteuertes Kopieren von Daten und Formatierungen zwischen Arbeitsblättern | Microsoft Docs"
ms.custom: 
ms.date: 02/02/2017
ms.reviewer: 
ms.suite: 
ms.technology: office-development
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- worksheets, copying data
- formatting [Office development in Visual Studio]
- data [Office development in Visual Studio], copying across worksheets
- copying data, Office development in Visual Studio
ms.assetid: eed7dbaf-bdb5-4330-ba2e-5f3d50817eca
caps.latest.revision: "37"
author: gewarren
ms.author: gewarren
manager: ghogen
ms.workload: office
ms.openlocfilehash: 9f8b976427abe35ef8383604eea93f1513316903
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 12/22/2017
---
# <a name="how-to-programmatically-copy-data-and-formatting-across-worksheets"></a>Gewusst wie: Programmgesteuertes Kopieren von Daten und Formatierungen zwischen Arbeitsblättern
  Sie können Daten in die anderen Blätter in einer Arbeitsmappe aus einem Bereich auf einem Blatt kopieren, mithilfe der <xref:Microsoft.Office.Interop.Excel.Worksheets.FillAcrossSheets%2A> Methode. Geben Sie einen Bereich, und gibt an, ob Sie Daten, formatieren oder beides kopieren möchten.  
  
 [!INCLUDE[appliesto_xlalldocapp](../vsto/includes/appliesto-xlalldocapp-md.md)]  
  
## <a name="example"></a>Beispiel  
 [!code-csharp[Trin_VstcoreExcelAutomation#44](../vsto/codesnippet/CSharp/Trin_VstcoreExcelAutomationCS/Sheet1.cs#44)]
 [!code-vb[Trin_VstcoreExcelAutomation#44](../vsto/codesnippet/VisualBasic/Trin_VstcoreExcelAutomation/Sheet1.vb#44)]  
  
## <a name="compiling-the-code"></a>Kompilieren des Codes  
 Dieses Beispiel benötigen Sie einen Bereich mit dem Namen `rangeData` in einem Arbeitsblatt.  
  
## <a name="see-also"></a>Siehe auch  
 [Arbeiten mit Arbeitsblättern](../vsto/working-with-worksheets.md)   
 [Vorgehensweise: Programmgesteuertes Hinzufügen neuer Arbeitsblätter zu Arbeitsmappen](../vsto/how-to-programmatically-add-new-worksheets-to-workbooks.md)   
 [Vorgehensweise: Programmgesteuertes Ändern der Formatierung in Arbeitsblattzeilen, die ausgewählte Zellen enthalten](../vsto/how-to-programmatically-change-formatting-in-worksheet-rows-containing-selected-cells.md)   
 [Optionale Parameter in Office-Projektmappen](../vsto/optional-parameters-in-office-solutions.md)  
  
  