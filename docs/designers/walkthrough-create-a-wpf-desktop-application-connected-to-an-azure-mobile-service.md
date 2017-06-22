---
title: 'Exemplarische Vorgehensweise: Erstellen einer WPF-Desktopanwendung, die mit einem Azure Mobile Service verbunden ist | Microsoft-Dokumentation'
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- vs-ide-general
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 8d42620f-553b-4b04-a38b-f6b306d73a50
caps.latest.revision: 7
author: kempb
ms.author: kempb
manager: ghogen
translation.priority.ht:
- de-de
- es-es
- fr-fr
- it-it
- ja-jp
- ko-kr
- ru-ru
- zh-cn
- zh-tw
translation.priority.mt:
- cs-cz
- pl-pl
- pt-br
- tr-tr
ms.translationtype: Human Translation
ms.sourcegitcommit: 47057e9611b824c17077b9127f8d2f8b192d6eb8
ms.openlocfilehash: 7716a0e9249c67760ae7b31160dcae89b77b9ca7
ms.contentlocale: de-de
ms.lasthandoff: 05/13/2017

---
# <a name="walkthrough-create-a-wpf-desktop-application-connected-to-an-azure-mobile-service"></a>Exemplarische Vorgehensweise: Erstellen einer WPF-Desktopanwendung, die mit einem Azure Mobile Service verbunden ist
Mit Windows Presentation Foundation (WPF) können Sie schnell eine moderne Desktopanwendung erstellen, die zum Speichern und Bereitstellen von Daten eines Azure Mobile Service verwendet.  
  
##  <a name="Requirements"></a> Erforderliche Komponenten  
 Für diese exemplarische Vorgehensweise wird Folgendes benötigt:  
  
-   Visual Studio 2015 – beliebige Version, die die WPF-Entwicklung unterstützt.  
  
-   Ein aktives Microsoft Azure-Konto.  
  
    -   Für ein kostenloses Testkonto können Sie sich [hier](http://azure.microsoft.com/en-us/pricing/free-trial/)anmelden.  
  
    -   Sie können [Vorteile für MSDN-Abonnenten](https://azure.microsoft.com/en-us/pricing/member-offers/msdn-benefits-details/?WT.mc_id=A261C142F)aktivieren. Über Ihr MSDN-Abonnement erhalten Sie monatlich eine Gutschrift, die Sie für kostenpflichtige Azure-Dienste verwenden können.  
  
## <a name="create-a-project-and-add-references"></a>Erstellen eines neuen Projekts und Hinzufügen von Verweisen  
 Zunächst erstellen Sie ein WPF-Projekt und fügen diesem ein NuGet-Paket hinzu, über das Sie eine Verbindung mit Azure Mobile Services herstellen können.  
  
#### <a name="to-create-the-project"></a>So erstellen Sie das Projekt  
  
1.  Wählen Sie in der Menüleiste **Datei**, **Neu**, **Projekt**aus.  
  
2.  Erweitern Sie im Dialogfeld **Neues Projekt** den Knoten **Visual C#** oder **Visual Basic** , und wählen Sie den Knoten **Windows** aus. Erweitern Sie dann den Knoten **Windows** , und wählen Sie den Knoten **Klassischer Desktop** aus.  
  
3.  Wählen Sie in der Vorlagenliste die Vorlage **WPF-Anwendung** aus.  
  
4.  Erweitern Sie im Dialogfeld **Name**  `WPFQuickStart`ein, und wählen Sie dann die Schaltfläche **OK** aus.  
  
     Das Projekt wird erstellt, und die Projektdateien werden dem **Projektmappen-Explorer**hinzugefügt. Zudem wird der Designer für das Standardanwendungsfenster namens **MainWindow.xaml** angezeigt.  
  
#### <a name="to-add-a-reference-to-the-windows-azure-mobile-services-sdk"></a>So fügen Sie dem Windows Azure Mobile Services SDK einen Verweis hinzu  
  
1.  Öffnen Sie im **Projektmappen-Explorer**das Kontextmenü für den Knoten **Verweise** , und wählen Sie **NuGet-Pakete verwalten**aus.  
  
2.  Erweitern Sie im Dialogfeld **NuGet-Paket-Manager**das Feld **Suche** aus, und geben Sie `mobileservices`anmelden.  
  
3.  Wählen Sie im linken Bereich **WindowsAzure.MobileServices**aus, und wählen Sie dann im rechten Bereich die Schaltfläche **Installieren** aus.  
  
    > [!NOTE]
    >  Wenn ein Dialogfeld mit einer **Vorschau** angezeigt wird, prüfen Sie die vorgeschlagenen Änderungen, und wählen Sie dann die Schaltfläche **OK** aus.  
  
4.  Lesen Sie im Dialogfeld zum **Akzeptieren der Lizenzbedingungen** die Lizenzbedingungen, und akzeptieren Sie diese durch Klicken auf die Schaltfläche **Ich stimme den Lizenzbedingungen zu** .  
  
     Die erforderlichen Verweise werden dem **Projektmappen-Explorer**hinzugefügt.  
  
    > [!NOTE]
    >  Wenn Sie die Lizenzbedingungen nicht akzeptieren, wählen Sie die Schaltfläche **Ich stimme nicht zu** aus. In diesem Fall können Sie die exemplarische Vorgehensweise nicht fortsetzen.  
  
## <a name="create-the-user-interface"></a>Erstellen der Benutzeroberfläche  
 Im nächsten Schritt erstellen Sie die Benutzeroberfläche für die Anwendung. Zunächst erstellen Sie ein wiederverwendbares Benutzersteuerelement, das ein nebeneinander angeordnetes, in zwei Bereiche unterteiltes Standardbereichslayout anzeigt. Dann fügen Sie das Benutzersteuerelement dem Hauptanwendungsfenster hinzu, und fügen Sie Steuerelemente zum Eingeben und Anzeigen von Daten hinzu. Anschließend schreiben Sie Code, um die Interaktion mit dem Mobile Service-Backend zu definieren.  
  
#### <a name="to-add-a-user-control"></a>So fügen Sie ein Benutzersteuerelement hinzu  
  
1.  Öffnen Sie in **Projektmappen-Explorer**das Kontextmenü des Knotens **WPFQuickStart** , und wählen Sie **Hinzufügen**, **Neuer Ordner**aus.  
  
2.  Geben Sie dem Ordner den Namen `Common`anmelden.  
  
3.  Öffnen Sie das Kontextmenü des Ordners **Common** , und wählen Sie **Hinzufügen**, **Benutzersteuerelement**aus.  
  
4.  Erweitern Sie im Dialogfeld **Neues Element hinzufügen** das Feld "Name" aus, und geben Sie `QuickStartTask`ein, und wählen Sie dann die Schaltfläche **Hinzufügen** aus.  
  
     Das Benutzersteuerelement wird dem Projekt hinzugefügt, und die Datei **QuickStartTask.xaml** wird im Designer geöffnet.  
  
5.  Wählen Sie im unteren Bereich des Designers die Tags `<Grid>` und `</Grid>` aus, und ersetzen Sie sie durch folgenden XAML-Code:  
  
    ```xaml  
    <Grid VerticalAlignment="Top">  
            <StackPanel Orientation="Horizontal">  
                <Border BorderThickness="0,0,1,0" BorderBrush="DarkGray" Margin="0,10" MinWidth="70">  
                    <TextBlock Text="{Binding Number}" FontSize="45" Foreground="DarkGray" Margin="20,0"/>  
                </Border>  
                <StackPanel>  
                    <TextBlock Text="{Binding Title}" Margin="10,10,0,0" FontSize="16" FontWeight="Bold" />  
                    <TextBlock Text="{Binding Description}" Margin="10,0,0,0" TextWrapping="Wrap" MaxWidth="500" />  
                </StackPanel>  
            </StackPanel>  
        </Grid>  
    ```  
  
     Dieser XAML-Code erstellt ein wiederverwendbares Layout mit Platzhaltern für Felder für Zahlen, Titel und Beschreibungen. Zur Laufzeit können die Platzhalter durch Text ersetzt werden, wie in der folgenden Abbildung dargestellt.  
  
     ![Das Benutzersteuerelement „QuickStartTask“](../designers/media/wpfquickstart1.PNG "WPFQuickStart1")  
  
6.  Erweitern Sie in **Projektmappen-Explorer**den Knoten **QuickStartTask.xaml** , und öffnen Sie die Datei **QuickStartTask.xaml.cs** oder **QuickStartTask.xaml.vb** .  
  
7.  Ersetzen Sie im Code-Editor den `namespace WPFQuickStart.Common` -Namespace (C#) oder die `Public Class QuickStartTask` Methode (VB) durch folgenden Code:  
  
    ```c#  
    namespace WPFQuickStart.Common  
    {  
        /// <summary>  
        /// Interaction logic for QuickStartTask.xaml  
        /// </summary>  
        public partial class QuickStartTask : UserControl  
        {  
            public QuickStartTask()  
            {  
                this.InitializeComponent();  
                this.DataContext = this;  
            }  
  
            public int Number  
            {  
                get { return (int)GetValue(NumberProperty); }  
                set { SetValue(NumberProperty, value); }  
            }  
  
            // Using a DependencyProperty as the backing store for Number.  This enables animation, styling, binding, etc...  
            public static readonly DependencyProperty NumberProperty =  
                DependencyProperty.Register("Number", typeof(int), typeof(QuickStartTask), new PropertyMetadata(0));  
  
            public string Title  
            {  
                get { return (string)GetValue(TitleProperty); }  
                set { SetValue(TitleProperty, value); }  
            }  
  
            // Using a DependencyProperty as the backing store for Title.  This enables animation, styling, binding, etc...  
            public static readonly DependencyProperty TitleProperty =  
                DependencyProperty.Register("Title", typeof(string), typeof(QuickStartTask), new PropertyMetadata(default(string)));  
  
            public string Description  
            {  
                get { return (string)GetValue(DescriptionProperty); }  
                set { SetValue(DescriptionProperty, value); }  
            }  
  
            // Using a DependencyProperty as the backing store for Description.  This enables animation, styling, binding, etc...  
            public static readonly DependencyProperty DescriptionProperty =  
                DependencyProperty.Register("Description", typeof(string), typeof(QuickStartTask), new PropertyMetadata(default(string)));  
        }  
    }  
    ```  
  
    ```vb  
    Partial Public Class QuickStartTask  
            Inherits UserControl  
  
            Public Sub New()  
                Me.InitializeComponent()  
                Me.DataContext = Me  
            End Sub  
  
            Public Property Number() As Integer  
                Get  
                    Return CInt(Fix(GetValue(NumberProperty)))  
                End Get  
                Set(ByVal value As Integer)  
                    SetValue(NumberProperty, value)  
                End Set  
            End Property  
  
            ' Using a DependencyProperty as the backing store for Number.  This enables animation, styling, binding, etc...  
            Public Shared ReadOnly NumberProperty As DependencyProperty = DependencyProperty.Register("Number", GetType(Integer), GetType(QuickStartTask), New PropertyMetadata(0))  
  
            Public Property Title() As String  
                Get  
                    Return CStr(GetValue(TitleProperty))  
                End Get  
                Set(ByVal value As String)  
                    SetValue(TitleProperty, value)  
                End Set  
            End Property  
  
            ' Using a DependencyProperty as the backing store for Title.  This enables animation, styling, binding, etc...  
            Public Shared ReadOnly TitleProperty As DependencyProperty = DependencyProperty.Register("Title", GetType(String), GetType(QuickStartTask), New PropertyMetadata(Nothing))  
  
            Public Property Description() As String  
                Get  
                    Return CStr(GetValue(DescriptionProperty))  
                End Get  
                Set(ByVal value As String)  
                    SetValue(DescriptionProperty, value)  
                End Set  
            End Property  
  
            ' Using a DependencyProperty as the backing store for Description.  This enables animation, styling, binding, etc...  
            Public Shared ReadOnly DescriptionProperty As DependencyProperty = DependencyProperty.Register("Description", GetType(String), GetType(QuickStartTask), New PropertyMetadata(Nothing))  
        End Class  
    ```  
  
     Dieser Code verwendet Abhängigkeitseigenschaften, um zur Laufzeit de Werte für die Felder für Zahlen, Titel und Beschreibungen festzulegen.  
  
8.  Wählen Sie auf der Menüleiste **Erstellen**, **WPFQuickStart erstellen** aus, um das Benutzerelement zu erstellen.  
  
#### <a name="to-create-and-modify-the-main-window"></a>So erstellen und ändern Sie das Hauptfenster  
  
1.  Öffnen Sie im **Projektmappen-Explorer**die Datei **MainWindow.xaml** .  
  
2.  **Wichtig**. Dieser Schritt gilt nur für C#. Wenn Sie Visual Basic verwenden, fahren Sie mit dem nächsten Schritt fort. Navigieren Sie im unteren Bereich des Designers zur Zeile `xmlns:local="clr-namespace:WPFQuickStart"` , und ersetzen Sie sie durch folgenden XAML-Code:  
  
    ```xaml  
    xmlns:local="clr-namespace:WPFQuickStart.Common"  
    ```  
  
3.  Erweitern Sie im Dialogfeld **Eigenschaften** den Kategorieknoten **Custom** , und wählen Sie die Eigenschaft **Title** aus. Geben Sie dann `WPF Todo List` ein, und drücken Sie die **EINGABETASTE** .  
  
     Beachten Sie, dass das **Title** -Element im XAML-Fenster nun dem neuen Wert entspricht. Sie können die XAML-Eigenschaften im XAML-Fenster oder im Fenster **Eigenschaften** bearbeiten. Die Änderungen werden synchronisiert.  
  
4.  Legen Sie im XAML-Fenster den Wert des Elements **Height** auf `768`fest, und legen Sie den Wert der Eigenschaft **Width** auf `1280`anmelden.  
  
     Diese Elemente entsprechen den Eigenschaften **Height** und **Width** in der Kategorie **Layout** im Fenster **Eigenschaften** .  
  
5.  Wählen Sie die Tags `<Grid>` und `</Grid>` aus, und ersetzen Sie sie durch folgenden XAML-Code:  
  
    ```xaml  
    <Grid>  
  
            <Grid Margin="50,50,10,10">  
                <Grid.ColumnDefinitions>  
                    <ColumnDefinition Width="*" />  
                    <ColumnDefinition Width="*" />  
                </Grid.ColumnDefinitions>  
                <Grid.RowDefinitions>  
                    <RowDefinition Height="Auto" />  
                    <RowDefinition Height="*" />  
                </Grid.RowDefinitions>  
  
                <Grid Grid.Row="0" Grid.ColumnSpan="2" Margin="0,0,0,20">  
                    <StackPanel>  
                        <TextBlock Foreground="#0094ff" FontFamily="Segoe UI Light" Margin="0,0,0,6">MICROSOFT AZURE MOBILE SERVICES</TextBlock>  
                        <TextBlock Foreground="Gray" FontFamily="Segoe UI Light" FontSize="45" ><Run Text="My Todo List"/></TextBlock>  
                    </StackPanel>  
                </Grid>  
  
                <Grid Grid.Row="1">  
                    <StackPanel>  
  
                        <local:QuickStartTask Number="1" Title="Insert a TodoItem" Description="Enter some text below and click Save to insert a new todo item into the list." />  
  
                        <StackPanel Orientation="Horizontal" Margin="72,0,0,0">  
                            <TextBox x:Name="TodoInput" Margin="5" MinWidth="300"/>  
                            <Button x:Name="ButtonSave" Click="ButtonSave_Click" Content="Save"/>  
                        </StackPanel>  
  
                    </StackPanel>  
                </Grid>  
  
                <Grid Grid.Row="1" Grid.Column="1">  
                    <Grid.RowDefinitions>  
                        <RowDefinition Height="Auto" />  
                        <RowDefinition />  
                    </Grid.RowDefinitions>  
                    <StackPanel>  
                        <local:QuickStartTask Number="2" Title="Query and Update Data" Description="Click the Refresh button to load the unfinished TodoItems from the Azure Mobile Service. Select the checkbox to mark a ToDo item as complete and update the list." />  
                        <Button Margin="72,0,0,0" Name="ButtonRefresh" Click="ButtonRefresh_Click">Refresh</Button>  
                    </StackPanel>  
  
                    <ListView Name="ListItems" Margin="62,10,0,0" Grid.Row="1">  
                        <ListView.ItemTemplate>  
                            <DataTemplate>  
                                <StackPanel Orientation="Horizontal">  
                                    <CheckBox Name="CheckBoxComplete" IsChecked="{Binding Complete, Mode=TwoWay}" Checked="CheckBoxComplete_Checked" Content="{Binding Text}" Margin="10,5" VerticalAlignment="Center"/>  
                                </StackPanel>  
                            </DataTemplate>  
                        </ListView.ItemTemplate>  
                    </ListView>  
  
                </Grid>  
  
            </Grid>  
        </Grid>  
    ```  
  
     Beachten Sie, dass die Änderungen im Entwurfsfenster wiedergegeben werden. Auch in diesem Fall hätten Sie die Benutzeroberfläche durch Hinzufügen von Steuerelementen aus dem Fenster **Toolbox** und Festlegen der Eigenschaften im Fenster **Eigenschaften** definieren können. Alle Aufgaben, die Sie im Designer ausführen, können im XAML-Code und umgekehrt ausgeführt werden.  
  
     An diesem Punkt sollte das Design der folgenden Abbildung entsprechen:  
  
     ![Das MainWindow-Element im Designer](../designers/media/wpfquickstart2.PNG "WPFQuickStart2")  
  
    > [!NOTE]
    >  Bei Ausführen der nächsten Vorgehensweisen werden möglicherweise Fehler in der **Fehlerliste** angezeigt, wenn diese geöffnet ist. Diese verschwinden wieder, während Sie die verbleibenden Vorgehensweisen ausführen.  
  
6.  Erweitern Sie in **Projektmappen-Explorer**den Knoten **MainWindow.xaml** , und öffnen Sie die Datei **MainWindow.xaml.cs** oder **MainWindow.xaml.vb** .  
  
7.  Fügen Sie im Code-Editor am Anfang der Datei folgende `using` - oder `Imports` Direktive hinzu:  
  
    ```c#  
    using Microsoft.WindowsAzure.MobileServices;  
    using Newtonsoft.Json;   
    ```  
  
    ```vb  
    Imports Microsoft.WindowsAzure.MobileServices  
    Imports Newtonsoft.Json  
    ```  
  
8.  Ersetzen Sie den gesamten Code im **WPFQuickStart** -Namespace (C#) oder in der **Class MainWindow** -Klasse (VB) durch folgenden Code:  
  
    ```c#  
    namespace WPFQuickStart  
    {  
        /// <summary>  
        /// Interaction logic for MainWindow.xaml  
        /// </summary>  
        public class TodoItem  
        {  
            public string Id { get; set; }  
  
            [JsonProperty(PropertyName = "text")]  
            public string Text { get; set; }  
  
            [JsonProperty(PropertyName = "complete")]  
            public bool Complete { get; set; }  
        }  
  
        public partial class MainWindow : Window  
        {  
            private MobileServiceCollection<TodoItem, TodoItem> items;  
            private IMobileServiceTable<TodoItem> todoTable = App.MobileService.GetTable<TodoItem>();  
  
            public MainWindow()  
            {  
                InitializeComponent();  
            }  
  
            private async void InsertTodoItem(TodoItem todoItem)  
            {  
                // This code inserts a new TodoItem into the database. When the operation completes  
                // and Mobile Services has assigned an Id, the item is added to the CollectionView  
                await todoTable.InsertAsync(todoItem);  
                items.Add(todoItem);  
            }  
  
            private async void RefreshTodoItems()  
            {  
                try  
                {  
                    // This code refreshes the entries in the list view by querying the TodoItem table.  
                    // The query excludes completed TodoItems  
                    items = await todoTable  
                        .Where(todoItem => todoItem.Complete == false)  
                        .ToCollectionAsync();  
                    ListItems.ItemsSource = items;  
                }  
                catch (MobileServiceInvalidOperationException e)  
                {  
                    MessageBox.Show(e.Message, "Error loading items");  
                }  
            }  
  
            private async void UpdateCheckedTodoItem(TodoItem item)  
            {  
                // This code takes a freshly completed TodoItem and updates the database. When the MobileService   
                // responds, the item is removed from the list   
                await todoTable.UpdateAsync(item);  
                items.Remove(item);  
            }  
  
            private void ButtonRefresh_Click(object sender, RoutedEventArgs e)  
            {  
                RefreshTodoItems();  
            }  
  
            private void ButtonSave_Click(object sender, RoutedEventArgs e)  
            {  
                var todoItem = new TodoItem { Text = TodoInput.Text };  
                InsertTodoItem(todoItem);  
                TodoInput.Text = "";  
            }  
  
            private void CheckBoxComplete_Checked(object sender, RoutedEventArgs e)  
            {  
                CheckBox cb = (CheckBox)sender;  
                TodoItem item = cb.DataContext as TodoItem;  
                UpdateCheckedTodoItem(item);  
            }  
  
            protected override void OnActivated(EventArgs e)  
            {  
                RefreshTodoItems();  
            }  
        }  
  
    }  
    ```  
  
    ```vb  
    Public Class TodoItem  
        Public Property Id() As String  
  
        <JsonProperty(PropertyName:="text")>  
        Public Property Text() As String  
  
        <JsonProperty(PropertyName:="complete")>  
        Public Property Complete() As Boolean  
    End Class  
  
    Partial Public Class MainWindow  
        Inherits Window  
  
        Private items As MobileServiceCollection(Of TodoItem, TodoItem)  
        Private todoTable As IMobileServiceTable(Of TodoItem) = Application.MobileService.GetTable(Of TodoItem)()  
  
        Public Sub New()  
            InitializeComponent()  
        End Sub  
  
        Private Async Sub InsertTodoItem(ByVal todoItem As TodoItem)  
            ' This code inserts a new TodoItem into the database. When the operation completes  
            ' and Mobile Services has assigned an Id, the item is added to the CollectionView  
            Await todoTable.InsertAsync(todoItem)  
            items.Add(todoItem)  
        End Sub  
  
        Private Async Sub RefreshTodoItems()  
            Dim exception As MobileServiceInvalidOperationException = Nothing  
            Try  
                ' This code refreshes the entries in the list view by querying the TodoItem table.  
                ' The query excludes completed TodoItems  
                items = Await todoTable.Where(Function(todoItem) todoItem.Complete = False).ToCollectionAsync()  
            Catch e As MobileServiceInvalidOperationException  
                exception = e  
            End Try  
  
            If exception IsNot Nothing Then  
                MessageBox.Show(exception.Message, "Error loading items")  
            Else  
                ListItems.ItemsSource = items  
            End If  
        End Sub  
  
        Private Async Sub UpdateCheckedTodoItem(ByVal item As TodoItem)  
            ' This code takes a freshly completed TodoItem and updates the database. When the MobileService   
            ' responds, the item is removed from the list   
            Await todoTable.UpdateAsync(item)  
            items.Remove(item)  
        End Sub  
  
        Private Sub ButtonRefresh_Click(ByVal sender As Object, ByVal e As RoutedEventArgs)  
            RefreshTodoItems()  
        End Sub  
  
        Private Sub ButtonSave_Click(ByVal sender As Object, ByVal e As RoutedEventArgs)  
            Dim todoItem = New TodoItem With {.Text = TodoInput.Text}  
            InsertTodoItem(todoItem)  
            TodoInput.Text = ""  
        End Sub  
  
        Private Sub CheckBoxComplete_Checked(ByVal sender As Object, ByVal e As RoutedEventArgs)  
            Dim cb As CheckBox = DirectCast(sender, CheckBox)  
            Dim item As TodoItem = TryCast(cb.DataContext, TodoItem)  
            UpdateCheckedTodoItem(item)  
        End Sub  
  
        Protected Overrides Sub OnActivated(ByVal e As EventArgs)  
            RefreshTodoItems()  
        End Sub  
    End Class  
    ```  
  
     Dieser Code definiert die Interaktion zwischen der Benutzeroberfläche und der Datenbank im mobilen Service mithilfe asynchroner Methoden.  
  
## <a name="create-the-azure-mobile-service"></a>Erstellen eines mobilen Services in Azure  
 Im letzten Schritt erstellen Sie einen mobilen Service in Microsoft Azure. Außerdem fügen Sie eine Tabelle zum Speichern Ihrer Daten hinzu und verweisen dann von Ihrer Anwendung auf die Dienstinstanz.  
  
#### <a name="to-create-a-mobile-service"></a>So erstellen Sie einen mobilen Service  
  
1.  Öffnen Sie einen Webbrowser, und melden Sie sich bei Ihrem Microsoft Azure-Portal an. Wählen Sie dann die Registerkarte **MOBILE SERVICES** aus.  
  
2.  Wählen Sie die Schaltfläche **NEU** aus, und wählen Sie im Popupdialogfenster nacheinander **COMPUTE** (BERECHNEN), **MOBILE SERVICE, CREATE** (MOBILER SERVICE, ERSTELLEN) aus.  
  
3.  Wählen Sie im Dialogfeld **NEUER MOBILER SERVICE** das Textfeld **URL** aus, und geben Sie `wpfquickstart01` ein.  
  
    > [!NOTE]
    >  Möglicherweise müssen Sie den numerischen Teil der URL zu ändern. Microsoft Azure erfordert eine eindeutige URL für jeden mobilen Service.  
  
     Dadurch wird die URL für den Service auf *https://wpfquickstart01.azure-mobile.net/*festgelegt.  
  
4.  Wählen Sie in der Liste **DATENBANK** eine Datenbankoption aus. Da es sich dabei um eine Anwendung handelt, die nur selten verwendet wird, können Sie die Option **Create a free 20MB SQL database** (Eine kostenlose 20-MB-SQL-Datenbank erstellen) bzw. die bereits in Ihrem Abonnement enthaltene kostenlose Datenbank auswählen.  
  
5.  Wählen Sie in der Liste **REGION** das Rechenzentrum aus, in dem Sie den mobilen Service bereitstellen möchten, und wählen Sie dann **Weiter** (Pfeil nach rechts) aus.  
  
    > [!NOTE]
    >  Für diesen Service verwenden Sie die standardmäßige **BACKEND** -Einstellung, **JavaScript**.  
  
6.  Wenn Sie eine neue Datenbank erstellen, wählen Sie auf der Seite **Datenbankeinstellungen angeben** in der Liste **SERVER** die Option **Neuer SQL-Datenbankserver**aus, geben Sie Ihren **SQL-ANMELDENAMEN** und Ihr **KENNWORT**ein, und wählen Sie dann die Schaltfläche **Abgeschlossen** (Häkchen) aus.  
  
7.  Wenn Sie eine vorhandene Datenbank verwenden, geben Sie auf der Seiten **Datenbankeinstellungen** Ihr **ANMELDEKENNWORT** ein, und wählen Sie dann die Schaltfläche **Abgeschlossen** (Häkchen) aus.  
  
     Der mobile Service wird nun erstellt. Sobald der Vorgang beendet ist, ändert sich der Status in **Bereit** , und Sie können mit dem nächsten Schritt fortfahren.  
  
8.  Wählen Sie im Portal den neu erstellten mobilen Service und dann die Schaltfläche **SCHLÜSSEL VERWALTEN** aus.  
  
9. Kopieren Sie in das Fenster **Zugriffsschlüssel verwalten** den **ANWENDUNGSSCHLÜSSEL**.  
  
     Sie verwenden diesen in der nächsten Vorgehensweise.  
  
#### <a name="to-create-a-table"></a>So erstellen Sie eine Tabelle  
  
1.  Wählen Sie im Microsoft Azure-Portal den Pfeil nach rechts neben dem Namen Ihres mobilen Service aus, und wählen Sie auf der Menüleiste **DATEN**und dann den Link **EINE TABELLE HINZUFÜGEN** aus.  
  
2.  Erweitern Sie im Dialogfeld **Neue Tabelle erstellen** im Textfeld **TABELLENNAME**  `TodoItem`ein, und wählen Sie dann die Schaltfläche **Abgeschlossen** (Häkchen) aus.  
  
     Warten Sie, bis die Tabelle erstellt ist, und fahren Sie dann mit der letzten Vorgehensweise fort.  
  
#### <a name="to-add-a-declaration-for-the-mobile-service"></a>So fügen Sie eine Deklaration für den mobilen Service hinzu  
  
1.  Kehren Sie zurück zu Visual Studio. Erweitern Sie in **Projektmappen-Explorer**den Knoten **App.xaml** (C#) oder **Application.xaml** (Visual Basic), und öffnen Sie die Datei **App.xaml.cs** oder **App.xaml.vb** .  
  
2.  Fügen Sie im Code-Editor am Anfang der Datei folgende `using` - oder **Imports** -Direktive hinzu:  
  
    ```c#  
    using Microsoft.WindowsAzure.MobileServices;  
    ```  
  
    ```vb  
    Imports Microsoft.WindowsAzure.MobileServices  
    ```  
  
3.  Fügen Sie folgende Deklaration der Klasse hinzu. Dadurch wird *YOUR-SERVICE_HERE* durch den Namen der URL für Ihren Service und *YOUR-KEY-HERE* durch den Anwendungsschlüssel ersetzt, den Sie in der vorherigen Vorgehensweise kopiert haben:  
  
    ```c#  
    public static MobileServiceClient MobileService = new MobileServiceClient(  
                 "https://YOUR-SERVICE-HERE.azure-mobile.net/",  
                 "YOUR-KEY-HERE"  
             );  
    ```  
  
    ```vb  
    Public Shared MobileService As New MobileServiceClient("https://YOUR-SERVICE-HERE.azure-mobile.net/", "YOUR-KEY-HERE")  
    ```  
  
     Mithilfe dieses Codes kann die Anwendung auf den mobilen Service unter Microsoft Azure zugreifen.  
  
## <a name="test-the-application"></a>Testen der Anwendung  
 Sie haben nun eine WPF-Desktopanwendung erstellt, die auf einen mobilen Service in Azure zugreift. Nun müssen Sie die Anwendung nur noch ausführen.  
  
#### <a name="to-run-the-application"></a>So führen Sie die Anwendung aus  
  
1.  Wählen Sie auf der Menüleiste **Debuggen**, **Debugging starten** aus (oder drücken Sie F5).  
  
2.  Erweitern Sie im Dialogfeld **TodoItem einfügen**  `Do something`ein, und wählen Sie dann die Schaltfläche **Speichern** aus.  
  
3.  EINGABETASTE `Do something else`ein, und wählen Sie dann die Schaltfläche **Speichern** aus.  
  
     Die beiden Einträge werden der Liste zum **Abfragen und Aktualisieren von Daten** hinzugefügt, wie in der folgenden Abbildung dargestellt.  
  
     ![Aktivitäteneinträge werden zur Liste hinzugefügt.](../designers/media/wpfquickstart3.PNG "WPFQuickStart3")  
  
4.  Aktivieren Sie das Kontrollkästchen für den Eintrag **Do something else** in der Liste.  
  
     Dadurch wird die **UpdateCheckedTodoItem** -Methode aufgerufen, die das Element von der Liste und aus der Datenbank entfernt.  
  
## <a name="next-steps"></a>Nächste Schritte  
 Sie haben ein recht einfaches Beispiel einer WPF-Desktopanwendung mit einem Azure-Backend ausgeführt. Echte Anwendungen sind natürlich viel komplexer, aber für diese gelten einige grundlegende Konzepte. Weitere Informationen finden Sie unter [WPF in .NET Framework](https://msdn.microsoft.com/en-us/library/ms754130\(v=vs.100\).aspx).  
  
 Sie können eine Benutzeroberfläche viel ansprechender gestalten, indem Sie dieser Farben, Formen, Grafiken und Animationen hinzufügen. Informationen hierzu finden Sie unter [Designing XAML in Visual Studio and Blend for Visual Studio (Entwerfen von XAML-Code in Visual Studio und Blend für Visual Studio)](../designers/designing-xaml-in-visual-studio.md).  
  
 Sie können eine Verbindung mit vorhandenen SQL-Datenbanken oder anderen Datenquellen mit Azure Mobile Services herstellen. Weitere Informationen finden Sie unter [Mobile Services – Dokumentation](http://azure.microsoft.com/en-us/services/app-service/mobile/).  
  
## <a name="see-also"></a>Siehe auch  
 [Exemplarische Vorgehensweise: Meine erste WPF-Desktopanwendung](../designers/walkthrough-my-first-wpf-desktop-application2.md)   
 [Erstellen von modernen Desktopanwendungen mit Windows Presentation Foundation](../designers/create-modern-desktop-applications-with-windows-presentation-foundation.md)
