---
title: "Exemplarische Vorgehensweise: Binden von WPF-Steuerelementen an einen WCF-Datendienst | Microsoft Docs"
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
ms.assetid: 8823537c-82f0-41f7-bf30-705f0e5e59fd
caps.latest.revision: 40
caps.handback.revision: 38
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# Exemplarische Vorgehensweise: Binden von WPF-Steuerelementen an einen WCF-Datendienst
In dieser exemplarischen Vorgehensweise erstellen Sie eine WPF\-Anwendung, die datengebundene Steuerelemente enthält.  Die Steuerelemente sind an Kundendatensätze gebunden, die in einem [!INCLUDE[ss_data_service](../data-tools/includes/ss_data_service_md.md)] gekapselt sind.  Sie fügen außerdem die Schaltflächen hinzu, mit denen Kunden Datensätze anzeigen und ändern können.  
  
 In dieser exemplarischen Vorgehensweise werden die folgenden Aufgaben veranschaulicht:  
  
-   Erstellen eines Entity Data Models, das aus Daten in der Beispieldatenbank AdventureWorksLT generiert wird.  
  
-   Erstellen eines [!INCLUDE[ss_data_service](../data-tools/includes/ss_data_service_md.md)], der die Daten im Entity Data Model für eine WPF\-Anwendung verfügbar macht.  
  
-   Erstellen eines Satzes datengebundener Steuerelemente durch Ziehen von Elementen aus dem **Datenquellenfenster** zum WPF\-Designer.  
  
-   Erstellen von Schaltflächen, mit denen die Navigation vorwärts und rückwärts durch die Kundendatensätze möglich ist.  
  
-   Erstellen einer Schaltfläche, die Änderungen an den Daten in den Steuerelementen des [!INCLUDE[ss_data_service](../data-tools/includes/ss_data_service_md.md)] und der darunterliegenden Datenquelle speichert.  
  
     [!INCLUDE[note_settings_general](../data-tools/includes/note_settings_general_md.md)]  
  
## Vorbereitungsmaßnahmen  
 Zum Durchführen dieser exemplarischen Vorgehensweise benötigen Sie die folgenden Komponenten:  
  
-   [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)]  
  
-   Zugriff auf eine laufende Instanz von SQL Server oder SQL Server Express, an die eine AdventureWorksLT\-Beispieldatenbank angefügt ist.  Sie können die AdventureWorksLT\-Datenbankvon der [CodePlex\-Website](http://go.microsoft.com/fwlink/?linkid=87843) herunterladen.  
  
 Vorkenntnisse der folgenden Konzepte sind ebenfalls hilfreich, wenn auch für die Durchführung der exemplarischen Vorgehensweise nicht erforderlich:  
  
-   WCF Data Services.  Weitere Informationen finden Sie unter [Übersicht](../Topic/WCF%20Data%20Services%20Overview.md).  
  
-   Datenmodelle in [!INCLUDE[ssAstoria](../data-tools/includes/ssastoria_md.md)].  
  
-   Entity Data Models und der ADO.NET Entity Framework.  Weitere Informationen finden Sie unter [Übersicht über das Entity Framework](../Topic/Entity%20Framework%20Overview.md).  
  
-   Arbeiten mit dem WPF\-Designer.  Weitere Informationen finden Sie unter [Übersicht über den WPF\- und Silverlight\-Designer](http://msdn.microsoft.com/de-de/570b7a5c-0c86-4326-a371-c9b63378fc62).  
  
-   WPF\-Datenbindung.  Weitere Informationen finden Sie unter [Übersicht über Datenbindung](../Topic/Data%20Binding%20Overview.md).  
  
## Erstellen des Dienstprojekts  
 Beginnen Sie diese exemplarische Vorgehensweise, indem Sie ein Projekt für einen [!INCLUDE[ss_data_service](../data-tools/includes/ss_data_service_md.md)] erstellen.  
  
#### So erstellen Sie das Dienstprojekt  
  
1.  Starten Sie Visual Studio.  
  
2.  Zeigen Sie im Menü **Datei** auf **Neu**, und klicken Sie dann auf **Projekt**.  
  
3.  Erweitern Sie **Visual C\#** oder **Visual Basic** und wählen Sie dann **Web**.  
  
4.  Wählen Sie die Projektvorlage **ASP.NET Web Application**.  
  
5.  Geben Sie im Feld **Name** den Namen `AdventureWorksService` ein und klicken Sie **OK**.  
  
     Visual Studio erstellt das Projekt `AdventureWorksService`.  
  
6.  Klicken Sie im **Projektmappen\-Explorer** mit der rechten Maustaste auf **Default.aspx** und wählen Sie **Löschen**.  Diese Datei wird für diese exemplarische Vorgehensweise benötigt.  
  
## Erstellen eines Entity Data Models für den Dienst  
 Damit die Daten mithilfe eines [!INCLUDE[ss_data_service](../data-tools/includes/ss_data_service_md.md)] für eine Anwendung verfügbar gemacht werden, müssen Sie ein Datenmodell für den Dienst definieren.  Der [!INCLUDE[ss_data_service](../data-tools/includes/ss_data_service_md.md)] unterstützt zwei Arten von Datenmodellen: Entity Data Models und benutzerdefinierte Datenmodelle, die mithilfe von Common Language Runtime \(CLR\) Objekten definiert werden, die die <xref:System.Linq.IQueryable%601>\-Schnittstelle implementieren.  In dieser exemplarischen Vorgehensweise erstellen Sie ein Entity Data Model für das Datenmodell.  
  
#### So erstellen Sie ein Entity Data Model  
  
1.  Klicken Sie im Menü **Projekt** auf **Neues Element hinzufügen**.  
  
2.  Klicken Sie in der Liste "Installierte Vorlagen" auf **Daten** und wählen Sie dann das Projektelement **ADO.NET Entity Data Model** aus.  
  
3.  Ändern Sie den Namen auf `AdventureWorksModel.edmx` und klicken Sie **Hinzufügen**.  
  
     Der **Assistent für Entity Data Model** wird geöffnet.  
  
4.  Klicken Sie auf der Seite **Modellinhalt auswählen** auf **Aus Datenbank generieren** und klicken Sie **Weiter**.  
  
5.  Wählen Sie auf der Seite **Wählen Sie Ihre Datenverbindung aus** eine der folgenden Optionen aus:  
  
    -   Wenn in der Dropdownliste eine Datenverbindung zur Beispieldatenbank "AdventureWorksLT" verfügbar ist, wählen Sie diese aus.  
  
         \- oder \-  
  
    -   Klicken Sie **Neue Verbindung** und erstellen Sie eine Verbindung zur Datenbank AdventureWorksLT.  
  
6.  Achten Sie darauf, dass auf der Seite **Wählen Sie Ihre Datenverbindung aus** die Option **Entitätsverbindungseinstellungen in App.Config speichern unter** und klicken Sie dann auf **Weiter**.  
  
7.  Erweitern Sie auf der Seite **Datenbankobjekte auswählen** den Punkt **Tabellen** und wählen Sie dann die Tabelle **SalesOrderHeader** aus.  
  
8.  Klicken Sie auf **Fertig stellen**.  
  
## Erstellen des Diensts  
 Erstellen Sie einen [!INCLUDE[ss_data_service](../data-tools/includes/ss_data_service_md.md)], der die Daten im Entity Data Model für eine WPF\-Anwendung verfügbar macht.  
  
#### So erstellen Sie den Dienst  
  
1.  Wählen Sie im Menü **Projekt** auf **Neues Element hinzufügen**.  
  
2.  Klicken Sie in der Liste "Installierte Vorlagen" auf **Web** und wählen Sie dann das Projektelement **WCF Data Services** aus.  
  
3.  Geben Sie im Feld **Name** den Namen `AdventureWorksService.svc` ein und klicken Sie **Hinzufügen**.  
  
     Visual Studio fügt `AdventureWorksService.svc` dem Projekt hinzu.  
  
## Den Dienst konfigurieren  
 Damit der Dienst mit dem von Ihnen erstellten Entity Data Model funktioniert, muss er konfiguriert werden.  
  
#### So konfigurieren Sie den Dienst  
  
1.  Ersetzen Sie in der Codedatei `AdventureWorks.svc`die Klassendeklaration `AdventureWorksService` durch folgenden Code.  
  
     [!code-cs[Data_WPFWCF#1](../data-tools/codesnippet/CSharp/bind-wpf-controls-to-a-wcf-data-service_1.cs)]
     [!code-vb[Data_WPFWCF#1](../data-tools/codesnippet/VisualBasic/bind-wpf-controls-to-a-wcf-data-service_1.vb)]  
  
     Dieser Code aktualisiert die Klasse `AdventureWorksService`, sodass sie sich von einem <xref:System.Data.Services.DataService%601> ableitet, der mit der `AdventureWorksLTEntities`\-Objektkontextklasse Ihres Entity Data Models funktioniert.  Außerdem aktualisiert er die Methode `InitializeService`, sodass Clients des Diensts vollen Lese\-\/Schreibzugriff auf die `SalesOrderHeader`\-Entität haben.  
  
2.  Erstellen Sie das Projekt und überprüfen Sie, ob es fehlerfrei erstellt wird.  
  
## Erstellen der WPF\-Clientanwendung  
 Um Daten aus dem [!INCLUDE[ss_data_service](../data-tools/includes/ss_data_service_md.md)] anzuzeigen, erstellen Sie eine neue WPF\-Anwendung mit einer Datenquelle, die auf dem Dienst basiert.  Später in dieser exemplarischen Vorgehensweise werden Sie datengebundene Steuerelemente zur Anwendung hinzufügen.  
  
#### So erstellen Sie die WPF\-Clientanwendung  
  
1.  Klicken Sie im **Projektmappen\-Explorer** mit der rechten Maustaste auf den Lösungsknoten, dann auf **Hinzufügen** und wählen Sie dann **Neues Projekt**.  
  
2.  Erweitern Sie im Dialogfeld **Neues Projekt** den Punkt **Visual C\#** oder **Visual Basic** und wählen Sie dann **Windows**.  
  
3.  Wählen Sie die Projektvorlage **WPF\-Anwendung**.  
  
4.  Geben Sie im Feld **Name** den Namen `AdventureWorksSalesEditor` ein und klicken Sie **OK**.  
  
     Visual Studio fügt das Projekt `AdventureWorksSalesEditor` der Lösung hinzu.  
  
5.  Klicken Sie im Menü **Daten** auf **Datenquellen anzeigen**.  
  
     Das **Datenquellenfenster** wird geöffnet.  
  
6.  Klicken Sie im **Datenquellenfenster** auf **Neue Datenquelle hinzufügen**.  
  
     Der **Assistent zum Konfigurieren von Datenquellen** wird geöffnet.  
  
7.  Wählen Sie auf der Seite **Datenquellentyp auswählen** des Assistenten **Dienst** und klicken Sie auf **Weiter**.  
  
8.  Klicken Sie im Dialogfeld **Dienstverweis hinzufügen** auf **Ermitteln**.  
  
     Visual Studio durchsucht die aktuelle Lösung nach verfügbaren Diensten und fügt `AdventureWorksService.svc` zur Liste verfügbarer Dienste im Feld **Dienste** hinzu.  
  
9. Geben Sie im Feld **Namespace** die Zeichenfolge `AdventureWorksService` ein.  
  
10. Geben Sie im Feld **Dienste** den Namen **AdventureWorksService.svc** ein und klicken Sie **OK**.  
  
     Visual Studio lädt die Dienstinformation herunter und kehrt dann zum **Assistenten zum Konfigurieren von Datenquellen** zurück.  
  
11. Klicken Sie auf der Seite **Dienstverweis hinzufügen** auf **Fertig stellen**.  
  
     Visual Studio fügt Knoten hinzu, der die vom Dienst zurückgegeben Daten im **Datenquellenfenster** anzeigt.  
  
## Die Benutzeroberfläche des Fensters definieren  
 Fügen Sie dem Fenster eine Reihe von Schaltflächen hinzu, indem Sie XAML im WPF\-Designer ändern.  Später in dieser exemplarischen Vorgehensweise fügen Sie dann Code hinzu, mit dem Anwender die Verkaufsdatensätze mithilfe dieser Schaltflächen anzeigen und ändern können.  
  
#### So erstellen Sie das Fensterlayout  
  
1.  Doppelklicken Sie in**Projektmappen\-Explorer** MainWindow.xaml.  
  
     Das Fenster wird automatisch im WPF\-Designer geöffnet.  
  
2.  Fügen Sie in der [!INCLUDE[TLA#tla_titlexaml](../data-tools/includes/tlasharptla_titlexaml_md.md)]\-Ansicht des Designers den folgenden Code zwischen den `<Grid>`\-Tags hinzu:  
  
    ```  
    <Grid.RowDefinitions>  
        <RowDefinition Height="75" />  
        <RowDefinition Height="525" />  
    </Grid.RowDefinitions>  
    <Button HorizontalAlignment="Left" Margin="22,20,0,24" Name="backButton" Width="75"><</Button>  
    <Button HorizontalAlignment="Left" Margin="116,20,0,24" Name="nextButton" Width="75">></Button>  
    <Button HorizontalAlignment="Right" Margin="0,21,46,24" Name="saveButton" Width="110">Save changes</Button>  
    ```  
  
3.  Erstellen Sie das Projekt.  
  
## Erstellen der datengebundenen Steuerelemente  
 Erstellen Sie Steuerelemente zum Anzeigen der Kundedatensätze, indem Sie den Knoten `SalesOrderHeaders` vom **Datenquellenfenster** auf den Designer ziehen.  
  
#### So erstellen Sie ein datengebundene Steuerelemente  
  
1.  Klicken Sie im **Datenquellenfenster** das Dropdownmenü für den Knoten **SalesOrderHeaders** und wählen Sie **Details**.  
  
2.  Erweitern Sie den Knoten **SalesOrderHeaders**.  
  
3.  In diesem Beispiel werden einige Felder nicht angezeigt. Klicken Sie also das Dropdownmenü neben den folgenden Knoten und wählen Sie **Keine**:  
  
    -   **CreditCardApprovalCode**  
  
    -   **ModifiedDate**  
  
    -   **OnlineOrderFlag**  
  
    -   **RevisionNumber**  
  
    -   **rowguid**  
  
     Durch diese Aktion wird Visual Studio daran gehindert, im nächsten Schritt datengebundene Steuerelemente für diese Knoten zu erstellen.  Bei dieser exemplarischen Vorgehensweise wird davon ausgegangen, dass der Endbenutzer diese Daten nicht sehen muss.  
  
4.  Ziehen Sie aus dem **Datenquellenfenster** den Knoten **SalesOrderHeaders** auf das Raster unter der Zeile, in der die Schaltflächen sind.  
  
     Visual Studio erzeugt XAML und Code, der einen Satz von Steuerelementen erstellt, die zu Daten in der Tabelle **Product** enthalten sind.  Weitere Informationen über das generierte XAML und den Code finden Sie unter [Binden von WPF\-Steuerelementen an Daten in Visual Studio](../data-tools/bind-wpf-controls-to-data-in-visual-studio1.md).  
  
5.  Klicken Sie im Designer auf das Textfeld neben der Bezeichnung **Customer ID**.  
  
6.  Wählen Sie im Fenster **Eigenschaften** das Kontrollkästchen neben der Eigenschaft **IsReadOnly**.  
  
7.  Legen Sie die Eigenschaft **IsReadOnly** für jedes der folgenden Textfelder fest:  
  
    -   **Purchase Order Number**  
  
    -   **Sales Order ID**  
  
    -   **Sales Order Number**  
  
## Laden Sie die Daten aus dem Dienst  
 Verwenden Sie das Dienstproxyobjekt des Diensts und weisen Sie dann die zurückgegeben Daten der Datenquelle für die <xref:System.Windows.Data.CollectionViewSource> im WPF\-Fenster zu.  
  
#### So laden Sie die Daten aus dem Dienst  
  
1.  Doppelklicken Sie im Designer auf folgenden Text: **MainWindow** zum Erstellen des `Window_Loaded`\-Ereignishandlers.  
  
2.  Ersetzen Sie den Ereignishandler durch den folgenden Code.  Achten Sie darauf, dass Sie die Adresse *localhost* in diesem Code durch die lokale Hostadresse Ihres Entwicklungscomputers ersetzen.  
  
     [!code-cs[Data_WPFWCF#2](../data-tools/codesnippet/CSharp/bind-wpf-controls-to-a-wcf-data-service_2.cs)]
     [!code-vb[Data_WPFWCF#2](../data-tools/codesnippet/VisualBasic/bind-wpf-controls-to-a-wcf-data-service_2.vb)]  
  
## Navigieren durch Sales Records  
 Fügen Sie Code hinzu, mit dessen Hilfe Benutzer durch die Salesdatensätze scrollen können, indem Sie die Schaltflächen **\<** und **\>** verwenden.  
  
#### Benutzern das Navigieren durch Sales Records ermöglichen  
  
1.  Doppelklicken Sie im Designer die Schaltfläche **\<** auf der Fensteroberfläche.  
  
     Visual Studio öffnet die CodeBehind\-Datei und erstellt einen neuen `backButton_Click`\-Ereignishandler für das <xref:System.Windows.Controls.Primitives.ButtonBase.Click>\-Ereignis.  
  
2.  Fügen Sie dem generierten `backButton_Click`\-Ereignishandler folgenden Code hinzu:  
  
     [!code-cs[Data_WPFWCF#3](../data-tools/codesnippet/CSharp/bind-wpf-controls-to-a-wcf-data-service_3.cs)]
     [!code-vb[Data_WPFWCF#3](../data-tools/codesnippet/VisualBasic/bind-wpf-controls-to-a-wcf-data-service_3.vb)]  
  
3.  Kehren Sie zum Designer zurück und doppelklicken Sie die Schaltfläche **\>**.  
  
     Visual Studio öffnet die CodeBehind\-Datei und erstellt einen neuen `nextButton_Click`\-Ereignishandler für das <xref:System.Windows.Controls.Primitives.ButtonBase.Click>\-Ereignis.  
  
4.  Fügen Sie dem generierten `nextButton_Click`\-Ereignishandler folgenden Code hinzu:  
  
     [!code-cs[Data_WPFWCF#4](../data-tools/codesnippet/CSharp/bind-wpf-controls-to-a-wcf-data-service_4.cs)]
     [!code-vb[Data_WPFWCF#4](../data-tools/codesnippet/VisualBasic/bind-wpf-controls-to-a-wcf-data-service_4.vb)]  
  
## Änderungen an Sales Records speichern  
 Fügen Sie Code hinzu, mit dem Benutzer Änderungen an Sales Records sowohl anzeigen als auch mithilfe der Taste **Änderungen speichern** speichern können.  
  
#### Die Möglichkeit zum Speichern von Änderungen zu Sales Records hinzufügen  
  
1.  Doppelklicken Sie im Designer auf die Schaltfläche **Änderungen speichern**.  
  
     Visual Studio öffnet die CodeBehind\-Datei und erstellt einen neuen `saveButton_Click`\-Ereignishandler für das <xref:System.Windows.Controls.Primitives.ButtonBase.Click>\-Ereignis.  
  
2.  Fügen Sie dem `saveButton_Click`\-Ereignishandler den folgenden Code hinzu.  
  
     [!code-cs[Data_WPFWCF#5](../data-tools/codesnippet/CSharp/bind-wpf-controls-to-a-wcf-data-service_5.cs)]
     [!code-vb[Data_WPFWCF#5](../data-tools/codesnippet/VisualBasic/bind-wpf-controls-to-a-wcf-data-service_5.vb)]  
  
## Testen der Anwendung  
 Erstellen Sie die Anwendung und führen Sie sie aus; prüfen Sie, ob Sie die Kundendatensätze anzeigen und ändern können.  
  
#### So testen Sie die Anwendung  
  
1.  Klicken Sie im Menü **Build** auf **Projektmappe erstellen**.  Überprüfen Sie, ob die Lösung ohne Fehler erstellt wurde.  
  
2.  Drücken Sie **STRG\+F5**.  
  
     Visual Studio startet das Projekt **AdventureWorksService** ohne Debugging.  
  
3.  Klicken Sie im **Projektmappen\-Explorer** mit der rechten Maustaste das Projekt **AdventureWorksSalesEditor**.  
  
4.  Klicken Sie im Kontextmenü unter **Debug** auf **Neue Instanz starten**.  
  
     Die Anwendung wird ausführt.  Überprüfen Sie Folgendes:  
  
    -   Die Textfelder zeigen unterschiedliche Datenfelder aus dem ersten Verkaufsdatensatz an, der die Sales Order ID **71774** hat.  
  
    -   Sie können die Schaltflächen **\>** oder **\<** für die Navigation durch andere Verkaufsdatensätze klicken.  
  
5.  Geben Sie Text in einen der Verkaufsdatensätze im Feld **Comment** ein und klicken Sie anschließend **Änderungen speichern**.  
  
6.  Schließen Sie die Anwendung und starten Sie sie dann erneut aus Visual Studio.  
  
7.  Navigieren Sie zum Verkaufsdatensatz, den Sie geändert haben und überprüfen Sie, dass die Änderung nach dem Schließen und erneut Öffnen noch vorhanden ist.  
  
8.  Schließen Sie die Anwendung.  
  
## Nächste Schritte  
 Nach Abschluss dieser exemplarischen Vorgehensweise können Sie folgende Aufgaben ausführen:  
  
-   Erfahren Sie, wie Sie das **Datenquellenfenster** in Visual Studio für die Bindung von WPF\-Steuerelementen an andere Typen von Datenquellen verwenden.  Weitere Informationen finden Sie unter [Exemplarische Vorgehensweise: Binden von WPF\-Steuerelementen an ein Dataset](../data-tools/bind-wpf-controls-to-a-dataset.md).  
  
-   Erfahren Sie, wie Sie das **Datenquellenfenster** in Visual Studio für die Anzeige zugehöriger Daten \(das heißt, Daten in einer Beziehung zwischen übergeordneten und untergeordneten Daten\) in WPF\-Steuerelementen verwenden.  Weitere Informationen finden Sie unter [Exemplarische Vorgehensweise: Anzeigen verknüpfter Daten in einer WPF\-Anwendung](../data-tools/walkthrough-displaying-related-data-in-a-wpf-application.md).  
  
## Siehe auch  
 [Binden von WPF\-Steuerelementen an Daten in Visual Studio](../data-tools/bind-wpf-controls-to-data-in-visual-studio1.md)   
 [Gewusst wie: Binden von WPF\-Steuerelementen an Daten in Visual Studio](../data-tools/bind-wpf-controls-to-data-in-visual-studio2.md)   
 [Exemplarische Vorgehensweise: Binden von WPF\-Steuerelementen an ein Dataset](../data-tools/bind-wpf-controls-to-a-dataset.md)   
 [Übersicht](../Topic/WCF%20Data%20Services%20Overview.md)   
 [Übersicht über das Entity Framework](../Topic/Entity%20Framework%20Overview.md)   
 [Übersicht über den WPF\- und Silverlight\-Designer](http://msdn.microsoft.com/de-de/570b7a5c-0c86-4326-a371-c9b63378fc62)   
 [Übersicht über Datenbindung](../Topic/Data%20Binding%20Overview.md)