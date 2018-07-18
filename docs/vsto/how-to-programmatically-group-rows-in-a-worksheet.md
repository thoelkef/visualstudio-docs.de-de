---
title: 'Gewusst wie: Programmgesteuertes Gruppieren von Zeilen in einem Arbeitsblatt'
ms.custom: ''
ms.date: 02/02/2017
ms.technology:
- office-development
ms.topic: conceptual
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- worksheets, creating groups
- groups, creating in worksheets
- ranges, creating groups
- worksheets, clearing groups
- groups
- groups [Office development in Visual Studio], clearing in worksheets
- worksheets, ungrouping rows and columns
- rows [Office development in Visual Studio], ungrouping
- columns [Office development in Visual Studio], ungrouping
author: TerryGLee
ms.author: tglee
manager: douge
ms.workload:
- office
ms.openlocfilehash: aa9624f90a337fb85ba2868b3b5c4f3cb1553ffb
ms.sourcegitcommit: 34f7d23ce3bd140dcae875b602d5719bb4363ed1
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 06/11/2018
ms.locfileid: "35258735"
---
# <a name="how-to-programmatically-group-rows-in-a-worksheet"></a>Gewusst wie: Programmgesteuertes Gruppieren von Zeilen in einem Arbeitsblatt
  Sie können eine oder mehrere ganze Zeilen gruppieren. Verwenden Sie zum Erstellen einer Gruppenstatus in einem Arbeitsblatt ein <xref:Microsoft.Office.Tools.Excel.NamedRange> Steuerelement oder ein systemeigenes Excel-Bereich-Objekt.  
  
 [!INCLUDE[appliesto_xlalldocapp](../vsto/includes/appliesto-xlalldocapp-md.md)]  
  
## <a name="use-a-namedrange-control"></a>Verwenden Sie ein NamedRange-Steuerelement  
 Wenn Sie beim Hinzufügen einer <xref:Microsoft.Office.Tools.Excel.NamedRange> Steuerelement zu einem Projekt auf Dokumentebene zur Entwurfszeit können Sie das Steuerelement eine Gruppe programmgesteuert zu erstellen. Im folgende Beispiel wird davon ausgegangen, dass es drei gibt <xref:Microsoft.Office.Tools.Excel.NamedRange> Steuerelemente auf dem gleichen Arbeitsblatt: `data2001`, `data2002`, und `dataAll`. Jeder benannte Bereich bezieht sich auf eine gesamte Zeile des Arbeitsblatts.  
  
### <a name="to-create-a-group-of-namedrange-controls-on-a-worksheet"></a>So erstellen Sie eine Gruppe von NamedRange-Steuerelementen in einem Arbeitsblatt  
  
1.  Gruppe von drei benannte Bereiche durch Aufrufen der <xref:Microsoft.Office.Tools.Excel.NamedRange.Group%2A> Methode jedes Bereichs. Dieser Code muss in einer Sheet-Klasse platziert werden und nicht in der `ThisWorkbook` -Klasse.  
  
     [!code-csharp[Trin_VstcoreExcelAutomation#32](../vsto/codesnippet/CSharp/Trin_VstcoreExcelAutomationCS/Sheet1.cs#32)]
     [!code-vb[Trin_VstcoreExcelAutomation#32](../vsto/codesnippet/VisualBasic/Trin_VstcoreExcelAutomation/Sheet1.vb#32)]  
  
    > [!NOTE]  
    >  Rufen Sie zum Aufheben der Gruppierung von Zeilen, die <xref:Microsoft.Office.Tools.Excel.NamedRange.Ungroup%2A> Methode.  
  
## <a name="use-native-excel-ranges"></a>Verwenden Sie systemeigene Excel-Bereiche  
 Der Code wird davon ausgegangen, dass Sie mit dem Namen der drei Excel-Bereichen verfügen `data2001`, `data2002`, und `dataAll` auf einem Arbeitsblatt.  
  
### <a name="to-create-a-group-of-excel-ranges-in-a-worksheet"></a>Um eine Gruppe von Excel-Bereiche in einem Arbeitsblatt zu erstellen.  
  
1.  Gruppe von drei benannte Bereiche durch Aufrufen der <xref:Microsoft.Office.Interop.Excel.Range.Group%2A> Methode jedes Bereichs. Im folgende Beispiel wird davon ausgegangen, dass es drei gibt <xref:Microsoft.Office.Interop.Excel.Range> -Steuerelemente namens `data2001`, `data2002`, und `dataAll` auf dem gleichen Arbeitsblatt. Jeder benannte Bereich bezieht sich auf eine gesamte Zeile des Arbeitsblatts.  
  
     [!code-csharp[Trin_VstcoreExcelAutomation#33](../vsto/codesnippet/CSharp/Trin_VstcoreExcelAutomationCS/Sheet1.cs#33)]
     [!code-vb[Trin_VstcoreExcelAutomation#33](../vsto/codesnippet/VisualBasic/Trin_VstcoreExcelAutomation/Sheet1.vb#33)]  
  
    > [!NOTE]  
    >  Rufen Sie zum Aufheben der Gruppierung von Zeilen, die <xref:Microsoft.Office.Interop.Excel.Range.Ungroup%2A> Methode.  
  
## <a name="see-also"></a>Siehe auch  
 [Arbeiten mit Arbeitsblättern](../vsto/working-with-worksheets.md)   
 [NamedRange-Steuerelement](../vsto/namedrange-control.md)   
 [Gewusst wie: Hinzufügen von NamedRange-Steuerelementen zu Arbeitsblättern](../vsto/how-to-add-namedrange-controls-to-worksheets.md)   
 [Optionaler Parameter in Office-Projektmappen](../vsto/optional-parameters-in-office-solutions.md)  
  
  