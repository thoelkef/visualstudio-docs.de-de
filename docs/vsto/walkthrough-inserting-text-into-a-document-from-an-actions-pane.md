---
title: 'Exemplarische Vorgehensweise: Einfügen von Text in ein Dokument aus einem Aktionsbereich | Microsoft Docs'
ms.custom: ''
ms.date: 02/02/2017
ms.technology:
- office-development
ms.topic: conceptual
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- smart documents [Office development in Visual Studio], creating in Word
- smart documents [Office development in Visual Studio], adding controls
- actions panes [Office development in Visual Studio], creating in Word
- actions panes [Office development in Visual Studio], adding controls
author: TerryGLee
ms.author: tglee
manager: douge
ms.workload:
- office
ms.openlocfilehash: 9e562f66dd43b4adc45727c8de1457a24ddf97b3
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/16/2018
---
# <a name="walkthrough-inserting-text-into-a-document-from-an-actions-pane"></a>Exemplarische Vorgehensweise: Einfügen von Text in ein Dokument aus einem Aktionsbereich
  Diese exemplarische Vorgehensweise veranschaulicht, wie einen Aktionsbereich in Microsoft Office Word-Dokument erstellt wird. Der Aktionsbereich enthält zwei Steuerelemente, die Benutzereingaben erfassen und senden Sie den Text zum Dokument.  
  
 [!INCLUDE[appliesto_wdalldoc](../vsto/includes/appliesto-wdalldoc-md.md)]  
  
 In dieser exemplarischen Vorgehensweise werden die folgenden Aufgaben veranschaulicht:  
  
-   Entwerfen eine Schnittstelle, mithilfe von Windows Forms-Steuerelemente in einem Aktionsbereich-Steuerelement.  
  
-   Anzeigen des Aktionsbereichs, wenn die Anwendung geöffnet wird.  
  
> [!NOTE]  
>  Auf Ihrem Computer werden möglicherweise andere Namen oder Speicherorte für die Benutzeroberflächenelemente von Visual Studio angezeigt als die in den folgenden Anweisungen aufgeführten. Diese Elemente sind von der jeweiligen Visual Studio-Version und den verwendeten Einstellungen abhängig. Weitere Informationen finden Sie unter [Personalisieren von Visual Studio-IDE](../ide/personalizing-the-visual-studio-ide.md).  
  
## <a name="prerequisites"></a>Erforderliche Komponenten  
 Zum Durchführen dieser exemplarischen Vorgehensweise benötigen Sie die folgenden Komponenten:  
  
-   [!INCLUDE[vsto_vsprereq](../vsto/includes/vsto-vsprereq-md.md)]  
  
-   [!INCLUDE[Word_15_short](../vsto/includes/word-15-short-md.md)] oder [!INCLUDE[Word_14_short](../vsto/includes/word-14-short-md.md)].  
  
## <a name="creating-the-project"></a>Erstellen des Projekts  
 Im ersten Schritt wird ein Word-Dokumentprojekt erstellt.  
  
#### <a name="to-create-a-new-project"></a>So erstellen Sie ein neues Projekt  
  
1.  Erstellen Sie ein Word-Dokumentprojekt mit dem Namen **Meine grundlegenden Aktionsbereich**. Wählen Sie im Assistenten **erstellen Sie ein neues Dokument**. Weitere Informationen finden Sie unter [How to: Create Office Projects in Visual Studio](../vsto/how-to-create-office-projects-in-visual-studio.md).  
  
     Visual Studio öffnet das neue Word-Dokument im Designer und fügt die **Meine grundlegenden Aktionsbereich** Projekt **Projektmappen-Explorer**.  
  
## <a name="adding-text-and-bookmarks-to-the-document"></a>Hinzufügen von Text und Lesezeichen zum Dokument  
 Der Aktionsbereich sendet Text an Lesezeichen im Dokument. Um das Dokument entwerfen, geben Sie Text um ein einfaches Formular zu erstellen.  
  
#### <a name="to-add-text-to-your-document"></a>So fügen Sie dem Dokument Text hinzu  
  
1.  Geben Sie den folgenden Text in Word-Dokument:  
  
     **Am 21. März 2008**  
  
     **Name**  
  
     **Adresse**  
  
     **Dies ist ein Beispiel für einen einfachen Aktionsbereich in Word.**  
  
 Können Sie hinzufügen, eine <xref:Microsoft.Office.Tools.Word.Bookmark> -Steuerelement zum Dokument durch Ziehen von der **Toolbox** in Visual Studio oder mithilfe der **Lesezeichen** in Word im Dialogfeld.  
  
#### <a name="to-add-a-bookmark-control-to-your-document"></a>So fügen Sie dem Dokument ein Lesezeichen-Steuerelement hinzu  
  
1.  Aus der **Word-Steuerelemente** auf der Registerkarte die **Toolbox**, ziehen Sie eine <xref:Microsoft.Office.Tools.Word.Bookmark> -Steuerelement zum Dokument.  
  
     Die **Lesezeichen-Steuerelement hinzufügen** Dialogfeld wird angezeigt.  
  
2.  Wählen Sie das Wort **Namen**, ohne die Absatzmarke, und klicken Sie auf **OK**.  
  
    > [!NOTE]  
    >  Die Absatzmarke sollte außerhalb der Textmarke sein. Wenn Absatzmarken nicht im Dokument angezeigt werden, klicken Sie auf die **Tools** Sie im Menü **Microsoft Office Word-Tools** , und klicken Sie dann auf **Optionen**. Klicken Sie auf die **Ansicht** , und wählen Sie die **Absatzmarken** Kontrollkästchen in der **Formatierungszeichen** Teil der **Optionen** (Dialogfeld).  
  
3.  In der **Eigenschaften** Ändern der **Namen** Eigenschaft **Bookmark1** auf **ShowName**.  
  
4.  Wählen Sie das Wort **Adresse**, ohne die Absatzmarke.  
  
5.  Auf der **einfügen** Registerkarte des Menübands in die **Links** zu gruppieren, klicken Sie auf **Lesezeichen**.  
  
6.  In der **Lesezeichen** Geben Sie im Dialogfeld **Lesezeichenname** in der **Name des Lesezeichens** Feld, und klicken Sie auf **hinzufügen**.  
  
## <a name="adding-controls-to-the-actions-pane"></a>Hinzufügen von Steuerelementen zum Aktionsbereich  
 Um die Benutzeroberfläche von Aktionsbereichen zu entwerfen, dem Projekt einen Aktionsbereich-Steuerelement hinzugefügt, und klicken Sie dann Windows Forms-Steuerelemente zum Aktionsbereich-Steuerelement hinzufügen.  
  
#### <a name="to-add-an-actions-pane-control"></a>So fügen Sie einem Aktionsbereich-Steuerelement hinzu  
  
1.  Wählen Sie die **Meine grundlegenden Aktionsbereich** Projekt **Projektmappen-Explorer**.  
  
2.  Klicken Sie im Menü **Projekt** auf **Neues Element hinzufügen**.  
  
3.  In der **neues Element hinzufügen** (Dialogfeld), klicken Sie auf **Aktionsbereich-Steuerelement**, benennen Sie das Steuerelement **InsertTextControl** , und klicken Sie auf **hinzufügen**.  
  
#### <a name="to-add-windows-form-controls-to-the-actions-pane-control"></a>Der Aktionsbereich-Steuerelement Windows Forms-Steuerelemente hinzu  
  
1.  Wenn der Aktionsbereich-Steuerelement nicht im Designer sichtbar ist, doppelklicken Sie auf **InsertTextControl**.  
  
2.  Aus der **Standardsteuerelementen** auf der Registerkarte die **Toolbox**, ziehen Sie eine **Bezeichnung** Steuerelement, um den Aktionsbereich-Steuerelement.  
  
3.  Ändern der **Text** Eigenschaft des Label-Steuerelements in **Namen**.  
  
4.  Hinzufügen einer **Textfeld** die Steuerung an den Aktionsbereich-Steuerelement, und ändern Sie die folgenden Eigenschaften.  
  
    |Eigenschaft|Wert|  
    |--------------|-----------|  
    |**Name**|**getName**|  
    |**Size**|**130, 20**|  
  
5.  Fügen Sie eine zweite **Bezeichnung** die Steuerung an den Aktionsbereich-Steuerelement, und ändern Sie die **Text** Eigenschaft **Adresse**.  
  
6.  Fügen Sie eine zweite **Textfeld** die Steuerung an den Aktionsbereich-Steuerelement, und ändern Sie die folgenden Eigenschaften.  
  
    |Eigenschaft|Wert|  
    |--------------|-----------|  
    |**Name**|**GetAddress**|  
    |**Akzeptiert die EINGABETASTE**|**True**|  
    |**Multiline**|**True**|  
    |**Size**|**130, 40**|  
  
7.  Hinzufügen einer **Schaltfläche** die Steuerung an den Aktionsbereich-Steuerelement, und ändern Sie die folgenden Eigenschaften.  
  
    |Eigenschaft|Wert|  
    |--------------|-----------|  
    |**Name**|**addText**|  
    |**Text**|**Einfügen**|  
  
## <a name="adding-code-to-insert-text-into-the-document"></a>Hinzufügen von Code zum Einfügen von Text in das Dokument  
 Klicken Sie im Bereich "Aktionen" Code schreiben, der den Text in den Textfeldern in die entsprechenden fügt <xref:Microsoft.Office.Tools.Word.Bookmark> Steuerelemente im Dokument. Sie können die `Globals` Klasse, um die Steuerelemente im Aktionsbereich Steuerelemente im Dokument zuzugreifen. Weitere Informationen finden Sie unter [globaler Zugriff auf Objekte in Office-Projekten](../vsto/global-access-to-objects-in-office-projects.md).  
  
#### <a name="to-insert-text-from-the-actions-pane-in-a-bookmark-in-the-document"></a>Zum Einfügen von Text aus dem Aktionsbereich "in einem Lesezeichen im Dokument  
  
1.  Fügen Sie folgenden Code, der <xref:System.Windows.Forms.Control.Click> -Ereignishandler des der **AddText** Schaltfläche.  
  
     [!code-csharp[Trin_VstcoreActionsPaneWord#8](../vsto/codesnippet/CSharp/Trin_VstcoreActionsPaneWordCS/InsertTextControl.cs#8)]
     [!code-vb[Trin_VstcoreActionsPaneWord#8](../vsto/codesnippet/VisualBasic/Trin_VstcoreActionsPaneWordVB/InsertTextControl.vb#8)]  
  
2.  In c# müssen Sie einen Ereignishandler für das Schaltflächen-Klickereignis hinzufügen. Sie können diesen Code im Platzieren der `InsertTextControl` Konstruktor nach dem Aufruf von `IntializeComponent`. Informationen zum Erstellen von Ereignishandlern finden Sie unter [Vorgehensweise: Erstellen von Ereignishandlern in Office-Projekten](../vsto/how-to-create-event-handlers-in-office-projects.md).  
  
     [!code-csharp[Trin_VstcoreActionsPaneWord#9](../vsto/codesnippet/CSharp/Trin_VstcoreActionsPaneWordCS/InsertTextControl.cs#9)]  
  
## <a name="adding-code-to-show-the-actions-pane"></a>Hinzufügen von Code zum Aktionsbereich anzeigen  
 Um den Aktionsbereich anzuzeigen, fügen Sie das Steuerelement, das Sie erstellt haben, die Control-Auflistung hinzu.  
  
#### <a name="to-show-the-actions-pane"></a>Um den Aktionsbereich anzuzeigen  
  
1.  Erstellen Sie eine neue Instanz der Aktionsbereich-Steuerelement in der `ThisDocument` Klasse.  
  
     [!code-csharp[Trin_VstcoreActionsPaneWord#10](../vsto/codesnippet/CSharp/Trin_VstcoreActionsPaneWordCS/ThisDocument.cs#10)]
     [!code-vb[Trin_VstcoreActionsPaneWord#10](../vsto/codesnippet/VisualBasic/Trin_VstcoreActionsPaneWordVB/ThisDocument.vb#10)]  
  
2.  Fügen Sie folgenden Code, der <xref:Microsoft.Office.Tools.Word.Document.Startup> -Ereignishandler des `ThisDocument`.  
  
     [!code-csharp[Trin_VstcoreActionsPaneWord#11](../vsto/codesnippet/CSharp/Trin_VstcoreActionsPaneWordCS/ThisDocument.cs#11)]
     [!code-vb[Trin_VstcoreActionsPaneWord#11](../vsto/codesnippet/VisualBasic/Trin_VstcoreActionsPaneWordVB/ThisDocument.vb#11)]  
  
## <a name="testing-the-application"></a>Testen der Anwendung  
 Testen Sie das Dokument, um sicherzustellen, dass der Aktionsbereich wird geöffnet, wenn das Dokument geöffnet ist und, dass Text in die Textfelder eingegeben haben in der Textmarke eingefügt wird, auf die Schaltfläche geklickt wird.  
  
#### <a name="to-test-your-document"></a>So testen Sie das Dokument  
  
1.  Drücken Sie F5, um das Projekt auszuführen.  
  
2.  Vergewissern Sie sich, dass der Aktionsbereich sichtbar ist.  
  
3.  Geben Sie Ihren Namen und die Adresse in die Textfelder in einem Aktionsbereich, und klicken Sie auf **einfügen**.  
  
## <a name="next-steps"></a>Nächste Schritte  
 Die folgenden Aufgaben könnten sich daran anschließen:  
  
-   Erstellen einen Aktionsbereich in Excel. Weitere Informationen finden Sie unter [wie: Hinzufügen eines Aktionsbereichs zu Excel-Arbeitsmappen](http://msdn.microsoft.com/en-us/62abfce6-e44f-419d-85d8-26bf59f33872).  
  
-   Binden von Daten an Steuerelemente in einem Aktionsbereich. Weitere Informationen finden Sie unter [Exemplarische Vorgehensweise: Binden von Daten an Steuerelemente in einem Word-Aktionsbereich](../vsto/walkthrough-binding-data-to-controls-on-a-word-actions-pane.md).  
  
## <a name="see-also"></a>Siehe auch  
 [Aktionsbereichsübersicht](../vsto/actions-pane-overview.md)   
 [Vorgehensweise: Hinzufügen eines Aktionsbereichs zu Word-Dokumenten oder Excel-Arbeitsmappen](../vsto/how-to-add-an-actions-pane-to-word-documents-or-excel-workbooks.md)   
 [Vorgehensweise: Hinzufügen eines Aktionsbereichs zu Excel-Arbeitsmappen](http://msdn.microsoft.com/en-us/62abfce6-e44f-419d-85d8-26bf59f33872)   
 [Vorgehensweise: Verwalten des Steuerelementlayouts in Aktionsbereichen](../vsto/how-to-manage-control-layout-on-actions-panes.md)   
 [Bookmark-Steuerelement](../vsto/bookmark-control.md)  
  
  