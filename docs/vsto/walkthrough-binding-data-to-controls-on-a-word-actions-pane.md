---
title: "Exemplarische Vorgehensweise: Binden von Daten an Steuerelemente in einem Word-Aktionsbereich | Microsoft Docs"
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
  - "Aktionsbereiche [Office-Entwicklung in Visual Studio], Binden von Steuerelementen"
  - "Aktionsbereiche [Office-Entwicklung in Visual Studio], Datenbindung"
  - "Steuerelemente [Office-Entwicklung in Visual Studio], Datenbindung"
  - "Datenbindung [Office-Entwicklung in Visual Studio], Aktionsbereiche"
  - "Datenbindung [Office-Entwicklung in Visual Studio], SmartDocuments"
  - "SmartDocuments [Office-Entwicklung in Visual Studio], Datenbindung"
ms.assetid: 5ef72fc7-412b-4454-9890-4479a13ee7f9
caps.latest.revision: 64
author: "kempb"
ms.author: "kempb"
manager: "ghogen"
caps.handback.revision: 63
---
# Exemplarische Vorgehensweise: Binden von Daten an Steuerelemente in einem Word-Aktionsbereich
  In dieser exemplarischen Vorgehensweise wird die Datenbindung an Steuerelemente in einem Aktionsbereich in Word.  Die Steuerelemente veranschaulichen eine Master\/Detail\-Beziehung zwischen Tabellen in einer SQL Server\-Datenbank.  
  
 [!INCLUDE[appliesto_wdalldoc](../vsto/includes/appliesto-wdalldoc-md.md)]  
  
 In dieser exemplarischen Vorgehensweise werden die folgenden Aufgaben veranschaulicht:  
  
-   Erstellen eines Aktionsbereichs mit Windows Forms\-Steuerelementen, die an Daten gebunden sind.  
  
-   Verwenden einer Master\/Detail\-Beziehung zum Anzeigen von Daten in den Steuerelementen.  
  
-   Anzeigen des Aktionsbereichs beim Öffnen der Anwendung.  
  
> [!NOTE]  
>  Auf Ihrem Computer werden möglicherweise andere Namen oder Speicherorte für die Benutzeroberflächenelemente von Visual Studio angezeigt als die in den folgenden Anweisungen aufgeführten.  Die von Ihnen verwendete Visual Studio\-Edition und die Einstellungen legen diese Elemente fest.  Weitere Informationen finden Sie unter [Customizing Development Settings in Visual Studio](http://msdn.microsoft.com/de-de/22c4debb-4e31-47a8-8f19-16f328d7dcd3).  
  
## Vorbereitungsmaßnahmen  
 Zum Durchführen dieser exemplarischen Vorgehensweise benötigen Sie die folgenden Komponenten:  
  
-   [!INCLUDE[vsto_vsprereq](../vsto/includes/vsto-vsprereq-md.md)]  
  
-   [!INCLUDE[Word_15_short](../vsto/includes/word-15-short-md.md)] oder [!INCLUDE[Word_14_short](../vsto/includes/word-14-short-md.md)].  
  
-   Zugriff auf einen Server mit der SQL Server\-Beispieldatenbank **Northwind**.  
  
-   Lese\- und Schreibberechtigungen für die SQL Server\-Datenbank.  
  
## Erstellen des Projekts  
 Der erste Schritt besteht darin, ein Word\-Dokumentprojekt zu erstellen.  
  
#### So erstellen Sie ein neues Projekt  
  
1.  Erstellen Sie ein Word\-Dokumentprojekt mit dem Namen My Word Actions Pane.  Wählen Sie im Assistenten **Neues Dokument erstellen** aus.  
  
     Weitere Informationen finden Sie unter [Gewusst wie: Erstellen von Office-Projekten in Visual Studio](../vsto/how-to-create-office-projects-in-visual-studio.md).  
  
     Visual Studio öffnet das neue Word\-Dokument im Designer und fügt dem **Projektmappen\-Explorer** das **My Word Actions Pane**\-Projekt hinzu.  
  
## Hinzufügen von Steuerelementen zum Aktionsbereich  
 Für diese exemplarische Vorgehensweise benötigen Sie ein Aktionsbereich\-Steuerelement mit datengebundenen Windows Forms\-Steuerelementen.  Fügen Sie eine Datenquelle zum Projekt hinzu, und ziehen Sie Steuerelemente aus dem **Datenquellenfenster** in das Aktionsbereich\-Steuerelement.  
  
#### So fügen Sie ein Aktionsbereich\-Steuerelement hinzu  
  
1.  Wählen Sie im **Projektmappen\-Explorer** das Projekt **My Word Actions Pane** aus.  
  
2.  Klicken Sie im Menü **Projekt** auf **Neues Element hinzufügen**.  
  
3.  Klicken Sie im Dialogfeld **Neues Element hinzufügen** auf **Aktionsbereich\-Steuerelement**. Nennen Sie das Steuerelement **ActionsControl**, und klicken Sie auf **Hinzufügen**.  
  
#### So fügen Sie dem Projekt eine Datenquelle hinzu  
  
1.  Wenn das **Datenquellen** nicht sichtbar ist, zeigen Sie sie durch, auf der Menüleiste auf und **Ansicht** auswählen, **Weitere Fenster**, **Datenquellen**.  
  
    > [!NOTE]  
    >  Wenn **Datenquellen anzeigen** nicht verfügbar ist, klicken Sie auf das Word\-Dokument, und versuchen Sie es dann erneut.  
  
2.  Klicken Sie auf **Neue Datenquelle hinzufügen**, um den **Assistent zum Konfigurieren von Datenquellen** zu starten.  
  
3.  Wählen Sie **Datenbank** aus, und klicken Sie auf **Weiter**.  
  
4.  Wählen Sie eine Datenverbindung zur Northwind SQL Server\-Beispieldatenbank aus, oder fügen Sie mithilfe der Schaltfläche **Neue Verbindung** eine neue Verbindung hinzu.  
  
5.  Klicken Sie auf **Weiter**.  
  
6.  Deaktivieren Sie ggf. die Option zum Speichern der Verbindung, und klicken Sie dann auf **Weiter**.  
  
7.  Erweitern Sie im Fenster **Datenbankobjekte** den Knoten **Tabellen**.  
  
8.  Aktivieren Sie die Kontrollkästchen neben der Tabelle **Suppliers** und der Tabelle **Products**.  
  
9. Klicken Sie auf **Fertig stellen**.  
  
 Der Assistent fügt dem **Datenquellenfenster** die Tabelle **Suppliers** und die Tabelle **Products** hinzu.  Außerdem wird dem Projekt ein typisiertes Dataset hinzugefügt, das im **Projektmappen\-Explorer** sichtbar ist.  
  
#### So fügen Sie datengebundene Windows Forms\-Steuerelemente zu einem Aktionsbereich\-Steuerelement hinzu  
  
1.  Erweitern Sie im **Datenquellenfenster** die Tabelle **Suppliers**.  
  
2.  Klicken Sie im Knoten **Company Name** auf den Dropdownpfeil, und wählen Sie **ComboBox**.  
  
3.  Ziehen Sie **CompanyName** aus dem **Datenquellenfenster** zum Aktionsbereich\-Steuerelement.  
  
     Im Aktionsbereich\-Steuerelement wird ein <xref:System.Windows.Forms.ComboBox>\-Steuerelement erstellt.  Gleichzeitig werden dem Projekt in der Komponentenleiste eine <xref:System.Windows.Forms.BindingSource> mit dem Namen `SuppliersBindingSource`, ein Tabellenadapter und ein <xref:System.Data.DataSet> hinzugefügt.  
  
4.  Wählen Sie in der **Komponentenleiste** den Eintrag `SuppliersBindingNavigator` aus, und drücken Sie ENTF.  In dieser exemplarischen Vorgehensweise verwenden Sie `SuppliersBindingNavigator` nicht.  
  
    > [!NOTE]  
    >  Beim Löschen des `SuppliersBindingNavigator` wird nicht der gesamte dafür generierte Code gelöscht.  Sie können diesen Code entfernen.  
  
5.  Verschieben Sie das Kombinationsfeld unter die Beschriftung, und ändern Sie die **Size**\-Eigenschaft auf 171, 21.  
  
6.  Erweitern Sie im Fenster **Datenquellen** die Tabelle **Products**, die ein untergeordnetes Element der Tabelle **Suppliers** darstellt.  
  
7.  Klicken Sie im Knoten **ProductName** auf den Dropdownpfeil, und wählen Sie **ListBox**aus.  
  
8.  Ziehen Sie **ProductName** in das Aktionsbereich\-Steuerelement.  
  
     Im Aktionsbereich\-Steuerelement wird ein <xref:System.Windows.Forms.ListBox>\-Steuerelement erstellt.  Gleichzeitig werden dem Projekt in der Komponentenleiste eine <xref:System.Windows.Forms.BindingSource> mit dem Namen `ProductBindingSource` und ein Tabellenadapter hinzugefügt.  
  
9. Verschieben Sie das Listenfeld unter die Beschriftung, und ändern Sie die **Size**\-Eigenschaft auf 171,95.  
  
10. Ziehen Sie aus der **Toolbox** eine <xref:System.Windows.Forms.Button> in das Aktionsbereich\-Steuerelement, und platzieren Sie diese unter dem Listenfeld.  
  
11. Klicken Sie mit der rechten Maustaste auf die <xref:System.Windows.Forms.Button>, klicken Sie im Kontextmenü auf **Eigenschaften**, und ändern Sie die folgenden Eigenschaften:  
  
    |Eigenschaft|Wert|  
    |-----------------|----------|  
    |**Name**|**Insert**|  
    |**Text**|**Insert**|  
  
12. Passen Sie die Größe des Benutzersteuerelements den Steuerelementen entsprechend an.  
  
## Einrichten der Datenquelle  
 Fügen Sie zum Einrichten der Datenquelle dem <xref:System.Windows.Forms.UserControl.Load>\-Ereignis des Aktionsbereich\-Steuerelements Code hinzu, damit das Steuerelement mit Daten aus der <xref:System.Data.DataTable> aufgefüllt wird, und legen Sie die <xref:System.Windows.Forms.Binding.DataSource%2A>\-Eigenschaft und die <xref:System.Windows.Forms.BindingSource.DataMember%2A>\-Eigenschaft für jedes Steuerelement fest.  
  
#### So laden Sie das Steuerelement mit Daten  
  
1.  Fügen Sie im <xref:System.Windows.Forms.UserControl.Load>\-Ereignishandler der `ActionsControl`\-Klasse folgenden Code hinzu:  
  
     [!code-csharp[Trin_VstcoreActionsPaneWord#1](../snippets/csharp/VS_Snippets_OfficeSP/Trin_VstcoreActionsPaneWord/CS/ActionsControl.cs#1)]
     [!code-vb[Trin_VstcoreActionsPaneWord#1](../snippets/visualbasic/VS_Snippets_OfficeSP/Trin_VstcoreActionsPaneWord/VB/ActionsControl.vb#1)]  
  
2.  In C\# müssen Sie den Ereignishandler an das <xref:System.Windows.Forms.UserControl.Load>\-Ereignis anfügen.  Sie können diesen Code im `ActionsControl`\-Konstruktor nach dem Aufruf von `InitializeComponent` platzieren.  Weitere Informationen zum Erstellen von Ereignishandlern finden Sie unter [Gewusst wie: Erstellen von Ereignishandlern in Office-Projekten](../vsto/how-to-create-event-handlers-in-office-projects.md).  
  
     [!code-csharp[Trin_VstcoreActionsPaneWord#33](../snippets/csharp/VS_Snippets_OfficeSP/Trin_VstcoreActionsPaneWord/CS/ActionsControl.cs#33)]  
  
#### So legen Sie die Datenbindungseigenschaften der Steuerelemente fest  
  
1.  Wählen Sie das `CompanyNameComboBox`\-Steuerelement aus.  
  
2.  Klicken Sie im **Eigenschaftenfenster** auf die Schaltfläche rechts von der **DataSource**\-Eigenschaft, und wählen Sie **SuppliersBindingSource** aus.  
  
3.  Klicken Sie auf die Schaltfläche rechts von der **DisplayMember**\-Eigenschaft, und wählen Sie **CompanyName** aus.  
  
4.  Erweitern Sie die **DataBindings**\-Eigenschaft, klicken Sie auf die Schaltfläche rechts von der **Text**\-Eigenschaft, und wählen Sie **Keine** aus.  
  
5.  Wählen Sie das `ProductNameListBox`\-Steuerelement aus.  
  
6.  Klicken Sie im **Eigenschaftenfenster** auf die Schaltfläche rechts von der **DataSource**\-Eigenschaft, und wählen Sie **productsBindingSource** aus.  
  
7.  Klicken Sie auf die Schaltfläche rechts von der **DisplayMember**\-Eigenschaft, und wählen Sie **ProductName** aus.  
  
8.  Erweitern Sie die **DataBindings**\-Eigenschaft, klicken Sie auf die Schaltfläche rechts von der **SelectedValue**\-Eigenschaft, und wählen Sie **Keine** aus.  
  
## Hinzufügen einer Methode zum Einfügen von Daten in eine Tabelle  
 Die nächste Aufgabe besteht darin, die Daten von den gebundenen Steuerelementen zu lesen und eine Tabelle im Word\-Dokument zu füllen.  Zunächst erstellen Sie eine Prozedur zum Formatieren der Tabellenüberschriften und fügen dann die `AddData`\-Methode zum Erstellen und Formatieren einer Word\-Tabelle hinzu.  
  
#### So formatieren Sie die Tabellenüberschriften  
  
1.  Erstellen Sie in der `ActionsControl`\-Klasse eine Methode zum Formatieren der Tabellenüberschriften.  
  
     [!code-csharp[Trin_VstcoreActionsPaneWord#2](../snippets/csharp/VS_Snippets_OfficeSP/Trin_VstcoreActionsPaneWord/CS/ActionsControl.cs#2)]
     [!code-vb[Trin_VstcoreActionsPaneWord#2](../snippets/visualbasic/VS_Snippets_OfficeSP/Trin_VstcoreActionsPaneWord/VB/ActionsControl.vb#2)]  
  
#### So erstellen Sie die Tabelle  
  
1.  Schreiben Sie in der `ActionsControl`\-Klasse eine Methode, die ggf. eine Tabelle erstellt und der Tabelle dann Daten aus dem Aktionsbereich hinzufügt.  
  
     [!code-csharp[Trin_VstcoreActionsPaneWord#3](../snippets/csharp/VS_Snippets_OfficeSP/Trin_VstcoreActionsPaneWord/CS/ActionsControl.cs#3)]
     [!code-vb[Trin_VstcoreActionsPaneWord#3](../snippets/visualbasic/VS_Snippets_OfficeSP/Trin_VstcoreActionsPaneWord/VB/ActionsControl.vb#3)]  
  
#### So fügen Sie Text in eine Word\-Tabelle ein  
  
1.  Fügen Sie folgenden Code zum <xref:System.Windows.Forms.Control.Click>\-Ereignishandler der Schaltfläche **Einfügen** hinzu.  
  
     [!code-csharp[Trin_VstcoreActionsPaneWord#4](../snippets/csharp/VS_Snippets_OfficeSP/Trin_VstcoreActionsPaneWord/CS/ActionsControl.cs#4)]
     [!code-vb[Trin_VstcoreActionsPaneWord#4](../snippets/visualbasic/VS_Snippets_OfficeSP/Trin_VstcoreActionsPaneWord/VB/ActionsControl.vb#4)]  
  
2.  In C\# müssen Sie einen Ereignishandler für das <xref:System.Windows.Forms.Control.Click>\-Ereignis der Schaltfläche erstellen.  Sie können diesen Code in den <xref:System.Windows.Forms.UserControl.Load>\-Ereignishandler der `ActionsControl`\-Klasse einfügen.  
  
     [!code-csharp[Trin_VstcoreActionsPaneWord#5](../snippets/csharp/VS_Snippets_OfficeSP/Trin_VstcoreActionsPaneWord/CS/ActionsControl.cs#5)]  
  
## Anzeigen des Aktionsbereichs  
 Der Aktionsbereich wird sichtbar, wenn Steuerelemente hinzugefügt werden.  
  
#### So zeigen Sie den Aktionsbereich an  
  
1.  Klicken Sie im **Projektmappen\-Explorer** mit der rechten Maustaste auf **ThisDocument.vb** oder **ThisDocument.cs**, und klicken Sie dann im Kontextmenü auf **Code anzeigen**.  
  
2.  Erstellen Sie wie im folgenden Beispiel eine neue Instanz des Steuerelements im oberen Teil der `ThisDocument`\-Klasse.  
  
     [!code-csharp[Trin_VstcoreActionsPaneWord#6](../snippets/csharp/VS_Snippets_OfficeSP/Trin_VstcoreActionsPaneWord/CS/ThisDocument.cs#6)]
     [!code-vb[Trin_VstcoreActionsPaneWord#6](../snippets/visualbasic/VS_Snippets_OfficeSP/Trin_VstcoreActionsPaneWord/VB/ThisDocument.vb#6)]  
  
3.  Fügen Sie dem <xref:Microsoft.Office.Tools.Word.Document.Startup>\-Ereignishandler von `ThisDocument` wie im folgenden Beispiel gezeigt Code hinzu.  
  
     [!code-csharp[Trin_VstcoreActionsPaneWord#7](../snippets/csharp/VS_Snippets_OfficeSP/Trin_VstcoreActionsPaneWord/CS/ThisDocument.cs#7)]
     [!code-vb[Trin_VstcoreActionsPaneWord#7](../snippets/visualbasic/VS_Snippets_OfficeSP/Trin_VstcoreActionsPaneWord/VB/ThisDocument.vb#7)]  
  
## Testen der Anwendung  
 Nun können Sie Ihr Dokument testen, um zu überprüfen, ob der Aktionsbereich beim Öffnen des Dokuments angezeigt wird.  Überprüfen Sie die Master\/Detail\-Beziehung der Steuerelemente im Aktionsbereich, und stellen Sie sicher, dass eine Word\-Tabelle mit Daten gefüllt wird, wenn auf die Schaltfläche **Einfügen** geklickt wird.  
  
#### So testen Sie das Dokument  
  
1.  Drücken Sie F5, um das Projekt auszuführen.  
  
2.  Bestätigen Sie, dass der Aktionsbereich angezeigt wird.  
  
3.  Wählen Sie eine Firma im Kombinationsfeld, und stellen Sie sicher, das sich die Elemente des Listenfelds **Products** ändern.  
  
4.  Wählen Sie ein Produkt, klicken Sie im Aktionsbereich auf **Einfügen**, und überprüfen Sie, ob die Produktdetails der Word\-Tabelle hinzugefügt werden.  
  
5.  Fügen Sie zusätzliche Produkte von verschiedenen Firmen ein.  
  
## Nächste Schritte  
 Diese exemplarische Vorgehensweise erklärt die Grundlagen der Bindung von Daten an Steuerelemente in einem Aktionsbereich in Word.  Die folgenden Aufgaben könnten sich daran anschließen:  
  
-   Binden von Daten an Steuerelemente in Excel.  Weitere Informationen finden Sie unter [Exemplarische Vorgehensweise: Bindung von Daten an Steuerelemente in einem Excel-Aktionsbereich](../vsto/walkthrough-binding-data-to-controls-on-an-excel-actions-pane.md).  
  
-   Bereitstellen des Projekts.  Weitere Informationen finden Sie unter [Bereitstellen einer Office-Lösung mithilfe von ClickOnce](../vsto/deploying-an-office-solution-by-using-clickonce.md).  
  
## Siehe auch  
 [Aktionsbereichsübersicht](../vsto/actions-pane-overview.md)   
 [Gewusst wie: Hinzufügen eines Aktionsbereichs zu Word-Dokumenten oder Excel-Arbeitsmappen](../vsto/how-to-add-an-actions-pane-to-word-documents-or-excel-workbooks.md)   
 [Binden von Daten an Steuerelemente in Office-Projektmappen](../vsto/binding-data-to-controls-in-office-solutions.md)  
  
  