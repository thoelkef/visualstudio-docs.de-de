---
title: 'Exemplarische Vorgehensweise: Erstellen eines WCF-Datendiensts mit WPF und Entity Framework'
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
manager: jillfra
ms.prod: visual-studio-dev15
ms.workload:
- data-storage
ms.openlocfilehash: 7c69b032e01d98030f75273b4ca48714530ddf38
ms.sourcegitcommit: 2193323efc608118e0ce6f6b2ff532f158245d56
ms.translationtype: MTE95
ms.contentlocale: de-DE
ms.lasthandoff: 01/25/2019
ms.locfileid: "54935163"
---
# <a name="walkthrough-creating-a-wcf-data-service-with-wpf-and-entity-framework"></a>Exemplarische Vorgehensweise: Erstellen eines WCF-Datendiensts mit WPF und Entity Framework
In dieser exemplarischen Vorgehensweise wird dargestellt, wie ein einfacher [!INCLUDE[ss_data_service](../data-tools/includes/ss_data_service_md.md)] erstellt wird, der in einer [!INCLUDE[vstecasp](../code-quality/includes/vstecasp_md.md)]-Webanwendung gehostet wird, und wie dann von einer Windows Forms-Anwendung aus darauf zugegriffen wird.

In dieser exemplarischen Vorgehensweise Sie:

- Eine Webanwendung erstellen, um einen [!INCLUDE[ss_data_service](../data-tools/includes/ss_data_service_md.md)] zu hosten.

- Erstellen Sie eine [!INCLUDE[adonet_edm](../data-tools/includes/adonet_edm_md.md)] darstellt, die die `Customers` Tabelle in der Northwind-Datenbank.

- Erstellen Sie eine [!INCLUDE[ss_data_service](../data-tools/includes/ss_data_service_md.md)].

- Eine Clientanwendung erstellen und dieser einen Verweis auf den [!INCLUDE[ss_data_service](../data-tools/includes/ss_data_service_md.md)] hinzufügen.

- Die Datenbindung zum Dienst aktivieren und die Benutzeroberfläche erstellen.

- Optional Filterfunktionen zur Anwendung hinzufügen.

## <a name="prerequisites"></a>Erforderliche Komponenten
In dieser exemplarischen Vorgehensweise verwendet SQL Server Express LocalDB und der Beispieldatenbank Northwind.

1. Wenn Sie SQL Server Express LocalDB nicht haben, installieren Sie es entweder über die [Downloadseite für SQL Server Express](https://www.microsoft.com/sql-server/sql-server-editions-express), oder über die **Visual Studio-Installer**. In der **Visual Studio-Installer**, können Sie SQL Server Express LocalDB installieren, als Teil der **datenspeicherung und-Verarbeitung** Workload oder als eine einzelne Komponente.

2. Installieren der Northwind-Beispieldatenbank mit folgenden Schritten:

    1. Öffnen Sie in Visual Studio die **Objekt-Explorer von SQL Server** Fenster. (**Objekt-Explorer von SQL Server** installiert ist, als Teil der **datenspeicherung und-Verarbeitung** Workload im Visual Studio-Installer.) Erweitern Sie die **SQL Server** Knoten. Mit der rechten Maustaste auf der LocalDB-Instanz, und wählen Sie **neue Abfrage**.

       Ein Abfrage-Editor-Fenster wird geöffnet.

    2. Kopieren der [Northwind Transact-SQL-Skript](https://github.com/MicrosoftDocs/visualstudio-docs/blob/master/docs/data-tools/samples/northwind.sql?raw=true) in die Zwischenablage. Dieses T-SQL-Skript wird die Northwind-Datenbank von Grund auf neu erstellt und mit Daten aufgefüllt.

    3. Fügen Sie das T-SQL-Skript im Abfrage-Editor, und wählen Sie dann die **Execute** Schaltfläche.

       Klicken Sie nach kurzer Zeit die Ausführung die Abfrage abgeschlossen ist, und die Northwind-Datenbank wird erstellt.

## <a name="creating-the-service"></a>Erstellen des Diensts
Um einen [!INCLUDE[ss_data_service](../data-tools/includes/ss_data_service_md.md)] zu erstellen, fügen Sie ein Webprojekt hinzu. Dann erstellen Sie ein [!INCLUDE[adonet_edm](../data-tools/includes/adonet_edm_md.md)] und anschließend den Dienst aus dem Modell.

Im ersten Schritt fügen Sie ein Webprojekt zum Hosten des Diensts hinzu.

[!INCLUDE[note_settings_general](../data-tools/includes/note_settings_general_md.md)]

### <a name="to-create-the-web-project"></a>So erstellen Sie das Webprojekt

1. Klicken Sie in der Menüleiste auf **Datei** > **Neu** > **Projekt**.

2. Erweitern Sie im Dialogfeld **Neues Projekt** die Knoten **Visual Basic** oder **Visual C#** sowie **Web**, und wählen Sie dann die Vorlage **ASP.NET-Webanwendung** aus.

3. Geben Sie **NorthwindWeb** im Textfeld **Name** ein, und wählen Sie dann die Schaltfläche **OK**.

4. Wählen Sie im Dialogfeld **Neues ASP.NET-Projekt** aus der Liste **Vorlage auswählen** die Option **Leer**, und klicken Sie dann auf die Schaltfläche **OK**.

In den nächsten Schritt erstellen Sie eine [!INCLUDE[adonet_edm](../data-tools/includes/adonet_edm_md.md)] darstellt, die die `Customers` Tabelle in der Northwind-Datenbank.

### <a name="to-create-the-entity-data-model"></a>So erstellen Sie das Entity Data Model

1. Wählen Sie in der Menüleiste **Projekt** > **Neues Element hinzufügen** aus.

2. Wählen Sie im Dialogfeld **Neues Element hinzufügen** den Knoten **Daten** und anschließend das Element **ADO.NET Entity Data Model** aus.

3. In der **Namen** Text geben `NorthwindModel`, und wählen Sie dann die **hinzufügen** Schaltfläche.

     Der Assistent für Entity Data Model wird angezeigt.

4. Wählen Sie im Entity Data Model-Assistenten auf der Seite **Modellinhalte auswählen** das Element **EF-Designer aus Datenbank** aus, und klicken Sie dann auf **Weiter**.

5. Führen Sie auf der Seite **Wählen Sie Ihre Datenverbindung aus** einen der folgenden Schritte aus:

    -   Wenn eine Datenverbindung mit der Beispieldatenbank Northwind in der Dropdownliste verfügbar ist, wählen Sie sie aus.

         - oder -

    -   Wählen Sie die Schaltfläche **Neue Verbindung**, um eine neue Datenverbindung zu konfigurieren. Weitere Informationen finden Sie unter [neue Verbindungen hinzufügen](../data-tools/add-new-connections.md).

6. Wenn für die Datenbank ein Kennwort erforderlich ist, klicken Sie auf das Optionsfeld **Ja, vertrauliche Daten in die Verbindungszeichenfolge einschließen** und dann auf die Schaltfläche **Weiter**.

    > [!NOTE]
    > Wenn ein Dialogfeld angezeigt wird, klicken Sie auf **Ja**, um die Datei im Projekt zu speichern.

7. Wählen Sie auf der Seite **Wählen Sie Ihre Version** das Optionsfeld **Entity Framework 5.0** aus, und klicken Sie dann auf die Schaltfläche **Weiter**.

    > [!NOTE]
    > Um die aktuelle Version vom Entity Framework 6 mit WCF-Diensten zu verwenden, müssen Sie das WCF Data Services Entity Framework Provider NuGet-Paket installieren. Finden Sie unter [Verwenden von WCF Data Services 5.6.0 mit Entitätsframework 6 +](https://blogs.msdn.microsoft.com/odatateam/2013/10/02/using-wcf-data-services-5-6-0-with-entity-framework-6/).

8. Erweitern Sie auf der Seite **Datenbankobjekte auswählen** den Knoten **Tabellen**, aktivieren Sie das Kontrollkästchen **Customers**, und wählen Sie dann die Schaltfläche **Fertig stellen**.

     Das Entitätsmodelldiagramm wird angezeigt, und ein *NorthwindModel.edmx* Datei wird dem Projekt hinzugefügt.

In den nächsten Schritt erstellen und Testen Sie den Datendienst.

### <a name="to-create-the-data-service"></a>So erstellen Sie den Datendienst

1. Wählen Sie in der Menüleiste **Projekt** > **Neues Element hinzufügen** aus.

2. Wählen Sie im Dialogfeld **Neues Element hinzufügen** den Knoten **Web** und anschließend das Element **WCF Data Service 5.6**.

3. In der **Namen** Text geben `NorthwindCustomers`, und wählen Sie dann die **hinzufügen** Schaltfläche.

     Die Datei **NorthwindCustomers.svc** wird im **Code-Editor** angezeigt.

4. Suchen Sie im **Code-Editor`TODO:` den ersten** -Kommentar, und ersetzen Sie den Code durch Folgendes:

     [!code-vb[WCFDataServiceWalkthrough#1](../data-tools/codesnippet/VisualBasic/walkthrough-creating-a-wcf-data-service-with-wpf-and-entity-framework_1.vb)]
     [!code-csharp[WCFDataServiceWalkthrough#1](../data-tools/codesnippet/CSharp/walkthrough-creating-a-wcf-data-service-with-wpf-and-entity-framework_1.cs)]

5. Ersetzen Sie die Kommentare im `InitializeService`-Ereignishandler durch folgenden Code:

     [!code-vb[WCFDataServiceWalkthrough#2](../data-tools/codesnippet/VisualBasic/walkthrough-creating-a-wcf-data-service-with-wpf-and-entity-framework_2.vb)]
     [!code-csharp[WCFDataServiceWalkthrough#2](../data-tools/codesnippet/CSharp/walkthrough-creating-a-wcf-data-service-with-wpf-and-entity-framework_2.cs)]

6. Wählen Sie auf der Menüleiste **Debuggen** > **Starten ohne Debugging** zum Ausführen des Diensts. Ein Browserfenster wird geöffnet und zeigt das XML-Schema für den Dienst an.

7. In der **Adresse** geben `Customers` am Ende der URL für **NorthwindCustomers.svc**, und wählen Sie dann die **EINGABETASTE** Schlüssel.

     Eine XML-Darstellung der Daten in die `Customers` Tabelle angezeigt wird.

    > [!NOTE]
    > In einigen Fällen interpretiert Internet Explorer die Daten fälschlicherweise als RSS-Feed. Sie müssen sicherstellen, dass die Option zum Anzeigen von RSS-Feeds deaktiviert ist. Weitere Informationen finden Sie unter [Troubleshooting service references (Problembehandlung bei Dienstverweisen)](../data-tools/troubleshooting-service-references.md).

8. Schließen Sie das Browserfenster.

In den nächsten Schritten erstellen Sie eine Windows Forms-Clientanwendung für den Dienst zu nutzen.

## <a name="creating-the-client-application"></a>Erstellen der Clientanwendung
 Zum Erstellen der Clientanwendung fügen Sie ein zweites Projekt hinzu, dem Sie einen Dienstverweis hinzufügen. Daraufhin konfigurieren Sie eine Datenquelle und erstellen eine Benutzeroberfläche zum Anzeigen der Daten des Diensts.

 Im ersten Schritt müssen Sie ein Windows Forms-Projekt zur Projektmappe hinzufügen und es als Startprojekt festlegen.

### <a name="to-create-the-client-application"></a>So erstellen Sie die Clientanwendung

1. Wählen Sie auf der Menüleiste Datei **hinzufügen** > **neues Projekt**.

2. In der **neues Projekt** Dialogfeld erweitern Sie die **Visual Basic** oder **Visual C#**  Knoten, wählen Sie die **Windows** Knoten, und wählen Sie dann **Windows Forms-Anwendung**.

3. Geben Sie im Textfeld **Name** `NorthwindClient` ein, und wählen Sie dann die Schaltfläche **OK** aus.

4. Wählen Sie im **Projektmappen-Explorer** den **NorthwindClient**-Projektknoten.

5. Wählen Sie in der Menüleiste **Projekt**, **Als Startprojekt festlegen** aus.

Im nächsten Schritt fügen Sie einen Dienstverweis auf die [!INCLUDE[ss_data_service](../data-tools/includes/ss_data_service_md.md)] im Webprojekt hinzu.

### <a name="to-add-a-service-reference"></a>So fügen Sie einen Dienstverweis hinzu

1. Wählen Sie auf der Menüleiste **Projekt** > **Hinzufügen eines Dienstverweises**.

2. Wählen Sie im Dialogfeld **Dienstverweis hinzufügen** die Schaltfläche **Ermitteln** aus.

     Die URL für den NorthwindCustomers-Dienst wird im Feld **Adresse** angezeigt.

3. Klicken Sie auf die Schaltfläche **OK**, um den Dienstverweis hinzuzufügen.

Im nächsten Schritt konfigurieren Sie eine Datenquelle zum Binden von Daten an den Dienst zu aktivieren.

### <a name="to-enable-data-binding-to-the-service"></a>So aktivieren Sie die Datenbindung zum Dienst

1. Wählen Sie auf der Menüleiste **Ansicht** > **Other Windows** > **Datenquellen**.

   Das Fenster **Datenquellen** wird geöffnet.

2. Wählen Sie im Fenster **Datenquellen** die Schaltfläche **Neue Datenquelle hinzufügen**.

3. Wählen Sie auf der Seite **Datenquellentyp auswählen** unter **Assistent zum Konfigurieren von Datenquellen** den Typ **Objekt** und dann die Schaltfläche **Weiter**.

4. Erweitern Sie auf der Seite **Datenobjekte auswählen** den Knoten **NorthwindClient**, und erweitern Sie dann den Knoten **NorthwindClient.ServiceReference1**.

5. Aktivieren Sie das Kontrollkästchen **Customer**, und wählen Sie dann **Fertig stellen**.

Im nächsten Schritt erstellen Sie die Benutzeroberfläche, in dem die Daten des Diensts angezeigt.

### <a name="to-create-the-user-interface"></a>So erstellen Sie die Benutzeroberfläche

1. Im Fenster **Datenquellen** öffnen Sie das Kontextmenü für den Knoten **Customers** und wählen **Kopieren** aus.

2. Öffnen Sie im Formular-Designer **Form1.vb** oder **Form1.cs** das Kontextmenü, und wählen Sie **Einfügen** aus.

    Ein <xref:System.Windows.Forms.DataGridView>-Steuerelement, eine <xref:System.Windows.Forms.BindingSource>-Komponente und eine <xref:System.Windows.Forms.BindingNavigator>-Komponente werden dem Formular hinzugefügt.

3. Wählen Sie das **CustomersDataGridView**-Steuerelement aus, und legen Sie dann im Fenster **Eigenschaften** die Eigenschaft **Andocken** auf **Füllbereich** fest.

4. In **Projektmappen-Explorer**, öffnen Sie das Kontextmenü für die **Form1** Knoten, und wählen Sie **Ansichtscode** , öffnen Sie den Code-Editor, und fügen Sie die folgenden `Imports` oder `Using`-Anweisung am Anfang der Datei:

   ```vb
   Imports NorthwindClient.ServiceReference1
   ```

   ```csharp
   using NorthwindClient.ServiceReference1;
   ```

5. Fügen Sie dem `Form1_Load` -Ereignishandler folgenden Code hinzu:

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

6. Öffnen Sie im **Projektmappen-Explorer** das Kontextmenü für die **NorthwindCustomers.svc**-Datei, und wählen Sie **In Browser anzeigen** aus. Internet Explorer wird geöffnet und zeigt das XML-Schema für den Dienst.

7. Kopieren Sie die URL aus der Adressleiste von Internet Explorer.

8. Markieren Sie in dem in Schritt 4 hinzugefügten Code den Text `http://localhost:53161/NorthwindCustomers.svc/`, und ersetzen Sie diesen durch die soeben kopierte URL.

9. Wählen Sie auf der Menüleiste **Debuggen** > **Debuggen starten** zum Ausführen der Anwendung. Die Kundeninformationen wird angezeigt.

   Sie verfügen nun über eine funktionierende Anwendung, die eine Liste der Kunden aus dem NorthwindCustomers-Dienst anzeigt. Wenn Sie weitere Daten über den Dienst bereitstellen möchten, können Sie das [!INCLUDE[adonet_edm](../data-tools/includes/adonet_edm_md.md)] so bearbeiten, dass zusätzliche Tabellen aus der Northwind-Datenbank eingebunden werden.

In den nächsten optionalen Schritt erfahren Sie, wie die Daten zu filtern, die vom Dienst zurückgegeben wird.

## <a name="adding-filtering-capabilities"></a>Hinzufügen von Filterfunktionen
 In diesem Schritt passen Sie die Anwendung aus, um die Daten nach dem Wohnort des Kunden zu filtern.

### <a name="to-add-filtering-by-city"></a>So fügen Sie Filterung anhand des Wohnorts hinzu

1. Öffnen Sie im **Projektmappen-Explorer** das Kontextmenü für den Knoten **Form1.vb** oder **Form1.cs**, und wählen Sie dann **Öffnen** aus.

2. Fügen Sie dem Formular ein <xref:System.Windows.Forms.TextBox>- und ein <xref:System.Windows.Forms.Button>-Steuerelement aus der **Toolbox** hinzu.

3. Öffnen Sie das Kontextmenü für die <xref:System.Windows.Forms.Button> steuern, wählen Sie **Anzeigecode**, und fügen Sie den folgenden Code in die `Button1_Click` -Ereignishandler:

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

4. Ersetzen Sie im vorherigen Code den Text `http://localhost:53161/NorthwindCustomers.svc` durch die URL aus dem `Form1_Load`-Ereignishandler.

5. Wählen Sie auf der Menüleiste **Debuggen** > **Debuggen starten** zum Ausführen der Anwendung.

6. Geben Sie im Textfeld die Zeichenfolge **London** ein, und klicken Sie dann auf die Schaltfläche. Nur die Kunden aus London werden angezeigt.

## <a name="see-also"></a>Siehe auch

- [Windows Communication Foundation-Dienste und WCF Data Services in Visual Studio](../data-tools/windows-communication-foundation-services-and-wcf-data-services-in-visual-studio.md)
- [Vorgehensweise: Hinzufügen, Aktualisieren oder Entfernen eines WCF-Datendienstverweises](../data-tools/how-to-add-update-or-remove-a-wcf-data-service-reference.md)