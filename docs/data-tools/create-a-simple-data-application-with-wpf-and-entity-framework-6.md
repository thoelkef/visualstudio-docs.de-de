---
title: Erstellen einer einfachen Datenanwendung mit WPF und Entity Framework 6
ms.date: 08/22/2017
ms.topic: conceptual
dev_langs:
- CSharp
author: gewarren
ms.author: gewarren
manager: douge
ms.prod: visual-studio-dev15
ms.workload:
- data-storage
ms.openlocfilehash: 4fa897ff92cb6956bef59dfcb7a860b24d0d8bae
ms.sourcegitcommit: 37fb7075b0a65d2add3b137a5230767aa3266c74
ms.translationtype: MTE95
ms.contentlocale: de-DE
ms.lasthandoff: 01/02/2019
ms.locfileid: "53885743"
---
# <a name="create-a-simple-data-application-with-wpf-and-entity-framework-6"></a>Erstellen einer einfachen Datenanwendung mit WPF und Entity Framework 6

Diese exemplarische Vorgehensweise veranschaulicht das Erstellen einer einfachen "Forms over Data"-Anwendung in Visual Studio. Die app verwendet SQL Server LocalDB, die Northwind-Datenbank, Entity Framework 6 und Windows Presentation Foundation. Es zeigt, wie Sie einfache Datenbindung mit einer Master / Detail-Ansicht, und sie hat auch eine benutzerdefinierte Bindung Navigator mit Schaltflächen für die **nächste verschieben**, **vorherige verschieben**, **abans**, **Ans Ende**, **Update** und **löschen**.

Dieser Artikel konzentriert sich auf das Verwenden von Datentools in Visual Studio, und versucht nicht, erläutern die zugrunde liegenden Technologien in jeder beliebigen Tiefe. Es wird davon ausgegangen, dass Sie über grundlegende Kenntnisse von XAML, Entity Framework und SQL verfügen. In diesem Beispiel wird auch nicht Model-View-ViewModel (MVVM)-Architektur veranschaulicht die standardmäßigen für WPF-Anwendungen ist. Allerdings können Sie diesen Code in Ihren eigenen MVVM-Anwendung mit geringfügigen Änderungen kopieren.

## <a name="install-and-connect-to-northwind"></a>Installieren und Verbinden mit Northwind

Dieses Beispiel verwendet die SQL Server Express LocalDB und der Beispieldatenbank Northwind. Wenn Sie der ADO.NET-Datenanbieter für das betreffende Produkt auf Entity Framework unterstützt, sollte es für andere Produkte der SQL-Datenbank genauso gut funktionieren.

1.  Wenn Sie SQL Server Express LocalDB nicht haben, installieren Sie es entweder über die [Downloadseite für SQL Server Express](https://www.microsoft.com/sql-server/sql-server-editions-express), oder über die **Visual Studio-Installer**. In der **Visual Studio-Installer**, können Sie SQL Server Express LocalDB installieren, als Teil der **.NET Desktopentwicklung** Workload oder als eine einzelne Komponente.

2.  Installieren der Northwind-Beispieldatenbank mit folgenden Schritten:

    1. Öffnen Sie in Visual Studio die **Objekt-Explorer von SQL Server** Fenster. (**Objekt-Explorer von SQL Server** installiert ist, als Teil der **datenspeicherung und-Verarbeitung** arbeitsauslastung in der **Visual Studio-Installer**.) Erweitern Sie die **SQL Server** Knoten. Mit der rechten Maustaste auf der LocalDB-Instanz, und wählen Sie **neue Abfrage**.

       Ein Abfrage-Editor-Fenster wird geöffnet.

    2. Kopieren der [Northwind Transact-SQL-Skript](https://github.com/MicrosoftDocs/visualstudio-docs/blob/master/docs/data-tools/samples/northwind.sql?raw=true) in die Zwischenablage. Dieses T-SQL-Skript wird die Northwind-Datenbank von Grund auf neu erstellt und mit Daten aufgefüllt.

    3. Fügen Sie das T-SQL-Skript im Abfrage-Editor, und wählen Sie dann die **Execute** Schaltfläche.

       Klicken Sie nach kurzer Zeit die Ausführung die Abfrage abgeschlossen ist, und die Northwind-Datenbank wird erstellt.

3.  [Hinzufügen von neuen Verbindungen](../data-tools/add-new-connections.md) für Northwind.

## <a name="configure-the-project"></a>Konfigurieren des Projekts

1.  Wählen Sie in Visual Studio **Datei** > **neu** > **Projekt** und erstellen Sie ein neues C# WPF-Anwendung.

2.  Als Nächstes fügen Sie das NuGet-Paket für Entity Framework 6 hinzu. In **Projektmappen-Explorer**, wählen Sie den Projektknoten aus. Wählen Sie im Hauptmenü **Projekt** > **NuGet-Pakete verwalten**.

     ![Menüelement für die NuGet-Pakete verwalten](../data-tools/media/raddata_vs2015_manage_nuget_packages.png)

3.  In der **NuGet Package Manager**, klicken Sie auf die **Durchsuchen** Link. Entitätsframework ist wahrscheinlich das oberste Paket in der Liste aus. Klicken Sie auf **installieren** im rechten Bereich und den aufforderungen folgen. Das Fenster "Ausgabe" erfahren Sie, wenn die Installation abgeschlossen ist.

     ![Entity Framework-NuGet-Pakets](../data-tools/media/raddata_vs2015_nuget_ef.png)

4.  Sie können nun Visual Studio verwenden, um ein Modell basierend auf der Northwind-Datenbank zu erstellen.

## <a name="create-the-model"></a>Erstellen des Modells

1. Mit der rechten Maustaste auf den Projektknoten im **Projektmappen-Explorer** , und wählen Sie **hinzufügen** > **neues Element**. Klicken Sie im linken Bereich unter der C# Knoten, wählen Sie **Daten** , und wählen Sie im mittleren Bereich **ADO.NET Entity Data Model**.

   ![Entity Framework Model Elemente bei neuen Projekten](../data-tools/media/raddata-ef-new-project-item.png)

2. Rufen Sie das Modell `Northwind_model` , und wählen Sie **OK**. Der **Assistent für Entity Data Model** wird geöffnet. Wählen Sie **EF Designer aus Datenbank** , und klicken Sie dann auf **Weiter**.

   ![EF-Modell aus der Datenbank](../data-tools/media/raddata-ef-model-from-database.png)

3. Wählen Sie im nächsten Bildschirm Ihre LocalDB Northwind-Verbindung, und klicken Sie auf **Weiter**.

4. Wählen Sie in der nächsten Seite des Assistenten für die Tabellen, gespeicherten Prozeduren und andere Datenbankobjekte in das Entity Framework-Modell eingeschlossen werden sollen. Erweitern Sie den Knoten "Dbo" in der Strukturansicht angezeigt, und wählen Sie **Kunden**, **Bestellungen**, und **Bestelldetails**. Lassen Sie die Standardeinstellungen unverändert, und klicken Sie auf **Fertig stellen**.

    ![Wählen Sie Datenbankobjekte aus, für das Modell](../data-tools/media/raddata-choose-ef-objects.png)

5. Der Assistent generiert die C# Klassen, die das Entity Framework-Modell darstellen. Die Klassen sind einfache alte C# Klassen und sie werden wir Databind der WPF-Benutzeroberfläche. Die *EDMX* Datei beschreibt die Beziehungen und anderen Metadaten, die Objekte in der Datenbank die Klassen zugeordnet. Die *TT* Dateien sind T4-Vorlagen, die den Code zu generieren, die für das Modell, und speichern Sie Änderungen an der Datenbank ausgeführt wird. Sehen Sie alle diese Dateien im **Projektmappen-Explorer** unter dem Knoten Northwind_model:

      ![Projektmappen-Explorer EF-Modelldateien](../data-tools/media/raddata-solution-explorer-ef-model-files.png)

    Die Designer-Oberfläche für die *EDMX* Datei können Sie einige Eigenschaften und Beziehungen im Modell zu ändern. Wir werden nicht in dieser exemplarischen Vorgehensweise den Designer zu verwenden.

6. Die *TT* Dateien sind allgemein und müssen Sie ein Knotentyp mit der WPF-Datenbindung, funktioniert die ObservableCollections erfordert optimieren. In **Projektmappen-Explorer**, erweitern Sie den Northwind_model-Knoten, bis Sie gefunden *Northwind_model.tt*. (Stellen Sie sicher, dass Sie sind nicht in der *. Context.tt* -Datei, die direkt unterhalb der *EDMX* Datei.)

   -   Ersetzen Sie die zwei Vorkommen des <xref:System.Collections.ICollection> mit <xref:System.Collections.ObjectModel.ObservableCollection%601>.

   -   Ersetzen Sie das erste Vorkommen des <xref:System.Collections.Generic.HashSet%601> mit <xref:System.Collections.ObjectModel.ObservableCollection%601> der Nähe von Zeile 51. Ersetzen Sie das zweite Vorkommen der HashSet nicht.

   -   Ersetzen Sie dies das einzige Vorkommen <xref:System.Collections.Generic> (Nähe von Zeile 431) mit <xref:System.Collections.ObjectModel>.

7. Drücken Sie **STRG**+**UMSCHALT**+**B** zum Erstellen des Projekts. Wenn der Build abgeschlossen ist, sind die Modellklassen des Datenquellen-Assistenten angezeigt.

Jetzt können Sie dieses Modell auf der Seite "XAML" einbinden, sodass Sie anzuzeigen, navigieren und die Daten ändern können.

## <a name="databind-the-model-to-the-xaml-page"></a>DataBind das Modell, das die XAML-Seite

Es ist möglich, einen eigenen Databinding-Code schreiben, aber es ist viel einfacher, Visual Studio, die es für Sie erledigen können.

1.  Wählen Sie im Hauptmenü **Projekt** > **neue Datenquelle hinzufügen** um die **Assistenten zur Datenquellenkonfiguration**. Wählen Sie **Objekt** , da Sie auf die Modellklassen, mit der Datenbank nicht binden:

     ![Datenquellen-Assistenten mit Objektquelle-Konfiguration](../data-tools/media/raddata-data-source-configuration-wizard-with-object-source.png)

2.  Wählen Sie **Kunden**. (Aus der Orders-Navigationseigenschaft im Hinblick auf werden Quellen für Aufträge, die automatisch generiert.)

     ![Fügen Sie Entitätsklassen als Datenquellen hinzu.](../data-tools/media/raddata-add-entity-classes-as-data-sources.png)

3.  Klicken Sie auf **Fertig stellen**.

4.  Navigieren Sie zu *"MainWindow.xaml"* in der Codeansicht. Die XAML ist für die Zwecke dieses Beispiels einfache bewusst. Ändern Sie den Titel der MainWindow-Element in einen aussagekräftigeren und erhöhen Sie seine Höhe und Breite auf 600 x 800-vorerst zu. Sie können es später jederzeit ändern. Fügen Sie nun diese drei Zeilendefinitionen Hauptraster wird angezeigt, die eine Zeile für die Navigationsschaltflächen, für die Details des Kunden und eine für das Raster, das zeigt, deren Bestellungen hinzu:

    ```xaml
    <Grid.RowDefinitions>
            <RowDefinition Height="auto"/>
            <RowDefinition Height="auto"/>
            <RowDefinition Height="*"/>
        </Grid.RowDefinitions>
    ```

5.  Öffnen Sie nun *"MainWindow.xaml"* , damit Sie es im Designer anzeigen. Dies bewirkt, dass die **Datenquellen** Fenster als Option auf den Rand der Visual Studio-Fenster angezeigt werden die **Toolbox**. Klicken Sie auf die Registerkarte, um das Fenster öffnen, oder klicken andernfalls **UMSCHALT**+**Alt**+**D** oder **Ansicht**  >  **Andere Windows** > **Datenquellen**. Wir werden auf jede Eigenschaft in der Kunden-Klasse in einem eigenen benutzerdefinierten Text-Feld angezeigt. Klicken Sie zunächst auf den Pfeil in der **Kunden** Kombinationsfeld und **Details**. Klicken Sie dann ziehen Sie den Knoten auf den mittleren Teil der Entwurfsoberfläche, damit der Designer weiß, dass Sie in der mittleren Zeile wechseln soll. Wenn Sie es vergessen haben, können Sie die Zeile zu einem späteren Zeitpunkt manuell in die XAML angeben. Standardmäßig werden die Steuerelemente vertikal in einem Grid-Element platziert, aber an diesem Punkt können angeordnet werden, werden beliebig auf dem Formular. Beispielsweise kann es sinnvoll Platzieren der **Namen** Textfeld am oberen Rand oberhalb der Adresse. Die beispielanwendung für diesen Artikel ordnet die Felder, und diese in zwei Spalten sortiert werden.

     ![Kunden datenquellenbindung in einzelne Steuerelemente](../data-tools/media/raddata-customers-data-source-binding-to-individual-controls.png)

     In der Codeansicht, Sie sehen nun eine neue `Grid` Element in Zeile 1 (die mittlere Zeile) des übergeordneten Rasters. Das übergeordnete Element, das Raster enthält ein `DataContext` Attribut, das eine Bindung zu CollectionViewSource verweist, das hinzugefügt wurde, wird, die `Windows.Resources` Element. Diesen Datenkontext erhält, wenn das erste Textfeld gebunden **Adresse**, diesem Namen zugeordnet ist die `Address` Eigenschaft in der aktuellen `Customer` Objekt in die CollectionViewSource.

    ```xaml
    <Grid DataContext="{StaticResource customerViewSource}">
    ```

6.  Wenn ein Kunde in der oberen Hälfte des Fensters sichtbar ist, möchten Sie ihre Aufträge in der unteren Hälfte finden Sie unter. Zeigen Sie die Aufträge in einem einzelnen Grid-Steuerelement. Für die Master / Detail-Datenbindung wie erwartet funktioniert ist es wichtig, dass Sie der Orders-Eigenschaft in der Kunden-Klasse, nicht auf den separaten Orders-Knoten binden. Ziehen Sie die Order-Eigenschaft der Kunden-Klasse auf der unteren Hälfte des Formulars, damit sie in Zeile 2, fügt der Designer:

     ![Ziehen Sie Klassen von Bestellungen als Raster](../data-tools/media/raddata-drag-orders-classes-as-grid.png)

7.  Visual Studio verfügt über den Bindungscode generiert, die die UI-Steuerelemente auf Ereignisse in das Modell stellt eine Verbindung her. Sie müssen lediglich um einige Daten zu sehen, lediglich zum Schreiben von Code zum Auffüllen des Modells. Navigieren Sie zunächst auf *"MainWindow.Xaml.cs"* und fügen Sie einen Datenmember der MainWindow-Klasse für den Datenkontext. Dieses Objekt, das für Sie generiert wurde, fungiert etwa ein Steuerelement, das verfolgt Änderungen und Ereignisse im Modell. Sie müssen auch die Initialisierung Konstruktorlogik hinzufügen. Der Anfang der Klasse sollte wie folgt aussehen:

     [!code-csharp[MainWindow#1](../data-tools/codesnippet/CSharp/CreateWPFDataApp/MainWindow.xaml.cs#1)]

     Hinzufügen einer `using` -Direktive für System.Data.Entity, die Load-Erweiterungsmethode in den Gültigkeitsbereich einzubinden:

     ```csharp
     using System.Data.Entity;
     ```

     Jetzt einen Bildlauf nach unten, und finden die `Window_Loaded` -Ereignishandler. Beachten Sie, dass Visual Studio ein CollectionViewSource-Objekt hinzugefügt hat. Dies stellt das NorthwindEntities-Objekt, das Sie ausgewählt, bei der Erstellung des Modells dar. Fügen Sie Code zum `Window_Loaded` , damit die gesamte Methode jetzt wie folgt aussieht:

     [!code-csharp[Window_Loaded#2](../data-tools/codesnippet/CSharp/CreateWPFDataApp/MainWindow.xaml.cs#2)]

8.  Drücken Sie **F5**. Sie sollten die Details für den ersten Kunden anzeigen, die in die CollectionViewSource abgerufen wurden. Sie sollte auch ihre Bestellungen im Datenraster angezeigt werden. Die Formatierung nicht besonders beeindruckend, lassen Sie uns, die Sie beheben. Sie können auch eine Möglichkeit, die anderen Datensätze anzuzeigen, und führen Sie grundlegende CRUD-Vorgänge erstellen.

## <a name="adjust-the-page-design-and-add-grids-for-new-customers-and-orders"></a>Passen Sie das Design der Seite und Hinzufügen von datenrastern für neue Kunden und Bestellungen

Die standardanordnung von Visual Studio erstellt ist nicht ideal für Ihre Anwendung, damit Sie einige Änderungen in der XAML manuell erstellen müssen. Außerdem benötigen Sie einige "Forms" (die tatsächlich Raster sind), um die Benutzer beim Hinzufügen eines neuen Kunden oder die Reihenfolge zu ermöglichen. Um einen neuen Kunden und Reihenfolge hinzufügen können, benötigen Sie einen separaten Satz von Textfeldern, die nicht eine Datenbindung an die `CollectionViewSource`. Sie müssen steuern, welche Raster zu jedem Zeitpunkt dem Benutzer angezeigt wird, indem Sie die Visible-Eigenschaft in die Handlermethoden festlegen. Abschließend fügen Sie eine Löschen-Schaltfläche auf jede Zeile im Raster Orders, um dem Benutzer ermöglichen, die einen einzelnen Auftrag zu löschen.

Fügen Sie zunächst diese Stile auf die `Windows.Resources` Element im *"MainWindow.xaml"*:

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
<Grid>
     <Grid.RowDefinitions>
         <RowDefinition Height="auto"/>
         <RowDefinition Height="auto"/>
         <RowDefinition Height="*"/>
     </Grid.RowDefinitions>
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
         <TextBox x:Name="customerIDTextBox" Grid.Row="0" Style="{StaticResource CustTextBox}"
                  Text="{Binding CustomerID, Mode=TwoWay, NotifyOnValidationError=true, ValidatesOnExceptions=true}"/>
         <Label Content="Company Name:" Grid.Row="1" Style="{StaticResource Label}"/>
         <TextBox x:Name="companyNameTextBox" Grid.Row="1" Style="{StaticResource CustTextBox}"
                  Text="{Binding CompanyName, Mode=TwoWay, NotifyOnValidationError=true, ValidatesOnExceptions=true}"/>
         <Label Content="Contact Name:" Grid.Row="2" Style="{StaticResource Label}"/>
         <TextBox x:Name="contactNameTextBox" Grid.Row="2" Style="{StaticResource CustTextBox}"
                  Text="{Binding ContactName, Mode=TwoWay, NotifyOnValidationError=true, ValidatesOnExceptions=true}"/>
         <Label Content="Contact Title:" Grid.Row="3" Style="{StaticResource Label}"/>
         <TextBox x:Name="contactTitleTextBox" Grid.Row="3" Style="{StaticResource CustTextBox}"
                  Text="{Binding ContactTitle, Mode=TwoWay, NotifyOnValidationError=true, ValidatesOnExceptions=true}"/>
         <Label Content="Address:" Grid.Row="4" Style="{StaticResource Label}"/>
         <TextBox x:Name="addressTextBox" Grid.Row="4" Style="{StaticResource CustTextBox}"
                  Text="{Binding Address, Mode=TwoWay, NotifyOnValidationError=true, ValidatesOnExceptions=true}"/>
         <Label Content="City:" Grid.Column="1" Grid.Row="0" Style="{StaticResource Label}"/>
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
         <TextBox x:Name="add_customerIDTextBox" Grid.Row="0" Style="{StaticResource CustTextBox}"
                  Text="{Binding CustomerID, Mode=TwoWay, NotifyOnValidationError=true, ValidatesOnExceptions=true}"/>
         <Label Content="Company Name:" Grid.Row="1" Style="{StaticResource Label}"/>
         <TextBox x:Name="add_companyNameTextBox" Grid.Row="1" Style="{StaticResource CustTextBox}"
                  Text="{Binding CompanyName, Mode=TwoWay, NotifyOnValidationError=true, ValidatesOnExceptions=true }"/>
         <Label Content="Contact Name:" Grid.Row="2" Style="{StaticResource Label}"/>
         <TextBox x:Name="add_contactNameTextBox" Grid.Row="2" Style="{StaticResource CustTextBox}"
                  Text="{Binding ContactName, Mode=TwoWay, NotifyOnValidationError=true, ValidatesOnExceptions=true}"/>
         <Label Content="Contact Title:" Grid.Row="3" Style="{StaticResource Label}"/>
         <TextBox x:Name="add_contactTitleTextBox" Grid.Row="3" Style="{StaticResource CustTextBox}"
                  Text="{Binding ContactTitle, Mode=TwoWay, NotifyOnValidationError=true, ValidatesOnExceptions=true}"/>
         <Label Content="Address:" Grid.Row="4" Style="{StaticResource Label}"/>
         <TextBox x:Name="add_addressTextBox" Grid.Row="4" Style="{StaticResource CustTextBox}"
                  Text="{Binding Address, Mode=TwoWay, NotifyOnValidationError=true, ValidatesOnExceptions=true}"/>
         <Label Content="City:" Grid.Column="1" Grid.Row="0" Style="{StaticResource Label}"/>
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
                         <Button Content="Delete" Command="{StaticResource DeleteOrderCommand}" CommandParameter="{Binding}"/>
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

In Windows Forms-Anwendungen erhalten Sie ein BindingNavigator-Objekt mit den Schaltflächen zur Navigation Zeilen in einer Datenbank und für grundlegende CRUD-Vorgänge ausführen. WPF bietet keine BindingNavigator, aber es ist einfach genug, um eines zu erstellen. Sie führen, die mit den Schaltflächen in einem horizontalen StackPanel, und ordnen die Schaltflächen mit Befehlen, die an Methoden in der CodeBehind-gebunden sind.

Es gibt die Befehlslogik statt vier Teilen: (1) die Befehle, (2) der Bindungen, (3) die Schaltflächen und (4) die Befehlshandler im Code-Behind.

### <a name="add-commands-bindings-and-buttons-in-xaml"></a>Hinzufügen von Befehlen, Bindungen und Schaltflächen in XAML

1.  Fügen Sie zunächst die Befehle in der *"MainWindow.xaml"* Datei innerhalb der `Windows.Resources` Element:

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

2.  Ordnet ein CommandBinding-Element ein `RoutedUICommand` Ereignis an eine Methode im Code im Hintergrund. Fügen Sie Folgendes `CommandBindings` Element an, nach der `Windows.Resources` schließendes Tag:

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

3.  Fügen Sie jetzt die `StackPanel` mit der Navigation hinzufügen, löschen und aktualisieren Sie die Schaltflächen. Fügen Sie zunächst diesen Stil `Windows.Resources`:

    ```xaml
    <Style x:Key="NavButton" TargetType="{x:Type Button}" BasedOn="{x:Null}">
        <Setter Property="FontSize" Value="24"/>
        <Setter Property="FontFamily" Value="Segoe UI Symbol"/>
        <Setter Property="Margin" Value="2,2,2,0"/>
        <Setter Property="Width" Value="40"/>
        <Setter Property="Height" Value="auto"/>
    </Style>
    ```

     Zweitens fügen Sie diesen Code direkt nach der `RowDefinitions` für das äußere `Grid` Element bis zum Anfang der XAML-Seite:

    ```xaml
    <StackPanel Orientation="Horizontal" Margin="2,2,2,0" Height="36" VerticalAlignment="Top" Background="Gainsboro" DataContext="{StaticResource customerViewSource}" d:LayoutOverrides="LeftMargin, RightMargin, TopMargin, BottomMargin">
        <Button Name="btnFirst" Content="|◄" Command="{StaticResource FirstCommand}" Style="{StaticResource NavButton}"/>
        <Button Name="btnPrev" Content="◄" Command="{StaticResource PreviousCommand}" Style="{StaticResource NavButton}"/>
        <Button Name="btnNext" Content="►" Command="{StaticResource NextCommand}" Style="{StaticResource NavButton}"/>
        <Button Name="btnLast" Content="►|" Command="{StaticResource LastCommand}" Style="{StaticResource NavButton}"/>
        <Button Name="btnDelete" Content="Delete Customer" Command="{StaticResource DeleteCustomerCommand}" FontSize="11" Width="120" Style="{StaticResource NavButton}"/>
        <Button Name="btnAdd" Content="New Customer" Command="{StaticResource AddCommand}" FontSize="11" Width="80" Style="{StaticResource NavButton}"/>
        <Button Content="New Order" Name="btnNewOrder" FontSize="11" Width="80" Style="{StaticResource NavButton}" Click="NewOrder_click"/>
        <Button Name="btnUpdate" Content="Commit" Command="{StaticResource UpdateCommand}" FontSize="11" Width="80" Style="{StaticResource NavButton}"/>
        <Button Content="Cancel" Name="btnCancel" Command="{StaticResource CancelCommand}" FontSize="11" Width="80" Style="{StaticResource NavButton}"/>
    </StackPanel>
    ```

### <a name="add-command-handlers-to-the-mainwindow-class"></a>Befehlshandler der MainWindow-Klasse hinzufügen

Das Code-Behind ist minimal, mit Ausnahme von Methoden zum Hinzufügen und löschen. Navigation wird durch Aufrufen von Methoden für die ansichtseigenschaft von CollectionViewSource ausgeführt. Die `DeleteOrderCommandHandler` zeigt, wie Sie eine Löschweitergabe für einen Auftrag ausführen. Wir müssen zunächst die "Order_Details" zu löschen, die verknüpft sind. Die `UpdateCommandHandler` der Auflistung einen neuen Kunden oder eine Bestellung hinzugefügt, da ansonsten nur mit Änderungen, die der Benutzer in die Textfelder aktualisiert eine vorhandene Kunden oder eine Bestellung.

Diese Handlermethoden in der MainWindow-Klasse hinzufügen *"MainWindow.Xaml.cs"*. Wenn Ihre CollectionViewSource-Element für die Customers-Tabelle auf einen anderen Namen aufweist, müssen Sie passen Sie den Namen in jeder der folgenden Methoden:

[!code-csharp[CommandHandlers#3](../data-tools/codesnippet/CSharp/CreateWPFDataApp/MainWindow.xaml.cs#3)]

## <a name="run-the-application"></a>Ausführen der Anwendung

Drücken Sie **F5**, um mit dem Debuggen zu beginnen. Sie sollten Kunden- und Bestelldaten in das Raster gefüllt, und die Navigationsschaltflächen sollte wie erwartet funktionieren. Klicken Sie auf **Commit** einen neuen Kunden oder eine Bestellung mit dem Modell hinzufügen, nachdem Sie die Daten eingegeben haben. Klicken Sie auf **Abbrechen** von einem neuen Kunden oder neue Bestellformulare zu sichern, ohne die Daten speichern. Sie können Änderungen an vorhandenen Kunden und Bestellungen direkt in die Textfelder vornehmen, und diese Änderungen werden automatisch in das Modell geschrieben.

## <a name="see-also"></a>Siehe auch

- [Visual Studio-Datentools für .NET](../data-tools/visual-studio-data-tools-for-dotnet.md)
- [Entity Framework-Dokumentation](/ef/)