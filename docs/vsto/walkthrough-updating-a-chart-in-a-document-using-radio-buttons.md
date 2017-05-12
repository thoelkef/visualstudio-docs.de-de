---
title: "Exemplarische Vorgehensweise: Aktualisieren eines Diagramms in einem Dokument mithilfe von Optionsfeldern"
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
  - "Steuerelemente [Office-Entwicklung in Visual Studio], Aktualisieren von Dokumenten"
  - "Dokumente [Office-Entwicklung in Visual Studio], Aktualisieren mit Steuerelementen"
ms.assetid: 56e6d1f2-65a4-41f0-aff5-f0cfd96d7185
caps.latest.revision: 60
author: "kempb"
ms.author: "kempb"
manager: "ghogen"
caps.handback.revision: 59
---
# Exemplarische Vorgehensweise: Aktualisieren eines Diagramms in einem Dokument mithilfe von Optionsfeldern
  Diese Vorgehensweise zeigt Ihnen, wie Sie Optionsfelder in einer Anpassung auf Dokumentebene für Microsoft Office Word verwenden, um Benutzern die Möglichkeit zu geben, Diagrammformatvorlagen im Dokument auszuwählen.  
  
 [!INCLUDE[appliesto_wdalldoc](../vsto/includes/appliesto-wdalldoc-md.md)]  
  
 In dieser exemplarischen Vorgehensweise werden die folgenden Aufgaben veranschaulicht:  
  
-   Hinzufügen eines Diagramms zum Dokument in einem Projekt auf Dokumentebene zur Entwurfszeit.  
  
-   Gruppieren von Optionsfeldern durch Hinzufügen zu einem Benutzersteuerelement.  
  
-   Ändern der Diagrammformatvorlage, wenn eine Option ausgewählt ist.  
  
 Um das Ergebnis als vollständiges Beispiel anzuzeigen, sehen Sie sich das Beispiel für Word\-Steuerelemente unter [Beispiele und exemplarische Vorgehensweisen für die Programmierung mit Office](../vsto/office-development-samples-and-walkthroughs.md) an.  
  
 [!INCLUDE[note_settings_general](../sharepoint/includes/note-settings-general-md.md)]  
  
## Vorbereitungsmaßnahmen  
 Zum Durchführen dieser exemplarischen Vorgehensweise benötigen Sie die folgenden Komponenten:  
  
-   [!INCLUDE[vsto_vsprereq](../vsto/includes/vsto-vsprereq-md.md)]  
  
-   [!INCLUDE[Word_15_short](../vsto/includes/word-15-short-md.md)] oder [!INCLUDE[Word_14_short](../vsto/includes/word-14-short-md.md)].  
  
## Erstellen des Projekts  
 Im ersten Schritt wird ein Word\-Dokumentprojekt erstellt.  
  
#### So erstellen Sie ein neues Projekt  
  
1.  Erstellen Sie ein Word\-Dokumentprojekt mit dem Namen **Meine Diagrammoptionen**.  Wählen Sie im Assistenten **Neues Dokument erstellen** aus.  Weitere Informationen finden Sie unter [Gewusst wie: Erstellen von Office-Projekten in Visual Studio](../vsto/how-to-create-office-projects-in-visual-studio.md).  
  
     Visual Studio öffnet das neue Word\-Dokument im Designer und fügt dem **Projektmappen\-Explorer** das **Meine Diagrammoptionen**\-Projekt hinzu.  
  
## Hinzufügen eines Diagramm zum Dokument  
  
#### So fügen Sie ein Diagramm hinzu  
  
1.  Klicken Sie im Word\-Dokument, das im Visual Studio\-Designer gehostet wird, auf dem Menüband auf die Registerkarte **Einfügen**.  
  
2.  Klicken Sie in der Gruppe **Text**  auf die Dropdown\-Schaltfläche **Objekt einfügen** und dann auf **Objekt**.  
  
     Das Dialogfeld **Objekt** wird geöffnet.  
  
3.  Wählen Sie auf der Registerkarte **Neu erstellen** in der Liste **Objekttyp** die Option **Microsoft Graph\-Diagramm** aus, und klicken Sie dann auf **OK**.  
  
     Dem Dokument wird an der Einfügemarke ein Diagramm hinzugefügt, und das Fenster **Datenblatt** wird mit einigen Standarddaten angezeigt.  
  
4.  Schließen Sie das Fenster **Datenblatt**, um die Standardwerte im Diagramm zu akzeptieren, und klicken Sie dann in das Dokument, um die Aktivierung des Diagramms aufzuheben.  
  
5.  Klicken Sie mit der rechten Maustaste auf das Diagramm, und klicken Sie dann auf **Objekt formatieren**.  
  
6.  Wählen Sie auf der Registerkarte **Layout** des Dialogfelds **Objekt formatieren** die Option **Quadrat** aus, und klicken Sie dann auf **OK**.  
  
## Hinzufügen eines Benutzersteuerelements zum Projekt  
 Optionsfelder in einem Dokument schließen sich standardmäßig nicht gegenseitig aus.  Sie können dafür sorgen, dass sie ordnungsgemäß funktionieren, indem Sie sie einem Benutzersteuerelement hinzufügen und dann Code schreiben, um die Auswahl zu steuern.  
  
#### So fügen Sie ein Benutzersteuerelement hinzu  
  
1.  Wählen Sie das Projekt **Meine Diagrammoptionen** im **Projektmappen\-Explorer** aus.  
  
2.  Klicken Sie im Menü **Projekt** auf **Neues Element hinzufügen**.  
  
3.  Klicken Sie im Dialogfeld **Neues Element hinzufügen** auf **Benutzersteuerelement**, benennen Sie das Steuerelement **ChartOptions**, und klicken Sie dann auf **Hinzufügen**.  
  
#### So fügen Sie dem Benutzersteuerelement Windows Forms\-Steuerelemente hinzu  
  
1.  Wenn das Benutzersteuerelement nicht im Designer sichtbar ist, doppelklicken Sie im **Projektmappen\-Explorer** auf **ChartOptions**.  
  
2.  Ziehen Sie aus der Registerkarte **Allgemeine Steuerelemente** des **Werkzeugkastens** das erste **Optionsfeld**\-Steuerelement auf das Benutzersteuerelement, und ändern Sie die folgenden Eigenschaften.  
  
    |Eigenschaft|Wert|  
    |-----------------|----------|  
    |**Name**|**columnChart**|  
    |**Text**|Säulendiagramm|  
  
3.  Fügen Sie dem Benutzersteuerelement ein zweites **Optionsfeld** hinzu, und ändern Sie die folgenden Eigenschaften.  
  
    |Eigenschaft|Wert|  
    |-----------------|----------|  
    |**Name**|**barChart**|  
    |**Text**|Balkendiagramm|  
  
4.  Fügen Sie dem Benutzersteuerelement ein drittes **Optionsfeld** hinzu, und ändern Sie die folgenden Eigenschaften.  
  
    |Eigenschaft|Wert|  
    |-----------------|----------|  
    |**Name**|**lineChart**|  
    |**Text**|Liniendiagramm|  
  
5.  Fügen Sie dem Benutzersteuerelement ein viertes **Optionsfeld** hinzu, und ändern Sie die folgenden Eigenschaften.  
  
    |Eigenschaft|Wert|  
    |-----------------|----------|  
    |**Name**|**areaBlockChart**|  
    |**Text**|Flächendiagramm|  
  
## Hinzufügen von Verweisen  
 Zum Zugriff auf das Diagramm über das Benutzersteuerelement in einem Dokument, müssen Sie einen Verweis auf die Microsoft.Office.Interop.Graph\-Assembly in Ihrem Projekt haben.  
  
#### So fügen Sie einen Verweis auf die Microsoft.Office.Interop.Graph\-Assembly hinzu  
  
1.  Klicken Sie im Menü **Projekt** auf **Verweis hinzufügen**.  
  
     Das Dialogfeld **Verweis hinzufügen** wird angezeigt.  
  
2.  Wählen Sie auf der **.NET**\-Registerkarte die Assembly **Microsoft.Office.Interop.Graph** aus, klicken Sie dann auf **OK**.  Verwenden Sie die 14.0.0.0\-Version der Assembly.  
  
## Ändern der Diagrammformatvorlage bei ausgewähltem Optionsfeld  
 Damit die Schaltflächen ordnungsgemäß funktionieren, erstellen Sie ein öffentliches Ereignis auf dem Benutzersteuerelement, fügen Sie eine Eigenschaft hinzu, um den Auswahltyp festzulegen, und erstellen Sie eine Prozedur für das `CheckedChanged`\-Ereignis der einzelnen Optionsfelder.  
  
#### So erstellen Sie ein Ereignis und eine Eigenschaft auf einem Benutzersteuerelement  
  
1.  Klicken Sie im **Projektmappen\-Explorer** mit der rechten Maustaste auf das Benutzersteuerelement, und wählen Sie dann **Code anzeigen**.  
  
2.  Fügen Sie Code hinzu, um ein `SelectionChanged`\-Ereignis und die `Selection`\-Eigenschaft der `ChartOptions`\-Klasse zu erstellen.  
  
     [!code-csharp[Trin_VstcoreProgrammingControlsWord#9](../snippets/csharp/VS_Snippets_OfficeSP/Trin_VstcoreProgrammingControlsWord/CS/ChartOptions.cs#9)]
     [!code-vb[Trin_VstcoreProgrammingControlsWord#9](../snippets/visualbasic/VS_Snippets_OfficeSP/Trin_VstcoreProgrammingControlsWord/VB/ChartOptions.vb#9)]  
  
#### So behandeln Sie das CheckedChange\-Ereignis der Optionsfelder  
  
1.  Legen Sie den Diagrammtyp im `CheckedChanged`\-Ereignishandler des `areaBlockChart`\-Optionsfelds fest, und erhöhen Sie dann das Ereignis.  
  
     [!code-csharp[Trin_VstcoreProgrammingControlsWord#10](../snippets/csharp/VS_Snippets_OfficeSP/Trin_VstcoreProgrammingControlsWord/CS/ChartOptions.cs#10)]
     [!code-vb[Trin_VstcoreProgrammingControlsWord#10](../snippets/visualbasic/VS_Snippets_OfficeSP/Trin_VstcoreProgrammingControlsWord/VB/ChartOptions.vb#10)]  
  
2.  Legen Sie den Diagrammtyp im `CheckedChanged`\-Ereignishandler des `barChart`\-Optionsfelds fest.  
  
     [!code-csharp[Trin_VstcoreProgrammingControlsWord#11](../snippets/csharp/VS_Snippets_OfficeSP/Trin_VstcoreProgrammingControlsWord/CS/ChartOptions.cs#11)]
     [!code-vb[Trin_VstcoreProgrammingControlsWord#11](../snippets/visualbasic/VS_Snippets_OfficeSP/Trin_VstcoreProgrammingControlsWord/VB/ChartOptions.vb#11)]  
  
3.  Legen Sie den Diagrammtyp im `CheckedChanged`\-Ereignishandler des `columnChart`\-Optionsfelds fest.  
  
     [!code-csharp[Trin_VstcoreProgrammingControlsWord#12](../snippets/csharp/VS_Snippets_OfficeSP/Trin_VstcoreProgrammingControlsWord/CS/ChartOptions.cs#12)]
     [!code-vb[Trin_VstcoreProgrammingControlsWord#12](../snippets/visualbasic/VS_Snippets_OfficeSP/Trin_VstcoreProgrammingControlsWord/VB/ChartOptions.vb#12)]  
  
4.  Legen Sie den Diagrammtyp im `CheckedChanged`\-Ereignishandler des `lineChart`\-Optionsfelds fest.  
  
     [!code-csharp[Trin_VstcoreProgrammingControlsWord#13](../snippets/csharp/VS_Snippets_OfficeSP/Trin_VstcoreProgrammingControlsWord/CS/ChartOptions.cs#13)]
     [!code-vb[Trin_VstcoreProgrammingControlsWord#13](../snippets/visualbasic/VS_Snippets_OfficeSP/Trin_VstcoreProgrammingControlsWord/VB/ChartOptions.vb#13)]  
  
5.  In C\# müssen Sie Ereignishandler für die Optionsfelder hinzufügen.  Sie können den Code dem `ChartOptions`\-Konstruktor hinzufügen, unterhalb des Aufrufs von `InitializeComponent`.  Weitere Informationen zum Erstellen von Ereignishandlern finden Sie unter [Gewusst wie: Erstellen von Ereignishandlern in Office-Projekten](../vsto/how-to-create-event-handlers-in-office-projects.md).  
  
     [!code-csharp[Trin_VstcoreProgrammingControlsWord#14](../snippets/csharp/VS_Snippets_OfficeSP/Trin_VstcoreProgrammingControlsWord/CS/ChartOptions.cs#14)]  
  
## Hinzufügen des Benutzersteuerelements zum Dokument  
 Wenn Sie die Projektmappe erstellen, wird das neue Benutzersteuerelement automatisch dem **Werkzeugkasten** hinzugefügt.  Anschließend können Sie das Steuerelement aus dem **Werkzeugkasten** in Ihr Dokument ziehen.  
  
#### So fügen Sie dem Dokument das Benutzersteuerelement hinzu  
  
1.  Klicken Sie im Menü **Erstellen** auf **Projektmappe erstellen**.  
  
     Das Benutzersteuerelement **ChartOptions** wird dem **Werkzeugkasten** hinzugefügt.  
  
2.  Klicken Sie im **Projektmappen\-Explorer** mit der rechten Maustaste auf **ThisDocument.vb** oder **ThisDocument.cs**, und wählen Sie dann **Ansicht\-Designer**.  
  
3.  Ziehen Sie das `ChartOptions`\-Steuerelement aus dem **Werkzeugkasten** in das Dokument.  
  
     Geben Sie dem Steuerelement, das Sie gerade dem Dokument `ChartOptions1` hinzugefügt haben, im Fenster **Eigenschaften** einen Namen.  
  
## Ändern des Diagrammtyps  
 Erstellen Sie einen Ereignishandler, um den Diagrammtyp gemäß der im Benutzersteuerelement ausgewählten Option zu ändern.  
  
#### So ändern Sie den Diagrammtyp, der im Dokument angezeigt wird  
  
1.  Fügen Sie der `ThisDocument`\-Klasse den folgenden Ereignishandler hinzu.  
  
     [!code-csharp[Trin_VstcoreProgrammingControlsWord#15](../snippets/csharp/VS_Snippets_OfficeSP/Trin_VstcoreProgrammingControlsWord/CS/ThisDocument.cs#15)]
     [!code-vb[Trin_VstcoreProgrammingControlsWord#15](../snippets/visualbasic/VS_Snippets_OfficeSP/Trin_VstcoreProgrammingControlsWord/VB/ThisDocument.vb#15)]  
  
2.  In C\# müssen Sie dem <xref:Microsoft.Office.Tools.Word.Document.Startup>\-Ereignis einen Ereignishandler für das Benutzersteuerelement hinzufügen.  
  
     [!code-csharp[Trin_VstcoreProgrammingControlsWord#16](../snippets/csharp/VS_Snippets_OfficeSP/Trin_VstcoreProgrammingControlsWord/CS/ThisDocument.cs#16)]  
  
## Testen der Anwendung  
 Sie können jetzt Ihr Dokument testen, um sicherzustellen, dass die Diagrammformatvorlage ordnungsgemäß aktualisiert wird, wenn Sie ein Optionsfeld auswählen.  
  
#### So testen Sie das Dokument  
  
1.  Drücken Sie F5, um das Projekt auszuführen.  
  
2.  Wählen Sie verschiedene Optionsfelder aus.  
  
3.  Stellen Sie sicher, dass sich die Diagrammformatvorlage ändert, um der Auswahl zu entsprechen.  
  
## Nächste Schritte  
 Die folgenden Aufgaben könnten sich daran anschließen:  
  
-   Verwenden einer Schaltfläche zum Ausfüllen eines Textfeldes.  Weitere Informationen finden Sie unter [Exemplarische Vorgehensweise: Anzeigen von Text in einem Textfeld in einem Dokument mithilfe einer Schaltfläche](../vsto/walkthrough-displaying-text-in-a-text-box-in-a-document-using-a-button.md).  
  
-   Ändern der Formatierung durch Auswahl eines Formats aus einem Kombinationsfeld.  Weitere Informationen finden Sie unter [Exemplarische Vorgehensweise: Ändern der Dokumentformatierung mit CheckBox-Steuerelementen](../vsto/walkthrough-changing-document-formatting-using-checkbox-controls.md).  
  
## Siehe auch  
 [Exemplarische Vorgehensweisen in Word](../vsto/walkthroughs-using-word.md)   
 [Beispiele und exemplarische Vorgehensweisen für die Programmierung mit Office](../vsto/office-development-samples-and-walkthroughs.md)   
 [Einschränkungen für Windows Forms-Steuerelemente in Office-Dokumenten](../vsto/limitations-of-windows-forms-controls-on-office-documents.md)  
  
  