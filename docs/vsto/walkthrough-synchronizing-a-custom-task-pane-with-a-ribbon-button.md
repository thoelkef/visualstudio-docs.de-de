---
title: "Exemplarische Vorgehensweise: Synchronisieren eines benutzerdefinierten Aufgabenbereichs mit einer Multifunktionsleistenschaltfl&#228;che | Microsoft Docs"
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
  - "Benutzerdefinierte Aufgabenbereiche [Office-Entwicklung in Visual Studio], Anzeigen und Ausblenden"
  - "Anzeigen von benutzerdefinierten Aufgabenbereichen"
  - "Menüband [Office-Entwicklung in Visual Studio], Benutzerdefinierte Aufgabenbereiche"
  - "Umschaltflächen [Office-Entwicklung in Visual Studio]"
  - "Benutzerdefinierte Aufgabenbereiche [Office-Entwicklung in Visual Studio], Synchronisieren mit Menübandschaltfläche"
  - "Benutzeroberflächen [Office-Entwicklung in Visual Studio], Benutzerdefinierte Aufgabenbereiche"
  - "Synchronisierung [Office-Entwicklung in Visual Studio], Benutzerdefinierte Aufgabenbereiche"
  - "Aufgabenbereiche [Office-Entwicklung in Visual Studio], Anzeigen und Ausblenden"
  - "Benutzerdefinierte Aufgabenbereiche [Office-Entwicklung in Visual Studio], Erstellen"
  - "Ausblenden von benutzerdefinierten Aufgabenbereichen"
  - "Aufgabenbereiche [Office-Entwicklung in Visual Studio], Erstellen"
  - "Aufgabenbereiche [Office-Entwicklung in Visual Studio], Synchronisieren mit Menübandschaltfläche"
ms.assetid: 00ce8b1e-1370-42f2-9dc9-609cada392f1
caps.latest.revision: 38
author: "kempb"
ms.author: "kempb"
manager: "ghogen"
caps.handback.revision: 37
---
# Exemplarische Vorgehensweise: Synchronisieren eines benutzerdefinierten Aufgabenbereichs mit einer Multifunktionsleistenschaltfl&#228;che
  Diese exemplarische Vorgehensweise veranschaulicht, wie ein benutzerdefinierter Aufgabenbereich erstellt wird, den Benutzer durch Klicken auf eine Umschaltfläche auf dem Menüband anzeigen oder ausblenden können. Sie sollten immer ein UI\-Element erstellen, z. B. eine Schaltfläche, auf die Benutzer klicken können, um Ihren benutzerdefinierten Aufgabenbereich anzeigen oder ausblenden zu können, da Microsoft Office\-Anwendung keine Standardmethode für Benutzer bereitstellen, um benutzerdefinierte Aufgabenbereiche anzuzeigen oder auszublenden.  
  
 [!INCLUDE[appliesto_olkallapp](../vsto/includes/appliesto-olkallapp-md.md)]  
  
 Obwohl in dieser exemplarischen Vorgehensweise speziell Excel verwendet wird, gelten die Konzepte in dieser exemplarischen Vorgehensweise für alle oben aufgelisteten Anwendungen.  
  
 In dieser exemplarischen Vorgehensweise werden die folgenden Aufgaben veranschaulicht:  
  
-   Entwerfen der Benutzeroberfläche \(UI\) des benutzerdefinierten Aufgabenbereichs  
  
-   Hinzufügen einer Umschaltfläche zum Menüband  
  
-   Synchronisieren der Umschaltfläche mit dem benutzerdefinierten Aufgabenbereich  
  
> [!NOTE]  
>  Auf Ihrem Computer werden möglicherweise andere Namen oder Speicherorte für die Benutzeroberflächenelemente von Visual Studio angezeigt als die in den folgenden Anweisungen aufgeführten. Diese Elemente sind von der jeweiligen Visual Studio\-Version und den verwendeten Einstellungen abhängig. Weitere Informationen finden Sie unter [Anpassen der Entwicklungseinstellungen in Visual Studio](http://msdn.microsoft.com/de-de/22c4debb-4e31-47a8-8f19-16f328d7dcd3).  
  
## Vorbereitungsmaßnahmen  
 Zum Durchführen dieser exemplarischen Vorgehensweise benötigen Sie die folgenden Komponenten:  
  
-   [!INCLUDE[vsto_vsprereq](../vsto/includes/vsto-vsprereq-md.md)]  
  
-   Microsoft Excel oder Microsoft [!INCLUDE[Excel_15_short](../vsto/includes/excel-15-short-md.md)].  
  
## Erstellen des Add\-In\-Projekts  
 In diesem Abschnitt erstellen Sie ein VSTO\-Add\-In\-Projekt für Excel.  
  
#### So erstellen Sie ein neues Projekt  
  
1.  Erstellen Sie ein Add\-In\-Projekt für Excel namens **SynchronizeTaskPaneAndRibbon**, indem Sie die Add\-In\-Projektvorlage für Excel verwenden. Weitere Informationen finden Sie unter [Gewusst wie: Erstellen von Office-Projekten in Visual Studio](../vsto/how-to-create-office-projects-in-visual-studio.md).  
  
     [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] öffnet die Codedatei **ThisAddIn.cs** oder **ThisAddIn.vb** und fügt das Projekt **SynchronizeTaskPaneAndRibbon** dem **Projektmappen\-Explorer** hinzu.  
  
## Hinzufügen einer Umschaltfläche zum Menüband  
 Eine der Entwurfsrichtlinien für Office\-Anwendungen besagt, dass Benutzer immer die Möglichkeit haben sollen, die Benutzeroberfläche von Office\-Anwendungen zu steuern. Damit Benutzer den benutzerdefinierten Aufgabenbereich steuern können, können Sie eine Menübandumschaltfläche hinzufügen, die den Aufgabenbereich anzeigt oder ausblendet. Fügen Sie zum Erstellen einer Umschaltfläche dem Projekt ein Element von **Menüband \(Visueller Designer\)** hinzu. Der Designer unterstützt Sie beim Hinzufügen und Anordnen von Steuerelementen, Festlegen von Steuerelementeigenschaften und Behandeln von Ereignissen von Steuerelementen. Weitere Informationen finden Sie unter [Multifunktionsleisten-Designer](../vsto/ribbon-designer.md).  
  
#### So fügen Sie eine Umschaltfläche zum Menüband hinzu  
  
1.  Klicken Sie im Menü **Projekt** auf **Neues Element hinzufügen**.  
  
2.  Wählen Sie im Dialogfeld **Neues Element hinzufügen** die Option **Menüband \(Visueller Designer\)** aus.  
  
3.  Ändern Sie den Namen des neuen Menübands in **ManageTaskPaneRibbon**, und klicken Sie auf **Hinzufügen**.  
  
     Die Datei **ManageTaskPaneRibbon.cs** oder **ManageTaskPaneRibbon.vb** wird im Menüband\-Designer geöffnet. Sie enthält eine Standardregisterkarte und eine Gruppe.  
  
4.  Klicken Sie im Menüband\-Designer auf **group1**.  
  
5.  Legen Sie im Fenster **Eigenschaften** die **Label**\-Eigenschaft auf **Aufgabenbereich\-Manager** fest.  
  
6.  Ziehen Sie ein **ToggleButton**\-Steuerelement von der Registerkarte **Steuerelemente für Office\-Menübänder** der **Toolbox** auf die Gruppe **Aufgabenbereich\-Manager**.  
  
7.  Klicken Sie auf **toggleButton1**.  
  
8.  Legen Sie im Fenster **Eigenschaften** die **Label**\-Eigenschaft auf **Aufgabenbereich anzeigen** fest.  
  
## Entwerfen der Benutzeroberfläche des benutzerdefinierten Aufgabenbereichs  
 Es gibt keinen visuellen Designer für benutzerdefinierte Aufgabenbereiche, Sie können aber dennoch ein Benutzersteuerelement mit dem gewünschten Layout entwerfen. Im weiteren Verlauf dieser exemplarischen Vorgehensweise fügen Sie dem benutzerdefinierten Aufgabenbereich das Benutzersteuerelement hinzu.  
  
#### So entwerfen Sie die Benutzeroberfläche des benutzerdefinierten Aufgabenbereichs  
  
1.  Klicken Sie im Menü **Projekt** auf **Benutzersteuerelement hinzufügen**.  
  
2.  Ändern Sie im Dialogfeld **Neues Element hinzufügen** den Namen des neuen Benutzersteuerelements in **TaskPaneControl**, und klicken Sie dann auf **Hinzufügen**.  
  
     Das Benutzersteuerelement wird im Designer geöffnet.  
  
3.  Ziehen Sie von der Registerkarte **Allgemeine Steuerelemente** der **Toolbox** ein **TextBox**\-Steuerelement auf das Benutzersteuerelement.  
  
## Erstellen des benutzerdefinierten Aufgabenbereichs  
 Um den benutzerdefinierten Aufgabenbereich beim Starten des VSTO\-Add\-Ins zu erstellen, fügen Sie dem Aufgabenbereich das Benutzersteuerelement im <xref:Microsoft.Office.Tools.AddIn.Startup>\-Ereignishandler des VSTO\-Add\-Ins hinzu. Standardmäßig wird der benutzerdefinierte Aufgabenbereich nicht angezeigt. Weiter unten in dieser exemplarischen Vorgehensweise werden Sie Code hinzufügen, der den Aufgabenbereich anzeigt oder ausblendet, wenn der Benutzer auf die Umschaltfläche klickt, die Sie dem Menüband hinzugefügt haben.  
  
#### So erstellen Sie den benutzerdefinierten Aufgabenbereich  
  
1.  Erweitern Sie im **Projektmappen\-Explorer** die Option **Excel**.  
  
2.  Klicken Sie mit der rechten Maustaste auf **ThisAddIn.cs** oder **ThisAddIn.vb**, und klicken Sie auf **Code anzeigen**.  
  
3.  Fügen Sie der `ThisAddIn`\-Klasse folgenden Code hinzu. Durch diesen Code wird eine Instanz von `TaskPaneControl` als Member von `ThisAddIn` deklariert.  
  
     [!code-csharp[Trin_TaskPaneRibbonSynchronize#1](../snippets/csharp/VS_Snippets_OfficeSP/Trin_TaskPaneRibbonSynchronize/CS/ThisAddIn.cs#1)]
     [!code-vb[Trin_TaskPaneRibbonSynchronize#1](../snippets/visualbasic/VS_Snippets_OfficeSP/Trin_TaskPaneRibbonSynchronize/VB/ThisAddIn.vb#1)]  
  
4.  Ersetzen Sie den `ThisAddIn_Startup`\-Ereignishandler durch den folgenden Code. Dieser Code fügt das `TaskPaneControl`\-Objekt zum `CustomTaskPanes`\-Feld hinzu, zeigt aber nicht den benutzerdefinierten Aufgabenbereich an \(standardmäßig ist die <xref:Microsoft.Office.Tools.CustomTaskPane.Visible%2A>\-Eigenschaft der <xref:Microsoft.Office.Tools.CustomTaskPane>\-Klasse **false**\). Der Visual C\#\-Code fügt dem <xref:Microsoft.Office.Tools.CustomTaskPane.VisibleChanged>\-Ereignis auch einen Ereignishandler an.  
  
     [!code-csharp[Trin_TaskPaneRibbonSynchronize#2](../snippets/csharp/VS_Snippets_OfficeSP/Trin_TaskPaneRibbonSynchronize/CS/ThisAddIn.cs#2)]
     [!code-vb[Trin_TaskPaneRibbonSynchronize#2](../snippets/visualbasic/VS_Snippets_OfficeSP/Trin_TaskPaneRibbonSynchronize/VB/ThisAddIn.vb#2)]  
  
5.  Fügen Sie der `ThisAddIn`\-Klasse die folgende Methode hinzu. Diese Methode behandelt das <xref:Microsoft.Office.Tools.CustomTaskPane.VisibleChanged>\-Ereignis. Wenn der Benutzer den Aufgabenbereich durch Klicken auf die Schaltfläche **Schließen** \(X\) schließt, aktualisiert diese Methode den Zustand der Umschaltfläche im Menüband.  
  
     [!code-csharp[Trin_TaskPaneRibbonSynchronize#3](../snippets/csharp/VS_Snippets_OfficeSP/Trin_TaskPaneRibbonSynchronize/CS/ThisAddIn.cs#3)]
     [!code-vb[Trin_TaskPaneRibbonSynchronize#3](../snippets/visualbasic/VS_Snippets_OfficeSP/Trin_TaskPaneRibbonSynchronize/VB/ThisAddIn.vb#3)]  
  
6.  Fügen Sie der `ThisAddIn`\-Klasse folgende Eigenschaft hinzu. Diese Eigenschaft stellt das private `myCustomTaskPane1`\-Objekt für andere Klassen bereit. Weiter unten in dieser exemplarischen Vorgehensweise werden Sie Code zur `MyRibbon`\-Klasse hinzufügen, der diese Eigenschaft verwendet.  
  
     [!code-csharp[Trin_TaskPaneRibbonSynchronize#4](../snippets/csharp/VS_Snippets_OfficeSP/Trin_TaskPaneRibbonSynchronize/CS/ThisAddIn.cs#4)]
     [!code-vb[Trin_TaskPaneRibbonSynchronize#4](../snippets/visualbasic/VS_Snippets_OfficeSP/Trin_TaskPaneRibbonSynchronize/VB/ThisAddIn.vb#4)]  
  
## Ausblenden und Anzeigen des benutzerdefinierte Aufgabenbereichs mit der Umschaltfläche  
 Im letzte Schritt wird Code hinzugefügt, der den benutzerdefinierten Aufgabenbereich anzeigt oder ausblendet, wenn der Benutzer im Menüband auf die Umschaltfläche klickt.  
  
#### So zeigen Sie den benutzerdefinierten Aufgabenbereich mithilfe der Umschaltfläche an oder blenden ihn aus  
  
1.  Doppelklicken Sie im Menüband\-Designer auf die Umschaltfläche **Aufgabenbereich anzeigen**.  
  
     Visual Studio generiert automatisch einen Ereignishandler namens `toggleButton1_Click`, der das <xref:Microsoft.Office.Tools.Ribbon.RibbonToggleButton.Click>\-Ereignis der Umschaltfläche verarbeitet. Visual Studio öffnet außerdem die Datei **MyRibbon.cs** oder **MyRibbon.vb** im Code\-Editor.  
  
2.  Ersetzen Sie den `toggleButton1_Click`\-Ereignishandler durch den folgenden Code. Wenn der Benutzer auf die Umschaltfläche klickt, zeigt dieser Code den benutzerdefinierten Aufgabenbereich an oder blendet ihn aus, je nachdem, ob die Umschaltfläche gedrückt wird oder nicht.  
  
     [!code-csharp[Trin_TaskPaneRibbonSynchronize#5](../snippets/csharp/VS_Snippets_OfficeSP/Trin_TaskPaneRibbonSynchronize/CS/ManageTaskPaneRibbon.cs#5)]
     [!code-vb[Trin_TaskPaneRibbonSynchronize#5](../snippets/visualbasic/VS_Snippets_OfficeSP/Trin_TaskPaneRibbonSynchronize/VB/ManageTaskPaneRibbon.vb#5)]  
  
## Testen des Add\-Ins  
 Wenn Sie das Projekt ausführen, wird Excel geöffnet, ohne den benutzerdefinierten Aufgabenbereich anzuzeigen. Klicken Sie im Menüband auf die Umschaltfläche, um den Code zu testen.  
  
#### So testen Sie Ihr VSTO\-Add\-In  
  
1.  Drücken Sie F5, um das Projekt auszuführen.  
  
     Vergewissern Sie sich, dass Excel geöffnet wird und die Registerkarte **Add\-Ins** im Menüband angezeigt wird.  
  
2.  Klicken Sie im Menüband auf die Registerkarte **Add\-Ins**.  
  
3.  Klicken Sie auf die Gruppe **Aufgabenbereich\-Manager** und dann auf die Umschaltfläche **Aufgabenbereich anzeigen**.  
  
     Überprüfen Sie, ob der Aufgabenbereich abwechselnd angezeigt und ausgeblendet wird, wenn Sie auf die Umschaltfläche klicken.  
  
4.  Wenn der Aufgabenbereich angezeigt wird, klicken Sie in der Ecke des Aufgabenbereichs auf die Schaltfläche **Schließen** \(X\).  
  
     Stellen Sie sicher, dass die Umschaltfläche als nicht gedrückt angezeigt wird.  
  
## Nächste Schritte  
 Weitere Informationen über das Erstellen von benutzerdefinierten Aufgabenbereichen finden Sie in diesen Themen:  
  
-   Erstellen eines benutzerdefinierten Aufgabenbereichs in einem VSTO\-Add\-In für eine andere Anwendung. Weitere Informationen über die Anwendungen, die benutzerdefinierte Aufgabenbereiche unterstützen, finden Sie unter [Benutzerdefinierte Aufgabenbereiche](../vsto/custom-task-panes.md).  
  
-   Automatisieren einer Anwendung über einen benutzerdefinierten Aufgabenbereich Weitere Informationen finden Sie unter [Exemplarische Vorgehensweise: Automatisieren einer Anwendung über einen benutzerdefinierten Aufgabenbereich](../vsto/walkthrough-automating-an-application-from-a-custom-task-pane.md).  
  
-   Erstellen eines benutzerdefinierten Aufgabenbereichs für jede E\-Mail\-Nachricht, die in Outlook geöffnet wird. Weitere Informationen finden Sie unter [Exemplarische Vorgehensweise: Anzeigen von benutzerdefinierten Aufgabenbereichen in E-Mails in Outlook](../vsto/walkthrough-displaying-custom-task-panes-with-e-mail-messages-in-outlook.md).  
  
## Siehe auch  
 [Benutzerdefinierte Aufgabenbereiche](../vsto/custom-task-panes.md)   
 [Gewusst wie: Hinzufügen eines benutzerdefinierten Aufgabenbereichs zu einer Anwendung](../vsto/how-to-add-a-custom-task-pane-to-an-application.md)   
 [Exemplarische Vorgehensweise: Automatisieren einer Anwendung über einen benutzerdefinierten Aufgabenbereich](../vsto/walkthrough-automating-an-application-from-a-custom-task-pane.md)   
 [Exemplarische Vorgehensweise: Anzeigen von benutzerdefinierten Aufgabenbereichen in E-Mails in Outlook](../vsto/walkthrough-displaying-custom-task-panes-with-e-mail-messages-in-outlook.md)   
 [Übersicht über die Multifunktionsleiste](../vsto/ribbon-overview.md)  
  
  