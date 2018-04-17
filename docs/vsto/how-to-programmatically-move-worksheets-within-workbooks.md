---
title: 'Vorgehensweise: Programmgesteuertes Verschieben von Arbeitsblättern in Arbeitsmappen | Microsoft Docs'
ms.custom: ''
ms.date: 02/02/2017
ms.technology:
- office-development
ms.topic: conceptual
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- worksheets, moving
- workbooks, moving worksheets in
author: TerryGLee
ms.author: tglee
manager: douge
ms.workload:
- office
ms.openlocfilehash: 5b34374b7795422aef83c7f79fe49931b1b69acc
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/16/2018
---
# <a name="how-to-programmatically-move-worksheets-within-workbooks"></a>Gewusst wie: Programmgesteuertes Verschieben von Arbeitsblättern in Arbeitsmappen
  Sie können die Position von Arbeitsblättern relativ zu anderen Arbeitsblättern in einer Arbeitsmappe programmgesteuert ändern. Wenn Sie keine Position für das zu verschiebende Blatt angeben, erstellt Excel eine neue Arbeitsmappe, in der das Blatt enthalten ist.  
  
 [!INCLUDE[appliesto_xlalldocapp](../vsto/includes/appliesto-xlalldocapp-md.md)]  
  
### <a name="to-move-a-worksheet-in-a-document-level-customization"></a>So verschieben Sie ein Arbeitsblatt in einer Anpassung auf Dokumentebene  
  
1.  Weisen Sie die Gesamtzahl von Blättern in der Arbeitsmappe einer Variablen zu, und verschieben Sie dann das erste Arbeitsblatt so, dass es zum letzten Blatt wird.  
  
     [!code-csharp[Trin_VstcoreExcelAutomation#24](../vsto/codesnippet/CSharp/Trin_VstcoreExcelAutomationCS/Sheet1.cs#24)]
     [!code-vb[Trin_VstcoreExcelAutomation#24](../vsto/codesnippet/VisualBasic/Trin_VstcoreExcelAutomation/Sheet1.vb#24)]  
  
### <a name="to-move-a-worksheet-in-an-vsto-add-in"></a>So verschieben Sie ein Arbeitsblatt in einem VSTO-Add-In  
  
1.  Weisen Sie die Gesamtzahl von Blättern in der Arbeitsmappe einer Variablen zu, und verschieben Sie dann das erste Arbeitsblatt so, dass es zum letzten Blatt wird.  
  
     [!code-csharp[Trin_VstcoreExcelAutomationAddIn#16](../vsto/codesnippet/CSharp/trin_vstcoreexcelautomationaddin/ThisAddIn.cs#16)]
     [!code-vb[Trin_VstcoreExcelAutomationAddIn#16](../vsto/codesnippet/VisualBasic/trin_vstcoreexcelautomationaddin/ThisAddIn.vb#16)]  
  
## <a name="see-also"></a>Siehe auch  
 [Arbeiten mit Arbeitsblättern](../vsto/working-with-worksheets.md)   
 [Vorgehensweise: Programmgesteuertes Ausblenden von Arbeitsblättern](../vsto/how-to-programmatically-hide-worksheets.md)   
 [Vorgehensweise: Programmgesteuertes Löschen von Arbeitsblättern aus Arbeitsmappen](../vsto/how-to-programmatically-delete-worksheets-from-workbooks.md)   
 [Vorgehensweise: Programmgesteuertes Schützen von Arbeitsblättern](../vsto/how-to-programmatically-protect-worksheets.md)   
 [Globaler Zugriff auf Objekte in Office-Projekten](../vsto/global-access-to-objects-in-office-projects.md)  
  
  