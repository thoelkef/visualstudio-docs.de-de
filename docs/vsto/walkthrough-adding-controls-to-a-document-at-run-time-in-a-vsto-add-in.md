---
title: "Exemplarische Vorgehensweise: Hinzuf&#252;gen von Steuerelementen zu einem Dokument zur Laufzeit in einem VSTO-Add-In | Microsoft Docs"
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
  - "Add-Ins [Office-Entwicklung in Visual Studio], Hinzufügen von Steuerelementen"
  - "Add-Ins auf Anwendungsebene [Office-Entwicklung in Visual Studio], Hinzufügen von Steuerelementen"
  - "Steuerelemente [Office-Entwicklung in Visual Studio], Hinzufügen von Dokumenten zur Laufzeit"
  - "Dokumente [Office-Entwicklung in Visual Studio], Hinzufügen von Steuerelementen zur Laufzeit"
ms.assetid: ab6dff40-9964-468a-938c-a71a3ac23718
caps.latest.revision: 29
author: "kempb"
ms.author: "kempb"
manager: "ghogen"
caps.handback.revision: 28
---
# Exemplarische Vorgehensweise: Hinzuf&#252;gen von Steuerelementen zu einem Dokument zur Laufzeit in einem VSTO-Add-In
  Mit einem VSTO\-Add\-In können Sie jedem geöffneten Microsoft Office Word\-Dokument Steuerelemente hinzufügen. In dieser exemplarischen Vorgehensweise wird veranschaulicht, wie Sie das Menüband verwenden können, um Benutzern das Hinzufügen eines <xref:Microsoft.Office.Tools.Word.Controls.Button>\- oder <xref:Microsoft.Office.Tools.Word.RichTextContentControl>\-Steuerelements zu einem Dokument zu ermöglichen.  
  
 **Betrifft:** Die Informationen in diesem Thema betreffen VSTO\-Add\-In\-Projekte für Word 2010. Weitere Informationen finden Sie unter [Verfügbare Funktionen nach Office-Anwendung und Projekttyp](../vsto/features-available-by-office-application-and-project-type.md).  
  
 In dieser exemplarischen Vorgehensweise werden die folgenden Aufgaben veranschaulicht:  
  
-   Erstellen eines neuen Word\-VSTO\-Add\-In\-Projekts  
  
-   Bereitstellen einer Benutzeroberfläche \(UI\) zum Hinzufügen von Steuerelementen zum Dokument  
  
-   Hinzufügen von Steuerelementen zum Dokument zur Laufzeit  
  
-   Entfernen von Steuerelementen aus dem Dokument  
  
 [!INCLUDE[note_settings_general](../sharepoint/includes/note-settings-general-md.md)]  
  
## Vorbereitungsmaßnahmen  
 Zum Durchführen dieser exemplarischen Vorgehensweise benötigen Sie die folgenden Komponenten:  
  
-   [!INCLUDE[vsto_vsprereq](../vsto/includes/vsto-vsprereq-md.md)]  
  
-   [!INCLUDE[Word_15_short](../vsto/includes/word-15-short-md.md)] oder [!INCLUDE[Word_14_short](../vsto/includes/word-14-short-md.md)].  
  
## Erstellen eines neuen Word\-Add\-in\-Projekts  
 Beginnen Sie, indem Sie ein Word\-VSTO\-Add\-In\-Projekt erstellen.  
  
#### So erstellen Sie ein neues Word\-VSTO\-Add\-In\-Projekt  
  
1.  Erstellen Sie VSTO\-Add\-In\-Projekt für Word namens **WordDynamicControls**. Weitere Informationen finden Sie unter [Gewusst wie: Erstellen von Office-Projekten in Visual Studio](../vsto/how-to-create-office-projects-in-visual-studio.md).  
  
2.  Fügen Sie einen Verweis auf die Assembly **Microsoft.Office.Tools.Word.v4.0.Utilities.dll** hinzu. Dieser Verweis ist erforderlich, um später in dieser exemplarischen Vorgehensweise dem Dokument programmgesteuert ein Windows Forms\-Steuerelement hinzuzufügen.  
  
## Bereitstellen einer Benutzeroberfläche zum Hinzufügen von Steuerelementen zu einem Dokument  
 Fügen Sie dem Menüband in Word eine benutzerdefinierte Registerkarte hinzu. Benutzer können Kontrollkästchen auf der Registerkarte aktivieren, um einem Dokument Steuerelemente hinzuzufügen.  
  
#### So stellen Sie eine Benutzeroberfläche zum Hinzufügen von Steuerelementen zu einem Dokument bereit  
  
1.  Klicken Sie im Menü **Projekt** auf **Neues Element hinzufügen**.  
  
2.  Wählen Sie im Dialogfeld **Neues Element hinzufügen** die Option **Menüband \(Visueller Designer\)** aus.  
  
3.  Ändern Sie den Namen des neuen Menübands in **MyRibbon**, und klicken Sie dann auf **Hinzufügen**.  
  
     Die Datei **MyRibbon.cs** oder **MyRibbon.vb** wird im Menüband\-Designer geöffnet. Sie beinhaltet eine standardmäßige Registerkarte und eine Gruppe.  
  
4.  Klicken Sie im Menüband\-Designer auf die Gruppe **group1**.  
  
5.  Ändern Sie im Fenster **Eigenschaften** die **Bezeichnung**\-Eigenschaft für **group1** in **Steuerelemente hinzufügen**.  
  
6.  Ziehen Sie ein **Kontrollkästchen**\-Steuerelement von der Registerkarte **Steuerelemente für Office\-Menübänder** der **Toolbox** auf **group1**.  
  
7.  Klicken Sie auf **CheckBox1**, um dieses Steuerelement auszuwählen.  
  
8.  Ändern Sie im Fenster **Eigenschaften** die folgenden Eigenschaften:  
  
    |Eigenschaft|Wert|  
    |-----------------|----------|  
    |**Name**|**addButtonCheckBox**|  
    |**Bezeichnung**|**Schaltfläche hinzufügen**|  
  
9. Fügen Sie **group1** ein zweites Kontrollkästchen hinzu, und ändern Sie dann die folgenden Eigenschaften.  
  
    |Eigenschaft|Wert|  
    |-----------------|----------|  
    |**Name**|**addRichTextCheckBox**|  
    |**Bezeichnung**|**Rich\-Text\-Steuerelement hinzufügen**|  
  
10. Doppelklicken Sie im Menüband\-Designer auf **Schaltfläche hinzufügen**.  
  
     Der <xref:Microsoft.Office.Tools.Ribbon.RibbonCheckBox.Click>\-Ereignishandler des Kontrollkästchens **Schaltfläche hinzufügen** wird im Code\-Editor geöffnet.  
  
11. Kehren Sie zum Menüband\-Designer zurück, und doppelklicken Sie auf **Rich\-Text\-Steuerelement hinzufügen**.  
  
     Der <xref:Microsoft.Office.Tools.Ribbon.RibbonCheckBox.Click>\-Ereignishandler des Kontrollkästchens **Rich\-Text\-Steuerelement hinzufügen** wird im Code\-Editor geöffnet.  
  
 Später in dieser exemplarischen Vorgehensweise werden Sie diesen Ereignishandlern Code hinzufügen, mit dem im aktiven Dokument Steuerelemente hinzugefügt und entfernt werden können.  
  
## Hinzufügen und Entfernen von Steuerelementen auf dem aktiven Dokument  
 Sie müssen das aktive Dokument im VSTO\-Add\-In\-Code in ein <xref:Microsoft.Office.Tools.Word.Document>\-*Hostelement* konvertieren, bevor Sie ein Steuerelement hinzufügen können. In Office\-Projektmappen können verwaltete Steuerelemente nur zu Hostelementen hinzugefügt werden, die als Container für die Steuerelemente fungieren. In VSTO\-Add\-In\-Projekten können Hostelemente zur Laufzeit über die GetVstoObject\-Methode erstellt werden.  
  
 Fügen Sie der `ThisAddIn`\-Klasse Methoden hinzu, die aufgerufen werden können, um ein <xref:Microsoft.Office.Tools.Word.Controls.Button>\- oder ein <xref:Microsoft.Office.Tools.Word.RichTextContentControl>\-Steuerelement auf dem aktiven Dokument hinzuzufügen oder zu entfernen. Später in dieser exemplarischen Vorgehensweise werden Sie diese Methoden aus den <xref:Microsoft.Office.Tools.Ribbon.RibbonCheckBox.Click>\-Ereignishandlern der Kontrollkästchen im Menüband aufrufen.  
  
#### So fügen Sie Steuerelemente auf dem aktiven Dokument hinzu oder entfernen diese  
  
1.  Doppelklicken Sie im **Projektmappen\-Explorer** auf „ThisAddIn.cs“ oder „ThisAddIn.vb“, um die Datei im Code\-Editor zu öffnen.  
  
2.  Fügen Sie der `ThisAddIn`\-Klasse folgenden Code hinzu. Mit diesem Code werden ein <xref:Microsoft.Office.Tools.Word.Controls.Button>\- und ein <xref:Microsoft.Office.Tools.Word.RichTextContentControl>\-Objekt deklariert, die den Steuerelementen entsprechen, die dem Dokument hinzugefügt werden.  
  
     [!code-csharp[Trin_WordAddInDynamicControlsWalkthrough#1](../snippets/csharp/VS_Snippets_OfficeSP/Trin_WordAddInDynamicControlsWalkthrough/CS/ThisAddIn.cs#1)]
     [!code-vb[Trin_WordAddInDynamicControlsWalkthrough#1](../snippets/visualbasic/VS_Snippets_OfficeSP/Trin_WordAddInDynamicControlsWalkthrough/VB/ThisAddIn.vb#1)]  
  
3.  Fügen Sie der `ThisAddIn`\-Klasse die folgende Methode hinzu. Wenn der Benutzer auf das Kontrollkästchen **Schaltfläche hinzufügen** im Menüband klickt, fügt diese Methode ein <xref:Microsoft.Office.Tools.Word.Controls.Button>\-Objekt zur aktuellen Auswahl im Dokument hinzu, wenn das Kontrollkästchen aktiviert ist, oder löscht sie das <xref:Microsoft.Office.Tools.Word.Controls.Button>\-Objekt, wenn das Kontrollkästchen deaktiviert ist.  
  
     [!code-csharp[Trin_WordAddInDynamicControlsWalkthrough#2](../snippets/csharp/VS_Snippets_OfficeSP/Trin_WordAddInDynamicControlsWalkthrough/CS/ThisAddIn.cs#2)]
     [!code-vb[Trin_WordAddInDynamicControlsWalkthrough#2](../snippets/visualbasic/VS_Snippets_OfficeSP/Trin_WordAddInDynamicControlsWalkthrough/VB/ThisAddIn.vb#2)]  
  
4.  Fügen Sie der `ThisAddIn`\-Klasse die folgende Methode hinzu. Wenn der Benutzer auf das Kontrollkästchen **Rich\-Text\-Steuerelement hinzufügen** im Menüband klickt, fügt diese Methode ein <xref:Microsoft.Office.Tools.Word.RichTextContentControl>\-Objekt zur aktuellen Auswahl im Dokument hinzu, wenn das Kontrollkästchen aktiviert ist, oder löscht sie das <xref:Microsoft.Office.Tools.Word.RichTextContentControl>\-Objekt, wenn das Kontrollkästchen deaktiviert ist.  
  
     [!code-csharp[Trin_WordAddInDynamicControlsWalkthrough#3](../snippets/csharp/VS_Snippets_OfficeSP/Trin_WordAddInDynamicControlsWalkthrough/CS/ThisAddIn.cs#3)]
     [!code-vb[Trin_WordAddInDynamicControlsWalkthrough#3](../snippets/visualbasic/VS_Snippets_OfficeSP/Trin_WordAddInDynamicControlsWalkthrough/VB/ThisAddIn.vb#3)]  
  
## Entfernen des Button\-Steuerelements, wenn das Dokument gespeichert wird  
 Windows Forms\-Steuerelemente bleiben nicht erhalten, wenn das Dokument gespeichert und dann geschlossen wird. Im Dokument verbleibt aber ein ActiveX\-Wrapper für jedes Steuerelement, und der Rand eines solchen Wrappers ist für Endbenutzer nach einem erneuten Öffnen des Dokuments sichtbar. Es gibt mehrere Möglichkeiten, dynamisch erstellte Windows Forms\-Steuerelemente in VSTO\-Add\-Ins zu bereinigen. In dieser exemplarischen Vorgehensweise wird das <xref:Microsoft.Office.Tools.Word.Controls.Button>\-Steuerelement programmgesteuert entfernt, wenn das Dokument gespeichert wird.  
  
#### So entfernen Sie das Button\-Steuerelement, wenn das Dokument gespeichert wird  
  
1.  Fügen Sie in der Codedatei „ThisAddIn.cs“ oder „ThisAddIn.vb“ der `ThisAddIn`\-Klasse die folgende Methode hinzu. Diese Methode ist ein Ereignishandler für das <xref:Microsoft.Office.Interop.Word.ApplicationEvents4_Event.DocumentBeforeSave>\-Ereignis. Wenn dem gespeicherten Dokument ein <xref:Microsoft.Office.Tools.Word.Document>\-Hostelement zugeordnet ist, ruft der Ereignishandler das Hostelement ab und entfernt das <xref:Microsoft.Office.Tools.Word.Controls.Button>\-Steuerelement, wenn es vorhanden ist.  
  
     [!code-csharp[Trin_WordAddInDynamicControlsWalkthrough#4](../snippets/csharp/VS_Snippets_OfficeSP/Trin_WordAddInDynamicControlsWalkthrough/CS/ThisAddIn.cs#4)]
     [!code-vb[Trin_WordAddInDynamicControlsWalkthrough#4](../snippets/visualbasic/VS_Snippets_OfficeSP/Trin_WordAddInDynamicControlsWalkthrough/VB/ThisAddIn.vb#4)]  
  
2.  In C\# fügen Sie dem `ThisAddIn_Startup`\-Ereignishandler den folgenden Code hinzu. Dieser Code ist in C\# erforderlich, um den `Application_DocumentBeforeSave`\-Ereignishandler mit dem <xref:Microsoft.Office.Interop.Word.ApplicationEvents4_Event.DocumentBeforeSave>\-Ereignis zu verbinden.  
  
     [!code-csharp[Trin_WordAddInDynamicControlsWalkthrough#5](../snippets/csharp/VS_Snippets_OfficeSP/Trin_WordAddInDynamicControlsWalkthrough/CS/ThisAddIn.cs#5)]  
  
## Hinzufügen und Entfernen von Steuerelementen, wenn der Benutzer auf die Kontrollkästchen im Menüband klickt  
 Ändern Sie abschließend die <xref:Microsoft.Office.Tools.Ribbon.RibbonCheckBox.Click>\-Ereignishandler der Kontrollkästchen, die Sie dem Menüband hinzugefügt haben, so, dass sie Steuerelemente auf dem Dokument hinzufügen oder entfernen.  
  
#### So fügen Sie Steuerelemente hinzu oder entfernen diese, wenn der Benutzer auf die Kontrollkästchen im Menüband klickt  
  
1.  Ersetzen Sie in der Codedatei „MyRibbon.cs“ oder „MyRibbon.vb“ die generierten Ereignishandler `addButtonCheckBox_Click` und `addRichTextCheckBox_Click` durch den folgenden Code. Dieser Code definiert diese Ereignishandler neu, sodass aus ihnen die `ToggleButtonOnDocument`\- und die `ToggleRichTextControlOnDocument`\-Methode aufgerufen werden, die Sie der `ThisAddIn`\-Klasse früher in dieser exemplarischen Vorgehensweise hinzugefügt haben.  
  
     [!code-csharp[Trin_WordAddInDynamicControlsWalkthrough#6](../snippets/csharp/VS_Snippets_OfficeSP/Trin_WordAddInDynamicControlsWalkthrough/CS/MyRibbon.cs#6)]
     [!code-vb[Trin_WordAddInDynamicControlsWalkthrough#6](../snippets/visualbasic/VS_Snippets_OfficeSP/Trin_WordAddInDynamicControlsWalkthrough/VB/MyRibbon.vb#6)]  
  
## Testen der Projektmappe  
 Fügen Sie einem Dokument Steuerelemente hinzu, indem Sie sie auf der benutzerdefinierten Registerkarte im Menüband auswählen. Wenn Sie das Dokument speichern, wird das <xref:Microsoft.Office.Tools.Word.Controls.Button>\-Steuerelement entfernt.  
  
#### So testen Sie die Projektmappe  
  
1.  Drücken Sie F5, um das Projekt auszuführen.  
  
2.  Drücken Sie im aktiven Dokument mehrmals die EINGABETASTE, um dem Dokument neue leere Absätze hinzuzufügen.  
  
3.  Wählen Sie den ersten Absatz aus.  
  
4.  Klicken Sie auf die Registerkarte **Add\-Ins**.  
  
5.  Klicken Sie in der Gruppe **Steuerelemente hinzufügen** auf **Schaltfläche hinzufügen**.  
  
     Im ersten Absatz wird eine Schaltfläche angezeigt.  
  
6.  Wählen Sie den letzten Absatz aus.  
  
7.  Klicken Sie in der Gruppe **Steuerelemente hinzufügen** auf **Rich\-Text\-Steuerelement hinzufügen**.  
  
     Dem letzten Absatz wird ein Rich\-Text\-Inhaltssteuerelement hinzugefügt.  
  
8.  Speichern Sie das Dokument.  
  
     Die Schaltfläche wird aus dem Dokument entfernt.  
  
## Nächste Schritte  
 In den folgenden Themen erhalten Sie weitere Informationen zu Steuerelementen in VSTO\-Add\-Ins:  
  
-   Ein Beispiel, in dem veranschaulicht wird, wie einem Dokument zur Laufzeit viele weitere Typen von Steuerelementen hinzugefügt und wie die Steuerelemente bei einem erneuten Öffnen des Dokuments neu erstellt werden, finden Sie in dem Beispiel für dynamische Add\-In\-Steuerelemente in Word unter [Beispiele und exemplarische Vorgehensweisen für die Programmierung mit Office](../vsto/office-development-samples-and-walkthroughs.md)  
  
-   Eine exemplarische Vorgehensweise, in der veranschaulicht wird, wie einem Arbeitsblatt Steuerelemente mit einem VSTO\-Add\-In für Excel hinzugefügt werden, finden Sie unter [Exemplarische Vorgehensweise: Hinzufügen von Steuerelementen zu einem Arbeitsblatt zur Laufzeit in einem VSTO-Ad-In-Projekt](../vsto/walkthrough-adding-controls-to-a-worksheet-at-run-time-in-vsto-add-in-project.md).  
  
## Siehe auch  
 [Word-Projektmappen](../vsto/word-solutions.md)   
 [Hinzufügen von Steuerelementen zu Office-Dokumenten zur Laufzeit](../vsto/adding-controls-to-office-documents-at-run-time.md)   
 [Beibehalten von dynamischen Steuerelementen in Office-Dokumenten](../vsto/persisting-dynamic-controls-in-office-documents.md)   
 [Gewusst wie: Hinzufügen von Windows Forms-Steuerelementen zu Office-Dokumenten](../vsto/how-to-add-windows-forms-controls-to-office-documents.md)   
 [Gewusst wie: Hinzufügen von Inhaltssteuerelementen zu Word-Dokumenten](../vsto/how-to-add-content-controls-to-word-documents.md)   
 [Erweitern von Word-Dokumenten und Excel-Arbeitsmappen in VSTO-Add-Ins zur Laufzeit](../vsto/extending-word-documents-and-excel-workbooks-in-vsto-add-ins-at-run-time.md)  
  
  