---
title: "Erweitern Sie die Eigenschaften, die Aufgabenliste, die Ausgabe und die Optionen Windows | Microsoft Docs"
ms.custom: ""
ms.date: "12/03/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "Eigenschaftenbereich"
  - "Aufgabenliste"
  - "Fenster "Ausgabe""
  - "Fenster "Eigenschaften""
  - "Lernprogramme"
  - "Toolfenster"
ms.assetid: 06990510-5424-44b8-9fd9-6481acec5c76
caps.latest.revision: 37
caps.handback.revision: 37
ms.author: "gregvanl"
manager: "ghogen"
---
# Erweitern Sie die Eigenschaften, die Aufgabenliste, die Ausgabe und die Optionen Windows
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

Sie können alle Toolfenster in Visual Studio zugreifen. In dieser exemplarischen Vorgehensweise veranschaulicht, wie Informationen über das Toolfenster in ein neues integrieren **Optionen** Seite und eine neue Einstellung für die **Eigenschaften** Seite sowie das Schreiben in die **Aufgabenliste** und **Ausgabe** Windows.  
  
## Vorbereitungsmaßnahmen  
 Starten in Visual Studio 2015, führen Sie Sie nicht Visual Studio SDK aus dem Downloadcenter installieren. Er ist als optionales Feature in Visual Studio\-Setup enthalten. Sie können auch später im Visual Studio SDK installieren. Weitere Informationen finden Sie unter [Das Visual Studio SDK installieren](../extensibility/installing-the-visual-studio-sdk.md).  
  
## Erstellen Sie eine Erweiterung mit einem Toolfenster  
  
1.  Erstellen Sie ein Projekt mit dem Namen **TodoList** mithilfe der VSIX\-Projektvorlage, und fügen Sie eine benutzerdefiniertes Tool Fenster Elementvorlage, die mit dem Namen **TodoWindow**.  
  
    > [!NOTE]
    >  Weitere Informationen zum Erstellen von einer Erweiterungs mit einem Toolfenster, finden Sie unter [Erstellen eine Erweiterung mit einem Toolfenster](../extensibility/creating-an-extension-with-a-tool-window.md).  
  
## Richten Sie das Toolfenster  
 Fügen Sie ein Textfeld, geben Sie ein neues TODO\-Element, das eine Schaltfläche, um das neue Element in der Liste hinzuzufügen, und ein Listenfeld die Elemente in der Liste angezeigt.  
  
1.  Löschen Sie in TodoWindow.xaml die Schaltfläche, TextBox und StackPanel\-Steuerelemente von der UserControl.  
  
    > [!NOTE]
    >  Dies löscht nicht die **button1\_Click** \-Ereignishandler in einem späteren Schritt wiederverwendet wird.  
  
2.  Aus der **alle WPF\-Steuerelemente** Teil der **Toolbox**, ziehen Sie eine **Canvas** Steuerelement am Raster.  
  
3.  Ziehen Sie eine **Textfeld**,  **Schaltfläche**, und ein **ListBox** der Canvas. Ordnen Sie die Elemente so an, dass das Textfeld und die Schaltfläche auf der gleichen Ebene sind und das Listenfeld den Rest des Fensters unter ihnen, wie in der folgenden Abbildung füllt.  
  
     ![Fertig gestelltes Toolfenster](../extensibility/media/t5-toolwindow.png "T5\-ToolWindow")  
  
4.  Klicken Sie im Bereich XAML die Schaltfläche "Suchen", und legen Sie dessen Eigenschaft Inhalt auf **Hinzufügen**. Schließen Sie den Ereignishandler der Schaltfläche auf das Schaltflächen\-Steuerelement durch Hinzufügen einer `Click="button1_Click"` Attribut. Der Canvas\-Block sollte wie folgt aussehen:  
  
    ```xml  
    <Canvas HorizontalAlignment="Left" Width="306">  
        <TextBox x:Name="textBox" HorizontalAlignment="Left" Height="23" Margin="10,10,0,0" TextWrapping="Wrap" Text="TextBox" VerticalAlignment="Top" Width="208"/>  
            <Button x:Name="button" Content="Add" HorizontalAlignment="Left" Margin="236,13,0,0" VerticalAlignment="Top" Width="48" Click="button1_Click"/>  
            <ListBox x:Name="listBox" HorizontalAlignment="Left" Height="222" Margin="10,56,0,0" VerticalAlignment="Top" Width="274"/>  
    </Canvas>  
    ```  
  
#### Anpassen des\-Konstruktors  
  
1.  Fügen Sie in der Datei TodoWindowControl.xaml.cs die folgende using\-Anweisung:  
  
    ```c#  
    using System;  
    ```  
  
2.  Fügen Sie einen öffentliche Verweis auf die TodoWindow und die TodoWindowControl Konstruktor einen TodoWindow\-Parameter. Der Code sollte wie folgt aussehen:  
  
    ```c#  
    public TodoWindow parent;  
  
    public TodoWindowControl(TodoWindow window)  
    {  
        InitializeComponent();  
        parent = window;  
    }  
    ```  
  
3.  Ändern Sie im TodoWindow.cs TodoWindowControl\-Konstruktor, um den TodoWindow\-Parameter enthalten. Der Code sollte wie folgt aussehen:  
  
    ```c#  
    public TodoWindow() : base(null)  
    {  
        this.Caption = "TodoWindow";  
        this.BitmapResourceID = 301;  
        this.BitmapIndex = 1;  
  
         this.Content = new TodoWindowControl(this);  
    }  
    ```  
  
## Erstellen Sie eine Optionsseite  
 Sie können angeben, dass eine Seite in der **Optionen** Dialogfeld, sodass Benutzer die Einstellungen für das Toolfenster ändern können. Erstellen eine Optionsseite erfordert eine Klasse, die die Optionen und einen Eintrag in der Datei TodoListPackage.cs oder TodoListPackage.vb beschreibt.  
  
1.  Fügen Sie eine Klasse mit dem Namen `ToolsOptions.cs`. Legen Sie die ToolsOptions\-Klasse, die von erben <xref:Microsoft.VisualStudio.Shell.DialogPage>.  
  
    ```c#  
    class ToolsOptions : DialogPage  
    {  
    }  
    ```  
  
2.  Fügen Sie die folgende using\-Anweisung:  
  
    ```c#  
    using Microsoft.VisualStudio.Shell;  
    ```  
  
3.  Die Seite "Optionen" in dieser exemplarischen Vorgehensweise bietet nur eine Option mit dem Namen DaysAhead. Fügen Sie ein privates Feld mit dem Namen **DaysAhead** und eine Eigenschaft mit dem Namen **DaysAhead** der ToolsOptions\-Klasse:  
  
    ```c#  
    private double daysAhead;  
  
    public double DaysAhead  
    {  
        get { return daysAhead; }  
        set { daysAhead = value; }  
    }  
    ```  
  
 Jetzt müssen Sie das Projekt dieser Seite hinzuweisen.  
  
#### Die Seite Optionen für Benutzer verfügbar machen  
  
1.  Fügen Sie in TodoWindowPackage.cs, eine <xref:Microsoft.VisualStudio.Shell.ProvideOptionPageAttribute> der TodoWindowPackage\-Klasse:  
  
    ```c#  
    [ProvideOptionPage(typeof(ToolsOptions), "ToDo", "General", 101, 106, true)]  
    ```  
  
2.  Der erste Parameter für den ProvideOptionPage\-Konstruktor ist der Typ der Klasse ToolsOptions, die Sie zuvor erstellt haben. Der zweite Parameter, "ToDo", ist der Name der Kategorie in der **Optionen** \(Dialogfeld\). Der dritte Parameter ist "Allgemein", ist der Name der Unterkategorie von der **Optionen** Dialogfeld, in dem die Seite Optionen verfügbar sein wird. Die nächsten beiden Parameter sind Ressourcen\-IDs für Zeichenfolgen. die erste ist der Name der Kategorie, und die zweite ist der Name der Unterkategorie. Der letzte Parameter bestimmt, ob dieser Seite zugegriffen werden kann, mithilfe der Automatisierung.  
  
     Wenn ein Benutzer die Optionsseite geöffnet wird, sollten sie die folgende Abbildung ähneln.  
  
     ![Seite Optionen](../extensibility/media/t5optionspage.png "T5OptionsPage")  
  
     Beachten Sie die Kategorie **ToDo** und die Unterkategorie **Allgemeine**.  
  
## Daten im Eigenschaftenfenster zur Verfügung stellen  
 Sie können Aufgaben Informationen verfügbar machen, durch Erstellen einer Klasse mit dem Namen TodoItem, das Informationen über die einzelnen Elemente in der Aufgabenliste gespeichert.  
  
1.  Fügen Sie eine Klasse mit dem Namen `TodoItem.cs`.  
  
     Wenn das Toolfenster für Benutzer verfügbar ist, werden die Elemente im Listenfeld durch TodoItems dargestellt werden. Wenn der Benutzer eines dieser Elemente im Listenfeld wählt die **Eigenschaften** Fenster werden Informationen zu dem Element angezeigt.  
  
     Um Daten in zur Verfügung stellen die **Eigenschaften** Fenster verwandeln Sie die Daten in öffentlichen Eigenschaften, die zwei spezifische Attribute `Description` und `Category`.`Description` ist der Text, der am unteren Rand angezeigt wird die **Eigenschaften** Fenster.`Category` Bestimmt, wo die Eigenschaft angezeigt werden soll die **Eigenschaften** Fenster wird angezeigt, der **nach Kategorien** anzeigen. In der folgenden Abbildung werden die **Eigenschaften** Fenster befindet sich im **nach Kategorien** anzeigen, die **Name** Eigenschaft in der **ToDo Fields** Kategorie ausgewählt ist, und die Beschreibung des der **Name** \-Eigenschaft wird am unteren Rand des Fensters angezeigt.  
  
     ![Eigenschaftenfenster](../extensibility/media/t5properties.png "T5Properties")  
  
2.  Fügen Sie die folgende using\-Anweisungen die TodoItem.cs\-Datei.  
  
    ```c#  
    using System.ComponentModel;  
    using System.Windows.Forms;  
    using Microsoft.VisualStudio.Shell.Interop;  
    ```  
  
3.  Hinzufügen der `public` Zugriffsmodifizierer der Klassendeklaration.  
  
    ```c#  
    public class TodoItem  
    {  
    }  
    ```  
  
     Fügen Sie die beiden Eigenschaften, Name und DueDate hinzu. Die UpdateList\(\) und CheckForErrors\(\) machen später.  
  
    ```c#  
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
  
4.  Fügen Sie einen privaten Verweis auf das Benutzersteuerelement. Fügen Sie einen Konstruktor, der das Benutzersteuerelement und der Name für diesen Eintrag. Um den Wert für DaysAhead zu ermitteln, ruft es die Optionen\-Seite\-Eigenschaft ab.  
  
    ```c#  
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
  
5.  Da Instanzen der `TodoItem` Klasse im Listenfeld gespeichert werden soll, und das Listenfeld rufen die `ToString` \-Funktion, die Sie überladen müssen die `ToString` Funktion. Fügen Sie den folgenden Code zum TodoItem.cs, nach dem Konstruktor und vor dem Ende der Klasse.  
  
    ```c#  
    public override string ToString()  
    {  
        return name + " Due: " + dueDate.ToShortDateString();  
    }  
    ```  
  
6.  Fügen Sie in TodoWindowControl.xaml.cs, Stubmethoden zur TodoWindowControl\-Klasse für die `CheckForError` und `UpdateList` Methoden. Fügen Sie sie nach dem ProcessDialogChar und vor dem Ende der Datei.  
  
    ```c#  
    public void CheckForErrors()  
    {  
    }  
    public void UpdateList(TodoItem item)  
    {  
    }  
    ```  
  
     Die `CheckForError` Methode wird eine Methode mit dem gleichen Namen im übergeordneten Objekt aufrufen, und diese Methode überprüft, ob Fehler aufgetreten sind und ordnungsgemäß zu behandeln. Die `UpdateList` \-Methode aktualisiert das Listenfeld im übergeordneten Steuerelement; die Methode wird aufgerufen, wenn die `Name` und `DueDate` Eigenschaften in dieser Klasse ändern. Sie werden später implementiert werden.  
  
## Integrieren Sie in das Eigenschaftenfenster  
 Jetzt schreiben Code, der ListBox, verwaltet die an gebunden werden, wird die **Eigenschaften** Fenster.  
  
 Sie müssen die Schaltfläche ändern Klick\-Handler, lesen das Textfeld ein, erstellen Sie ein TodoItem, und das Listenfeld hinzugefügt.  
  
1.  Ersetzen Sie die vorhandene `button1_Click` Funktion mit Code, der ein neues Aktivitätselement erstellt und in das Listenfeld hinzugefügt. Sie ruft TrackSelection\(\), der weiter unten definiert wird.  
  
    ```c#  
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
  
2.  Wählen Sie in der Entwurfsansicht das ListBox\-Steuerelement. In der **Eigenschaften** klicken Sie im Fenster der **Ereignishandler** Schaltfläche, und suchen Sie das SelectionChanged\-Ereignis. Füllen Sie das Textfeld mit **ListBox\_SelectionChanged**. Dadurch wird ein Stub für eine SelectionChanged\-Ereignishandler hinzugefügt, und das Ereignis zugewiesen.  
  
3.  Implementieren Sie die TrackSelection\(\)\-Methode. Da Sie erhalten müssen die <xref:Microsoft.VisualStudio.Shell.Interop.SVsUIShell> <xref:Microsoft.VisualStudio.Shell.Interop.STrackSelection> Dienste, die Sie vornehmen müssen die <xref:Microsoft.VisualStudio.Shell.WindowPane.GetService%2A> die TodoWindowControl zugänglich.  Fügen Sie der TodoWindow\-Klasse die folgende Methode hinzu:  
  
    ```  
    internal object GetVsService(Type service)  
    {  
        return GetService(service);  
    }  
    ```  
  
4.  Fügen Sie die folgende using\-Anweisungen zu TodoWindowControl.xaml.cs:  
  
    ```c#  
    using System.Runtime.InteropServices;  
    using Microsoft.VisualStudio.Shell.Interop;  
    using Microsoft.VisualStudio;  
    using Microsoft.VisualStudio.Shell;  
    ```  
  
5.  Füllen Sie das SelectionChanged\-Ereignishandler wie folgt aus:  
  
    ```  
    private void listBox_SelectionChanged(object sender, SelectionChangedEventArgs e)  
    {  
        TrackSelection();  
    }  
    ```  
  
6.  Füllen Sie die Funktion überschrieben, die Integration mit bieten jetzt die **Eigenschaften** Fenster. Diese Funktion wird aufgerufen, wenn der Benutzer dem Listenfeld ein Element hinzugefügt oder ein Element im Listenfeld klickt. Er fügt den Inhalt des Listenfelds eine SelectionContainer hinzu und übergibt die SelectionContainer an die **Eigenschaften** des Fensters <xref:Microsoft.VisualStudio.Shell.Interop.ITrackSelection.OnSelectChange%2A> \-Ereignishandler. Der Dienst überschrieben verfolgt ausgewählten Objekte in der Benutzeroberfläche \(UI\) und zeigt ihre Eigenschaften  
  
    ```c#  
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
  
     Nun, Sie verfügen über eine Klasse, die **Eigenschaften** Fenster verwenden kann, können Sie integrieren die **Eigenschaften** Fenster mit dem Toolfenster. Klickt der Benutzer ein Element im Listenfeld im Toolfenster, die **Eigenschaften** Fenster entsprechend aktualisiert werden soll. Wenn der Benutzer ändert einen Eintrag in der **Eigenschaften** Fenster, das zugeordnete Element aktualisiert werden soll.  
  
7.  Fügen Sie nun den restlichen Code der UpdateList in TodoWindowControl.xaml.cs. Es sollte löschen und erneut geänderte Todoitems aus dem Listenfeld hinzuzufügen.  
  
    ```c#  
    public void UpdateList(TodoItem item)  
    {  
        var index = listBox.SelectedIndex;  
        listBox.Items.RemoveAt(index);  
        listBox.Items.Insert(index, item);  
        listBox.SelectedItem = index;  
    }  
    ```  
  
8.  Testen Sie den Code. Erstellen Sie das Projekt, und starten Sie das Debugging. Die experimentelle Instanz sollte angezeigt werden.  
  
9. Öffnen Sie die **Extras \/ Optionen** Seiten. Die Kategorie "ToDo" im linken Bereich angezeigt. Kategorien werden in alphabetischer aufgeführt, so suchen Sie unter der Ts.  
  
10. Auf der Seite "Todo" sollte die DaysAhead\-Eigenschaft auf **0**. Ändern Sie ihn in **2**.  
  
11. In der Ansicht \/ Weitere Fenster öffnen Sie im Menü **TodoWindow**. Typ **EndDate** in das Textfeld und klicken Sie auf **Hinzufügen**.  
  
12. Im Listenfeld sollte ein Datum zwei Tage später als heute.  
  
## Hinzufügen von Text in das Ausgabefenster und Elemente zur Aufgabenliste  
 Für die **Aufgabenliste**, Sie erstellen ein neues Objekt des Typs Task und klicken Sie dann hinzufügen, Task\-Objekt, das **Aufgabenliste** durch Aufrufen der Add\-Methode. Zum Schreiben in die **Ausgabe** rufen Sie seine GetPane\-Methode zum Abrufen des Objekts im Bereich, und rufen Sie dann die OutputString\-Methode des Objekts im Bereich.  
  
1.  In TodoWindowControl.xaml.cs in der `button1_Click` \-Methode, fügen Sie Code zum Abrufen der **Allgemeine** im Bereich der **Ausgabe** Fenster \(der Standardname ist\), und darin schreiben. Die Methode sollte wie folgt aussehen:  
  
    ```c#  
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
  
2.  Um der Liste Elemente hinzuzufügen, müssen Sie eine geschachtelte Klasse die TodoWindowControl\-Klasse hinzu. Die geschachtelte Klasse ableiten muss <xref:Microsoft.VisualStudio.Shell.TaskProvider>. Fügen Sie folgenden Code am Ende der TodoWindowControl\-Klasse.  
  
    ```c#  
    [Guid("72de1eAD-a00c-4f57-bff7-57edb162d0be")]  
    public class TodoWindowTaskProvider : TaskProvider  
    {  
        public TodoWindowTaskProvider(IServiceProvider sp)  
            : base(sp)  
        {  
        }  
    }  
    ```  
  
3.  Fügen Sie einen privaten Verweis auf TodoTaskProvider und eine CreateProvider\(\)\-Methode der TodoWindowControl\-Klasse. Der Code sollte wie folgt aussehen:  
  
    ```c#  
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
  
4.  Fügen Sie ClearError\(\), die der Aufgabenliste löscht, und ReportError\(\), die der Aufgabenliste einen Eintrag hinzugefügt hinzu, der TodoWindowControl\-Klasse.  
  
    ```c#  
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
  
5.  Nun implementieren Sie die Methode CheckForErrors wie folgt.  
  
    ```c#  
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
  
## Ausprobieren  
  
1.  Erstellen Sie das Projekt, und starten Sie das Debugging. Die experimentelle Instanz angezeigt wird.  
  
2.  Öffnen Sie die TodoWindow \(**Anzeigen \/ andere Fenster \/ TodoWindow**\).  
  
3.  Geben Sie etwas in das Textfeld, und klicken Sie dann auf **Hinzufügen**.  
  
     Ein Fälligkeitsdatum zwei Tage nach dem Listenfeld heute hinzugefügt wird. Es werden keine Fehler generiert, und die **Aufgabenliste** \(**Anzeigen \/ Task Liste**\) sollten keine Einträge aufweisen.  
  
4.  Jetzt ändern Sie die Einstellung für die **Extras \/ Optionen \/ ToDo** Seite **2** an **0**.  
  
5.  Geben Sie etwas in die **TodoWindow** und klicken Sie dann auf **Hinzufügen** erneut. Dadurch wird ein Fehler auftritt und auch einen Eintrag in der **Aufgabenliste**.  
  
     Wenn Sie Elemente hinzufügen, wird das ursprüngliche Datum jetzt plus 2 Tage festgelegt.  
  
6.  Auf der **Ansicht** Menü klicken Sie auf **Ausgabe** zum Öffnen der **Ausgabe** Fenster.  
  
     Beachten Sie, dass jedes Mal, dass Sie ein Element hinzufügen, wird eine Meldung angezeigt, der **Aufgabenliste** Bereich.  
  
7.  Klicken Sie auf eines der Elemente im Listenfeld.  
  
     Die **Eigenschaften** werden die beiden Eigenschaften für das Element angezeigt.  
  
8.  Ändern Sie eine der Eigenschaften, und drücken Sie dann die EINGABETASTE.  
  
     Das Element im ListBox aktualisiert.