---
title: Erweitern die Eigenschaften, Aufgabenliste, Ausgabe und Optionen für Windows | Microsoft-Dokumentation
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- properties pane
- task list
- output window
- properties window
- tutorials
- tool windows
ms.assetid: 06990510-5424-44b8-9fd9-6481acec5c76
caps.latest.revision: 38
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: cf42be1e62bfb4895d29a61fcadc221d5c14bec9
ms.sourcegitcommit: 47eeeeadd84c879636e9d48747b615de69384356
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 04/23/2019
ms.locfileid: "63443905"
---
# <a name="extending-the-properties-task-list-output-and-options-windows"></a>Erweitern der Fenster für Eigenschaften, Aufgabenlisten, Ausgaben und Optionen
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Sie können alle Toolfenster in Visual Studio zugreifen. Diese exemplarische Vorgehensweise zeigt, wie Informationen über das Toolfenster in ein neues Integration **Optionen** Seite und eine neue Einstellung für die **Eigenschaften** Seite sowie das Schreiben in die **Aufgabenliste** und **Ausgabe** Windows.  
  
## <a name="prerequisites"></a>Vorraussetzungen  
 Ab Visual Studio 2015, sind Sie nicht Visual Studio SDK aus dem Downloadcenter installieren. Er ist als optionales Feature in Visual Studio-Setup enthalten. Sie können das VS-SDK auch später installieren. Weitere Informationen finden Sie unter [Installieren von Visual Studio SDK](../extensibility/installing-the-visual-studio-sdk.md).  
  
## <a name="create-an-extension-with-a-tool-window"></a>Erstellen Sie eine Erweiterung mit einem Toolfenster  
  
1. Erstellen Sie ein Projekt mit dem Namen **"Todolist"** mithilfe der VSIX-Projektvorlage aus, und fügen Sie der Elementvorlage ein benutzerdefiniertes Tool-Fenster, der mit dem Namen **TodoWindow**.  
  
    > [!NOTE]
    > Weitere Informationen zu eine Erweiterung mit einem Toolfenster erstellen, finden Sie unter [erstellen eine Erweiterung mit einem Toolfenster](../extensibility/creating-an-extension-with-a-tool-window.md).  
  
## <a name="set-up-the-tool-window"></a>Richten Sie das Toolfenster  
 Fügen Sie ein Textfeld, geben Sie ein neues ToDo-Element, eine Schaltfläche, um das neue Element zur Liste hinzuzufügen, und ein ListBox-Element zum Anzeigen von Elementen in der Liste hinzu.  
  
1. Löschen Sie die Schaltfläche "," ein, und "StackPanel-Steuerelemente in TodoWindow.xaml von der UserControl.  
  
    > [!NOTE]
    > Dies wird nicht gelöscht. die **button1_Click** Ereignishandler, die Sie in einem späteren Schritt wiederverwendet.  
  
2. Von der **alle WPF-Steuerelemente** Teil der **Toolbox**, ziehen Sie eine **Canvas** Steuerelement zum Raster.  
  
3. Ziehen Sie eine **Textfeld**, **Schaltfläche**, und ein **ListBox** auf den Zeichenbereich. Ordnen Sie die Elemente so an, dass das Textfeld und die Schaltfläche auf der gleichen Ebene befinden und das Listenfeld den Rest des Fensters unter ihnen, wie in der folgenden Abbildung füllt.  
  
     ![Beendet die Toolfenster](../extensibility/media/t5-toolwindow.png "T5-Toolfenster")  
  
4. Klicken Sie im Bereich "XAML" die Schaltfläche "Suchen", und legen Sie deren Content-Eigenschaft auf **hinzufügen**. Verbinden Sie den Ereignishandler der Schaltfläche auf das Schaltflächen-Steuerelement durch Hinzufügen einer `Click="button1_Click"` Attribut. Der Canvas-Block sollte wie folgt aussehen:  
  
    ```xml  
    <Canvas HorizontalAlignment="Left" Width="306">  
        <TextBox x:Name="textBox" HorizontalAlignment="Left" Height="23" Margin="10,10,0,0" TextWrapping="Wrap" Text="TextBox" VerticalAlignment="Top" Width="208"/>  
            <Button x:Name="button" Content="Add" HorizontalAlignment="Left" Margin="236,13,0,0" VerticalAlignment="Top" Width="48" Click="button1_Click"/>  
            <ListBox x:Name="listBox" HorizontalAlignment="Left" Height="222" Margin="10,56,0,0" VerticalAlignment="Top" Width="274"/>  
    </Canvas>  
    ```  
  
#### <a name="customize-the-constructor"></a>Anpassen des-Konstruktors  
  
1. Fügen Sie in der Datei TodoWindowControl.xaml.cs die folgenden using-Anweisung:  
  
    ```csharp  
    using System;  
    ```  
  
2. Fügen Sie einen öffentlichen Verweis auf die TodoWindow und die TodoWindowControl Konstruktor einen TodoWindow-Parameter akzeptieren. Der Code sollte wie folgt aussehen:  
  
    ```csharp  
    public TodoWindow parent;  
  
    public TodoWindowControl(TodoWindow window)  
    {  
        InitializeComponent();  
        parent = window;  
    }  
    ```  
  
3. Ändern Sie im TodoWindow.cs TodoWindowControl Konstruktor auf, um den TodoWindow-Parameter enthalten. Der Code sollte wie folgt aussehen:  
  
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
 Sie können angeben, dass eine Seite in der **Optionen** Dialogfeld, sodass Benutzer die Einstellungen für das Toolfenster ändern können. Erstellen einer Optionsseite erfordert eine Klasse, die die Optionen und einen Eintrag in der Datei TodoListPackage.cs oder TodoListPackage.vb beschreibt.  
  
1. Fügen Sie eine Klasse, die mit dem Namen `ToolsOptions.cs`. Legen Sie die ToolsOptions-Klasse, die von erben <xref:Microsoft.VisualStudio.Shell.DialogPage>.  
  
   ```csharp  
   class ToolsOptions : DialogPage  
   {  
   }  
   ```  
  
2. Fügen Sie die folgenden using-Anweisung:  
  
   ```csharp  
   using Microsoft.VisualStudio.Shell;  
   ```  
  
3. Die Seite "Optionen" in dieser exemplarischen Vorgehensweise stellt nur eine Option, die mit dem Namen DaysAhead bereit. Fügen Sie ein privates Feld namens **DaysAhead** und eine Eigenschaft mit dem Namen **DaysAhead** der ToolsOptions-Klasse:  
  
   ```csharp  
   private double daysAhead;  
  
   public double DaysAhead  
   {  
       get { return daysAhead; }  
       set { daysAhead = value; }  
   }  
   ```  
  
   Nachdem Sie das Projekt auf die Optionsseite aufmerksam machen müssen.  
  
#### <a name="make-the-options-page-available-to-users"></a>Die Seite "Optionen" für Benutzer verfügbar machen  
  
1. Fügen Sie in TodoWindowPackage.cs, eine <xref:Microsoft.VisualStudio.Shell.ProvideOptionPageAttribute> der TodoWindowPackage-Klasse:  
  
    ```csharp  
    [ProvideOptionPage(typeof(ToolsOptions), "ToDo", "General", 101, 106, true)]  
    ```  
  
2. Der erste Parameter an den Konstruktor ProvideOptionPage ist der Typ der Klasse ToolsOptions, die Sie zuvor erstellt haben. Der zweite Parameter, "ToDo", ist der Name der Kategorie an, in der **Optionen** Dialogfeld. Der dritte Parameter, "Allgemein", ist der Name der Unterkategorie der **Optionen** Dialogfeld, in dem die Seite "Optionen" verfügbar sein wird. Die nächsten beiden Parameter sind die Ressourcen-IDs für Zeichenfolgen. die erste ist der Name der Kategorie, und die zweite ist der Name der Unterkategorie. Der letzte Parameter bestimmt, ob diese Seite zugegriffen werden kann, mithilfe der Automatisierung.  
  
     Wenn ein Benutzer auf Ihrer Seite "Optionen" geöffnet wird, sollten sie in der folgende Abbildung ähneln.  
  
     ![Seite "Optionen"](../extensibility/media/t5optionspage.gif "T5OptionsPage")  
  
     Beachten Sie, dass die Kategorie **ToDo** und die Unterkategorie **allgemeine**.  
  
## <a name="make-data-available-to-the-properties-window"></a>Verfügbarmachen von Daten für das Fenster "Eigenschaften"  
 Sie können zum Auflisten von Informationen verfügbar machen, erstellen Sie eine Klasse namens TodoItem, die Informationen zu den einzelnen Elementen in der ToDo-Liste speichert.  
  
1. Fügen Sie eine Klasse, die mit dem Namen `TodoItem.cs`.  
  
     Wenn das Toolfenster für Benutzer verfügbar ist, werden die Elemente im Listenfeld durch TodoItems dargestellt werden. Wenn der Benutzer eines dieser Elemente im Listenfeld wählt die **Eigenschaften** Fenster werden Informationen zum Element angezeigt.  
  
     Daten in zur Verfügung stellen die **Eigenschaften** Fenster aktivieren Sie die Daten in der öffentlichen Eigenschaften, die zwei spezielle Attribute, `Description` und `Category`. `Description` ist der Text, der am unteren Rand angezeigt wird. die **Eigenschaften** Fenster. `Category` Bestimmt, in dem die Eigenschaft angezeigt werden sollte die **Eigenschaften** Fenster wird angezeigt, der **nach Kategorien** anzeigen. In der folgenden Abbildung ist die **Eigenschaften** Fenster befindet sich im **nach Kategorien** anzeigen, die **Namen** -Eigenschaft in der **ToDo Fields** Kategorie ausgewählt, und die Beschreibung der **Namen** Eigenschaft wird am unteren Rand des Fensters angezeigt.  
  
     ![Fenster "Eigenschaften"](../extensibility/media/t5properties.png "T5Properties")  
  
2. Fügen Sie die folgenden using-Anweisungen die TodoItem.cs-Datei.  
  
    ```csharp  
    using System.ComponentModel;  
    using System.Windows.Forms;  
    using Microsoft.VisualStudio.Shell.Interop;  
    ```  
  
3. Hinzufügen der `public` Zugriffsmodifizierer der Klassendeklaration.  
  
    ```csharp  
    public class TodoItem  
    {  
    }  
    ```  
  
     Fügen Sie die beiden Eigenschaften, Namen und die DueDate hinzu. Die UpdateList() und CheckForErrors() machen später wir.  
  
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
  
4. Fügen Sie einen privaten Verweis auf das Benutzersteuerelement hinzu. Fügen Sie einen Konstruktor, der das Benutzersteuerelement und den Namen für dieses Aufgabenelement hinzu. Um den Wert für DaysAhead zu suchen, ruft er die Optionen-Seite-Eigenschaft ab.  
  
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
  
5. Da Instanzen der `TodoItem` Klasse gespeichert werden soll, im Listenfeld aus, und rufen Sie das Listenfeld wird die `ToString` -Funktion, die Sie überladen müssen die `ToString` Funktion. Fügen Sie den folgenden Code zum TodoItem.cs, nach dem Konstruktor und vor dem Ende der Klasse.  
  
    ```csharp  
    public override string ToString()  
    {  
        return name + " Due: " + dueDate.ToShortDateString();  
    }  
    ```  
  
6. Fügen Sie in TodoWindowControl.xaml.cs, Stubmethoden zur TodoWindowControl-Klasse für den `CheckForError` und `UpdateList` Methoden. Fügen Sie sie nach der ProcessDialogChar und vor dem Ende der Datei.  
  
    ```csharp  
    public void CheckForErrors()  
    {  
    }  
    public void UpdateList(TodoItem item)  
    {  
    }  
    ```  
  
     Die `CheckForError` Methodenaufruf wird eine Methode, die im übergeordneten Objekt den gleichen Namen hat, und diese Methode überprüft, ob Fehler aufgetreten sind und ordnungsgemäß behandeln. Die `UpdateList` Methode aktualisiert das Listenfeld im übergeordneten Steuerelement, das die Methode wird aufgerufen, wenn die `Name` und `DueDate` Eigenschaften in dieser Klasse ändern. Sie werden später implementiert werden.  
  
## <a name="integrate-into-the-properties-window"></a>Integrieren Sie in das Fenster "Eigenschaften"  
 Jetzt schreiben Sie Code, das Listenfeld verwaltet, die an gebunden werden, wird die **Eigenschaften** Fenster.  
  
 Müssen Sie die Schaltfläche ändern click-Ereignishandler, lesen das Textfeld ein, erstellen ein Aufgabenelement und fügt es dem Listenfeld hinzu.  
  
1. Ersetzen Sie die vorhandene `button1_Click` -Funktion mit Code, der erstellt eines neuen TodoItem ein, und fügt es dem Listenfeld hinzu. Er ruft TrackSelection(), die später definiert werden.  
  
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
  
2. Wählen Sie in der Entwurfsansicht das ListBox-Steuerelement. In der **Eigenschaften** klicken Sie im Fenster der **Ereignishandler** Schaltfläche, und suchen Sie das SelectionChanged-Ereignis. Geben Sie in das Textfeld mit **ListBox_SelectionChanged**. Dadurch wird ein Stub für einen SelectionChanged-Handler hinzugefügt, und weist sie auf das Ereignis.  
  
3. Implementieren Sie die TrackSelection()-Methode. Da Sie zum Abrufen müssen die <xref:Microsoft.VisualStudio.Shell.Interop.SVsUIShell> <xref:Microsoft.VisualStudio.Shell.Interop.STrackSelection> Dienste, die Sie vornehmen müssen die <xref:Microsoft.VisualStudio.Shell.WindowPane.GetService%2A> der TodoWindowControl zugreifen können. Fügen Sie der TodoWindow-Klasse die folgende Methode hinzu:  
  
    ```  
    internal object GetVsService(Type service)  
    {  
        return GetService(service);  
    }  
    ```  
  
4. Fügen Sie die folgenden using-Anweisungen TodoWindowControl.xaml.cs:  
  
    ```csharp  
    using System.Runtime.InteropServices;  
    using Microsoft.VisualStudio.Shell.Interop;  
    using Microsoft.VisualStudio;  
    using Microsoft.VisualStudio.Shell;  
    ```  
  
5. Füllen Sie das SelectionChanged-Ereignishandler wie folgt aus:  
  
    ```  
    private void listBox_SelectionChanged(object sender, SelectionChangedEventArgs e)  
    {  
        TrackSelection();  
    }  
    ```  
  
6. Geben Sie nun die Funktion überschrieben, die Integration in bereitstellen, wird die **Eigenschaften** Fenster. Diese Funktion wird aufgerufen, wenn der Benutzer ein Element an das ListBox fügt oder ein Element im Listenfeld klickt. Sie fügt den Inhalt des ListBox-Elements ein SelectionContainer hinzu, und übergibt die SelectionContainer auf die **Eigenschaften** Fensters <xref:Microsoft.VisualStudio.Shell.Interop.ITrackSelection.OnSelectChange%2A> -Ereignishandler. Der Dienst überschrieben verfolgt die ausgewählten Objekte in der Benutzeroberfläche (UI) und zeigt ihre Eigenschaften  
  
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
  
     Nun, da eine Klasse, die die **Eigenschaften** Fenster verwenden kann, können Sie integrieren die **Eigenschaften** Fenster mit dem Toolfenster. Klickt der Benutzer ein Element im Listenfeld im Toolfenster, die **Eigenschaften** Fenster entsprechend aktualisiert werden soll. Auf ähnliche Weise, wenn der Benutzer ändert ein ToDo-Element in der **Eigenschaften** Fenster, das zugeordnete Element aktualisiert werden soll.  
  
7. Fügen Sie nun den Rest des Funktionscodes UpdateList in TodoWindowControl.xaml.cs hinzu. Es sollte löschen und erneut die geänderte TodoItem hinzufügen, aus dem Listenfeld.  
  
    ```csharp  
    public void UpdateList(TodoItem item)  
    {  
        var index = listBox.SelectedIndex;  
        listBox.Items.RemoveAt(index);  
        listBox.Items.Insert(index, item);  
        listBox.SelectedItem = index;  
    }  
    ```  
  
8. Testen Sie Ihres Codes. Erstellen Sie das Projekt, und starten Sie das Debugging. Die experimentelle Instanz sollten angezeigt werden.  
  
9. Öffnen der **Extras / Optionen** Seiten. Die Kategorie "ToDo" im linken Bereich sollte angezeigt werden. Kategorien sind in alphabetischer aufgelistet wird, suchen Sie also in der Ts.  
  
10. Klicken Sie auf der Seite "Todo" sollte die DaysAhead-Eigenschaft auf festgelegt **0**. Ändern Sie ihn in **2**.  
  
11. In der Ansicht / Other Windows Startmenü **TodoWindow**. Typ **"EndDate"** in das Textfeld und klicken Sie auf **hinzufügen**.  
  
12. Im Listenfeld sehen Sie ein Datum zwei Tage später als heute.  
  
## <a name="add-text-to-the-output-window-and-items-to-the-task-list"></a>Hinzufügen von Text in das Fenster "Ausgabe" und die Elemente in der Aufgabenliste  
 Für die **Aufgabenliste**, Sie erstellen ein neues Objekt des Typs Task, und fügen Sie dann das Task-Objekt, mit der **Aufgabenliste** durch Aufrufen der-Methode hinzufügen. Zum Schreiben in die **Ausgabe** , rufen Sie dessen GetPane-Methode, um ein Objekt im Bereich zu erhalten, und klicken Sie dann rufen Sie die OutputString-Methode des Objekts im Bereich.  
  
1. In TodoWindowControl.xaml.cs in der `button1_Click` -Methode, fügen Sie Code zum Abrufen der **allgemeine** im Bereich der **Ausgabe** Fenster (der Standardwert ist), und in ihn schreiben. Die Methode sollte wie folgt aussehen:  
  
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
  
2. Um die Elemente der Aufgabenliste hinzugefügt haben, müssen Sie eine der TodoWindowControl-Klasse eine geschachtelte Klasse hinzu. Die geschachtelte Klasse muss für die Ableitung <xref:Microsoft.VisualStudio.Shell.TaskProvider>. Fügen Sie den folgenden Code am Ende der TodoWindowControl-Klasse.  
  
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
  
3. Als Nächstes fügen Sie einen privaten Verweis auf TodoTaskProvider und eine CreateProvider()-Methode der TodoWindowControl Klasse hinzu. Der Code sollte wie folgt aussehen:  
  
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
  
4. Fügen Sie ClearError(), dabei werden der Aufgabenliste gelöscht, und ReportError(), die einen Eintrag zur Aufgabenliste hinzufügt, auf die TodoWindowControl-Klasse an.  
  
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
  
5. Implementieren Sie jetzt die CheckForErrors-Methode, wie folgt an.  
  
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
  
1. Erstellen Sie das Projekt, und starten Sie das Debugging. Die experimentelle Instanz angezeigt wird.  
  
2. Öffnen Sie die TodoWindow (**anzeigen / andere Windows / TodoWindow**).  
  
3. Geben Sie etwas in das Textfeld, und klicken Sie dann auf **hinzufügen**.  
  
     Ein Fälligkeitsdatum 2 Tage nach der heute in das Listenfeld hinzugefügt wird. Es werden keine Fehler generiert, und die **Aufgabenliste** (**anzeigen / Task Liste**) sollten keine Einträge besitzen.  
  
4. Nun ändern Sie die Einstellung für die **Extras / Optionen / ToDo** Seite **2** an **0**.  
  
5. Geben Sie einen anderen in der **TodoWindow** , und klicken Sie dann auf **hinzufügen** erneut aus. Dies löst einen Fehler sowie einen Eintrag in der **Aufgabenliste**.  
  
     Wenn Sie Elemente hinzufügen, wird das ursprüngliche Datum jetzt zuzüglich 2 Tage festgelegt.  
  
6. Auf der **anzeigen** Menü klicken Sie auf **Ausgabe** zum Öffnen der **Ausgabe** Fenster.  
  
     Beachten Sie, dass jedes Mal, dass ein Element hinzufügen, wird eine Meldung angezeigt, der **Aufgabenliste** Bereich.  
  
7. Klicken Sie auf eines der Elemente im Listenfeld.  
  
     Die **Eigenschaften** Fenster werden die beiden Eigenschaften für das Element angezeigt.  
  
8. Ändern Sie eine der Eigenschaften, und drücken Sie dann die EINGABETASTE.  
  
     Das Element wird im Listenfeld aktualisiert.
