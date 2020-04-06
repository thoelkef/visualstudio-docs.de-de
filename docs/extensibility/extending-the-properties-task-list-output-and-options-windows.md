---
title: Erweitern der Eigenschaften, Aufgabenliste, Ausgabe, Optionen Fenster
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- properties pane
- task list
- output window
- properties window
- tutorials
- tool windows
ms.assetid: 06990510-5424-44b8-9fd9-6481acec5c76
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: db14068c97ff6868f5fb73c9ddd790020e99e7c8
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/06/2020
ms.locfileid: "80711633"
---
# <a name="extend-the-properties-task-list-output-and-options-windows"></a>Erweitern der Fenster Eigenschaften, Aufgabenliste, Ausgabe und Optionen
Sie können auf jedes Toolfenster in Visual Studio zugreifen. In dieser exemplarischen Vorgehensweise wird gezeigt, wie Sie Informationen über Ihr Toolfenster in eine neue **Optionsseite** und eine neue Einstellung auf der Seite **Eigenschaften** integrieren und auch in die **Aufgabenliste** und die **Ausgabefenster** schreiben.

## <a name="prerequisites"></a>Voraussetzungen
 Ab Visual Studio 2015 installieren Sie das Visual Studio SDK nicht aus dem Downloadcenter. Es ist als optionale Funktion in Visual Studio-Setup enthalten. Sie können das VS SDK auch später installieren. Weitere Informationen finden Sie unter [Installieren des Visual Studio SDK](../extensibility/installing-the-visual-studio-sdk.md).

## <a name="create-an-extension-with-a-tool-window"></a>Erstellen einer Erweiterung mit einem Werkzeugfenster

1. Erstellen Sie ein Projekt mit dem Namen **TodoList** mithilfe der VSIX-Vorlage, und fügen Sie eine benutzerdefinierte Vorlagenvorlage für das Toolfenster mit dem Namen **TodoWindow**hinzu.

    > [!NOTE]
    > Weitere Informationen zum Erstellen einer Erweiterung mit einem Toolfenster finden Sie unter [Erstellen einer Erweiterung mit einem Toolfenster](../extensibility/creating-an-extension-with-a-tool-window.md).

## <a name="set-up-the-tool-window"></a>Einrichten des Werkzeugfensters
 Fügen Sie eine TextBox hinzu, in die Sie ein neues ToDo-Element eingeben möchten, eine Schaltfläche, um das neue Element zur Liste hinzuzufügen, und eine ListBox, um die Elemente in der Liste anzuzeigen.

1. Löschen Sie in *TodoWindow.xaml*die Steuerelemente Button, TextBox und StackPanel aus dem UserControl.

    > [!NOTE]
    > Dadurch wird der **button1_Click** Ereignishandler nicht gelöscht, den Sie in einem späteren Schritt wiederverwenden.

2. Ziehen Sie im Abschnitt **Alle WPF-Steuerelemente** der **Toolbox**ein **Canvas-Steuerelement** in das Raster.

3. Ziehen Sie eine **TextBox**, eine **Schaltfläche**und eine **ListBox** in den Canvas-Bereich. Ordnen Sie die Elemente so an, dass sich die TextBox und die Schaltfläche auf derselben Ebene befinden, und das ListBox füllt den Rest des Fensters darunter aus, wie in der Abbildung unten.

     ![Fertig gestelltes Toolfenster](../extensibility/media/t5-toolwindow.png "T5-ToolFenster")

4. Suchen Sie im XAML-Bereich die Schaltfläche, und legen Sie die Content-Eigenschaft auf **Hinzufügen**fest. Verbinden Sie den Button-Ereignishandler erneut `Click="button1_Click"` mit dem Button-Steuerelement, indem Sie ein Attribut hinzufügen. Der Canvas-Block sollte wie folgt aussehen:

    ```xml
    <Canvas HorizontalAlignment="Left" Width="306">
        <TextBox x:Name="textBox" HorizontalAlignment="Left" Height="23" Margin="10,10,0,0" TextWrapping="Wrap" Text="TextBox" VerticalAlignment="Top" Width="208"/>
            <Button x:Name="button" Content="Add" HorizontalAlignment="Left" Margin="236,13,0,0" VerticalAlignment="Top" Width="48" Click="button1_Click"/>
            <ListBox x:Name="listBox" HorizontalAlignment="Left" Height="222" Margin="10,56,0,0" VerticalAlignment="Top" Width="274"/>
    </Canvas>
    ```

### <a name="customize-the-constructor"></a>Anpassen des Konstruktors

1. Fügen Sie in der *Datei TodoWindowControl.xaml.cs* die folgende Mitdirektive hinzu:

    ```csharp
    using System;
    ```

2. Fügen Sie dem TodoWindow einen öffentlichen Verweis hinzu, und lassen Sie den TodoWindowControl-Konstruktor einen TodoWindow-Parameter verwenden. Der Code sollte wie folgt aussehen:

    ```csharp
    public TodoWindow parent;

    public TodoWindowControl(TodoWindow window)
    {
        InitializeComponent();
        parent = window;
    }
    ```

3. Ändern Sie in *TodoWindow.cs*den TodoWindowControl-Konstruktor, um den TodoWindow-Parameter einzuschließen. Der Code sollte wie folgt aussehen:

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
 Sie können eine Seite im Dialogfeld **Optionen** bereitstellen, damit Benutzer die Einstellungen für das Toolfenster ändern können. Das Erstellen einer Optionsseite erfordert sowohl eine Klasse, die die Optionen beschreibt, als auch einen Eintrag in der *Datei TodoListPackage.cs* oder *TodoListPackage.vb.*

1. Fügen Sie eine Klasse namens `ToolsOptions.cs`hinzu. Lassen `ToolsOptions` Sie die Klasse <xref:Microsoft.VisualStudio.Shell.DialogPage>von erben.

   ```csharp
   class ToolsOptions : DialogPage
   {
   }
   ```

2. Fügen Sie Folgendes mithilfe einer Direktive hinzu:

   ```csharp
   using Microsoft.VisualStudio.Shell;
   ```

3. Die Seite Optionen in dieser exemplarischen Vorgehensweise bietet nur eine Option mit dem Namen DaysAhead. Fügen Sie der `ToolsOptions` Klasse ein privates Feld mit dem Namen **daysAhead** und eine Eigenschaft mit dem Namen **DaysAhead** hinzu:

   ```csharp
   private double daysAhead;

   public double DaysAhead
   {
       get { return daysAhead; }
       set { daysAhead = value; }
   }
   ```

   Jetzt müssen Sie das Projekt auf diese Optionsseite aufmerksam machen.

### <a name="make-the-options-page-available-to-users"></a>Die Seite Optionen für Benutzer verfügbar machen

1. Fügen *Sie*in <xref:Microsoft.VisualStudio.Shell.ProvideOptionPageAttribute> `TodoWindowPackage` TodoWindowPackage.cs der Klasse eine hinzu:

    ```csharp
    [ProvideOptionPage(typeof(ToolsOptions), "ToDo", "General", 101, 106, true)]
    ```

2. Der erste Parameter für den ProvideOptionPage-Konstruktor `ToolsOptions`ist der Typ der Klasse , die Sie zuvor erstellt haben. Der zweite Parameter, "ToDo", ist der Name der Kategorie im Dialogfeld **Optionen.** Der dritte Parameter, "Allgemein", ist der Name der Unterkategorie des Dialogfelds **Optionen,** in dem die Seite Optionen verfügbar sein wird. Die nächsten beiden Parameter sind Ressourcen-IDs für Zeichenfolgen. die erste ist der Name der Kategorie, und die zweite ist der Name der Unterkategorie. Der letzte Parameter bestimmt, ob mithilfe der Automatisierung auf diese Seite zugegriffen werden kann.

     Wenn ein Benutzer die Seite "Optionen" öffnet, sollte sie dem folgenden Bild ähneln.

     ![Optionsseite](../extensibility/media/t5optionspage.gif "T5OptionsPage")

     Beachten Sie die Kategorie **ToDo** und die Unterkategorie **Allgemein**.

## <a name="make-data-available-to-the-properties-window"></a>Daten für das Eigenschaftenfenster verfügbar machen
 Sie können ToDo-Listeninformationen verfügbar machen, indem Sie eine Klasse mit dem Namen `TodoItem` erstellen, die Informationen zu den einzelnen Elementen in der Aufgabenliste speichert.

1. Fügen Sie eine Klasse namens `TodoItem.cs`hinzu.

     Wenn das Toolfenster für Benutzer verfügbar ist, werden die Elemente in der ListBox durch TodoItems dargestellt. Wenn der Benutzer eines dieser Elemente im ListBox auswählt, werden im **Fenster Eigenschaften** Informationen zum Element angezeigt.

     Um Daten im **Eigenschaftenfenster** verfügbar zu machen, wandeln Sie die Daten `Description` `Category`in öffentliche Eigenschaften mit zwei speziellen Attributen um, und . `Description`ist der Text, der am unteren Rand des **Eigenschaftenfensters** angezeigt wird. `Category`bestimmt, wo die Eigenschaft angezeigt werden soll, wenn das **Eigenschaftenfenster** in der **kategorisierten** Ansicht angezeigt wird. In der folgenden Abbildung befindet sich das **Eigenschaftenfenster** in der **kategorisierten** Ansicht, die **Name-Eigenschaft** in der Kategorie **ToDo-Felder** ist ausgewählt, und die Beschreibung der **Name-Eigenschaft** wird am unteren Rand des Fensters angezeigt.

     ![Eigenschaftenfenster](../extensibility/media/t5properties.png "T5Eigenschaften")

2. Fügen Sie die folgenden Anweisungen mithilfe von Direktiven *hinzu, die TodoItem.cs* Datei.

    ```csharp
    using System.ComponentModel;
    using System.Windows.Forms;
    using Microsoft.VisualStudio.Shell.Interop;
    ```

3. Fügen `public` Sie der Klassendeklaration den Zugriffsmodifizierer hinzu.

    ```csharp
    public class TodoItem
    {
    }
    ```

     Fügen Sie die `Name` `DueDate`beiden Eigenschaften hinzu, und . Wir werden die `UpdateList()` `CheckForErrors()` und später tun.

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

4. Fügen Sie dem Benutzersteuerelement einen privaten Verweis hinzu. Fügen Sie einen Konstruktor hinzu, der das Benutzersteuerelement und den Namen für dieses ToDo-Element übernimmt. Um den Wert `daysAhead`für zu finden, ruft er die Optionsseiteneigenschaft ab.

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

5. Da Instanzen `TodoItem` der Klasse in der ListBox gespeichert werden `ToString` und die ListBox `ToString` die Funktion aufruft, müssen Sie die Funktion überladen. Fügen Sie den folgenden Code *zu TodoItem.cs*hinzu, nach dem Konstruktor und vor dem Ende der Klasse.

    ```csharp
    public override string ToString()
    {
        return name + " Due: " + dueDate.ToShortDateString();
    }
    ```

6. In *TodoWindowControl.xaml.cs*fügen Sie `TodoWindowControl` der Klasse `CheckForError` `UpdateList` für die und-Methoden Stubmethoden hinzu. Setzen Sie sie nach dem ProcessDialogChar und vor dem Ende der Datei.

    ```csharp
    public void CheckForErrors()
    {
    }
    public void UpdateList(TodoItem item)
    {
    }
    ```

     Die `CheckForError` Methode ruft eine Methode auf, die denselben Namen im übergeordneten Objekt hat, und diese Methode überprüft, ob Fehler aufgetreten sind, und behandelt sie ordnungsgemäß. Die `UpdateList` Methode aktualisiert die ListBox im übergeordneten Steuerelement. Die Methode wird `Name` aufgerufen, wenn sich die und-Eigenschaften `DueDate` in dieser Klasse ändern. Sie werden später umgesetzt.

## <a name="integrate-into-the-properties-window"></a>Integrieren in das Eigenschaftenfenster
 Schreiben Sie nun den Code, der die ListBox verwaltet, die an das **Eigenschaftenfenster** gebunden wird.

 Sie müssen den Schaltflächenklickhandler ändern, um die TextBox zu lesen, ein TodoItem zu erstellen und es der ListBox hinzu.

1. Ersetzen Sie `button1_Click` die vorhandene Funktion durch Code, der ein neues TodoItem erstellt und der ListBox hinzufügt. Es `TrackSelection()`ruft , die später definiert werden.

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

2. Wählen Sie in der Entwurfsansicht das ListBox-Steuerelement aus. Klicken Sie im **Eigenschaftenfenster** auf die Schaltfläche **Ereignishandler,** und suchen Sie das **SelectionChanged-Ereignis.** Füllen Sie das Textfeld mit **listBox_SelectionChanged**aus. Dadurch wird ein Stub für einen SelectionChanged-Handler hinzugefügt und dem Ereignis zugewiesen.

3. Implementieren Sie die `TrackSelection()`-Methode. Da Sie die <xref:Microsoft.VisualStudio.Shell.Interop.SVsUIShell> <xref:Microsoft.VisualStudio.Shell.Interop.STrackSelection> Dienste erhalten müssen, <xref:Microsoft.VisualStudio.Shell.WindowPane.GetService%2A> müssen Sie die mit dem TodoWindowControl zugänglich machen. Fügen Sie der `TodoWindow`-Klasse die folgende Methode hinzu:

    ```
    internal object GetVsService(Type service)
    {
        return GetService(service);
    }
    ```

4. Fügen Sie *TodoWindowControl.xaml.cs*Folgendes mithilfe von Direktiven hinzu:

    ```csharp
    using System.Runtime.InteropServices;
    using Microsoft.VisualStudio.Shell.Interop;
    using Microsoft.VisualStudio;
    using Microsoft.VisualStudio.Shell;
    ```

5. Füllen Sie den SelectionChanged-Handler wie folgt aus:

    ```
    private void listBox_SelectionChanged(object sender, SelectionChangedEventArgs e)
    {
        TrackSelection();
    }
    ```

6. Geben Sie nun die Funktion TrackSelection aus, die die Integration in das **Eigenschaftenfenster** bietet. Diese Funktion wird aufgerufen, wenn der Benutzer ein Element zur ListBox hinzufügt oder auf ein Element in der ListBox klickt. Es fügt den Inhalt der ListBox zu einem SelectionContainer hinzu und <xref:Microsoft.VisualStudio.Shell.Interop.ITrackSelection.OnSelectChange%2A> übergibt den SelectionContainer an den Ereignishandler des **Eigenschaftenfensters.** Der TrackSelection-Dienst verfolgt ausgewählte Objekte in der Benutzeroberfläche und zeigt deren Eigenschaften an.

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

     Da Sie nun über eine Klasse verfügen, die das **Eigenschaftenfenster** verwenden kann, können Sie das **Eigenschaftenfenster** in das Werkzeugfenster integrieren. Wenn der Benutzer im Toolfenster auf ein Element in der ListBox klickt, sollte das **Eigenschaftenfenster** entsprechend aktualisiert werden. Wenn der Benutzer ein ToDo-Element im **Eigenschaftenfenster** ändert, sollte das zugeordnete Element ebenfalls aktualisiert werden.

7. Fügen Sie nun den Rest des UpdateList-Funktionscodes in *TodoWindowControl.xaml.cs hinzu.* Es sollte das geänderte TodoItem aus der ListBox löschen und erneut hinzufügen.

    ```csharp
    public void UpdateList(TodoItem item)
    {
        var index = listBox.SelectedIndex;
        listBox.Items.RemoveAt(index);
        listBox.Items.Insert(index, item);
        listBox.SelectedItem = index;
    }
    ```

8. Testen Sie Ihren Code. Erstellen Sie das Projekt, und starten Sie das Debugging. Die experimentelle Instanz sollte angezeigt werden.

9. Öffnen Sie die Seite > **Tools-Optionen.** **Tools** Die Kategorie "ToDo" sollte im linken Bereich angezeigt werden. Kategorien sind alphabetisch aufgelistet, also schauen Sie unter ts.

10. Auf der Seite **"Umkleben"** sollte die `DaysAhead` Eigenschaft auf **0**festgelegt werden. Ändern Sie es in **2**.

11. Öffnen Sie im Menü **Ansicht / Andere Windows** **TodoWindow**. Geben Sie **EndDate** in das Textfeld ein, und klicken Sie auf **Hinzufügen**.

12. Im Listenfeld sollte ein Datum zwei Tage später als heute angezeigt werden.

## <a name="add-text-to-the-output-window-and-items-to-the-task-list"></a>Hinzufügen von Text zum Ausgabefenster und Elementen zur Aufgabenliste
 Für die **Aufgabenliste**erstellen Sie ein neues Objekt vom Typ Task und fügen `Add` dieses Taskobjekt dann der **Aufgabenliste** hinzu, indem Sie dessen Methode aufrufen. Um in das **Ausgabefenster** zu `GetPane` schreiben, rufen Sie die Methode `OutputString` auf, um ein Bereichsobjekt abzurufen, und rufen dann die Methode des Bereichsobjekts auf.

1. Fügen *Sie*in `button1_Click` TodoWindowControl.xaml.cs in der Methode Code hinzu, um den **Bereich Allgemein** des **Ausgabefensters** abzubekommen (was die Standardeinstellung ist), und schreiben Sie darauf. Die Methode sollte wie folgt aussehen:

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

2. Um Elemente zur Aufgabenliste hinzuzufügen, benötigen Sie eine, um der TodoWindowControl-Klasse eine geschachtelte Klasse hinzuzufügen. Die verschachtelte Klasse muss <xref:Microsoft.VisualStudio.Shell.TaskProvider>von ableiten. Fügen Sie den folgenden Code `TodoWindowControl` am Ende der Klasse hinzu.

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

3. Fügen Sie als `TodoTaskProvider` Nächstes `CreateProvider()` einen privaten `TodoWindowControl` Verweis auf und eine Methode zur Klasse hinzu. Der Code sollte wie folgt aussehen:

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

4. Fügen `ClearError()`Sie hinzu , wodurch `ReportError()`die Aufgabenliste und der , `TodoWindowControl` der der Aufgabenliste einen Eintrag hinzufügt, zur Klasse werden.

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

5. Implementieren Sie `CheckForErrors` nun die Methode wie folgt.

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

## <a name="try-it-out"></a>Ausprobieren

1. Erstellen Sie das Projekt, und starten Sie das Debugging. Die experimentelle Instanz wird angezeigt.

2. Öffnen Sie das **TodoWindow** (**Andere** > Windows**TodoWindow****Other Windows** > anzeigen ).

3. Geben Sie etwas in das Textfeld ein, und klicken Sie dann auf **Hinzufügen**.

     Ein Fälligkeitsdatum 2 Tage nach heute wird dem Listenfeld hinzugefügt. Es werden keine Fehler generiert, und die **Aufgabenliste** (**Aufgabenliste****anzeigen** > ) sollte keine Einträge enthalten.

4. Ändern Sie nun die Einstellung auf der Seite **Tools** > **Options** > **ToDo** von **2** zurück auf **0**.

5. Geben Sie etwas anderes in das **TodoWindow** ein, und klicken Sie dann erneut auf **Hinzufügen.** Dies löst einen Fehler und auch einen Eintrag in der **Aufgabenliste**aus.

     Beim Hinzufügen von Elementen wird das Anfangsdatum auf jetzt plus 2 Tage festgelegt.

6. Klicken Sie im Menü **Ansicht** auf **Ausgabe,** um das **Ausgabefenster** zu öffnen.

     Beachten Sie, dass jedes Mal, wenn Sie ein Element hinzufügen, eine Nachricht im Bereich **Aufgabenliste** angezeigt wird.

7. Klicken Sie auf eines der Elemente in der ListBox.

     Im **Fenster Eigenschaften** werden die beiden Eigenschaften für das Element angezeigt.

8. Ändern Sie eine der Eigenschaften, und drücken Sie dann **die Eingabetaste**.

     Das Element wird im ListBox aktualisiert.
