---
title: 'Vorgehensweise: Ändern der Größe Steuerelementen innerhalb der Arbeitsblattzellen'
ms.date: 02/02/2017
ms.topic: conceptual
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- controls [Office development in Visual Studio], resizing
- managed controls, resizing
- worksheets, resizing
- Windows Forms controls [Office development in Visual Studio], resizing
author: John-Hart
ms.author: johnhart
manager: jillfra
ms.workload:
- office
ms.openlocfilehash: b51f26a4ea2dec50c5ee90c38f49412866b6f866
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/23/2019
ms.locfileid: "62961490"
---
# <a name="how-to-resize-controls-within-worksheet-cells"></a>Vorgehensweise: Ändern der Größe Steuerelementen innerhalb der Arbeitsblattzellen
  Wenn Sie die Spalten oder Zeilen in einem Arbeitsblatt Größe, die Größe ändern alle Hoststeuerelemente in den Zellen automatisch an die Höhe oder Breite der Zelle, die Größe geändert wurde. Windows Forms-Steuerelemente sind standardmäßig nicht automatisch angepasst.

 [!INCLUDE[appliesto_xlalldoc](../vsto/includes/appliesto-xlalldoc-md.md)]

 Wenn Sie die Steuerelemente zur Entwurfszeit hinzufügen, müssen Sie die Positionierungsoptionen für jedes Steuerelement festlegen.

 Wenn Sie ein Windows Forms-Steuerelement programmgesteuert hinzufügen, und geben Sie eine Bereichsargument, ändert die Größe des Steuerelements automatisch beim Ändern der Größe einer Zelle innerhalb des Bereichs. Weitere Informationen finden Sie unter [Hinzufügen von Steuerelementen zu Office-Dokumenten zur Laufzeit](../vsto/adding-controls-to-office-documents-at-run-time.md).

## <a name="resize-controls-at-design-time"></a>Größe der Steuerelemente zur Entwurfszeit

### <a name="to-make-controls-resize-with-cells-at-design-time"></a>Um mit Steuerelementen zur Entwurfszeit mit Zellen ändern der Größe

1. Von der **Toolbox**, ziehen Sie ein Windows Forms-Steuerelement in einem Arbeitsblatt.

2. Klicken Sie auf das Steuerelement, und klicken Sie dann auf **Formatsteuerung**.

3. In der **Formatsteuerung** Dialogfeld klicken Sie auf die **Eigenschaften** Registerkarte.

4. Klicken Sie unter **Objektposition**, wählen die **Größe und mit Zellen** aus, und klicken Sie dann auf **OK**.

     Wenn Sie die Größe der Zelle, die das Steuerelement enthält, wird die Größe des Steuerelements die Zelle eingepasst werden.

## <a name="resize-controls-at-runtime"></a>Ändern der Größe Steuerelementen zur Laufzeit
 Wenn Sie ein Windows Forms-Steuerelement zur Laufzeit hinzufügen, und übergeben einen <xref:Microsoft.Office.Interop.Excel.Range> als Speicherort für das Steuerelement, das Steuerelement wird automatisch angepasst, wenn die Arbeitsblatt-Zelle, die den Bereich enthält die Größe geändert wird.

### <a name="to-make-controls-resize-with-cells-at-run-time"></a>Um mit Steuerelementen zur Laufzeit mit Zellen ändern der Größe

1. Fügen Sie ein Steuerelement zum Bereich A1.

     [!code-vb[Trin_VstcoreProgrammingControlsExcel#5](../vsto/codesnippet/VisualBasic/my excel chart/Sheet1.vb#5)]
     [!code-csharp[Trin_VstcoreProgrammingControlsExcel#5](../vsto/codesnippet/CSharp/Trin_VstcoreProgrammingControlsExcelCS/Sheet1.cs#5)]

     Wenn Sie die Größe der Zelle, die das Steuerelement enthält, wird die Größe des Steuerelements die Zelle eingepasst werden.

## <a name="reset-control-placement"></a>Zurücksetzen von Steuerelementen
 Sie können die Platzierung und Ändern der Größe des Steuerelements durch Festlegen von Zurücksetzen der `Placement` -Eigenschaft auf einen der folgenden <xref:Microsoft.Office.Interop.Excel.XlPlacement> Werte:

- <xref:Microsoft.Office.Interop.Excel.XlPlacement.xlFreeFloating>

- <xref:Microsoft.Office.Interop.Excel.XlPlacement.xlMove>

- <xref:Microsoft.Office.Interop.Excel.XlPlacement.xlMoveAndSize>

### <a name="to-change-the-behavior-of-a-control-so-that-it-does-not-resize-or-move-with-the-cell"></a>Um das Verhalten eines Steuerelements zu ändern, damit es nicht mit der Zelle zu verschieben oder Ändern der Größe

1. Rufen Sie die Placement-Eigenschaft des Steuerelements, und legen Sie den Wert <xref:Microsoft.Office.Interop.Excel.XlPlacement.xlFreeFloating>.

     [!code-vb[Trin_VstcoreProgrammingControlsExcel#6](../vsto/codesnippet/VisualBasic/my excel chart/Sheet1.vb#6)]
     [!code-csharp[Trin_VstcoreProgrammingControlsExcel#6](../vsto/codesnippet/CSharp/Trin_VstcoreProgrammingControlsExcelCS/Sheet1.cs#6)]

## <a name="see-also"></a>Siehe auch
- [Steuerelemente für Office-Dokumente](../vsto/controls-on-office-documents.md)
- [Vorgehensweise: Hinzufügen von Windows Forms-Steuerelementen zu Office-Dokumenten](../vsto/how-to-add-windows-forms-controls-to-office-documents.md)
- [Vorgehensweise: Ausblenden von Steuerelementen auf Arbeitsblättern beim Drucken](../vsto/how-to-hide-controls-on-worksheets-when-printing.md)
- [Hinzufügen von Steuerelementen zu Office-Dokumenten zur Laufzeit](../vsto/adding-controls-to-office-documents-at-run-time.md)
- [Einschränkungen für Windows Forms-Steuerelemente in Office-Dokumente](../vsto/limitations-of-windows-forms-controls-on-office-documents.md)
