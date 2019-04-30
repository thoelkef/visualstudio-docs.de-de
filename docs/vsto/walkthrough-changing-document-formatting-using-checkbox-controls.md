---
title: 'Exemplarische Vorgehensweise: Ändern der dokumentformatierung mit CheckBox-Steuerelementen'
ms.date: 02/02/2017
ms.topic: conceptual
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- Word documents, changing formatting using controls
- documents [Office development in Visual Studio], formatting
- check boxes, Word documents
- documents [Office development in Visual Studio], check box controls
- controls [Office development in Visual Studio], adding to documents
author: John-Hart
ms.author: johnhart
manager: jillfra
ms.workload:
- office
ms.openlocfilehash: 284b7f501d729a89ff31ab9fee187d3f3e19d4b2
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/23/2019
ms.locfileid: "62982097"
---
# <a name="walkthrough-change-document-formatting-using-checkbox-controls"></a>Exemplarische Vorgehensweise: Ändern der dokumentformatierung mit CheckBox-Steuerelementen
  In dieser exemplarischen Vorgehensweise wird veranschaulicht, wie Windows Forms-Steuerelemente in einer Anpassung auf Dokumentebene für Microsoft Office Word verwendet, um textformatierung zu ändern.

 [!INCLUDE[appliesto_wdalldoc](../vsto/includes/appliesto-wdalldoc-md.md)]

 In dieser exemplarischen Vorgehensweise werden die folgenden Aufgaben veranschaulicht:

- Hinzufügen von Text und ein Steuerelement auf das Dokument in einem Projekt auf Dokumentebene zur Entwurfszeit.

- Formatieren des Texts, wenn eine Option ausgewählt ist.

  Das Ergebnis als vollständiges Beispiel finden Sie unter dem Beispiel des Word-Steuerelemente unter [Office-Entwicklungsbeispiele und exemplarische Vorgehensweisen](../vsto/office-development-samples-and-walkthroughs.md).

  [!INCLUDE[note_settings_general](../sharepoint/includes/note-settings-general-md.md)]

## <a name="prerequisites"></a>Vorraussetzungen
 Zum Durchführen dieser exemplarischen Vorgehensweise benötigen Sie die folgenden Komponenten:

- [!INCLUDE[vsto_vsprereq](../vsto/includes/vsto-vsprereq-md.md)]

- [!INCLUDE[Word_15_short](../vsto/includes/word-15-short-md.md)] oder [!INCLUDE[Word_14_short](../vsto/includes/word-14-short-md.md)].

## <a name="create-the-project"></a>Erstellen eines Projekts
 Im ersten Schritt wird ein Word-Dokumentprojekt erstellt.

### <a name="create-a-new-project"></a>Erstellt ein neues Projekt

1. Erstellen Sie ein Word-Dokumentprojekt mit dem Namen **Meine Word-Formatierung**. Wählen Sie im Assistenten **ein neues Dokument erstellen**.

     Weitere Informationen finden Sie unter [Vorgehensweise: Erstellen von Office-Projekten in Visual Studio](../vsto/how-to-create-office-projects-in-visual-studio.md).

     Visual Studio öffnet das neue Word-Dokument im Designer und fügt die **Meine Word-Formatierung** Projekt **Projektmappen-Explorer**.

## <a name="add-text-and-controls-to-the-word-document"></a>Hinzufügen von Text und Steuerelementen zu Word-Dokument
 In dieser exemplarischen Vorgehensweise fügen Sie drei Kontrollkästchen und Text in einem <xref:Microsoft.Office.Tools.Word.Bookmark> Steuerelement zum Word-Dokument. Die Kontrollkästchen werden Optionen zum Formatieren des Texts für den Benutzer angezeigt.

### <a name="add-three-check-boxes"></a>Fügen Sie drei Kontrollkästchen hinzu.

1. Stellen Sie sicher, dass das Dokument im Visual Studio-Designer geöffnet ist.

2. Von der **Standardsteuerelementen** Registerkarte die **Toolbox**, ziehen Sie das erste <xref:Microsoft.Office.Tools.Word.Controls.CheckBox> Steuerelement auf das Dokument.

3. Ändern Sie im Fenster **Eigenschaften** die folgenden Eigenschaften:

    |Eigenschaft|Wert|
    |--------------|-----------|
    |**Name**|**applyBoldFont**|
    |**Text**|**Fett**|

4. Drücken Sie **EINGABETASTE** zum Verschieben der Einfügemarke ein. unter das erste Kontrollkästchen.

5. Fügen Sie ein zweites Kontrollkästchen für das folgende Dokument die `ApplyBoldFont` Kontrollkästchen, und ändern Sie die folgenden Eigenschaften.

    |Eigenschaft|Wert|
    |--------------|-----------|
    |**Name**|**applyItalicFont**|
    |**Text**|**Kursiv**|

6. Drücken Sie **EINGABETASTE** zum Verschieben der Einfügemarke ein. unter das zweite Kontrollkästchen.

7. Fügen Sie ein drittes Kontrollkästchen für das folgende Dokument die `ApplyItalicFont` Kontrollkästchen, und ändern Sie die folgenden Eigenschaften.

    |Eigenschaft|Wert|
    |--------------|-----------|
    |**Name**|**applyUnderlineFont**|
    |**Text**|**Underline**|

### <a name="add-text-and-a-bookmark-control"></a>Hinzufügen von Text und ein Lesezeichen-Steuerelement

1. Verschieben Sie die Einfügemarke unter dem Kontrollkästchen-Steuerelemente, und geben Sie den folgenden Text:

    **Klicken Sie auf das Kontrollkästchen, um die Formatierung von Text zu ändern.**

2. Von der **Word-Steuerelemente** Registerkarte die **Toolbox**, ziehen Sie eine <xref:Microsoft.Office.Tools.Word.Bookmark> Steuerelement auf das Dokument.

    Die **Lesezeichen-Steuerelement hinzufügen** Dialogfeld wird angezeigt.

3. Wählen Sie den Text, die Sie dem Dokument hinzugefügt, und klicken Sie auf **OK**.

    Ein <xref:Microsoft.Office.Tools.Word.Bookmark> Steuerelement mit dem Namen **Bookmark1** auf den ausgewählten Text im Dokument hinzugefügt wird.

4. In der **Eigenschaften** Fenster, ändern Sie den Wert von der **(Name)** Eigenschaft **FontText.**

   Als Nächstes schreiben Sie den Code, um den Text zu formatieren, wenn das Kontrollkästchen aktiviert oder deaktiviert ist.

## <a name="format-the-text-when-a-check-box-is-checked-or-cleared"></a>Formatieren Sie den Text ein, wenn das Kontrollkästchen aktiviert oder deaktiviert ist
 Wenn der Benutzer eine Formatierungsoption aus auswählt, wird ändern Sie das Format des Texts im Dokument.

### <a name="change-formatting-when-a-check-box-is-selected"></a>Ändern der Formatierung, wenn das Kontrollkästchen aktiviert ist

1. Mit der rechten Maustaste `ThisDocument` in **Projektmappen-Explorer**, und klicken Sie dann auf **Ansichtscode** im Kontextmenü auf.

2. Für C# , fügen Sie die folgenden Konstanten, die **ThisDocument** Klasse.

     [!code-csharp[Trin_VstcoreProgrammingControlsWord#2](../vsto/codesnippet/CSharp/Trin_VstcoreProgrammingControlsWordCS/ThisDocument.cs#2)]

3. Fügen Sie den folgenden Code der <xref:System.Windows.Forms.Control.Click> -Ereignishandler von dem `applyBoldFont` Kontrollkästchen.

     [!code-vb[Trin_VstcoreProgrammingControlsWord#3](../vsto/codesnippet/VisualBasic/my chart options/ThisDocument.vb#3)]
     [!code-csharp[Trin_VstcoreProgrammingControlsWord#3](../vsto/codesnippet/CSharp/Trin_VstcoreProgrammingControlsWordCS/ThisDocument.cs#3)]

4. Fügen Sie den folgenden Code der <xref:System.Windows.Forms.Control.Click> -Ereignishandler von dem `applyItalicFont` Kontrollkästchen.

     [!code-vb[Trin_VstcoreProgrammingControlsWord#4](../vsto/codesnippet/VisualBasic/my chart options/ThisDocument.vb#4)]
     [!code-csharp[Trin_VstcoreProgrammingControlsWord#4](../vsto/codesnippet/CSharp/Trin_VstcoreProgrammingControlsWordCS/ThisDocument.cs#4)]

5. Fügen Sie den folgenden Code der <xref:System.Windows.Forms.Control.Click> -Ereignishandler von dem `applyUnderlineFont` Kontrollkästchen.

     [!code-vb[Trin_VstcoreProgrammingControlsWord#5](../vsto/codesnippet/VisualBasic/my chart options/ThisDocument.vb#5)]
     [!code-csharp[Trin_VstcoreProgrammingControlsWord#5](../vsto/codesnippet/CSharp/Trin_VstcoreProgrammingControlsWordCS/ThisDocument.cs#5)]

6. In C#, müssen Sie Ereignishandler für die Textfelder hinzufügen der <xref:Microsoft.Office.Tools.Word.Document.Startup> Ereignis. Weitere Informationen über das Erstellen von Ereignishandlern finden Sie unter [Vorgehensweise: Erstellen von Ereignishandlern in Office-Projekten](../vsto/how-to-create-event-handlers-in-office-projects.md).

     [!code-csharp[Trin_VstcoreProgrammingControlsWord#6](../vsto/codesnippet/CSharp/Trin_VstcoreProgrammingControlsWordCS/ThisDocument.cs#6)]

## <a name="test-the-application"></a>Testen der Anwendung
 Sie können jetzt testen, dass das Dokument, um sicherzustellen, dass der Text korrekt formatiert ist, wenn Sie aktivieren bzw. Sie das Kontrollkästchen deaktivieren.

### <a name="test-your-document"></a>Testen Sie das Dokument

1. Drücken Sie **F5** um Ihr Projekt auszuführen.

2. Aktivieren Sie oder deaktivieren Sie das Kontrollkästchen.

3. Vergewissern Sie sich, dass der Text korrekt formatiert ist.

## <a name="next-steps"></a>Nächste Schritte
 In dieser exemplarischen Vorgehensweise wird gezeigt, die Grundlagen der Verwendung von Kontrollkästchen und Text-Formatierung in Word-Dokumenten programmgesteuert zu ändern. Die folgenden Aufgaben könnten sich daran anschließen:

- Verwenden Sie eine Schaltfläche, um ein Textfeld zu füllen. Weitere Informationen finden Sie unter [Exemplarische Vorgehensweise: Anzeigen von Text in einem Textfeld in einem Dokument mithilfe einer Schaltfläche](../vsto/walkthrough-displaying-text-in-a-text-box-in-a-document-using-a-button.md).

- Auswählen von Diagrammformaten mithilfe von Optionsfeldern. Weitere Informationen finden Sie unter [Exemplarische Vorgehensweise: Aktualisieren eines Diagramms in einem Dokument mithilfe von Optionsfeldern](../vsto/walkthrough-updating-a-chart-in-a-document-using-radio-buttons.md).

## <a name="see-also"></a>Siehe auch
- [Exemplarische Vorgehensweisen mit Word](../vsto/walkthroughs-using-word.md)
- [Office-Entwicklungsbeispiele und exemplarische Vorgehensweisen](../vsto/office-development-samples-and-walkthroughs.md)
- [NamedRange-Steuerelement](../vsto/namedrange-control.md)
- [Einschränkungen für Windows Forms-Steuerelemente in Office-Dokumente](../vsto/limitations-of-windows-forms-controls-on-office-documents.md)
