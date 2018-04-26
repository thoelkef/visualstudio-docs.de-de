---
title: Binden von WPF-Steuerelementen an einen WCF-Datendienst
ms.date: 11/04/2016
ms.topic: conceptual
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- WPF, data binding in Visual Studio
- WPF data binding [Visual Studio], walkthroughs
- WPF Designer, data binding
ms.assetid: 8823537c-82f0-41f7-bf30-705f0e5e59fd
author: gewarren
ms.author: gewarren
manager: douge
ms.prod: visual-studio-dev15
ms.technology: vs-data-tools
ms.workload:
- data-storage
ms.openlocfilehash: 8152a02df8f335a92024134dde89b45d2f3e115a
ms.sourcegitcommit: e13e61ddea6032a8282abe16131d9e136a927984
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/26/2018
---
# <a name="bind-wpf-controls-to-a-wcf-data-service"></a>Binden von WPF-Steuerelementen an einen WCF-Datendienst

In dieser exemplarischen Vorgehensweise erstellen Sie eine WPF-Anwendung, die datengebundene Steuerelemente enthält. Die Steuerelemente sind an Kundendatensätze gebunden, die in einem [!INCLUDE[ss_data_service](../data-tools/includes/ss_data_service_md.md)] gekapselt sind. Sie fügen außerdem die Schaltflächen hinzu, mit denen Kunden Datensätze anzeigen und ändern können.

In dieser exemplarischen Vorgehensweise werden die folgenden Aufgaben veranschaulicht:

- Erstellen eines Entity Data Models, das aus Daten in der Beispieldatenbank AdventureWorksLT generiert wird.

- Erstellen einer [!INCLUDE[ss_data_service](../data-tools/includes/ss_data_service_md.md)] , der die Daten in das Entity Data Model für eine WPF-Anwendung verfügbar macht.

- Erstellen eines Satzes von datengebundene Steuerelemente durch Ziehen von Elementen aus der **Datenquellen** in den WPF-Designer.

- Erstellen von Schaltflächen, mit denen die Navigation vorwärts und rückwärts durch die Kundendatensätze möglich ist.

- Erstellen eine Schaltfläche, die Änderungen an Daten in den Steuerelementen speichert die [!INCLUDE[ss_data_service](../data-tools/includes/ss_data_service_md.md)] und der zugrunde liegenden Datenquelle.

[!INCLUDE[note_settings_general](../data-tools/includes/note_settings_general_md.md)]

## <a name="prerequisites"></a>Erforderliche Komponenten
Zum Durchführen dieser exemplarischen Vorgehensweise benötigen Sie die folgenden Komponenten:

-   [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)]

-   Zugriff auf eine laufende Instanz von SQL Server oder SQL Server Express, an die eine AdventureWorksLT-Beispieldatenbank angefügt ist. Sie können die AdventureWorksLT-datenbankvon der [CodePlex-Website](http://go.microsoft.com/fwlink/?linkid=87843).

Vorkenntnisse der folgenden Konzepte sind ebenfalls hilfreich, wenn auch für die Durchführung der exemplarischen Vorgehensweise nicht erforderlich:

-   WCF Data Services. Weitere Informationen finden Sie unter [Übersicht](/dotnet/framework/data/wcf/wcf-data-services-overview).

-   Datenmodelle in [!INCLUDE[ssAstoria](../data-tools/includes/ssastoria_md.md)].

-   Entity Data Models und der ADO.NET Entity Framework. Weitere Informationen finden Sie unter [Übersicht über Entity Framework](/dotnet/framework/data/adonet/ef/overview).

-   WPF-Datenbindung. Weitere Informationen finden Sie unter [Übersicht über Datenbindung](/dotnet/framework/wpf/data/data-binding-overview).

## <a name="create-the-service-project"></a>Erstellen des Dienstprojekts
Beginnen Sie diese exemplarische Vorgehensweise, indem Sie ein Projekt für einen [!INCLUDE[ss_data_service](../data-tools/includes/ss_data_service_md.md)] erstellen.

### <a name="to-create-the-service-project"></a>So erstellen Sie das Dienstprojekt

1.  Starten Sie Visual Studio.

2.  Zeigen Sie im Menü **Datei** auf **Neu**, und klicken Sie dann auf **Projekt**.

3.  Erweitern Sie **Visual C#-** oder **Visual Basic**, und wählen Sie dann **Web**.

4.  Wählen Sie die Projektvorlage **ASP.NET-Webanwendung** aus.

5.  In der **Namen** geben `AdventureWorksService` , und klicken Sie auf **OK**.

     Visual Studio erstellt das `AdventureWorksService` Projekt.

6.  In **Projektmappen-Explorer**, mit der rechten Maustaste **"default.aspx"** , und wählen Sie **löschen**. Diese Datei wird für diese exemplarische Vorgehensweise benötigt.

## <a name="create-an-entity-data-model-for-the-service"></a>Erstellen Sie ein Entity Data Model für den Dienst
Damit die Daten mithilfe eines [!INCLUDE[ss_data_service](../data-tools/includes/ss_data_service_md.md)] für eine Anwendung verfügbar gemacht werden, müssen Sie ein Datenmodell für den Dienst definieren. Die [!INCLUDE[ss_data_service](../data-tools/includes/ss_data_service_md.md)] unterstützt zwei Typen von Datenmodellen: Entity Data Models und benutzerdefinierte Datenmodelle, die definiert werden, mit der common Language Runtime (CLR) Objekte, implementieren die <xref:System.Linq.IQueryable%601> Schnittstelle. In dieser exemplarischen Vorgehensweise erstellen Sie ein Entity Data Model für das Datenmodell.

### <a name="to-create-an-entity-data-model"></a>So erstellen Sie ein Entity Data Model

1.  Klicken Sie im Menü **Projekt** auf **Neues Element hinzufügen**.

2.  Klicken Sie in der Liste der installierten Vorlagen auf **Daten**, und wählen Sie dann die **ADO.NET Entity Data Model** Projektelement.

3.  Ändern Sie den Namen in `AdventureWorksModel.edmx`, und klicken Sie auf **hinzufügen**.

     Die **Entity Data Model** -Assistent wird geöffnet.

4.  Auf der **Modellinhalte** auf **aus Datenbank generieren**, und klicken Sie auf **Weiter**.

5.  Auf der **wählen Sie Ihre Datenverbindung** Seite, wählen Sie eine der folgenden Optionen:

    -   Wenn in der Dropdownliste eine Datenverbindung zur Beispieldatenbank „AdventureWorksLT“ verfügbar ist, wählen Sie diese aus.

    -   Klicken Sie auf **neue Verbindung**, und erstellen Sie eine Verbindung zur Datenbank AdventureWorksLT.

6.  Auf der **wählen Sie Ihre Datenverbindung** Seite, stellen Sie sicher, dass die **Entität Speichern der Verbindungseinstellungen in app.config-Datei als** Option ausgewählt ist, und klicken Sie dann auf **Weiter**.

7.  Auf der **Datenbankobjekte auswählen** Seite **Tabellen**, und wählen Sie dann die **SalesOrderHeader** Tabelle.

8.  Klicken Sie auf **Fertig stellen**.

## <a name="create-the-service"></a>Erstellen Sie den Dienst
Erstellen einer [!INCLUDE[ss_data_service](../data-tools/includes/ss_data_service_md.md)] zur Verfügbarmachung der Daten in das Entity Data Model für eine WPF-Anwendung.

### <a name="to-create-the-service"></a>So erstellen Sie den Dienst

1.  Auf der **Projekt** klicken Sie im Menü **neues Element hinzufügen**.

2.  Klicken Sie in der Liste der installierten Vorlagen auf **Web**, und wählen Sie dann die **WCF Data Service** Projektelement.

3.  In der **Namen** geben `AdventureWorksService.svc`, und klicken Sie auf **hinzufügen**.

     Visual Studio fügt die `AdventureWorksService.svc` zum Projekt.

## <a name="configure-the-service"></a>Konfigurieren Sie den Dienst.
Damit der Dienst mit dem von Ihnen erstellten Entity Data Model funktioniert, muss er konfiguriert werden.

### <a name="to-configure-the-service"></a>So konfigurieren Sie den Dienst

1.  In der `AdventureWorks.svc` Codedatei, ersetzen Sie die `AdventureWorksService` -Klassendeklaration durch den folgenden Code.

     [!code-csharp[Data_WPFWCF#1](../data-tools/codesnippet/CSharp/bind-wpf-controls-to-a-wcf-data-service_1.cs)]
     [!code-vb[Data_WPFWCF#1](../data-tools/codesnippet/VisualBasic/bind-wpf-controls-to-a-wcf-data-service_1.vb)]

     Dieser Code aktualisiert den `AdventureWorksService` Klasse, sodass sie von abgeleitet ist ein <xref:System.Data.Services.DataService%601> den Zugriff auf die `AdventureWorksLTEntities` Context-Klasse in Ihr Entity Data Model-Objekt. Außerdem aktualisiert er die Methode `InitializeService`, sodass Clients des Diensts vollen Lese-/Schreibzugriff auf die `SalesOrderHeader`-Entität haben.

2.  Erstellen Sie das Projekt und überprüfen Sie, ob es fehlerfrei erstellt wird.

## <a name="create-the-wpf-client-application"></a>Erstellen der WPF-Clientanwendung
Um Daten aus dem [!INCLUDE[ss_data_service](../data-tools/includes/ss_data_service_md.md)] anzuzeigen, erstellen Sie eine neue WPF-Anwendung mit einer Datenquelle, die auf dem Dienst basiert. Später in dieser exemplarischen Vorgehensweise werden Sie datengebundene Steuerelemente zur Anwendung hinzufügen.

### <a name="to-create-the-wpf-client-application"></a>So erstellen Sie die WPF-Clientanwendung

1.  In **Projektmappen-Explorer**mit der rechten Maustaste auf den Projektmappenknoten, klicken Sie auf **hinzufügen**, und wählen Sie **neues Projekt**.

2.  In der **neues Projekt** Dialogfeld erweitern Sie **Visual C#-** oder **Visual Basic**, und wählen Sie dann **Windows**.

3.  Wählen Sie die **WPF-Anwendung** -Projektvorlage.

4.  In der **Namen** geben `AdventureWorksSalesEditor`, und klicken Sie auf **OK**.

     Visual Studio fügt die `AdventureWorksSalesEditor` Projekt der Projektmappe.

5.  Klicken Sie im Menü **Daten** auf **Datenquellen anzeigen**.

     Die **Datenquellen** Fenster wird geöffnet.

6.  Klicken Sie im **Datenquellenfenster** auf **Neue Datenquelle hinzufügen**.

     Die **Datenquellenkonfiguration** -Assistent wird geöffnet.

7.  In der **wählen Sie einen Datenquellentyp** Seite des Assistenten die Option **Service**, und klicken Sie dann auf **Weiter**.

8.  In der **Hinzufügen eines Dienstverweises** (Dialogfeld), klicken Sie auf **Discover**.

     Visual Studio durchsucht die aktuelle Lösung nach verfügbaren Diensten und fügt `AdventureWorksService.svc` zur Liste der verfügbaren Dienste in der **Services** Feld.

9. In der **Namespace** geben `AdventureWorksService`.

10. In der **Services** auf **AdventureWorksService.svc**, und klicken Sie dann auf **OK**.

     Visual Studio lädt die Dienstinformation herunter, und gibt anschließend an die **Datenquellenkonfiguration** Assistenten.

11. In der **Hinzufügen eines Dienstverweises** auf **Fertig stellen**.

     Visual Studio fügt Knoten, die vom Dienst für den zurückgegebenen Daten darstellen, die **Datenquellen** Fenster.

## <a name="define-the-user-interface-of-the-window"></a>Die Benutzeroberfläche des Fensters definieren
Fügen Sie dem Fenster eine Reihe von Schaltflächen hinzu, indem Sie XAML im WPF-Designer ändern. Später in dieser exemplarischen Vorgehensweise fügen Sie dann Code hinzu, mit dem Anwender die Verkaufsdatensätze mithilfe dieser Schaltflächen anzeigen und ändern können.

### <a name="to-create-the-window-layout"></a>So erstellen Sie das Fensterlayout

1.  In **Projektmappen-Explorer**, doppelklicken Sie auf **"MainWindow.xaml"**.

     Das Fenster wird automatisch im WPF-Designer geöffnet.

2.  Fügen Sie in der [!INCLUDE[TLA#tla_titlexaml](../data-tools/includes/tlasharptla_titlexaml_md.md)]-Ansicht des Designers den folgenden Code zwischen den `<Grid>`-Tags hinzu:

    ```xaml
    <Grid.RowDefinitions>
        <RowDefinition Height="75" />
        <RowDefinition Height="525" />
    </Grid.RowDefinitions>
    <Button HorizontalAlignment="Left" Margin="22,20,0,24" Name="backButton" Width="75"><</Button>
    <Button HorizontalAlignment="Left" Margin="116,20,0,24" Name="nextButton" Width="75">></Button>
    <Button HorizontalAlignment="Right" Margin="0,21,46,24" Name="saveButton" Width="110">Save changes</Button>
    ```

3.  Erstellen Sie das Projekt.

## <a name="create-the-data-bound-controls"></a>Erstellen Sie die datengebundenen Steuerelemente
Erstellen Sie Steuerelemente, die Kundendatensätze, indem Sie ziehen anzeigen die `SalesOrderHeaders` Knoten aus der **Datenquellen** in den Designer.

### <a name="to-create-the-data-bound-controls"></a>So erstellen Sie ein datengebundene Steuerelemente

1.  In der **Datenquellen** Fenster, klicken Sie auf das Dropdownmenü für die **SalesOrderHeaders** Knoten, und wählen **Details**.

2.  Erweitern Sie die **SalesOrderHeaders** Knoten.

3.  In diesem Beispiel einige Felder nicht angezeigt, so klicken Sie auf das Dropdownmenü neben den folgenden Knoten und wählen Sie **keine**:

    -   **Verschlüsselten CreditCardApprovalCode**

    -   **ModifiedDate**

    -   **OnlineOrderFlag**

    -   **RevisionNumber**

    -   **rowguid**

    Durch diese Aktion wird Visual Studio daran gehindert, im nächsten Schritt datengebundene Steuerelemente für diese Knoten zu erstellen. In dieser exemplarischen Vorgehensweise wird davon ausgegangen Sie, dass der Endbenutzer nicht, diese Daten anzuzeigen.

4.  Aus der **Datenquellen** Fenster, ziehen Sie die **SalesOrderHeaders** Knoten auf das Raster unter der Zeile, die die Schaltflächen enthält.

     Visual Studio generiert XAML und Code, der einen Satz von Steuerelementen, die an Daten gebunden sind, erstellt der **Produkt** Tabelle. Weitere Informationen über die generierten XAML und generierter Code finden Sie unter [Binden von WPF-Steuerelementen an Daten in Visual Studio](../data-tools/bind-wpf-controls-to-data-in-visual-studio.md).

5.  Im Designer, klicken Sie auf das Textfeld neben der **Kunden-ID** Bezeichnung.

6.  In der **Eigenschaften** Fenster, wählen Sie das Kontrollkästchen neben den **IsReadOnly** Eigenschaft.

7.  Legen Sie die **IsReadOnly** -Eigenschaft für jedes der folgenden Textfelder:

    -   **Bestellnummer**

    -   **Auftrags-ID**

    -   **Bestellnummer**

## <a name="load-the-data-from-the-service"></a>Laden Sie die Daten aus dem Dienst
Verwenden Sie das Dienstobjekt für den Proxy, um Umsatzdaten aus dem Dienst zu laden. Weisen Sie die zurückgegebenen Daten an die Datenquelle für die <xref:System.Windows.Data.CollectionViewSource> im WPF-Fenster.

### <a name="to-load-the-data-from-the-service"></a>So laden Sie die Daten aus dem Dienst

1.  In den Designer, zum Erstellen der `Window_Loaded` Ereignishandler, doppelklicken Sie auf den Text, der liest: **MainWindow**.

2.  Ersetzen Sie den Ereignishandler durch den folgenden Code. Stellen Sie sicher, dass Sie ersetzen die *"localhost"* Adresse in diesem Code mit der Adresse des lokalen Hosts auf dem Entwicklungscomputer.

     [!code-csharp[Data_WPFWCF#2](../data-tools/codesnippet/CSharp/bind-wpf-controls-to-a-wcf-data-service_2.cs)]
     [!code-vb[Data_WPFWCF#2](../data-tools/codesnippet/VisualBasic/bind-wpf-controls-to-a-wcf-data-service_2.vb)]

## <a name="navigate-sales-records"></a>Navigieren Sie Verkaufsdatensätze
Fügen Sie Code, der Benutzern ermöglicht, den Bildlauf Verkaufsdatensätze mithilfe der **\<** und **>** Schaltflächen.

### <a name="to-enable-users-to-navigate-sales-records"></a>Benutzern das Navigieren durch Sales Records ermöglichen

1.  Doppelklicken Sie im Designer auf die **<** Schaltfläche auf der Fensteroberfläche.

     Visual Studio öffnet die CodeBehind-Datei und erstellt ein neues `backButton_Click` -Ereignishandler für das <xref:System.Windows.Controls.Primitives.ButtonBase.Click> Ereignis.

2.  Fügen Sie dem generierten `backButton_Click`-Ereignishandler folgenden Code hinzu:

     [!code-csharp[Data_WPFWCF#3](../data-tools/codesnippet/CSharp/bind-wpf-controls-to-a-wcf-data-service_3.cs)]
     [!code-vb[Data_WPFWCF#3](../data-tools/codesnippet/VisualBasic/bind-wpf-controls-to-a-wcf-data-service_3.vb)]

3.  Kehren Sie zum Designer zurück, und doppelklicken Sie auf die **>** Schaltfläche.

     Visual Studio öffnet die CodeBehind-Datei und erstellt ein neues `nextButton_Click` -Ereignishandler für das <xref:System.Windows.Controls.Primitives.ButtonBase.Click> Ereignis.

4.  Fügen Sie dem generierten `nextButton_Click`-Ereignishandler folgenden Code hinzu:

     [!code-csharp[Data_WPFWCF#4](../data-tools/codesnippet/CSharp/bind-wpf-controls-to-a-wcf-data-service_4.cs)]
     [!code-vb[Data_WPFWCF#4](../data-tools/codesnippet/VisualBasic/bind-wpf-controls-to-a-wcf-data-service_4.vb)]

## <a name="saving-changes-to-sales-records"></a>Änderungen an sales Records speichern
Hinzufügen von Code, der ermöglicht Benutzern das Anzeigen und Speichern von Änderungen an sales Records mithilfe der **Änderungen speichern** Schaltfläche.

### <a name="to-add-the-ability-to-save-changes-to-sales-records"></a>Die Möglichkeit zum Speichern von Änderungen zu Sales Records hinzufügen

1.  Doppelklicken Sie im Designer auf die **Änderungen speichern** Schaltfläche.

     Visual Studio öffnet die CodeBehind-Datei und erstellt ein neues `saveButton_Click` -Ereignishandler für das <xref:System.Windows.Controls.Primitives.ButtonBase.Click> Ereignis.

2.  Fügen Sie dem `saveButton_Click`-Ereignishandler den folgenden Code hinzu.

     [!code-csharp[Data_WPFWCF#5](../data-tools/codesnippet/CSharp/bind-wpf-controls-to-a-wcf-data-service_5.cs)]
     [!code-vb[Data_WPFWCF#5](../data-tools/codesnippet/VisualBasic/bind-wpf-controls-to-a-wcf-data-service_5.vb)]

## <a name="testing-the-application"></a>Testen der Anwendung
Erstellen Sie die Anwendung und führen Sie sie aus; prüfen Sie, ob Sie die Kundendatensätze anzeigen und ändern können.

### <a name="to-test-the-application"></a>So testen Sie die Anwendung

1.  Auf **erstellen** Menü klicken Sie auf **Projektmappe**. Überprüfen Sie, ob die Lösung ohne Fehler erstellt wurde.

2.  Drücken Sie **STRG + F5**.

     Visual Studio startet den **AdventureWorksService** Projekt, ohne es zu debuggen.

3.  In **Projektmappen-Explorer**, mit der rechten Maustaste die **AdventureWorksSalesEditor** Projekt.

4.  Klicken Sie im Kontextmenü unter **Debuggen**, klicken Sie auf **neue Instanz starten**.

     Die Anwendung wird ausführt. Überprüfen Sie Folgendes:

    -   Die Textfelder zeigen unterschiedliche Datenfelder aus dem ersten Verkaufsdatensatz, die die Auftrags-ID hat **71774**.

    -   Klicken Sie auf die **>** oder **<** Schaltflächen zum Navigieren durch andere Verkaufsdatensätze.

5.  Geben Sie in einem Verkaufsdatensätze, etwas Text in die **Kommentar** Feld, und klicken Sie dann auf **Änderungen speichern**.

6.  Schließen Sie die Anwendung und starten Sie sie dann erneut aus Visual Studio.

7.  Navigieren Sie zum Verkaufsdatensatz, den Sie geändert haben und überprüfen Sie, dass die Änderung nach dem Schließen und erneut Öffnen noch vorhanden ist.

8.  Schließen Sie die Anwendung.

## <a name="next-steps"></a>Nächste Schritte

Nach Abschluss dieser exemplarischen Vorgehensweise können Sie folgende Aufgaben ausführen:

-   Informationen zum Verwenden der **Datenquellen** in Visual Studio für die Bindung von WPF-Steuerelementen an andere Typen von Datenquellen. Weitere Informationen finden Sie unter [Binden von WPF-Steuerelementen an ein Dataset](../data-tools/bind-wpf-controls-to-a-dataset.md).

-   Informationen zum Verwenden der **Datenquellen** in Visual Studio für die Anzeige zugehöriger Daten (d. h. Daten in einer über-/ unterordnungsbeziehung) in WPF-Steuerelemente. Weitere Informationen finden Sie unter [Exemplarische Vorgehensweise: Anzeigen von verknüpften Daten in einer WPF-Anwendung](../data-tools/display-related-data-in-wpf-applications.md).

## <a name="see-also"></a>Siehe auch

- [Binden von WPF-Steuerelementen an Daten in Visual Studio](../data-tools/bind-wpf-controls-to-data-in-visual-studio.md)
- [WPF-Steuerelemente an einen Datensatz binden](../data-tools/bind-wpf-controls-to-a-dataset.md)
- [Überblick über WCF ((.NET Framework)](/dotnet/framework/data/wcf/wcf-data-services-overview)
- [Übersicht über Entity Framework ((.NET Framework)](/dotnet/framework/data/adonet/ef/overview)
- [Datenbindung (Übersicht) ((.NET Framework)](/dotnet/framework/wpf/data/data-binding-overview)