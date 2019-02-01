---
title: Binden von WPF-Steuerelementen an ein Dataset
ms.date: 11/04/2016
ms.topic: conceptual
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- WPF, data binding in Visual Studio
- WPF data binding [Visual Studio], walkthroughs
- WPF Designer, data binding
ms.assetid: 177420b9-568b-4dad-9d16-1b0e98a24d71
author: gewarren
ms.author: gewarren
manager: jillfra
ms.prod: visual-studio-dev15
ms.workload:
- data-storage
ms.openlocfilehash: 7fec000357046c9a5309b5f501032633df196bb6
ms.sourcegitcommit: 2193323efc608118e0ce6f6b2ff532f158245d56
ms.translationtype: MTE95
ms.contentlocale: de-DE
ms.lasthandoff: 01/25/2019
ms.locfileid: "55007776"
---
# <a name="bind-wpf-controls-to-a-dataset"></a>Binden von WPF-Steuerelementen an ein Dataset

In dieser exemplarischen Vorgehensweise erstellen Sie eine WPF-Anwendung, die von datengebundenen Steuerelementen enthält. Die Steuerelemente sind an Produktdatensätze gebunden, die in einem Dataset gekapselt sind. Sie fügen außerdem Schaltflächen klicken, um Produkte durchsuchen, und speichern Änderungen an Product Records hinzu.

In dieser exemplarischen Vorgehensweise werden die folgenden Aufgaben veranschaulicht:

- Erstellen einer WPF-Anwendung und eines Datasets, das aus Daten in der Beispieldatenbank AdventureWorksLT generiert wird.

- Erstellen mehrerer datengebundener Steuerelemente durch Ziehen einer Datentabelle aus dem **Datenquellenfenster** zu einem Fenster im WPF-Designer.

- Erstellen von Schaltflächen, mit denen die Navigation vorwärts und rückwärts durch die Produktdatensätze möglich ist.

- Erstellen einer Schaltfläche, die Änderungen durch Kunden an den Produktdatensätzen in der Tabelle und der darunterliegenden Datenquelle speichert.

[!INCLUDE[note_settings_general](../data-tools/includes/note_settings_general_md.md)]

## <a name="prerequisites"></a>Erforderliche Komponenten

Zum Durchführen dieser exemplarischen Vorgehensweise benötigen Sie die folgenden Komponenten:

- Visual Studio

- Zugriff auf eine ausgeführte Instanz von SQL Server oder SQL Server Express, die der AdventureWorks-Light (AdventureWorksLT)-Beispieldatenbank angefügt ist. Sie können die AdventureWorksLT-datenbankvon der [CodePlex Archiv](https://archive.codeplex.com/?p=awlt2008dbscript).

Vorkenntnisse der folgenden Konzepte sind ebenfalls hilfreich, wenn auch für die Durchführung der exemplarischen Vorgehensweise nicht erforderlich:

- DataSets und TableAdapters. Weitere Informationen finden Sie unter [datasettools in Visual Studio](../data-tools/dataset-tools-in-visual-studio.md) und [TableAdapters](../data-tools/create-and-configure-tableadapters.md).

- WPF-Datenbindung. Weitere Informationen finden Sie unter [Übersicht über Datenbindung](/dotnet/framework/wpf/data/data-binding-overview).

## <a name="create-the-project"></a>Erstellen eines Projekts

Erstellen Sie ein neues WPF-Projekt zur Produktdatensätze.

1. Starten Sie Visual Studio.

2. Klicken Sie im Menü **Datei** auf **Neu** > **Projekt**.

3. Erweitern Sie **Visual Basic** oder **Visual C#**, und wählen Sie dann **Windows** aus.

4. Wählen Sie die Projektvorlage **WPF-Anwendung** aus.

5. In der **Namen** geben **AdventureWorksProductsEditor** und wählen Sie dann **OK**.

   Visual Studio erstellt das Projekt „AdventureWorksProductsEditor“.

## <a name="create-a-dataset-for-the-application"></a>Erstellen Sie ein Dataset für die Anwendung

Ehe Sie datengebundene Steuerelemente erstellen können, müssen Sie ein Datenmodell für die Anwendung definieren und es dem **Datenquellenfenster** hinzufügen. In dieser exemplarischen Vorgehensweise erstellen Sie ein Dataset als Datenmodell.

1. Klicken Sie im Menü **Daten** auf **Datenquellen anzeigen**.

   Das Fenster **Datenquellen** wird geöffnet.

2. Klicken Sie im **Datenquellenfenster** auf **Neue Datenquelle hinzufügen**.

   Der **Assistent zum Konfigurieren von Datenquellen** wird geöffnet.

3. Wählen Sie auf der Seite **Datenquellentyp auswählen** die Option **Datenbank** aus, und klicken Sie dann auf **Weiter**.

4. Wählen Sie auf der Seite **Wählen Sie ein Datenbankmodell aus** die Option **DataSet** aus, und klicken Sie dann auf **Weiter**.

5. Wählen Sie auf der Seite **Wählen Sie Ihre Datenverbindung aus** eine der folgenden Optionen aus:

   - Wenn in der Dropdownliste eine Datenverbindung zur Beispieldatenbank „AdventureWorksLT“ verfügbar ist, wählen Sie diese aus, und klicken Sie anschließend auf **Weiter**.

   - Klicken Sie **Neue Verbindung**, und erstellen Sie eine Verbindung zur Datenbank AdventureWorksLT.

6. Wählen Sie auf der Seite **Verbindungszeichenfolge in der Anwendungskonfigurationsdatei speichern** das Kontrollkästchen **Ja, Verbindung speichern unter**, und klicken Sie anschließend auf **Weiter**.

7. Erweitern Sie auf der Seite **Datenbankobjekte auswählen** den Punkt **Tabellen**, und wählen Sie dann die Tabelle **Product (SalesLT)** aus.

8. Klicken Sie auf **Fertig stellen**.

   Visual Studio fügt ein neues `AdventureWorksLTDataSet.xsd` Datei dem Projekt, und fügt ein entsprechendes **AdventureWorksLTDataSet** Element für die **Datenquellen** Fenster. Die `AdventureWorksLTDataSet.xsd` -Datei definiert ein typisiertes Dataset namens `AdventureWorksLTDataSet` und einen TableAdapter namens `ProductTableAdapter`. Weiter unten in dieser exemplarischen Vorgehensweise verwenden Sie `ProductTableAdapter` für das Füllen des Datasets mit Daten und speichern die Änderungen zurück in die Datenbank.

9. Erstellen Sie das Projekt.

## <a name="edit-the-default-fill-method-of-the-tableadapter"></a>Bearbeiten Sie die Standard-Fill-Methode des TableAdapter

Verwenden Sie zum Füllen des Datasets die `Fill`-Methode des `ProductTableAdapter`. Standardmäßig füllt die `Fill`-Methode die `ProductDataTable` im `AdventureWorksLTDataSet` mit allen Datenzeilen aus der Product-Tabelle. Sie können diese Methode modifizieren, sodass nur eine Teilmenge von Zeilen zurückgeben wird. Ändern Sie für diese exemplarische Vorgehensweise die `Fill`-Methode, sodass nur Zeilen für Produkte zurückgegeben werden, die Fotos haben.

1. Öffnen Sie im **Projektmappen-Explorer** die Datei *AdventureWorksLTDataSet.xsd*.

     Der DataSet-Designer wird geöffnet.

2. Klicken Sie die Abfrage **Fill**, **GetData()** mit der rechten Maustaste, und wählen Sie **Konfigurieren** aus.

     Der **TableAdapter-Konfigurations-Assistent** wird geöffnet.

3. Fügen Sie auf der Seite **SQL-Anweisung eingeben** die folgende WHERE-Klausel nach der `SELECT`-Anweisung im Textfeld ein.

    ```sql
    WHERE ThumbnailPhotoFileName <> 'no_image_available_small.gif'
    ```

4. Klicken Sie auf **Fertig stellen**.

## <a name="define-the-user-interface"></a>Definieren der Benutzeroberfläche

Fügen Sie dem Fenster eine Reihe von Schaltflächen hinzu, indem Sie XAML im WPF-Designer ändern. Später in dieser exemplarischen Vorgehensweise fügen Sie dann Code hinzu, mit dem Anwender durch Produktdatensätze blättern und Änderungen daran mithilfe dieser Schaltflächen speichern können.

1. Doppelklicken Sie im **Projektmappen-Explorer** auf *MainWindow.xaml*.

    Das Fenster wird automatisch im **WPF-Designer** geöffnet.

2. Fügen Sie in der [!INCLUDE[TLA#tla_titlexaml](../data-tools/includes/tlasharptla_titlexaml_md.md)]-Ansicht des Designers den folgenden Code zwischen den `<Grid>`-Tags hinzu:

   ```xaml
   <Grid.RowDefinitions>
       <RowDefinition Height="75" />
       <RowDefinition Height="625" />
   </Grid.RowDefinitions>
   <Button HorizontalAlignment="Left" Margin="22,20,0,24" Name="backButton" Width="75"><</Button>
   <Button HorizontalAlignment="Left" Margin="116,20,0,24" Name="nextButton" Width="75">></Button>
   <Button HorizontalAlignment="Right" Margin="0,21,46,24" Name="saveButton" Width="110">Save changes</Button>
   ```

3. Erstellen Sie das Projekt.

## <a name="create-data-bound-controls"></a>Erstellen Sie datengebundene Steuerelemente.

Steuerelemente erstellen, die Kundendatensätze, indem Sie ziehen anzeigen die `Product` -Tabelle aus dem **Datenquellen** in den WPF-Designer.

1. Klicken Sie im **Datenquellenfenster** das Dropdownmenü für den Knoten **Product**, und klicken Sie auf **Details**.

2. Erweitern Sie den **Product**-Knoten.

3. In diesem Beispiel werden einige Felder nicht angezeigt. Klicken Sie also das Dropdownmenü neben den folgenden Knoten, und wählen Sie **Keine**:

    - ProductCategoryID

    - ProductModelID

    - ThumbnailPhotoFileName

    - rowguid

    - ModifiedDate

4. Klicken Sie auf das Dropdownmenü neben dem Knoten-**ThumbNailPhoto**, und wählen Sie **Bild**.

    > [!NOTE]
    > Standardmäßig haben Elemente im Fenster **Datenquellen**, die Bilder repräsentieren, als Steuerelementsatz **Kein** ausgewählt. Dies ist deshalb so, weil Bilder als Bytearrays in Datenbanken gespeichert werden und alles enthalten können, von einer einfachen Array an Bytes bis zur ausführbaren Datei einer großen Anwendung.

5. Ziehen Sie aus dem Fenster **Datenquellen** den Knoten **Product** auf das Raster unter der Zeile, in der die Schaltflächen sind.

     Visual Studio erzeugt XAML, der mehrere Steuerelemente definiert, die an Daten in der Tabelle **Products** gebunden sind. Es generiert außerdem Code, der die Daten lädt. Weitere Informationen zu den generierten XAML und Code finden Sie unter [Binden von WPF-Steuerelementen an Daten in Visual Studio](../data-tools/bind-wpf-controls-to-data-in-visual-studio.md).

6. Klicken Sie im Designer auf das Textfeld neben der Bezeichnung **Product ID**.

7. Aktivieren Sie im Fenster **Eigenschaften** das Kontrollkästchen neben der Eigenschaft **IsReadOnly**.

## <a name="navigate-product-records"></a>Durchsuchen Sie die Produktdatensätze

Fügen Sie Code hinzu, mit dessen Hilfe Benutzer durch die Produktdatensätze scrollen können, indem Sie die Schaltflächen **\<** und **>** verwenden.

1. Doppelklicken Sie im Designer die Schaltfläche **<** auf der Fensteroberfläche.

     Visual Studio öffnet die CodeBehind-Datei und erstellt einen neuen `backButton_Click`-Ereignishandler für das <xref:System.Windows.Controls.Primitives.ButtonBase.Click>-Ereignis.

2. Ändern Sie den `Window_Loaded`-Ereignishandler, sodass `ProductViewSource`, `AdventureWorksLTDataSet` und `AdventureWorksLTDataSetProductTableAdapter` sich außerhalb der Methode befinden und für das gesamte Formular zugänglich sind. Deklarieren Sie nur diese global für das Formular sein, und weisen sie in der `Window_Loaded` Ereignishandler, die etwa wie folgt:

     [!code-csharp[Data_WPFDATASET#1](../data-tools/codesnippet/CSharp/bind-wpf-controls-to-a-dataset_1.cs)]
     [!code-vb[Data_WPFDATASET#1](../data-tools/codesnippet/VisualBasic/bind-wpf-controls-to-a-dataset_1.vb)]

3. Fügen Sie dem `backButton_Click` -Ereignishandler folgenden Code hinzu:

     [!code-csharp[Data_WPFDATASET#2](../data-tools/codesnippet/CSharp/bind-wpf-controls-to-a-dataset_2.cs)]
     [!code-vb[Data_WPFDATASET#2](../data-tools/codesnippet/VisualBasic/bind-wpf-controls-to-a-dataset_2.vb)]

4. Kehren Sie zum Designer zurück, und doppelklicken Sie auf die Schaltfläche **>**.

5. Fügen Sie dem `nextButton_Click` -Ereignishandler folgenden Code hinzu:

     [!code-csharp[Data_WPFDATASET#3](../data-tools/codesnippet/CSharp/bind-wpf-controls-to-a-dataset_3.cs)]
     [!code-vb[Data_WPFDATASET#3](../data-tools/codesnippet/VisualBasic/bind-wpf-controls-to-a-dataset_3.vb)]

## <a name="save-changes-to-product-records"></a>Änderungen an Product Records speichern

Fügen Sie Code hinzu, mit dem Benutzer Änderungen an Product Records mithilfe der Taste **Änderungen speichern** speichern können.

1. Doppelklicken Sie im Designer auf die Schaltfläche **Änderungen speichern**.

     Visual Studio öffnet die CodeBehind-Datei und erstellt einen neuen `saveButton_Click`-Ereignishandler für das <xref:System.Windows.Controls.Primitives.ButtonBase.Click>-Ereignis.

2. Fügen Sie dem `saveButton_Click` -Ereignishandler folgenden Code hinzu:

     [!code-csharp[Data_WPFDATASET#4](../data-tools/codesnippet/CSharp/bind-wpf-controls-to-a-dataset_4.cs)]
     [!code-vb[Data_WPFDATASET#4](../data-tools/codesnippet/VisualBasic/bind-wpf-controls-to-a-dataset_4.vb)]

    > [!NOTE]
    > In diesem Beispiel wird die Methode `Save` des `TableAdapter` für das Speichern von Änderungen verwendet. Das ist in dieser exemplarischen Vorgehensweise angebracht, denn es wird nur eine Datentabelle geändert. Wenn Sie Änderungen an mehreren Datentabellen speichern möchten, können Sie alternativ die Methode `UpdateAll` des `TableAdapterManager` einsetzen, die Visual Studio mit dem Dataset generiert. Weitere Informationen finden Sie unter [TableAdapters](../data-tools/create-and-configure-tableadapters.md).

## <a name="test-the-application"></a>Testen der Anwendung

Erstellen Sie die Anwendung, und führen Sie sie aus. Stellen Sie sicher, dass Sie Produktdatensätze anzeigen und ändern können.

1. Drücken Sie **F5**.

     Die Anwendung wird erstellt und ausgeführt. Überprüfen Sie Folgendes:

    - Die Textfelder zeigen Daten aus dem ersten Produktdatensatz, der ein Foto hat. Dieses Produkt hat die ID 713 und heißt **Long-Sleeve Logo Jersey, S**.

    - Sie können auf die Schaltflächen **>** oder **<** für die Navigation durch andere Produktdatensätze klicken.

2. Ändern Sie in einem der Datensätze im Feld **Größe** den Wert, und klicken Sie anschließend auf **Änderungen speichern**.

3. Schließen Sie die Anwendung, und starten Sie dann die Anwendung in Visual Studio erneut, indem Sie **F5** drücken.

4. Navigieren Sie zum Produktdatensatz, den Sie geändert haben und prüfen Sie, ob die Änderung gespeichert wurde.

5. Schließen Sie die Anwendung.

## <a name="next-steps"></a>Nächste Schritte

Nach Abschluss dieser exemplarischen Vorgehensweise können Sie die nachstehenden verwandten Aufgaben versuchen:

- Erfahren Sie, wie Sie das **Datenquellenfenster** in Visual Studio für die Bindung von WPF-Steuerelementen an andere Typen von Datenquellen verwenden. Weitere Informationen finden Sie unter [Binden von WPF-Steuerelemente an einen WCF-Datendienst](../data-tools/bind-wpf-controls-to-a-wcf-data-service.md).

- Erfahren Sie, wie Sie das **Datenquellenfenster** in Visual Studio für die Anzeige zugehöriger Daten (das heißt, Daten in einer Beziehung zwischen übergeordneten und untergeordneten Daten) in WPF-Steuerelementen verwenden. Weitere Informationen finden Sie unter [Exemplarische Vorgehensweise: Anzeigen verknüpfter Daten in einer WPF-Anwendung](../data-tools/display-related-data-in-wpf-applications.md).

## <a name="see-also"></a>Siehe auch

- [Binden von WPF-Steuerelementen an Daten in Visual Studio](../data-tools/bind-wpf-controls-to-data-in-visual-studio.md)
- [Datasettools in Visual Studio](../data-tools/dataset-tools-in-visual-studio.md)
- [Übersicht zur Datenbindung](/dotnet/framework/wpf/data/data-binding-overview)
