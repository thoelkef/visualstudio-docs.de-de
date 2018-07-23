---
title: 'Exemplarische Vorgehensweise: Erstellen einen WCF-Datendienst mit WPF und Entitätsframework'
ms.date: 11/04/2016
ms.topic: conceptual
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- data services in Visual Studio
- WCF Data Services, Visual Studio
- ADO.NET Data Services, Visual Studio
- WCF data services in Visual Studio
ms.assetid: da66ad1b-a25d-485c-af13-2d18f0422e3d
author: gewarren
ms.author: gewarren
manager: douge
ms.prod: visual-studio-dev15
ms.technology: vs-data-tools
ms.workload:
- data-storage
ms.openlocfilehash: d4fa9ea1538d051aebd025c641c0520197f986ef
ms.sourcegitcommit: 5b767247b3d819a99deb0dbce729a0562b9654ba
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 07/20/2018
ms.locfileid: "39178386"
---
# <a name="walkthrough-creating-a-wcf-data-service-with-wpf-and-entity-framework"></a>Exemplarische Vorgehensweise: Erstellen einen WCF-Datendienst mit WPF und Entitätsframework
In dieser exemplarischen Vorgehensweise wird veranschaulicht, wie zum Erstellen eines einfachen [!INCLUDE[ss_data_service](../data-tools/includes/ss_data_service_md.md)] , befindet sich einer [!INCLUDE[vstecasp](../code-quality/includes/vstecasp_md.md)] Webanwendung, und klicken Sie dann eine Windows Forms-Anwendung zugreifen.

In dieser exemplarischen Vorgehensweise Sie:

-   Erstellen einer Webanwendung zum Hosten einer [!INCLUDE[ss_data_service](../data-tools/includes/ss_data_service_md.md)].

-   Erstellen Sie eine [!INCLUDE[adonet_edm](../data-tools/includes/adonet_edm_md.md)] darstellt, die die `Customers` Tabelle in der Northwind-Datenbank.

-   Erstellen Sie eine [!INCLUDE[ss_data_service](../data-tools/includes/ss_data_service_md.md)].

-   Eine Clientanwendung erstellen und dieser einen Verweis auf den [!INCLUDE[ss_data_service](../data-tools/includes/ss_data_service_md.md)] hinzufügen.

-   Die Datenbindung zum Dienst aktivieren und die Benutzeroberfläche erstellen.

-   Optional Filterfunktionen zur Anwendung hinzufügen.

## <a name="prerequisites"></a>Erforderliche Komponenten
In dieser exemplarischen Vorgehensweise verwendet SQL Server Express LocalDB und der Beispieldatenbank Northwind.

1.  Wenn Sie SQL Server Express LocalDB nicht haben, installieren Sie es entweder über die [Downloadseite für SQL Server Express](https://www.microsoft.com/sql-server/sql-server-editions-express), oder über die **Visual Studio-Installer**. In der **Visual Studio-Installer**, können Sie SQL Server Express LocalDB installieren, als Teil der **datenspeicherung und-Verarbeitung** Workload oder als eine einzelne Komponente.

2.  Installieren der Northwind-Beispieldatenbank mit folgenden Schritten:

    1. Öffnen Sie in Visual Studio die **Objekt-Explorer von SQL Server** Fenster. (**Objekt-Explorer von SQL Server** installiert ist, als Teil der **datenspeicherung und-Verarbeitung** Workload im Visual Studio-Installer.) Erweitern Sie die **SQL Server** Knoten. Mit der rechten Maustaste auf der LocalDB-Instanz, und wählen Sie **neue Abfrage**.

       Ein Abfrage-Editor-Fenster wird geöffnet.

    2. Kopieren der [Northwind Transact-SQL-Skript](https://github.com/MicrosoftDocs/visualstudio-docs/blob/master/docs/data-tools/samples/northwind.sql?raw=true) in die Zwischenablage. Dieses T-SQL-Skript wird die Northwind-Datenbank von Grund auf neu erstellt und mit Daten aufgefüllt.

    3. Fügen Sie das T-SQL-Skript im Abfrage-Editor, und wählen Sie dann die **Execute** Schaltfläche.

       Klicken Sie nach kurzer Zeit die Ausführung die Abfrage abgeschlossen ist, und die Northwind-Datenbank wird erstellt.

## <a name="creating-the-service"></a>Erstellen des Diensts
Zum Erstellen einer [!INCLUDE[ss_data_service](../data-tools/includes/ss_data_service_md.md)], Sie fügen Sie ein Webprojekt hinzu, erstellen Sie eine [!INCLUDE[adonet_edm](../data-tools/includes/adonet_edm_md.md)], und erstellen Sie dann den Dienst aus dem Modell.

Im ersten Schritt fügen Sie ein Webprojekt zum Hosten des Diensts hinzu.

[!INCLUDE[note_settings_general](../data-tools/includes/note_settings_general_md.md)]

#### <a name="to-create-the-web-project"></a>Zum Erstellen von Webprojekten

1.  Klicken Sie in der Menüleiste auf **Datei** > **Neu** > **Projekt**.

2.  In der **neues Projekt** Dialogfeld erweitern Sie die **Visual Basic** oder **Visual C#-** und **Web** Knoten, und wählen Sie dann die **ASP. NET-Webanwendung** Vorlage.

3.  In der **Namen** Text geben **NorthwindWeb**, und wählen Sie dann die **OK** Schaltfläche.

4.  In der **neues ASP.NET-Projekt** Dialogfeld die **wählen Sie eine Vorlage** wählen **leere**, und wählen Sie dann die **OK** Schaltfläche.

In den nächsten Schritt erstellen Sie eine [!INCLUDE[adonet_edm](../data-tools/includes/adonet_edm_md.md)] darstellt, die die `Customers` Tabelle in der Northwind-Datenbank.

#### <a name="to-create-the-entity-data-model"></a>So erstellen Sie das Entity Data Model

1.  Wählen Sie in der Menüleiste **Projekt** > **Neues Element hinzufügen** aus.

2.  In der **neues Element hinzufügen** Dialogfeld auf die **Daten** Knoten, und wählen Sie dann die **ADO.NET Entity Data Model** Element.

3.  In der **Namen** Text geben `NorthwindModel`, und wählen Sie dann die **hinzufügen** Schaltfläche.

     Der Assistent für Entity Data Model wird angezeigt.

4.  Im Entity Data Model-Assistenten auf die **auswählen des Modellinhalts** Seite die **EF Designer aus Datenbank** Element aus, und wählen Sie dann die **Weiter** Schaltfläche.

5.  Führen Sie auf der Seite **Wählen Sie Ihre Datenverbindung aus** einen der folgenden Schritte aus:

    -   Wenn eine Datenverbindung mit der Beispieldatenbank Northwind in der Dropdownliste verfügbar ist, wählen Sie sie aus.

         - oder - 

    -   Wählen Sie die **neue Verbindung** um eine neue Datenverbindung zu konfigurieren. Weitere Informationen finden Sie unter [neue Verbindungen hinzufügen](../data-tools/add-new-connections.md).

6.  Wenn die Datenbank ein Kennwort erfordert, wählen Sie die **Ja, vertrauliche Daten enthalten, in der Verbindungszeichenfolge** Optionsfeld aus, und wählen Sie dann die **Weiter** Schaltfläche.

    > [!NOTE]
    >  Wenn ein Dialogfeld angezeigt wird, wählen Sie **Ja** zum Speichern der Datei zu Ihrem Projekt.

7.  Auf der **wählen Sie Ihre Version** Seite die **Entity Framework 5.0** Optionsfeld aus, und wählen Sie dann die **Weiter** Schaltfläche.

    > [!NOTE]
    >  Um die neueste Version von Entity Framework 6 mit WCF-Dienste verwenden zu können, müssen Sie das WCF Data Services Entity Framework Provider NuGet-Paket zu installieren. Finden Sie unter [Verwenden von WCF Data Services 5.6.0 mit Entitätsframework 6 +](http://blogs.msdn.com/b/odatateam/archive/2013/10/02/using-wcf-data-services-5-6-0-with-entity-framework-6.aspx).

8.  Auf der **Datenbankobjekte auswählen** Seite, erweitern Sie die **Tabellen** Knoten die **Kunden** aus, und wählen Sie dann die **Fertig stellen** Schaltfläche ".

     Das Entitätsmodelldiagramm wird angezeigt, und ein *NorthwindModel.edmx* Datei wird dem Projekt hinzugefügt.

In den nächsten Schritt erstellen und Testen Sie den Datendienst.

#### <a name="to-create-the-data-service"></a>So erstellen Sie den Datendienst

1.  Wählen Sie in der Menüleiste **Projekt** > **Neues Element hinzufügen** aus.

2.  In der **neues Element hinzufügen** Dialogfeld auf die **Web** Knoten, und wählen Sie dann die **WCF Data Service 5.6** Element.

3.  In der **Namen** Text geben `NorthwindCustomers`, und wählen Sie dann die **hinzufügen** Schaltfläche.

     Die **NorthwindCustomers.svc** Datei wird angezeigt, der **Code-Editor**.

4.  In der **Code-Editor**, suchen Sie den ersten `TODO:` Kommentar, und Ersetzen Sie den Code durch Folgendes:

     [!code-vb[WCFDataServiceWalkthrough#1](../data-tools/codesnippet/VisualBasic/walkthrough-creating-a-wcf-data-service-with-wpf-and-entity-framework_1.vb)]
     [!code-csharp[WCFDataServiceWalkthrough#1](../data-tools/codesnippet/CSharp/walkthrough-creating-a-wcf-data-service-with-wpf-and-entity-framework_1.cs)]

5.  Ersetzen Sie die Kommentare im `InitializeService`-Ereignishandler durch folgenden Code:

     [!code-vb[WCFDataServiceWalkthrough#2](../data-tools/codesnippet/VisualBasic/walkthrough-creating-a-wcf-data-service-with-wpf-and-entity-framework_2.vb)]
     [!code-csharp[WCFDataServiceWalkthrough#2](../data-tools/codesnippet/CSharp/walkthrough-creating-a-wcf-data-service-with-wpf-and-entity-framework_2.cs)]

6.  Wählen Sie auf der Menüleiste **Debuggen** > **Starten ohne Debugging** zum Ausführen des Diensts. Ein Browserfenster wird geöffnet und zeigt das XML-Schema für den Dienst an.

7.  In der **Adresse** geben `Customers` am Ende der URL für **NorthwindCustomers.svc**, und wählen Sie dann die **EINGABETASTE** Schlüssel.

     Eine XML-Darstellung der Daten in die `Customers` Tabelle angezeigt wird.

    > [!NOTE]
    >  In einigen Fällen interpretiert Internet Explorer die Daten fälschlicherweise als RSS-Feed. Sie müssen sicherstellen, dass die Option zum Anzeigen von RSS-Feeds deaktiviert ist. Weitere Informationen finden Sie unter [Problembehandlung bei Dienstverweisen](../data-tools/troubleshooting-service-references.md).

8.  Schließen Sie das Browserfenster.

In den nächsten Schritten erstellen Sie eine Windows Forms-Clientanwendung für den Dienst zu nutzen.

## <a name="creating-the-client-application"></a>Erstellen der Clientanwendung
 Um die Client-Anwendung zu erstellen, fügen Sie ein zweites Projekt hinzu, Hinzufügen eines Dienstverweises zum Projekt, konfigurieren eine Datenquelle, und erstellen eine Benutzeroberfläche zum Anzeigen der Daten aus dem Dienst.

 Im ersten Schritt müssen Sie ein Windows Forms-Projekt zur Projektmappe hinzufügen und es als Startprojekt festlegen.

#### <a name="to-create-the-client-application"></a>So erstellen Sie die Clientanwendung

1.  Wählen Sie auf der Menüleiste Datei **hinzufügen** > **neues Projekt**.

2.  In der **neues Projekt** Dialogfeld erweitern Sie die **Visual Basic** oder **Visual C#-** Knoten, wählen Sie die **Windows** Knoten und wählen Sie dann auf  **Windows Forms-Anwendung**.

3.  Geben Sie im Textfeld **Name** `NorthwindClient` ein, und wählen Sie dann die Schaltfläche **OK** aus.

4.  In **Projektmappen-Explorer**, wählen Sie die **NorthwindClient** Projektknoten.

5.  Wählen Sie auf der Menüleiste **Projekt**, **als Startprojekt festlegen**.

Im nächsten Schritt fügen Sie einen Dienstverweis auf die [!INCLUDE[ss_data_service](../data-tools/includes/ss_data_service_md.md)] im Webprojekt hinzu.

#### <a name="to-add-a-service-reference"></a>So fügen Sie einen Dienstverweis hinzu

1.  Wählen Sie auf der Menüleiste **Projekt** > **Hinzufügen eines Dienstverweises**.

2.  In der **Hinzufügen eines Dienstverweises** Dialogfeld auf die **Discover** Schaltfläche.

     Die URL für den NorthwindCustomers-Dienst wird angezeigt, der **Adresse** Feld.

3.  Wählen Sie die **OK** , um den Dienstverweis hinzuzufügen.

Im nächsten Schritt konfigurieren Sie eine Datenquelle zum Binden von Daten an den Dienst zu aktivieren.

#### <a name="to-enable-data-binding-to-the-service"></a>So aktivieren Sie die Datenbindung zum Dienst

1.  Wählen Sie auf der Menüleiste **Ansicht** > **Other Windows** > **Datenquellen**.

2.  In der **Datenquellen** Fenster, wählen Sie die **neue Datenquelle hinzufügen** Schaltfläche.

3.  Auf der **wählen Sie einen Datenquellentyp** auf der Seite die **Assistenten zur Datenquellenkonfiguration**, wählen Sie **Objekt**, und wählen Sie dann die **Weiter** Schaltfläche .

4.  Auf der **Datenobjekte auswählen** Seite, erweitern Sie die **NorthwindClient** Knoten, und erweitern Sie dann die **Servicereference1** Knoten.

5.  Wählen Sie **Kunden** aus, und wählen Sie dann die **Fertig stellen** Schaltfläche.

Im nächsten Schritt erstellen Sie die Benutzeroberfläche, in dem die Daten des Diensts angezeigt.

#### <a name="to-create-the-user-interface"></a>So erstellen Sie die Benutzeroberfläche

1.  In der **Datenquellen** Fenster öffnen Sie das Kontextmenü für die **Kunden** Knoten, und wählen Sie **Kopie**.

2.  In der **Form1.vb** oder **"Form1.cs"** Formular-Designer, öffnen Sie im Kontextmenü den Befehl aus, und wählen Sie **einfügen**.

     Ein <xref:System.Windows.Forms.DataGridView>-Steuerelement, eine <xref:System.Windows.Forms.BindingSource>-Komponente und eine <xref:System.Windows.Forms.BindingNavigator>-Komponente werden dem Formular hinzugefügt.

3.  Wählen Sie die **CustomersDataGridView** -Steuerelement, und klicken Sie dann im der **Eigenschaften** legen die **Dock** Eigenschaft, um **füllen**.

4.  In **Projektmappen-Explorer**, öffnen Sie das Kontextmenü für die **Form1** Knoten, und wählen Sie **Ansichtscode** , öffnen Sie den Code-Editor, und fügen Sie die folgenden `Imports` oder `Using`-Anweisung am Anfang der Datei:

    ```vb
    Imports NorthwindClient.ServiceReference1
    ```

    ```csharp
    using NorthwindClient.ServiceReference1;
    ```

5.  Fügen Sie dem `Form1_Load`-Ereignishandler folgenden Code hinzu:

    ```vb
    Private Sub Form1_Load(sender As Object, e As EventArgs) Handles MyBase.Load
            Dim proxy As New NorthwindEntities _
    (New Uri("http://localhost:53161/NorthwindCustomers.svc/"))
            Me.CustomersBindingSource.DataSource = proxy.Customers
        End Sub
    ```

    ```csharp
    private void Form1_Load(object sender, EventArgs e)
    {
    NorthwindEntities proxy = new NorthwindEntities(new Uri("http://localhost:53161/NorthwindCustomers.svc/"));
    this.CustomersBindingSource.DataSource = proxy.Customers;
    }

    ```

6.  In **Projektmappen-Explorer**, öffnen Sie das Kontextmenü für die **NorthwindCustomers.svc** Datei, und wählen **in Browser anzeigen**. Internet Explorer wird geöffnet und zeigt das XML-Schema für den Dienst.

7.  Kopieren Sie die URL aus der Adressleiste von Internet Explorer.

8.  Markieren Sie in dem in Schritt 4 hinzugefügten Code den Text `http://localhost:53161/NorthwindCustomers.svc/`, und ersetzen Sie diesen durch die soeben kopierte URL.

9. Wählen Sie auf der Menüleiste **Debuggen** > **Debuggen starten** zum Ausführen der Anwendung. Die Kundeninformationen wird angezeigt.

 Sie verfügen nun über eine funktionierende Anwendung, die eine Liste der Kunden aus dem NorthwindCustomers-Dienst anzeigt. Wenn Sie weitere Daten über den Dienst bereitstellen möchten, können Sie das [!INCLUDE[adonet_edm](../data-tools/includes/adonet_edm_md.md)] so bearbeiten, dass zusätzliche Tabellen aus der Northwind-Datenbank eingebunden werden.

In den nächsten optionalen Schritt erfahren Sie, wie die Daten zu filtern, die vom Dienst zurückgegeben wird.

## <a name="adding-filtering-capabilities"></a>Hinzufügen von Filterfunktionen
 In diesem Schritt passen Sie die Anwendung aus, um die Daten nach dem Wohnort des Kunden zu filtern.

#### <a name="to-add-filtering-by-city"></a>So fügen Sie Filterung anhand des Wohnorts hinzu

1.  In **Projektmappen-Explorer**, öffnen Sie das Kontextmenü für die **Form1.vb** oder **"Form1.cs"** Knoten, und wählen Sie **öffnen**.

2.  Hinzufügen einer <xref:System.Windows.Forms.TextBox> Steuerelement und ein <xref:System.Windows.Forms.Button> -Steuerelement aus der **Toolbox** auf das Formular.

3.  Öffnen Sie das Kontextmenü für die <xref:System.Windows.Forms.Button> steuern, wählen Sie **Anzeigecode**, und fügen Sie den folgenden Code in die `Button1_Click` -Ereignishandler:

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

    ```csharp
    private void Button1_Click(object sender, EventArgs e)
    {
    ServiceReference1.northwindModel.northwindEntities proxy = new northwindEntities(new Uri("http://localhost:53161/NorthwindCustomers.svc"));
    string city = TextBox1.Text;

    if (!string.IsNullOrEmpty(city)) {
    this.CustomersBindingSource.DataSource = from c in proxy.Customers where c.City == city;
    }

    }
    ```

4.  Ersetzen Sie im vorherigen Code den Text `http://localhost:53161/NorthwindCustomers.svc` durch die URL aus dem `Form1_Load`-Ereignishandler.

5.  Wählen Sie auf der Menüleiste **Debuggen** > **Debuggen starten** zum Ausführen der Anwendung.

6.  Geben Sie in das Textfeld ein **London**, und klicken Sie dann auf die Schaltfläche. Nur die Kunden aus London werden angezeigt.

## <a name="see-also"></a>Siehe auch

- [Windows Communication Foundation-Dienste und WCF Data Services in Visual Studio](../data-tools/windows-communication-foundation-services-and-wcf-data-services-in-visual-studio.md)
- [Gewusst wie: hinzufügen, aktualisieren oder Entfernen eines Verweises WCF Data Service](../data-tools/how-to-add-update-or-remove-a-wcf-data-service-reference.md)