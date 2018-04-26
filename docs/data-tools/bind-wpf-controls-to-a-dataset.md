---
title: Binden von WPF-Steuerelementen zu einem dataset
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
manager: douge
ms.prod: visual-studio-dev15
ms.technology: vs-data-tools
ms.workload:
- data-storage
ms.openlocfilehash: bd0aa9ae269da4cfd4ae5ab3dfb45e96052d75fe
ms.sourcegitcommit: e13e61ddea6032a8282abe16131d9e136a927984
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/26/2018
---
# <a name="bind-wpf-controls-to-a-dataset"></a>Binden von WPF-Steuerelementen zu einem dataset
In dieser exemplarischen Vorgehensweise erstellen Sie eine WPF-Anwendung, die datengebundene Steuerelemente enthält. Die Steuerelemente sind an Produktdatensätze gebunden, die in einem Dataset gekapselt sind. Sie fügen außerdem Schaltflächen hinzu, mit denen es möglich ist, Produkte zu durchsuchen und Änderungen an Produktdatensätzen zu speichern.

In dieser exemplarischen Vorgehensweise werden die folgenden Aufgaben veranschaulicht:

- Erstellen einer WPF-Anwendung und eines Datasets, das aus Daten in der Beispieldatenbank AdventureWorksLT generiert wird.

- Erstellen eines Satzes von datengebundene Steuerelemente durch Ziehen einer Datentabelle aus dem **Datenquellen** zum Fenster im WPF-Designer.

- Erstellen von Schaltflächen, mit denen die Navigation vorwärts und rückwärts durch die Produktdatensätze möglich ist.

- Erstellen einer Schaltfläche, die Änderungen durch Kunden an den Produktdatensätzen in der Tabelle und der darunterliegenden Datenquelle speichert.

[!INCLUDE[note_settings_general](../data-tools/includes/note_settings_general_md.md)]

## <a name="prerequisites"></a>Erforderliche Komponenten
Zum Durchführen dieser exemplarischen Vorgehensweise benötigen Sie die folgenden Komponenten:

-   [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)]

-   Zugriff auf eine laufende Instanz von SQL Server oder SQL Server Express, an die eine AdventureWorksLT-Beispieldatenbank angefügt ist. Sie können die AdventureWorksLT-datenbankvon der [CodePlex-Website](http://go.microsoft.com/fwlink/?linkid=87843).

Vorkenntnisse der folgenden Konzepte sind ebenfalls hilfreich, wenn auch für die Durchführung der exemplarischen Vorgehensweise nicht erforderlich:

-   DataSets und TableAdapters. Weitere Informationen finden Sie unter [Dataset-Tools in Visual Studio](../data-tools/dataset-tools-in-visual-studio.md) und [TableAdapter](../data-tools/create-and-configure-tableadapters.md).

-   WPF-Datenbindung. Weitere Informationen finden Sie unter [Übersicht über Datenbindung](/dotnet/framework/wpf/data/data-binding-overview).

## <a name="create-the-project"></a>Erstellen eines Projekts
 Erstellen eines neuen WPF-Projekts. Das Projekt zeigt Produktdatensätze.

#### <a name="to-create-the-project"></a>So erstellen Sie das Projekt

1.  Starten Sie Visual Studio.

2.  Zeigen Sie im Menü **Datei** auf **Neu**, und klicken Sie dann auf **Projekt**.

3.  Erweitern Sie **Visual Basic** oder **Visual C#-**, und wählen Sie dann **Windows**.

4.  Wählen Sie die **WPF-Anwendung** -Projektvorlage.

5.  In der **Namen** geben `AdventureWorksProductsEditor` , und klicken Sie auf **OK**.

     Visual Studio erstellt das `AdventureWorksProductsEditor` Projekt.

## <a name="create-a-dataset-for-the-application"></a>Erstellen Sie ein Dataset für die Anwendung
 Bevor Sie datengebundene Steuerelemente erstellen können, müssen Sie ein Datenmodell für die Anwendung definieren und Hinzufügen zu den **Datenquellen** Fenster. In dieser exemplarischen Vorgehensweise erstellen Sie ein Dataset als Datenmodell.

#### <a name="to-create-a-dataset"></a>So erstellen Sie ein DataSet

1.  Klicken Sie im Menü **Daten** auf **Datenquellen anzeigen**.

     Die **Datenquellen** Fenster wird geöffnet.

2.  Klicken Sie im **Datenquellenfenster** auf **Neue Datenquelle hinzufügen**.

     Die **Datenquellenkonfiguration** -Assistent wird geöffnet.

3.  Auf der **wählen Sie einen Datenquellentyp** Seite **Datenbank**, und klicken Sie dann auf **Weiter**.

4.  Auf der **Auswählen eines Datenbankmodells** Seite **Dataset**, und klicken Sie dann auf **Weiter**.

5.  Auf der **wählen Sie Ihre Datenverbindung** Seite, wählen Sie eine der folgenden Optionen:

    -   Wenn eine Datenverbindung zur Beispieldatenbank "AdventureWorksLT" verfügbar, in der Dropdown-Liste ist, wählen Sie ihn, und klicken Sie dann auf **Weiter**.

    -   Klicken Sie auf **neue Verbindung**, und erstellen Sie eine Verbindung zur Datenbank AdventureWorksLT.

6.  Auf der **Verbindungszeichenfolge in der Anwendungskonfigurationsdatei speichern** Seite der **Ja, Verbindung speichern unter** Kontrollkästchen, und klicken Sie dann auf **Weiter**.

7.  Auf der **Datenbankobjekte auswählen** Seite **Tabellen**, und wählen Sie dann die **Product (SalesLT)** Tabelle.

8.  Klicken Sie auf **Fertig stellen**.

     Visual Studio fügt ein neues `AdventureWorksLTDataSet.xsd` Datei an das Projekt, und fügt ein entsprechendes **AdventureWorksLTDataSet** Element zum der **Datenquellen** Fenster. Die `AdventureWorksLTDataSet.xsd` -Datei definiert ein typisiertes Dataset namens `AdventureWorksLTDataSet` und einen TableAdapter namens `ProductTableAdapter`. Weiter unten in dieser exemplarischen Vorgehensweise verwenden Sie `ProductTableAdapter` für das Füllen des Datasets mit Daten und speichern die Änderungen zurück in die Datenbank.

9. Erstellen Sie das Projekt.

## <a name="edit-the-default-fill-method-of-the-tableadapter"></a>Bearbeiten Sie die Standard-Fill-Methode des TableAdapter
 Verwenden Sie zum Füllen des Datasets die `Fill`-Methode des `ProductTableAdapter`. Standardmäßig füllt die `Fill`-Methode die `ProductDataTable` im `AdventureWorksLTDataSet` mit allen Datenzeilen aus der Product-Tabelle. Sie können diese Methode modifizieren, sodass nur eine Teilmenge von Zeilen zurückgeben wird. Ändern Sie für diese exemplarische Vorgehensweise die `Fill`-Methode, sodass nur Zeilen für Produkte zurückgegeben werden, die Fotos haben.

#### <a name="to-load-product-rows-that-have-photos"></a>So laden Sie Produktzeilen, die Fotos haben

1.  In **Projektmappen-Explorer**, doppelklicken Sie auf die `AdventureWorksLTDataSet.xsd` Datei.

     Der DataSet-Designer wird geöffnet.

2.  Klicken Sie im Designer mit der Maustaste die **zu füllen, GetData()** abzufragen, und wählen Sie **konfigurieren**.

     Die **TableAdapter-Konfigurations** -Assistent wird geöffnet.

3.  In der **Geben Sie eine SQL-Anweisung** Seite, die folgende WHERE-Klausel nach dem Hinzufügen der `SELECT` -Anweisung in das Textfeld.

    ```
    WHERE ThumbnailPhotoFileName <> 'no_image_available_small.gif'
    ```

4.  Klicken Sie auf **Fertig stellen**.

## <a name="define-the-user-interface"></a>Definieren der Benutzeroberfläche
 Fügen Sie dem Fenster eine Reihe von Schaltflächen hinzu, indem Sie XAML im WPF-Designer ändern. Später in dieser exemplarischen Vorgehensweise fügen Sie dann Code hinzu, mit dem Anwender durch Produktdatensätze blättern und Änderungen daran mithilfe dieser Schaltflächen speichern können.

#### <a name="to-define-the-user-interface-of-the-window"></a>Die Benutzeroberfläche des Fensters definieren

1.  In **Projektmappen-Explorer**, doppelklicken Sie auf "MainWindow.xaml".

     Das Fenster wird automatisch im WPF-Designer geöffnet.

2.  Fügen Sie in der [!INCLUDE[TLA#tla_titlexaml](../data-tools/includes/tlasharptla_titlexaml_md.md)]-Ansicht des Designers den folgenden Code zwischen den `<Grid>`-Tags hinzu:

    ```xaml
    <Grid.RowDefinitions>
        <RowDefinition Height="75" />
        <RowDefinition Height="625" />
    </Grid.RowDefinitions>
    <Button HorizontalAlignment="Left" Margin="22,20,0,24" Name="backButton" Width="75"><</Button>
    <Button HorizontalAlignment="Left" Margin="116,20,0,24" Name="nextButton" Width="75">></Button>
    <Button HorizontalAlignment="Right" Margin="0,21,46,24" Name="saveButton" Width="110">Save changes</Button>
    ```

3.  Erstellen Sie das Projekt.

## <a name="create-data-bound-controls"></a>Erstellen Sie datengebundene Steuerelemente
 Erstellen Sie Steuerelemente, die Kundendatensätze, indem Sie ziehen anzeigen die `Product` Tabelle aus der **Datenquellen** in den WPF-Designer.

#### <a name="to-create-data-bound-controls"></a>So erstellen Sie datengebundene Steuerelemente

1.  In der **Datenquellen** Fenster, klicken Sie auf das Dropdownmenü für die **Produkt** Knoten, und wählen **Details**.

2.  Erweitern Sie die **Produkt** Knoten.

3.  In diesem Beispiel einige Felder nicht angezeigt, so klicken Sie auf das Dropdownmenü neben den folgenden Knoten und wählen Sie **keine**:

    -   ProductCategoryID

    -   ProductModelID

    -   ThumbnailPhotoFileName

    -   rowguid

    -   ModifiedDate

4.  Klicken Sie auf das Dropdownmenü neben den **ThumbNailPhoto** Knoten, und wählen **Image**.

    > [!NOTE]
    >  Standardmäßig Elemente in der **Datenquellen** Fenster, das Bilder repräsentieren haben Steuerelementsatz zum **keine**. Dies ist deshalb so, weil Bilder als Bytearrays in Datenbanken gespeichert werden und alles enthalten können, von einer einfachen Array an Bytes bis zur ausführbaren Datei einer großen Anwendung.

5.  Aus der **Datenquellen** Fenster, ziehen Sie die **Produkt** Knoten auf das Raster unter der Zeile, die die Schaltflächen enthält.

     Visual Studio generiert XAML, das einen Satz von Steuerelementen definiert, die an Daten gebunden werden die **Produkte** Tabelle. Es generiert außerdem Code, der die Daten lädt. Weitere Informationen über die generierten XAML und generierter Code finden Sie unter [Binden von WPF-Steuerelementen an Daten in Visual Studio](../data-tools/bind-wpf-controls-to-data-in-visual-studio.md).

6.  Im Designer, klicken Sie auf das Textfeld neben der **Produkt-ID** Bezeichnung.

7.  In der **Eigenschaften** Fenster, wählen Sie das Kontrollkästchen neben den **IsReadOnly** Eigenschaft.

## <a name="navigating-product-records"></a>Navigieren durch Product records
 Fügen Sie Code, der Benutzern ermöglicht, durch die Produktdatensätze scrollen, mithilfe der **\<** und **>** Schaltflächen.

#### <a name="to-enable-users-to-navigate-product-records"></a>Benutzern das Navigieren durch Product Records ermöglichen

1.  Doppelklicken Sie im Designer auf die **<** Schaltfläche auf der Fensteroberfläche.

     Visual Studio öffnet die CodeBehind-Datei und erstellt ein neues `backButton_Click` -Ereignishandler für das <xref:System.Windows.Controls.Primitives.ButtonBase.Click> Ereignis.

2.  Ändern der `Window_Loaded` Ereignishandler, sodass die `ProductViewSource`, `AdventureWorksLTDataSet`, und `AdventureWorksLTDataSetProductTableAdapter` außerhalb der Methode und für das gesamte Formular zugänglich sind. Deklarieren Sie nur diese als global für das Formular, und weisen sie in der `Window_Loaded` -Ereignishandler der folgenden ähnelt:

     [!code-csharp[Data_WPFDATASET#1](../data-tools/codesnippet/CSharp/bind-wpf-controls-to-a-dataset_1.cs)]
     [!code-vb[Data_WPFDATASET#1](../data-tools/codesnippet/VisualBasic/bind-wpf-controls-to-a-dataset_1.vb)]

3.  Fügen Sie dem `backButton_Click`-Ereignishandler folgenden Code hinzu:

     [!code-csharp[Data_WPFDATASET#2](../data-tools/codesnippet/CSharp/bind-wpf-controls-to-a-dataset_2.cs)]
     [!code-vb[Data_WPFDATASET#2](../data-tools/codesnippet/VisualBasic/bind-wpf-controls-to-a-dataset_2.vb)]

4.  Zurück zu den Designer und doppelklicken Sie auf die **>** Schaltfläche.

5.  Fügen Sie dem `nextButton_Click`-Ereignishandler folgenden Code hinzu:

     [!code-csharp[Data_WPFDATASET#3](../data-tools/codesnippet/CSharp/bind-wpf-controls-to-a-dataset_3.cs)]
     [!code-vb[Data_WPFDATASET#3](../data-tools/codesnippet/VisualBasic/bind-wpf-controls-to-a-dataset_3.vb)]

## <a name="save-changes-to-product-records"></a>Änderungen an Product Records speichern
Hinzufügen von Code, der ermöglicht Benutzern das Speichern von Änderungen an Product Records mithilfe der **Änderungen speichern** Schaltfläche.

#### <a name="to-add-the-ability-to-save-changes-to-product-records"></a>Die Möglichkeit zum Speichern von Änderungen zu Product Records hinzufügen

1.  Doppelklicken Sie im Designer auf die **Änderungen speichern** Schaltfläche.

     Visual Studio öffnet die CodeBehind-Datei und erstellt ein neues `saveButton_Click` -Ereignishandler für das <xref:System.Windows.Controls.Primitives.ButtonBase.Click> Ereignis.

2.  Fügen Sie dem `saveButton_Click`-Ereignishandler folgenden Code hinzu:

     [!code-csharp[Data_WPFDATASET#4](../data-tools/codesnippet/CSharp/bind-wpf-controls-to-a-dataset_4.cs)]
     [!code-vb[Data_WPFDATASET#4](../data-tools/codesnippet/VisualBasic/bind-wpf-controls-to-a-dataset_4.vb)]

    > [!NOTE]
    >  In diesem Beispiel wird die Methode `Save` des `TableAdapter` für das Speichern von Änderungen verwendet. Das ist in dieser exemplarischen Vorgehensweise angebracht, denn es wird nur eine Datentabelle geändert. Wenn Sie Änderungen an mehreren Datentabellen speichern möchten, können Sie alternativ die Methode `UpdateAll` des `TableAdapterManager` einsetzen, die Visual Studio mit dem Dataset generiert. Weitere Informationen finden Sie unter [TableAdapters](../data-tools/create-and-configure-tableadapters.md).

## <a name="test-the-application"></a>Testen der Anwendung
 Erstellen Sie die Anwendung, und führen Sie sie aus. Stellen Sie sicher, dass Sie Produktdatensätze anzeigen und ändern können.

#### <a name="to-test-the-application"></a>So testen Sie die Anwendung

1.  Drücken Sie **F5**.

     Die Anwendung wird erstellt und ausgeführt. Überprüfen Sie Folgendes:

    -   Die Textfelder zeigen Daten aus dem ersten Produktdatensatz, der ein Foto hat. Dieses Produkt hat die Produkt-ID 713 und den Namen **Long-Sleeve Logo Jersey, S**.

    -   Klicken Sie auf die **>** oder **<** Schaltflächen zum Navigieren durch andere Produktdatensätze.

2.  Ändern Sie in einem der Datensätze, die **Größe** -Wert aus, und klicken Sie dann auf **Änderungen speichern**.

3.  Schließen Sie die Anwendung, und starten Sie die Anwendung durch Drücken von **F5** in Visual Studio.

4.  Navigieren Sie zum Produktdatensatz, den Sie geändert haben und prüfen Sie, ob die Änderung gespeichert wurde.

5.  Schließen Sie die Anwendung.

## <a name="next-steps"></a>Nächste Schritte
 Nach Abschluss dieser exemplarischen Vorgehensweise können Sie folgende Aufgaben ausführen:

-   Informationen zum Verwenden der **Datenquellen** in Visual Studio für die Bindung von WPF-Steuerelementen an andere Typen von Datenquellen. Weitere Informationen finden Sie unter [Binden von WPF-Steuerelementen an einen WCF-Datendienst](../data-tools/bind-wpf-controls-to-a-wcf-data-service.md).

-   Informationen zum Verwenden der **Datenquellen** in Visual Studio für die Anzeige zugehöriger Daten (d. h. Daten in einer über-/ unterordnungsbeziehung) in WPF-Steuerelemente. Weitere Informationen finden Sie unter [Exemplarische Vorgehensweise: Anzeigen von verknüpften Daten in einer WPF-Anwendung](../data-tools/display-related-data-in-wpf-applications.md).

## <a name="see-also"></a>Siehe auch

- [Binden von WPF-Steuerelementen an Daten in Visual Studio](../data-tools/bind-wpf-controls-to-data-in-visual-studio.md)
- [Datasettools in Visual Studio](../data-tools/dataset-tools-in-visual-studio.md)
- [Übersicht zur Datenbindung](/dotnet/framework/wpf/data/data-binding-overview)