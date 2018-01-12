---
title: 'Exemplarische Vorgehensweise: Binden von Daten an Steuerelemente in einem Word-Aktionsbereich | Microsoft Docs'
ms.custom: 
ms.date: 02/02/2017
ms.reviewer: 
ms.suite: 
ms.technology: office-development
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- controls [Office development in Visual Studio], data binding
- actions panes [Office development in Visual Studio], data binding
- data binding [Office development in Visual Studio], smart documents
- data binding [Office development in Visual Studio], actions panes
- actions panes [Office development in Visual Studio], binding controls
- smart documents [Office development in Visual Studio], data binding
author: TerryGLee
ms.author: tglee
manager: ghogen
ms.workload: office
ms.openlocfilehash: c53c8ba65c07f2c488f33835cb045524069e3285
ms.sourcegitcommit: f9fbf1f55f9ac14e4e5c6ae58c30dc1800ca6cda
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 01/10/2018
---
# <a name="walkthrough-binding-data-to-controls-on-a-word-actions-pane"></a>Exemplarische Vorgehensweise: Binden von Daten an Steuerelemente in einem Word-Aktionsbereich
  In dieser exemplarischen Vorgehensweise veranschaulicht das Binden von Daten an Steuerelemente in einem Aktionsbereich in Word. Die Steuerelemente zeigen eine Master/Detail-Beziehung zwischen Tabellen in einer SQL Server-Datenbank.  
  
 [!INCLUDE[appliesto_wdalldoc](../vsto/includes/appliesto-wdalldoc-md.md)]  
  
 In dieser exemplarischen Vorgehensweise werden die folgenden Aufgaben veranschaulicht:  
  
-   Erstellen eines Aktionsbereichs mit Windows Forms-Steuerelemente, die an Daten gebunden sind.  
  
-   Verwenden eine Master/Detail-Beziehung zum Anzeigen von Daten in den Steuerelementen.  
  
-   Anzeigen des Aktionsbereichs, wenn die Anwendung geöffnet wird.  
  
> [!NOTE]  
>  Auf Ihrem Computer werden möglicherweise andere Namen oder Speicherorte für die Benutzeroberflächenelemente von Visual Studio angezeigt als die in den folgenden Anweisungen aufgeführten. Diese Elemente sind von der jeweiligen Visual Studio-Version und den verwendeten Einstellungen abhängig. Weitere Informationen finden Sie unter [Personalisieren von Visual Studio-IDE](../ide/personalizing-the-visual-studio-ide.md).  
  
## <a name="prerequisites"></a>Erforderliche Komponenten  
 Zum Durchführen dieser exemplarischen Vorgehensweise benötigen Sie die folgenden Komponenten:  
  
-   [!INCLUDE[vsto_vsprereq](../vsto/includes/vsto-vsprereq-md.md)]  
  
-   [!INCLUDE[Word_15_short](../vsto/includes/word-15-short-md.md)] oder [!INCLUDE[Word_14_short](../vsto/includes/word-14-short-md.md)].  
  
-   Zugriff auf einen Server mit der Beispieldatenbank Northwind-SQL Server.  
  
-   Berechtigungen zum Lesen und Schreiben in SQL Server-Datenbank.  
  
## <a name="creating-the-project"></a>Erstellen des Projekts  
 Im ersten Schritt wird ein Word-Dokumentprojekt erstellt.  
  
#### <a name="to-create-a-new-project"></a>So erstellen Sie ein neues Projekt  
  
1.  Erstellen Sie ein Word-Dokumentprojekt mit dem Namen **My Word-Aktionsbereich**. Wählen Sie im Assistenten **erstellen Sie ein neues Dokument**.  
  
     Weitere Informationen finden Sie unter [How to: Create Office Projects in Visual Studio](../vsto/how-to-create-office-projects-in-visual-studio.md).  
  
     Visual Studio öffnet das neue Word-Dokument im Designer und fügt die **My Word-Aktionsbereich** Projekt **Projektmappen-Explorer**.  
  
## <a name="adding-controls-to-the-actions-pane"></a>Hinzufügen von Steuerelementen zum Aktionsbereich  
 In dieser exemplarischen Vorgehensweise benötigen Sie ein Aktionsbereich-Steuerelement, das von datengebundenen Windows Forms-Steuerelemente enthält. Das Projekt eine Datenquelle hinzu, und ziehen Sie Steuerelemente aus der **Datenquellen** Fenster aus, um den Aktionsbereich-Steuerelement.  
  
#### <a name="to-add-an-actions-pane-control"></a>So fügen Sie einem Aktionsbereich-Steuerelement hinzu  
  
1.  Wählen Sie die **My Word-Aktionsbereich** Projekt **Projektmappen-Explorer**.  
  
2.  Klicken Sie im Menü **Projekt** auf **Neues Element hinzufügen**.  
  
3.  In der **neues Element hinzufügen** wählen Sie im Dialogfeld **Aktionsbereich-Steuerelement**, nennen Sie sie **ActionsControl**, und klicken Sie dann auf **hinzufügen**.  
  
#### <a name="to-add-a-data-source-to-the-project"></a>Das Projekt eine Datenquelle hinzu  
  
1.  Wenn das Fenster **Datenquellen** nicht sichtbar ist, zeigen Sie es an, indem Sie in der Menüleiste **Ansicht**, **Weitere Fenster**und **Datenquellen**wählen.  
  
    > [!NOTE]  
    >  Wenn **Datenquellen anzeigen** ist nicht verfügbar ist, klicken Sie auf das Word-Dokument, und klicken Sie dann erneut.  
  
2.  Klicken Sie auf **neue Datenquelle hinzufügen** zum Starten der **Datenquellen Konfigurations-Assistenten**.  
  
3.  Wählen Sie **Datenbank** , und klicken Sie dann auf **Weiter**.  
  
4.  Wählen Sie eine Datenverbindung zur Northwind-Beispieldatenbank SQL Server, oder fügen Sie eine neue Verbindung mit der **neue Verbindung** Schaltfläche.  
  
5.  Klicken Sie auf **Weiter**.  
  
6.  Deaktivieren Sie die Option aus, um die Verbindung zu speichern, wenn diese Option ausgewählt ist, und klicken Sie dann auf **Weiter**.  
  
7.  Erweitern Sie die **Tabellen** Knoten in der **-Datenbankobjekte** Fenster.  
  
8.  Aktivieren Sie das Kontrollkästchen neben den **Lieferanten** und **Produkte** Tabellen.  
  
9. Klicken Sie auf **Fertig stellen**.  
  
 Fügt der Assistent die **Lieferanten** Tabelle und **Produkte** Tabelle, auf die **Datenquellen** Fenster. Es auch ein typisiertes Dataset dem Projekt hinzugefügt, die in angezeigt wird **Projektmappen-Explorer**.  
  
#### <a name="to-add-data-bound-windows-forms-controls-to-an-actions-pane-control"></a>Hinzufügen von datengebundenen Windows Forms-Steuerelementen zu einem Aktionsbereich-Steuerelement  
  
1.  In der **Datenquellen** Fenster, erweitern Sie die **Lieferanten** Tabelle.  
  
2.  Klicken Sie auf den Dropdown Pfeil auf der **Firmenname** Knoten, und wählen **ComboBox**.  
  
3.  Ziehen Sie **CompanyName** aus der **Datenquellen** Fenster aus, um den Aktionsbereich-Steuerelement.  
  
     Ein <xref:System.Windows.Forms.ComboBox> -Steuerelement wird auf dem Aktionsbereich-Steuerelement erstellt. Zur gleichen Zeit eine <xref:System.Windows.Forms.BindingSource> mit dem Namen `SuppliersBindingSource`, Tabellenadapters, und ein <xref:System.Data.DataSet> werden dem Projekt in der Komponentenleiste hinzugefügt.  
  
4.  Wählen Sie `SuppliersBindingNavigator` in der **Komponente** infobereichsanwendung, und drücken Sie ENTF. Verwenden Sie nicht die `SuppliersBindingNavigator` in dieser exemplarischen Vorgehensweise.  
  
    > [!NOTE]  
    >  Durch das Löschen der `SuppliersBindingNavigator` wird nicht der gesamte Code, der für sie generiert wurde entfernt. Sie können diesen Code entfernen.  
  
5.  Verschieben Sie das Kombinationsfeld unter die Bezeichnung und Ändern der **Größe** Eigenschaft **171, 21**.  
  
6.  In der **Datenquellen** Fenster, erweitern Sie die **Produkte** Tabelle, d. h. ein untergeordnetes Element eines der **Lieferanten** Tabelle.  
  
7.  Klicken Sie auf den Dropdown Pfeil auf der **ProductName** Knoten, und wählen **ListBox**.  
  
8.  Ziehen Sie **ProductName** in den Aktionsbereich-Steuerelement.  
  
     Ein <xref:System.Windows.Forms.ListBox> -Steuerelement wird auf dem Aktionsbereich-Steuerelement erstellt. Zur gleichen Zeit eine <xref:System.Windows.Forms.BindingSource> mit dem Namen `ProductBindingSource` und Tabellenadapters werden dem Projekt in der Komponentenleiste hinzugefügt.  
  
9. Verschieben Sie im Listenfeld unter die Bezeichnung und Ändern der **Größe** Eigenschaft **171,95**.  
  
10. Ziehen Sie eine <xref:System.Windows.Forms.Button> aus der **Toolbox** auf Aktionsbereich steuern und platzieren Sie es unter dem Listenfeld.  
  
11. Mit der rechten Maustaste die <xref:System.Windows.Forms.Button>, klicken Sie auf **Eigenschaften** im Kontextmenü, und ändern Sie die folgenden Eigenschaften.  
  
    |Eigenschaft|Wert|  
    |--------------|-----------|  
    |**Name**|**Einfügen**|  
    |**Text**|**Einfügen**|  
  
12. Ändern Sie das Benutzersteuerelement, um die Steuerelemente an.  
  
## <a name="setting-up-the-data-source"></a>Einrichten der Datenquelle  
 Informationen zum Einrichten der Datenquelle, fügen Sie Code zu der <xref:System.Windows.Forms.UserControl.Load> -Ereignis für den Aktionsbereich-Steuerelement, füllen Sie das Steuerelement mit Daten aus der <xref:System.Data.DataTable>, und legen Sie die <xref:System.Windows.Forms.Binding.DataSource%2A> und <xref:System.Windows.Forms.BindingSource.DataMember%2A> Eigenschaften für jedes Steuerelement.  
  
#### <a name="to-load-the-control-with-data"></a>Um das Steuerelement mit Daten zu laden.  
  
1.  In der <xref:System.Windows.Forms.UserControl.Load> -Ereignishandler des der `ActionsControl` Klasse, fügen Sie den folgenden Code hinzu.  
  
     [!code-vb[Trin_VstcoreActionsPaneWord#1](../vsto/codesnippet/VisualBasic/Trin_VstcoreActionsPaneWordVB/ActionsControl.vb#1)]
     [!code-csharp[Trin_VstcoreActionsPaneWord#1](../vsto/codesnippet/CSharp/Trin_VstcoreActionsPaneWordCS/ActionsControl.cs#1)]  
  
2.  In c# müssen Sie den Ereignishandler zum Anfügen der <xref:System.Windows.Forms.UserControl.Load> Ereignis. Sie können diesen Code im Platzieren der `ActionsControl` -Konstruktor nach dem Aufruf von `InitializeComponent`. Weitere Informationen zum Erstellen von Ereignishandlern finden Sie unter [Vorgehensweise: Erstellen von Ereignishandlern in Office-Projekten](../vsto/how-to-create-event-handlers-in-office-projects.md).  
  
     [!code-csharp[Trin_VstcoreActionsPaneWord#33](../vsto/codesnippet/CSharp/Trin_VstcoreActionsPaneWordCS/ActionsControl.cs#33)]  
  
#### <a name="to-set-data-binding-properties-of-the-controls"></a>Um die Datenbindungseigenschaften der Steuerelemente festlegen  
  
1.  Wählen Sie das `CompanyNameComboBox`-Steuerelement.  
  
2.  In der **Eigenschaften** Fenster, klicken Sie auf die Schaltfläche rechts neben der **DataSource** Eigenschaft, und wählen **SuppliersBindingSource**.  
  
3.  Klicken Sie auf die Schaltfläche rechts neben der **DisplayMember** Eigenschaft, und wählen **CompanyName**.  
  
4.  Erweitern Sie die **DataBindings** -Eigenschaft, klicken Sie auf die Schaltfläche rechts neben der **Text** Eigenschaft, und wählen **keine**.  
  
5.  Wählen Sie das `ProductNameListBox`-Steuerelement.  
  
6.  In der **Eigenschaften** Fenster, klicken Sie auf die Schaltfläche rechts neben der **DataSource** Eigenschaft, und wählen **ProductsBindingSource**.  
  
7.  Klicken Sie auf die Schaltfläche rechts neben der **DisplayMember** Eigenschaft, und wählen **ProductName**.  
  
8.  Erweitern Sie die **DataBindings** -Eigenschaft, klicken Sie auf die Schaltfläche rechts neben der **"SelectedValue"** Eigenschaft, und wählen **keine**.  
  
## <a name="adding-a-method-to-insert-data-into-a-table"></a>Hinzufügen einer Methode zum Einfügen von Daten in eine Tabelle  
 Die nächste Aufgabe besteht darin lesen Sie die Daten von den gebundenen Steuerelementen und eine Tabelle im Word-Dokument füllen. Erstellen Sie zunächst eine Prozedur zum Formatieren der Tabellenüberschriften, und fügen Sie dann die `AddData` Methode zum Erstellen und formatieren eine Word-Tabelle.  
  
#### <a name="to-format-the-table-headings"></a>Die Tabellenüberschriften formatieren.  
  
1.  In der `ActionsControl` Klasse, erstellen Sie eine Methode, um die Spaltenüberschriften der Tabelle zu formatieren.  
  
     [!code-vb[Trin_VstcoreActionsPaneWord#2](../vsto/codesnippet/VisualBasic/Trin_VstcoreActionsPaneWordVB/ActionsControl.vb#2)]
     [!code-csharp[Trin_VstcoreActionsPaneWord#2](../vsto/codesnippet/CSharp/Trin_VstcoreActionsPaneWordCS/ActionsControl.cs#2)]  
  
#### <a name="to-create-the-table"></a>Zum Erstellen der Tabelle  
  
1.  In der `ActionsControl` Klasse, erstellen Sie eine Methode, die eine Tabelle erstellt, wenn eine nicht bereits vorhanden, und klicken Sie im Bereich "Aktionen" der Tabelle Daten hinzufügen.  
  
     [!code-vb[Trin_VstcoreActionsPaneWord#3](../vsto/codesnippet/VisualBasic/Trin_VstcoreActionsPaneWordVB/ActionsControl.vb#3)]
     [!code-csharp[Trin_VstcoreActionsPaneWord#3](../vsto/codesnippet/CSharp/Trin_VstcoreActionsPaneWordCS/ActionsControl.cs#3)]  
  
#### <a name="to-insert-text-into-a-word-table"></a>Zum Einfügen von Text in einem Word-Tabelle  
  
1.  Fügen Sie den folgenden Code hinzu. die <xref:System.Windows.Forms.Control.Click> -Ereignishandler des der **einfügen** Schaltfläche.  
  
     [!code-vb[Trin_VstcoreActionsPaneWord#4](../vsto/codesnippet/VisualBasic/Trin_VstcoreActionsPaneWordVB/ActionsControl.vb#4)]
     [!code-csharp[Trin_VstcoreActionsPaneWord#4](../vsto/codesnippet/CSharp/Trin_VstcoreActionsPaneWordCS/ActionsControl.cs#4)]  
  
2.  In c#, erstellen Sie einen Ereignishandler für das <xref:System.Windows.Forms.Control.Click> -Ereignis der Schaltfläche.  Sie können diesen Code im Platzieren der <xref:System.Windows.Forms.UserControl.Load> Ereignishandler, der die `ActionsControl` Klasse.  
  
     [!code-csharp[Trin_VstcoreActionsPaneWord#5](../vsto/codesnippet/CSharp/Trin_VstcoreActionsPaneWordCS/ActionsControl.cs#5)]  
  
## <a name="showing-the-actions-pane"></a>Anzeigen des Aktionsbereichs  
 Der Aktionsbereich wird angezeigt, nachdem Steuerelemente hinzugefügt werden.  
  
#### <a name="to-show-the-actions-pane"></a>Um den Aktionsbereich anzuzeigen  
  
1.  In **Projektmappen-Explorer**, mit der rechten Maustaste **ThisDocument.vb** oder **ThisDocument.cs**, und klicken Sie dann auf **Code anzeigen** im Kontextmenü.  
  
2.  Erstellen Sie eine neue Instanz des Steuerelements am Anfang der `ThisDocument` Klasse, damit sie das folgende Beispiel aussieht.  
  
     [!code-csharp[Trin_VstcoreActionsPaneWord#6](../vsto/codesnippet/CSharp/Trin_VstcoreActionsPaneWordCS/ThisDocument.cs#6)]
     [!code-vb[Trin_VstcoreActionsPaneWord#6](../vsto/codesnippet/VisualBasic/Trin_VstcoreActionsPaneWordVB/ThisDocument.vb#6)]  
  
3.  Hinzufügen von Code für die <xref:Microsoft.Office.Tools.Word.Document.Startup> -Ereignishandler des `ThisDocument` , damit sie das folgende Beispiel aussieht.  
  
     [!code-csharp[Trin_VstcoreActionsPaneWord#7](../vsto/codesnippet/CSharp/Trin_VstcoreActionsPaneWordCS/ThisDocument.cs#7)]
     [!code-vb[Trin_VstcoreActionsPaneWord#7](../vsto/codesnippet/VisualBasic/Trin_VstcoreActionsPaneWordVB/ThisDocument.vb#7)]  
  
## <a name="testing-the-application"></a>Testen der Anwendung  
 Sie können jetzt testen, dass das Dokument, um sicherzustellen, dass der Aktionsbereich angezeigt wird, wenn das Dokument geöffnet wird. Für die Master-/Detail-Beziehung in die Steuerelemente im Aktionsbereich testen, und stellen Sie sicher, dass Daten in einem Wort aufgefüllt werden bei Verwendung der **einfügen** geklickt wird.  
  
#### <a name="to-test-your-document"></a>So testen Sie das Dokument  
  
1.  Drücken Sie F5, um das Projekt auszuführen.  
  
2.  Vergewissern Sie sich, dass der Aktionsbereich sichtbar ist.  
  
3.  Wählen Sie im Kombinationsfeld ein Unternehmen, und überprüfen Sie, ob die Elemente in der **Produkte** Liste ändern.  
  
4.  Wählen Sie ein Produkt aus, klicken Sie auf **einfügen** im Aktionsbereich und stellen Sie sicher, dass die Produktdetails der Word-Tabelle hinzugefügt werden.  
  
5.  Fügen Sie weitere Produkte aus verschiedenen Unternehmen.  
  
## <a name="next-steps"></a>Nächste Schritte  
 Diese exemplarische Vorgehensweise veranschaulicht die Grundlagen der Bindung von Daten an Steuerelemente in einem Aktionsbereich in Word. Die folgenden Aufgaben könnten sich daran anschließen:  
  
-   Binden von Daten an Steuerelemente in Excel. Weitere Informationen finden Sie unter [Exemplarische Vorgehensweise: Binden von Daten an Steuerelemente in einem Excel-Aktionsbereich](../vsto/walkthrough-binding-data-to-controls-on-an-excel-actions-pane.md).  
  
-   Beim Bereitstellen des Projekts. Weitere Informationen finden Sie unter [Bereitstellen einer Office-Lösung mithilfe von ClickOnce](../vsto/deploying-an-office-solution-by-using-clickonce.md).  
  
## <a name="see-also"></a>Siehe auch  
 [Aktionsbereichsübersicht](../vsto/actions-pane-overview.md)   
 [Vorgehensweise: Hinzufügen eines Aktionsbereichs zu Word-Dokumenten oder Excel-Arbeitsmappen](../vsto/how-to-add-an-actions-pane-to-word-documents-or-excel-workbooks.md)   
 [Binden von Daten an Steuerelemente in Office-Projektmappen](../vsto/binding-data-to-controls-in-office-solutions.md)  
  
  