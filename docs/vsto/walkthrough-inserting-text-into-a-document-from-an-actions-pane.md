---
title: "Exemplarische Vorgehensweise: Einf&#252;gen von Text in ein Dokument aus einem Aktionsbereich | Microsoft Docs"
ms.custom: ""
ms.date: "02/02/2017"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "office-development"
ms.tgt_pltfrm: ""
ms.topic: "article"
dev_langs: 
  - "VB"
  - "CSharp"
helpviewer_keywords: 
  - "Aktionsbereiche [Office-Entwicklung in Visual Studio], Hinzufügen von Steuerelementen"
  - "Aktionsbereiche [Office-Entwicklung in Visual Studio], Erstellen in Word"
  - "SmartDocuments [Office-Entwicklung in Visual Studio], Hinzufügen von Steuerelementen"
  - "SmartDocuments [Office-Entwicklung in Visual Studio], Erstellen in Word"
ms.assetid: fd14c896-5737-4a20-94f7-6064b67112c5
caps.latest.revision: 70
author: "kempb"
ms.author: "kempb"
manager: "ghogen"
caps.handback.revision: 69
---
# Exemplarische Vorgehensweise: Einf&#252;gen von Text in ein Dokument aus einem Aktionsbereich
  In dieser exemplarischen Vorgehensweise wird die Erstellung eines Aktionsbereichs in einem Microsoft Office Word 2003\-Dokument veranschaulicht.  Der Aktionsbereich enthält zwei Steuerelemente, die Benutzereingaben erfassen und den Text dann an das Dokument senden.  
  
 [!INCLUDE[appliesto_wdalldoc](../vsto/includes/appliesto-wdalldoc-md.md)]  
  
 In dieser exemplarischen Vorgehensweise werden die folgenden Aufgaben veranschaulicht:  
  
-   Entwerfen einer Schnittstelle mithilfe von Windows Forms\-Steuerelementen auf einem Aktionsbereich\-Steuerelement  
  
-   Anzeigen des Aktionsbereichs, wenn die Anwendung geöffnet wird  
  
> [!NOTE]  
>  Auf Ihrem Computer werden möglicherweise andere Namen oder Speicherorte für die Benutzeroberflächenelemente von Visual Studio angezeigt als die in den folgenden Anweisungen aufgeführten.  Die von Ihnen verwendete Visual Studio\-Edition und die Einstellungen legen diese Elemente fest.  Weitere Informationen finden Sie unter [Customizing Development Settings in Visual Studio](http://msdn.microsoft.com/de-de/22c4debb-4e31-47a8-8f19-16f328d7dcd3).  
  
## Vorbereitungsmaßnahmen  
 Zum Durchführen dieser exemplarischen Vorgehensweise benötigen Sie die folgenden Komponenten:  
  
-   [!INCLUDE[vsto_vsprereq](../vsto/includes/vsto-vsprereq-md.md)]  
  
-   [!INCLUDE[Word_15_short](../vsto/includes/word-15-short-md.md)] oder [!INCLUDE[Word_14_short](../vsto/includes/word-14-short-md.md)].  
  
## Erstellen des Projekts  
 Der erste Schritt besteht darin, ein Word\-Dokumentprojekt zu erstellen.  
  
#### So erstellen Sie ein neues Projekt  
  
1.  Erstellen Sie ein Word\-Dokumentprojekt mit dem Namen My Basic Actions Pane.  Wählen Sie im Assistenten **Neues Dokument erstellen** aus.  Weitere Informationen finden Sie unter [Gewusst wie: Erstellen von Office-Projekten in Visual Studio](../vsto/how-to-create-office-projects-in-visual-studio.md).  
  
     Visual Studio wird das neue Word\-Dokument im Designer öffnet, und im **Projektmappen\-Explorer** wird das Projekt **My Basic Actions Pane** hinzugefügt.  
  
## Hinzufügen von Text und Lesezeichen im Dokument  
 Der Aktionsbereich sendet Text an Lesezeichen im Dokument.  Wenn Sie ein Dokument entwerfen möchten, geben Sie einen kurzen Text ein, um ein einfaches Formular zu erstellen.  
  
#### So fügen Sie dem Dokument Text hinzu  
  
1.  Geben Sie im Word\-Dokument folgenden Text ein:  
  
     March 21, 2008  
  
     Name  
  
     Adresse  
  
     **Dies ist ein Beispiel für einen einfachen Aktionsbereich in Word.**  
  
 Sie können dem Dokument ein <xref:Microsoft.Office.Tools.Word.Bookmark>\-Steuerelement hinzufügen, indem Sie es in Visual Studio aus der **Toolbox** ziehen oder indem Sie in Word das Dialogfeld **Lesezeichen** verwenden.  
  
#### So fügen Sie dem Dokument ein Lesezeichen\-Steuerelement hinzu  
  
1.  Ziehen Sie von der Registerkarte **Word\-Steuerelemente** der **Toolbox** ein <xref:Microsoft.Office.Tools.Word.Bookmark>\-Steuerelement zum Dokument.  
  
     Das Dialogfeld **Lesezeichen\-Steuerelement hinzufügen** wird angezeigt.  
  
2.  Markieren Sie das Wort **Name** ohne die Absatzmarke, und klicken Sie auf **OK**.  
  
    > [!NOTE]  
    >  Die Absatzmarke sollte nicht im Lesezeichen enthalten sein.  Wenn die Absatzmarken nicht im Dokument angezeigt werden, klicken Sie auf das Menü **Extras**, zeigen auf **Microsoft Office Word\-Tools** und klicken dann auf **Optionen**.  Klicken Sie auf die Registerkarte **Ansicht**, und markieren Sie im Dialogfeld **Optionen** im Bereich **Formatierungszeichen** das Kontrollkästchen **Absatzmarken**.  
  
3.  Ändern Sie im **Eigenschaftenfenster** die **Name**\-Eigenschaft von **Bookmark1** in **showName**.  
  
4.  Markieren Sie das Wort **Address** ohne die Absatzmarke.  
  
5.  Klicken Sie auf der Registerkarte **Einfügen** des Menübands in der Gruppe **Links** auf **Lesezeichen**.  
  
6.  Im Dialogfeld **Lesezeichen** geben Sie im Feld **LesezeichennameshowAddress** ein und klicken auf **Hinzufügen**.  
  
## Hinzufügen von Steuerelementen zum Aktionsbereich  
 Um die Benutzeroberfläche von Aktionsbereichen zu entwerfen, fügen Sie ein Aktionsbereich\-Steuerelement zum Projekt und anschließend Windows Forms\-Steuerelemente zum Aktionsbereich\-Steuerelement hinzu.  
  
#### So fügen Sie ein Aktionsbereich\-Steuerelement hinzu  
  
1.  Wählen Sie im **Projektmappen\-Explorer** das Projekt **Mein Bereich Grundlegende Aktionen** aus.  
  
2.  Klicken Sie im Menü **Projekt** auf **Neues Element hinzufügen**.  
  
3.  Im Dialogfeld **Neues Element hinzufügen** klicken Sie auf **Aktionsbereich\-Steuerelement**, bezeichnen das Steuerelement **InsertTextControl** und klicken auf **Hinzufügen**.  
  
#### So fügen Sie dem Aktionsbereich\-Steuerelement Windows Form\-Steuerelemente hinzu  
  
1.  Wenn das Aktionsbereich\-Steuerelement im Designer nicht sichtbar ist, doppelklicken Sie auf **InsertTextControl** im Designer.  
  
2.  Ziehen Sie von der Registerkarte **Allgemeine Steuerelemente** der **Toolbox** ein **Label**\-Steuerelement zum Aktionsbereich\-Steuerelement.  
  
3.  Ändern Sie die **Text**\-Eigenschaft des Label\-Steuerelements auf **Name**.  
  
4.  Fügen Sie dem Aktionsbereich\-Steuerelement ein **Textbox**\-Steuerelement hinzu, und ändern Sie die folgenden Eigenschaften.  
  
    |Eigenschaft|Wert|  
    |-----------------|----------|  
    |**Name**|**getName**|  
    |**Größe**|**130, 20**|  
  
5.  Fügen Sie dem Aktionsbereich\-Steuerelement ein zweites **Label**\-Steuerelement hinzu, und ändern Sie die **Text**\-Eigenschaft auf **Address**.  
  
6.  Fügen Sie dem Aktionsbereich\-Steuerelement ein zweites **Textbox**\-Steuerelement hinzu, und ändern Sie die folgenden Eigenschaften.  
  
    |Eigenschaft|Wert|  
    |-----------------|----------|  
    |**Name**|**getAddress**|  
    |**AcceptsReturn**|**True**|  
    |**Multiline**|**True**|  
    |**Größe**|**130, 40**|  
  
7.  Fügen Sie dem Aktionsbereich\-Steuerelement ein **Button**\-Steuerelement hinzu, und ändern Sie die folgenden Eigenschaften.  
  
    |Eigenschaft|Wert|  
    |-----------------|----------|  
    |**Name**|**addText**|  
    |**Text**|**Insert**|  
  
## Hinzufügen von Code, um Text in das Dokument einzufügen  
 Schreiben Sie im Aktionsbereich Code, der Text aus den Textfeldern in die entsprechenden <xref:Microsoft.Office.Tools.Word.Bookmark>\-Steuerelemente des Dokuments einfügt.  Sie können die `Globals`\-Klasse verwenden, um über die Steuerelemente des Aktionsbereichs auf die Steuerelemente im Dokument zuzugreifen.  Weitere Informationen finden Sie unter [Globaler Zugriff auf Objekte in Office-Projekten](../vsto/global-access-to-objects-in-office-projects.md).  
  
#### So fügen Sie Text aus dem Aktionsbereich in ein Lesezeichen im Dokument ein  
  
1.  Fügen Sie den folgenden Code zum <xref:System.Windows.Forms.Control.Click>\-Ereignishandler für die **addText**\-Schaltfläche hinzu.  
  
     [!code-csharp[Trin_VstcoreActionsPaneWord#8](../snippets/csharp/VS_Snippets_OfficeSP/Trin_VstcoreActionsPaneWord/CS/InsertTextControl.cs#8)]
     [!code-vb[Trin_VstcoreActionsPaneWord#8](../snippets/visualbasic/VS_Snippets_OfficeSP/Trin_VstcoreActionsPaneWord/VB/InsertTextControl.vb#8)]  
  
2.  In C\# müssen Sie einen Ereignishandler für Klickereignisse auf Schaltflächen hinzufügen.  Sie können diesen Code nach dem Aufruf von `IntializeComponent` in den `InsertTextControl`\-Konstruktor einfügen.  Weitere Informationen zum Erstellen von Ereignishandlern finden Sie unter [Gewusst wie: Erstellen von Ereignishandlern in Office-Projekten](../vsto/how-to-create-event-handlers-in-office-projects.md).  
  
     [!code-csharp[Trin_VstcoreActionsPaneWord#9](../snippets/csharp/VS_Snippets_OfficeSP/Trin_VstcoreActionsPaneWord/CS/InsertTextControl.cs#9)]  
  
## Hinzufügen von Code, um den Aktionsbereich anzuzeigen  
 Um den Aktionsbereich anzuzeigen, müssen Sie das von Ihnen erstellte Steuerelement zur Steuerelementauflistung hinzufügen.  
  
#### So zeigen Sie den Aktionsbereich an  
  
1.  Erstellen Sie in der `ThisDocument`\-Klasse eine neue Instanz des Aktionsbereich\-Steuerelements.  
  
     [!code-csharp[Trin_VstcoreActionsPaneWord#10](../snippets/csharp/VS_Snippets_OfficeSP/Trin_VstcoreActionsPaneWord/CS/ThisDocument.cs#10)]
     [!code-vb[Trin_VstcoreActionsPaneWord#10](../snippets/visualbasic/VS_Snippets_OfficeSP/Trin_VstcoreActionsPaneWord/VB/ThisDocument.vb#10)]  
  
2.  Fügen Sie dem <xref:Microsoft.Office.Tools.Word.Document.Startup>\-Ereignishandler von `ThisDocument` den folgenden Code hinzu.  
  
     [!code-csharp[Trin_VstcoreActionsPaneWord#11](../snippets/csharp/VS_Snippets_OfficeSP/Trin_VstcoreActionsPaneWord/CS/ThisDocument.cs#11)]
     [!code-vb[Trin_VstcoreActionsPaneWord#11](../snippets/visualbasic/VS_Snippets_OfficeSP/Trin_VstcoreActionsPaneWord/VB/ThisDocument.vb#11)]  
  
## Testen der Anwendung  
 Testen Sie das Dokument, um zu überprüfen, ob der Aktionsbereich nach dem Öffnen des Dokuments geöffnet wird und ob in den Textfeldern eingegebener Text nach dem Klicken auf die entsprechende Schaltfläche in die Lesezeichen eingefügt wird.  
  
#### So testen Sie das Dokument  
  
1.  Drücken Sie F5, um das Projekt auszuführen.  
  
2.  Bestätigen Sie, dass der Aktionsbereich angezeigt wird.  
  
3.  Geben Sie Ihren Namen und Ihre Adresse in die Textfelder im Aktionsbereich ein, und klicken Sie auf **Einfügen**.  
  
## Nächste Schritte  
 Die folgenden Aufgaben könnten sich daran anschließen:  
  
-   Erstellen eines Aktionsbereichs in Excel.  Weitere Informationen finden Sie unter [How to: Add an Actions Pane to Excel Workbooks](http://msdn.microsoft.com/de-de/62abfce6-e44f-419d-85d8-26bf59f33872).  
  
-   Binden von Daten an Steuerelemente im Aktionsbereich.  Weitere Informationen finden Sie unter [Exemplarische Vorgehensweise: Binden von Daten an Steuerelemente in einem Word-Aktionsbereich](../vsto/walkthrough-binding-data-to-controls-on-a-word-actions-pane.md).  
  
## Siehe auch  
 [Aktionsbereichsübersicht](../vsto/actions-pane-overview.md)   
 [Gewusst wie: Hinzufügen eines Aktionsbereichs zu Word-Dokumenten oder Excel-Arbeitsmappen](../vsto/how-to-add-an-actions-pane-to-word-documents-or-excel-workbooks.md)   
 [How to: Add an Actions Pane to Excel Workbooks](http://msdn.microsoft.com/de-de/62abfce6-e44f-419d-85d8-26bf59f33872)   
 [Gewusst wie: Verwalten des Steuerelementlayouts in Aktionsbereichen](../vsto/how-to-manage-control-layout-on-actions-panes.md)   
 [Bookmark-Steuerelement](../vsto/bookmark-control.md)  
  
  