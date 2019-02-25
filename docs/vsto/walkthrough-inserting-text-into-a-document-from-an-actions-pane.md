---
title: 'Exemplarische Vorgehensweise: Einfügen von Text in ein Dokument aus einem Aktionsbereich'
ms.date: 02/02/2017
ms.topic: conceptual
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- smart documents [Office development in Visual Studio], creating in Word
- smart documents [Office development in Visual Studio], adding controls
- actions panes [Office development in Visual Studio], creating in Word
- actions panes [Office development in Visual Studio], adding controls
author: John-Hart
ms.author: johnhart
manager: jillfra
ms.workload:
- office
ms.openlocfilehash: 55c5bc57cb419b8614c6c6055a75c633e4012d60
ms.sourcegitcommit: d0425b6b7d4b99e17ca6ac0671282bc718f80910
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 02/21/2019
ms.locfileid: "56634746"
---
# <a name="walkthrough-insert-text-into-a-document-from-an-actions-pane"></a>Exemplarische Vorgehensweise: Einfügen von Text in ein Dokument aus einem Aktionsbereich
  Diese exemplarische Vorgehensweise veranschaulicht, wie ein Bereich "Aktionen" in Microsoft Office Word-Dokument erstellt wird. Der Bereich "Aktionen" enthält zwei Steuerelemente, die Benutzereingaben erfassen, und klicken Sie dann den Text an das Dokument senden.

 [!INCLUDE[appliesto_wdalldoc](../vsto/includes/appliesto-wdalldoc-md.md)]

 In dieser exemplarischen Vorgehensweise werden die folgenden Aufgaben veranschaulicht:

-   Entwerfen Sie eine Schnittstelle, durch die Verwendung von Windows Forms-Steuerelementen in einem Aktionsbereich-Steuerelement.

-   Der Bereich "Aktionen" angezeigt, wenn die Anwendung wird geöffnet.

> [!NOTE]
>  Auf Ihrem Computer werden möglicherweise andere Namen oder Speicherorte für die Benutzeroberflächenelemente von Visual Studio angezeigt als die in den folgenden Anweisungen aufgeführten. Diese Elemente sind von der jeweiligen Visual Studio-Version und den verwendeten Einstellungen abhängig. Weitere Informationen finden Sie unter [Personalisieren von Visual Studio-IDE](../ide/personalizing-the-visual-studio-ide.md).

## <a name="prerequisites"></a>Vorraussetzungen
 Zum Durchführen dieser exemplarischen Vorgehensweise benötigen Sie die folgenden Komponenten:

-   [!INCLUDE[vsto_vsprereq](../vsto/includes/vsto-vsprereq-md.md)]

-   [!INCLUDE[Word_15_short](../vsto/includes/word-15-short-md.md)] oder [!INCLUDE[Word_14_short](../vsto/includes/word-14-short-md.md)].

## <a name="create-the-project"></a>Erstellen eines Projekts
 Im ersten Schritt wird ein Word-Dokumentprojekt erstellt.

### <a name="to-create-a-new-project"></a>So erstellen Sie ein neues Projekt

1.  Erstellen Sie ein Word-Dokumentprojekt mit dem Namen **My Basic Actions Pane**. Wählen Sie im Assistenten **ein neues Dokument erstellen**. Weitere Informationen finden Sie unter [Vorgehensweise: Erstellen von Office-Projekten in Visual Studio](../vsto/how-to-create-office-projects-in-visual-studio.md).

     Visual Studio öffnet das neue Word-Dokument im Designer und fügt die **My Basic Actions Pane** Projekt **Projektmappen-Explorer**.

## <a name="add-text-and-bookmarks-to-the-document"></a>Hinzufügen von Text und Lesezeichen zum Dokument
 Der Bereich "Aktionen" sendet Text zu Lesezeichen im Dokument. Geben Sie Text zum Erstellen eines einfachen Formulars, um das Dokument zu entwerfen.

### <a name="to-add-text-to-your-document"></a>So fügen Sie dem Dokument Text hinzu

1. Geben Sie den folgenden Text in das Word-Dokument:

    **21. März 2008**

    **Name**

    **Address**

    **Dies ist ein Beispiel für eine grundlegende Aktionsbereich in Word.**

   Hinzufügbaren eine <xref:Microsoft.Office.Tools.Word.Bookmark> Steuerelement in Ihr Dokument ziehen Sie es aus der **Toolbox** in Visual Studio oder mithilfe der **Lesezeichen** in Word im Dialogfeld.

### <a name="to-add-a-bookmark-control-to-your-document"></a>So fügen Sie dem Dokument ein Lesezeichen-Steuerelement hinzu

1.  Von der **Word-Steuerelemente** Registerkarte die **Toolbox**, ziehen Sie eine <xref:Microsoft.Office.Tools.Word.Bookmark> -Steuerelement zum Dokument.

     Die **Lesezeichen-Steuerelement hinzufügen** Dialogfeld wird angezeigt.

2.  Wählen Sie das Wort **Namen**, ohne die Absatzmarke, und klicken Sie auf **OK**.

    > [!NOTE]
    >  Die Absatzmarke sollte außerhalb des Lesezeichens. Wenn Absatzmarken nicht im Dokument angezeigt werden, klicken Sie auf die **Tools** Startmenü **Microsoft Office Word-Tools** , und klicken Sie dann auf **Optionen**. Klicken Sie auf die **Ansicht** , und wählen Sie die **Absatzmarken** Kontrollkästchen in der **Formatierungszeichen** Teil der **Optionen** im Dialogfeld.

3.  In der **Eigenschaften** Ändern der **Namen** Eigenschaft **Bookmark1** zu **ShowName**.

4.  Wählen Sie das Wort **Adresse**, ohne die Absatzmarke.

5.  Auf der **einfügen** Registerkarte des Menübands in die **Links** auf **Lesezeichen**.

6.  In der **Lesezeichen** (Dialogfeld), Typ **Lesezeichenname** in die **Lesezeichennamen** ein, und klicken Sie auf **hinzufügen**.

## <a name="add-controls-to-the-actions-pane"></a>Hinzufügen von Steuerelementen im Aktionsbereich
 Informationen zum Entwerfen der Benutzeroberfläche von Aktionsbereichen fügen Sie ein Aktionsbereich-Steuerelements zum Projekt hinzu, und fügen Sie dann auf das Aktionsbereich-Steuerelement Windows Forms-Steuerelemente hinzu.

### <a name="to-add-an-actions-pane-control"></a>Hinzufügen ein Aktionsbereich-Steuerelements

1.  Wählen Sie die **My Basic Actions Pane** Projekt **Projektmappen-Explorer**.

2.  Klicken Sie im Menü **Projekt** auf **Neues Element hinzufügen**.

3.  In der **neues Element hinzufügen** Dialogfeld klicken Sie auf **Aktionsbereich-Steuerelements**, benennen Sie das Steuerelement **InsertTextControl** , und klicken Sie auf **hinzufügen**.

#### <a name="to-add-windows-form-controls-to-the-actions-pane-control"></a>Windows Form-Steuerelemente das Aktionsbereich-Steuerelement hinzu

1.  Wenn das Aktionsbereich-Steuerelement nicht im Designer sichtbar ist, doppelklicken Sie auf **InsertTextControl**.

2.  Aus der **Standardsteuerelementen** Registerkarte die **Toolbox**, ziehen Sie eine **Bezeichnung** Steuerelement, das Aktionsbereich-Steuerelement.

3.  Ändern der **Text** -Eigenschaft des Label-Steuerelements in **Namen**.

4.  Hinzufügen einer **Textfeld** die Steuerung an das Aktionsbereich-Steuerelement, und ändern Sie die folgenden Eigenschaften.

    |Eigenschaft|Wert|
    |--------------|-----------|
    |**Name**|**getName**|
    |**Size**|**130, 20**|

5.  Fügen Sie eine zweite **Bezeichnung** die Steuerung an das Aktionsbereich-Steuerelement, und ändern Sie die **Text** Eigenschaft **Adresse**.

6.  Fügen Sie eine zweite **Textfeld** die Steuerung an das Aktionsbereich-Steuerelement, und ändern Sie die folgenden Eigenschaften.

    |Eigenschaft|Wert|
    |--------------|-----------|
    |**Name**|**getAddress**|
    |**Rückgabe akzeptiert**|**True**|
    |**Multiline**|**True**|
    |**Size**|**130, 40**|

7.  Hinzufügen einer **Schaltfläche** die Steuerung an das Aktionsbereich-Steuerelement, und ändern Sie die folgenden Eigenschaften.

    |Eigenschaft|Wert|
    |--------------|-----------|
    |**Name**|**addText**|
    |**Text**|**Einfügen**|

## <a name="add-code-to-insert-text-into-the-document"></a>Hinzufügen von Code zum Einfügen von Text in das Dokument
 Klicken Sie im Bereich "Aktionen" Code schreiben, der den Text aus den Textfeldern in die entsprechenden fügt <xref:Microsoft.Office.Tools.Word.Bookmark> Steuerelemente im Dokument. Sie können die `Globals` Klasse, um die Steuerelemente im Aktionsbereich Steuerelemente im Dokument zugreifen. Weitere Informationen finden Sie unter [Global den Zugriff auf Objekte in Office-Projekten](../vsto/global-access-to-objects-in-office-projects.md).

### <a name="to-insert-text-from-the-actions-pane-in-a-bookmark-in-the-document"></a>Zum Einfügen von Text aus dem Aktionsbereich "in einem Lesezeichen im Dokument

1.  Fügen Sie den folgenden Code der <xref:System.Windows.Forms.Control.Click> -Ereignishandler von dem **AddText** Schaltfläche.

     [!code-csharp[Trin_VstcoreActionsPaneWord#8](../vsto/codesnippet/CSharp/Trin_VstcoreActionsPaneWordCS/InsertTextControl.cs#8)]
     [!code-vb[Trin_VstcoreActionsPaneWord#8](../vsto/codesnippet/VisualBasic/Trin_VstcoreActionsPaneWordVB/InsertTextControl.vb#8)]

2.  In c# müssen Sie einen Ereignishandler für das Schaltflächen-Klickereignis hinzufügen. Sie können diesen Code in Platzieren der `InsertTextControl` Konstruktor nach dem Aufruf von `InitializeComponent`. Informationen zum Erstellen von Ereignishandlern finden Sie unter [Vorgehensweise: Erstellen von Ereignishandlern in Office-Projekten](../vsto/how-to-create-event-handlers-in-office-projects.md).

     [!code-csharp[Trin_VstcoreActionsPaneWord#9](../vsto/codesnippet/CSharp/Trin_VstcoreActionsPaneWordCS/InsertTextControl.cs#9)]

## <a name="add-code-to-show-the-actions-pane"></a>Hinzufügen von Code zum Anzeigen der Bereich "Aktionen"
 Um den Bereich "Aktionen" anzuzeigen, fügen Sie das Steuerelement, das Sie erstellt haben hinzu, das der steuerelementauflistung.

### <a name="to-show-the-actions-pane"></a>Der Bereich "Aktionen" angezeigt.

1.  Erstellen Sie eine neue Instanz der Aktionsbereich-Steuerelements in der `ThisDocument` Klasse.

     [!code-csharp[Trin_VstcoreActionsPaneWord#10](../vsto/codesnippet/CSharp/Trin_VstcoreActionsPaneWordCS/ThisDocument.cs#10)]
     [!code-vb[Trin_VstcoreActionsPaneWord#10](../vsto/codesnippet/VisualBasic/Trin_VstcoreActionsPaneWordVB/ThisDocument.vb#10)]

2.  Fügen Sie den folgenden Code der <xref:Microsoft.Office.Tools.Word.Document.Startup> -Ereignishandler des `ThisDocument`.

     [!code-csharp[Trin_VstcoreActionsPaneWord#11](../vsto/codesnippet/CSharp/Trin_VstcoreActionsPaneWordCS/ThisDocument.cs#11)]
     [!code-vb[Trin_VstcoreActionsPaneWord#11](../vsto/codesnippet/VisualBasic/Trin_VstcoreActionsPaneWordVB/ThisDocument.vb#11)]

## <a name="test-the-application"></a>Testen der Anwendung
 Testen Sie das Dokument, um sicherzustellen, dass der Bereich "Aktionen" wird geöffnet, wenn das Dokument geöffnet ist, dass Text in die Textfelder eingegebenen in die Lesezeichen eingefügt wird, wenn auf die Schaltfläche geklickt wird.

### <a name="to-test-your-document"></a>So testen Sie das Dokument

1.  Drücken Sie **F5** um Ihr Projekt auszuführen.

2.  Vergewissern Sie sich, dass der Bereich "Aktionen" angezeigt wird.

3.  Geben Sie Ihren Namen und Adresse in die Textfelder für den Bereich "Aktionen", und klicken Sie auf **einfügen**.

## <a name="next-steps"></a>Nächste Schritte
 Die folgenden Aufgaben könnten sich daran anschließen:

-   Erstellen Sie einen Aktionsbereich in Excel. Weitere Informationen finden Sie unter [Vorgehensweise: Hinzufügen eines Aktionsbereichs zu Excel-Arbeitsmappen](/previous-versions/visualstudio/visual-studio-2010/e3zbk0hz(v=vs.100)).

-   Binden Sie Daten an Steuerelemente in einem Aktionsbereich an. Weitere Informationen finden Sie unter [Exemplarische Vorgehensweise: Binden von Daten an Steuerelemente in einem Word-Aktionsbereich](../vsto/walkthrough-binding-data-to-controls-on-a-word-actions-pane.md).

## <a name="see-also"></a>Siehe auch
- [Übersicht über den Aktionsbereich](../vsto/actions-pane-overview.md)
- [Vorgehensweise: Hinzufügen eines Aktionsbereichs zu Word-Dokumenten oder Excel-Arbeitsmappen](../vsto/how-to-add-an-actions-pane-to-word-documents-or-excel-workbooks.md)
- [Vorgehensweise: Hinzufügen eines Aktionsbereichs zu Excel-Arbeitsmappen](/previous-versions/visualstudio/visual-studio-2010/e3zbk0hz(v=vs.100))
- [Vorgehensweise: Verwalten des Steuerelementlayouts in Aktionsbereichen](../vsto/how-to-manage-control-layout-on-actions-panes.md)
- [Bookmark-Steuerelement](../vsto/bookmark-control.md)
