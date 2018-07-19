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
manager: douge
ms.prod: visual-studio-dev15
ms.technology: vs-data-tools
ms.workload:
- data-storage
ms.openlocfilehash: aef6236b896495f81e91cbdd7befd2923c013a33
ms.sourcegitcommit: 7a11a094a353f2e2a2077ad863ca4c0fb97f7ec5
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 07/18/2018
ms.locfileid: "39131959"
---
# <a name="bind-wpf-controls-to-a-dataset"></a>Binden von WPF-Steuerelementen an ein Dataset

In dieser exemplarischen Vorgehensweise erstellen Sie eine WPF-Anwendung, die von datengebundenen Steuerelementen enthält. Die Steuerelemente sind an Produktdatensätze gebunden, die in einem Dataset gekapselt sind. Sie fügen außerdem Schaltflächen klicken, um Produkte durchsuchen, und speichern Änderungen an Product Records hinzu.

In dieser exemplarischen Vorgehensweise werden die folgenden Aufgaben veranschaulicht:

- Erstellen einer WPF-Anwendung und eines Datasets, das aus Daten in der Beispieldatenbank AdventureWorksLT generiert wird.

- Erstellen eines Satzes von datengebundenen Steuerelementen durch Ziehen einer Datentabelle aus dem **Datenquellen** zum Fenster im WPF-Designer.

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

1.  Starten Sie Visual Studio.

2.  Klicken Sie im Menü **Datei** auf **Neu** > **Projekt**.

3.  Erweitern Sie **Visual Basic** oder **Visual C#-**, und wählen Sie dann **Windows**.

4.  Wählen Sie die **WPF-Anwendung** Projektvorlage.

5.  In der **Namen** geben **AdventureWorksProductsEditor** und wählen Sie dann **OK**.

   Visual Studio erstellt das Projekt AdventureWorksProductsEditor.

## <a name="create-a-dataset-for-the-application"></a>Erstellen Sie ein Dataset für die Anwendung

Bevor Sie datengebundene Steuerelemente erstellen können, müssen Sie ein Datenmodell für Ihre Anwendung definieren und Hinzufügen der **Datenquellen** Fenster. In dieser exemplarischen Vorgehensweise erstellen Sie ein Dataset als Datenmodell.

1.  Klicken Sie im Menü **Daten** auf **Datenquellen anzeigen**.

     Die **Datenquellen** Fenster wird geöffnet.

2.  Klicken Sie im **Datenquellenfenster** auf **Neue Datenquelle hinzufügen**.

     Die **Datenquellenkonfiguration** -Assistent wird geöffnet.

3.  Auf der **wählen Sie einen Datenquellentyp** Seite **Datenbank**, und klicken Sie dann auf **Weiter**.

4.  Auf der **Auswählen eines Datenbankmodells** Seite **Dataset**, und klicken Sie dann auf **Weiter**.

5.  Auf der **wählen Sie Ihre Datenverbindung** Seite, wählen Sie eine der folgenden Optionen:

    - Wenn eine Datenverbindung mit der AdventureWorksLT-Beispieldatenbank in der Dropdown-Liste verfügbar ist, wählen Sie ihn, und klicken Sie dann auf **Weiter**.

    - Klicken Sie auf **neue Verbindung**, und erstellen Sie eine Verbindung mit der AdventureWorksLT-Datenbank.

6.  Auf der **Verbindungszeichenfolge in der Anwendungskonfigurationsdatei speichern** Seite die **Ja, Verbindung speichern unter** , und klicken Sie dann auf **Weiter**.

7.  Auf der **Datenbankobjekte auswählen** Seite **Tabellen**, und wählen Sie dann die **Product (SalesLT)** Tabelle.

8.  Klicken Sie auf **Fertig stellen**.

     Visual Studio fügt ein neues `AdventureWorksLTDataSet.xsd` Datei dem Projekt, und fügt ein entsprechendes **AdventureWorksLTDataSet** Element für die **Datenquellen** Fenster. Die `AdventureWorksLTDataSet.xsd` -Datei definiert ein typisiertes Dataset namens `AdventureWorksLTDataSet` und einen TableAdapter namens `ProductTableAdapter`. Weiter unten in dieser exemplarischen Vorgehensweise verwenden Sie `ProductTableAdapter` für das Füllen des Datasets mit Daten und speichern die Änderungen zurück in die Datenbank.

9. Erstellen Sie das Projekt.

## <a name="edit-the-default-fill-method-of-the-tableadapter"></a>Bearbeiten Sie die Standard-Fill-Methode des TableAdapter

Verwenden Sie zum Füllen des Datasets die `Fill`-Methode des `ProductTableAdapter`. Standardmäßig füllt die `Fill`-Methode die `ProductDataTable` im `AdventureWorksLTDataSet` mit allen Datenzeilen aus der Product-Tabelle. Sie können diese Methode modifizieren, sodass nur eine Teilmenge von Zeilen zurückgeben wird. Ändern Sie für diese exemplarische Vorgehensweise die `Fill`-Methode, sodass nur Zeilen für Produkte zurückgegeben werden, die Fotos haben.

1.  In **Projektmappen-Explorer**, doppelklicken Sie auf die *AdventureWorksLTDataSet.xsd* Datei.

     Der DataSet-Designer wird geöffnet.

2.  Klicken Sie im Designer mit der Maustaste der **füllen**, **GetData()** abzufragen, und wählen Sie **konfigurieren**.

     Die **TableAdapter-Konfigurations** -Assistent wird geöffnet.

3.  In der **Geben Sie eine SQL-Anweisung** Seite, die folgende WHERE-Klausel nach dem Hinzufügen der `SELECT` -Anweisung in das Textfeld ein.

    ```sql
    WHERE ThumbnailPhotoFileName <> 'no_image_available_small.gif'
    ```

4.  Klicken Sie auf **Fertig stellen**.

## <a name="define-the-user-interface"></a>Definieren der Benutzeroberfläche

Fügen Sie dem Fenster eine Reihe von Schaltflächen hinzu, indem Sie XAML im WPF-Designer ändern. Später in dieser exemplarischen Vorgehensweise fügen Sie dann Code hinzu, mit dem Anwender durch Produktdatensätze blättern und Änderungen daran mithilfe dieser Schaltflächen speichern können.

1.  In **Projektmappen-Explorer**, doppelklicken Sie auf *"MainWindow.xaml"*.

     Das Fenster wird geöffnet, der **WPF-Designer**.

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

## <a name="create-data-bound-controls"></a>Erstellen von datengebundenen Steuerelementen

Steuerelemente erstellen, die Kundendatensätze, indem Sie ziehen anzeigen die `Product` -Tabelle aus dem **Datenquellen** in den WPF-Designer.

1.  In der **Datenquellen** Fenster, klicken Sie auf das Dropdownmenü für die **Produkt** Knoten, und wählen **Details**.

2.  Erweitern Sie die **Produkt** Knoten.

3.  In diesem Beispiel einige Felder werden nicht angezeigt, daher klicken Sie auf das Dropdownmenü neben den folgenden Knoten und anschließend auf **keine**:

    - ProductCategoryID

    - ProductModelID

    - ThumbnailPhotoFileName

    - rowguid

    - ModifiedDate

4.  Klicken Sie auf das Dropdownmenü neben der **ThumbNailPhoto** Knoten, und wählen **Image**.

    > [!NOTE]
    > Standardmäßig haben Elemente der **Datenquellen** Fenster, das Darstellen von Bildern haben Steuerelementsatz zum **keine**. Dies ist deshalb so, weil Bilder als Bytearrays in Datenbanken gespeichert werden und alles enthalten können, von einer einfachen Array an Bytes bis zur ausführbaren Datei einer großen Anwendung.

5.  Von der **Datenquellen** ziehen Sie die **Produkt** Knoten auf das Raster unter der Zeile, die die Schaltflächen enthält.

     Visual Studio generiert XAML, die einen Satz von Steuerelementen definiert, die an Daten gebunden sind, die **Produkte** Tabelle. Es generiert außerdem Code, der die Daten lädt. Weitere Informationen zu den generierten XAML und Code finden Sie unter [Binden von WPF-Steuerelementen an Daten in Visual Studio](../data-tools/bind-wpf-controls-to-data-in-visual-studio.md).

6.  Im Designer, klicken Sie auf das Textfeld neben der **Produkt-ID** Bezeichnung.

7.  In der **Eigenschaften** wählen Sie im Fenster das Kontrollkästchen neben den **IsReadOnly** Eigenschaft.

## <a name="navigate-product-records"></a>Durchsuchen Sie die Produktdatensätze

Hinzufügen von Code, der Benutzern ermöglicht, durch die Produktdatensätze Scrollen Sie mithilfe der **\<** und **>** Schaltflächen.

1.  Doppelklicken Sie im Designer auf die **<** Schaltfläche auf der Fensteroberfläche.

     Visual Studio öffnet die CodeBehind-Datei und erstellt ein neues `backButton_Click` -Ereignishandler für die <xref:System.Windows.Controls.Primitives.ButtonBase.Click> Ereignis.

2.  Ändern der `Window_Loaded` -Ereignishandler daher `ProductViewSource`, `AdventureWorksLTDataSet`, und `AdventureWorksLTDataSetProductTableAdapter` außerhalb der Methode und für das gesamte Formular zugänglich sind. Deklarieren Sie nur diese global für das Formular sein, und weisen sie in der `Window_Loaded` Ereignishandler, die etwa wie folgt:

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

Hinzufügen von Code, der Benutzern ermöglicht, das Speichern von Änderungen an Product Records mithilfe der **speichern Änderungen** Schaltfläche.

1.  Doppelklicken Sie im Designer auf die **speichern Änderungen** Schaltfläche.

     Visual Studio öffnet die CodeBehind-Datei und erstellt ein neues `saveButton_Click` -Ereignishandler für die <xref:System.Windows.Controls.Primitives.ButtonBase.Click> Ereignis.

2.  Fügen Sie dem `saveButton_Click`-Ereignishandler folgenden Code hinzu:

     [!code-csharp[Data_WPFDATASET#4](../data-tools/codesnippet/CSharp/bind-wpf-controls-to-a-dataset_4.cs)]
     [!code-vb[Data_WPFDATASET#4](../data-tools/codesnippet/VisualBasic/bind-wpf-controls-to-a-dataset_4.vb)]

    > [!NOTE]
    > In diesem Beispiel wird die Methode `Save` des `TableAdapter` für das Speichern von Änderungen verwendet. Das ist in dieser exemplarischen Vorgehensweise angebracht, denn es wird nur eine Datentabelle geändert. Wenn Sie Änderungen an mehreren Datentabellen speichern möchten, können Sie alternativ die Methode `UpdateAll` des `TableAdapterManager` einsetzen, die Visual Studio mit dem Dataset generiert. Weitere Informationen finden Sie unter [TableAdapters](../data-tools/create-and-configure-tableadapters.md).

## <a name="test-the-application"></a>Testen der Anwendung

Erstellen Sie die Anwendung, und führen Sie sie aus. Stellen Sie sicher, dass Sie Produktdatensätze anzeigen und ändern können.

1.  Drücken Sie **F5**.

     Die Anwendung wird erstellt und ausgeführt. Überprüfen Sie Folgendes:

    - Die Textfelder zeigen Daten aus dem ersten Produktdatensatz, der ein Foto hat. Dieses Produkt hat die Produkt-ID 713 und den Namen **Long-Sleeve Logo Jersey, S**.

    - Klicken Sie auf die **>** oder **<** Schaltflächen zum Navigieren durch andere Produktdatensätze.

2.  Ändern Sie in einem der Datensätze, die **Größe** Wert ein, und klicken Sie dann auf **speichern Änderungen**.

3.  Schließen Sie die Anwendung, und wiederholen Sie die Anwendung durch Drücken von **F5** in Visual Studio.

4.  Navigieren Sie zum Produktdatensatz, den Sie geändert haben und prüfen Sie, ob die Änderung gespeichert wurde.

5.  Schließen Sie die Anwendung.

## <a name="next-steps"></a>Nächste Schritte

Nach Abschluss dieser exemplarischen Vorgehensweise können Sie die nachstehenden verwandten Aufgaben versuchen:

- Erfahren Sie, wie Sie mit der **Datenquellen** Fenster in Visual Studio zum Binden von WPF-Steuerelementen an andere Typen von Datenquellen. Weitere Informationen finden Sie unter [Binden von WPF-Steuerelemente an einen WCF-Datendienst](../data-tools/bind-wpf-controls-to-a-wcf-data-service.md).

- Erfahren Sie, wie Sie mit der **Datenquellen** Fenster in Visual Studio zum Anzeigen von verwandter Daten (d. h. Daten in einer über-/ unterordnungsbeziehung) in WPF-Steuerelementen. Weitere Informationen finden Sie unter [Exemplarische Vorgehensweise: Anzeigen verknüpfter Daten in einer WPF-Anwendung](../data-tools/display-related-data-in-wpf-applications.md).

## <a name="see-also"></a>Siehe auch

- [Binden von WPF-Steuerelementen an Daten in Visual Studio](../data-tools/bind-wpf-controls-to-data-in-visual-studio.md)
- [Datasettools in Visual Studio](../data-tools/dataset-tools-in-visual-studio.md)
- [Übersicht zur Datenbindung](/dotnet/framework/wpf/data/data-binding-overview)
