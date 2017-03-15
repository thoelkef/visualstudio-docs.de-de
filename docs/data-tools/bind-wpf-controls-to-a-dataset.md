---
title: "Exemplarische Vorgehensweise: Binden von WPF-Steuerelementen an ein Dataset | Microsoft Docs"
ms.custom: ""
ms.date: "12/15/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
dev_langs: 
  - "VB"
  - "CSharp"
  - "C++"
  - "aspx"
helpviewer_keywords: 
  - "WPF-Datenbindung [Visual Studio], Exemplarische Vorgehensweisen"
  - "WPF-Designer, Datenbindung"
  - "WPF, Datenbindung in Visual Studio"
ms.assetid: 177420b9-568b-4dad-9d16-1b0e98a24d71
caps.latest.revision: 32
caps.handback.revision: 30
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# Exemplarische Vorgehensweise: Binden von WPF-Steuerelementen an ein Dataset
In dieser exemplarischen Vorgehensweise erstellen Sie eine WPF\-Anwendung, die datengebundene Steuerelemente enthält.  Die Steuerelemente sind an Produktdatensätze gebunden, die in einem Dataset gekapselt sind.  Sie fügen außerdem Schaltflächen hinzu, mit denen es möglich ist, Produkte zu durchsuchen und Änderungen an Produktdatensätzen zu speichern.  
  
 In dieser exemplarischen Vorgehensweise werden die folgenden Aufgaben veranschaulicht:  
  
-   Erstellen einer WPF\-Anwendung und eines Datasets, das aus Daten in der Beispieldatenbank AdventureWorksLT generiert wird.  
  
-   Erstellen eines Satzes datengebundener Steuerelemente durch Ziehen einer Datentabelle aus dem **Datenquellenfenster** zum Fenster im WPF\-Designer.  
  
-   Erstellen von Schaltflächen, mit denen die Navigation vorwärts und rückwärts durch die Produktdatensätze möglich ist.  
  
-   Erstellen einer Schaltfläche, die Änderungen durch Kunden an den Produktdatensätzen in der Tabelle und der darunterliegenden Datenquelle speichert.  
  
     [!INCLUDE[note_settings_general](../data-tools/includes/note_settings_general_md.md)]  
  
## Vorbereitungsmaßnahmen  
 Zum Durchführen dieser exemplarischen Vorgehensweise benötigen Sie die folgenden Komponenten:  
  
-   [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)]  
  
-   Zugriff auf eine laufende Instanz von SQL Server oder SQL Server Express, an die eine AdventureWorksLT\-Beispieldatenbank angefügt ist.  Sie können die AdventureWorksLT\-Datenbankvon der [CodePlex\-Website](http://go.microsoft.com/fwlink/?linkid=87843) herunterladen.  
  
 Vorkenntnisse der folgenden Konzepte sind ebenfalls hilfreich, wenn auch für die Durchführung der exemplarischen Vorgehensweise nicht erforderlich:  
  
-   DataSets und TableAdapters.  Weitere Informationen finden Sie unter [Arbeiten mit Datasets in Visual Studio](../data-tools/dataset-tools-in-visual-studio.md) und [Übersicht über TableAdapters](../data-tools/tableadapter-overview.md).  
  
-   Arbeiten mit dem WPF\-Designer.  Weitere Informationen finden Sie unter [Übersicht über den WPF\- und Silverlight\-Designer](http://msdn.microsoft.com/de-de/570b7a5c-0c86-4326-a371-c9b63378fc62).  
  
-   WPF\-Datenbindung.  Weitere Informationen finden Sie unter [Übersicht über Datenbindung](../Topic/Data%20Binding%20Overview.md).  
  
## Erstellen des Projekts  
 Erstellen eines neuen WPF\-Projekts.  Das Projekt zeigt Produktdatensätze.  
  
#### So erstellen Sie das Projekt  
  
1.  Starten Sie Visual Studio.  
  
2.  Zeigen Sie im Menü **Datei** auf **Neu**, und klicken Sie dann auf **Projekt**.  
  
3.  Erweitern Sie **Visual Basic** oder **Visual C\#** und wählen Sie dann **Windows**.  
  
4.  Wählen Sie die Projektvorlage **WPF\-Anwendung**.  
  
5.  Geben Sie im Feld **Name** den Namen `AdventureWorksProductsEditor` ein und klicken Sie **OK**.  
  
     Visual Studio erstellt das Projekt `AdventureWorksProductsEditor`.  
  
## Erstellt ein Dataset für die Anwendung  
 Ehe Sie datengebundene Steuerelemente erstellen können, müssen Sie ein Datenmodell für die Anwendung definieren und es dem **Datenquellenfenster** hinzufügen.  In dieser exemplarischen Vorgehensweise erstellen Sie ein Dataset als Datenmodell.  
  
#### So erstellen Sie ein DataSet  
  
1.  Klicken Sie im Menü **Daten** auf **Datenquellen anzeigen**.  
  
     Das **Datenquellenfenster** wird geöffnet.  
  
2.  Klicken Sie im **Datenquellenfenster** auf **Neue Datenquelle hinzufügen**.  
  
     Der **Assistent zum Konfigurieren von Datenquellen** wird geöffnet.  
  
3.  Wählen Sie auf der Seite **Datenquellentyp auswählen** die Option **Datenbank** aus, und klicken Sie dann auf **Weiter**.  
  
4.  Wählen Sie auf der Seite **Wählen Sie ein Datenbankmodell aus** die Option **DataSet** aus, und klicken Sie dann auf **Weiter**.  
  
5.  Wählen Sie auf der Seite **Wählen Sie Ihre Datenverbindung aus** eine der folgenden Optionen aus:  
  
    -   Wenn in der Dropdownliste eine Datenverbindung zur Beispieldatenbank "AdventureWorksLT" verfügbar ist, wählen Sie diese aus und klicken Sie anschließend **Weiter**.  
  
         \- oder \-  
  
    -   Klicken Sie **Neue Verbindung** und erstellen Sie eine Verbindung zur Datenbank AdventureWorksLT.  
  
6.  Wählen Sie auf der Seite **Verbindungszeichenfolge in der Anwendungskonfigurationsdatei speichern** das Kontrollkästchen **Ja, Verbindung speichern unter** und klicken Sie anschließend auf **Weiter**.  
  
7.  Erweitern Sie auf der Seite **Datenbankobjekte auswählen** den Punkt **Tabellen** und wählen Sie dann die Tabelle **Product \(SalesLT\)** aus.  
  
8.  Klicken Sie auf **Fertig stellen**.  
  
     Visual Studio fügt eine neue Datei AdventureWorksLTDataSet.xsd zum Projekt hinzu und fügt ein entsprechendes **AdventureWorksLTDataSet**\-Objekt dem Fenster **Datenquellen** hinzu.  Die Datei AdventureWorksLTDataSet.xsd definiert ein typisiertes Dataset namens `AdventureWorksLTDataSet` und einen TableAdapter namens `ProductTableAdapter`.  Weiter unten in dieser exemplarischen Vorgehensweise verwenden Sie `ProductTableAdapter` für das Füllen des Datasets mit Daten und speichern die Änderungen zurück in die Datenbank.  
  
9. Erstellen Sie das Projekt.  
  
## Bearbeiten der Standard\-Fill\-Methode auf dem TableAdapter  
 Verwenden Sie zum Füllen des Datasets die `Fill`\-Methode des `ProductTableAdapter`.  Standardmäßig füllt die `Fill`\-Methode die `ProductDataTable` im `AdventureWorksLTDataSet` mit allen Datenzeilen aus der Product\-Tabelle.  Sie können diese Methode modifizieren, sodass nur eine Teilmenge von Zeilen zurückgeben wird.  Ändern Sie für diese exemplarische Vorgehensweise die `Fill`\-Methode, sodass nur Zeilen für Produkte zurückgegeben werden, die Fotos haben.  
  
#### So laden Sie Produktzeilen, die Fotos haben  
  
1.  Öffnen Sie im **Projektmappen\-Explorer** die Datei "AdventureWorksLTDataSet.xsd".  
  
     Der DataSet\-Designer wird geöffnet.  
  
2.  Klicken Sie die Abfrage **Fill,GetData\(\)** mit der rechten Maustaste und wählen Sie **Konfigurieren**.  
  
     Der **TableAdapter\-Konfigurations\-Assistent** wird geöffnet.  
  
3.  Fügen Sie auf der Seite **SQL\-Anweisung eingeben** die folgende WHERE\-Klausel nach der `SELECT`\-Anweisung im Textfeld ein.  
  
    ```  
    WHERE ThumbnailPhotoFileName <> 'no_image_available_small.gif'  
    ```  
  
4.  Klicken Sie auf **Fertig stellen**.  
  
## Definieren der Benutzeroberfläche  
 Fügen Sie dem Fenster eine Reihe von Schaltflächen hinzu, indem Sie XAML im WPF\-Designer ändern.  Später in dieser exemplarischen Vorgehensweise fügen Sie dann Code hinzu, mit dem Anwender durch Produktdatensätze blättern und Änderungen daran mithilfe dieser Schaltflächen speichern können.  
  
#### Die Benutzeroberfläche des Fensters definieren  
  
1.  Doppelklicken Sie in**Projektmappen\-Explorer** MainWindow.xaml.  
  
     Das Fenster wird automatisch im WPF\-Designer geöffnet.  
  
2.  Fügen Sie in der [!INCLUDE[TLA#tla_titlexaml](../data-tools/includes/tlasharptla_titlexaml_md.md)]\-Ansicht des Designers den folgenden Code zwischen den `<Grid>`\-Tags hinzu:  
  
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
  
## Erstellen datengebundener Steuerelemente  
 Erstellen Sie Steuerelemente zum Anzeigen der Kundedatensätze, indem Sie die Tabelle `Product` vom **Datenquellenfenster** auf den WPF\-Designer ziehen.  
  
#### So erstellen Sie datengebundene Steuerelemente  
  
1.  Klicken Sie im **Datenquellenfenster** das Dropdownmenü für den Knoten **Product** und wählen Sie **Details**.  
  
2.  Erweitern Sie den **Product**\-Knoten.  
  
3.  In diesem Beispiel werden einige Felder nicht angezeigt. Klicken Sie also das Dropdownmenü neben den folgenden Knoten und wählen Sie **Keine**:  
  
    -   ProductCategoryID  
  
    -   ProductModelID  
  
    -   ThumbnailPhotoFileName  
  
    -   rowguid  
  
    -   ModifiedDate  
  
4.  Klicken Sie auf das Dropdownmenü neben dem Knoten\-**ThumbNailPhoto** und wählen Sie **Bild**.  
  
    > [!NOTE]
    >  Standardmäßig haben Elemente im **Datenquellenfenster**, die Bilder repräsentieren, als Steuerelementsatz **Kein** ausgewählt.  Dies ist deshalb so, weil Bilder als Bytearrays in Datenbanken gespeichert werden und alles enthalten können, von einer einfachen Array an Bytes bis zur ausführbaren Datei einer großen Anwendung.  
  
5.  Ziehen Sie aus dem **Datenquellenfenster** den Knoten **Product** auf das Raster unter der Zeile, in der die Schaltflächen sind.  
  
     Visual Studio erzeugt XAML, der einen Satz von Steuerelementen definiert, der an Daten in der Tabelle **Products** gebunden ist.  Es generiert außerdem Code, der die Daten lädt.  Weitere Informationen über das generierte XAML und den Code finden Sie unter [Binden von WPF\-Steuerelementen an Daten in Visual Studio](../data-tools/bind-wpf-controls-to-data-in-visual-studio1.md).  
  
6.  Klicken Sie im Designer auf das Textfeld neben der Bezeichnung **Product ID**.  
  
7.  Wählen Sie im Fenster **Eigenschaften** das Kontrollkästchen neben der Eigenschaft **IsReadOnly**.  
  
## Navigieren durch Product Records  
 Fügen Sie Code hinzu, mit dessen Hilfe Benutzer durch die Produktdatensätze scrollen können, indem Sie die Schaltflächen **\<** und **\>** verwenden.  
  
#### Benutzern das Navigieren durch Product Records ermöglichen  
  
1.  Doppelklicken Sie im Designer die Schaltfläche **\<** auf der Fensteroberfläche.  
  
     Visual Studio öffnet die CodeBehind\-Datei und erstellt einen neuen `backButton_Click`\-Ereignishandler für das <xref:System.Windows.Controls.Primitives.ButtonBase.Click>\-Ereignis.  
  
2.  Ändern Sie den `Window_Loaded`\-Ereignishandler, sodass `ProductViewSource`, `AdventureWorksLTDataSet` und `AdventureWorksLTDataSetProductTableAdapter` sich außerhalb der Methode befinden und für das gesamte Formular zugänglich sind.  Erklären Sie nur diese als global für das Formular und weisen Sie diese im `Window_Loaded`\-Ereignishandler wie folgt zu:  
  
     [!code-cs[Data_WPFDATASET#1](../data-tools/codesnippet/CSharp/bind-wpf-controls-to-a-dataset_1.cs)]
     [!code-vb[Data_WPFDATASET#1](../data-tools/codesnippet/VisualBasic/bind-wpf-controls-to-a-dataset_1.vb)]  
  
3.  Fügen Sie dem `backButton_Click`\-Ereignishandler folgenden Code hinzu:  
  
     [!code-cs[Data_WPFDATASET#2](../data-tools/codesnippet/CSharp/bind-wpf-controls-to-a-dataset_2.cs)]
     [!code-vb[Data_WPFDATASET#2](../data-tools/codesnippet/VisualBasic/bind-wpf-controls-to-a-dataset_2.vb)]  
  
4.  Kehren Sie zum Designer zurück und doppelklicken Sie die Schaltfläche **\>**.  
  
5.  Fügen Sie dem `nextButton_Click`\-Ereignishandler folgenden Code hinzu:  
  
     [!code-cs[Data_WPFDATASET#3](../data-tools/codesnippet/CSharp/bind-wpf-controls-to-a-dataset_3.cs)]
     [!code-vb[Data_WPFDATASET#3](../data-tools/codesnippet/VisualBasic/bind-wpf-controls-to-a-dataset_3.vb)]  
  
## Änderungen an Product Records speichern  
 Fügen Sie Code hinzu, mit dem Benutzer Änderungen an Product Records mithilfe der Taste **Änderungen speichern** speichern können.  
  
#### Die Möglichkeit zum Speichern von Änderungen zu Product Records hinzufügen  
  
1.  Doppelklicken Sie im Designer auf die Schaltfläche **Änderungen speichern**.  
  
     Visual Studio öffnet die CodeBehind\-Datei und erstellt einen neuen `saveButton_Click`\-Ereignishandler für das <xref:System.Windows.Controls.Primitives.ButtonBase.Click>\-Ereignis.  
  
2.  Fügen Sie dem `saveButton_Click`\-Ereignishandler folgenden Code hinzu:  
  
     [!code-cs[Data_WPFDATASET#4](../data-tools/codesnippet/CSharp/bind-wpf-controls-to-a-dataset_4.cs)]
     [!code-vb[Data_WPFDATASET#4](../data-tools/codesnippet/VisualBasic/bind-wpf-controls-to-a-dataset_4.vb)]  
  
    > [!NOTE]
    >  In diesem Beispiel wird die Methode `Save` des `TableAdapter` für das Speichern von Änderungen verwendet.  Das ist in dieser exemplarischen Vorgehensweise angebracht, denn es wird nur eine Datentabelle geändert.  Wenn Sie Änderungen an mehreren Datentabellen speichern möchten, können Sie alternativ die Methode `UpdateAll` des `TableAdapterManager` einsetzen, die Visual Studio mit dem Dataset generiert.  Weitere Informationen finden Sie unter [Übersicht über TableAdapterManager](../Topic/TableAdapterManager%20Overview.md).  
  
## Testen der Anwendung  
 Erstellen Sie die Anwendung, und führen Sie sie aus.  Stellen Sie sicher, dass Sie Produktdatensätze anzeigen und ändern können.  
  
#### So testen Sie die Anwendung  
  
1.  Drücken Sie **F5**.  
  
     Die Anwendung wird erstellt und ausgeführt.  Überprüfen Sie Folgendes:  
  
    -   Die Textfelder zeigen Daten aus dem ersten Produktdatensatz, der ein Foto hat.  Dieses Produkt hat die ID 713 und heißt **Long\-Sleeve Logo Jersey, S**.  
  
    -   Sie können die Schaltflächen **\>** oder **\<** für die Navigation durch andere Produktdatensätze klicken.  
  
2.  Ändern Sie in einem der Datensätze im Feld **Größe** den Wert und klicken Sie anschließend **Änderungen speichern**.  
  
3.  Schließen Sie die Anwendung und starten Sie sie dann die Anwendung in Visual Studio erneut, indem Sie **F5** drücken.  
  
4.  Navigieren Sie zum Produktdatensatz, den Sie geändert haben und prüfen Sie, ob die Änderung gespeichert wurde.  
  
5.  Schließen Sie die Anwendung.  
  
## Nächste Schritte  
 Nach Abschluss dieser exemplarischen Vorgehensweise können Sie folgende Aufgaben ausführen:  
  
-   Erfahren Sie, wie Sie das **Datenquellenfenster** in Visual Studio für die Bindung von WPF\-Steuerelementen an andere Typen von Datenquellen verwenden.  Weitere Informationen finden Sie unter [Exemplarische Vorgehensweise: Binden von WPF\-Steuerelementen an einen WCF\-Datendienst](../data-tools/bind-wpf-controls-to-a-wcf-data-service.md).  
  
-   Erfahren Sie, wie Sie das **Datenquellenfenster** in Visual Studio für die Anzeige zugehöriger Daten \(das heißt, Daten in einer Beziehung zwischen übergeordneten und untergeordneten Daten\) in WPF\-Steuerelementen verwenden.  Weitere Informationen finden Sie unter [Exemplarische Vorgehensweise: Anzeigen verknüpfter Daten in einer WPF\-Anwendung](../data-tools/walkthrough-displaying-related-data-in-a-wpf-application.md).  
  
## Siehe auch  
 [Binden von WPF\-Steuerelementen an Daten in Visual Studio](../data-tools/bind-wpf-controls-to-data-in-visual-studio1.md)   
 [Gewusst wie: Binden von WPF\-Steuerelementen an Daten in Visual Studio](../data-tools/bind-wpf-controls-to-data-in-visual-studio2.md)   
 [Arbeiten mit Datasets in Visual Studio](../data-tools/dataset-tools-in-visual-studio.md)   
 [Übersicht über den WPF\- und Silverlight\-Designer](http://msdn.microsoft.com/de-de/570b7a5c-0c86-4326-a371-c9b63378fc62)   
 [Übersicht über Datenbindung](../Topic/Data%20Binding%20Overview.md)