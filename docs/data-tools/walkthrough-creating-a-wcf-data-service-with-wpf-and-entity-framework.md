---
title: "Walkthrough: Creating and Accessing a WCF Data Service in Visual Studio | Microsoft Docs"
ms.custom: ""
ms.date: "12/15/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "data services in Visual Studio"
  - "WCF Data Services, Visual Studio"
  - "ADO.NET Data Services, Visual Studio"
  - "WCF data services in Visual Studio"
ms.assetid: da66ad1b-a25d-485c-af13-2d18f0422e3d
caps.latest.revision: 24
caps.handback.revision: 21
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# Walkthrough: Creating and Accessing a WCF Data Service in Visual Studio
In dieser exemplarischen Vorgehensweise wird dargestellt, wie ein einfacher [!INCLUDE[ss_data_service](../data-tools/includes/ss_data_service_md.md)] erstellt wird, der in einer [!INCLUDE[vstecasp](../code-quality/includes/vstecasp_md.md)]\-Webanwendung gehostet wird, und wie dann von einer Windows Forms\-Anwendung aus darauf zugegriffen wird.  
  
 In dieser exemplarischen Vorgehensweise werden Sie:  
  
-   Eine Webanwendung erstellen, um einen [!INCLUDE[ss_data_service](../data-tools/includes/ss_data_service_md.md)] zu hosten.  
  
-   Ein [!INCLUDE[adonet_edm](../data-tools/includes/adonet_edm_md.md)] zur Darstellung der Tabelle "Customers" in der Northwind\-Datenbank erstellen.  
  
-   Erstellen Sie eine [!INCLUDE[ss_data_service](../data-tools/includes/ss_data_service_md.md)].  
  
-   Eine Clientanwendung erstellen und dieser einen Verweis auf den [!INCLUDE[ss_data_service](../data-tools/includes/ss_data_service_md.md)] hinzufügen.  
  
-   Die Datenbindung zum Dienst aktivieren und die Benutzeroberfläche erstellen.  
  
-   Optional Filterfunktionen zur Anwendung hinzufügen.  
  
## Vorbereitungsmaßnahmen  
 Zum Durchführen dieser exemplarischen Vorgehensweise benötigen Sie die folgenden Komponenten:  
  
-   Die Beispieldatenbank Northwind.  
  
     Befindet sich diese Datenbank nicht auf Ihrem Entwicklungscomputer, können Sie diese aus dem [Microsoft Download Center](http://go.microsoft.com/fwlink/?LinkID=98088) herunterladen.  Anweisungen hierzu finden Sie unter [Herunterladen von Beispieldatenbanken](../Topic/Downloading%20Sample%20Databases.md).  
  
## Erstellen des Diensts  
 Um einen [!INCLUDE[ss_data_service](../data-tools/includes/ss_data_service_md.md)] zu erstellen, fügen Sie ein Webprojekt hinzu. Dann erstellen Sie ein [!INCLUDE[adonet_edm](../data-tools/includes/adonet_edm_md.md)] und erstellen anschließend den Dienst aus dem Modell.  
  
 Im ersten Schritt fügen Sie ein Webprojekt zum Hosten des Diensts hinzu.  
  
 [!INCLUDE[note_settings_general](../data-tools/includes/note_settings_general_md.md)]  
  
#### So erstellen Sie das Webprojekt  
  
1.  Wählen Sie in der Menüleiste **Datei**, **Neu**, **Projekt** aus.  
  
2.  Erweitern Sie im Dialogfeld **Neues Projekt** den Knoten **Visual Basic** oder **Visual C\#** sowie **Web**, und wählen Sie dann die Vorlage **ASP.NET\-Webanwendung** aus.  
  
3.  Geben Sie "NorthwindWeb" im Textfeld **Name** ein, und wählen Sie dann die Schaltfläche **OK**.  
  
4.  Wählen Sie im Dialogfeld **Neues ASP.NET\-Projekt** aus der Liste **Vorlage auswählen** die Option **Leer**, und klicken Sie dann auf die Schaltfläche **OK**.  
  
 In diesem Schritt erstellen Sie ein [!INCLUDE[adonet_edm](../data-tools/includes/adonet_edm_md.md)] zur Darstellung der Tabelle "Customers" in der Northwind\-Datenbank.  
  
#### So erstellen Sie das Entity Data Model  
  
1.  Wählen Sie in der Menüleiste **Projekt**,  **Neues Element hinzufügen** aus.  
  
2.  Wählen Sie im Dialogfeld **Neues Element hinzufügen** den Knoten **Daten** und anschließend das Element **ADO.NET Entity Data Model** aus.  
  
3.  Geben Sie **NorthwindModel** im Textfeld `Name` ein, und wählen Sie dann die Schaltfläche **Hinzufügen**.  
  
     Der Assistent für Entity Data Model wird angezeigt.  
  
4.  Wählen Sie im Entity Data Model\-Assistenten auf der Seite **Modellinhalte auswählen** das Element **EF\-Designer aus Datenbank** aus, und wählen Sie dann **Weiter**.  
  
5.  Führen Sie auf der Seite **Wählen Sie Ihre Datenverbindung aus** einen der folgenden Schritte aus:  
  
    -   Wenn eine Datenverbindung mit der Beispieldatenbank Northwind in der Dropdownliste verfügbar ist, wählen Sie sie aus.  
  
         \- oder \-  
  
    -   Wählen Sie die Schaltfläche **Neue Verbindung**, um eine neue Datenverbindung zu konfigurieren.  Weitere Informationen finden Sie unter [Gewusst wie: Erstellen von Verbindungen mit SQL Server\-Datenbanken](http://msdn.microsoft.com/de-de/360c340d-e5a6-4a7e-a569-e95d500be43d).  
  
6.  Wenn für die Datenbank ein Kennwort erforderlich sein, wählen Sie das Optionsfeld **Ja, vertrauliche Daten in die Verbindungszeichenfolge einschließen** und dann die Schaltfläche **Weiter**.  
  
    > [!NOTE]
    >  Wenn ein Dialogfeld angezeigt wird, wählen Sie **Ja**, um die Datei im Projekt zu speichern.  
  
7.  Wählen Sie auf der Seite **Wählen Sie Ihre Version** das Optionsfeld **Entity Framework 5.0** aus, und klicken Sie dann auf die Schaltfläche **Weiter**.  
  
    > [!NOTE]
    >  Um die aktuelle Version vom Entity Framework 6 mit WCF\-Diensten zu verwenden, müssen Sie das WCF Data Services Entity Framework Provider NuGet\-Paket installieren.  Weitere Informationen finden Sie unter [Verwenden von WCF Data Services 5.6.0 mit Entity Framework 6\+](http://blogs.msdn.com/b/odatateam/archive/2013/10/02/using-wcf-data-services-5-6-0-with-entity-framework-6.aspx) \(möglicherweise nur in englischer Sprache\).  
  
8.  Erweitern Sie auf der Seite **Datenbankobjekte auswählen** den Knoten **Tabellen**, aktivieren Sie das Kontrollkästchen **Customers**, und wählen Sie dann die Schaltfläche **Fertig stellen**.  
  
     Das Entitätsmodelldiagramm wird angezeigt, und dem Projekt wird die Datei NorthwindModel.edmx hinzugefügt.  
  
 In diesem Schritt erstellen und testen Sie den Datendienst.  
  
#### So erstellen Sie den Datendienst  
  
1.  Wählen Sie in der Menüleiste **Projekt**,  **Neues Element hinzufügen** aus.  
  
2.  Wählen Sie im Dialogfeld **Neues Element hinzufügen** den Knoten **Web** und anschließend das Element **WCF Data Service 5.6**.  
  
3.  Geben Sie im Textfeld **Name** den Eintrag `NorthwindCustomers` ein, und wählen Sie dann die Schaltfläche **Hinzufügen**.  
  
     Die Datei "NorthwindCustomers.svc" wird im **Code\-Editor** angezeigt.  
  
4.  Suchen Sie im **Code\-Editor** den ersten `TODO:`\-Kommentar, und ersetzen Sie den Code durch Folgendes:  
  
     [!code-vb[WCFDataServiceWalkthrough#1](../data-tools/codesnippet/VisualBasic/walkthrough-creating-a-wcf-data-service-with-wpf-and-entity-framework_1.vb)]
     [!code-cs[WCFDataServiceWalkthrough#1](../data-tools/codesnippet/CSharp/walkthrough-creating-a-wcf-data-service-with-wpf-and-entity-framework_1.cs)]  
  
5.  Ersetzen Sie die Kommentare im `InitializeService`\-Ereignishandler durch folgenden Code:  
  
     [!code-vb[WCFDataServiceWalkthrough#2](../data-tools/codesnippet/VisualBasic/walkthrough-creating-a-wcf-data-service-with-wpf-and-entity-framework_2.vb)]
     [!code-cs[WCFDataServiceWalkthrough#2](../data-tools/codesnippet/CSharp/walkthrough-creating-a-wcf-data-service-with-wpf-and-entity-framework_2.cs)]  
  
6.  Wählen Sie zum Ausführen des Dienstes auf der Menüleiste **Debuggen**, **Starten ohne Debugging** aus.  Ein Browserfenster wird geöffnet, und das XML\-Schema für den Dienst wird angezeigt.  
  
7.  Geben Sie in der Leiste **Adresse** am Ende der URL für "NorthwindCustomers.svc" die Zeichenfolge `Customers` ein, und wählen Sie die EINGABETASTE.  
  
     Eine XML\-Darstellung der Daten in der Tabelle "Customers" wird angezeigt.  
  
    > [!NOTE]
    >  In einigen Fällen interpretiert Internet Explorer die Daten fälschlicherweise als RSS\-Feed.  Sie müssen sicherstellen, dass die Option zum Anzeigen von RSS\-Feeds deaktiviert ist.  Weitere Informationen finden Sie unter [Troubleshooting Service References](../data-tools/troubleshooting-service-references.md).  
  
8.  Schließen Sie das Browserfenster.  
  
 In den nächsten Schritten erstellen Sie eine Windows Forms\-Clientanwendung zur Verwendung des Diensts.  
  
## Erstellen der Clientanwendung  
 Zum Erstellen der Clientanwendung fügen Sie ein zweites Projekt hinzu, dem Sie einen Dienstverweis hinzufügen. Daraufhin konfigurieren Sie eine Datenquelle, und erstellen eine Benutzeroberfläche zum Anzeigen der Daten des Diensts.  
  
 Im ersten Schritt fügen Sie der Projektmappe ein Windows Forms\-Projekt hinzu und legen dieses als Startprojekt fest.  
  
#### So erstellen Sie die Clientanwendung  
  
1.  Wählen Sie auf der Menüleiste "Datei", **Hinzufügen**, **Neues Projekt**.  
  
2.  Erweitern Sie im Dialogfeld **Neues Projekt** den Knoten **Visual Basic** oder **Visual C\#**, wählen Sie den Knoten **Windows** und dann **Windows Forms\-Anwendung**.  
  
3.  Geben Sie im Textfeld **Name** den Eintrag `NorthwindClient` ein, und wählen Sie dann die Schaltfläche **OK**.  
  
4.  Wählen Sie im **Projektmappen\-Explorer** den **NorthwindClient**\-Projektknoten.  
  
5.  Wählen Sie in der Menüleiste **Projekt**, **Als Startprojekt festlegen** aus.  
  
 In diesem Schritt fügen Sie dem [!INCLUDE[ss_data_service](../data-tools/includes/ss_data_service_md.md)] im Webprojekt einen Dienstverweis hinzu.  
  
#### So fügen Sie einen Dienstverweis hinzu  
  
1.  Wählen Sie in der Menüleiste **Projekt**, **Dienstverweis hinzufügen** aus.  
  
2.  Wählen Sie im Dialogfeld **Dienstverweis hinzufügen** die Schaltfläche **Ermitteln**.  
  
     Die URL für den NorthwindCustomers\-Dienst wird im Feld **Adresse** angezeigt.  
  
3.  Wählen Sie die Schaltfläche **OK**, um den Dienstverweis hinzuzufügen.  
  
 In diesem Schritt konfigurieren Sie eine Datenquelle, um die Datenbindung zum Dienst zu aktivieren.  
  
#### So aktivieren Sie die Datenbindung zum Dienst  
  
1.  Wählen Sie auf der Menüleiste **Ansicht**, **Weitere Fenster**, **Datenquellen** aus.  
  
2.  Wählen Sie im Fenster **Datenquellen** die Schaltfläche **Neue Datenquelle hinzufügen**.  
  
3.  Wählen Sie auf der Seite **Datenquellentyp auswählen** unter **Assistent zum Konfigurieren von Datenquellen** den Typ **Objekt** und dann die Schaltfläche **Weiter**.  
  
4.  Erweitern Sie auf der Seite **Datenobjekte auswählen** den Knoten **NorthwindClient**, und erweitern Sie dann den Knoten **NorthwindClient.ServiceReference1**.  
  
5.  Aktivieren Sie das Kontrollkästchen **Customer**, und wählen Sie dann **Fertig stellen**.  
  
 In diesem Schritt erstellen Sie die Benutzeroberfläche, auf der die Daten des Diensts angezeigt werden.  
  
#### So erstellen Sie die Benutzeroberfläche  
  
1.  Im Fenster **Datenquellen** öffnen Sie das Kontextmenü für den Knoten **Customers** und wählen **Kopieren**.  
  
2.  In Formular\-Designer **Form1.vb** oder **Form1.cs** öffnen Sie das Kontextmenü und wählen **Einfügen**.  
  
     Ein <xref:System.Windows.Forms.DataGridView>\-Steuerelement, eine <xref:System.Windows.Forms.BindingSource>\-Komponente und eine <xref:System.Windows.Forms.BindingNavigator>\-Komponente werden dem Formular hinzugefügt.  
  
3.  Wählen Sie das **CustomersDataGridView**\-Steuerelement aus, und legen Sie dann im Fenster **Eigenschaften** die Eigenschaft **Andocken** auf **Füllbereich** fest.  
  
4.  Öffnen Sie im **Projektmappen\-Explorer** das Kontextmenü für den **Form1**\-Knoten, und wählen Sie **Code anzeigen** aus, um den Code\-Editor zu öffnen, und fügen die folgende Imports\- oder Using\-Anweisung am Anfang der Datei ein:  
  
    ```vb  
    Imports NorthwindClient.ServiceReference1  
    ```  
  
    ```c#  
    using NorthwindClient.ServiceReference1;  
    ```  
  
5.  Fügen Sie dem `Form1_Load`\-Ereignishandler folgenden Code hinzu:  
  
    ```vb  
    Private Sub Form1_Load(sender As Object, e As EventArgs) Handles MyBase.Load  
            Dim proxy As New NorthwindEntities _  
    (New Uri("http://localhost:53161/NorthwindCustomers.svc/"))  
            Me.CustomersBindingSource.DataSource = proxy.Customers  
        End Sub  
    ```  
  
    ```c#  
    private void Form1_Load(object sender, EventArgs e)  
    {  
    NorthwindEntities proxy = new NorthwindEntities(new Uri("http://localhost:53161/NorthwindCustomers.svc/"));  
    this.CustomersBindingSource.DataSource = proxy.Customers;  
    }  
  
    ```  
  
6.  In **Projektmappen\-Explorer** öffnen Sie das Kontextmenü für die NorthwindCustomers.svc\-Datei und wählen **In Browser anzeigen**.  Das XML\-Schema für den Dienst wird im Internet Explorer angezeigt.  
  
7.  Kopieren Sie die URL aus der Adressleiste von Internet Explorer.  
  
8.  Markieren Sie in dem in Schritt 4 hinzugefügten Code den Text `http://localhost:53161/NorthwindCustomers.svc/`, und ersetzen Sie diesen durch die soeben kopierte URL.  
  
9. Klicken Sie auf der Menüleiste auf **Debuggen**, **Debuggen starten**, um die Anwendung zu starten.  Die Kundeninformationen werden angezeigt.  
  
 Sie verfügen nun über eine funktionierende Anwendung, die eine Liste der Kunden aus dem NorthwindCustomers\-Dienst anzeigt.  Wenn Sie weitere Daten über den Dienst bereitstellen möchten, können Sie das [!INCLUDE[adonet_edm](../data-tools/includes/adonet_edm_md.md)] so bearbeiten, dass zusätzliche Tabellen aus der Northwind\-Datenbank eingebunden werden.  
  
 Im nächsten optionalen Schritt erfahren Sie, wie die vom Dienst zurückgegebenen Daten gefiltert werden.  
  
## Hinzufügen von Filterfunktionen  
 In diesem Schritt passen Sie die Anwendung an, um die Daten nach dem Wohnort des Kunden zu filtern.  
  
#### So fügen Sie Filterung anhand des Wohnorts hinzu  
  
1.  Öffnen Sie im **Projektmappen\-Explorer** das Kontextmenü für den Knoten **Form1.vb** oder **Form1.cs** und wählen Sie dann **Öffnen**.  
  
2.  Fügen Sie dem Formular ein <xref:System.Windows.Forms.TextBox>\- und ein <xref:System.Windows.Forms.Button>\-Steuerelement aus dem **Werkzeugkasten** hinzu.  
  
3.  Öffnen Sie das Kontextmenü für das <xref:System.Windows.Forms.Button>\-Steuerelement, und wählen Sie **Code anzeigen**, und fügen Sie dann den folgenden Code im `Button1_Click`\-Ereignishandler hinzu:  
  
    ```vb  
    Private Sub Button1_Click(sender As Object, e As EventArgs) Handles Button1.Click  
            Dim proxy As New northwindEntities _  
    (New Uri("http://localhost:53161/NorthwindCustomers.svc"))  
            Dim city As String = TextBox1.Text  
  
            If city <> "" Then  
                Me.CustomersBindingSource.DataSource = From c In _  
             proxy.Customers Where c.City = city  
            End If  
  
        End Sub  
    ```  
  
    ```c#  
    private void Button1_Click(object sender, EventArgs e)  
    {  
    ServiceReference1.northwindModel.northwindEntities proxy = new northwindEntities(new Uri("http://localhost:53161/NorthwindCustomers.svc"));  
    string city = TextBox1.Text;  
  
    if (!string.IsNullOrEmpty(city)) {  
    this.CustomersBindingSource.DataSource = from c in proxy.Customers where c.City == city;  
    }  
  
    }  
    ```  
  
4.  Ersetzen Sie im vorherigen Code den Text `http://localhost:53161/NorthwindCustomers.svc` durch die URL aus dem `Form1_Load`\-Ereignishandler.  
  
5.  Klicken Sie auf der Menüleiste auf **Debuggen**, **Debuggen starten**, um die Anwendung zu starten.  
  
6.  Geben Sie im Textfeld die Zeichenfolge "London" ein, und wählen Sie dann die Schaltfläche.  Nur die Kunden aus London werden angezeigt.  
  
## Siehe auch  
 [How to: Add, Update, or Remove a WCF Data Service Reference](../data-tools/how-to-add-update-or-remove-a-wcf-data-service-reference.md)