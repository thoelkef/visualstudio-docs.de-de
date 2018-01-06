---
title: 'Vorgehensweise: Programmgesteuertes Gruppieren von Zeilen in einem Arbeitsblatt | Microsoft Docs'
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
- worksheets, creating groups
- groups, creating in worksheets
- ranges, creating groups
- worksheets, clearing groups
- groups
- groups [Office development in Visual Studio], clearing in worksheets
- worksheets, ungrouping rows and columns
- rows [Office development in Visual Studio], ungrouping
- columns [Office development in Visual Studio], ungrouping
ms.assetid: 48037dca-35a2-4df2-918b-6a9f568fae91
caps.latest.revision: "46"
author: gewarren
ms.author: gewarren
manager: ghogen
ms.workload: office
ms.openlocfilehash: f17c90fb5f10dfdc0658f9176e0e15cedcc6f1d5
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 12/22/2017
---
# <a name="how-to-programmatically-group-rows-in-a-worksheet"></a>Gewusst wie: Programmgesteuertes Gruppieren von Zeilen in einem Arbeitsblatt
  Sie können eine oder mehrere ganze Zeilen gruppieren. Verwenden Sie zum Erstellen einer Gruppenstatus in einem Arbeitsblatt ein <xref:Microsoft.Office.Tools.Excel.NamedRange> Steuerelement oder ein systemeigenes Excel-Range-Objekt.  
  
 [!INCLUDE[appliesto_xlalldocapp](../vsto/includes/appliesto-xlalldocapp-md.md)]  
  
## <a name="using-a-namedrange-control"></a>Verwenden ein NamedRange-Steuerelement  
 Wenn Sie beim Hinzufügen einer <xref:Microsoft.Office.Tools.Excel.NamedRange> Steuerelement zu einem Projekt auf Dokumentebene zur Entwurfszeit können Sie das Steuerelement verwenden, um eine Gruppe programmgesteuert zu erstellen. Im folgende Beispiel wird davon ausgegangen, dass es drei gibt <xref:Microsoft.Office.Tools.Excel.NamedRange> Steuerelemente auf dem Arbeitsblatt: `data2001`, `data2002`, und `dataAll`. Jeder benannte Bereich bezieht sich auf eine ganze Zeile im Arbeitsblatt.  
  
#### <a name="to-create-a-group-of-namedrange-controls-on-a-worksheet"></a>So erstellen eine Gruppe von NamedRange-Steuerelementen in einem Arbeitsblatt  
  
1.  Gruppieren Sie drei benannte Bereiche durch Aufrufen der <xref:Microsoft.Office.Tools.Excel.NamedRange.Group%2A> Methode der einzelnen Bereiche liegen. Dieser Code muss in einer Sheet-Klasse platziert werden und nicht in der `ThisWorkbook` -Klasse.  
  
     [!code-csharp[Trin_VstcoreExcelAutomation#32](../vsto/codesnippet/CSharp/Trin_VstcoreExcelAutomationCS/Sheet1.cs#32)]
     [!code-vb[Trin_VstcoreExcelAutomation#32](../vsto/codesnippet/VisualBasic/Trin_VstcoreExcelAutomation/Sheet1.vb#32)]  
  
    > [!NOTE]  
    >  Rufen Sie zum Aufheben der Gruppierung von Zeilen die <xref:Microsoft.Office.Tools.Excel.NamedRange.Ungroup%2A> Methode.  
  
## <a name="using-native-excel-ranges"></a>Verwenden von systemeigenen Excel-Bereichen  
 Der Code wird davon ausgegangen, dass stehen Ihnen drei Excel-Bereiche, die mit dem Namen `data2001`, `data2002`, und `dataAll` in einem Arbeitsblatt.  
  
#### <a name="to-create-a-group-of-excel-ranges-in-a-worksheet"></a>So erstellen eine Gruppe von Excel-Bereichen in einem Arbeitsblatt  
  
1.  Gruppieren Sie drei benannte Bereiche durch Aufrufen der <xref:Microsoft.Office.Interop.Excel.Range.Group%2A> Methode der einzelnen Bereiche liegen. Im folgende Beispiel wird davon ausgegangen, dass es drei gibt <xref:Microsoft.Office.Interop.Excel.Range> -Steuerelemente namens `data2001`, `data2002`, und `dataAll` auf dem Arbeitsblatt. Jeder benannte Bereich bezieht sich auf eine ganze Zeile im Arbeitsblatt.  
  
     [!code-csharp[Trin_VstcoreExcelAutomation#33](../vsto/codesnippet/CSharp/Trin_VstcoreExcelAutomationCS/Sheet1.cs#33)]
     [!code-vb[Trin_VstcoreExcelAutomation#33](../vsto/codesnippet/VisualBasic/Trin_VstcoreExcelAutomation/Sheet1.vb#33)]  
  
    > [!NOTE]  
    >  Rufen Sie zum Aufheben der Gruppierung von Zeilen die <xref:Microsoft.Office.Interop.Excel.Range.Ungroup%2A> Methode.  
  
## <a name="see-also"></a>Siehe auch  
 [Arbeiten mit Arbeitsblättern](../vsto/working-with-worksheets.md)   
 [NamedRange-Steuerelement](../vsto/namedrange-control.md)   
 [Vorgehensweise: Hinzufügen von NamedRange-Steuerelementen zu Arbeitsblättern](../vsto/how-to-add-namedrange-controls-to-worksheets.md)   
 [Optionale Parameter in Office-Projektmappen](../vsto/optional-parameters-in-office-solutions.md)  
  
  