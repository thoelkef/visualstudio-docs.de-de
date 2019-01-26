---
title: 'Vorgehensweise: Programmgesteuertes Anwenden von Farben auf Excel-Bereiche'
ms.date: 02/02/2017
ms.topic: conceptual
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- formatting [Office development in Visual Studio]
- color, Excel ranges
- ranges, applying color
author: John-Hart
ms.author: johnhart
manager: jillfra
ms.workload:
- office
ms.openlocfilehash: 83a7a3e58212b0c20264b3b325f3658760aa5ae4
ms.sourcegitcommit: c0202a77d4dc562cdc55dc2e6223c062281d9749
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 01/24/2019
ms.locfileid: "54868169"
---
# <a name="how-to-programmatically-apply-color-to-excel-ranges"></a>Vorgehensweise: Programmgesteuertes Anwenden von Farben auf Excel-Bereiche
  Verwenden Sie zum Anwenden einer Farbe Sie Text in einem Zellbereich eine <xref:Microsoft.Office.Tools.Excel.NamedRange> Steuerelement oder ein systemeigenes Excel-Bereich-Objekt.  
  
 [!INCLUDE[appliesto_xlalldocapp](../vsto/includes/appliesto-xlalldocapp-md.md)]  
  
## <a name="use-a-namedrange-control"></a>Verwenden Sie ein NamedRange-Steuerelement  
 In diesem Beispiel ist für Anpassungen auf Dokumentebene.  
  
### <a name="to-apply-color-to-a-namedrange-control"></a>Farbe auf ein NamedRange-Steuerelement anwenden  
  
1.  Erstellen Sie eine <xref:Microsoft.Office.Tools.Excel.NamedRange> -Steuerelement zur Zelle A1.  
  
     [!code-csharp[Trin_VstcoreExcelAutomation#65](../vsto/codesnippet/CSharp/Trin_VstcoreExcelAutomationCS/Sheet1.cs#65)]
     [!code-vb[Trin_VstcoreExcelAutomation#65](../vsto/codesnippet/VisualBasic/Trin_VstcoreExcelAutomation/Sheet1.vb#65)]  
  
2.  Legen Sie die Farbe des Texts in der <xref:Microsoft.Office.Tools.Excel.NamedRange> Steuerelement.  
  
     [!code-csharp[Trin_VstcoreExcelAutomation#66](../vsto/codesnippet/CSharp/Trin_VstcoreExcelAutomationCS/Sheet1.cs#66)]
     [!code-vb[Trin_VstcoreExcelAutomation#66](../vsto/codesnippet/VisualBasic/Trin_VstcoreExcelAutomation/Sheet1.vb#66)]  
  
## <a name="use-native-excel-ranges"></a>Verwenden Sie systemeigene Excel-Bereiche  
  
### <a name="to-apply-color-to-a-native-excel-range-object"></a>Farbe auf ein systemeigenes Excel-Bereich-Objekt anwenden  
  
1.  Erstellen Sie einen Bereich in Zelle A1 aus, und legen Sie dann die Farbe des Texts.  
  
     [!code-csharp[Trin_VstcoreExcelAutomation#67](../vsto/codesnippet/CSharp/Trin_VstcoreExcelAutomationCS/Sheet1.cs#67)]
     [!code-vb[Trin_VstcoreExcelAutomation#67](../vsto/codesnippet/VisualBasic/Trin_VstcoreExcelAutomation/Sheet1.vb#67)]  
  
## <a name="see-also"></a>Siehe auch  
 [Arbeiten mit Bereichen](../vsto/working-with-ranges.md)   
 [NamedRange-Steuerelement](../vsto/namedrange-control.md)   
 [Vorgehensweise: Programmgesteuertes Anwenden von Formaten auf Bereiche in Arbeitsmappen](../vsto/how-to-programmatically-apply-styles-to-ranges-in-workbooks.md)   
 [Vorgehensweise: Programmgesteuertes Verweisen Sie auf Arbeitsblattbereiche im code](../vsto/how-to-programmatically-refer-to-worksheet-ranges-in-code.md)   
 [Automatisieren von Excel mithilfe von erweiterten Objekten](../vsto/automating-excel-by-using-extended-objects.md)   
 [Optionaler Parameter in Office-Projektmappen](../vsto/optional-parameters-in-office-solutions.md)  
