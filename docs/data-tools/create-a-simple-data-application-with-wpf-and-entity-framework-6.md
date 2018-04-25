---
title: Erstellen einer einfachen datenanwendung mit WPF und Entity Framework 6
ms.date: 08/22/2017
ms.topic: conceptual
dev_langs:
- CSharp
author: gewarren
ms.author: gewarren
manager: douge
ms.technology: vs-data-tools
ms.workload:
- data-storage
ms.openlocfilehash: 180b4bc58c3c915eede55b6b30e0e3e9693b6ab6
ms.sourcegitcommit: 42ea834b446ac65c679fa1043f853bea5f1c9c95
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/19/2018
---
# <a name="create-a-simple-data-application-with-wpf-and-entity-framework-6"></a>Erstellen einer einfachen datenanwendung mit WPF und Entity Framework 6

Diese exemplarische Vorgehensweise zeigt, wie eine grundlegende "Formulare über Daten"-Anwendung in Visual Studio erstellen. Die app verwendet SQL Server LocalDB, die Northwind-Datenbank, Entity Framework 6 und Windows Presentation Foundation. Es zeigt, wie Sie einfache Datenbindung mit einer Master / Detail-Ansicht, und sie hat auch eine benutzerdefinierte "binden Navigator" mit den Schaltflächen für "Nächste verschieben", "Vorherige verschieben," "An den Anfang, verschieben" "ans Ende," "Aktualisieren" und "Delete".

Dieser Artikel konzentriert sich auf die mit Data Tools in Visual Studio und versucht nicht, die zugrunde liegenden Technologien in jeder beliebigen Tiefe erläutern. Es wird davon ausgegangen, dass Sie über grundlegende Kenntnisse von XAML-Entity Framework und SQL verfügen. In diesem Beispiel wird auch nicht Model-View-View Model (MVVM)-Architektur veranschaulicht, bei der standard für WPF-Anwendungen ist. Allerdings können Sie diesen Code in Ihrer eigenen Anwendung MVVM mit geringfügigen Änderungen kopieren.

## <a name="install-and-connect-to-northwind"></a>Installieren und Verbinden mit Northwind

Dieses Beispiel verwendet die SQL Server Express LocalDB und der Beispieldatenbank Northwind. Wenn ADO.NET Data Provider für dieses Produkt Entity Framework unterstützt, sollte er mit anderen SQL-Datenbank-Produkten genauso gut funktionieren.

1.  Wenn Sie nicht über SQL Server Express LocalDB verfügen, installieren Sie es entweder aus der [Downloadseite für SQL Server Express](https://www.microsoft.com/sql-server/sql-server-editions-express), oder über die **Installer für Visual Studio**. In der Visual Studio-Installer können als Teil des SQL Server Express LocalDB installiert werden die **.NET Desktopentwicklung** arbeitsauslastung oder als eine einzelne Komponente.

2.  Installieren Sie die Beispieldatenbank Northwind, indem folgende Schritte:

    1. Öffnen Sie in Visual Studio die **Objekt-Explorer von SQL Server** Fenster. (Objekt-Explorer von SQL Server installiert ist, als Teil der **datenspeicherung und Verarbeitung** arbeitsauslastung in der Visual Studio-Installer.) Erweitern Sie die **SQL Server** Knoten. Rechtsklicken Sie auf der LocalDB-Instanz, und wählen Sie **neue Abfrage...** .

       Ein Abfrage-Editorfenster wird geöffnet.

    2. Kopieren der [Northwind Transact-SQL-Skript](https://github.com/MicrosoftDocs/visualstudio-docs/blob/master/docs/data-tools/samples/northwind.sql?raw=true) in die Zwischenablage. Dieses T-SQL-Skript die Northwind-Datenbank von Grund auf neu erstellt und mit Daten aufgefüllt.

    3. Fügen Sie das T-SQL-Skript im Abfrage-Editor, und wählen Sie dann die **Execute** Schaltfläche.

       Nach kurzer Zeit die Abfrage die Ausführung abgeschlossen ist, und die Northwind-Datenbank wird erstellt.

3.  [Hinzufügen von neuen Verbindungen](../data-tools/add-new-connections.md) für Northwind.

## <a name="configure-the-project"></a>Konfigurieren des Projekts

1.  Wählen Sie in Visual Studio **Datei**, **neu**, **Projekt...**  , und erstellen Sie eine neue C#-WPF-Anwendung.

2.  Als Nächstes fügen Sie das NuGet-Paket für Entity Framework 6. Wählen Sie im Projektmappen-Explorer den Projektknoten aus. Wählen Sie im Hauptmenü **Projekt**, **NuGet-Pakete verwalten...**

     ![Menüelement NuGet-Pakete verwalten](../data-tools/media/raddata_vs2015_manage_nuget_packages.png)

3.  NuGet-Paket-Manager, klicken Sie auf die **Durchsuchen** Link. Entity Framework ist wahrscheinlich das oberste Paket in der Liste aus. Klicken Sie auf **installieren** im rechten Bereich, und befolgen Sie die Anweisungen. Das Fenster "Ausgabe" gibt Aufschluss darüber, wann die Installation abgeschlossen ist.

     ![Entity Framework NuGet-Paket](../data-tools/media/raddata_vs2015_nuget_ef.png)

4.  Jetzt können wir die Visual Studio zum Erstellen eines Modells auf Basis der Northwind-Datenbank verwenden.

## <a name="create-the-model"></a>Erstellen des Modells

1.  Klicken Sie mit der rechten Maustaste auf den Projektknoten im Projektmappen-Explorer, und wählen Sie **hinzufügen**, **neues Element...** . Wählen Sie im linken Bereich unter dem C#-Knoten, **Daten** und wählen Sie im mittleren Bereich **ADO.NET Entity Data Model**.

     ![Entity Framework Model neues Projektelement](../data-tools/media/raddata-ef-new-project-item.png)

  2.  Rufen Sie das Modell `Northwind_model` und wählen Sie OK. Die **Entity Data Model-Assistenten** wird geöffnet. Wählen Sie **EF Designer aus Datenbank** , und klicken Sie dann auf **Weiter**.

     ![EF-Modell aus der Datenbank](../data-tools/media/raddata-ef-model-from-database.png)

3.  Wählen Sie im nächsten Bildschirm Ihre LocalDB Northwind Verbindung, und klicken Sie auf **Weiter**.

4.  In der nächsten Seite des Assistenten wählen Sie die Tabellen, gespeicherte Prozeduren und andere Datenbankobjekte in das Modell im Entity Framework eingeschlossen werden sollen. Erweitern Sie den Knoten "Dbo" in der Strukturansicht, und wählen Sie Kunden, Bestellungen und Bestellungsdetails. Lassen Sie standardmäßig aktiviert, und klicken Sie auf **Fertig stellen**.

     ![Wählen Sie Datenbankobjekte für das Modell](../data-tools/media/raddata-choose-ef-objects.png)

5.  Der Assistent generiert die C#-Klassen, die das Entity Framework-Modell darstellen. Die Klassen sind einfache alte C#-Klassen und welche wir Databind für die WPF-Benutzeroberfläche. Die EDMX-Datei beschreibt die Beziehungen und anderen Metadaten, die die Klassen der Objekte in der Datenbank zuordnet. Die TT-Dateien sind T4-Vorlagen, die den Code zu generieren, der für das Modell ausgeführt wird und Änderungen an der Datenbank speichern. Sie können alle diese Dateien im Projektmappen-Explorer unter dem Knoten Northwind_model anzeigen:

       ![Projektmappen-Explorer EF Modelldateien](../data-tools/media/raddata-solution-explorer-ef-model-files.png)

     Die Designeroberfläche für die EDMX-Datei können Sie einige Eigenschaften und Beziehungen im Modell ändern. Wir sind nicht den Designer in dieser exemplarischen Vorgehensweise verwenden.

6.  Die TT-Dateien sind allgemeine Zwecke, und wir müssen Optimieren eines mit WPF-Datenbindung ermöglicht die ObservableCollections erforderlich ist. Erweitern Sie im Projektmappen-Explorer die Northwind_model-Knoten, bis Sie Northwind_model.tt gefunden. (Stellen Sie sicher, dass Sie *nicht* in der *. Kontext TT-Datei, die direkt unterhalb der EDMX-Datei ist.)

    -   Ersetzen Sie die zwei Vorkommen des <xref:System.Collections.ICollection> mit <xref:System.Collections.ObjectModel.ObservableCollection%601>.

    -   Ersetzen Sie das erste Vorkommen des <xref:System.Collections.Generic.HashSet%601> mit <xref:System.Collections.ObjectModel.ObservableCollection%601> um Linie 51. Ersetzen Sie das zweite Vorkommen der HashSet nicht

    -   Ersetzen Sie das einzige Vorkommen <xref:System.Collections.Generic> (in der Nähe der Zeile 431) mit <xref:System.Collections.ObjectModel>.

7.  Drücken Sie **STRG + UMSCHALT + B** zum Erstellen des Projekts. Wenn der Build abgeschlossen ist, werden die Modellklassen beim Datenquellen-Assistenten angezeigt.

Jetzt können wir dieses Modell zur Verwendung von XAML-Seite verknüpft, damit wir anzeigen, navigieren und die Daten ändern können.

## <a name="databind-the-model-to-the-xaml-page"></a>Man das Modell, das der XAML-Seite

Es ist möglich, einen eigenen Databinding-Code schreiben, aber es ist viel einfacher zu Visual Studio, die Sie erledigen können.

1.  Wählen Sie im Hauptmenü **Projekt > neue Datenquelle hinzufügen** um die **Datenquellen Konfigurations-Assistenten**. Wählen Sie **Objekt** da wir an der Modellklassen, nicht mit der Datenbank binden:

     ![Datenquellen-Assistenten mit Objektquelle Konfiguration](../data-tools/media/raddata-data-source-configuration-wizard-with-object-source.png)

2.  Wählen Sie die Kunden. (Quellen für Aufträge werden aus der Orders-Navigationseigenschaft im Kunden automatisch generiert.)

     ![Hinzufügen von Entitätsklassen als Datenquellen](../data-tools/media/raddata-add-entity-classes-as-data-sources.png)

3.  Klicken Sie auf **Fertig stellen**

4.  Navigieren Sie zu "MainWindow.xaml" in der Codeansicht. Wir werden den XAML-Code für dieses Beispiel einfach zu halten. Ändern Sie den Titel der MainWindow-Element in einen aussagekräftigeren, und erhöhen Sie die Höhe und Breite auf 600 x 800 vorläufig. Sie können ihn jederzeit später ändern. Fügen Sie nun diese nachrichtenstrukturdefinitionen werden drei Zeilen hinzu Hauptraster wird angezeigt, eine Zeile für die Navigationsschaltflächen, eine für die Details des Kunden, eine für das Raster, in der ihre Bestellungen angezeigt:

    ```xaml
    <Grid.RowDefinitions>
            <RowDefinition Height="auto"/>
            <RowDefinition Height="auto"/>
            <RowDefinition Height="*"/>
        </Grid.RowDefinitions>
    ```

5.  Öffnen Sie jetzt "MainWindow.xaml" auf, sodass Sie es im Designer anzeigen. Dies bewirkt, dass das Fenster "Datenquellen" als Option in der Visual Studio-Fenster-Rand neben der Toolbox angezeigt werden. Klicken Sie auf der Registerkarte ", öffnen Sie das Fenster, oder drücken andernfalls **UMSCHALT**+**Alt**+**D** , oder wählen Sie **Ansicht**  >  **Anderen Fenstern** > **Datenquellen**. Wir jede Eigenschaft in der Customers-Klasse in einem eigenen Feld bestimmtem Text anzeigen möchten. Zunächst klicken Sie auf den Pfeil im Kombinationsfeld Kunden, und wählen Sie **Details**. Ziehen Sie die Knoten auf den mittleren Teil der Entwurfsoberfläche angezeigt, damit der Designer weiß, dass Sie in der mittleren Zeile wechseln soll. Wenn Sie es vergessen haben, können Sie die Zeile manuell zu einem späteren Zeitpunkt in der XAML-Code angeben. Standardmäßig befinden sich die Steuerelemente vertikal in einem Rasterelement, aber an diesem Punkt Sie können sie auf dem Formular beliebig anordnen. Beispielsweise kann es sinnvoll sein, das Textfeld am oberen Rand, über die Adresse eingefügt werden soll. Die beispielanwendung für diesen Artikel ordnet die Felder neu und ordnet diese in zwei Spalten.

     ![Kunden-datenquellenbindung in einzelne Steuerelemente](../data-tools/media/raddata-customers-data-source-binding-to-individual-controls.png)

     In der Codeansicht Sie sehen nun eine neue `Grid` Element in Zeile 1 (die mittlere Zeile) des übergeordneten Elements Raster. Das übergeordnete Element, das Raster verfügt über eine `DataContext` Attribut, das eine Bindung zu CollectionViewSource verweist, das hinzugefügt wurde, wird, die `Windows.Resources` Element. Dieser Datenkontext angegeben, wenn das erste Textfeld "Address" gebunden wird, diesen Namen zugeordnet ist die `Address` Eigenschaft in der aktuellen `Customer` Objekt in das CollectionViewSource-Element.

    ```xaml
    <Grid DataContext="{StaticResource customerViewSource}">
    ```

6.  Wenn ein Kunde in der oberen Hälfte des Fensters angezeigt wird, möchten wir ihre Aufträge in der unteren Hälfte finden Sie unter. Wir zeigen die Bestellungen in einem einzelnen Grid-Steuerelement. Für Master / Detail-Databinding wie erwartet funktioniert ist es wichtig, dass der Orders-Eigenschaft in der Kunden-Klasse ist nicht auf den separaten Bestellungen Knoten hergestellt werden. Ziehen Sie die Orders-Eigenschaft der Klasse Kunden auf der unteren Hälfte des Formulars, damit der Designer legt er in Zeile 2:

     ![Ziehen Sie Aufträge Klassen als Raster](../data-tools/media/raddata-drag-orders-classes-as-grid.png)

7.  Visual Studio verfügt über alle Bindungscode generiert, die die UI-Steuerelemente mit Ereignissen im Modell verbunden. Alles, was müssen wir tun, um einige Daten zu sehen, wird zum Schreiben von Code zum Auffüllen des Modells. Erste wir navigieren Sie zu "MainWindow.Xaml.cs", und fügen Sie einen Datenmember für den Datenkontext der MainWindow-Klasse. Dieses Objekt, das für uns generiert wurde, fungiert etwa ein Steuerelement, das die Änderungen und Ereignisse in das Modell nachverfolgt. Wir werden außerdem die Initialisierung Konstruktorlogik hinzufügen. Am Anfang der Klasse sollte wie folgt aussehen:

     [!code-csharp[MainWindow#1](../data-tools/codesnippet/CSharp/CreateWPFDataApp/MainWindow.xaml.cs#1)]

     Hinzufügen einer `using` -Direktive für System.Data.Entity, um die Erweiterung Lademethode in den Gültigkeitsbereich einzubinden:

     ```csharp
     using System.Data.Entity;
     ```

     Nun einen Bildlauf nach unten, und suchen Sie den Ereignishandler Window_Loaded. Beachten Sie, dass Visual Studio ein CollectionViewSource-Objekt für uns hinzugefügt wurde. Dies stellt das NorthwindEntities-Objekt, das wir ausgewählt, wenn es bei der Erstellung des Modells dar. Wir fügen Sie Code zum Window_Loaded, damit die gesamte Methode jetzt wie folgt aussieht:

     [!code-csharp[Window_Loaded#2](../data-tools/codesnippet/CSharp/CreateWPFDataApp/MainWindow.xaml.cs#2)]

8.  Drücken Sie **F5**. Für den ersten Kunden, die in CollectionViewSource abgerufen wurde, sollten Sie die Details anzuzeigen. Sie sollte auch deren Bestellungen im Datenraster angezeigt werden. Die Formatierung ist ideal wir also reparieren, die nicht. Wir erstellen außerdem eine Möglichkeit zum Anzeigen von der anderen Datensätzen und grundlegende CRUD-Vorgänge durchführen.

## <a name="adjust-the-page-design-and-add-grids-for-new-customers-and-orders"></a>Passen Sie den Entwurf der Seite, und fügen Sie Rastern für neue Kunden und Bestellungen

Die Standardreihenfolge der von Visual Studio erzeugt ist nicht ideal für die Anwendung, damit wir einige Änderungen in der XAML-Code manuell vornehmen müssen. Wir benötigen auch einige "Forms" (die tatsächlich Rastern sind), die dem Benutzer ermöglichen, einen neuen Kunden oder eine Bestellung hinzufügen. Um einen neuen Kunden und Reihenfolge hinzufügen können, benötigen wir einen separaten Satz von Textfeldern, die keine Daten gebunden sind die `CollectionViewSource`. Wir müssen steuern, welche Raster dem Benutzer zu einem beliebigen Zeitpunkt angezeigt wird, indem Sie die Visible-Eigenschaft in die Handlermethoden festlegen. Schließlich fügen wir eine Schaltfläche "löschen" auf jede Zeile in der Orders-Raster, um dem Benutzer ermöglichen, eine einzelne Bestellung zu löschen.

Fügen Sie zunächst diese Formate, auf das Windows.Resources-Element in der Datei "MainWindow.xaml":

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

Ersetzen Sie anschließend die gesamte äußere Raster mit diesem Markup:

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

In Windows Forms-Anwendungen erhalten Sie ein BindingNavigator-Objekt mit den Schaltflächen für das Navigieren auf Zeilen in einer Datenbank sowie bei der Erledigung grundlegende CRUD-Vorgänge. WPF bietet keine BindingNavigator, aber es ist einfach genug, um eines zu erstellen. Wir machen, die mit den Schaltflächen in einem horizontalen StackPanel, und ordnen wir die Schaltflächen mit Befehlen, die an Methoden in der Code-behind gebunden sind.

Vieren Teile der Befehl Logik vorhanden sind: (1) die Befehle, (2) der Bindungen, (3) die Schaltflächen und (4) der Befehlshandler in das Code-Behind-Modell.

### <a name="add-commands-bindings-and-buttons-in-xaml"></a>Hinzufügen von Befehlen, Bindungen und Schaltflächen in XAML

1.  Zunächst fügen wir die Befehle in der Datei "MainWindow.xaml" innerhalb des Windows.Resources-Elements hinzu:

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

2.  Eine CommandBinding ordnet ein RoutedUICommand-Ereignis an eine Methode im Code-behind. Fügen Sie dieses Element CommandBindings nach der Windows.Resources schließendes Tag hinzu:

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

3.  Jetzt sehen wir StackPanel bei die Navigationsleiste hinzufügen, hinzufügen, löschen und aktualisieren Sie die Schaltflächen. Fügen Sie zunächst, dieses Format Windows.Resources hinzu:

    ```xaml
    <Style x:Key="NavButton" TargetType="{x:Type Button}" BasedOn="{x:Null}">
        <Setter Property="FontSize" Value="24"/>
        <Setter Property="FontFamily" Value="Segoe UI Symbol"/>
        <Setter Property="Margin" Value="2,2,2,0"/>
        <Setter Property="Width" Value="40"/>
        <Setter Property="Height" Value="auto"/>
    </Style>
    ```

     Zweitens, fügen Sie diesen Code direkt hinter dem RowDefinitions für die äußere Grid-Element, weiter oben in der XAML-Seite:

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

### <a name="add-command-handlers-to-the-mainwindow-class"></a>Hinzufügen von Befehlshandler der MainWindow-Klasse

Das Code-Behind-Modell ist minimal, mit Ausnahme von Methoden zum Hinzufügen und löschen. Navigation erfolgt durch Aufrufen von Methoden für die ansichtseigenschaft von CollectionViewSource. Die DeleteOrderCommandHandler wird gezeigt, wie eine kaskadierendes Delete für eine Bestellung ausgeführt wird. Wir haben die "Order_Details" erst zu löschen, die mit ihm verknüpft sind. Die UpdateCommandHandler der Auflistung einen neuen Kunden oder eine Bestellung hinzugefügt, andernfalls wird nur eine vorhandene Kunde oder eine Bestellung mit der der Benutzer in die Textfelder vorgenommenen Änderungen aktualisiert.

Diese Handlermethoden der MainWindow-Klasse in "MainWindow.Xaml.cs" hinzufügen. Wenn Ihre CollectionViewSource für die Customers-Tabelle auf einen anderen Namen aufweist, müssen Sie den Namen in jeder dieser Methoden anpassen:

[!code-csharp[CommandHandlers#3](../data-tools/codesnippet/CSharp/CreateWPFDataApp/MainWindow.xaml.cs#3)]

## <a name="run-the-application"></a>Ausführen der Anwendung

Drücken Sie **F5**, um mit dem Debuggen zu beginnen. Daraufhin sollte Kunden- und Bestelldaten aufgefüllt, die im Raster, und die Navigationsschaltflächen sollte wie erwartet funktionieren. Klicken Sie auf "Commit", um einen neuen Kunden oder eine Bestellung mit dem Modell hinzufügen, nachdem Sie die Daten eingegeben haben. Klicken Sie auf "Abbrechen", um aus einem neuen Kunden oder neue Bestellformular zurück, ohne die Daten zu speichern. Nehmen Sie Änderungen vor, um vorhandene Kunden und Bestellungen direkt in die Textfelder ein, und diese Änderungen werden automatisch in das Modell geschrieben.

## <a name="see-also"></a>Siehe auch

- [Visual Studio-Datentools für .NET](../data-tools/visual-studio-data-tools-for-dotnet.md)
- [Dokumentation zu Entity Framework](/ef/)