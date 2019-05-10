---
title: 'Vorgehensweise: Programmgesteuertes Anzeigen einer Zeichenfolge in einer Arbeitsblattzelle'
ms.date: 02/02/2017
ms.topic: conceptual
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- text [Office development in Visual Studio], adding to worksheets
- worksheets, displaying text in cells
author: John-Hart
ms.author: johnhart
manager: jillfra
ms.workload:
- office
ms.openlocfilehash: a9760d019fa80d4ecae63633c38ac9df60932202
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/23/2019
ms.locfileid: "62813022"
---
# <a name="how-to-programmatically-display-a-string-in-a-worksheet-cell"></a>Vorgehensweise: Programmgesteuertes Anzeigen einer Zeichenfolge in einer Arbeitsblattzelle
  In diesem Beispiel wird veranschaulicht, wie Text programmgesteuert in einer Zelle angezeigt wird. Um Text in Zelle anzuzeigen, verwenden Sie entweder eine <xref:Microsoft.Office.Tools.Excel.NamedRange> Steuerelement oder ein systemeigenes Excel-Bereich-Objekt.

 [!INCLUDE[appliesto_xlalldocapp](../vsto/includes/appliesto-xlalldocapp-md.md)]

## <a name="use-a-namedrange-control"></a>Verwenden Sie ein NamedRange-Steuerelement
 Dieses Beispiel verwendet eine <xref:Microsoft.Office.Tools.Excel.NamedRange> Steuerelement mit dem Namen `message`. Das Steuerelement muss eine Anpassung auf Dokumentebene zur Entwurfszeit hinzugefügt werden. Der folgende Code muss in einer Sheet-Klasse platziert werden, nicht in der `ThisWorkbook` Klasse.

### <a name="to-display-text-in-a-namedrange-control"></a>Zum Anzeigen von Text in einem NamedRange-Steuerelement

1. Legen Sie den Wert, der die <xref:Microsoft.Office.Tools.Excel.NamedRange> die Steuerung an **Hello World**.

     [!code-csharp[Trin_VstcoreExcelAutomation#68](../vsto/codesnippet/CSharp/Trin_VstcoreExcelAutomationCS/Sheet1.cs#68)]
     [!code-vb[Trin_VstcoreExcelAutomation#68](../vsto/codesnippet/VisualBasic/Trin_VstcoreExcelAutomation/Sheet1.vb#68)]

## <a name="use-a-native-excel-range"></a>Verwenden Sie einen systemeigenen Excel-Bereich
 Der folgende Code wird einen neuen Bereich programmgesteuert erstellt, und klicken Sie dann ein Wert zugewiesen.

### <a name="to-display-text-in-an-excel-range"></a>Zum Anzeigen von Text in einem Excel-Bereich

1. Rufen Sie den Bereich in Zelle **A1** auf `Sheet1` und legen Sie den Wert **Hello World**.

     [!code-csharp[Trin_VstcoreExcelAutomation#69](../vsto/codesnippet/CSharp/Trin_VstcoreExcelAutomationCS/Sheet1.cs#69)]
     [!code-vb[Trin_VstcoreExcelAutomation#69](../vsto/codesnippet/VisualBasic/Trin_VstcoreExcelAutomation/Sheet1.vb#69)]

## <a name="see-also"></a>Siehe auch
- [Exemplarische Vorgehensweise: Sammeln von Daten mit einem Windows form](../vsto/walkthrough-collecting-data-using-a-windows-form.md)
- [Problembehandlung bei Office-Projektmappen](../vsto/troubleshooting-office-solutions.md)
- [NamedRange-Steuerelement](../vsto/namedrange-control.md)
- [Globaler Zugriff auf Objekte in Office-Projekten](../vsto/global-access-to-objects-in-office-projects.md)
- [Optionaler Parameter in Office-Projektmappen](../vsto/optional-parameters-in-office-solutions.md)
