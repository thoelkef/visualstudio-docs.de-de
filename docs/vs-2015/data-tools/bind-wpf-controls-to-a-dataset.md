---
title: Binden von WPF-Steuerelementen zu einem Dataset | Microsoft-Dokumentation
ms.custom: ''
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
dev_langs:
- VB
- CSharp
- C++
- aspx
helpviewer_keywords:
- WPF, data binding in Visual Studio
- WPF data binding [Visual Studio], walkthroughs
- WPF Designer, data binding
ms.assetid: 177420b9-568b-4dad-9d16-1b0e98a24d71
caps.latest.revision: 35
author: gewarren
ms.author: gewarren
manager: ghogen
ms.openlocfilehash: 19189e63a3fb3fdfa3016cb2643cc34a193a2a52
ms.sourcegitcommit: 240c8b34e80952d00e90c52dcb1a077b9aff47f6
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 10/23/2018
ms.locfileid: "49892999"
---
# <a name="bind-wpf-controls-to-a-dataset"></a>Binden von WPF-Steuerelementen an ein Dataset
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

  
In dieser exemplarischen Vorgehensweise erstellen Sie eine WPF-Anwendung, die datengebundene Steuerelemente enthält. Die Steuerelemente sind an Produktdatensätze gebunden, die in einem Dataset gekapselt sind. Sie fügen außerdem Schaltflächen hinzu, mit denen es möglich ist, Produkte zu durchsuchen und Änderungen an Produktdatensätzen zu speichern.  
  
 In dieser exemplarischen Vorgehensweise werden die folgenden Aufgaben veranschaulicht:  
  
- Erstellen einer WPF-Anwendung und eines Datasets, das aus Daten in der Beispieldatenbank AdventureWorksLT generiert wird.  
  
- Erstellen eines Satzes von datengebundenen Steuerelementen durch Ziehen einer Datentabelle aus dem **Datenquellen** zum Fenster im WPF-Designer.  
  
- Erstellen von Schaltflächen, mit denen die Navigation vorwärts und rückwärts durch die Produktdatensätze möglich ist.  
  
- Erstellen einer Schaltfläche, die Änderungen durch Kunden an den Produktdatensätzen in der Tabelle und der darunterliegenden Datenquelle speichert.  
  
   [!INCLUDE[note_settings_general](../includes/note-settings-general-md.md)]  
  
## <a name="prerequisites"></a>Vorraussetzungen  
 Zum Durchführen dieser exemplarischen Vorgehensweise benötigen Sie die folgenden Komponenten:  
  
- [!INCLUDE[vsprvs](../includes/vsprvs-md.md)]  
  
- Zugriff auf eine laufende Instanz von SQL Server oder SQL Server Express, an die eine AdventureWorksLT-Beispieldatenbank angefügt ist. Sie können die AdventureWorksLT-datenbankvon der [CodePlex-Website](http://go.microsoft.com/fwlink/?linkid=87843).  
  
  Vorkenntnisse der folgenden Konzepte sind ebenfalls hilfreich, wenn auch für die Durchführung der exemplarischen Vorgehensweise nicht erforderlich:  
  
- DataSets und TableAdapters. Weitere Informationen finden Sie unter [datasettools in Visual Studio](../data-tools/dataset-tools-in-visual-studio.md) und [Übersicht über TableAdapters](../data-tools/tableadapter-overview.md).  
  
- Arbeiten mit dem WPF-Designer. Weitere Informationen finden Sie unter [WPF- und Silverlight Designer Overview](http://msdn.microsoft.com/en-us/570b7a5c-0c86-4326-a371-c9b63378fc62).  
  
- WPF-Datenbindung. Weitere Informationen finden Sie unter [Übersicht über Datenbindung](http://msdn.microsoft.com/library/c707c95f-7811-401d-956e-2fffd019a211).  
  
## <a name="create-the-project"></a>Erstellen eines Projekts  
 Erstellen eines neuen WPF-Projekts. Das Projekt zeigt Produktdatensätze.  
  
#### <a name="to-create-the-project"></a>So erstellen Sie das Projekt  
  
1.  Starten Sie Visual Studio.  
  
2.  Zeigen Sie im Menü **Datei** auf **Neu**, und klicken Sie dann auf **Projekt**.  
  
3.  Erweitern Sie **Visual Basic** oder **Visual C#-**, und wählen Sie dann **Windows**.  
  
4.  Wählen Sie die **WPF-Anwendung** Projektvorlage.  
  
5.  In der **Namen** geben `AdventureWorksProductsEditor` , und klicken Sie auf **OK**.  
  
     Visual Studio erstellt die `AdventureWorksProductsEditor` Projekt.  
  
## <a name="create-a-dataset-for-the-application"></a>Erstellen Sie ein Dataset für die Anwendung  
 Bevor Sie datengebundene Steuerelemente erstellen können, müssen Sie ein Datenmodell für Ihre Anwendung definieren und Hinzufügen der **Datenquellen** Fenster. In dieser exemplarischen Vorgehensweise erstellen Sie ein Dataset als Datenmodell.  
  
#### <a name="to-create-a-dataset"></a>So erstellen Sie ein DataSet  
  
1.  Klicken Sie im Menü **Daten** auf **Datenquellen anzeigen**.  
  
     Die **Datenquellen** Fenster wird geöffnet.  
  
2.  Klicken Sie im **Datenquellenfenster** auf **Neue Datenquelle hinzufügen**.  
  
     Die **Datenquellenkonfiguration**-Assistent wird geöffnet.  
  
3.  Auf der **wählen Sie einen Datenquellentyp** Seite **Datenbank**, und klicken Sie dann auf **Weiter**.  
  
4.  Auf der **Auswählen eines Datenbankmodells** Seite **Dataset**, und klicken Sie dann auf **Weiter**.  
  
5.  Auf der **wählen Sie Ihre Datenverbindung** Seite, wählen Sie eine der folgenden Optionen:  
  
    -   Wenn eine Datenverbindung mit der AdventureWorksLT-Beispieldatenbank in der Dropdown-Liste verfügbar ist, wählen Sie ihn, und klicken Sie dann auf **Weiter**.  
  
    -   Klicken Sie auf **neue Verbindung**, und erstellen Sie eine Verbindung mit der AdventureWorksLT-Datenbank.  
  
6.  Auf der **Verbindungszeichenfolge in der Anwendungskonfigurationsdatei speichern** Seite die **Ja, Verbindung speichern unter** , und klicken Sie dann auf **Weiter**.  
  
7.  Auf der **Datenbankobjekte auswählen** Seite **Tabellen**, und wählen Sie dann die **Product (SalesLT)** Tabelle.  
  
8.  Klicken Sie auf **Fertig stellen**.  
  
     Visual Studio fügt eine neue Datei AdventureWorksLTDataSet.xsd zum Projekt und fügt ein entsprechendes **AdventureWorksLTDataSet** Element für die **Datenquellen** Fenster. Die Datei AdventureWorksLTDataSet.xsd definiert ein typisiertes Dataset namens `AdventureWorksLTDataSet` und einen TableAdapter namens `ProductTableAdapter`. Weiter unten in dieser exemplarischen Vorgehensweise verwenden Sie `ProductTableAdapter` für das Füllen des Datasets mit Daten und speichern die Änderungen zurück in die Datenbank.  
  
9. Erstellen Sie das Projekt.  
  
## <a name="edit-the-default-fill-method-of-the-tableadapter"></a>Bearbeiten Sie die Standard-Fill-Methode des TableAdapter  
 Verwenden Sie zum Füllen des Datasets die `Fill`-Methode des `ProductTableAdapter`. Standardmäßig füllt die `Fill`-Methode die `ProductDataTable` im `AdventureWorksLTDataSet` mit allen Datenzeilen aus der Product-Tabelle. Sie können diese Methode modifizieren, sodass nur eine Teilmenge von Zeilen zurückgeben wird. Ändern Sie für diese exemplarische Vorgehensweise die `Fill`-Methode, sodass nur Zeilen für Produkte zurückgegeben werden, die Fotos haben.  
  
#### <a name="to-load-product-rows-that-have-photos"></a>So laden Sie Produktzeilen, die Fotos haben  
  
1.  In **Projektmappen-Explorer**, doppelklicken Sie auf die Datei "AdventureWorksLTDataSet.xsd".  
  
     Der DataSet-Designer wird geöffnet.  
  
2.  Klicken Sie im Designer mit der Maustaste der **Fill,GetData()** abzufragen, und wählen Sie **konfigurieren**.  
  
     Die **TableAdapter-Konfigurations**-Assistent wird geöffnet.  
  
3.  In der **Geben Sie eine SQL-Anweisung** Seite, die folgende WHERE-Klausel nach dem Hinzufügen der `SELECT` -Anweisung in das Textfeld ein.  
  
    ```  
    WHERE ThumbnailPhotoFileName <> 'no_image_available_small.gif'  
    ```  
  
4.  Klicken Sie auf **Fertig stellen**.  
  
## <a name="define-the-user-interface"></a>Definieren der Benutzeroberfläche  
 Fügen Sie dem Fenster eine Reihe von Schaltflächen hinzu, indem Sie XAML im WPF-Designer ändern. Später in dieser exemplarischen Vorgehensweise fügen Sie dann Code hinzu, mit dem Anwender durch Produktdatensätze blättern und Änderungen daran mithilfe dieser Schaltflächen speichern können.  
  
#### <a name="to-define-the-user-interface-of-the-window"></a>Die Benutzeroberfläche des Fensters definieren  
  
1.  In **Projektmappen-Explorer**, doppelklicken Sie auf "MainWindow.xaml".  
  
     Das Fenster wird automatisch im WPF-Designer geöffnet.  
  
2.  Fügen Sie in der [!INCLUDE[TLA#tla_titlexaml](../includes/tlasharptla-titlexaml-md.md)]-Ansicht des Designers den folgenden Code zwischen den `<Grid>`-Tags hinzu:  
  
    ```  
    <Grid.RowDefinitions>  
        <RowDefinition Height="75" />  
        <RowDefinition Height="625" />  
    </Grid.RowDefinitions>  
    <Button HorizontalAlignment="Left" Margin="22,20,0,24" Name="backButton" Width="75"><</Button>  
    <Button HorizontalAlignment="Left" Margin="116,20,0,24" Name="nextButton" Width="75">></Button>  
    <Button HorizontalAlignment="Right" Margin="0,21,46,24" Name="saveButton" Width="110">Save changes</Button>  
    ```  
  
3.  Erstellen Sie das Projekt.  
  
## <a name="createdata-bound-controls"></a>Createdata datengebundenen Steuerelementen  
 Steuerelemente erstellen, die Kundendatensätze, indem Sie ziehen anzeigen die `Product` -Tabelle aus dem **Datenquellen** in den WPF-Designer.  
  
#### <a name="to-create-data-bound-controls"></a>So erstellen Sie datengebundene Steuerelemente  
  
1.  In der **Datenquellen** Fenster, klicken Sie auf das Dropdownmenü für die **Produkt** Knoten, und wählen **Details**.  
  
2.  Erweitern Sie die **Produkt** Knoten.  
  
3.  In diesem Beispiel einige Felder werden nicht angezeigt, daher klicken Sie auf das Dropdownmenü neben den folgenden Knoten und anschließend auf **keine**:  
  
    -   ProductCategoryID  
  
    -   ProductModelID  
  
    -   ThumbnailPhotoFileName  
  
    -   rowguid  
  
    -   ModifiedDate  
  
4.  Klicken Sie auf das Dropdownmenü neben der **ThumbNailPhoto** Knoten, und wählen **Image**.  
  
    > [!NOTE]
    >  Standardmäßig haben Elemente der **Datenquellen** Fenster, das Darstellen von Bildern haben Steuerelementsatz zum **keine**. Dies ist deshalb so, weil Bilder als Bytearrays in Datenbanken gespeichert werden und alles enthalten können, von einer einfachen Array an Bytes bis zur ausführbaren Datei einer großen Anwendung.  
  
5.  Von der **Datenquellen** ziehen Sie die **Produkt** Knoten auf das Raster unter der Zeile, die die Schaltflächen enthält.  
  
     Visual Studio generiert XAML, die einen Satz von Steuerelementen definiert, die an Daten gebunden sind, die **Produkte** Tabelle. Es generiert außerdem Code, der die Daten lädt. Weitere Informationen zu den generierten XAML und Code finden Sie unter [Binden von WPF-Steuerelementen an Daten in Visual Studio](../data-tools/bind-wpf-controls-to-data-in-visual-studio1.md).  
  
6.  Im Designer, klicken Sie auf das Textfeld neben der **Produkt-ID** Bezeichnung.  
  
7.  In der **Eigenschaften** wählen Sie im Fenster das Kontrollkästchen neben den **IsReadOnly** Eigenschaft.  
  
## <a name="navigating-product-records"></a>Navigieren durch Product records  
 Hinzufügen von Code, der Benutzern ermöglicht, durch die Produktdatensätze Scrollen Sie mithilfe der **\<** und **>** Schaltflächen.  
  
#### <a name="to-enable-users-to-navigate-product-records"></a>Benutzern das Navigieren durch Product Records ermöglichen  
  
1.  Doppelklicken Sie im Designer auf die **<** Schaltfläche auf der Fensteroberfläche.  
  
     Visual Studio öffnet die CodeBehind-Datei und erstellt ein neues `backButton_Click` -Ereignishandler für die <xref:System.Windows.Controls.Primitives.ButtonBase.Click> Ereignis.  
  
2.  Ändern der `Window_Loaded` -Ereignishandler daher `ProductViewSource`, `AdventureWorksLTDataSet`, und `AdventureWorksLTDataSetProductTableAdapter` außerhalb der Methode und für das gesamte Formular zugänglich sind. Deklarieren Sie nur diese global für das Formular sein, und weisen sie in der `Window_Loaded` Ereignishandler, die etwa wie folgt:  
  
     [!code-csharp[Data_WPFDATASET#1](../snippets/csharp/VS_Snippets_ProTools/data_wpfdataset/cs/mainwindow.xaml.cs#1)]
     [!code-vb[Data_WPFDATASET#1](../snippets/visualbasic/VS_Snippets_ProTools/data_wpfdataset/vb/mainwindow.xaml.vb#1)]  
  
3.  Fügen Sie dem `backButton_Click` -Ereignishandler folgenden Code hinzu:  
  
     [!code-csharp[Data_WPFDATASET#2](../snippets/csharp/VS_Snippets_ProTools/data_wpfdataset/cs/mainwindow.xaml.cs#2)]
     [!code-vb[Data_WPFDATASET#2](../snippets/visualbasic/VS_Snippets_ProTools/data_wpfdataset/vb/mainwindow.xaml.vb#2)]  
  
4.  Zurück zu den Designer und doppelklicken Sie auf die **>** Schaltfläche.  
  
5.  Fügen Sie dem `nextButton_Click` -Ereignishandler folgenden Code hinzu:  
  
     [!code-csharp[Data_WPFDATASET#3](../snippets/csharp/VS_Snippets_ProTools/data_wpfdataset/cs/mainwindow.xaml.cs#3)]
     [!code-vb[Data_WPFDATASET#3](../snippets/visualbasic/VS_Snippets_ProTools/data_wpfdataset/vb/mainwindow.xaml.vb#3)]  
  
## <a name="savechanges-to-product-records"></a>"SaveChanges" an Product records  
 Hinzufügen von Code, der Benutzern ermöglicht, das Speichern von Änderungen an Product Records mithilfe der **speichern Änderungen** Schaltfläche.  
  
#### <a name="to-add-the-ability-to-save-changes-to-product-records"></a>Die Möglichkeit zum Speichern von Änderungen zu Product Records hinzufügen  
  
1.  Doppelklicken Sie im Designer auf die **speichern Änderungen** Schaltfläche.  
  
     Visual Studio öffnet die CodeBehind-Datei und erstellt ein neues `saveButton_Click` -Ereignishandler für die <xref:System.Windows.Controls.Primitives.ButtonBase.Click> Ereignis.  
  
2.  Fügen Sie dem `saveButton_Click` -Ereignishandler folgenden Code hinzu:  
  
     [!code-csharp[Data_WPFDATASET#4](../snippets/csharp/VS_Snippets_ProTools/data_wpfdataset/cs/mainwindow.xaml.cs#4)]
     [!code-vb[Data_WPFDATASET#4](../snippets/visualbasic/VS_Snippets_ProTools/data_wpfdataset/vb/mainwindow.xaml.vb#4)]  
  
    > [!NOTE]
    >  In diesem Beispiel wird die Methode `Save` des `TableAdapter` für das Speichern von Änderungen verwendet. Das ist in dieser exemplarischen Vorgehensweise angebracht, denn es wird nur eine Datentabelle geändert. Wenn Sie Änderungen an mehreren Datentabellen speichern möchten, können Sie alternativ die Methode `UpdateAll` des `TableAdapterManager` einsetzen, die Visual Studio mit dem Dataset generiert. Weitere Informationen finden Sie unter [Übersicht über TableAdapterManager](http://msdn.microsoft.com/library/33076d42-6b41-491a-ac11-6c6339aea650).  
  
## <a name="test-the-application"></a>Testen der Anwendung  
 Erstellen Sie die Anwendung, und führen Sie sie aus. Stellen Sie sicher, dass Sie Produktdatensätze anzeigen und ändern können.  
  
#### <a name="to-test-the-application"></a>So testen Sie die Anwendung  
  
1.  Drücken Sie **F5**.  
  
     Die Anwendung wird erstellt und ausgeführt. Überprüfen Sie Folgendes:  
  
    -   Die Textfelder zeigen Daten aus dem ersten Produktdatensatz, der ein Foto hat. Dieses Produkt hat die Produkt-ID 713 und den Namen **Long-Sleeve Logo Jersey, S**.  
  
    -   Klicken Sie auf die **>** oder **<** Schaltflächen zum Navigieren durch andere Produktdatensätze.  
  
2.  Ändern Sie in einem der Datensätze, die **Größe** Wert ein, und klicken Sie dann auf **speichern Änderungen**.  
  
3.  Schließen Sie die Anwendung, und wiederholen Sie die Anwendung durch Drücken von **F5** in Visual Studio.  
  
4.  Navigieren Sie zum Produktdatensatz, den Sie geändert haben und prüfen Sie, ob die Änderung gespeichert wurde.  
  
5.  Schließen Sie die Anwendung.  
  
## <a name="next-steps"></a>Nächste Schritte  
 Nach Abschluss dieser exemplarischen Vorgehensweise können Sie folgende Aufgaben ausführen:  
  
-   Erfahren Sie, wie Sie mit der **Datenquellen** Fenster in Visual Studio zum Binden von WPF-Steuerelementen an andere Typen von Datenquellen. Weitere Informationen finden Sie unter [Binden von WPF-Steuerelemente an einen WCF-Datendienst](../data-tools/bind-wpf-controls-to-a-wcf-data-service.md).  
  
-   Erfahren Sie, wie Sie mit der **Datenquellen** Fenster in Visual Studio zum Anzeigen von verwandter Daten (d. h. Daten in einer über-/ unterordnungsbeziehung) in WPF-Steuerelementen. Weitere Informationen finden Sie unter [Exemplarische Vorgehensweise: Anzeigen von verknüpften Daten in einer WPF-Anwendung](../data-tools/walkthrough-displaying-related-data-in-a-wpf-application.md).  
  
## <a name="see-also"></a>Siehe auch  
 [Binden von WPF-Steuerelementen an Daten in Visual Studio](../data-tools/bind-wpf-controls-to-data-in-visual-studio1.md)   
 [Binden von WPF-Steuerelementen an Daten in Visual Studio](../data-tools/bind-wpf-controls-to-data-in-visual-studio2.md)   
 [Datasettools in Visual Studio](../data-tools/dataset-tools-in-visual-studio.md)   
 [WPF und Silverlight-Designer (Übersicht)](http://msdn.microsoft.com/en-us/570b7a5c-0c86-4326-a371-c9b63378fc62)   
 [Übersicht zur Datenbindung](http://msdn.microsoft.com/library/c707c95f-7811-401d-956e-2fffd019a211)

