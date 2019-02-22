---
title: 'Exemplarische Vorgehensweise: Ändern der arbeitsblattformatierung mithilfe von CheckBox-Steuerelementen'
ms.date: 02/02/2017
ms.topic: conceptual
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- worksheets, changing formatting using managed controls
- worksheets, check box controls
- controls [Office development in Visual Studio], adding to worksheets
author: John-Hart
ms.author: johnhart
manager: jillfra
ms.workload:
- office
ms.openlocfilehash: 77b9226857a7dbd43f8f2cd0f5d247e8a1386d4f
ms.sourcegitcommit: d0425b6b7d4b99e17ca6ac0671282bc718f80910
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 02/21/2019
ms.locfileid: "56624658"
---
# <a name="walkthrough-change-worksheet-formatting-using-checkbox-controls"></a>Exemplarische Vorgehensweise: Ändern der arbeitsblattformatierung mithilfe von CheckBox-Steuerelementen
  In dieser exemplarischen Vorgehensweise wird gezeigt, die Grundlagen der Verwendung von Kontrollkästchen in einem Microsoft Office Excel-Arbeitsblatt zum Ändern der Formatierung. Verwenden Sie Office-Entwicklungstools in Visual Studio erstellen, und fügen Sie Code zum Projekt hinzu. Das Ergebnis als vollständiges Beispiel finden Sie unter dem Beispiel des Excel-Steuerelemente unter [Office-Entwicklungsbeispiele und exemplarische Vorgehensweisen](../vsto/office-development-samples-and-walkthroughs.md).

 [!INCLUDE[appliesto_xlalldoc](../vsto/includes/appliesto-xlalldoc-md.md)]

 Bei dieser exemplarischen Vorgehensweise lernen Sie Folgendes:

-   Hinzufügen von Text und Steuerelementen zu einem Arbeitsblatt.

-   Der Text wird formatiert, wenn eine Option ausgewählt ist.

-   Testen Sie das Projekt ein.

> [!NOTE]
>  Auf Ihrem Computer werden möglicherweise andere Namen oder Speicherorte für die Benutzeroberflächenelemente von Visual Studio angezeigt als die in den folgenden Anweisungen aufgeführten. Diese Elemente sind von der jeweiligen Visual Studio-Version und den verwendeten Einstellungen abhängig. Weitere Informationen finden Sie unter [Personalisieren von Visual Studio-IDE](../ide/personalizing-the-visual-studio-ide.md).

## <a name="prerequisites"></a>Vorraussetzungen
 Zum Durchführen dieser exemplarischen Vorgehensweise benötigen Sie die folgenden Komponenten:

-   [!INCLUDE[vsto_vsprereq](../vsto/includes/vsto-vsprereq-md.md)]

-   [!INCLUDE[Excel_15_short](../vsto/includes/excel-15-short-md.md)] oder [!INCLUDE[Excel_14_short](../vsto/includes/excel-14-short-md.md)].

## <a name="create-the-project"></a>Erstellen eines Projekts
 In diesem Schritt erstellen Sie ein Excel-Workbook-Projekt mit Visual Studio.

### <a name="to-create-a-new-project"></a>So erstellen Sie ein neues Projekt

1.  Erstellen Sie ein Excel-Workbook-Projekt mit dem Namen **meine Excel-Formatierung**. Stellen Sie sicher, dass **ein neues Dokument erstellen** ausgewählt ist. Weitere Informationen finden Sie unter [Vorgehensweise: Erstellen von Office-Projekten in Visual Studio](../vsto/how-to-create-office-projects-in-visual-studio.md).

     Visual Studio öffnet die neue Excel-Arbeitsmappe im Designer und fügt die **meine Excel-Formatierung** Projekt **Projektmappen-Explorer**.

## <a name="add-text-and-controls-to-the-worksheet"></a>Hinzufügen von Text und Steuerelementen zum Arbeitsblatt
 In dieser exemplarischen Vorgehensweise benötigen Sie drei <xref:Microsoft.Office.Tools.Excel.Controls.CheckBox> Steuerelementen und Text in einem <xref:Microsoft.Office.Tools.Excel.NamedRange> Steuerelement.

### <a name="to-add-three-check-boxes"></a>Drei Kontrollkästchen hinzufügen

1.  Stellen Sie sicher, dass die Arbeitsmappe öffnen in Visual Studio-Designer und die `Sheet1` geöffnet ist.

2.  Aus der **Standardsteuerelementen** Registerkarte die **Toolbox**, ziehen Sie eine <xref:Microsoft.Office.Tools.Excel.Controls.CheckBox> Steuerelement in der Nähe von Zelle **B2** in **Sheet1**.

3.  Von der **Ansicht** , wählen Sie im Menü **Eigenschaften** Fenster.

4.  Achten Sie darauf, **Checkbox1** sichtbar ist, in der im Listenfeld Namen Objekt die **Eigenschaften** Fenster, und ändern Sie die folgenden Eigenschaften:

    |Eigenschaft|Wert|
    |--------------|-----------|
    |**Name**|**applyBoldFont**|
    |**Text**|**Fett**|

5.  Ziehen Sie ein zweites Kontrollkästchen auf oder neben der Zelle **B4** , und ändern Sie die folgenden Eigenschaften:

    |Eigenschaft|Wert|
    |--------------|-----------|
    |**Name**|**applyItalicFont**|
    |**Text**|**Kursiv**|

6.  Ziehen Sie ein drittes Kontrollkästchen auf oder neben der Zelle **B6** , und ändern Sie die folgenden Eigenschaften:

    |Eigenschaft|Wert|
    |--------------|-----------|
    |**Name**|**applyUnderlineFont**|
    |**Text**|**Underline**|

7.  Wählen Sie alle drei Kontrollkästchen-Steuerelemente, indem Sie bei gedrückter der **STRG** Schlüssel.

8.  Klicken Sie in der Gruppe anordnen von der Registerkarte "Format" in Excel auf **ausrichten**, und klicken Sie dann auf **linksbündig**.

     Die drei Kontrollkästchen-Steuerelemente werden auf der linken Seite, an der Position des ersten Steuerelements ausgerichtet, die Sie ausgewählt haben.

     Ziehen Sie als Nächstes werden ein <xref:Microsoft.Office.Tools.Excel.NamedRange> Steuerelement in das Arbeitsblatt.

    > [!NOTE]
    >  Sie können auch hinzufügen der <xref:Microsoft.Office.Tools.Excel.NamedRange> Steuerelement durch Eingabe **Name TextFont** in die **Namen** Feld.

#### <a name="to-add-text-to-a-namedrange-control"></a>Hinzufügen von Text an ein NamedRange-Steuerelement

1. Von der **Excel-Steuerelemente** Registerkarte der Toolbox, ziehen Sie eine <xref:Microsoft.Office.Tools.Excel.NamedRange> -Steuerelement zur Zelle **B9**.

2. Überprüfen Sie, ob **$B$ 9** wird in der editierbares Textfeld, und dieser Zelle **B9** ausgewählt ist. Wenn sie nicht der Fall ist, klicken Sie auf die Zelle **B9** um es auszuwählen.

3. Klicken Sie auf **OK**.

4. Zelle **B9** wird zu einem Bereich mit dem Namen `NamedRange1`.

    Gibt es dafür keinen sichtbaren Hinweis auf dem Arbeitsblatt aber `NamedRange1` wird in der **Namenfeld** (direkt über dem Arbeitsblatt auf der linken Seite) Wenn Zelle **B9** ausgewählt ist.

5. Achten Sie darauf, **NamedRange1** sichtbar ist, in der im Listenfeld Namen Objekt die **Eigenschaften** Fenster, und ändern Sie die folgenden Eigenschaften:

   |Eigenschaft|Wert|
   |--------------|-----------|
   |**Name**|**textFont**|
   |**Value2**|**Klicken Sie auf das Kontrollkästchen, um die Formatierung von Text zu ändern.**|

   Als Nächstes schreiben Sie den Code, um den Text zu formatieren, wenn eine Option ausgewählt ist.

## <a name="format-the-text-when-an-option-is-selected"></a>Formatieren Sie den Text ein, wenn eine Option ausgewählt ist
 In diesem Abschnitt werden Sie Code schreiben, sodass Wenn der Benutzer eine Formatierungsoption aus auswählt, die das Format des Texts im Arbeitsblatt geändert wird.

### <a name="to-change-formatting-when-a-check-box-is-selected"></a>Zum Ändern der Formatierung, wenn das Kontrollkästchen aktiviert ist

1.  Mit der rechten Maustaste **Sheet1**, und klicken Sie dann auf **Ansichtscode** im Kontextmenü auf.

2.  Fügen Sie den folgenden Code der <xref:System.Windows.Forms.Control.Click> -Ereignishandler von dem `applyBoldFont` Kontrollkästchen:

     [!code-vb[Trin_VstcoreProgrammingControlsExcel#7](../vsto/codesnippet/VisualBasic/my excel chart/Sheet1.vb#7)]
     [!code-csharp[Trin_VstcoreProgrammingControlsExcel#7](../vsto/codesnippet/CSharp/Trin_VstcoreProgrammingControlsExcelCS/Sheet1.cs#7)]

3.  Fügen Sie den folgenden Code der <xref:System.Windows.Forms.Control.Click> -Ereignishandler von dem `applyItalicFont` Kontrollkästchen:

     [!code-vb[Trin_VstcoreProgrammingControlsExcel#8](../vsto/codesnippet/VisualBasic/my excel chart/Sheet1.vb#8)]
     [!code-csharp[Trin_VstcoreProgrammingControlsExcel#8](../vsto/codesnippet/CSharp/Trin_VstcoreProgrammingControlsExcelCS/Sheet1.cs#8)]

4.  Fügen Sie den folgenden Code der <xref:System.Windows.Forms.Control.Click> -Ereignishandler von dem `applyUnderlineFont` Kontrollkästchen:

     [!code-vb[Trin_VstcoreProgrammingControlsExcel#9](../vsto/codesnippet/VisualBasic/my excel chart/Sheet1.vb#9)]
     [!code-csharp[Trin_VstcoreProgrammingControlsExcel#9](../vsto/codesnippet/CSharp/Trin_VstcoreProgrammingControlsExcelCS/Sheet1.cs#9)]

5.  In c# müssen Sie Ereignishandler für die Kontrollkästchen zum Hinzufügen der <xref:Microsoft.Office.Tools.Excel.Worksheet.Startup> Ereignis wie unten dargestellt. Informationen zum Erstellen von Ereignishandlern finden Sie unter [Vorgehensweise: Erstellen von Ereignishandlern in Office-Projekten](../vsto/how-to-create-event-handlers-in-office-projects.md).

     [!code-csharp[Trin_VstcoreProgrammingControlsExcel#10](../vsto/codesnippet/CSharp/Trin_VstcoreProgrammingControlsExcelCS/Sheet1.cs#10)]

## <a name="test-the-application"></a>Testen der Anwendung
 Sie können jetzt Testen Ihrer Arbeitsmappe, um sicherzustellen, dass der Text korrekt formatiert ist, wenn Sie aktivieren bzw. Sie das Kontrollkästchen deaktivieren.

### <a name="to-test-your-workbook"></a>So testen Sie die Arbeitsmappe

1.  Drücken Sie **F5** um Ihr Projekt auszuführen.

2.  Aktivieren Sie oder deaktivieren Sie das Kontrollkästchen.

3.  Vergewissern Sie sich, dass der Text korrekt formatiert ist.

## <a name="next-steps"></a>Nächste Schritte
 In dieser exemplarischen Vorgehensweise wird gezeigt, die Grundlagen der Verwendung von Kontrollkästchen, und Formatieren von Text in Excel-Arbeitsblättern. Die folgenden Aufgaben könnten sich daran anschließen:

-   Bereitstellen des Projekts an. Weitere Informationen finden Sie unter [Bereitstellen einer Office-Projektmappe mithilfe von ClickOnce](../vsto/deploying-an-office-solution-by-using-clickonce.md).
-   Verwenden einer Schaltfläche zum Ausfüllen eines Textfeldes. Weitere Informationen finden Sie unter [Exemplarische Vorgehensweise: Anzeigen von Text in einem Textfeld eines Arbeitsblatts mithilfe einer Schaltfläche](../vsto/walkthrough-displaying-text-in-a-text-box-in-a-worksheet-using-a-button.md).

## <a name="see-also"></a>Siehe auch
- [Exemplarische Vorgehensweisen in Excel](../vsto/walkthroughs-using-excel.md)
- [NamedRange-Steuerelement](../vsto/namedrange-control.md)
- [Einschränkungen für Windows Forms-Steuerelemente in Office-Dokumente](../vsto/limitations-of-windows-forms-controls-on-office-documents.md)
