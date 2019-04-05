---
title: Erstellen eine einfachen datenanwendung mit WPF und Entity Framework 6 | Microsoft-Dokumentation
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-data-tools
ms.topic: conceptual
ms.assetid: 65929fab-5d78-4e04-af1e-cf4957f230f6
caps.latest.revision: 25
author: gewarren
ms.author: gewarren
manager: jillfra
ms.openlocfilehash: 56c211597e99689e1ad263cfe12d7dafdf3cf5cc
ms.sourcegitcommit: d3a485d47c6ba01b0fc9878cbbb7fe88755b29af
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 03/19/2019
ms.locfileid: "59001557"
---
# <a name="create-a-simple-data-application-with-wpf-and-entity-framework-6"></a>Erstellen einer einfachen Datenanwendung mit WPF und Entity Framework 6
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

  
Dieser exemplarischen Vorgehensweise wird gezeigt, wie eine grundlegende "Forms over Data"-Anwendung in Visual Studio mit SQL Server LocalDB, die Northwind-Datenbank, Entity Framework 6 und Windows Presentation Foundation erstellt wird. Es zeigt, wie Sie einfache Datenbindung mit einer Master / Detail-Ansicht, und sie hat auch einen benutzerdefinierten "Bindung Navigator" mit Schaltflächen für die "Nächste verschieben", "Vorherige verschieben," "Wechseln zu beginnen," "Wechseln zu beenden," "Update" und "Delete".  
  
 Dieser Artikel konzentriert sich auf das Verwenden von Datentools in Visual Studio, und versucht nicht, erläutern die zugrunde liegenden Technologien in jeder beliebigen Tiefe. Es wird davon ausgegangen, dass Sie über grundlegende Kenntnisse von XAML, Entity Framework und SQL verfügen. In diesem Beispiel wird auch nicht MVVM-Architektur veranschaulicht die standardmäßigen für WPF-Anwendungen ist. Allerdings können Sie diesen Code in Ihren eigenen MVVM-Anwendung mit sehr wenigen Änderungen kopieren.  
  
## <a name="install-and-connect-to-northwind"></a>Installieren und Verbinden mit Northwind  
 Dieses Beispiel verwendet die SQL Server Express LocalDB und der Beispieldatenbank Northwind. Es sollte auch für andere Produkte der SQL-Datenbank funktionieren, wenn Sie der ADO.NET-Datenanbieter für dieses Produkt Entity Framework unterstützt.  
  
1.  Wenn Sie noch nicht geschehen, installieren Sie SQL Server 2014 LocalDB Express 32-bit-aus der [Downloadseite für SQL Server-Editionen](https://www.microsoft.com/sql-server/sql-server-editions-express).  
  
2.  Installieren Sie die Northwind-Beispieldatenbank, indem Sie die Anweisungen befolgen: [Installieren von SQL Server-Beispieldatenbanken](../data-tools/install-sql-server-sample-databases.md).  
  
3.  [Hinzufügen von neuen Verbindungen](../data-tools/add-new-connections.md) für Northwind.  
  
## <a name="configure-the-project"></a>Konfigurieren des Projekts  
  
1.  Wählen Sie in Visual Studio **Datei &#124; neues Projekt** und erstellen Sie eine neue C#-WPF-Anwendung.  
  
2.  Als Nächstes fügen wir das NuGet-Paket für Entity Framework 6. Wählen Sie im Projektmappen-Explorer den Projektknoten aus. Wählen Sie im Hauptmenü **Projekt &#124; NuGet-Pakete verwalten...**  
  
     ![Verwalten von NuGet-Pakete-Menüelement](../data-tools/media/raddata-vs2015-manage-nuget-packages.png "raddata_vs2015_manage_nuget_packages")  
  
3.  Im NuGet-Paket-Manager, klicken Sie auf die **Durchsuchen** Link. Entitätsframework ist wahrscheinlich das oberste Paket in der Liste aus. Klicken Sie auf **installieren** im rechten Bereich und den aufforderungen folgen. Das Fenster "Ausgabe" informiert Sie, wenn die Installation abgeschlossen ist.  
  
     ![Entity Framework-NuGet-Pakets](../data-tools/media/raddata-vs2015-nuget-ef.png "raddata_vs2015_Nuget_EF")  
  
4.  Jetzt können wir Visual Studio verwenden, um ein Modell basierend auf der Northwind-Datenbank zu erstellen.  
  
## <a name="create-the-model"></a>Erstellen des Modells  
  
1. Klicken Sie mit der rechten Maustaste auf den Projektknoten im Projektmappen-Explorer, und wählen Sie **hinzufügen &#124; neues Element**. Wählen Sie im linken Bereich unter dem C#-Knoten **Daten** , und wählen Sie im mittleren Bereich **ADO.NET Entity Data Model**.  
  
    ![Entity Framework Model Elemente bei neuen Projekten](../data-tools/media/raddata-ef-new-project-item.png "Raddata EF Elemente bei neuen Projekten")  
  
2. Rufen Sie das Modell `Northwind_model` und wählen Sie OK. Dadurch wird die **Entity Data Model-Assistenten**. Wählen Sie **EF Designer aus Datenbank** , und klicken Sie dann auf **Weiter**.  
  
    ![EF-Modell aus der Datenbank](../data-tools/media/raddata-ef-model-from-database.png "Raddata EF-Modell aus der Datenbank")  
  
3. Wählen Sie im nächsten Bildschirm Ihre LocalDB Northwind-Verbindung, und klicken Sie auf **Weiter**.  
  
4. In der nächsten Seite des Assistenten wählen wir die Tabellen, gespeicherte Prozeduren und andere Datenbankobjekte in das Entity Framework-Modell eingeschlossen werden sollen. Erweitern Sie den Knoten "Dbo" in der Strukturansicht angezeigt, und wählen Sie Kunden, Bestellungen und Bestelldetails. Lassen Sie die Standardeinstellungen unverändert, und klicken Sie auf **Fertig stellen**.  
  
    ![Wählen Sie Datenbankobjekte aus, für das Modell](../data-tools/media/raddata-choose-ef-objects.png "EF Objekte, die Raddata auswählen")  
  
5. Der Assistent generiert der c#-Klassen, die das Entity Framework-Modell darstellen. Hierbei handelt es sich um plain old C#-Klassen aus, und sie sind, was wir wird Databind der WPF-Benutzeroberfläche. Die EDMX-Datei beschreibt die Beziehungen und anderen Metadaten, die Objekte in der Datenbank die Klassen zugeordnet.  Die TT-Dateien sind T4-Vorlagen, die den Code zu generieren, die das Modell verarbeiten und speichern Sie Änderungen an der Datenbank. Sie können alle diese Dateien im Projektmappen-Explorer unter dem Knoten Northwind_model sehen:  
  
    ![Projektmappen-Explorer EF-Modelldateien](../data-tools/media/raddata-solution-explorer-ef-model-files.png "Raddata Projektmappen-Explorer EF-Model-Dateien")  
  
    Die Oberfläche des Designers für die EDMX-Datei können Sie einige Eigenschaften und Beziehungen im Modell zu ändern. Wir werden nicht in dieser exemplarischen Vorgehensweise den Designer zu verwenden.  
  
6. Die TT-Dateien sind allgemeine, aber wir benötigen, Optimieren Sie eine der sie mit der WPF-Datenbindung, funktionieren die ObservableCollections erforderlich ist.  Erweitern Sie im Projektmappen-Explorer die Northwind_model-Knoten, bis Sie Northwind_model.tt gefunden. (Stellen Sie sicher, dass **nicht** in den *. Kontext TT-Datei handelt es sich direkt unterhalb der EDMX-Datei).  
  
   -   Ersetzen Sie die zwei Vorkommen des <xref:System.Collections.ICollection> mit <xref:System.Collections.ObjectModel.ObservableCollection%601>.  
  
   -   Ersetzen Sie das erste Vorkommen des <xref:System.Collections.Generic.HashSet%601> mit <xref:System.Collections.ObjectModel.ObservableCollection%601> der Nähe von Zeile 51. Das zweite Vorkommen der HashSet nicht ersetzen  
  
   -   Ersetzen Sie dies das einzige Vorkommen <xref:System.Collections.Generic> (Nähe von Zeile 334) mit <xref:System.Collections.ObjectModel>.  
  
7. Drücken Sie **STRG + UMSCHALT + B** zum Erstellen des Projekts. Wenn der Build abgeschlossen ist, sind die Modellklassen des Datenquellen-Assistenten angezeigt.  
  
   Nun können wir dieses Modell auf der Seite "XAML" verknüpft, damit wir anzeigen, navigieren und die Daten ändern können.  
  
## <a name="databind-the-model-to-the-xaml-page"></a>DataBind das Modell, das die XAML-Seite  
 Es ist möglich, einen eigenen Databinding-Code schreiben, aber es ist viel einfacher, Visual Studio, die es für Sie erledigen können.  
  
1.  Wählen Sie im Hauptmenü **Projekt &#124; neue Datenquelle hinzufügen** um die **Assistenten zur Datenquellenkonfiguration**. Wählen Sie **Objekt** da an die Modellklassen, nicht auf die Datenbank gebunden sind:  
  
     ![Assistenten zur Datenquellenkonfiguration mit Objektquelle](../data-tools/media/raddata-data-source-configuration-wizard-with-object-source.png "Raddata Assistenten zur Datenquellenkonfiguration mit Objektquelle")  
  
2.  Wählen Sie die Kunden.  (Quellen für Aufträge werden automatisch aus der Orders-Navigationseigenschaft im Hinblick auf generiert werden.)  
  
     ![Hinzufügen von Entitätsklassen als Datenquellen](../data-tools/media/raddata-add-entity-classes-as-data-sources.png "Raddata Entität hinzufügen Klassen als Datenquellen")  
  
3.  Klicken Sie auf **Fertig stellen**  
  
4.  Navigieren Sie zu "MainWindow.xaml" in der Codeansicht. Wir werden das XAML für die Zwecke dieses Beispiels sehr einfach zu halten. Ändern Sie den Titel der MainWindow-Element in einen aussagekräftigeren und erhöhen Sie seine Höhe und Breite auf 600 x 800-vorerst zu. Sie können es später jederzeit ändern. Fügen Sie jetzt diese drei Zeilendefinitionen zum Hauptraster, eine Zeile für die Navigationsschaltflächen, eine für die Details des Kunden, eine für das Raster, das zeigt, deren Bestellungen hinzu:  
  
    ```xaml  
    <Grid.RowDefinitions>  
               <RowDefinition Height="auto"/>  
               <RowDefinition Height="auto"/>  
               <RowDefinition Height="*"/>  
           </Grid.RowDefinitions>  
    ```  
  
5.  Öffnen Sie jetzt "MainWindow.xaml" auf, sodass Sie es im Designer anzeigen. Dadurch wird das Fenster Datenquellen als eine Option am Rand des Visual Studio-Fenster neben der Toolbox angezeigt werden. Klicken Sie auf die Registerkarte, um das Fenster öffnen, oder klicken andernfalls **Umschalt + Alt + D** oder **Ansicht &#124; Other Windows &#124; Datenquellen**. Wir werden auf jede Eigenschaft in der Kunden-Klasse in einem eigenen benutzerdefinierten Text-Feld angezeigt. Zunächst klicken Sie auf den Pfeil in das Kombinationsfeld für Kunden, und wählen Sie **Details**. Ziehen Sie die Knoten auf den mittleren Teil der Entwurfsoberfläche, damit der Designer weiß, dass Sie in der mittleren Zeile wechseln soll.  Wenn Sie es vergessen haben, können Sie die Zeile zu einem späteren Zeitpunkt manuell in die XAML angeben. Standardmäßig werden die Steuerelemente vertikal in einem Grid-Element platziert, aber an diesem Punkt können angeordnet werden, werden beliebig auf dem Formular.  Beispielsweise kann es sinnvoll, platzieren das Textfeld am oberen Rand oberhalb der Adresse. Die beispielanwendung für diesen Artikel ordnet die Felder, und diese in zwei Spalten sortiert werden.  
  
     ![Kunden datenquellenbindung in einzelne Steuerelemente](../data-tools/media/raddata-customers-data-source-binding-to-individual-controls.png "Raddata Kunden datenquellenbindung in einzelne Steuerelemente")  
  
     In der Codeansicht, Sie sehen nun eine neue `Grid` Element in Zeile 1 (die mittlere Zeile) des übergeordneten Rasters. Das übergeordnete Element, das Raster enthält ein `DataContext` Attribut, das eine Bindung zu CollectionViewSource verweist, die hinzugefügt wurde die `Windows.Resources` Element. Bei der das erste Textfeld, z. B. diesen Datenkontext zugewiesen an "dieses Namens"Address"zugeordnet ist die `Address` Eigenschaft in der aktuellen `Customer` Objekt in die CollectionViewSource.  
  
    ```xaml  
    <Grid DataContext="{StaticResource customerViewSource}">  
    ```  
  
6.  Wenn ein Kunde in der oberen Hälfte des Fensters sichtbar ist, möchten wir ihre Bestellungen in der unteren Hälfte angezeigt. Wir zeigen die Aufträge in einem einzelnen Grid-Steuerelement. Für Master / Detail-Datenbindung wie erwartet funktioniert ist es wichtig, dass wir auf die Order-Eigenschaft in der Kunden-Klasse, nicht auf den separaten Orders-Knoten binden. Achten Sie darauf, in der folgenden Abbildung. Ziehen Sie die Order-Eigenschaft der Kunden-Klasse auf der unteren Hälfte des Formulars, damit sie in Zeile 2, fügt der Designer:  
  
     ![Ziehen Sie Klassen von Bestellungen als Raster](../data-tools/media/raddata-drag-orders-classes-as-grid.png "Raddata ziehen Sie Bestellungen Klassen als Raster")  
  
7.  Visual Studio verfügt über den Bindungscode generiert, die die UI-Steuerelemente auf Ereignisse in das Modell stellt eine Verbindung her. Alles, was wir tun, um einige Daten anzuzeigen, müssen zum Schreiben von Code zum Auffüllen des Modells ist. Zuerst sehen wir navigieren Sie zu "MainWindow.Xaml.cs", und fügen Sie einen Datenmember der MainWindow-Klasse für den Datenkontext. Dieses Objekt, das für uns generiert wurde, fungiert etwa ein Steuerelement, das verfolgt Änderungen und Ereignisse im Modell. Während wir hier sind, fügen wir zwei Elemente, die wir später verwenden einen neuen Kunden oder eine neue Bestellung hinzufügen. Wir werden auch die Initialisierung Konstruktorlogik hinzufügen. Am Anfang der Klasse sollte wie folgt aussehen:  
  
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
  
     Hinzufügen einer `using` -Direktive für System.Data.Entity, die Load-Erweiterungsmethode in den Gültigkeitsbereich einzubinden:  
  
    ```csharp  
    using System.Data.Entity;  
    ```  
  
     Jetzt einen Bildlauf nach unten, und suchen Sie den Window_Loaded-Ereignishandler. Beachten Sie, dass Visual Studio ein CollectionViewSource-Objekt für uns hinzugefügt hat. Dies stellt das NorthwindEntities-Objekt, das wir ausgewählt, wenn wir das Modell erstellt haben. Wir fügen Sie Code zum Window_loaded, damit die gesamte Methode jetzt wie folgt aussieht:  
  
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
  
8.  Drücken Sie **F5**. Sie sollte die Details für den ersten Kunden angezeigt werden, die in die CollectionViewSource und deren Bestellungen im Datenraster abgerufen wurden. Die Formatierung nicht besonders beeindruckend, lassen Sie uns, die Sie beheben. Erstellen Sie eine Möglichkeit, die anderen Datensätze anzeigen und führen Sie grundlegende CRUD-Vorgänge können aus.  
  
## <a name="adjust-the-page-design-and-add-grids-for-new-customers-and-orders"></a>Passen Sie das Design der Seite und Hinzufügen von datenrastern für neue Kunden und Bestellungen  
 Die standardanordnung von Visual Studio erstellt ist nicht ideal, bei unserer Anwendung, damit wir einige Änderungen an der XAML manuell vornehmen müssen. Wir benötigen einige "Forms" (die tatsächlich Raster sind) auch auf dem Benutzer ermöglichen, einen neuen Kunden oder eine neue Bestellung hinzufügen.    Um einen neuen Kunden und Reihenfolge hinzufügen können, benötigen wir einen separaten Satz von Textfeldern, die nicht eine Datenbindung an die `CollectionViewSource`. Wir müssen steuern, welche Raster zu jedem Zeitpunkt dem Benutzer angezeigt wird, indem Sie die Visible-Eigenschaft in die Handlermethoden festlegen.  
  
 Abschließend fügen wir eine Löschen-Schaltfläche auf jede Zeile im Raster Bestellungen zum Aktivieren eines Benutzers zum Löschen einer einzelnen Bestellung hinzu.  
  
 Fügen Sie zunächst diese Formate zu Windows.Resources:  
  
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
  
 Ersetzen Sie als Nächstes die gesamte äußere Raster mit diesem Markup:  
  
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
 In Windows Forms-Anwendungen erhalten Sie ein BindingNavigator-Objekt mit den Schaltflächen zur Navigation Zeilen in einer Datenbank und für grundlegende CRUD-Vorgänge ausführen. WPF bietet keine BindingNavigator, aber sie sind einfach genug. Machen wir, die mit den Schaltflächen in einem horizontalen StackPanel in der untersten Zeile des Rasters Seite, und ordnen wir die Schaltflächen mit Befehlen, die an Methoden in der CodeBehind-gebunden sind.  
  
 Es gibt die Befehlslogik statt vier Teilen: (1) die Befehle, (2) der Bindungen, (3) die Schaltflächen und (4) die Befehlshandler im Code-Behind.  
  
#### <a name="add-commands-bindings-and-buttons-in-xaml"></a>Hinzufügen von Befehlen, Bindungen und Schaltflächen in XAML  
  
1.  Zunächst fügen wir die Befehle in unsere Datei "MainWindow.xaml" im Windows.Resources-Element hinzu:  
  
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
  
2.  Ein CommandBinding-Element wird ein Ereignis RoutedUICommand eine Methode in der CodeBehind zugeordnet. Fügen Sie dieses CommandBindings-Element, nach dem schließenden Tag Windows.Resources:  
  
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
  
3.  Jetzt sehen wir Hinzufügen des StackPanels mit der Navigation, hinzufügen, löschen und aktualisieren Sie die Schaltflächen. Fügen Sie zunächst diesen Stil auf Windows.Resources:  
  
    ```xaml  
    <Style x:Key="NavButton" TargetType="{x:Type Button}" BasedOn="{x:Null}">  
        <Setter Property="FontSize" Value="24"/>  
        <Setter Property="FontFamily" Value="Segoe UI Symbol"/>  
        <Setter Property="Margin" Value="2,2,2,0"/>  
        <Setter Property="Width" Value="40"/>  
        <Setter Property="Height" Value="auto"/>  
    </Style>  
    ```  
  
     Nun fügen Sie diesen Code direkt nach der RowDefinitions für das äußere Element für Raster im oberen Rand der XAML-Seite ein:  
  
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
  
#### <a name="add-command-handlers-to-the-mainwindow-class"></a>Befehlshandler der MainWindow-Klasse hinzufügen  
  
1.  Das Code-Behind ist minimal, mit Ausnahme von Methoden zum Hinzufügen und löschen. Beachten Sie, dass die Navigation durch Aufrufen von Methoden für die ansichtseigenschaft von CollectionViewSource ausgeführt wird. Die DeleteOrderCommandHandler wird gezeigt, wie eine kaskadierende Delete für einen Auftrag ausgeführt wird. Wir müssen zunächst die "Order_Details" zu löschen, die verknüpft sind. Die UpdateCommandHandler der Auflistung einen neuen Kunde hinzugefügt, andernfalls nur das vorhandene Objekt mit, was den Benutzer, die in den Textfeldern vorgenommen Änderungen aktualisiert.  
  
2.  Diese Handlermethoden der MainWindow-Klasse in "MainWindow.Xaml.cs" hinzufügen, wenn Ihre CollectionViewSource-Element für die Customers-Tabelle auf einen anderen Namen aufweist, müssen Sie den Namen in jeder dieser Methoden anpassen:  
  
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
  
3.  Drücken Sie **F5**. Daraufhin sollte die Daten, und die Navigationsschaltflächen sollte wie erwartet funktionieren. Klicken Sie auf "Commit", um einen neuen Kunden oder eine Bestellung zum Modell hinzuzufügen, nachdem Sie die Daten eingegeben haben.  Klicken Sie auf "Abbrechen", für die Sicherung aus einem Kunden oder eine neue Bestellung Formulars ohne zu speichern. Sie können Änderungen an vorhandenen Kunden und Bestellungen direkt in die Textfelder vornehmen, und diese Änderungen werden automatisch in das Modell geschrieben werden.  
  
## <a name="see-also"></a>Siehe auch  
 [Visual Studio-Datentools für .NET](../data-tools/visual-studio-data-tools-for-dotnet.md) [Entity Framework-Dokumentation](https://msdn.microsoft.com/data/ee712907.aspx)
