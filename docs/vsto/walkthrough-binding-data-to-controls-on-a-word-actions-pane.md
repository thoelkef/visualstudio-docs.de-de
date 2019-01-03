---
title: 'Exemplarische Vorgehensweise: Binden von Daten an Steuerelemente in einem Word-Aktionsbereich'
ms.date: 02/02/2017
ms.topic: conceptual
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
manager: douge
ms.workload:
- office
ms.openlocfilehash: a113cbdffffb202a832ce145c4507bf5845ff52d
ms.sourcegitcommit: 37fb7075b0a65d2add3b137a5230767aa3266c74
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 01/02/2019
ms.locfileid: "53926449"
---
# <a name="walkthrough-bind-data-to-controls-on-a-word-actions-pane"></a>Exemplarische Vorgehensweise: Binden von Daten an Steuerelemente in einem Word-Aktionsbereich
  Diese exemplarische Vorgehensweise veranschaulicht die Datenbindung an Steuerelemente in einem Aktionsbereich in Word. Die Steuerelemente zeigen eine Master/Detail-Beziehung zwischen Tabellen in einer SQL Server-Datenbank.  
  
 [!INCLUDE[appliesto_wdalldoc](../vsto/includes/appliesto-wdalldoc-md.md)]  
  
 In dieser exemplarischen Vorgehensweise werden die folgenden Aufgaben veranschaulicht:  
  
-   Erstellen einen Bereich "Aktionen" mit Windows Forms-Steuerelementen, die an Daten gebunden sind.  
  
-   Verwenden zum Anzeigen von Daten in den Steuerelementen eine Master/Detail-Beziehung.  
  
-   Zeigen Sie im Aktionsbereich beim Öffnen der Anwendung.  
  
> [!NOTE]  
>  Auf Ihrem Computer werden möglicherweise andere Namen oder Speicherorte für die Benutzeroberflächenelemente von Visual Studio angezeigt als die in den folgenden Anweisungen aufgeführten. Diese Elemente sind von der jeweiligen Visual Studio-Version und den verwendeten Einstellungen abhängig. Weitere Informationen finden Sie unter [Personalisieren von Visual Studio-IDE](../ide/personalizing-the-visual-studio-ide.md).  
  
## <a name="prerequisites"></a>Vorraussetzungen  
 Zum Durchführen dieser exemplarischen Vorgehensweise benötigen Sie die folgenden Komponenten:  
  
-   [!INCLUDE[vsto_vsprereq](../vsto/includes/vsto-vsprereq-md.md)]  
  
-   [!INCLUDE[Word_15_short](../vsto/includes/word-15-short-md.md)] oder [!INCLUDE[Word_14_short](../vsto/includes/word-14-short-md.md)].  
  
-   Zugriff auf einen Server mit der Beispieldatenbank Northwind-SQL Server.  
  
-   Berechtigungen zum Lesen und Schreiben in SQL Server-Datenbank.  
  
## <a name="create-the-project"></a>Erstellen eines Projekts  
 Im ersten Schritt wird ein Word-Dokumentprojekt erstellt.  
  
### <a name="to-create-a-new-project"></a>So erstellen Sie ein neues Projekt  
  
1.  Erstellen Sie ein Word-Dokumentprojekt mit dem Namen **My Word-Aktionsbereich**. Wählen Sie im Assistenten **ein neues Dokument erstellen**.  
  
     Weitere Informationen finden Sie unter [Vorgehensweise: Erstellen von Office-Projekten in Visual Studio](../vsto/how-to-create-office-projects-in-visual-studio.md).  
  
     Visual Studio öffnet das neue Word-Dokument im Designer und fügt die **My Word-Aktionsbereich** Projekt **Projektmappen-Explorer**.  
  
## <a name="add-controls-to-the-actions-pane"></a>Hinzufügen von Steuerelementen im Aktionsbereich  
 In dieser exemplarischen Vorgehensweise benötigen Sie ein Aktionsbereich-Steuerelement, das von datengebundenen Windows Forms-Steuerelementen enthält. Fügen Sie dem Projekt eine Datenquelle aus, und ziehen Sie dann die Steuerelemente aus der **Datenquellen** Fenster aus, um das Aktionsbereich-Steuerelement.  
  
### <a name="to-add-an-actions-pane-control"></a>Hinzufügen ein Aktionsbereich-Steuerelements  
  
1.  Wählen Sie die **My Word-Aktionsbereich** Projekt **Projektmappen-Explorer**.  
  
2.  Klicken Sie im Menü **Projekt** auf **Neues Element hinzufügen**.  
  
3.  In der **neues Element hinzufügen** wählen Sie im Dialogfeld **Aktionsbereich-Steuerelements**, nennen Sie sie **ActionsControl**, und klicken Sie dann auf **hinzufügen**.  
  
### <a name="to-add-a-data-source-to-the-project"></a>Um eine Datenquelle zum Projekt hinzufügen  
  
1. Wenn die **Datenquellen** Fenster ist nicht sichtbar ist, zeigen Sie es an, indem in der Menüleiste die Optionen **Ansicht** > **Other Windows**  >   **Datenquellen**.  
  
   > [!NOTE]  
   >  Wenn **Datenquellen anzeigen** ist nicht verfügbar ist, klicken Sie auf das Word-Dokument, und klicken Sie dann erneut.  
  
2. Klicken Sie auf **neue Datenquelle hinzufügen** zum Starten der **Assistenten zur Datenquellenkonfiguration**.  
  
3. Wählen Sie **Datenbank** , und klicken Sie dann auf **Weiter**.  
  
4. Wählen Sie eine Datenverbindung zur Northwind-Beispieldatenbank SQL Server, oder fügen Sie eine neue Verbindung mit der **neue Verbindung** Schaltfläche.  
  
5. Klicken Sie auf **Weiter**.  
  
6. Deaktivieren Sie die Option zum Speichern der Verbindung, wenn diese Option ausgewählt ist, und klicken Sie dann auf **Weiter**.  
  
7. Erweitern Sie die **Tabellen** Knoten in der **Datenbankobjekte** Fenster.  
  
8. Aktivieren Sie das Kontrollkästchen neben den **Lieferanten** und **Produkte** Tabellen.  
  
9. Klicken Sie auf **Fertig stellen**.  
  
   Der Assistent fügt die **Lieferanten** Tabelle und **Produkte** Tabelle, auf die **Datenquellen** Fenster. Es auch ein typisiertes Dataset dem Projekt hinzugefügt, die in angezeigt wird **Projektmappen-Explorer**.  
  
### <a name="to-add-data-bound-windows-forms-controls-to-an-actions-pane-control"></a>Datengebundene Windows Forms-Steuerelemente einem Aktionsbereich-Steuerelement hinzu  
  
1.  In der **Datenquellen** Fenster, erweitern Sie die **Lieferanten** Tabelle.  
  
2.  Klicken Sie auf die Dropdown-Pfeil der **Firmenname** Knoten, und wählen **"ComboBox"**.  
  
3.  Ziehen Sie **CompanyName** aus der **Datenquellen** Fenster aus, um das Aktionsbereich-Steuerelement.  
  
     Ein <xref:System.Windows.Forms.ComboBox> -Steuerelement auf das Aktionsbereich-Steuerelement erstellt wird. Zur gleichen Zeit eine <xref:System.Windows.Forms.BindingSource> mit dem Namen `SuppliersBindingSource`, ein Tabellenadapter und eine <xref:System.Data.DataSet> werden dem Projekt in der Komponentenleiste hinzugefügt.  
  
4.  Wählen Sie `SuppliersBindingNavigator` in die **Komponente** Taskleiste, und drücken Sie **löschen**. Verwenden Sie nicht die `SuppliersBindingNavigator` in dieser exemplarischen Vorgehensweise.  
  
    > [!NOTE]  
    >  Löschen der `SuppliersBindingNavigator` entfernt nicht der gesamte Code, der für sie generiert wurde. Sie können diesen Code entfernen.  
  
5.  Verschieben Sie im Kombinationsfeld, damit es unter der Bezeichnung und die Änderung ist die **Größe** Eigenschaft **171, 21**.  
  
6.  In der **Datenquellen** Fenster, erweitern Sie die **Produkte** Tabelle, d. h. ein untergeordnetes Element des der **Lieferanten** Tabelle.  
  
7.  Klicken Sie auf die Dropdown-Pfeil der **ProductName** Knoten, und wählen **ListBox**.  
  
8.  Ziehen Sie **ProductName** auf das Aktionsbereich-Steuerelement.  
  
     Ein <xref:System.Windows.Forms.ListBox> -Steuerelement auf das Aktionsbereich-Steuerelement erstellt wird. Zur gleichen Zeit eine <xref:System.Windows.Forms.BindingSource> mit dem Namen `ProductBindingSource` und Tabellenadapters werden dem Projekt in der Komponentenleiste hinzugefügt.  
  
9. Verschieben Sie im Listenfeld aus, damit es unter der Bezeichnung und die Änderung ist die **Größe** Eigenschaft **171,95**.  
  
10. Ziehen Sie eine <xref:System.Windows.Forms.Button> aus der **Toolbox** auf den Bereich "Aktionen" steuern, und platzieren Sie es unter dem Listenfeld.  
  
11. Mit der rechten Maustaste die <xref:System.Windows.Forms.Button>, klicken Sie auf **Eigenschaften** im Kontextmenü, und ändern Sie die folgenden Eigenschaften.  
  
    |Eigenschaft|Wert|  
    |--------------|-----------|  
    |**Name**|**Einfügen**|  
    |**Text**|**Einfügen**|  
  
12. Ändern Sie das Benutzersteuerelement, um die Steuerelemente passen die Größe.  
  
## <a name="set-up-the-data-source"></a>Richten Sie die Datenquelle  
 Fügen Sie Code zum Einrichten der Datenquelle die <xref:System.Windows.Forms.UserControl.Load> Ereignis des Aktionsbereich-Steuerelements zum Ausfüllen des Steuerelements mit Daten aus der <xref:System.Data.DataTable>, und legen Sie die <xref:System.Windows.Forms.Binding.DataSource%2A> und <xref:System.Windows.Forms.BindingSource.DataMember%2A> Eigenschaften für jedes Steuerelement.  
  
### <a name="to-load-the-control-with-data"></a>Um das Steuerelement mit Daten zu laden.  
  
1.  In der <xref:System.Windows.Forms.UserControl.Load> -Ereignishandler von dem `ActionsControl` -Klasse verwenden, fügen Sie den folgenden Code.  
  
     [!code-vb[Trin_VstcoreActionsPaneWord#1](../vsto/codesnippet/VisualBasic/Trin_VstcoreActionsPaneWordVB/ActionsControl.vb#1)]
     [!code-csharp[Trin_VstcoreActionsPaneWord#1](../vsto/codesnippet/CSharp/Trin_VstcoreActionsPaneWordCS/ActionsControl.cs#1)]  
  
2.  In c# müssen Sie den Ereignishandler zu Anfügen der <xref:System.Windows.Forms.UserControl.Load> Ereignis. Sie können diesen Code in Platzieren der `ActionsControl` -Konstruktor nach dem Aufruf von `InitializeComponent`. Weitere Informationen über das Erstellen von Ereignishandlern finden Sie unter [Vorgehensweise: Erstellen von Ereignishandlern in Office-Projekten](../vsto/how-to-create-event-handlers-in-office-projects.md).  
  
     [!code-csharp[Trin_VstcoreActionsPaneWord#33](../vsto/codesnippet/CSharp/Trin_VstcoreActionsPaneWordCS/ActionsControl.cs#33)]  
  
### <a name="to-set-data-binding-properties-of-the-controls"></a>Datenbindungseigenschaften Steuerelemente festlegen  
  
1.  Wählen Sie das `CompanyNameComboBox`-Steuerelement.  
  
2.  In der **Eigenschaften** Fenster, klicken Sie auf die Schaltfläche rechts neben der **DataSource** Eigenschaft, und wählen **SuppliersBindingSource**.  
  
3.  Klicken Sie auf die Schaltfläche rechts neben der **DisplayMember** Eigenschaft, und wählen **CompanyName**.  
  
4.  Erweitern Sie die **DataBindings** -Eigenschaft, klicken Sie auf die Schaltfläche rechts neben der **Text** Eigenschaft, und wählen **keine**.  
  
5.  Wählen Sie das `ProductNameListBox`-Steuerelement.  
  
6.  In der **Eigenschaften** Fenster, klicken Sie auf die Schaltfläche rechts neben der **DataSource** Eigenschaft, und wählen **ProductsBindingSource**.  
  
7.  Klicken Sie auf die Schaltfläche rechts neben der **DisplayMember** Eigenschaft, und wählen **ProductName**.  
  
8.  Erweitern Sie die **DataBindings** -Eigenschaft, klicken Sie auf die Schaltfläche rechts neben der **SelectedValue** Eigenschaft, und wählen **keine**.  
  
## <a name="add-a-method-to-insert-data-into-a-table"></a>Hinzufügen einer Methode zum Einfügen von Daten in einer Tabelle  
 Die nächste Aufgabe ist, lesen Sie die Daten aus den gebundenen Steuerelementen und eine Tabelle im Word-Dokument füllen. Zunächst erstellen Sie eine Prozedur zum Formatieren der Spaltenüberschriften in der Tabelle, und fügen Sie dann die `AddData` Methode zum Erstellen und formatieren eine Word-Tabelle.  
  
### <a name="to-format-the-table-headings"></a>Um die Tabellenüberschriften formatieren  
  
1.  In der `ActionsControl` Klasse, erstellen Sie eine Methode, um die Spaltenüberschriften der Tabelle zu formatieren.  
  
     [!code-vb[Trin_VstcoreActionsPaneWord#2](../vsto/codesnippet/VisualBasic/Trin_VstcoreActionsPaneWordVB/ActionsControl.vb#2)]
     [!code-csharp[Trin_VstcoreActionsPaneWord#2](../vsto/codesnippet/CSharp/Trin_VstcoreActionsPaneWordCS/ActionsControl.cs#2)]  
  
### <a name="to-create-the-table"></a>Zum Erstellen der Tabelle  
  
1.  In der `ActionsControl` Klasse, eine Methode, die eine Tabelle erstellt wird, falls es sich bei einer nicht bereits vorhanden, und Hinzufügen von Daten aus dem Bereich "Aktionen" auf die Tabelle zu schreiben.  
  
     [!code-vb[Trin_VstcoreActionsPaneWord#3](../vsto/codesnippet/VisualBasic/Trin_VstcoreActionsPaneWordVB/ActionsControl.vb#3)]
     [!code-csharp[Trin_VstcoreActionsPaneWord#3](../vsto/codesnippet/CSharp/Trin_VstcoreActionsPaneWordCS/ActionsControl.cs#3)]  
  
### <a name="to-insert-text-into-a-word-table"></a>Zum Einfügen von Text in einem Word-Tabelle  
  
1.  Fügen Sie den folgenden Code der <xref:System.Windows.Forms.Control.Click> -Ereignishandler von dem **einfügen** Schaltfläche.  
  
     [!code-vb[Trin_VstcoreActionsPaneWord#4](../vsto/codesnippet/VisualBasic/Trin_VstcoreActionsPaneWordVB/ActionsControl.vb#4)]
     [!code-csharp[Trin_VstcoreActionsPaneWord#4](../vsto/codesnippet/CSharp/Trin_VstcoreActionsPaneWordCS/ActionsControl.cs#4)]  
  
2.  In c# müssen Sie erstellen einen Ereignishandler für die <xref:System.Windows.Forms.Control.Click> -Ereignis der Schaltfläche.  Sie können diesen Code in Platzieren der <xref:System.Windows.Forms.UserControl.Load> -Ereignishandler des der `ActionsControl` Klasse.  
  
     [!code-csharp[Trin_VstcoreActionsPaneWord#5](../vsto/codesnippet/CSharp/Trin_VstcoreActionsPaneWordCS/ActionsControl.cs#5)]  
  
## <a name="show-the-actions-pane"></a>Zeigen Sie den Bereich "Aktionen"  
 Der Bereich "Aktionen" wird angezeigt, wenn Steuerelemente hinzugefügt haben.  
  
### <a name="to-show-the-actions-pane"></a>Der Bereich "Aktionen" angezeigt.  
  
1.  In **Projektmappen-Explorer**, mit der rechten Maustaste **ThisDocument.vb** oder **ThisDocument.cs**, und klicken Sie dann auf **Ansichtscode** im Kontextmenü auf.  
  
2.  Erstellen Sie eine neue Instanz des Steuerelements am oberen Rand der `ThisDocument` Klasse, sodass sie wie im folgenden Beispiel aussieht.  
  
     [!code-csharp[Trin_VstcoreActionsPaneWord#6](../vsto/codesnippet/CSharp/Trin_VstcoreActionsPaneWordCS/ThisDocument.cs#6)]
     [!code-vb[Trin_VstcoreActionsPaneWord#6](../vsto/codesnippet/VisualBasic/Trin_VstcoreActionsPaneWordVB/ThisDocument.vb#6)]  
  
3.  Fügen Sie Code in die <xref:Microsoft.Office.Tools.Word.Document.Startup> -Ereignishandler des `ThisDocument` , damit sie wie im folgenden Beispiel aussieht.  
  
     [!code-csharp[Trin_VstcoreActionsPaneWord#7](../vsto/codesnippet/CSharp/Trin_VstcoreActionsPaneWordCS/ThisDocument.cs#7)]
     [!code-vb[Trin_VstcoreActionsPaneWord#7](../vsto/codesnippet/VisualBasic/Trin_VstcoreActionsPaneWordVB/ThisDocument.vb#7)]  
  
## <a name="test-the-application"></a>Testen der Anwendung  
 Jetzt können Sie testen, das Dokument, um sicherzustellen, dass der Bereich "Aktionen", das angezeigt wird, wenn das Dokument geöffnet wird. Für die Master/Detail-Beziehung in den Steuerelementen im Aktionsbereich zu testen, und stellen Sie sicher, dass Daten in einem Wort aufgefüllt werden Tabelle, wenn die **einfügen** geklickt wird.  
  
### <a name="to-test-your-document"></a>So testen Sie das Dokument  
  
1.  Drücken Sie **F5** um Ihr Projekt auszuführen.  
  
2.  Vergewissern Sie sich, dass der Bereich "Aktionen" angezeigt wird.  
  
3.  Wählen Sie ein Unternehmen im Kombinationsfeld aus, und überprüfen Sie, ob die Elemente in der **Produkte** Liste ändern.  
  
4.  Wählen Sie ein Produkt aus, klicken Sie auf **einfügen** im Aktionsbereich, und stellen Sie sicher, dass die Produktdetails der Word-Tabelle hinzugefügt werden.  
  
5.  Fügen Sie zusätzliche Produkte aus verschiedenen Unternehmen ein.  
  
## <a name="next-steps"></a>Nächste Schritte  
 In dieser exemplarischen Vorgehensweise wird gezeigt, die Grundlagen der Datenbindung an Steuerelemente in einem Aktionsbereich in Word. Die folgenden Aufgaben könnten sich daran anschließen:  
  
-   Binden von Daten an Steuerelemente in Excel. Weitere Informationen finden Sie unter [Exemplarische Vorgehensweise: Binden von Daten an Steuerelemente in einem Excel-Aktionsbereich](../vsto/walkthrough-binding-data-to-controls-on-an-excel-actions-pane.md).  
  
-   Bereitstellen des Projekts an. Weitere Informationen finden Sie unter [Bereitstellen einer Office-Projektmappe mithilfe von ClickOnce](../vsto/deploying-an-office-solution-by-using-clickonce.md).  
  
## <a name="see-also"></a>Siehe auch  
 [Übersicht über den Aktionsbereich](../vsto/actions-pane-overview.md)   
 [Vorgehensweise: Hinzufügen eines Aktionsbereichs zu Word-Dokumenten oder Excel-Arbeitsmappen](../vsto/how-to-add-an-actions-pane-to-word-documents-or-excel-workbooks.md)   
 [Binden von Daten an Steuerelemente in Office-Projektmappen](../vsto/binding-data-to-controls-in-office-solutions.md)  
