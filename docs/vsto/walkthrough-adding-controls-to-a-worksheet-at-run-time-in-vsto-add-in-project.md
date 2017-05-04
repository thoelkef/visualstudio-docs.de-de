---
title: "Exemplarische Vorgehensweise: Hinzuf&#252;gen von Steuerelementen zu einem Arbeitsblatt zur Laufzeit in einem VSTO-Ad-In-Projekt | Microsoft Docs"
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
  - "Steuerelemente [Office-Entwicklung in Visual Studio], Hinzufügen zu Arbeitsblättern zur Laufzeit"
  - "Arbeitsblätter, Hinzufügen von Steuerelementen zur Laufzeit"
ms.assetid: 4f68677a-4789-4564-b229-02e2d4031a5f
caps.latest.revision: 38
author: "kempb"
ms.author: "kempb"
manager: "ghogen"
caps.handback.revision: 37
---
# Exemplarische Vorgehensweise: Hinzuf&#252;gen von Steuerelementen zu einem Arbeitsblatt zur Laufzeit in einem VSTO-Ad-In-Projekt
  Sie können einem beliebigen geöffneten Arbeitblatt Steuerelemente mithilfe eines Excel\-VSTO\-Add\-In hinzufügen.  Diese exemplarische Vorgehensweise veranschaulicht, wie Benutzer einem Arbeitsblatt mithilfe des Menübands ein <xref:Microsoft.Office.Tools.Excel.Controls.Button>, <xref:Microsoft.Office.Tools.Excel.NamedRange> und <xref:Microsoft.Office.Tools.Excel.ListObject> hinzufügen können.  Weitere Informationen finden Sie unter [Hinzufügen von Steuerelementen zu Office-Dokumenten zur Laufzeit](../vsto/adding-controls-to-office-documents-at-run-time.md).  
  
 **Betrifft:** Die Informationen in diesem Thema beziehen sich auf VSTO\-Add\-In\-Projekte für Excel.  Weitere Informationen finden Sie unter [Verfügbare Funktionen nach Office-Anwendung und Projekttyp](../vsto/features-available-by-office-application-and-project-type.md).  
  
 In dieser exemplarischen Vorgehensweise werden die folgenden Aufgaben veranschaulicht:  
  
-   Bereitstellen einer Benutzeroberfläche \(UI\) zum Hinzufügen von Steuerelementen zum Arbeitsblatt  
  
-   Hinzufügen von Steuerelementen zum Arbeitsblatt  
  
-   Entfernen von Steuerelementen aus dem Arbeitsblatt  
  
 [!INCLUDE[note_settings_general](../sharepoint/includes/note-settings-general-md.md)]  
  
## Vorbereitungsmaßnahmen  
 Zum Durchführen dieser exemplarischen Vorgehensweise benötigen Sie die folgenden Komponenten:  
  
-   [!INCLUDE[vsto_vsprereq](../vsto/includes/vsto-vsprereq-md.md)]  
  
-   Excel  
  
## Erstellen eines neuen Excel\-VSTO\-Add\-In\-Projekts  
 Beginnen Sie mit der Erstellung eines Excel VSTO\-Add\-In\-Projekts.  
  
#### So erstellen Sie ein neues Excel\-VSTO\-Add\-In\-Projekt  
  
1.  Erstellen Sie in [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] ein Excel\-VSTO\-Add\-In\-Projekt namens "ExcelDynamicControls".  Weitere Informationen finden Sie unter [Gewusst wie: Erstellen von Office-Projekten in Visual Studio](../vsto/how-to-create-office-projects-in-visual-studio.md).  
  
2.  Fügen Sie einen Verweis auf die Assembly **Microsoft.Office.Tools.Excel.v4.0.Utilities.dll** hinzu.  Dieser Verweis ist erforderlich, um einem Arbeitsblatt ein Windows Forms\-Steuerelement in dieser exemplarischen Vorgehensweise später programmgesteuert hinzuzufügen.  
  
## Bereitstellen einer Benutzeroberfläche zum Hinzufügen von Steuerelementen zu einem Arbeitsblatt  
 Fügen Sie dem Excel\-Menüband eine benutzerdefinierte Registerkarte hinzu.  Benutzer können Kontrollkästchen auf der Registerkarte aktivieren, um einem Arbeitsblatt Steuerelemente hinzuzufügen.  
  
#### So stellen Sie eine Benutzeroberfläche zum Hinzufügen von Steuerelementen zu einem Arbeitsblatt bereit  
  
1.  Klicken Sie im Menü **Projekt** auf **Neues Element hinzufügen**.  
  
2.  Wählen Sie im Dialogfeld **Neues Element hinzufügen** die Option **Menüband \(Visueller Designer\)** aus, und klicken Sie auf **Hinzufügen**.  
  
     Die Datei **Ribbon1.cs** oder **Ribbon1.vb** wird im Menüband\-Designer geöffnet. Sie enthält eine standardmäßige Registerkarte und Gruppe.  
  
3.  Ziehen Sie ein CheckBox\-Steuerelement von der Registerkarte **Steuerelemente für Office\-Menübänder** der **Toolbox** auf **group1**.  
  
4.  Klicken Sie auf **CheckBox1**, um dieses Steuerelement auszuwählen.  
  
5.  Ändern Sie im Fenster **Eigenschaften** die folgenden Eigenschaften:  
  
    |Eigenschaft|Wert|  
    |-----------------|----------|  
    |**Name**|Schaltfläche|  
    |**Bezeichnung**|Schaltfläche|  
  
6.  Fügen Sie **group1** ein zweites Kontrollkästchen hinzu, und ändern Sie dann die folgenden Eigenschaften.  
  
    |Eigenschaft|Wert|  
    |-----------------|----------|  
    |**Name**|NamedRange|  
    |**Bezeichnung**|NamedRange|  
  
7.  Fügen Sie **group1** ein drittes Kontrollkästchen hinzu, und ändern Sie dann die folgenden Eigenschaften.  
  
    |Eigenschaft|Wert|  
    |-----------------|----------|  
    |**Name**|ListObject|  
    |**Bezeichnung**|ListObject|  
  
## Hinzufügen von Steuerelementen zum Arbeitsblatt  
 Verwaltete Steuerelemente können nur Hostelementen hinzugefügt werden, die als Container fungieren.  Da VSTO\-Add\-in\-Projekte mit allen geöffneten Arbeitsmappen funktionieren, konvertiert das VSTO\-Add\-In das Arbeitsblatt in ein Hostelement oder ruft ein vorhandenes Hostelement ab, bevor das Steuerelement hinzugefügt wird.  Fügen Sie den Click\-Ereignishandlern jedes Steuerelements Code hinzu, um ein auf dem geöffneten Arbeitsblatt basierendes <xref:Microsoft.Office.Tools.Excel.Worksheet>\-Hostelement zu generieren.  Fügen Sie dann ein <xref:Microsoft.Office.Tools.Excel.Controls.Button>, <xref:Microsoft.Office.Tools.Excel.NamedRange> und <xref:Microsoft.Office.Tools.Excel.ListObject> an der aktuellen Auswahlposition in das Arbeitsblatt ein.  
  
#### So fügen Sie einem Arbeitsblatt Steuerelemente hinzu  
  
1.  Doppelklicken Sie im Menüband\-Designer auf **Button**.  
  
     Der <xref:Microsoft.Office.Tools.Ribbon.RibbonCheckBox.Click>\-Ereignishandler des Kontrollkästchens **Button** wird im Code\-Editor geöffnet.  
  
2.  Ersetzen Sie den `Button_Click`\-Ereignishandler durch den folgenden Code.  
  
     Dieser Code verwendet die `GetVstoObject`\-Methode, um ein Hostelement abzurufen, das das erste Arbeitsblatt in der Arbeitsmappe darstellt, und fügt der aktuell ausgewählten Zelle dann ein <xref:Microsoft.Office.Tools.Excel.Controls.Button>\-Steuerelement hinzu.  
  
     [!code-csharp[Trin_Excel_Dynamic_Controls#2](../snippets/csharp/VS_Snippets_OfficeSP/Trin_Excel_Dynamic_Controls/CS/Ribbon1.cs#2)]
     [!code-vb[Trin_Excel_Dynamic_Controls#2](../snippets/visualbasic/VS_Snippets_OfficeSP/Trin_Excel_Dynamic_Controls/VB/Ribbon1.vb#2)]  
  
3.  Wählen Sie im **Projektmappen\-Explorer** Ribbon1.cs oder Ribbon1.vb aus.  
  
4.  Klicken Sie im Menü **Ansicht** auf **Designer**.  
  
5.  Doppelklicken Sie im Menüband\-Designer auf **NamedRange**.  
  
6.  Ersetzen Sie den `NamedRange_Click`\-Ereignishandler durch den folgenden Code.  
  
     Dieser Code verwendet die `GetVstoObject`\-Methode, um ein Hostelement abzurufen, das das erste Arbeitsblatt in der Arbeitsmappe darstellt, und fügt der oder den aktuell ausgewählten Zellen dann ein <xref:Microsoft.Office.Tools.Excel.NamedRange>\-Steuerelement hinzu.  
  
     [!code-csharp[Trin_Excel_Dynamic_Controls#3](../snippets/csharp/VS_Snippets_OfficeSP/Trin_Excel_Dynamic_Controls/CS/Ribbon1.cs#3)]
     [!code-vb[Trin_Excel_Dynamic_Controls#3](../snippets/visualbasic/VS_Snippets_OfficeSP/Trin_Excel_Dynamic_Controls/VB/Ribbon1.vb#3)]  
  
7.  Doppelklicken Sie im Menüband\-Designer auf **ListObject**.  
  
8.  Ersetzen Sie den `ListObject_Click`\-Ereignishandler durch den folgenden Code.  
  
     Dieser Code verwendet die `GetVstoObject`\-Methode, um ein Hostelement abzurufen, das das erste Arbeitsblatt in der Arbeitsmappe darstellt, und fügt der oder den aktuell ausgewählten Zellen dann ein <xref:Microsoft.Office.Tools.Excel.ListObject> hinzu.  
  
     [!code-csharp[Trin_Excel_Dynamic_Controls#4](../snippets/csharp/VS_Snippets_OfficeSP/Trin_Excel_Dynamic_Controls/CS/Ribbon1.cs#4)]
     [!code-vb[Trin_Excel_Dynamic_Controls#4](../snippets/visualbasic/VS_Snippets_OfficeSP/Trin_Excel_Dynamic_Controls/VB/Ribbon1.vb#4)]  
  
9. Fügen Sie am Anfang der Menüband\-Codedatei die folgenden Anweisungen hinzu.  
  
     [!code-csharp[Trin_Excel_Dynamic_Controls#1](../snippets/csharp/VS_Snippets_OfficeSP/Trin_Excel_Dynamic_Controls/CS/Ribbon1.cs#1)]
     [!code-vb[Trin_Excel_Dynamic_Controls#1](../snippets/visualbasic/VS_Snippets_OfficeSP/Trin_Excel_Dynamic_Controls/VB/Ribbon1.vb#1)]  
  
## Entfernen von Steuerelementen aus dem Arbeitsblatt  
 Steuerelemente werden nicht beibehalten, wenn das Arbeitsblatt gespeichert und geschlossen wird.  Sie sollten alle generierten Windows Forms\-Steuerelemente programmgesteuert entfernen, bevor das Arbeitsblatt gespeichert wird, ansonsten wird beim erneuten Öffnen der Arbeitsmappe nur ein Umriss des Steuerelements angezeigt.  Fügen Sie dem <xref:Microsoft.Office.Interop.Excel.AppEvents_Event.WorkbookBeforeSave>\-Ereignis Code hinzu, durch den Windows Forms\-Steuerelemente aus der Steuerelementauflistung des generierten Hostelements entfernt werden.  Weitere Informationen finden Sie unter [Beibehalten von dynamischen Steuerelementen in Office-Dokumenten](../vsto/persisting-dynamic-controls-in-office-documents.md).  
  
#### So entfernen Sie Steuerelemente aus dem Arbeitsblatt  
  
1.  Wählen Sie im **Projektmappen\-Explorer** "ThisAddIn.cs" oder "ThisAddIn.vb" aus.  
  
2.  Klicken Sie im Menü **Ansicht** auf **Code**.  
  
3.  Fügen Sie der ThisAddin\-Klasse die folgende Methode hinzu.  Durch diesen Code wird das erste Arbeitsblatt in der Arbeitsmappe abgerufen und dann anhand der `HasVstoObject`\-Methode überprüft, ob das Arbeitsblatt über ein generiertes Arbeitsblattobjekt verfügt.  Wenn das generierte Arbeitsblattobjekt über Steuerelemente verfügt, ruft der Code das Arbeitsblattobjekt ab und durchläuft die Steuerelementauflistung, um Steuerelemente zu entfernen.  
  
     [!code-csharp[Trin_Excel_Dynamic_Controls#6](../snippets/csharp/VS_Snippets_OfficeSP/Trin_Excel_Dynamic_Controls/CS/ThisAddIn.cs#6)]
     [!code-vb[Trin_Excel_Dynamic_Controls#6](../snippets/visualbasic/VS_Snippets_OfficeSP/Trin_Excel_Dynamic_Controls/VB/ThisAddIn.vb#6)]  
  
4.  In C\# müssen Sie einen Ereignishandler für das <xref:Microsoft.Office.Interop.Excel.AppEvents_Event.WorkbookBeforeSave>\-Ereignis erstellen.  Sie können diesen Code in der `ThisAddIn_Startup`\-Methode positionieren.  Informationen zum Erstellen von Ereignishandlern finden Sie unter [Gewusst wie: Erstellen von Ereignishandlern in Office-Projekten](../vsto/how-to-create-event-handlers-in-office-projects.md).  Ersetzen Sie die `ThisAddIn_Startup`\-Methode durch folgenden Code:  
  
     [!code-csharp[Trin_Excel_Dynamic_Controls#5](../snippets/csharp/VS_Snippets_OfficeSP/Trin_Excel_Dynamic_Controls/CS/ThisAddIn.cs#5)]  
  
## Testen der Projektmappe  
 Fügen Sie einem Arbeitsblatt Steuerelemente hinzu, indem Sie sie von einer benutzerdefinierten Registerkarte des Menübands auswählen.  Diese Steuerelemente werden beim Speichern des Arbeitsblatts entfernt.  
  
#### So testen Sie die Projektmappe  
  
1.  Drücken Sie F5, um das Projekt auszuführen.  
  
2.  Wählen Sie eine beliebige Zelle in Tabelle1 aus.  
  
3.  Klicken Sie auf die Registerkarte **Add\-Ins**.  
  
4.  Klicken Sie in der Gruppe **group1** auf **Button**.  
  
     In der ausgewählten Zelle wird eine Schaltfläche angezeigt.  
  
5.  Wählen Sie eine andere Zelle in Tabelle1 aus.  
  
6.  Klicken Sie in der Gruppe **group1** auf **NamedRange**.  
  
     Für die ausgewählte Zelle wird ein benannter Bereich definiert.  
  
7.  Wählen Sie eine Reihe von Zellen in Tabelle1 aus.  
  
8.  Klicken Sie in der Gruppe **group1** auf **ListObject**.  
  
     Für die ausgewählten Zellen wird ein Listenobjekt hinzugefügt.  
  
9. Speichern Sie das Arbeitsblatt.  
  
     Die Steuerelemente, die Sie Tabelle1 hinzugefügt haben, werden nicht mehr angezeigt.  
  
## Nächste Schritte  
 Im folgenden Thema erfahren Sie mehr über Steuerelemente in Excel\-VSTO\-Add\-In\-Projekten:  
  
-   Wenn Sie mehr über das Speichern von Steuerelementen in einem Arbeitsblatt erfahren möchten, sehen Sie sich das Excel\-VSTO\-Add\-In für dynamische Steuerelemente unter [Beispiele und exemplarische Vorgehensweisen für die Programmierung mit Office](../vsto/office-development-samples-and-walkthroughs.md) an.  
  
## Siehe auch  
 [Excel-Projektmappen](../vsto/excel-solutions.md)   
 [Übersicht über Windows Forms-Steuerelemente in Office-Dokumenten](../vsto/windows-forms-controls-on-office-documents-overview.md)   
 [Steuerelemente für Office-Dokumente](../vsto/controls-on-office-documents.md)   
 [NamedRange-Steuerelement](../vsto/namedrange-control.md)   
 [ListObject-Steuerelement](../vsto/listobject-control.md)  
  
  