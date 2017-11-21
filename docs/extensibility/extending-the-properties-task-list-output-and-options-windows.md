---
title: Erweitern die Eigenschaften, die Aufgabenliste, die Ausgabe und die Optionen Windows | Microsoft Docs
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- properties pane
- task list
- output window
- properties window
- tutorials
- tool windows
ms.assetid: 06990510-5424-44b8-9fd9-6481acec5c76
caps.latest.revision: "37"
author: gregvanl
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: f94a8364f52f7723a1ab9dae6114a8bb66a91683
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 10/31/2017
---
# <a name="extending-the-properties-task-list-output-and-options-windows"></a>Erweitern Sie die Eigenschaften, die Aufgabenliste, die Ausgabe und die Optionen Windows
Sie können alle Toolfenster in Visual Studio zugreifen. In dieser exemplarischen Vorgehensweise wird gezeigt, wie Informationen über das Toolfenster in ein neues Integration **Optionen** Seiten- und eine neue Einstellung für die **Eigenschaften** Seite sowie Informationen zum Schreiben in die **Aufgabenliste** und **Ausgabe** Windows.  
  
## <a name="prerequisites"></a>Erforderliche Komponenten  
 Ab Visual Studio 2015, führen Sie Sie nicht Visual Studio-SDK aus dem Downloadcenter installieren. Sie ist als optionales Feature in Visual Studio-Setup aus. Sie können das VS-SDK auch später installieren. Weitere Informationen finden Sie unter [Installieren von Visual Studio SDK](../extensibility/installing-the-visual-studio-sdk.md).  
  
## <a name="create-an-extension-with-a-tool-window"></a>Erstellen Sie eine Erweiterung mit einem Toolfenster  
  
1.  Erstellen Sie ein Projekt mit dem Namen **"Todolist"** die VSIX-Vorlage, und fügen Sie eine Elementvorlage für benutzerdefiniertes Tool-Fenster mit dem Namen **TodoWindow**.  
  
    > [!NOTE]
    >  Weitere Informationen zum Erstellen von Erweiterung mit einem Toolfenster, finden Sie unter [erstellen eine Erweiterung mit einem Toolfenster](../extensibility/creating-an-extension-with-a-tool-window.md).  
  
## <a name="set-up-the-tool-window"></a>Richten Sie das Toolfenster  
 Fügen Sie ein Textfeld, geben Sie ein neues TODO-Element, eine Schaltfläche, um das neue Element der Liste hinzuzufügen, und ein Listenfeld zum Anzeigen von Elementen in der Liste hinzu.  
  
1.  Löschen Sie die Schaltfläche, TextBox und StackPanel-Steuerelemente in TodoWindow.xaml von der UserControl.  
  
    > [!NOTE]
    >  Dies löscht keine der **button1_Click** -Ereignishandler in einem späteren Schritt wieder verwendet wird.  
  
2.  Aus der **alle WPF-Steuerelemente** Teil der **Toolbox**, ziehen Sie eine **Zeichenbereich** Steuerelement am Raster.  
  
3.  Ziehen Sie eine **Textfeld**, **Schaltfläche**, und ein **ListBox** auf den Zeichenbereich. Ordnen Sie die Elemente so an, dass das Textfeld ein, und die Schaltfläche auf der gleichen Ebene sind und im Listenfeld den Rest des Fensters unten, wie in der folgenden Abbildung füllt.  
  
     ![Beendet das Toolfenster "](../extensibility/media/t5-toolwindow.png "T5-(Toolfenster)")  
  
4.  Klicken Sie im Bereich "XAML" die Schaltfläche "Suchen", und die Content-Eigenschaft auf festgelegt **hinzufügen**. Verbinden Sie den Ereignishandler der Schaltfläche auf das Schaltflächen-Steuerelement durch Hinzufügen einer `Click="button1_Click"` Attribut. Das Canvas-Block sollte wie folgt aussehen:  
  
    ```xml  
    <Canvas HorizontalAlignment="Left" Width="306">  
        <TextBox x:Name="textBox" HorizontalAlignment="Left" Height="23" Margin="10,10,0,0" TextWrapping="Wrap" Text="TextBox" VerticalAlignment="Top" Width="208"/>  
            <Button x:Name="button" Content="Add" HorizontalAlignment="Left" Margin="236,13,0,0" VerticalAlignment="Top" Width="48" Click="button1_Click"/>  
            <ListBox x:Name="listBox" HorizontalAlignment="Left" Height="222" Margin="10,56,0,0" VerticalAlignment="Top" Width="274"/>  
    </Canvas>  
    ```  
  
#### <a name="customize-the-constructor"></a>Den Konstruktor anpassen  
  
1.  Fügen Sie in der Datei TodoWindowControl.xaml.cs die folgende Anweisung:  
  
    ```csharp  
    using System;  
    ```  
  
2.  Fügen Sie einen öffentlichen Verweis auf die TodoWindow und haben Sie den TodoWindowControl-Konstruktor einen Parameter TodoWindow aufnehmen. Der Code sollte wie folgt aussehen:  
  
    ```csharp  
    public TodoWindow parent;  
  
    public TodoWindowControl(TodoWindow window)  
    {  
        InitializeComponent();  
        parent = window;  
    }  
    ```  
  
3.  Ändern Sie in TodoWindow.cs TodoWindowControl-Konstruktor, um den TodoWindow-Parameter enthalten. Der Code sollte wie folgt aussehen:  
  
    ```csharp  
    public TodoWindow() : base(null)  
    {  
        this.Caption = "TodoWindow";  
        this.BitmapResourceID = 301;  
        this.BitmapIndex = 1;  
  
         this.Content = new TodoWindowControl(this);  
    }  
    ```  
  
## <a name="create-an-options-page"></a>Erstellen einer Optionsseite  
 Sie können angeben, dass eine Seite in der **Optionen** Dialogfeld, sodass Benutzer die Einstellungen für das Toolfenster ändern können. Erstellen einer Optionsseite erfordert eine Klasse, die die Optionen und einen Eintrag in der Datei TodoListPackage.cs oder TodoListPackage.vb beschreiben.  
  
1.  Fügen Sie eine Klasse mit dem Namen `ToolsOptions.cs`. Legen Sie die ToolsOptions-Klasse, die von erben <xref:Microsoft.VisualStudio.Shell.DialogPage>.  
  
    ```csharp  
    class ToolsOptions : DialogPage  
    {  
    }  
    ```  
  
2.  Fügen Sie die folgende Anweisung:  
  
    ```csharp  
    using Microsoft.VisualStudio.Shell;  
    ```  
  
3.  Die Seite "Optionen" in dieser exemplarischen Vorgehensweise bietet nur eine Option, die mit dem Namen DaysAhead. Hinzufügen eines privates Felds mit dem Namen **DaysAhead** und eine Eigenschaft namens **DaysAhead** der ToolsOptions-Klasse:  
  
    ```csharp  
    private double daysAhead;  
  
    public double DaysAhead  
    {  
        get { return daysAhead; }  
        set { daysAhead = value; }  
    }  
    ```  
  
 Jetzt müssen Sie das Projekt dieser Seite erkennen.  
  
#### <a name="make-the-options-page-available-to-users"></a>Die Seite "Optionen" für Benutzer verfügbar machen  
  
1.  Fügen Sie in TodoWindowPackage.cs, eine <xref:Microsoft.VisualStudio.Shell.ProvideOptionPageAttribute> der TodoWindowPackage-Klasse:  
  
    ```csharp  
    [ProvideOptionPage(typeof(ToolsOptions), "ToDo", "General", 101, 106, true)]  
    ```  
  
2.  Der erste Parameter an den Konstruktor ProvideOptionPage ist der Typ der Klasse ToolsOptions, die Sie zuvor erstellt haben. Der zweite Parameter ist "ToDo", ist der Name der Kategorie in den **Optionen** (Dialogfeld). Der dritte Parameter "Allgemein", ist der Name der Unterkategorie, der die **Optionen** (Dialogfeld), in denen die Seite "Optionen" verfügbar sein wird. Die nächsten beiden Parameter sind Ressourcen-IDs für Zeichenfolgen. der erste ist der Name der Kategorie, und die zweite ist der Name der Unterkategorie. Der letzte Parameter bestimmt, ob diese Seite mithilfe der Automatisierung zugegriffen werden kann.  
  
     Wenn ein Benutzer die Seite "Optionen" geöffnet wird, sollte er die folgende Abbildung ähneln.  
  
     ![Seite "Optionen"](../extensibility/media/t5optionspage.gif "T5OptionsPage")  
  
     Beachten Sie die Kategorie **ToDo** und die Unterkategorie **allgemeine**.  
  
## <a name="make-data-available-to-the-properties-window"></a>Verfügbarmachen von Daten für das Eigenschaftenfenster  
 Sie können folgendermaßen vor, um Informationen verfügbar machen, durch Erstellen einer Klasse mit dem Namen TodoItem, in dem Informationen zu den einzelnen Elementen in der TODO-Liste gespeichert.  
  
1.  Fügen Sie eine Klasse mit dem Namen `TodoItem.cs`.  
  
     Wenn das Toolfenster Benutzern zur Verfügung steht, werden die Elemente im Listenfeld durch TodoItems dargestellt werden. Wenn der Benutzer eines dieser Elemente im Listenfeld wählt der **Eigenschaften** Fenster werden Informationen über das Element angezeigt.  
  
     Um Daten in verfügbar machen die **Eigenschaften** Fenster, wandeln Sie die Daten in öffentlichen Eigenschaften, die zwei spezielle Attribute verfügen, `Description` und `Category`. `Description`ist der Text, der am unteren Rand der **Eigenschaften** Fenster. `Category`Bestimmt, in dem die Eigenschaft angezeigt werden sollte die **Eigenschaften** Fenster wird angezeigt, der **nach Kategorien** anzeigen. In der folgenden Abbildung der **Eigenschaften** Fenster befindet sich im **nach Kategorien** anzeigen, die **Namen** Eigenschaft in der **ToDo Fields** Kategorie ist ausgewählt, und die Beschreibung der **Namen** Eigenschaft wird am unteren Rand des Fensters angezeigt.  
  
     ![Fenster "Eigenschaften"](../extensibility/media/t5properties.png "T5Properties")  
  
2.  Fügen Sie die folgenden using-Anweisungen die TodoItem.cs-Datei.  
  
    ```csharp  
    using System.ComponentModel;  
    using System.Windows.Forms;  
    using Microsoft.VisualStudio.Shell.Interop;  
    ```  
  
3.  Hinzufügen der `public` Zugriffsmodifizierer in der Klassendeklaration.  
  
    ```csharp  
    public class TodoItem  
    {  
    }  
    ```  
  
     Fügen Sie die beiden Eigenschaften, Namen und die DueDate hinzu. Wir müssen die UpdateList() und CheckForErrors() später durchführen.  
  
    ```csharp  
    public class TodoItem  
    {  
        private TodoWindowControl parent;  
        private string name;  
        [Description("Name of the ToDo item")]  
        [Category("ToDo Fields")]  
        public string Name  
        {  
            get { return name; }  
            set  
            {  
                name = value;  
                parent.UpdateList(this);  
            }  
        }  
  
        private DateTime dueDate;  
        [Description("Due date of the ToDo item")]  
        [Category("ToDo Fields")]  
        public DateTime DueDate  
        {  
            get { return dueDate; }  
            set  
            {  
                dueDate = value;  
                parent.UpdateList(this);  
                parent.CheckForErrors();  
            }  
        }  
    }  
    ```  
  
4.  Fügen Sie einen privaten Verweis auf das Benutzersteuerelement. Fügen Sie einen Konstruktor, der das Benutzersteuerelement und den Namen für dieses TODO-Element akzeptiert. Um den Wert für DaysAhead zu suchen, ruft er die Seite Options-Eigenschaft ab.  
  
    ```csharp  
    private TodoWindowControl parent;  
  
    public TodoItem(TodoWindowControl control, string itemName)  
    {  
        parent = control;  
        name = itemName;  
        dueDate = DateTime.Now;  
  
        double daysAhead = 0;  
        IVsPackage package = parent.parent.Package as IVsPackage;  
        if (package != null)  
        {  
            object obj;  
            package.GetAutomationObject("ToDo.General", out obj);  
  
            ToolsOptions options = obj as ToolsOptions;  
            if (options != null)  
            {  
                daysAhead = options.DaysAhead;  
            }  
        }  
  
        dueDate = dueDate.AddDays(daysAhead);  
    }  
    ```  
  
5.  Da Instanzen von der `TodoItem` Klasse im Listenfeld gespeichert wird und im Listenfeld rufen die `ToString` -Funktion, die Sie überladen müssen die `ToString` Funktion. Fügen Sie den folgenden Code Sie TodoItem.cs, nach dem Konstruktor und vor dem Ende der Klasse hinzu.  
  
    ```csharp  
    public override string ToString()  
    {  
        return name + " Due: " + dueDate.ToShortDateString();  
    }  
    ```  
  
6.  Fügen Sie in TodoWindowControl.xaml.cs, Stubmethoden der TodoWindowControl-Klasse für die `CheckForError` und `UpdateList` Methoden. Fügen Sie sie nach der ProcessDialogChar und vor dem Ende der Datei.  
  
    ```csharp  
    public void CheckForErrors()  
    {  
    }  
    public void UpdateList(TodoItem item)  
    {  
    }  
    ```  
  
     Die `CheckForError` Methodenaufruf wird eine Methode, die im übergeordneten Objekt den gleichen Namen hat, und diese Methode überprüft, ob Fehler aufgetreten sind und ordnungsgemäß zu behandeln. Die `UpdateList` Methode aktualisiert das Listenfeld im übergeordneten Steuerelement; die Methode wird aufgerufen, wenn die `Name` und `DueDate` Eigenschaften in dieser Klasse ändern. Sie werden später implementiert werden.  
  
## <a name="integrate-into-the-properties-window"></a>Integrieren Sie in das Eigenschaftenfenster  
 Nun den Code schreiben, der im Listenfeld verwaltet, die an gebunden werden, wird die **Eigenschaften** Fenster.  
  
 Müssen Sie die Schaltfläche ändern klicken Sie auf das Textfeld zu lesen, erstellen Sie eine TodoItem-Handler, und fügt es dem Listenfeld hinzu.  
  
1.  Ersetzen Sie die vorhandene `button1_Click` -Funktion mit Code, der erstellt eine neue TodoItem und fügt es dem Listenfeld hinzu. Er ruft TrackSelection(), der weiter unten definiert wird.  
  
    ```csharp  
    private void button1_Click(object sender, RoutedEventArgs e)  
    {  
        if (textBox.Text.Length > 0)  
        {  
            var item = new TodoItem(this, textBox.Text);  
            listBox.Items.Add(item);  
            TrackSelection();  
            CheckForErrors();  
        }  
    }  
    ```  
  
2.  Wählen Sie in der Entwurfsansicht das ListBox-Steuerelement. In der **Eigenschaften** klicken Sie im Fenster der **Ereignishandler** Schaltfläche, und suchen Sie das SelectionChanged-Ereignis. Füllen Sie das Textfeld mit **ListBox_SelectionChanged**. Dadurch wird ein Stub für einen SelectionChanged Handler hinzugefügt und das Ereignis zugewiesen.  
  
3.  Implementieren Sie die TrackSelection()-Methode. Da Sie abrufen müssen die <xref:Microsoft.VisualStudio.Shell.Interop.SVsUIShell> <xref:Microsoft.VisualStudio.Shell.Interop.STrackSelection> -Dienste, die Sie vornehmen müssen die <xref:Microsoft.VisualStudio.Shell.WindowPane.GetService%2A> der TodoWindowControl zugänglich. Fügen Sie die folgende Methode der TodoWindow-Klasse:  
  
    ```  
    internal object GetVsService(Type service)  
    {  
        return GetService(service);  
    }  
    ```  
  
4.  Fügen Sie die folgenden using-Anweisungen hinzu TodoWindowControl.xaml.cs:  
  
    ```csharp  
    using System.Runtime.InteropServices;  
    using Microsoft.VisualStudio.Shell.Interop;  
    using Microsoft.VisualStudio;  
    using Microsoft.VisualStudio.Shell;  
    ```  
  
5.  Füllen Sie die SelectionChanged-Ereignishandler wie folgt aus:  
  
    ```  
    private void listBox_SelectionChanged(object sender, SelectionChangedEventArgs e)  
    {  
        TrackSelection();  
    }  
    ```  
  
6.  Füllen Sie die Funktion überschrieben, die Integration in bereitstellen, wird jetzt die **Eigenschaften** Fenster. Diese Funktion wird aufgerufen, wenn der Benutzer ein Element in das Listenfeld fügt oder ein Element im Listenfeld klickt. Er fügt den Inhalt des Listenfelds eine SelectionContainer hinzu, und übergibt die SelectionContainer auf die **Eigenschaften** Fensters <xref:Microsoft.VisualStudio.Shell.Interop.ITrackSelection.OnSelectChange%2A> -Ereignishandler. Der Dienst überschrieben verfolgt die ausgewählten Objekte in der Benutzeroberfläche (UI) und zeigt ihre Eigenschaften  
  
    ```csharp  
    private SelectionContainer mySelContainer;  
    private System.Collections.ArrayList mySelItems;  
    private IVsWindowFrame frame = null;  
  
    private void TrackSelection()  
    {  
        if (frame == null)  
        {  
            var shell = parent.GetVsService(typeof(SVsUIShell)) as IVsUIShell;  
            if (shell != null)  
            {  
                var guidPropertyBrowser = new  
                Guid(ToolWindowGuids.PropertyBrowser);  
                shell.FindToolWindow((uint)__VSFINDTOOLWIN.FTW_fForceCreate,  
                ref guidPropertyBrowser, out frame);  
            }  
        }  
        if (frame != null)  
            {  
                frame.Show();  
            }  
        if (mySelContainer == null)  
        {  
            mySelContainer = new SelectionContainer();  
        }  
  
        mySelItems = new System.Collections.ArrayList();  
  
        var selected = listBox.SelectedItem as TodoItem;  
        if (selected != null)  
        {  
            mySelItems.Add(selected);  
        }  
  
        mySelContainer.SelectedObjects = mySelItems;  
  
        ITrackSelection track = parent.GetVsService(typeof(STrackSelection))  
                                as ITrackSelection;  
        if (track != null)  
        {  
            track.OnSelectChange(mySelContainer);  
        }  
    }  
    ```  
  
     Nun, dass Sie eine Klasse haben, die die **Eigenschaften** Fenster verwenden kann, können Sie integrieren die **Eigenschaften** Fenster mit dem Toolfenster. Klickt der Benutzer ein Element im Listenfeld im Toolfenster, die **Eigenschaften** Fenster entsprechend aktualisiert werden soll. Auf ähnliche Weise, wenn der Benutzer ändert TODO-Element in der **Eigenschaften** Fenster des zugeordneten Elements aktualisiert werden soll.  
  
7.  Fügen Sie nun die restliche den Funktionscode UpdateList in TodoWindowControl.xaml.cs hinzu. Es sollte löschen und erneut die geänderte TodoItem aus dem Listenfeld hinzuzufügen.  
  
    ```csharp  
    public void UpdateList(TodoItem item)  
    {  
        var index = listBox.SelectedIndex;  
        listBox.Items.RemoveAt(index);  
        listBox.Items.Insert(index, item);  
        listBox.SelectedItem = index;  
    }  
    ```  
  
8.  Testen Sie den Code ein. Erstellen Sie das Projekt, und starten Sie das Debugging. Die experimentelle Instanz sollte angezeigt werden.  
  
9. Öffnen der **Extras / Optionen** Seiten. Es sollte die TODO-Kategorie im linken Bereich angezeigt. Kategorien sind in alphabetischer aufgelistet, also schauen Sie unter der Ts.  
  
10. Auf der Seite für den TODO-Optionen, sehen Sie die DaysAhead-Eigenschaft auf festgelegt **0**. Ändern Sie ihn in **2**.  
  
11. Für die Sicht / Weitere Fenster öffnen Sie im Menü **TodoWindow**. Typ **EndDate** in das Textfeld ein und klicken Sie auf **hinzufügen**.  
  
12. In der Liste sollte ein Datum zwei Tage später, nach dem aktuellen Datum angezeigt werden.  
  
## <a name="add-text-to-the-output-window-and-items-to-the-task-list"></a>Hinzufügen von Text in das Fenster "Ausgabe" und die Elemente in der Aufgabenliste  
 Für die **Aufgabenliste**, Sie erstellen ein neues Objekt des Typs Task, und fügen Sie dann dieses Task-Objekt an den **Aufgabenliste** durch Aufrufen der Methode hinzufügen. Zum Schreiben in die **Ausgabe** , rufen Sie dessen GetPane-Methode, um ein Objekt zu erhalten, und rufen Sie anschließend die OutputString-Methode des Objekts im Bereich.  
  
1.  In TodoWindowControl.xaml.cs in der `button1_Click` -Methode, fügen Sie Code zum Abrufen der **allgemeine** im Bereich der **Ausgabe** Fenster (die Standardeinstellung), und in diese schreiben. Die Methode sollte wie folgt aussehen:  
  
    ```csharp  
    private void button1_Click(object sender, EventArgs e)  
    {  
        if (textBox.Text.Length > 0)  
        {  
            var item = new TodoItem(this, textBox.Text);  
            listBox.Items.Add(item);  
  
            var outputWindow = parent.GetVsService(  
                typeof(SVsOutputWindow)) as IVsOutputWindow;  
            IVsOutputWindowPane pane;  
            Guid guidGeneralPane = VSConstants.GUID_OutWindowGeneralPane;  
            outputWindow.GetPane(ref guidGeneralPane, out pane);  
            if (pane != null)  
            {  
                 pane.OutputString(string.Format(  
                    "To Do item created: {0}\r\n",  
                 item.ToString()));  
        }  
            TrackSelection();  
            CheckForErrors();  
        }  
    }  
    ```  
  
2.  Die Aufgabenliste Elemente hinzufügen, müssen Sie eine der TodoWindowControl-Klasse eine geschachtelte Klasse hinzu. Die geschachtelte Klasse abgeleitet sein muss <xref:Microsoft.VisualStudio.Shell.TaskProvider>. Fügen Sie den folgenden Code am Ende der TodoWindowControl-Klasse.  
  
    ```csharp  
    [Guid("72de1eAD-a00c-4f57-bff7-57edb162d0be")]  
    public class TodoWindowTaskProvider : TaskProvider  
    {  
        public TodoWindowTaskProvider(IServiceProvider sp)  
            : base(sp)  
        {  
        }  
    }  
    ```  
  
3.  Fügen Sie einen privaten Verweis auf TodoTaskProvider und eine CreateProvider()-Methode der TodoWindowControl-Klasse. Der Code sollte wie folgt aussehen:  
  
    ```csharp  
    private TodoWindowTaskProvider taskProvider;  
    private void CreateProvider()  
    {  
        if (taskProvider == null)  
        {  
            taskProvider = new TodoWindowTaskProvider(parent);  
            taskProvider.ProviderName = "To Do";  
        }  
    }  
    ```  
  
4.  Fügen Sie ClearError(), die der Aufgabenliste löscht, und ReportError(), das einen Eintrag in die Taskliste hinzufügt hinzu, der TodoWindowControl-Klasse.  
  
    ```csharp  
    private void ClearError()  
    {  
        CreateProvider();  
        taskProvider.Tasks.Clear();  
    }  
    private void ReportError(string p)  
    {  
        CreateProvider();  
        var errorTask = new Task();  
        errorTask.CanDelete = false;  
        errorTask.Category = TaskCategory.Comments;  
        errorTask.Text = p;  
  
        taskProvider.Tasks.Add(errorTask);  
  
        taskProvider.Show();  
  
        var taskList = parent.GetVsService(typeof(SVsTaskList))  
            as IVsTaskList2;  
        if (taskList == null)  
        {  
            return;  
        }  
  
        var guidProvider = typeof(TodoWindowTaskProvider).GUID;  
         taskList.SetActiveProvider(ref guidProvider);  
    }  
    ```  
  
5.  Implementieren Sie jetzt die CheckForErrors-Methode, wie folgt an.  
  
    ```csharp  
    public void CheckForErrors()  
    {  
        foreach (TodoItem item in listBox.Items)  
        {  
            if (item.DueDate < DateTime.Now)  
            {  
                ReportError("To Do Item is out of date: "  
                    + item.ToString());  
            }  
        }  
    }  
    ```  
  
## <a name="trying-it-out"></a>Ausprobieren  
  
1.  Erstellen Sie das Projekt, und starten Sie das Debugging. Die experimentelle Instanz angezeigt wird.  
  
2.  Öffnen Sie die TodoWindow (**Ansicht / anderen Fenstern / TodoWindow**).  
  
3.  Geben Sie ein Element in das Textfeld ein, und klicken Sie dann auf **hinzufügen**.  
  
     Ein Fälligkeitsdatum 2 Tage nach dem Listenfeld heute hinzugefügt wird. Es werden keine Fehler generiert, und die **Aufgabenliste** (**anzeigen / Aufgabe Liste**) müssen keine Einträge.  
  
4.  Jetzt ändern Sie die Einstellung für die **Extras / Optionen / ToDo** Seite von **2** an **0**.  
  
5.  Geben Sie etwas in der **TodoWindow** , und klicken Sie dann auf **hinzufügen** erneut aus. Dies bewirkt einen Fehler, und auch einen Eintrag in der **Aufgabenliste**.  
  
     Wenn Sie Elemente hinzufügen, wird das ursprüngliche Datum jetzt plus 2 Tage festgelegt.  
  
6.  Auf der **Ansicht** Menü klicken Sie auf **Ausgabe** So öffnen die **Ausgabe** Fenster.  
  
     Beachten Sie, dass jedes Mal, dass ein Element hinzufügen, wird eine Meldung angezeigt, der **Aufgabenliste** Bereich.  
  
7.  Klicken Sie auf eines der Elemente im Listenfeld.  
  
     Die **Eigenschaften** Fenster werden die beiden Eigenschaften für das Element angezeigt.  
  
8.  Ändern Sie eine der Eigenschaften, und drücken Sie dann die EINGABETASTE.  
  
     Das Element wird im Listenfeld aktualisiert.