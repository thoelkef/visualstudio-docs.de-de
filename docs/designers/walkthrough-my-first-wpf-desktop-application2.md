---
title: "Exemplarische Vorgehensweise: Meine erste WPF-Desktopanwendung | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-general"
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: 3c460fa9-2ea1-413f-ae54-54a1f2a499d1
caps.latest.revision: 6
author: "kempb"
ms.author: "kempb"
manager: "ghogen"
caps.handback.revision: 6
---
# Exemplarische Vorgehensweise: Meine erste WPF-Desktopanwendung
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

<a name="introduction"></a> Diese exemplarische Vorgehensweise enthält eine Einführung in die Windows Presentation Foundation \(WPF\)\-Entwicklung. Sie erstellen eine Basisanwendung mit Elementen, die für die meisten WPF\-Desktopanwendung verwendet werden: XAML\-Markup, CodeBehind, Anwendungsdefinitionen, Steuerelemente, Layout, Datenbindung und Stile.  
  
##  <a name="Create_The_Application_Code_Files"></a> Erstellen des Anwendungsprojekts  
 In diesem Abschnitt erstellen Sie die Anwendungsstruktur, die das Projekt und ein Hauptfenster oder \-formular enthält.  
  
#### So erstellen Sie das Projekt  
  
1.  Wählen Sie in der Menüleiste **Datei**, **Neu**, **Projekt** aus.  
  
2.  Erweitern Sie im Dialogfeld **Neues Projekt** den Knoten **Visual C\#** oder **Visual Basic**, und wählen Sie den Knoten **Windows** aus. Erweitern Sie dann den Knoten **Windows**, und wählen Sie den Knoten **Klassischer Desktop** aus.  
  
3.  Wählen Sie in der Vorlagenliste die Vorlage **WPF\-Anwendung** aus.  
  
4.  Geben Sie im Textfeld **Name**`ExpenseIt` ein, und wählen Sie dann die Schaltfläche **OK** aus.  
  
     Das Projekt wird erstellt, und die Projektdateien werden dem **Projektmappen\-Explorer** hinzugefügt. Zudem wird der Designer für das Standardanwendungsfenster namens **MainWindow.xaml** angezeigt.  
  
#### So ändern Sie das Hauptfenster  
  
1.  Wählen Sie im Designer die Registerkarte **MainWindow.xaml** aus, falls sie noch nicht die aktive Designerregisterkarte ist.  
  
2.  Wenn Sie C\# verwenden, suchen Sie die Zeile `<Window x:Class="ExpenseIt.MainWindow"`, und ersetzen Sie sie durch `<NavigationWindow x:Class="ExpenseIt.MainWindow"`.  
  
     Wenn Sie Visual Basic verwenden, suchen Sie die Zeile `<Window x:Class=" MainWindow"`, und ersetzen Sie sie durch `<NavigationWindow x:Class="MainWindow"`.  
  
     Beachten Sie Folgendes. Wenn Sie das `<Window`\-Tag in `<NavigationWindow` ändern, wird das Endtag von IntelliSense ebenfalls automatisch in `</NavigationWindow>` geändert.  
  
    > [!NOTE]
    >  Wenn nach dem Ändern des Tags das Fenster **Fehlerliste** geöffnet ist, können mehrere Fehler angezeigt werden. Allerdings werden sie durch die Änderungen, die Sie in den nächsten Schritten vornehmen, behoben.  
  
3.  Wählen Sie das `<Grid>`\-Tag und das `</Grid>`\-Tag aus, und löschen Sie sie.  
  
     **NavigationWindow** darf keine anderen Benutzeroberflächenelemente enthalten, wie z. B. **Grid**.  
  
4.  Erweitern Sie im Fenster **Eigenschaften** den Kategorieknoten **Common**, und wählen Sie die **Title**\-Eigenschaft aus. Geben Sie dann `ExpenseIt` ein, und drücken Sie die **EINGABETASTE**.  
  
     Beachten Sie, dass das **Title**\-Element im XAML\-Fenster nun dem neuen Wert entspricht. Sie können die XAML\-Eigenschaften im XAML\-Fenster oder im Fenster **Eigenschaften** bearbeiten. Die Änderungen werden synchronisiert.  
  
5.  Legen Sie im XAML\-Fenster den Wert des Elements **Height** auf `375` fest, und legen Sie den Wert der Eigenschaft **Width** auf `500` fest.  
  
     Diese Elemente entsprechen den Eigenschaften **Height** und **Width** in der Kategorie **Layout** im Fenster **Eigenschaften**.  
  
     Ihre Datei **MainWindow.xaml** sollte jetzt in C\# wie folgt aussehen:  
  
    ```xaml  
    <NavigationWindow x:Class="ExpenseIt.MainWindow" xmlns="http://schemas.microsoft.com/winfx/2006/xaml/presentation" xmlns:x="http://schemas.microsoft.com/winfx/2006/xaml" xmlns:d="http://schemas.microsoft.com/expression/blend/2008" xmlns:mc="http://schemas.openxmlformats.org/markup-compatibility/2006" xmlns:local="clr-namespace:ExpenseIt" mc:Ignorable="d" Title="ExpenseIt" Height="375" Width="500"> </NavigationWindow>  
    ```  
  
     Oder in Visual Basic wie folgt:  
  
    ```xaml  
    <NavigationWindow x:Class="MainWindow" xmlns="http://schemas.microsoft.com/winfx/2006/xaml/presentation" xmlns:x="http://schemas.microsoft.com/winfx/2006/xaml" xmlns:d="http://schemas.microsoft.com/expression/blend/2008" xmlns:mc="http://schemas.openxmlformats.org/markup-compatibility/2006" xmlns:local="clr-namespace:ExpenseIt" mc:Ignorable="d" Title="ExpenseIt" Height="375" Width="500"> </NavigationWindow>  
    ```  
  
#### So ändern Sie die CodeBehind\-Datei \(C\#\)  
  
1.  Erweitern Sie im **Projektmappen\-Explorer** den Knoten **MainWindow.xaml**, und öffnen Sie die Datei **MainWindow.xaml.cs**.  
  
2.  Suchen Sie die Zeile `public partial class MainWindow : Window`, und ersetzen Sie sie durch `public partial class MainWindow : NavigationWindow`.  
  
     Dadurch wird die `MainWindow`\-Klasse so geändert, dass sie von `NavigationWindow` abgeleitet wird. In Visual Basic geschieht dies automatisch, wenn Sie das Fenster in XAML ändern. Daher sind keine Codeänderungen erforderlich.  
  
##  <a name="add_files_to_the_application"></a> Hinzufügen von Dateien zur Anwendung  
 In diesem Abschnitt fügen Sie der Anwendung zwei Seiten und ein Bild hinzu.  
  
#### So fügen Sie einen Startbildschirm hinzu  
  
1.  Öffnen Sie im **Projektmappen\-Explorer** das Kontextmenü für den Knoten **ExpenseIt**, und wählen Sie **Hinzufügen**, **Seite** aus.  
  
2.  Wählen Sie im Dialogfeld **Neues Element hinzufügen** das Textfeld **Name** aus, und geben Sie `ExpenseItHome` ein. Wählen Sie dann die Schaltfläche **Hinzufügen** aus.  
  
     Diese Seite ist das erste Fenster, das beim Anwendungsstart angezeigt wird:  
  
3.  Wählen Sie im Designer die Registerkarte **ExpenseItHome.xaml** aus, falls sie noch nicht die aktive Designerregisterkarte ist.  
  
4.  Wählen Sie das `<Title>`\-Element aus, und ändern Sie den Titel in **ExpenseIt – Home**.  
  
     Ihre Datei **ExpenseItHome.xaml** sollte jetzt in C\# wie folgt aussehen:  
  
    ```xaml  
    <Page x:Class="ExpenseIt.ExpenseItHome" xmlns="http://schemas.microsoft.com/winfx/2006/xaml/presentation" xmlns:x="http://schemas.microsoft.com/winfx/2006/xaml" xmlns:mc="http://schemas.openxmlformats.org/markup-compatibility/2006" xmlns:d="http://schemas.microsoft.com/expression/blend/2008" xmlns:local="clr-namespace:ExpenseIt" mc:Ignorable="d" d:DesignHeight="300" d:DesignWidth="300" Title="ExpenseIt - Home"> <Grid> </Grid> </Page>  
    ```  
  
     Oder in Visual Basic wie folgt:  
  
    ```xaml  
    <Page x:Class="ExpenseItHome" xmlns="http://schemas.microsoft.com/winfx/2006/xaml/presentation" xmlns:x="http://schemas.microsoft.com/winfx/2006/xaml" xmlns:mc="http://schemas.openxmlformats.org/markup-compatibility/2006" xmlns:d="http://schemas.microsoft.com/expression/blend/2008" xmlns:local="clr-namespace:ExpenseIt" mc:Ignorable="d" d:DesignHeight="300" d:DesignWidth="300" Title="ExpenseIt - Home"> <Grid> </Grid> </Page>  
    ```  
  
5.  Wählen Sie im Designer die Registerkarte **MainWindow.xaml** aus.  
  
6.  Suchen Sie das `Title="ExpenseIt" Height="375" Width="500">`\-Zeilenelement, und fügen Sie eine `Source="ExpenseItHome.xaml"`\-Eigenschaft hinzu.  
  
     Dadurch wird **ExpenseItHome.xaml** als erste Seite festgelegt, die beim Start der Anwendung geöffnet wird. Ihre Datei **MainWindow.xaml** sollte jetzt in C\# wie folgt aussehen:  
  
    ```xaml  
    <NavigationWindow x:Class="ExpenseIt.MainWindow" xmlns="http://schemas.microsoft.com/winfx/2006/xaml/presentation" xmlns:x="http://schemas.microsoft.com/winfx/2006/xaml" xmlns:d="http://schemas.microsoft.com/expression/blend/2008" xmlns:mc="http://schemas.openxmlformats.org/markup-compatibility/2006" xmlns:local="clr-namespace:ExpenseIt" mc:Ignorable="d" Title="ExpenseIt" Height="375" Width="500" Source="ExpenseItHome.xaml"> </NavigationWindow>  
    ```  
  
     Oder in Visual Basic wie folgt:  
  
    ```xaml  
    NavigationWindow x:Class="MainWindow" xmlns="http://schemas.microsoft.com/winfx/2006/xaml/presentation" xmlns:x="http://schemas.microsoft.com/winfx/2006/xaml" xmlns:d="http://schemas.microsoft.com/expression/blend/2008" xmlns:mc="http://schemas.openxmlformats.org/markup-compatibility/2006" xmlns:local="clr-namespace:ExpenseIt" mc:Ignorable="d" Title="ExpenseIt" Height="375" Width="500" Source="ExpenseItHome.xaml"> </NavigationWindow>  
    ```  
  
     Wie bei den zuvor festgelegten Eigenschaften hätten Sie die `Source`\-Eigenschaft in der Kategorie **Sonstiges** im Fenster **Eigenschaften** festlegen können.  
  
#### So fügen Sie ein Detailsfenster hinzu  
  
1.  Öffnen Sie im **Projektmappen\-Explorer** das Kontextmenü für den Knoten **ExpenseIt**, und wählen Sie **Hinzufügen**, **Seite** aus.  
  
2.  Wählen Sie im Dialogfeld **Neues Element hinzufügen** das Textfeld **Name** aus, und geben Sie `ExpenseReportPage` ein. Wählen Sie dann die Schaltfläche **Hinzufügen** aus.  
  
     In diesem Fenster wird eine einzelne Spesenabrechnung angezeigt.  
  
3.  Wählen Sie im Designer die Registerkarte **ExpenseReportPage.xaml** aus, falls sie noch nicht die aktive Designerregisterkarte ist.  
  
4.  Wählen Sie das `<Title>`\-Element aus, und ändern Sie den Titel in **ExpenseIt – View Expense**.  
  
     Ihre Datei "ExpenseReportPage.xaml" sollte jetzt in C\# wie folgt aussehen:  
  
    ```xaml  
    Page x:Class="ExpenseIt.ExpenseReportPage" xmlns="http://schemas.microsoft.com/winfx/2006/xaml/presentation" xmlns:x="http://schemas.microsoft.com/winfx/2006/xaml" xmlns:mc="http://schemas.openxmlformats.org/markup-compatibility/2006" xmlns:d="http://schemas.microsoft.com/expression/blend/2008" xmlns:local="clr-namespace:ExpenseIt" mc:Ignorable="d" d:DesignHeight="300" d:DesignWidth="300" Title="ExpenseIt - View Expense"> <Grid> </Grid> </Page>  
    ```  
  
     Oder in Visual Basic wie folgt:  
  
    ```xaml  
    <Page x:Class="ExpenseReportPage" xmlns="http://schemas.microsoft.com/winfx/2006/xaml/presentation" xmlns:x="http://schemas.microsoft.com/winfx/2006/xaml" xmlns:mc="http://schemas.openxmlformats.org/markup-compatibility/2006" xmlns:d="http://schemas.microsoft.com/expression/blend/2008" xmlns:local="clr-namespace:ExpenseIt" mc:Ignorable="d" d:DesignHeight="300" d:DesignWidth="300" Title="ExpenseIt - View Expense"> <Grid> </Grid> </Page>  
    ```  
  
5.  Wählen Sie auf der Menüleiste **Debuggen**, **Debuggen starten** aus \(oder drücken Sie F5\), um die Anwendung auszuführen.  
  
     Die folgende Abbildung zeigt die Anwendung mit den Navigationsschaltflächen des Fensters.  
  
     ![Bildschirmabbildung für ExpenseIt&#45;Beispiel](../designers/media/gettingstartedfigure1.png "GettingStartedFigure1")  
  
6.  Schließen Sie die Anwendung, um zum Entwurfsmodus zurückzukehren.  
  
##  <a name="Add_Layout"></a> Erstellen der Benutzeroberfläche  
 Das Layout bietet die Möglichkeit, Elemente anzuordnen und die Größe und Position dieser Elemente zu verwalten, wenn ein Formular vergrößert oder verkleinert wird. In diesem Abschnitt erstellen Sie ein einspaltiges Raster mit drei Zeilen. Sie fügen den beiden Seiten Steuerelemente hinzu, fügen dann Code hinzu und definieren zum Schluss wiederverwendbare Stile für die Steuerelemente.  
  
#### So erstellen Sie das Layout  
  
1.  Öffnen Sie **ExpenseItHome.xaml**, und wählen Sie das `<Grid>`\-Element aus.  
  
2.  Erweitern Sie im Fenster **Eigenschaften** den Kategorieknoten **Layout**, und legen Sie die Werte für **Margin** auf `10`, `10`, `0` und `10` fest. Diese entsprechen dem linken, rechten, oberen und unteren Seitenrand.  
  
     Das `Margin="10,0,10,10"`\-Element wird dem `<Grid>`\-Element in XAML hinzugefügt. Auch in diesem Fall hätten Sie die Werte direkt im XAML\-Code statt im Fenster **Eigenschaften** eingeben können und dasselbe Ergebnis erzielt.  
  
3.  Fügen Sie dem `Grid`\-Element den folgenden XAML\-Code hinzu, um die Zeilen\- und Spaltendefinitionen zu erstellen:  
  
    ```xaml  
    <Grid.ColumnDefinitions> <ColumnDefinition /> </Grid.ColumnDefinitions> <Grid.RowDefinitions> <RowDefinition Height="Auto"/> <RowDefinition /> <RowDefinition Height="Auto"/> </Grid.RowDefinitions>  
    ```  
  
#### So fügen Sie Steuerelemente hinzu  
  
1.  Öffnen Sie **ExpenseItHome.xaml**.  
  
2.  Fügen Sie direkt über dem `</Grid>`\-Tag folgenden XAML\-Code hinzu, um die Steuerelemente `Border`, `ListBox` und `Button` zu erstellen.  
  
    ```xaml  
    <!-- People list --> <Border Grid.Column="0" Grid.Row="0" Height="35" Padding="5" Background="#4E87D4"> <Label VerticalAlignment="Center" Foreground="White">Names</Label> </Border> <ListBox Name="peopleListBox" Grid.Column="0" Grid.Row="1"> <ListBoxItem>Mike</ListBoxItem> <ListBoxItem>Lisa</ListBoxItem> <ListBoxItem>John</ListBoxItem> <ListBoxItem>Mary</ListBoxItem> </ListBox> <!-- View report button --> <Button Grid.Column="0" Grid.Row="2" Margin="0,10,0,0" Width="125" Height="25" HorizontalAlignment="Right">View</Button>  
  
    ```  
  
     Beachten Sie, dass die Steuerelemente im Entwurfsfenster angezeigt werden. Sie hätten die Steuerelemente auch erstellen können, indem Sie sie aus dem Fenster **Toolbox** in das Entwurfsfenster gezogen und deren Eigenschaften im Fenster **Eigenschaften** festgelegt hätten.  
  
3.  Erstellen Sie die Anwendung, und führen Sie sie aus. Die folgende Abbildung zeigt, wie die durch die XAML in diesem Verfahren erstellten Steuerelemente zur Laufzeit dargestellt werden.  
  
     ![Bildschirmabbildung für ExpenseIt&#45;Beispiel](../designers/media/gettingstartedfigure2.png "GettingStartedFigure2")  
  
4.  Schließen Sie die Anwendung, um zum Entwurfsmodus zurückzukehren.  
  
#### So fügen Sie ein Hintergrundbild hinzu  
  
1.  Wählen Sie das folgende Bild aus, und speichern Sie es als `watermark.png`.  
  
     ![Watermark image for walkthrough](../designers/media/wpf_watermark.png "WPF\_watermark")  
  
    > [!NOTE]
    >  Alternativ können Sie ein eigenes Bild erstellen und als `watermark.png` speichern.  
  
2.  Öffnen Sie im **Projektmappen\-Explorer** das Kontextmenü für den Knoten **ExpenseIt**, und wählen Sie **Hinzufügen**, **Vorhandenes Element** aus.  
  
3.  Suchen Sie im Dialogfeld **Vorhandenes Element hinzufügen** das Bild **watermark.png**, das Sie gerade hinzugefügt haben, wählen Sie es aus, und wählen Sie dann die Schaltfläche **Hinzufügen** aus.  
  
    > [!NOTE]
    >  Sie müssen möglicherweise die Liste **Dateitypen** erweitern und **Bilddateien** auswählen.  
  
4.  Öffnen Sie die Datei **ExpenseItHome.xaml**, und fügen Sie direkt über dem `</Grid>`\-Tag den folgenden XAML\-Code hinzu, um ein Hintergrundbild zu erstellen:  
  
    ```xaml  
    <Grid.Background> <ImageBrush ImageSource="watermark.png"/> </Grid.Background>  
  
    ```  
  
#### So fügen Sie einen Titel hinzu  
  
1.  Öffnen Sie **ExpenseItHome.xaml**.  
  
2.  Suchen Sie die Zeile `<Grid.ColumnDefinitions>`, und fügen Sie direkt darunter folgenden Code hinzu:  
  
    ```xaml  
    <ColumnDefinition Width="230" />  
  
    ```  
  
     Dadurch wird links neben den anderen Spalten eine zusätzliche Spalte mit einer festen Breite von 230 Pixeln erstellt.  
  
3.  Suchen Sie die Zeile `<Grid.RowDefinitions>`, und fügen Sie direkt darunter folgenden Code hinzu:  
  
    ```xaml  
    <RowDefinition />  
  
    ```  
  
     Dadurch wird oben im Raster eine Zeile hinzugefügt.  
  
4.  Verschieben Sie die Steuerelemente in die zweite Spalte, indem Sie den `Grid.Column`\-Wert auf 1 festlegen. Verschieben Sie jedes Steuerelement um eine Zeile nach unten, indem Sie jeden `Grid.Row`\-Wert um 1 erhöhen.  
  
    1.  Suchen Sie die Zeile `<Border Grid.Column="0" Grid.Row="0" Height="35" Padding="5" Background="#4E87D4">`. Ändern Sie `Grid.Column="0"` in `Grid.Column="1"` und `Grid.Row="0"` in `Grid.Row="1"`.  
  
    2.  Suchen Sie die Zeile `<ListBox Name="peopleListBox" Grid.Column="0" Grid.Row="1"`. Ändern Sie `Grid.Column="0"` in `Grid.Column="1"` und `Grid.Row="1"` in `Grid.Row="2"`.  
  
    3.  Suchen Sie die Zeile `<Button Grid.Column="0" Grid.Row="2" Margin="0,10,0,0" Width="125"`. Ändern Sie `Grid.Column="0"` in `Grid.Column="1"` und `Grid.Row="2"` in `Grid.Row="3"`.  
  
5.  Fügen Sie direkt vor dem `<Border`\-Element den folgenden XAML\-Code hinzu, um den Titel anzuzeigen:  
  
    ```xaml  
    <Label Grid.Column="1" VerticalAlignment="Center" FontFamily="Trebuchet MS" FontWeight="Bold" FontSize="18" Foreground="#0066cc"> View Expense Report </Label>  
  
    ```  
  
     Der Inhalt von **ExpenseItHome.xaml** sollte jetzt in C\# wie folgt aussehen:  
  
    ```xaml  
    <Page x:Class="ExpenseIt.ExpenseItHome" xmlns="http://schemas.microsoft.com/winfx/2006/xaml/presentation" xmlns:x="http://schemas.microsoft.com/winfx/2006/xaml" xmlns:mc="http://schemas.openxmlformats.org/markup-compatibility/2006" xmlns:d="http://schemas.microsoft.com/expression/blend/2008" xmlns:local="clr-namespace:ExpenseIt" mc:Ignorable="d" d:DesignHeight="300" d:DesignWidth="300" Title="ExpenseIt - Home"> <Grid Margin="10,0,10,10"> <Grid.ColumnDefinitions> <ColumnDefinition Width="230" /> <ColumnDefinition /> </Grid.ColumnDefinitions> <Grid.RowDefinitions> <RowDefinition /> <RowDefinition Height="Auto"/> <RowDefinition /> <RowDefinition Height="Auto"/> </Grid.RowDefinitions> <Border Grid.Column="1" Grid.Row="1" Height="35" Padding="5" Background="#4E87D4"> <Label VerticalAlignment="Center" Foreground="White">Names</Label> </Border> <!-- People list --> <Label Grid.Column="1" VerticalAlignment="Center" FontFamily="Trebuchet MS" FontWeight="Bold" FontSize="18" Foreground="#0066cc"> View Expense Report </Label> <ListBox Name="peopleListBox" Grid.Column="1" Grid.Row="2"> <ListBoxItem>Mike</ListBoxItem> <ListBoxItem>Lisa</ListBoxItem> <ListBoxItem>John</ListBoxItem> <ListBoxItem>Mary</ListBoxItem> </ListBox> <!-- View report button --> <Button Grid.Column="1" Grid.Row="3" Margin="0,10,0,0" Width="125" Height="25" HorizontalAlignment="Right">View</Button> <Grid.Background> <ImageBrush ImageSource="watermark.png"/> </Grid.Background> </Grid> </Page>  
    ```  
  
     Oder in Visual Basic wie folgt:  
  
    ```xaml  
    <Page x:Class="ExpenseItHome" xmlns="http://schemas.microsoft.com/winfx/2006/xaml/presentation" xmlns:x="http://schemas.microsoft.com/winfx/2006/xaml" xmlns:mc="http://schemas.openxmlformats.org/markup-compatibility/2006" xmlns:d="http://schemas.microsoft.com/expression/blend/2008" xmlns:local="clr-namespace:ExpenseIt" mc:Ignorable="d" d:DesignHeight="300" d:DesignWidth="300" Title="ExpenseIt - Home" > <Grid Margin="10,0,10,10"> <Grid.ColumnDefinitions> <ColumnDefinition Width="230" /> <ColumnDefinition /> </Grid.ColumnDefinitions> <Grid.RowDefinitions> <RowDefinition /> <RowDefinition Height="Auto"/> <RowDefinition /> <RowDefinition Height="Auto"/> </Grid.RowDefinitions> <Border Grid.Column="1" Grid.Row="1" Height="35" Padding="5" Background="#4E87D4"> <Label VerticalAlignment="Center" Foreground="White">Names</Label> </Border> <!-- People list --> <Label Grid.Column="1" VerticalAlignment="Center" FontFamily="Trebuchet MS" FontWeight="Bold" FontSize="18" Foreground="#0066cc"> View Expense Report </Label> <ListBox Name="peopleListBox" Grid.Column="1" Grid.Row="2"> <ListBoxItem>Mike</ListBoxItem> <ListBoxItem>Lisa</ListBoxItem> <ListBoxItem>John</ListBoxItem> <ListBoxItem>Mary</ListBoxItem> </ListBox> <!-- View report button --> <Button Grid.Column="1" Grid.Row="3" Margin="0,10,0,0" Width="125" Height="25" HorizontalAlignment="Right">View</Button> <Grid.Background> <ImageBrush ImageSource="watermark.png"/> </Grid.Background> </Grid> </Page>  
    ```  
  
6.  Wenn Sie die Anwendung an diesem Punkt erstellen und ausführen, sollte sie wie in der folgenden Abbildung aussehen:  
  
     ![Bildschirmabbildung für ExpenseIt&#45;Beispiel](../designers/media/gettingstartedfigure3.png "GettingStartedFigure3")  
  
#### So fügen Sie der Schaltfläche Code hinzu  
  
1.  Öffnen Sie **ExpenseItHome.xaml**.  
  
2.  Wählen Sie das `<Button`\-Element aus, und fügen Sie direkt nach dem **HorizontalAlignment\="Right"**\-Element folgenden XAML\-Code hinzu: `Click="Button_Click"`.  
  
     Dadurch wird ein Ereignishandler für das `Click`\-Ereignis der Schaltfläche hinzugefügt. Der Code für das **\<Button**\-Element sollte nun wie folgt aussehen:  
  
    ```  
    <!-- View report button --> <Button Grid.Column="1" Grid.Row="3" Margin="0,10,0,0" Width="125" Height="25" HorizontalAlignment="Right" Click="Button_Click">View</Button>  
    ```  
  
3.  Öffnen Sie die Datei **ExpenseItHome.xaml.cs** oder **ExpenseItHome.xaml.vb**.  
  
4.  Fügen Sie der `ExpenseItHome`\-Klasse folgenden Code hinzu:  
  
    ```c#  
    private void Button_Click(object sender, RoutedEventArgs e) { // View Expense Report ExpenseReportPage expenseReportPage = new ExpenseReportPage(); this.NavigationService.Navigate(expenseReportPage); }  
    ```  
  
    ```vb  
    Private Sub Button_Click(ByVal sender As Object, ByVal e As RoutedEventArgs) ' View Expense Report Dim expenseReportPage As New ExpenseReportPage() Me.NavigationService.Navigate(expenseReportPage) End Sub  
    ```  
  
     Durch diesen Ereignishandler wird die Spesenabrechnungsseite geöffnet, wenn auf die Schaltfläche geklickt wird.  
  
#### So erstellen Sie die Benutzeroberfläche für die Berichtsseite  
  
1.  Öffnen Sie **ExpenseReportPage.xaml**.  
  
     Auf dieser Seite wird die Spesenabrechnung für die auf der Startseite ausgewählte Person angezeigt.  
  
2.  Fügen Sie zwischen dem `<Grid>`\-Tag und `</Grid>`\-Tag folgenden XAML\-Code hinzu.  
  
    ```xaml  
    <Grid.Background> <ImageBrush ImageSource="watermark.png" /> </Grid.Background> <Grid.ColumnDefinitions> <ColumnDefinition Width="230" /> <ColumnDefinition /> </Grid.ColumnDefinitions> <Grid.RowDefinitions> <RowDefinition Height="Auto" /> <RowDefinition /> </Grid.RowDefinitions> <Label Grid.Column="1" VerticalAlignment="Center" FontFamily="Trebuchet MS" FontWeight="Bold" FontSize="18" Foreground="#0066cc"> Expense Report For: </Label> <Grid Margin="10" Grid.Column="1" Grid.Row="1"> <Grid.ColumnDefinitions> <ColumnDefinition /> <ColumnDefinition /> </Grid.ColumnDefinitions> <Grid.RowDefinitions> <RowDefinition Height="Auto" /> <RowDefinition Height="Auto" /> <RowDefinition /> </Grid.RowDefinitions> <!-- Name --> <StackPanel Grid.Column="0" Grid.ColumnSpan="2" Grid.Row="0" Orientation="Horizontal"> <Label Margin="0,0,0,5" FontWeight="Bold">Name:</Label> <Label Margin="0,0,0,5" FontWeight="Bold"></Label> </StackPanel> <!-- Department --> <StackPanel Grid.Column="0" Grid.ColumnSpan="2" Grid.Row="1" Orientation="Horizontal"> <Label Margin="0,0,0,5" FontWeight="Bold">Department:</Label> <Label Margin="0,0,0,5" FontWeight="Bold"></Label> </StackPanel> <Grid Grid.Column="0" Grid.ColumnSpan="2" Grid.Row="2" VerticalAlignment="Top" HorizontalAlignment="Left"> <!-- Expense type and Amount table --> <DataGrid  AutoGenerateColumns="False" RowHeaderWidth="0" > <DataGrid.ColumnHeaderStyle> <Style TargetType="{x:Type DataGridColumnHeader}"> <Setter Property="Height" Value="35" /> <Setter Property="Padding" Value="5" /> <Setter Property="Background" Value="#4E87D4" /> <Setter Property="Foreground" Value="White" /> </Style> </DataGrid.ColumnHeaderStyle> <DataGrid.Columns> <DataGridTextColumn Header="ExpenseType" /> <DataGridTextColumn Header="Amount"  /> </DataGrid.Columns> </DataGrid> </Grid> </Grid>  
    ```  
  
     Diese Benutzeroberfläche ähnelt der für die Startseite erstellten Benutzeroberfläche, allerdings werden die Berichtsdaten in einem **DataGrid**\-Steuerelement angezeigt.  
  
3.  Erstellen Sie die Anwendung, und führen Sie sie aus.  
  
4.  Wählen Sie die Schaltfläche **View** aus.  
  
     Die Spesenabrechnungsseite wird angezeigt.  
  
     Die folgende Abbildung zeigt die Spesenabrechnungsseite. Beachten Sie, dass die Navigationsschaltfläche "Zurück" aktiviert ist.  
  
     ![Bildschirmabbildung für ExpenseIt&#45;Beispiel](../designers/media/gettingstartedfigure4.png "GettingStartedFigure4")  
  
#### So formatieren Sie Steuerelemente  
  
1.  Öffnen Sie die Datei **App.xaml** \(C\#\) oder **Application.xaml** \(Visual Basic\).  
  
2.  Fügen Sie zwischen dem `<Application.Resources>`\-Tag und `</Application.Resources>`\-Tag folgenden XAML\-Code hinzu.  
  
    ```xaml  
    <!-- Header text style --> <Style x:Key="headerTextStyle"> <Setter Property="Label.VerticalAlignment" Value="Center"></Setter> <Setter Property="Label.FontFamily" Value="Trebuchet MS"></Setter> <Setter Property="Label.FontWeight" Value="Bold"></Setter> <Setter Property="Label.FontSize" Value="18"></Setter> <Setter Property="Label.Foreground" Value="#0066cc"></Setter> </Style> <!-- Label style --> <Style x:Key="labelStyle" TargetType="{x:Type Label}"> <Setter Property="VerticalAlignment" Value="Top" /> <Setter Property="HorizontalAlignment" Value="Left" /> <Setter Property="FontWeight" Value="Bold" /> <Setter Property="Margin" Value="0,0,0,5" /> </Style> <!-- DataGrid header style --> <Style x:Key="columnHeaderStyle" TargetType="{x:Type DataGridColumnHeader}"> <Setter Property="Height" Value="35" /> <Setter Property="Padding" Value="5" /> <Setter Property="Background" Value="#4E87D4" /> <Setter Property="Foreground" Value="White" /> </Style> <!-- List header style --> <Style x:Key="listHeaderStyle" TargetType="{x:Type Border}"> <Setter Property="Height" Value="35" /> <Setter Property="Padding" Value="5" /> <Setter Property="Background" Value="#4E87D4" /> </Style> <!-- List header text style --> <Style x:Key="listHeaderTextStyle" TargetType="{x:Type Label}"> <Setter Property="Foreground" Value="White" /> <Setter Property="VerticalAlignment" Value="Center" /> <Setter Property="HorizontalAlignment" Value="Left" /> </Style> <!-- Button style --> <Style x:Key="buttonStyle" TargetType="{x:Type Button}"> <Setter Property="Width" Value="125" /> <Setter Property="Height" Value="25" /> <Setter Property="Margin" Value="0,10,0,0" /> <Setter Property="HorizontalAlignment" Value="Right" /> </Style>  
    ```  
  
     Durch diese XAML werden folgende Stile hinzugefügt:  
  
    -   `headerTextStyle`: Zum Formatieren des Seitentitels für `Label`.  
  
    -   `labelStyle`: Zum Formatieren der `Label`\-Steuerelemente.  
  
    -   `columnHeaderStyle`: Zum Formatieren von `DataGridColumnHeader`.  
  
    -   `listHeaderStyle`: Zum Formatieren der `Border`\-Kopfzeilensteuerelemente.  
  
    -   `listHeaderTextStyle`: Zum Formatieren der Kopfzeile für **Label**.  
  
    -   `buttonStyle`: Zum Formatieren von `Button` auf der Seite **ExpenseItHome.xaml**.  
  
3.  Öffnen Sie **ExpenseItHome.xaml**, und ersetzen Sie alles zwischen dem `<Grid>`\-Element und `</Grid>`\-Element durch folgenden XAML\-Code.  
  
    ```xaml  
    <Grid.ColumnDefinitions> <ColumnDefinition Width="230" /> <ColumnDefinition /> </Grid.ColumnDefinitions> <Grid.RowDefinitions> <RowDefinition/> <RowDefinition Height="Auto"/> <RowDefinition /> <RowDefinition Height="Auto"/> </Grid.RowDefinitions> <Label Grid.Column="1" Style="{StaticResource headerTextStyle}" > View Expense Report </Label> <!-- People list --> <Border Grid.Column="1" Grid.Row="1" Style="{StaticResource listHeaderStyle}"> <Label Style="{StaticResource listHeaderTextStyle}">Names</Label> </Border> <ListBox Name="peopleListBox" Grid.Column="1" Grid.Row="2"> <ListBoxItem>Mike</ListBoxItem> <ListBoxItem>Lisa</ListBoxItem> <ListBoxItem>John</ListBoxItem> <ListBoxItem>Mary</ListBoxItem> </ListBox> <!-- View report button --> <Button Grid.Column="1" Grid.Row="3" Click="Button_Click" Style="{StaticResource buttonStyle}">View</Button> <Grid.Background> <ImageBrush ImageSource="watermark.png"  /> </Grid.Background>  
    ```  
  
     Eigenschaften wie `VerticalAlignment` und `FontFamily`, die die Darstellung der einzelnen Steuerelemente definieren, werden entfernt und ersetzt, indem die Stile angewendet werden.  
  
4.  Öffnen Sie **ExpenseReportPage.xaml**, und ersetzen Sie alles zwischen dem `<Grid>`\-Element und dem `</Grid>`\-Endelement durch folgenden XAML\-Code.  
  
    ```xaml  
    <Grid.Background> <ImageBrush ImageSource="watermark.png" /> </Grid.Background> <Grid.ColumnDefinitions> <ColumnDefinition Width="230" /> <ColumnDefinition /> </Grid.ColumnDefinitions> <Grid.RowDefinitions> <RowDefinition Height="Auto" /> <RowDefinition /> </Grid.RowDefinitions> <Label Grid.Column="1" Style="{StaticResource headerTextStyle}"> Expense Report For: </Label> <Grid Margin="10" Grid.Column="1" Grid.Row="1"> <Grid.ColumnDefinitions> <ColumnDefinition /> <ColumnDefinition /> </Grid.ColumnDefinitions> <Grid.RowDefinitions> <RowDefinition Height="Auto" /> <RowDefinition Height="Auto" /> <RowDefinition /> </Grid.RowDefinitions> <!-- Name --> <StackPanel Grid.Column="0" Grid.ColumnSpan="2" Grid.Row="0" Orientation="Horizontal"> <Label Style="{StaticResource labelStyle}">Name:</Label> <Label Style="{StaticResource labelStyle}"></Label> </StackPanel> <!-- Department --> <StackPanel Grid.Column="0" Grid.ColumnSpan="2" Grid.Row="1" Orientation="Horizontal"> <Label Style="{StaticResource labelStyle}">Department:</Label> <Label Style="{StaticResource labelStyle}"></Label> </StackPanel> <Grid Grid.Column="0" Grid.ColumnSpan="2" Grid.Row="2" VerticalAlignment="Top" HorizontalAlignment="Left"> <!-- Expense type and Amount table --> <DataGrid ColumnHeaderStyle="{StaticResource columnHeaderStyle}" AutoGenerateColumns="False" RowHeaderWidth="0" > <DataGrid.Columns> <DataGridTextColumn Header="ExpenseType" /> <DataGridTextColumn Header="Amount"  /> </DataGrid.Columns> </DataGrid> </Grid> </Grid>  
  
    ```  
  
     Dadurch werden dem `<Label>`\-Element und `<Border>`\-Element Stile hinzugefügt.  
  
## Herstellen von Datenverbindungen  
 In diesem Abschnitt erstellen Sie einen Datenanbieter und eine Datenvorlage und verbinden dann die Steuerelemente, um die Daten anzuzeigen.  
  
#### So binden Sie Daten an ein Steuerelement  
  
1.  Öffnen Sie **ExpenseItHome.xaml**, und wählen Sie das `<Grid>`\-Element aus.  
  
2.  Fügen Sie den folgenden XAML\-Code hinzu:  
  
    ```xaml  
  
    <Grid.Resources> <!-- Expense Report Data --> <XmlDataProvider x:Key="ExpenseDataSource" XPath="Expenses"> <x:XData> <Expenses> <Person Name="Mike" Department="Legal"> <Expense ExpenseType="Lunch" ExpenseAmount="50" /> <Expense ExpenseType="Transportation" ExpenseAmount="50" /> </Person> <Person Name="Lisa" Department="Marketing"> <Expense ExpenseType="Document printing" ExpenseAmount="50"/> <Expense ExpenseType="Gift" ExpenseAmount="125" /> </Person> <Person Name="John" Department="Engineering"> <Expense ExpenseType="Magazine subscription" ExpenseAmount="50"/> <Expense ExpenseType="New machine" ExpenseAmount="600" /> <Expense ExpenseType="Software" ExpenseAmount="500" /> </Person> <Person Name="Mary" Department="Finance"> <Expense ExpenseType="Dinner" ExpenseAmount="100" /> </Person> </Expenses> </x:XData> </XmlDataProvider> </Grid.Resources>  
    ```  
  
     Durch diesen Code wird eine `XmlDataProvider`\-Klasse erstellt, die die Daten für jede Person enthält. Normalerweise würde sie als Datei geladen, aus Gründen der Einfachheit werden die Daten aber inline hinzugefügt.  
  
3.  Fügen Sie im `<Grid.Resources>`\-Element folgenden XAML\-Code hinzu:  
  
    ```xaml  
    <!-- Name item template --> <DataTemplate x:Key="nameItemTemplate"> <Label Content="{Binding XPath=@Name}"/> </DataTemplate>  
    ```  
  
     Dadurch wird `Data Template` hinzugefügt, wodurch die Anzeige der Daten in **ListBox** definiert wird.  
  
4.  Ersetzen Sie das vorhandene `<ListBox>`\-Element durch folgenden XAML\-Code.  
  
    ```xaml  
    <ListBox Name="peopleListBox" Grid.Column="1" Grid.Row="2" ItemsSource="{Binding Source={StaticResource ExpenseDataSource}, XPath=Person}" ItemTemplate="{StaticResource nameItemTemplate}"> </ListBox>  
    ```  
  
     Dieser Code bindet die `ItemsSource`\-Eigenschaft von `ListBox` an die Datenquelle und wendet die Datenvorlage als `ItemTemplate` an.  
  
#### So verbinden Sie Daten mit Steuerelementen  
  
1.  Öffnen Sie **ExpenseReportPage.xaml.vb** oder **ExpenseReportPage.xaml.cs**.  
  
2.  Fügen Sie in C\# der **ExpenseReportPage**\-Klasse folgenden Konstruktor hinzu, oder ersetzen Sie in Visual Basic die vorhandene Klasse durch folgenden Code:  
  
    ```c#  
    // Custom constructor to pass expense report data public ExpenseReportPage(object data):this() { // Bind to expense report data. this.DataContext = data; }  
    ```  
  
    ```vb  
    Partial Public Class ExpenseReportPage Inherits Page Public Sub New() InitializeComponent() End Sub ' Custom constructor to pass expense report data Public Sub New(ByVal data As Object) Me.New() ' Bind to expense report data. Me.DataContext = data End Sub End Class  
    ```  
  
     Dieser Konstruktor akzeptiert ein Datenobjekt als Parameter. In diesem Fall enthält das Datenobjekt den Namen der ausgewählten Person.  
  
3.  Öffnen Sie **ExpenseItHome.xaml.vb** oder **ExpenseItHome.xaml.cs**.  
  
4.  Ersetzen Sie den `Click`\-Ereignishandlercode durch den folgenden Code:  
  
    ```c#  
    private void Button_Click(object sender, RoutedEventArgs e) { // View Expense Report ExpenseReportPage expenseReportPage = new ExpenseReportPage(this.peopleListBox.SelectedItem); this.NavigationService.Navigate(expenseReportPage); }  
    ```  
  
    ```vb  
    Private Sub Button_Click(ByVal sender As Object, ByVal e As RoutedEventArgs) ' View Expense Report Dim expenseReportPage As New ExpenseReportPage(Me.peopleListBox.SelectedItem) Me.NavigationService.Navigate(expenseReportPage) End Sub  
    ```  
  
     Dieser Code ruft den neuen Konstruktor auf.  
  
#### So aktualisieren Sie die Benutzeroberfläche mit Datenvorlagen  
  
1.  Öffnen Sie **ExpenseReportPage.xaml**.  
  
2.  Ersetzen Sie den XAML\-Code für das **Name**\-Element und **Department** `<StackPanel`\-Element durch folgenden Code:  
  
    ```xaml  
    <!-- Name --> <StackPanel Grid.Column="0" Grid.ColumnSpan="2" Grid.Row="0" Orientation="Horizontal"> <Label Style="{StaticResource labelStyle}">Name:</Label> <Label Style="{StaticResource labelStyle}" Content="{Binding XPath=@Name}"></Label> </StackPanel> <!-- Department --> <StackPanel Grid.Column="0" Grid.ColumnSpan="2" Grid.Row="1" Orientation="Horizontal"> <Label Style="{StaticResource labelStyle}">Department:</Label> <Label Style="{StaticResource labelStyle}" Content="{Binding XPath=@Department}"></Label> </StackPanel>  
  
    ```  
  
     Dadurch werden die **Label**\-Steuerelemente an die geeigneten Datenquelleneigenschaften gebunden.  
  
3.  Fügen Sie im `<Grid>`\-Element folgenden XAML\-Code hinzu:  
  
    ```xaml  
    <!--Templates to display expense report data--> <Grid.Resources> <!-- Reason item template --> <DataTemplate x:Key="typeItemTemplate"> <Label Content="{Binding XPath=@ExpenseType}"/> </DataTemplate> <!-- Amount item template --> <DataTemplate x:Key="amountItemTemplate"> <Label Content="{Binding XPath=@ExpenseAmount}"/> </DataTemplate> </Grid.Resources>  
  
    ```  
  
     Dadurch wird definiert, wie die Spesenabrechnungsdaten angezeigt werden.  
  
4.  Ersetzen Sie das `<DataGrid>`\-Element durch folgenden Code:  
  
    ```xaml  
    <!-- Expense type and Amount table --> <DataGrid ItemsSource="{Binding XPath=Expense}" ColumnHeaderStyle="{StaticResource columnHeaderStyle}" AutoGenerateColumns="False" RowHeaderWidth="0" > <DataGrid.Columns> <DataGridTextColumn Header="ExpenseType" Binding="{Binding XPath=@ExpenseType}"  /> <DataGridTextColumn Header="Amount" Binding="{Binding XPath=@ExpenseAmount}" /> </DataGrid.Columns> </DataGrid>  
    ```  
  
     Dadurch werden **ItemSource** hinzugefügt und die Bindungen für die Aufwandsposten definiert.  
  
5.  Erstellen Sie die Anwendung, und führen Sie sie aus.  
  
6.  Wählen Sie eine Person aus, und wählen Sie dann die Schaltfläche **View** aus.  
  
     Die folgende Abbildung zeigt die beiden Seiten der ExpenseIt\-Anwendung mit Steuerelementen, Layout, Stilen, Datenbindung und Datenvorlagen, die angewendet wurden.  
  
     ![Bildschirmabbildungen für ExpenseIt&#45;Beispiel](../designers/media/gettingstartedfigure5.png "GettingStartedFigure5")  
  
##  <a name="Best_Practices"></a> Bewährte Methoden  
 Dieses Beispiel veranschaulicht die Grundlagen von WPF und folgt daher nicht bewährten Methoden für die Anwendungsentwicklung. Ausführlichere Informationen zu bewährten Methoden für die Anwendungsentwicklung mit WPF und .NET Framework finden Sie ggf. unter den folgenden Themen:  
  
-   Barrierefreiheit – [Bewährte Methoden für Eingabehilfen](https://msdn.microsoft.com/en-us/library/aa350483\(v=vs.100\).aspx)  
  
-   Sicherheit – [Sicherheit \(WPF\)](https://msdn.microsoft.com/en-us/library/aa970906\(v=vs.100\).aspx)  
  
-   Lokalisierung – [Übersicht über WPF\-Globalisierung und \-Lokalisierung](https://msdn.microsoft.com/en-us/library/ms788718\(v=vs.100\).aspx)  
  
-   Leistung – [Optimieren der WPF\-Anwendungsleistung](https://msdn.microsoft.com/en-us/library/aa970683\(v=vs.100\).aspx)  
  
##  <a name="Whats_Next"></a> Weitere Informationen  
 Sie haben jetzt eine Reihe von Techniken zum Erstellen von Desktopanwendungen mithilfe von WPF kennengelernt. Sie verfügen nun über grundlegende Kenntnisse der Bausteine, die eine datengebundene WPF\-Anwendung ausmachen. Dieses Thema erhebt keinen Anspruch auf Vollständigkeit, soll aber eine Vorstellung einiger Möglichkeiten vermitteln, die Sie neben den in diesem Thema vorgestellten Techniken selbst entdecken können.  
  
 Weitere Informationen über die WPF\-Architektur und \-Programmiermodelle finden Sie in den folgenden Themen:  
  
-   [WPF\-Architektur](https://msdn.microsoft.com/en-us/library/ms750441\(v=vs.100\).aspx)  
  
-   [Übersicht über XAML](https://msdn.microsoft.com/en-us/library/ms752059\(v=vs.100\).aspx)  
  
-   [Übersicht über Abhängigkeitseigenschaften](https://msdn.microsoft.com/en-us/library/ms752914\(v=vs.100\).aspx)  
  
-   [Layoutsystem](https://msdn.microsoft.com/en-us/library/ms745058\(v=vs.100\).aspx)  
  
-   [Stile und Vorlagen](https://msdn.microsoft.com/en-us/library/bb613570\(v=vs.100\).aspx)  
  
 Weitere Informationen zum Erstellen von Anwendungen finden Sie in den folgenden Themen:  
  
-   [Übersicht über die Anwendungsentwicklung](https://msdn.microsoft.com/en-us/library/bb613549\(v=vs.100\).aspx)  
  
-   [Übersicht zu Steuerelementen](https://msdn.microsoft.com/en-us/library/bb613551\(v=vs.100\).aspx)  
  
-   [Übersicht zur Datenbindung](https://msdn.microsoft.com/en-us/library/ms752347\(v=vs.100\).aspx)  
  
-   [Übersicht zu WPF\-Grafiken, \-Animationen und \-Medien](https://msdn.microsoft.com/en-us/library/ms742562\(v=vs.100\).aspx)  
  
-   [Dokumente in WPF](https://msdn.microsoft.com/en-us/library/ms748388\(v=vs.100\).aspx)  
  
## Siehe auch  
 [Exemplarische Vorgehensweise: Erstellen einer WPF\-Desktopanwendung, die mit einem Azure Mobile Service verbunden ist](../designers/walkthrough-create-a-wpf-desktop-application-connected-to-an-azure-mobile-service.md)   
 [Erstellen von modernen Desktopanwendungen mit Windows Presentation Foundation](../designers/create-modern-desktop-applications-with-windows-presentation-foundation.md)