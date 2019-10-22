---
title: Erstellen einer einfachen Daten Anwendung mit WPF und Entity Framework 6 | Microsoft-Dokumentation
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-data-tools
ms.topic: conceptual
ms.assetid: 65929fab-5d78-4e04-af1e-cf4957f230f6
caps.latest.revision: 25
author: jillre
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: 403415eaf8a882efdd63fdb9a73b5489b91f2529
ms.sourcegitcommit: a8e8f4bd5d508da34bbe9f2d4d9fa94da0539de0
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 10/19/2019
ms.locfileid: "72651084"
---
# <a name="create-a-simple-data-application-with-wpf-and-entity-framework-6"></a>Erstellen einer einfachen Datenanwendung mit WPF und Entity Framework 6
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

In dieser exemplentyp Anleitung wird veranschaulicht, wie Sie eine einfache "Forms over Data"-Anwendung in Visual Studio mit SQL Server localdb, der Northwind-Datenbank, Entity Framework 6 und Windows Presentation Foundation erstellen. Es zeigt, wie die grundlegende Datenbindung mit einer Master/Detail-Ansicht durchzuführen ist. Außerdem enthält Sie einen benutzerdefinierten "Bindungs Navigator" mit Schaltflächen für "weiter verschieben", "nach oben verschieben", "an den Anfang verschieben", "an das Ende verschieben", "Aktualisieren" und "Löschen".

 Der Schwerpunkt dieses Artikels liegt auf der Verwendung von Data Tools in Visual Studio. es wird nicht versucht, die zugrunde liegenden Technologien in beliebiger Tiefe zu erläutern. Dabei wird davon ausgegangen, dass Sie über eine grundlegende Vertrautheit mit XAML, Entity Framework und SQL verfügen. In diesem Beispiel wird auch die MVVM-Architektur nicht veranschaulicht, die für WPF-Anwendungen standardmäßig verwendet wird. Sie können diesen Code jedoch mit sehr wenigen Änderungen in Ihre eigene MVVM-Anwendung kopieren.

## <a name="install-and-connect-to-northwind"></a>Installieren von und Herstellen einer Verbindung mit Northwind
 In diesem Beispiel werden SQL Server Express localdb-und Northwind-Beispieldatenbank verwendet. Es sollte auch mit anderen SQL-Datenbankprodukten funktionieren, wenn der ADO.NET-Datenanbieter für dieses Produkt Entity Framework unterstützt.

1. Wenn Sie dies noch nicht getan haben, installieren Sie SQL Server 2014 localdb Express 32 Bit auf der [Downloadseite für die SQL Server Editionen](https://www.microsoft.com/sql-server/sql-server-editions-express).

2. Installieren Sie die Beispieldatenbank Northwind, indem Sie die folgenden Anweisungen befolgen: [Install SQL Server Sample](../data-tools/install-sql-server-sample-databases.md)Database.

3. [Fügen Sie neue Verbindungen](../data-tools/add-new-connections.md) für Northwind hinzu.

## <a name="configure-the-project"></a>Konfigurieren des Projekts

1. Wählen Sie in Visual Studio **Datei &#124; neu Projekt** aus, und erstellen Sie C# dann eine neue WPF-Anwendung.

2. Als Nächstes fügen wir das nuget-Paket für Entity Framework 6 hinzu. Wählen Sie in Projektmappen-Explorer den Projekt Knoten aus. Wählen Sie im Hauptmenü **Projekt &#124; nuget-Pakete verwalten... aus.**

     ![Menü Element "nuget-Pakete verwalten"](../data-tools/media/raddata-vs2015-manage-nuget-packages.png "raddata_vs2015_manage_nuget_packages")

3. Klicken Sie im nuget-Paket-Manager auf den Link zum **Durchsuchen** . Entity Framework ist wahrscheinlich das oberste Paket in der Liste. Klicken Sie im rechten Bereich auf **Installieren** , und befolgen Sie die Anweisungen. Im Ausgabefenster werden Sie informiert, wenn die Installation abgeschlossen ist.

     ![Entity Framework nuget-Pakets](../data-tools/media/raddata-vs2015-nuget-ef.png "raddata_vs2015_Nuget_EF")

4. Nun können wir Visual Studio verwenden, um ein Modell zu erstellen, das auf der Northwind-Datenbank basiert.

## <a name="create-the-model"></a>Erstellen des Modells

1. Klicken Sie in Projektmappen-Explorer mit der rechten Maustaste auf den Projekt Knoten, und wählen Sie **Neues Element hinzufügen &#124;** Wählen Sie im linken Bereich unter dem C# Knoten **Daten** aus, und wählen Sie dann im mittleren Bereich die Option **ADO.NET Entity Data Model**aus.

    ![Neues Projekt Element Entity Framework Modell](../data-tools/media/raddata-ef-new-project-item.png "raddata EF, neues Projekt Element")

2. Nennen Sie das Modell `Northwind_model`, und wählen Sie OK aus. Dadurch wird der **Entity Data Model-Assistent**geöffnet. Wählen Sie **EF Designer aus Datenbank aus** , und klicken Sie dann auf **weiter**.

    ![EF-Modell aus der Datenbank](../data-tools/media/raddata-ef-model-from-database.png "raddata EF-Modell aus der Datenbank")

3. Wählen Sie im nächsten Bildschirm Ihre localdb-Verbindung mit Northwind aus, und klicken Sie auf **weiter**.

4. Auf der nächsten Seite des Assistenten wählen Sie aus, welche Tabellen, gespeicherten Prozeduren und anderen Datenbankobjekte in das Entity Framework Modell eingeschlossen werden sollen. Erweitern Sie den Knoten dbo in der Strukturansicht, und wählen Sie Kunden, Bestellungen und Bestell Details aus. Lassen **Sie die**Standardeinstellungen aktiviert

    ![Datenbankobjekte für das Modell auswählen](../data-tools/media/raddata-choose-ef-objects.png "raddata auswählen von EF-Objekten")

5. Der Assistent generiert die C# Klassen, die das Entity Framework Modell darstellen. Dabei handelt es sich C# um reine alte Klassen, die wir mit der WPF-Benutzeroberfläche verbinden werden. Die EDMX-Datei beschreibt die Beziehungen und anderen Metadaten, die die Klassen den Objekten in der Datenbank zuordnen.  Die TT-Dateien sind T4-Vorlagen, die den Code generieren, der für das Modell verwendet wird, und Änderungen an der Datenbank speichern. Sie können alle diese Dateien in Projektmappen-Explorer unter dem Knoten Northwind_model sehen:

    ![Projektmappen-Explorer EF-Modelldateien](../data-tools/media/raddata-solution-explorer-ef-model-files.png "raddata Projektmappen-Explorer EF-Modelldateien")

    Die Designer Oberfläche für die EDMX-Datei ermöglicht es Ihnen, einige Eigenschaften und Beziehungen im Modell zu ändern. Der Designer wird in dieser exemplarischen Vorgehensweise nicht verwendet.

6. Die TT-Dateien sind universell, und wir müssen einen von Ihnen für die Arbeit mit WPF-Datenbindung optimieren, was observablecollections erfordert.  Erweitern Sie in Projektmappen-Explorer den Knoten Northwind_model, bis Sie Northwind_model. tt gefunden haben. (Stellen Sie sicher, dass Sie **nicht** im *. Die Datei "context. tt" direkt unterhalb der EDMX-Datei).

   - Ersetzen Sie die beiden Vorkommen von <xref:System.Collections.ICollection> durch <xref:System.Collections.ObjectModel.ObservableCollection%601>.

   - Ersetzen Sie das erste Vorkommen von <xref:System.Collections.Generic.HashSet%601> durch <xref:System.Collections.ObjectModel.ObservableCollection%601> um Zeile 51. Zweites Vorkommen des Hashsets nicht ersetzen

   - Ersetzen Sie das einzige Vorkommen von <xref:System.Collections.Generic> (um Zeile 334) durch <xref:System.Collections.ObjectModel>.

7. Drücken Sie **STRG + UMSCHALT + B** , um das Projekt zu erstellen. Wenn der Build abgeschlossen ist, sind die Modellklassen für den Datenquellen-Assistenten sichtbar.

   Nun können wir dieses Modell mit der XAML-Seite verbinden, damit wir die Daten anzeigen, navigieren und ändern können.

## <a name="databind-the-model-to-the-xaml-page"></a>DataBind des Modells an die XAML-Seite
 Es ist möglich, ihren eigenen Datenbindung-Code zu schreiben, aber es ist viel einfacher, Visual Studio für Sie zu verwenden.

1. Wählen Sie im Hauptmenü **Projekt &#124; neue Datenquelle hinzufügen** aus, um den **Assistenten zum Konfigurieren von Datenquellen**zu aktivieren. Wählen Sie **Objekt** aus, da wir an die Modellklassen binden, nicht an die Datenbank:

     ![Assistent zum Konfigurieren von Datenquellen mit Objekt Quelle](../data-tools/media/raddata-data-source-configuration-wizard-with-object-source.png "Assistent zum Konfigurieren der raddata-Datenquelle mit der Objekt Quelle")

2. Wählen Sie Kunde aus.  (Quellen für Aufträge werden automatisch aus der Orders-Navigations Eigenschaft in Customer generiert.)

     ![Entitäts Klassen als Datenquellen hinzufügen](../data-tools/media/raddata-add-entity-classes-as-data-sources.png "raddata Hinzufügen von Entitäts Klassen als Datenquellen")

3. Klicken auf **Fertig** stellen

4. Navigieren Sie in der Code Ansicht zu "MainWindow. XAML". Der XAML-Code wird für dieses Beispiel sehr einfach gehalten. Ändern Sie den Titel von "MainWindow" in einen aussagekräftigeren Namen, und vergrößern Sie seine Höhe und Breite auf 600 x 800. Sie können Sie später jederzeit ändern. Fügen Sie nun die drei Zeilen Definitionen dem Haupt Raster hinzu, eine Zeile für die Navigations Schaltflächen, eine für die Details des Kunden, eine für das Raster, das Ihre Bestellungen anzeigt:

    ```xaml
    <Grid.RowDefinitions>
               <RowDefinition Height="auto"/>
               <RowDefinition Height="auto"/>
               <RowDefinition Height="*"/>
           </Grid.RowDefinitions>
    ```

5. Öffnen Sie nun die Datei "MainWindow. XAML", sodass Sie Sie im Designer anzeigen. Dadurch wird das Fenster Datenquellen als Option im Visual Studio-Fensterrand neben Toolbox angezeigt. Klicken Sie auf die Registerkarte, um das Fenster zu öffnen, oder drücken Sie **UMSCHALT + ALT + D** , oder wählen Sie **andere Windows &#124; &#124; -Datenquellen anzeigen**aus. Jede Eigenschaft in der Customers-Klasse wird in einem eigenen Textfeld angezeigt. Klicken Sie zuerst auf den Pfeil im Kombinations Feld Customers, und wählen Sie **Details**aus. Ziehen Sie dann den Knoten auf den mittleren Teil der Entwurfs Oberfläche, damit der Designer weiß, dass er in der mittleren Zeile angezeigt werden soll.  Wenn Sie ihn falsch angeben, können Sie die Zeile später in der XAML manuell angeben. Standardmäßig werden die Steuerelemente vertikal in einem Raster Element platziert, aber an dieser Stelle können Sie Sie im Formular anordnen.  Beispielsweise kann es sinnvoll sein, das Textfeld Name oberhalb der Adresse zu platzieren. Die Beispielanwendung für diesen Artikel ordnet die Felder neu an und ordnet Sie in zwei Spalten an.

     ![Kundendaten Quellen Bindung an einzelne Steuerelemente](../data-tools/media/raddata-customers-data-source-binding-to-individual-controls.png "Datenquellen Bindung für raddata-Kunden an einzelne Steuerelemente")

     In der Code Ansicht können Sie nun ein neues `Grid`-Element in Zeile 1 (die mittlere Zeile) des übergeordneten Rasters sehen. Das übergeordnete Raster verfügt über ein `DataContext` Attribut, das auf eine CollectionViewSource verweist, die dem `Windows.Resources`-Element hinzugefügt wurde. Bei diesem Datenkontext, wenn das erste Textfeld z. b. an "Address" gebunden ist, wird dieser Name der `Address`-Eigenschaft im aktuellen `Customer`-Objekt in der CollectionViewSource zugeordnet.

    ```xaml
    <Grid DataContext="{StaticResource customerViewSource}">
    ```

6. Wenn ein Kunde in der oberen Hälfte des Fensters sichtbar ist, werden die Bestellungen in der unteren Hälfte des Fensters angezeigt. Wir zeigen die Aufträge in einem einzelnen Rasteransicht-Steuerelement an. Damit die Master-Detail-Datenbindung erwartungsgemäß funktioniert, ist es wichtig, dass wir an die Orders-Eigenschaft in der Customers-Klasse und nicht an den separaten Knoten Orders gebunden werden. Beachten Sie die folgende Abbildung. Ziehen Sie die Orders-Eigenschaft der Customers-Klasse in die untere Hälfte des Formulars, sodass der Designer Sie in Zeile 2 einfügt:

     ![Ziehen Sie Orders-Klassen als Raster.](../data-tools/media/raddata-drag-orders-classes-as-grid.png "raddata Drag Orders-Klassen als Raster")

7. Visual Studio hat den gesamten Bindungs Code generiert, der die UI-Steuerelemente mit Ereignissen im Modell verbindet. Alles, was wir tun müssen, um einige Daten anzuzeigen, ist das Schreiben von Code zum Auffüllen des Modells. Navigieren Sie zunächst zu MainWindow.XAML.cs, und fügen Sie der MainWindow-Klasse für den Datenkontext ein Datenmember hinzu. Dieses Objekt, das für uns generiert wurde, verhält sich ähnlich wie ein Steuerelement, das Änderungen und Ereignisse im Modell nachverfolgt. In diesem Artikel fügen wir zwei Mitglieder hinzu, die wir später verwenden werden, um einen neuen Kunden oder eine neue Bestellung hinzuzufügen. Außerdem fügen wir die Initialisierungs Logik für den Konstruktor hinzu. Der Anfang der Klasse sollte wie folgt aussehen:

    ```csharp
    public partial class MainWindow : Window
       {
           public Customer newCustomer { get; set; }
           public Order newOrder { get; set; }

           NorthwindEntities context = new NorthwindEntities();
           CollectionViewSource custViewSource;
           CollectionViewSource ordViewSource;

           public MainWindow()
           {
               InitializeComponent();
               newCustomer = new Customer();
               newOrder = new Order();
               custViewSource = ((CollectionViewSource)
                   (FindResource("customerViewSource")));
               ordViewSource = ((CollectionViewSource)
                   (FindResource("customerOrdersViewSource")));
               DataContext = this;
           }
    ```

     Fügen Sie eine `using`-Direktive für "System. Data. Entity" hinzu, um die Lasten Erweiterungsmethode in den Gültigkeitsbereich

    ```csharp
    using System.Data.Entity;
    ```

     Scrollen Sie nun nach unten, und suchen Sie den Window_Loaded-Ereignishandler. Beachten Sie, dass Visual Studio ein CollectionViewSource-Objekt für uns hinzugefügt hat. Dies stellt das NorthwindEntities-Objekt dar, das wir bei der Erstellung des Modells ausgewählt haben. Fügen Sie Window_loaded Code hinzu, damit die gesamte Methode nun wie folgt aussieht:

    ```csharp
    private void Window_Loaded(object sender, RoutedEventArgs e)
        {
            // Load is an extension method on IQueryable,
            // defined in the System.Data.Entity namespace.
            // This method enumerates the results of the query,
            // similar to ToList but without creating a list.
            // When used with Linq to Entities this method
            // creates entity objects and adds them to the context.
            context.Customers.Load();

            // After the data is loaded call the DbSet<T>.Local property
            // to use the DbSet<T> as a binding source.
            custViewSource.Source = context.Customers.Local;
        }
    ```

8. Drücken Sie **F5**. Die Details für den ersten Kunden, der in CollectionViewSource abgerufen wurde, und deren Bestellungen im Datenraster sollten angezeigt werden. Die Formatierung ist nicht groß, also korrigieren wir dies. und können eine Möglichkeit zum Anzeigen der anderen Datensätze sowie grundlegende CRUD-Vorgänge durchführen.

## <a name="adjust-the-page-design-and-add-grids-for-new-customers-and-orders"></a>Anpassen des Seiten Entwurfs und Hinzufügen von Rastern für neue Kunden und Bestellungen
 Die von Visual Studio erstellte Standardanordnung ist nicht ideal für unsere Anwendung. Daher nehmen wir einige Änderungen manuell in XAML vor. Wir benötigen auch einige "Formulare" (die tatsächlich Raster sind), damit der Benutzer einen neuen Kunden oder eine neue Bestellung hinzufügen kann.    Um einen neuen Kunden und eine Bestellung hinzufügen zu können, benötigen wir einen separaten Satz von Textfeldern, die nicht an die `CollectionViewSource` gebunden sind. Wir steuern, welches Raster der Benutzer zu einem beliebigen Zeitpunkt sieht, indem Sie die Visible-Eigenschaft in den Handlermethoden festlegen.

 Schließlich fügen wir jeder Zeile im Raster Orders eine Lösch Schaltfläche hinzu, um es Benutzern zu ermöglichen, eine einzelne Bestellung zu löschen.

 Fügen Sie zunächst die folgenden Stile zu Windows. resources hinzu:

```xaml
<Style x:Key="Label" TargetType="{x:Type Label}" BasedOn="{x:Null}">
    <Setter Property="HorizontalAlignment" Value="Left"/>
    <Setter Property="VerticalAlignment" Value="Center"/>
    <Setter Property="Margin" Value="3"/>
    <Setter Property="Height" Value="23"/>
</Style>
<Style x:Key="CustTextBox" TargetType="{x:Type TextBox}" BasedOn="{x:Null}">
    <Setter Property="HorizontalAlignment" Value="Right"/>
    <Setter Property="VerticalAlignment" Value="Center"/>
    <Setter Property="Margin" Value="3"/>
    <Setter Property="Height" Value="26"/>
    <Setter Property="Width" Value="120"/>
</Style>
```

 Ersetzen Sie als nächstes das gesamte äußere Raster durch dieses Markup:

```xaml
<Grid >
     <Grid.RowDefinitions>
         <RowDefinition Height="auto"/>
         <RowDefinition Height="auto"/>
         <RowDefinition Height="*"/>
     </Grid.RowDefinitions>
     <StackPanel  Orientation="Horizontal" Margin="2,2,2,0" Height="36" VerticalAlignment="Top" Background="Gainsboro" DataContext="{StaticResource customerViewSource}" d:LayoutOverrides="LeftMargin, RightMargin, TopMargin, BottomMargin">
         <Button Name="btnFirst" Content="|◄" Command="{StaticResource FirstCommand}" Style="{StaticResource NavButton}"  />
         <Button Name="btnPrev"  Content="◄" Command="{StaticResource PreviousCommand}" Style="{StaticResource NavButton}"/>
         <Button Name="btnNext"  Content="►" Command="{StaticResource NextCommand}"     Style="{StaticResource NavButton}"/>
         <Button Name="btnLast"  Content="►|" Command="{StaticResource LastCommand}" Style="{StaticResource NavButton}"/>
         <Button Name="btnDelete" Content="Delete Customer" Command="{StaticResource DeleteCustomerCommand}" FontSize="11" Width="120" Style="{StaticResource NavButton}"/>
         <Button  Name="btnAdd"   Content="New Customer"  Command="{StaticResource AddCommand}" FontSize="11" Width="80" Style="{StaticResource NavButton}"/>
         <Button Content="New Order" Name="btnNewOrder" FontSize="11" Width="80" Style="{StaticResource NavButton}" Click="NewOrder_click"/>
         <Button Name="btnUpdate" Content="Commit" Command="{StaticResource UpdateCommand}" FontSize="11" Width="80" Style="{StaticResource NavButton}"/>
         <Button Content="Cancel" Name="btnCancel"  Command="{StaticResource CancelCommand}" FontSize="11" Width="80" Style="{StaticResource NavButton}"/>
     </StackPanel>
     <Grid x:Name="existingCustomerGrid" Grid.Row="1" HorizontalAlignment="Left" Margin="5" Visibility="Visible" VerticalAlignment="Top" Background="AntiqueWhite" DataContext="{StaticResource customerViewSource}">
         <Grid.ColumnDefinitions>
             <ColumnDefinition Width="Auto" MinWidth="233"/>
             <ColumnDefinition Width="Auto" MinWidth="397"/>
         </Grid.ColumnDefinitions>
         <Grid.RowDefinitions>
             <RowDefinition Height="Auto"/>
             <RowDefinition Height="Auto"/>
             <RowDefinition Height="Auto"/>
             <RowDefinition Height="Auto"/>
             <RowDefinition Height="Auto"/>
             <RowDefinition Height="Auto"/>
         </Grid.RowDefinitions>
         <Label Content="Customer ID:" Grid.Row="0" Style="{StaticResource Label}"/>
         <TextBox x:Name="customerIDTextBox"  Grid.Row="0" Style="{StaticResource CustTextBox}"
                  Text="{Binding CustomerID, Mode=TwoWay, NotifyOnValidationError=true, ValidatesOnExceptions=true}"/>
         <Label Content="Company Name:"  Grid.Row="1" Style="{StaticResource Label}"/>
         <TextBox x:Name="companyNameTextBox"  Grid.Row="1" Style="{StaticResource CustTextBox}"
                  Text="{Binding CompanyName, Mode=TwoWay, NotifyOnValidationError=true, ValidatesOnExceptions=true}"/>
         <Label Content="Contact Name:"  Grid.Row="2" Style="{StaticResource Label}"/>
         <TextBox x:Name="contactNameTextBox" Grid.Row="2" Style="{StaticResource CustTextBox}"
                  Text="{Binding ContactName, Mode=TwoWay, NotifyOnValidationError=true, ValidatesOnExceptions=true}"/>
         <Label Content="Contact Title:"  Grid.Row="3" Style="{StaticResource Label}"/>
         <TextBox x:Name="contactTitleTextBox" Grid.Row="3" Style="{StaticResource CustTextBox}"
                  Text="{Binding ContactTitle, Mode=TwoWay, NotifyOnValidationError=true, ValidatesOnExceptions=true}"/>
         <Label Content="Address:" Grid.Row="4" Style="{StaticResource Label}"/>
         <TextBox x:Name="addressTextBox" Grid.Row="4" Style="{StaticResource CustTextBox}"
                  Text="{Binding Address, Mode=TwoWay, NotifyOnValidationError=true, ValidatesOnExceptions=true}"/>
         <Label Content="City:" Grid.Column="1" Grid.Row="0"  Style="{StaticResource Label}"/>
         <TextBox x:Name="cityTextBox" Grid.Column="1" Grid.Row="0" Style="{StaticResource CustTextBox}"
                  Text="{Binding City, Mode=TwoWay, NotifyOnValidationError=true, ValidatesOnExceptions=true}"/>
         <Label Content="Country:" Grid.Column="1" Grid.Row="1" Style="{StaticResource Label}"/>
         <TextBox x:Name="countryTextBox" Grid.Column="1" Grid.Row="1" Style="{StaticResource CustTextBox}"
                  Text="{Binding Country, Mode=TwoWay, NotifyOnValidationError=true, ValidatesOnExceptions=true}"/>
         <Label Content="Fax:" Grid.Column="1" Grid.Row="2" Style="{StaticResource Label}"/>
         <TextBox x:Name="faxTextBox" Grid.Column="1" Grid.Row="2" Style="{StaticResource CustTextBox}"
                  Text="{Binding Fax, Mode=TwoWay, NotifyOnValidationError=true, ValidatesOnExceptions=true}"/>
         <Label Content="Phone:" Grid.Column="1" Grid.Row="3" Style="{StaticResource Label}"/>
         <TextBox x:Name="phoneTextBox" Grid.Column="1" Grid.Row="3" Style="{StaticResource CustTextBox}"
                  Text="{Binding Phone, Mode=TwoWay, NotifyOnValidationError=true, ValidatesOnExceptions=true}"/>
         <Label Content="Postal Code:" Grid.Column="1" Grid.Row="4" VerticalAlignment="Center" Style="{StaticResource Label}"/>
         <TextBox x:Name="postalCodeTextBox" Grid.Column="1" Grid.Row="4" Style="{StaticResource CustTextBox}"
                  Text="{Binding PostalCode, Mode=TwoWay, NotifyOnValidationError=true, ValidatesOnExceptions=true}"/>
         <Label Content="Region:" Grid.Column="1" Grid.Row="5" Style="{StaticResource Label}"/>
         <TextBox x:Name="regionTextBox" Grid.Column="1" Grid.Row="5" Style="{StaticResource CustTextBox}"
                  Text="{Binding Region, Mode=TwoWay, NotifyOnValidationError=true, ValidatesOnExceptions=true}"/>
     </Grid>
     <Grid x:Name="newCustomerGrid" Grid.Row="1" HorizontalAlignment="Left" VerticalAlignment="Top" Margin="5" DataContext="{Binding RelativeSource={RelativeSource FindAncestor, AncestorType={x:Type Window}}, Path=newCustomer, UpdateSourceTrigger=Explicit}" Visibility="Collapsed" Background="CornflowerBlue">
         <Grid.ColumnDefinitions>
             <ColumnDefinition Width="Auto" MinWidth="233"/>
             <ColumnDefinition Width="Auto" MinWidth="397"/>
         </Grid.ColumnDefinitions>
         <Grid.RowDefinitions>
             <RowDefinition Height="Auto"/>
             <RowDefinition Height="Auto"/>
             <RowDefinition Height="Auto"/>
             <RowDefinition Height="Auto"/>
             <RowDefinition Height="Auto"/>
             <RowDefinition Height="Auto"/>
         </Grid.RowDefinitions>
         <Label Content="Customer ID:" Grid.Row="0" Style="{StaticResource Label}"/>
         <TextBox x:Name="add_customerIDTextBox"  Grid.Row="0"  Style="{StaticResource CustTextBox}"
                  Text="{Binding CustomerID, Mode=TwoWay, NotifyOnValidationError=true, ValidatesOnExceptions=true}"/>
         <Label Content="Company Name:"  Grid.Row="1" Style="{StaticResource Label}"/>
         <TextBox x:Name="add_companyNameTextBox"  Grid.Row="1" Style="{StaticResource CustTextBox}"
                  Text="{Binding CompanyName, Mode=TwoWay, NotifyOnValidationError=true, ValidatesOnExceptions=true }"/>
         <Label Content="Contact Name:"  Grid.Row="2" Style="{StaticResource Label}"/>
         <TextBox x:Name="add_contactNameTextBox" Grid.Row="2" Style="{StaticResource CustTextBox}"
                  Text="{Binding ContactName, Mode=TwoWay, NotifyOnValidationError=true, ValidatesOnExceptions=true}"/>
         <Label Content="Contact Title:"  Grid.Row="3" Style="{StaticResource Label}"/>
         <TextBox x:Name="add_contactTitleTextBox" Grid.Row="3" Style="{StaticResource CustTextBox}"
                  Text="{Binding ContactTitle, Mode=TwoWay, NotifyOnValidationError=true, ValidatesOnExceptions=true}"/>
         <Label Content="Address:" Grid.Row="4" Style="{StaticResource Label}"/>
         <TextBox x:Name="add_addressTextBox" Grid.Row="4" Style="{StaticResource CustTextBox}"
                  Text="{Binding Address, Mode=TwoWay, NotifyOnValidationError=true, ValidatesOnExceptions=true}"/>
         <Label Content="City:" Grid.Column="1" Grid.Row="0"  Style="{StaticResource Label}"/>
         <TextBox x:Name="add_cityTextBox" Grid.Column="1" Grid.Row="0" Style="{StaticResource CustTextBox}"
                  Text="{Binding City, Mode=TwoWay, NotifyOnValidationError=true, ValidatesOnExceptions=true}"/>
         <Label Content="Country:" Grid.Column="1" Grid.Row="1" Style="{StaticResource Label}"/>
         <TextBox x:Name="add_countryTextBox" Grid.Column="1" Grid.Row="1" Style="{StaticResource CustTextBox}"
                  Text="{Binding Country, Mode=TwoWay, NotifyOnValidationError=true, ValidatesOnExceptions=true}"/>
         <Label Content="Fax:" Grid.Column="1" Grid.Row="2" Style="{StaticResource Label}"/>
         <TextBox x:Name="add_faxTextBox" Grid.Column="1" Grid.Row="2" Style="{StaticResource CustTextBox}"
                  Text="{Binding Fax, Mode=TwoWay, NotifyOnValidationError=true, ValidatesOnExceptions=true}"/>
         <Label Content="Phone:" Grid.Column="1" Grid.Row="3" Style="{StaticResource Label}"/>
         <TextBox x:Name="add_phoneTextBox" Grid.Column="1" Grid.Row="3" Style="{StaticResource CustTextBox}"
                  Text="{Binding Phone, Mode=TwoWay, NotifyOnValidationError=true, ValidatesOnExceptions=true}"/>
         <Label Content="Postal Code:" Grid.Column="1" Grid.Row="4" VerticalAlignment="Center" Style="{StaticResource Label}"/>
         <TextBox x:Name="add_postalCodeTextBox" Grid.Column="1" Grid.Row="4" Style="{StaticResource CustTextBox}"
                  Text="{Binding PostalCode, Mode=TwoWay, NotifyOnValidationError=true, ValidatesOnExceptions=true}"/>
         <Label Content="Region:" Grid.Column="1" Grid.Row="5" Style="{StaticResource Label}"/>
         <TextBox x:Name="add_regionTextBox" Grid.Column="1" Grid.Row="5" Style="{StaticResource CustTextBox}"
                  Text="{Binding Region, Mode=TwoWay, NotifyOnValidationError=true, ValidatesOnExceptions=true}"/>
     </Grid>
     <Grid x:Name="newOrderGrid" Grid.Row="1" HorizontalAlignment="Left" VerticalAlignment="Top" Margin="5" DataContext="{Binding Path=newOrder, Mode=TwoWay}" Visibility="Collapsed" Background="LightGreen">
         <Grid.ColumnDefinitions>
             <ColumnDefinition Width="Auto" MinWidth="233"/>
             <ColumnDefinition Width="Auto" MinWidth="397"/>
         </Grid.ColumnDefinitions>
         <Grid.RowDefinitions>
             <RowDefinition Height="Auto"/>
             <RowDefinition Height="Auto"/>
             <RowDefinition Height="Auto"/>
             <RowDefinition Height="Auto"/>
             <RowDefinition Height="Auto"/>
             <RowDefinition Height="Auto"/>
             <RowDefinition Height="Auto"/>
         </Grid.RowDefinitions>
         <Label Content="New Order Form" FontWeight="Bold"/>
         <Label Content="Employee ID:"  Grid.Row="1" Style="{StaticResource Label}"/>
         <TextBox x:Name="add_employeeIDTextBox" Grid.Row="1" Style="{StaticResource CustTextBox}"
                  Text="{Binding EmployeeID, Mode=TwoWay, NotifyOnValidationError=true, ValidatesOnExceptions=true}"/>
         <Label Content="Order Date:"  Grid.Row="2" Style="{StaticResource Label}"/>
         <DatePicker x:Name="add_orderDatePicker" Grid.Row="2"  HorizontalAlignment="Right" Width="120"
                 SelectedDate="{Binding OrderDate, Mode=TwoWay, NotifyOnValidationError=true, ValidatesOnExceptions=true, UpdateSourceTrigger=PropertyChanged}"/>
         <Label Content="Required Date:" Grid.Row="3" Style="{StaticResource Label}"/>
         <DatePicker x:Name="add_requiredDatePicker" Grid.Row="3" HorizontalAlignment="Right" Width="120"
                  SelectedDate="{Binding RequiredDate, Mode=TwoWay, NotifyOnValidationError=true, ValidatesOnExceptions=true, UpdateSourceTrigger=PropertyChanged}"/>
         <Label Content="Shipped Date:"  Grid.Row="4"  Style="{StaticResource Label}"/>
         <DatePicker x:Name="add_shippedDatePicker"  Grid.Row="4"  HorizontalAlignment="Right" Width="120"
                 SelectedDate="{Binding ShippedDate, Mode=TwoWay, NotifyOnValidationError=true, ValidatesOnExceptions=true, UpdateSourceTrigger=PropertyChanged}"/>
         <Label Content="Ship Via:"  Grid.Row="5" Style="{StaticResource Label}"/>
         <TextBox x:Name="add_ShipViaTextBox"  Grid.Row="5" Style="{StaticResource CustTextBox}"
                  Text="{Binding ShipVia, Mode=TwoWay, NotifyOnValidationError=true, ValidatesOnExceptions=true}"/>
         <Label Content="Freight"  Grid.Row="6" Style="{StaticResource Label}"/>
         <TextBox x:Name="add_freightTextBox" Grid.Row="6" Style="{StaticResource CustTextBox}"
                  Text="{Binding Freight, Mode=TwoWay, NotifyOnValidationError=true, ValidatesOnExceptions=true}"/>
     </Grid>
     <DataGrid x:Name="ordersDataGrid" SelectionUnit="Cell" SelectionMode="Single" AutoGenerateColumns="False" CanUserAddRows="false" IsEnabled="True" EnableRowVirtualization="True" Width="auto" ItemsSource="{Binding Source={StaticResource customerOrdersViewSource}}" Margin="10,10,10,10" Grid.Row="2" RowDetailsVisibilityMode="VisibleWhenSelected">
         <DataGrid.Columns>
             <DataGridTemplateColumn>
                 <DataGridTemplateColumn.CellTemplate>
                     <DataTemplate>
                         <Button Content="Delete"  Command="{StaticResource DeleteOrderCommand}" CommandParameter="{Binding}"/>
                     </DataTemplate>
                 </DataGridTemplateColumn.CellTemplate>
             </DataGridTemplateColumn>
             <DataGridTextColumn x:Name="customerIDColumn" Binding="{Binding CustomerID}" Header="Customer ID" Width="SizeToHeader"/>
             <DataGridTextColumn x:Name="employeeIDColumn" Binding="{Binding EmployeeID}" Header="Employee ID" Width="SizeToHeader"/>
             <DataGridTextColumn x:Name="freightColumn" Binding="{Binding Freight}" Header="Freight" Width="SizeToHeader"/>
             <DataGridTemplateColumn x:Name="orderDateColumn" Header="Order Date" Width="SizeToHeader">
                 <DataGridTemplateColumn.CellTemplate>
                     <DataTemplate>
                         <DatePicker SelectedDate="{Binding OrderDate, Mode=TwoWay, NotifyOnValidationError=true, ValidatesOnExceptions=true, UpdateSourceTrigger=PropertyChanged}"/>
                     </DataTemplate>
                 </DataGridTemplateColumn.CellTemplate>
             </DataGridTemplateColumn>
             <DataGridTextColumn x:Name="orderIDColumn" Binding="{Binding OrderID}" Header="Order ID" Width="SizeToHeader"/>
             <DataGridTemplateColumn x:Name="requiredDateColumn" Header="Required Date" Width="SizeToHeader">
                 <DataGridTemplateColumn.CellTemplate>
                     <DataTemplate>
                         <DatePicker SelectedDate="{Binding RequiredDate, Mode=TwoWay, NotifyOnValidationError=true, ValidatesOnExceptions=true, UpdateSourceTrigger=PropertyChanged}"/>
                     </DataTemplate>
                 </DataGridTemplateColumn.CellTemplate>
             </DataGridTemplateColumn>
             <DataGridTextColumn x:Name="shipAddressColumn" Binding="{Binding ShipAddress}" Header="Ship Address" Width="SizeToHeader"/>
             <DataGridTextColumn x:Name="shipCityColumn" Binding="{Binding ShipCity}" Header="Ship City" Width="SizeToHeader"/>
             <DataGridTextColumn x:Name="shipCountryColumn" Binding="{Binding ShipCountry}" Header="Ship Country" Width="SizeToHeader"/>
             <DataGridTextColumn x:Name="shipNameColumn" Binding="{Binding ShipName}" Header="Ship Name" Width="SizeToHeader"/>
             <DataGridTemplateColumn x:Name="shippedDateColumn" Header="Shipped Date" Width="SizeToHeader">
                 <DataGridTemplateColumn.CellTemplate>
                     <DataTemplate>
                         <DatePicker SelectedDate="{Binding ShippedDate, Mode=TwoWay, NotifyOnValidationError=true, ValidatesOnExceptions=true, UpdateSourceTrigger=PropertyChanged}"/>
                     </DataTemplate>
                 </DataGridTemplateColumn.CellTemplate>
             </DataGridTemplateColumn>
             <DataGridTextColumn x:Name="shipPostalCodeColumn" Binding="{Binding ShipPostalCode}" Header="Ship Postal Code" Width="SizeToHeader"/>
             <DataGridTextColumn x:Name="shipRegionColumn" Binding="{Binding ShipRegion}" Header="Ship Region" Width="SizeToHeader"/>
             <DataGridTextColumn x:Name="shipViaColumn" Binding="{Binding ShipVia}" Header="Ship Via" Width="SizeToHeader"/>
         </DataGrid.Columns>
     </DataGrid>
 </Grid>
```

## <a name="add-buttons-to-navigate-add-update-and-delete"></a>Hinzufügen von Schaltflächen zum Navigieren, hinzufügen, aktualisieren und löschen
 In Windows Forms-Anwendungen erhalten Sie ein BindingNavigator-Objekt mit Schaltflächen, mit denen Sie durch Zeilen in einer Datenbank navigieren und grundlegende CRUD-Vorgänge ausführen können. WPF stellt keinen BindingNavigator bereit, Sie sind jedoch leicht zu erstellen. Dies geschieht mit Schaltflächen in einem horizontalen StackPanel in der unteren Zeile des Seiten Rasters, und wir ordnen die Schaltflächen den Befehlen zu, die an Methoden im Code Behind gebunden sind.

 Es gibt Teile der Befehls Logik: (1) die Befehle, (2) die Bindungen, (3) die Schaltflächen und (4) die Befehls Handler im Code-Behind.

#### <a name="add-commands-bindings-and-buttons-in-xaml"></a>Hinzufügen von Befehlen, Bindungen und Schaltflächen in XAML

1. Fügen Sie zunächst die Befehle in der Datei "MainWindow. XAML" im Windows. Resources-Element hinzu:

    ```xaml

     <RoutedUICommand x:Key="FirstCommand" Text="First"/>
    <RoutedUICommand x:Key="LastCommand" Text="Last"/>
    <RoutedUICommand x:Key="NextCommand" Text="Next"/>
    <RoutedUICommand x:Key="PreviousCommand" Text="Previous"/>
    <RoutedUICommand x:Key="DeleteCustomerCommand" Text="Delete Customer"/>
    <RoutedUICommand x:Key="DeleteOrderCommand" Text="Delete Order"/>
    <RoutedUICommand x:Key="UpdateCommand" Text="Update"/>
    <RoutedUICommand x:Key="AddCommand" Text="Add"/>
    <RoutedUICommand x:Key="CancelCommand" Text="Cancel"/>
    ```

2. Eine CommandBinding ordnet ein RoutedUICommand-Ereignis einer Methode im Code Behind zu. Fügen Sie dieses CommandBinding-Element nach dem schließenden Windows. Resources-Tag hinzu:

    ```xaml

        <Window.CommandBindings>
        <CommandBinding Command="{StaticResource FirstCommand}" Executed="FirstCommandHandler"/>
        <CommandBinding Command="{StaticResource LastCommand}" Executed="LastCommandHandler"/>
        <CommandBinding Command="{StaticResource NextCommand}" Executed="NextCommandHandler"/>
        <CommandBinding Command="{StaticResource PreviousCommand}" Executed="PreviousCommandHandler"/>
        <CommandBinding Command="{StaticResource DeleteCustomerCommand}" Executed="DeleteCustomerCommandHandler"/>
        <CommandBinding Command="{StaticResource DeleteOrderCommand}" Executed="DeleteOrderCommandHandler"/>
        <CommandBinding Command="{StaticResource UpdateCommand}" Executed="UpdateCommandHandler"/>
        <CommandBinding Command="{StaticResource AddCommand}" Executed="AddCommandHandler"/>
        <CommandBinding Command="{StaticResource CancelCommand}" Executed="CancelCommandHandler"/>
    </Window.CommandBindings>
    ```

3. Nun fügen wir den StackPanel mit den Schaltflächen Navigation, hinzufügen, löschen und aktualisieren hinzu. Fügen Sie dieser Art zunächst "Windows. Resources" hinzu:

    ```xaml
    <Style x:Key="NavButton" TargetType="{x:Type Button}" BasedOn="{x:Null}">
        <Setter Property="FontSize" Value="24"/>
        <Setter Property="FontFamily" Value="Segoe UI Symbol"/>
        <Setter Property="Margin" Value="2,2,2,0"/>
        <Setter Property="Width" Value="40"/>
        <Setter Property="Height" Value="auto"/>
    </Style>
    ```

     Fügen Sie nun diesen Code direkt nach den rowdefinitionen für das äußere Raster Element an den Anfang der XAML-Seite ein:

    ```xaml
    <StackPanel  Orientation="Horizontal" Margin="2,2,2,0" Height="36" VerticalAlignment="Top" Background="Gainsboro" DataContext="{StaticResource customerViewSource}" d:LayoutOverrides="LeftMargin, RightMargin, TopMargin, BottomMargin">
        <Button Name="btnFirst" Content="|◄" Command="{StaticResource FirstCommand}" Style="{StaticResource NavButton}"  />
        <Button Name="btnPrev"  Content="◄" Command="{StaticResource PreviousCommand}" Style="{StaticResource NavButton}"/>
        <Button Name="btnNext"  Content="►" Command="{StaticResource NextCommand}"     Style="{StaticResource NavButton}"/>
        <Button Name="btnLast"  Content="►|" Command="{StaticResource LastCommand}" Style="{StaticResource NavButton}"/>
        <Button Name="btnDelete" Content="Delete Customer" Command="{StaticResource DeleteCustomerCommand}" FontSize="11" Width="120" Style="{StaticResource NavButton}"/>
        <Button  Name="btnAdd"   Content="New Customer"  Command="{StaticResource AddCommand}" FontSize="11" Width="80" Style="{StaticResource NavButton}"/>
        <Button Content="New Order" Name="btnNewOrder" FontSize="11" Width="80" Style="{StaticResource NavButton}" Click="NewOrder_click"/>
        <Button Name="btnUpdate" Content="Commit" Command="{StaticResource UpdateCommand}" FontSize="11" Width="80" Style="{StaticResource NavButton}"/>
        <Button Content="Cancel" Name="btnCancel"  Command="{StaticResource CancelCommand}" FontSize="11" Width="80" Style="{StaticResource NavButton}"/>
    </StackPanel>
    ```

#### <a name="add-command-handlers-to-the-mainwindow-class"></a>Hinzufügen von Befehls Handlern zur MainWindow-Klasse

1. Der Code Behind ist nur minimal, mit Ausnahme der Add-und Delete-Methoden. Beachten Sie, dass die Navigation durch Aufrufen von Methoden für die View-Eigenschaft von CollectionViewSource erfolgt. Der deleteordercommandhandler zeigt, wie ein Lösch Löschvorgang in einer Reihenfolge durchgeführt wird. Wir müssen zunächst die Order_Details löschen, die ihr zugeordnet sind. Der Update CommandHandler fügt der Sammlung einen neuen Kunden hinzu oder aktualisiert das vorhandene Objekt mit den Änderungen, die der Benutzer in den Textfeldern vorgenommen hat.

2. Fügen Sie diese Handlermethoden der MainWindow-Klasse in MainWindow.XAML.cs hinzu, wenn Ihre CollectionViewSource für die Customers-Tabelle einen anderen Namen aufweist, müssen Sie den Namen in jeder der folgenden Methoden anpassen:

    ```csharp
       private void LastCommandHandler(object sender, ExecutedRoutedEventArgs e)
    {
        custViewSource.View.MoveCurrentToLast();
    }

    private void PreviousCommandHandler(object sender, ExecutedRoutedEventArgs e)
    {
        custViewSource.View.MoveCurrentToPrevious();
    }

    private void NextCommandHandler(object sender, ExecutedRoutedEventArgs e)
    {
        custViewSource.View.MoveCurrentToNext();
    }

    private void FirstCommandHandler(object sender, ExecutedRoutedEventArgs e)
    {
        custViewSource.View.MoveCurrentToFirst();
    }

    private void DeleteCustomerCommandHandler(object sender, ExecutedRoutedEventArgs e)
    {
        // If existing window is visible, then delete the customer and all their orders.
        // In a real application, you should add warnings and allow a user to cancel the operation.
        var cur = custViewSource.View.CurrentItem as Customer;

        var cust = (from c in context.Customers
                    where c.CustomerID == cur.CustomerID
                    select c).FirstOrDefault();

        if (cust != null)
        {
            foreach (var ord in cust.Orders.ToList())
            {
                Delete_Order(ord);
            }
            context.Customers.Remove(cust);
        }
        context.SaveChanges();
        custViewSource.View.Refresh();
    }

    // Commit changes from the new customer form, the new order form,
    // or edits made to the existing customer form.
    private void UpdateCommandHandler(object sender, ExecutedRoutedEventArgs e)
    {
        if (newCustomerGrid.IsVisible)
        {
            // Create a new object because the old one
            // is being tracked by EF now.
            newCustomer = new Customer();
            newCustomer.Address = add_addressTextBox.Text;
            newCustomer.City = add_cityTextBox.Text;
            newCustomer.CompanyName = add_companyNameTextBox.Text;
            newCustomer.ContactName = add_contactNameTextBox.Text;
            newCustomer.ContactTitle = add_contactTitleTextBox.Text;
            newCustomer.Country = add_countryTextBox.Text;
            newCustomer.CustomerID = add_customerIDTextBox.Text;
            newCustomer.Fax = add_faxTextBox.Text;
            newCustomer.Phone = add_phoneTextBox.Text;
            newCustomer.PostalCode = add_postalCodeTextBox.Text;
            newCustomer.Region = add_regionTextBox.Text;

            // Perform very basic validation
            if (newCustomer.CustomerID.Length == 5)
            {
                // Insert the new customer at correct position:
                int len = context.Customers.Local.Count();
                int pos = len;
                for (int i = 0; i < len; ++i)
                {
                    if (String.CompareOrdinal(newCustomer.CustomerID, context.Customers.Local[i].CustomerID) < 0)
                    {
                        pos = i;
                        break;
                    }
                }
                context.Customers.Local.Insert(pos, newCustomer);
                custViewSource.View.Refresh();
                custViewSource.View.MoveCurrentTo(newCustomer);
            }
            else
            {
                MessageBox.Show("CustomerID must have 5 characters.");
            }

            newCustomerGrid.Visibility = Visibility.Collapsed;
            existingCustomerGrid.Visibility = Visibility.Visible;
        }
        else if (newOrderGrid.IsVisible)
        {
            // Order ID is auto-generated so we don't set it here.
            // For CustomerID, address, etc we use the values from current customer.
            // User can modify these in the datagrid after the order is entered.

            newOrder.OrderDate = add_orderDatePicker.SelectedDate;
            newOrder.RequiredDate = add_requiredDatePicker.SelectedDate;
            newOrder.ShippedDate = add_shippedDatePicker.SelectedDate;
            try
            {
                // Exercise for the reader if you are using Northwind:
                // Add the Northwind Shippers table to the model.
                // Acceptable ShipperID values are 1, 2, or 3.
                if (add_ShipViaTextBox.Text == "1" || add_ShipViaTextBox.Text == "2"
                    || add_ShipViaTextBox.Text == "3")
                {
                    newOrder.ShipVia = Convert.ToInt32(add_ShipViaTextBox.Text);
                }
                else
                {
                    MessageBox.Show("Shipper ID must be 1, 2, or 3 in Northwind.");
                    return;
                }
            }
            catch
            {
                MessageBox.Show("Ship Via must be convertible to int");
                return;
            }
            try
            {
                newOrder.Freight = Convert.ToDecimal(add_freightTextBox.Text);
            }
            catch
            {
                MessageBox.Show("Freight must be convertible to decimal.");
                return;
            }

            // Add the order into the EF model
            context.Orders.Add(newOrder);
            ordViewSource.View.Refresh();
        }

        // Save the changes, either for a new customer, a new order
        // or an edit in an existing customer or order
        context.SaveChanges();
    }

    // Sets up the form so that user can enter data. Data is later
    // saved when user clicks Commit.
    private void AddCommandHandler(object sender, ExecutedRoutedEventArgs e)
    {
        existingCustomerGrid.Visibility = Visibility.Collapsed;
        newOrderGrid.Visibility = Visibility.Collapsed;
        newCustomerGrid.Visibility = Visibility.Visible;

        // Clear all the text boxes before adding a new customer.
        foreach (var child in newCustomerGrid.Children)
        {
            var tb = child as TextBox;
            if (tb != null)
            {
                tb.Text = "";
            }
        }
    }

    private void NewOrder_click(object sender, RoutedEventArgs e)
    {
        var cust = custViewSource.View.CurrentItem as Customer;
        if (cust == null)
        {
            MessageBox.Show("No customer selected.");
            return;
        }

        newOrder.CustomerID = cust.CustomerID;

        // Get address and other mostly constant fields from
        // an existing order, if one exists
        var coll = custViewSource.Source as IEnumerable<Customer>;
        var lastOrder = (from c in coll
                         from ord in c.Orders
                         select ord).LastOrDefault();
        if (lastOrder != null)
        {
            newOrder.ShipAddress = lastOrder.ShipAddress;
            newOrder.ShipCity = lastOrder.ShipCity;
            newOrder.ShipCountry = lastOrder.ShipCountry;
            newOrder.ShipName = lastOrder.ShipName;
            newOrder.ShipPostalCode = lastOrder.ShipPostalCode;
            newOrder.ShipRegion = lastOrder.ShipRegion;
        }

        existingCustomerGrid.Visibility = Visibility.Collapsed;
        newCustomerGrid.Visibility = Visibility.Collapsed;
        newOrderGrid.UpdateLayout();
        newOrderGrid.Visibility = Visibility.Visible;
    }

    // Cancels any input into the new customer form
    private void CancelCommandHandler(object sender, ExecutedRoutedEventArgs e)
    {
        add_addressTextBox.Text = "";
        add_cityTextBox.Text = "";
        add_companyNameTextBox.Text = "";
        add_contactNameTextBox.Text = "";
        add_contactTitleTextBox.Text = "";
        add_countryTextBox.Text = "";
        add_customerIDTextBox.Text = "";
        add_faxTextBox.Text = "";
        add_phoneTextBox.Text = "";
        add_postalCodeTextBox.Text = "";
        add_regionTextBox.Text = "";

        existingCustomerGrid.Visibility = Visibility.Visible;
        newCustomerGrid.Visibility = Visibility.Collapsed;
        newOrderGrid.Visibility = Visibility.Collapsed;
    }

    private void Delete_Order(Order order)
    {
        // Find the order in the EF model.
        var ord = (from o in context.Orders.Local
                   where o.OrderID == order.OrderID
                   select o).FirstOrDefault();

        // Delete all the order_details that have
        // this Order as a foreign key
        foreach (var detail in ord.Order_Details.ToList())
        {
            context.Order_Details.Remove(detail);
        }

        // Now it's safe to delete the order.
        context.Orders.Remove(ord);
        context.SaveChanges();

        // Update the data grid.
        ordViewSource.View.Refresh();
    }

    private void DeleteOrderCommandHandler(object sender, ExecutedRoutedEventArgs e)
    {
        // Get the Order in the row in which the Delete button was clicked.
        Order obj = e.Parameter as Order;
        Delete_Order(obj);
    }
    ```

3. Drücken Sie **F5**. Ihre Daten sollten angezeigt werden, und die Navigations Schaltflächen sollten erwartungsgemäß funktionieren. Klicken Sie auf "Commit", um dem Modell einen neuen Kunden hinzuzufügen, nachdem Sie die Daten eingegeben haben.  Klicken Sie auf "Abbrechen", um ein neues Kunden-oder neues Bestellformular zu sichern, ohne zu speichern. Sie können Änderungen an vorhandenen Kunden und Aufträgen direkt in den Textfeldern vornehmen, und diese Änderungen werden automatisch in das Modell geschrieben.

## <a name="see-also"></a>Siehe auch
 Dokumentation [zu Visual Studio Data Tools für .net](../data-tools/visual-studio-data-tools-for-dotnet.md) [Entity Framework](https://msdn.microsoft.com/data/ee712907.aspx)
