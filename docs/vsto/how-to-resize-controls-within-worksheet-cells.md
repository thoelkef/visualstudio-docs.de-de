---
title: "Vorgehensweise: Ändern der Größe Steuerelementen innerhalb der Arbeitsblattzellen | Microsoft Docs"
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
- controls [Office development in Visual Studio], resizing
- managed controls, resizing
- worksheets, resizing
- Windows Forms controls [Office development in Visual Studio], resizing
ms.assetid: 1439db4a-e64b-4381-a6e6-605ba94db3de
caps.latest.revision: "33"
author: gewarren
ms.author: gewarren
manager: ghogen
ms.workload: office
ms.openlocfilehash: 75759b501741329808198aafbc7dd39d0994cb98
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 12/22/2017
---
# <a name="how-to-resize-controls-within-worksheet-cells"></a>Gewusst wie: Ändern der Größe von Steuerelementen innerhalb der Arbeitsblattzellen
  Wenn Sie die Spalten oder Zeilen in einem Arbeitsblatt Größe, ändern Sie die Größe alle Hoststeuerelemente, die in den Zellen enthalten sind, automatisch an die Höhe oder Breite der Zelle, die Größe geändert wurde. Windows Forms-Steuerelemente sind standardmäßig nicht automatisch angepasst.  
  
 [!INCLUDE[appliesto_xlalldoc](../vsto/includes/appliesto-xlalldoc-md.md)]  
  
 Wenn Sie die Steuerelemente zur Entwurfszeit hinzufügen, müssen Sie die Positionierungsoptionen für jedes Steuerelement festlegen.  
  
 Wenn Sie ein Windows Forms-Steuerelement programmgesteuert hinzufügen, und geben Sie ein Bereichsargument, ändert die Größe des Steuerelements automatisch beim Ändern der Größe einer Zelle innerhalb des Bereichs. Weitere Informationen finden Sie unter [Adding Controls to Office Documents at Run Time](../vsto/adding-controls-to-office-documents-at-run-time.md).  
  
## <a name="resizing-controls-at-design-time"></a>Ändern der Größe von Steuerelementen zur Entwurfszeit  
  
#### <a name="to-make-controls-resize-with-cells-at-design-time"></a>Um zur Entwurfszeit mit Zellen Größe von Steuerelementen zu machen.  
  
1.  Aus der **Toolbox**, ziehen Sie ein Windows Forms-Steuerelement zu einem Arbeitsblatt.  
  
2.  Maustaste auf das Steuerelement, und klicken Sie dann auf **Formatsteuerung**.  
  
3.  In der **Formatsteuerung** (Dialogfeld), klicken Sie auf die **Eigenschaften** Registerkarte.  
  
4.  Klicken Sie unter **Objektposition**, wählen die **Größe und mit Zellen** aus, und klicken Sie dann auf **OK**.  
  
     Wenn Sie die Größe der Zelle, die das Steuerelement enthält, wird das Steuerelement die Zelle angepasst.  
  
## <a name="resizing-controls-at-run-time"></a>Ändern der Größe von Steuerelementen zur Laufzeit  
 Wenn Sie ein Windows Forms-Steuerelement zur Laufzeit hinzufügen, und übergeben Sie eine <xref:Microsoft.Office.Interop.Excel.Range> als Speicherort für das Steuerelement, wird automatisch die Größe des Steuerelements beim Ändern der Größe der Zelle des Arbeitsblatts beschrieben, die der Bereich enthält.  
  
#### <a name="to-make-controls-resize-with-cells-at-run-time"></a>Um Steuerelemente zur Laufzeit mit Zellen ändern  
  
1.  Fügen Sie ein Steuerelement zum Bereich A1.  
  
     [!code-vb[Trin_VstcoreProgrammingControlsExcel#5](../vsto/codesnippet/VisualBasic/my excel chart/Sheet1.vb#5)]
     [!code-csharp[Trin_VstcoreProgrammingControlsExcel#5](../vsto/codesnippet/CSharp/Trin_VstcoreProgrammingControlsExcelCS/Sheet1.cs#5)]  
  
     Wenn Sie die Größe der Zelle, die das Steuerelement enthält, wird das Steuerelement die Zelle angepasst.  
  
## <a name="resetting-control-placement"></a>Zurücksetzen von Steuerelementen  
 Sie können zurücksetzen, die Platzierung und Ändern der Größe des Steuerelements durch Festlegen der `Placement` -Eigenschaft auf einen der folgenden <xref:Microsoft.Office.Interop.Excel.XlPlacement> Werte:  
  
-   <xref:Microsoft.Office.Interop.Excel.XlPlacement.xlFreeFloating>  
  
-   <xref:Microsoft.Office.Interop.Excel.XlPlacement.xlMove>  
  
-   <xref:Microsoft.Office.Interop.Excel.XlPlacement.xlMoveAndSize>  
  
#### <a name="to-change-the-behavior-of-a-control-so-that-it-does-not-resize-or-move-with-the-cell"></a>Um das Verhalten eines Steuerelements ändern, damit ändern Sie die Größe oder nicht mit der Zelle zu verschieben  
  
1.  Rufen Sie die Platzierungseigenschaft des Steuerelements, und legen den Wert auf <xref:Microsoft.Office.Interop.Excel.XlPlacement.xlFreeFloating>.  
  
     [!code-vb[Trin_VstcoreProgrammingControlsExcel#6](../vsto/codesnippet/VisualBasic/my excel chart/Sheet1.vb#6)]
     [!code-csharp[Trin_VstcoreProgrammingControlsExcel#6](../vsto/codesnippet/CSharp/Trin_VstcoreProgrammingControlsExcelCS/Sheet1.cs#6)]  
  
## <a name="see-also"></a>Siehe auch  
 [Steuerelemente für Office-Dokumente](../vsto/controls-on-office-documents.md)   
 [Vorgehensweise: Hinzufügen von Windows Forms-Steuerelementen zu Office-Dokumenten](../vsto/how-to-add-windows-forms-controls-to-office-documents.md)   
 [Vorgehensweise: Ausblenden von Steuerelementen auf Arbeitsblättern beim Drucken](../vsto/how-to-hide-controls-on-worksheets-when-printing.md)   
 [Hinzufügen von Steuerelementen zu Office-Dokumenten zur Laufzeit](../vsto/adding-controls-to-office-documents-at-run-time.md)   
 [Einschränkungen für Windows Forms-Steuerelemente in Office-Dokumenten](../vsto/limitations-of-windows-forms-controls-on-office-documents.md)  
  