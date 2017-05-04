---
title: "Exemplarische Vorgehensweise: Erstellen einer benutzerdefinierten Registerkarte mit dem Multifunktionsleisten-Designer | Microsoft Docs"
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
  - "Aktionsbereiche [Office-Entwicklung in Visual Studio], Steuern mit der Multifunktionsleiste"
  - "Benutzerdefiniertes Menüband, Registerkarten"
  - "Benutzerdefinierte Registerkarte [Office-Entwicklung in Visual Studio]"
  - "Anpassen des Menübands, Registerkarten"
  - "Menüband [Office-Entwicklung in Visual Studio], Anpassen"
  - "Menüband-Designer [Office-Entwicklung in Visual Studio]"
ms.assetid: 312865e6-950f-46ab-88de-fe7eb8036bfe
caps.latest.revision: 68
author: "kempb"
ms.author: "kempb"
manager: "ghogen"
caps.handback.revision: 67
---
# Exemplarische Vorgehensweise: Erstellen einer benutzerdefinierten Registerkarte mit dem Multifunktionsleisten-Designer
  Mit dem Menüband\-Designer können Steuerelemente auf der benutzerdefinierten Registerkarte hinzugefügt und positioniert werden.  
  
 [!INCLUDE[appliesto_xlalldoc](../vsto/includes/appliesto-xlalldoc-md.md)]  
  
 In dieser exemplarischen Vorgehensweise werden die folgenden Aufgaben veranschaulicht:  
  
-   [Erstellen von Aktionsbereichen](#BKMK_CreateActionsPanes).  
  
-   [Erstellen einer benutzerdefinierten Registerkarte](#BKMK_CreateCustomTab).  
  
-   [Ausblenden und Anzeigen von Aktionsbereichen mithilfe von Schaltflächen auf der benutzerdefinierten Registerkarte](#BKMK_HideShowActionsPane).  
  
> [!NOTE]  
>  Auf Ihrem Computer werden möglicherweise andere Namen oder Speicherorte für die Benutzeroberflächenelemente von Visual Studio angezeigt als die in den folgenden Anweisungen aufgeführten.  Diese Elemente sind von der jeweiligen Visual Studio\-Version und den verwendeten Einstellungen abhängig.  Weitere Informationen finden Sie unter [Customizing Development Settings in Visual Studio](http://msdn.microsoft.com/de-de/22c4debb-4e31-47a8-8f19-16f328d7dcd3).  
  
## Vorbereitungsmaßnahmen  
 Zum Durchführen dieser exemplarischen Vorgehensweise benötigen Sie die folgenden Komponenten:  
  
-   [!INCLUDE[vsto_vsprereq](../vsto/includes/vsto-vsprereq-md.md)]  
  
-   Microsoft Excel  
  
## Erstellen eines Excel\-Arbeitsmappenprojekts  
 Die Schritte für die Verwendung des Menüband\-Designers sind für alle Office\-Anwendungen nahezu identisch.  In diesem Beispiel wird eine Excel\-Arbeitsmappe verwendet.  
  
#### So erstellen Sie ein Excel\-Arbeitsmappenprojekt  
  
-   Erstellen Sie ein Excel\-Arbeitsmappenprojekt mit dem Namen "MyExcelRibbon".  Weitere Informationen finden Sie unter [Gewusst wie: Erstellen von Office-Projekten in Visual Studio](../vsto/how-to-create-office-projects-in-visual-studio.md).  
  
     Visual Studio öffnet die neue Excel\-Arbeitsmappe im Designer und fügt dem **Projektmappen\-Explorer** das **MyExcelRibbon**\-Projekt hinzu.  
  
##  <a name="BKMK_CreateActionsPanes"></a> Erstellen von Aktionsbereichen  
 Fügen Sie dem Projekt zwei benutzerdefinierte Aktionsbereiche hinzu.  Später werden der benutzerdefinierten Registerkarte Schaltflächen hinzugefügt, mit denen diese Aktionsbereiche angezeigt und ausgeblendet werden.  
  
#### So erstellen Sie Aktionsbereiche  
  
1.  Klicken Sie im Menü **Projekt** auf **Neues Element hinzufügen**.  
  
2.  Wählen Sie im Dialogfeld **Neues Element hinzufügen** die Option **ActionsPaneControl** und dann **Hinzufügen** aus.  
  
     Im Designer wird die Datei **ActionsPaneControl1.cs** oder die Datei **ActionsPaneControl1.vb** geöffnet.  
  
3.  Fügen Sie der Oberfläche des Designers auf der Registerkarte **Allgemeine Steuerelemente** der **Toolbox** eine Bezeichnung hinzu.  
  
4.  Legen Sie im Fenster **Eigenschaften** die **Text**\-Eigenschaft von label1 auf "Actions Pane 1" fest.  
  
5.  Wiederholen Sie die Schritte 1 bis 5, um einen zweiten Aktionsbereich und eine Bezeichnung zu erstellen.  Legen Sie die **Text**\-Eigenschaft der zweiten Bezeichnung auf "Actions Pane 2" fest.  
  
##  <a name="BKMK_CreateCustomTab"></a> Erstellen einer benutzerdefinierten Registerkarte  
 Eine der Entwurfsrichtlinien für Office\-Anwendungen besagt, dass Benutzer immer die Möglichkeit haben sollen, die Benutzeroberfläche von Office\-Anwendungen zu steuern.  Um diese Funktion für die Aktionsbereiche hinzuzufügen, können Schaltflächen hinzugefügt werden, mit denen jeder Aktionsbereich von einer benutzerdefinierten Registerkarte auf dem Menüband angezeigt und ausgeblendet werden kann.  Fügen Sie zum Erstellen einer benutzerdefinierten Registerkarte dem Projekt ein Element von **Menüband \(Visueller Designer\)** hinzu.  Der Designer unterstützt Sie beim Hinzufügen und Anordnen von Steuerelementen, Festlegen von Steuerelementeigenschaften und Behandeln von Ereignissen von Steuerelementen.  
  
#### So erstellen Sie eine benutzerdefinierte Registerkarte  
  
1.  Klicken Sie im Menü **Projekt** auf **Neues Element hinzufügen**.  
  
2.  Wählen Sie im Dialogfeld **Neues Element hinzufügen** die Option **Menüband \(Visueller Designer\)** aus.  
  
3.  Ändern Sie den Namen des neuen Menübands in **MyRibbon**, und wählen Sie **Hinzufügen** aus.  
  
     Die Datei **MyRibbon.cs** oder **MyRibbon.vb** wird im Menüband\-Designer geöffnet. Sie beinhaltet eine standardmäßige Registerkarte und eine Gruppe.  
  
4.  Wählen Sie im Menüband\-Designer die Standardregisterkarte aus.  
  
5.  Erweitern Sie im Fenster **Eigenschaften** die **ControlId**\-Eigenschaft, und legen Sie anschließend die **ControlIdType**\-Eigenschaft auf **Benutzerdefiniert** fest.  
  
6.  Legen Sie die Eigenschaft **Bezeichnung** auf "Meine benutzerdefinierte Registerkarte" fest.  
  
7.  Wählen Sie im Menüband\-Designer **group1** aus.  
  
8.  Legen Sie im Fenster **Eigenschaften** die **Label**\-Eigenschaft auf "Actions Pane Manager" fest.  
  
9. Ziehen Sie von der Registerkarte **Steuerelemente für Office\-Menübänder** der **Toolbox** eine Schaltfläche auf **group1**.  
  
10. Wählen Sie **button1** aus.  
  
11. Legen Sie im Fenster **Eigenschaften** die **Label**\-Eigenschaft auf "Show Actions Pane 1" fest.  
  
12. Fügen Sie **group1** eine zweite Schaltfläche hinzu, und legen Sie die **Label**\-Eigenschaft auf "Show Actions Pane 2" fest.  
  
13. Ziehen Sie von der Registerkarte **Steuerelemente für Office\-Menübänder** der **Toolbox** ein **ToggleButton**\-Steuerelement zu **group1**.  
  
14. Legen Sie die **Label**\-Eigenschaft auf "Hide Actions Pane" fest.  
  
##  <a name="BKMK_HideShowActionsPane"></a> Ausblenden und Anzeigen von Aktionsbereichen mithilfe von Schaltflächen auf der benutzerdefinierten Registerkarte  
 Im letzten Schritt wird Code hinzugefügt, der auf den Benutzer reagiert.  Fügen Sie Ereignishandler für die <xref:Microsoft.Office.Tools.Ribbon.RibbonButton.Click>\-Ereignisse der zwei Schaltflächen und das <xref:Microsoft.Office.Tools.Ribbon.RibbonToggleButton.Click>\-Ereignis der Umschaltfläche hinzu.  Fügen Sie diesen Ereignishandlern Code hinzu, um das Aus\- und Einblenden der Aktionsbereiche zu aktivieren.  
  
#### So werden Aktionsbereiche mithilfe von Schaltflächen auf der benutzerdefinierten Registerkarte ausgeblendet und angezeigt  
  
1.  Öffnen Sie im **Projektmappen\-Explorer** das Kontextmenü für "MyRibbon.cs" oder "MyRibbon.vb", und wählen Sie dann **Code anzeigen** aus.  
  
2.  Fügen Sie oben in der `MyRibbon`\-Klasse den folgenden Code hinzu:  Mit diesem Code werden zwei Aktionsbereichobjekte erstellt.  
  
     [!code-csharp[Trin_Ribbon_Custom_Tab#1](../snippets/csharp/VS_Snippets_OfficeSP/Trin_Ribbon_Custom_Tab/CS/MyRibbon.cs#1)]
     [!code-vb[Trin_Ribbon_Custom_Tab#1](../snippets/visualbasic/VS_Snippets_OfficeSP/Trin_Ribbon_Custom_Tab/VB/MyRibbon.vb#1)]  
  
3.  Ersetzen Sie die `MyRibbon_Load`\-Methode durch folgenden Code:  Mit diesem Code werden die Aktionsbereichsobjekte der <xref:Microsoft.Office.Tools.ActionsPane.Controls%2A>\-Auflistung hinzugefügt und die Objekte ausgeblendet.  Durch den Visual C\#\-Code werden außerdem Delegate an mehrere Menüband\-Steuerelementereignisse angefügt.  
  
     [!code-csharp[Trin_Ribbon_Custom_Tab#2](../snippets/csharp/VS_Snippets_OfficeSP/Trin_Ribbon_Custom_Tab/CS/MyRibbon.cs#2)]
     [!code-vb[Trin_Ribbon_Custom_Tab#2](../snippets/visualbasic/VS_Snippets_OfficeSP/Trin_Ribbon_Custom_Tab/VB/MyRibbon.vb#2)]  
  
4.  Fügen Sie der `MyRibbon`\-Klasse die folgenden drei Ereignishandlermethoden hinzu.  Diese Methoden dienen zur Behandlung der <xref:Microsoft.Office.Tools.Ribbon.RibbonButton.Click>\-Ereignisse der zwei Schaltflächen und des <xref:Microsoft.Office.Tools.Ribbon.RibbonToggleButton.Click>\-Ereignisses der Umschaltfläche.  Die Ereignishandler für button1 und button2 zeigen andere Aktionsbereiche an.  Der Ereignishandler für toggleButton1 zeigt den aktiven Aktionsbereich an und blendet diesen aus.  
  
     [!code-csharp[Trin_Ribbon_Custom_Tab#3](../snippets/csharp/VS_Snippets_OfficeSP/Trin_Ribbon_Custom_Tab/CS/MyRibbon.cs#3)]
     [!code-vb[Trin_Ribbon_Custom_Tab#3](../snippets/visualbasic/VS_Snippets_OfficeSP/Trin_Ribbon_Custom_Tab/VB/MyRibbon.vb#3)]  
  
## Testen der benutzerdefinierten Registerkarte  
 Beim Ausführen des Projekts wird Excel gestartet, und die Registerkarte **Meine benutzerdefinierte Registerkarte** wird auf dem Menüband angezeigt.  Wählen Sie die Schaltflächen der Registerkarte **Meine benutzerdefinierte Registerkarte** aus, um die Aktionsbereiche ein\- und auszublenden.  
  
#### So testen Sie die benutzerdefinierte Registerkarte  
  
1.  Drücken Sie F5, um das Projekt auszuführen.  
  
2.  Wählen Sie die Registerkarte **Meine benutzerdefinierte Registerkarte** aus.  
  
3.  Wählen Sie in der Gruppe **Custom Actions Pane Manager** die Option **Show Actions Pane 1** aus.  
  
     Im daraufhin erscheinenden Aktionsbereich wird die Actions Pane 1\-Bezeichnung angezeigt.  
  
4.  Wählen Sie **Show Actions Pane 2** aus.  
  
     Im daraufhin erscheinenden Aktionsbereich wird die Actions Pane 2\-Bezeichnung angezeigt.  
  
5.  Wählen Sie **Hide Actions Pane** aus.  
  
     Die Aktionsbereiche werden nicht mehr angezeigt.  
  
## Nächste Schritte  
 Weitere Informationen zum Anpassen der Office\-Benutzeroberfläche finden Sie in diesen Themen:  
  
-   Fügen Sie jeder Anpassung auf Dokumentebene kontextbasierte Benutzeroberfläche hinzu.  Weitere Informationen finden Sie unter [Aktionsbereichsübersicht](../vsto/actions-pane-overview.md).  
  
-   Erweitern Sie ein standardmäßiges oder benutzerdefiniertes Microsoft Office Outlook\-Formular.  Weitere Informationen finden Sie unter [Exemplarische Vorgehensweise: Entwerfen eines Outlook-Formularbereichs](../vsto/walkthrough-designing-an-outlook-form-region.md).  
  
## Siehe auch  
 [Zugreifen auf die Multifunktionsleiste zur Laufzeit](../vsto/accessing-the-ribbon-at-run-time.md)   
 [Übersicht über die Multifunktionsleiste](../vsto/ribbon-overview.md)   
 [Multifunktionsleisten-Designer](../vsto/ribbon-designer.md)   
 [Anpassen einer Multifunktionsleiste in Outlook](../vsto/customizing-a-ribbon-for-outlook.md)   
 [Gewusst wie: Erste Schritte beim Anpassen der Multifunktionsleiste](../vsto/how-to-get-started-customizing-the-ribbon.md)   
 [Gewusst wie: Ändern der Position einer Registerkarte im Menüband](../vsto/how-to-change-the-position-of-a-tab-on-the-ribbon.md)   
 [Gewusst wie: Anpassen einer integrierten Registerkarte](../vsto/how-to-customize-a-built-in-tab.md)   
 [Gewusst wie: Hinzufügen von Steuerelementen zur Backstage-Ansicht](../vsto/how-to-add-controls-to-the-backstage-view.md)   
 [Multifunktionsleisten-Objektmodellübersicht](../vsto/ribbon-object-model-overview.md)  
  
  