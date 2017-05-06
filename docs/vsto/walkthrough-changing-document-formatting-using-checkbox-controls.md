---
title: "Exemplarische Vorgehensweise: &#196;ndern der Dokumentformatierung mit CheckBox-Steuerelementen"
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
  - "Kontrollkästchen, Word-Dokumente"
  - "Steuerelemente [Office-Entwicklung in Visual Studio], Hinzufügen zu Dokumenten"
  - "Dokumente [Office-Entwicklung in Visual Studio], Kontrollkästchen-Steuerelemente"
  - "Dokumente [Office-Entwicklung in Visual Studio], Formatierung"
  - "Word-Dokumente, Ändern der Formatierung mit Steuerelementen"
ms.assetid: 3740e41d-a57e-43bb-87e7-6e5481ef290b
caps.latest.revision: 70
author: "kempb"
ms.author: "kempb"
manager: "ghogen"
caps.handback.revision: 69
---
# Exemplarische Vorgehensweise: &#196;ndern der Dokumentformatierung mit CheckBox-Steuerelementen
  In dieser exemplarischen Vorgehensweise wird die Verwendung von Windows Forms\-Steuerelementen für die Änderung der Textformatierung in einer Anpassung auf Dokumentebene für Microsoft Office Word veranschaulicht.  
  
 [!INCLUDE[appliesto_wdalldoc](../vsto/includes/appliesto-wdalldoc-md.md)]  
  
 In dieser exemplarischen Vorgehensweise werden die folgenden Aufgaben veranschaulicht:  
  
-   So fügen Sie dem Dokument in einem Projekt auf Dokumentebene zur Entwurfszeit einen Text und ein Steuerelement hinzu  
  
-   Formatieren des Texts beim Auswählen einer Option  
  
 Das Ergebnis in einem vollständigen Beispiel finden Sie in dem Beispiel für Word\-Steuerelemente unter [Beispiele und exemplarische Vorgehensweisen für die Programmierung mit Office](../vsto/office-development-samples-and-walkthroughs.md).  
  
 [!INCLUDE[note_settings_general](../sharepoint/includes/note-settings-general-md.md)]  
  
## Vorbereitungsmaßnahmen  
 Zum Durchführen dieser exemplarischen Vorgehensweise benötigen Sie die folgenden Komponenten:  
  
-   [!INCLUDE[vsto_vsprereq](../vsto/includes/vsto-vsprereq-md.md)]  
  
-   [!INCLUDE[Word_15_short](../vsto/includes/word-15-short-md.md)] oder [!INCLUDE[Word_14_short](../vsto/includes/word-14-short-md.md)].  
  
## Erstellen des Projekts  
 Der erste Schritt besteht darin, ein Word\-Dokumentprojekt zu erstellen.  
  
#### So erstellen Sie ein neues Projekt  
  
1.  Erstellen Sie ein Word\-Dokumentprojekt mit dem Namen Meine Word\-Formatierung.  Wählen Sie im Assistenten **Neues Dokument erstellen** aus.  
  
     Weitere Informationen finden Sie unter [Gewusst wie: Erstellen von Office-Projekten in Visual Studio](../vsto/how-to-create-office-projects-in-visual-studio.md).  
  
     Visual Studio öffnet das neue Word\-Dokument im Designer und fügt dem **Projektmappen\-Explorer** das **Meine Word\-Formatierung**\-Projekt hinzu.  
  
## Hinzufügen von Text und Steuerelementen zum Word\-Dokument  
 Für diese exemplarische Vorgehensweise fügen Sie dem Word\-Dokument drei Kontrollkästchen und etwas Text in einem <xref:Microsoft.Office.Tools.Word.Bookmark>\-Steuerelement hinzu.  Die Kontrollkästchen bieten dem Benutzer Optionen zum Formatieren des Texts.  
  
#### So fügen Sie drei Kontrollkästchen hinzu  
  
1.  Überprüfen Sie, ob das Dokument im Visual Studio\-Designer geöffnet ist.  
  
2.  Ziehen Sie von der Registerkarte **Allgemeine Steuerelemente** der **Toolbox** das erste <xref:Microsoft.Office.Tools.Word.Controls.CheckBox>\-Steuerelement in das Dokument.  
  
3.  Ändern Sie im **Eigenschaftenfenster** die folgenden Eigenschaften.  
  
    |Eigenschaft|Wert|  
    |-----------------|----------|  
    |**Name**|**applyBoldFont**|  
    |**Text**|Fett|  
  
4.  Drücken Sie die **EINGABETASTE**, um die Einfügemarke unter das erste Kontrollkästchen zu bewegen.  
  
5.  Fügen Sie dem Dokument unterhalb des `ApplyBoldFont`\-Kontrollkästchens ein zweites Kontrollkästchen hinzu, und ändern Sie die folgenden Eigenschaften.  
  
    |Eigenschaft|Wert|  
    |-----------------|----------|  
    |**Name**|**applyItalicFont**|  
    |**Text**|Kursiv|  
  
6.  Drücken Sie die **EINGABETASTE**, um die Einfügemarke unter das zweite Kontrollkästchen zu bewegen.  
  
7.  Fügen Sie dem Dokument unterhalb des `ApplyItalicFont`\-Kontrollkästchens ein drittes Kontrollkästchen hinzu, und ändern Sie die folgenden Eigenschaften.  
  
    |Eigenschaft|Wert|  
    |-----------------|----------|  
    |**Name**|**applyUnderlineFont**|  
    |**Text**|Unterstreichen|  
  
#### So fügen Sie Text und ein Bookmark\-Steuerelement hinzu  
  
1.  Bewegen Sie die Einfügemarke unter die CheckBox\-Steuerelemente, und geben Sie den folgenden Text ein:  
  
     Klicken Sie auf ein Kontrollkästchen, um die Formatierung des Texts zu ändern.  
  
2.  Ziehen Sie von der Registerkarte **Word\-Steuerelemente** der **Toolbox** ein <xref:Microsoft.Office.Tools.Word.Bookmark>\-Steuerelement in das Dokument.  
  
     Das Dialogfeld **Lesezeichen\-Steuerelement hinzufügen** wird angezeigt.  
  
3.  Wählen Sie den Text aus, den Sie dem Dokument hinzugefügt haben, und klicken Sie auf **OK**.  
  
     Dem ausgewählten Text wird im Dokument ein <xref:Microsoft.Office.Tools.Word.Bookmark>\-Steuerelement mit Namen **Bookmark1** hinzugefügt.  
  
4.  Ändern Sie im **Eigenschaftenfenster** den Wert der **\(Name\)**\-Eigenschaft in **fontText.**  
  
 Schreiben Sie dann den Code zum Formatieren des Texts beim Aktivieren oder Deaktivieren eines Kontrollkästchens.  
  
## Formatieren des Texts beim Aktivieren oder Deaktivieren eines Kontrollkästchens  
 Ändern Sie das Format des Texts im Dokument, wenn der Benutzer eine Formatierungsoption auswählt.  
  
#### So ändern Sie die Formatierung beim Aktivieren eines Kontrollkästchens  
  
1.  Klicken Sie im **Projektmappen\-Explorer** mit der rechten Maustaste auf `ThisDocument`, und klicken Sie anschließend im Kontextmenü auf **Code anzeigen**.  
  
2.  Fügen Sie der **ThisDocument**\-Klasse die folgenden Konstanten hinzu \(nur C\#\).  
  
     [!code-csharp[Trin_VstcoreProgrammingControlsWord#2](../snippets/csharp/VS_Snippets_OfficeSP/Trin_VstcoreProgrammingControlsWord/CS/ThisDocument.cs#2)]  
  
3.  Fügen Sie dem <xref:System.Windows.Forms.Control.Click>\-Ereignishandler des `applyBoldFont`\-Kontrollkästchens den folgenden Code hinzu.  
  
     [!code-csharp[Trin_VstcoreProgrammingControlsWord#3](../snippets/csharp/VS_Snippets_OfficeSP/Trin_VstcoreProgrammingControlsWord/CS/ThisDocument.cs#3)]
     [!code-vb[Trin_VstcoreProgrammingControlsWord#3](../snippets/visualbasic/VS_Snippets_OfficeSP/Trin_VstcoreProgrammingControlsWord/VB/ThisDocument.vb#3)]  
  
4.  Fügen Sie dem <xref:System.Windows.Forms.Control.Click>\-Ereignishandler des `applyItalicFont`\-Kontrollkästchens den folgenden Code hinzu.  
  
     [!code-csharp[Trin_VstcoreProgrammingControlsWord#4](../snippets/csharp/VS_Snippets_OfficeSP/Trin_VstcoreProgrammingControlsWord/CS/ThisDocument.cs#4)]
     [!code-vb[Trin_VstcoreProgrammingControlsWord#4](../snippets/visualbasic/VS_Snippets_OfficeSP/Trin_VstcoreProgrammingControlsWord/VB/ThisDocument.vb#4)]  
  
5.  Fügen Sie dem <xref:System.Windows.Forms.Control.Click>\-Ereignishandler des `applyUnderlineFont`\-Kontrollkästchens den folgenden Code hinzu.  
  
     [!code-csharp[Trin_VstcoreProgrammingControlsWord#5](../snippets/csharp/VS_Snippets_OfficeSP/Trin_VstcoreProgrammingControlsWord/CS/ThisDocument.cs#5)]
     [!code-vb[Trin_VstcoreProgrammingControlsWord#5](../snippets/visualbasic/VS_Snippets_OfficeSP/Trin_VstcoreProgrammingControlsWord/VB/ThisDocument.vb#5)]  
  
6.  In C\# müssen Sie Ereignishandler für die Textfelder zum <xref:Microsoft.Office.Tools.Word.Document.Startup>\-Ereignis hinzufügen.  Informationen zum Erstellen von Ereignishandlern finden Sie unter [Gewusst wie: Erstellen von Ereignishandlern in Office-Projekten](../vsto/how-to-create-event-handlers-in-office-projects.md).  
  
     [!code-csharp[Trin_VstcoreProgrammingControlsWord#6](../snippets/csharp/VS_Snippets_OfficeSP/Trin_VstcoreProgrammingControlsWord/CS/ThisDocument.cs#6)]  
  
## Testen der Anwendung  
 Sie können das Dokument nun testen, um zu überprüfen, ob der Text beim Aktivieren bzw. Deaktivieren eines Kontrollkästchens richtig formatiert wird.  
  
#### So testen Sie das Dokument  
  
1.  Drücken Sie F5, um das Projekt auszuführen.  
  
2.  Aktivieren bzw. deaktivieren Sie ein Kontrollkästchen.  
  
3.  Überprüfen Sie, ob der Text richtig formatiert ist.  
  
## Nächste Schritte  
 In dieser exemplarischen Vorgehensweise werden die Grundlagen für die Verwendung von Kontrollkästchen sowie die programmgesteuerte Änderung der Textformatierung in Word\-Dokumenten beschrieben.  Die folgenden Aufgaben könnten sich daran anschließen:  
  
-   Verwenden einer Schaltfläche zum Auffüllen eines Textfelds.  Weitere Informationen finden Sie unter [Exemplarische Vorgehensweise: Anzeigen von Text in einem Textfeld in einem Dokument mithilfe einer Schaltfläche](../vsto/walkthrough-displaying-text-in-a-text-box-in-a-document-using-a-button.md).  
  
-   Verwenden von Optionsfeldern, um Diagrammstile auszuwählen.  Weitere Informationen finden Sie unter [Exemplarische Vorgehensweise: Aktualisieren eines Diagramms in einem Dokument mithilfe von Optionsfeldern](../vsto/walkthrough-updating-a-chart-in-a-document-using-radio-buttons.md).  
  
## Siehe auch  
 [Exemplarische Vorgehensweisen in Word](../vsto/walkthroughs-using-word.md)   
 [Beispiele und exemplarische Vorgehensweisen für die Programmierung mit Office](../vsto/office-development-samples-and-walkthroughs.md)   
 [NamedRange-Steuerelement](../vsto/namedrange-control.md)   
 [Einschränkungen für Windows Forms-Steuerelemente in Office-Dokumenten](../vsto/limitations-of-windows-forms-controls-on-office-documents.md)  
  
  