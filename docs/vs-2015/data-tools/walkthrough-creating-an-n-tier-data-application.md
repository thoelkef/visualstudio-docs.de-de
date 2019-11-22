---
title: 'Walkthrough: Creating an N-Tier Data Application | Microsoft Docs'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-data-tools
ms.topic: conceptual
dev_langs:
- VB
- CSharp
- C++
- aspx
helpviewer_keywords:
- n-tier applications, creating
- n-tier applications, walkthroughs
ms.assetid: d15e4d31-2839-48d9-9e0e-2e73404d82a2
caps.latest.revision: 51
author: jillre
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: bd77006eda03b716e3c54c0b5b52ac633a383377
ms.sourcegitcommit: bad28e99214cf62cfbd1222e8cb5ded1997d7ff0
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 11/21/2019
ms.locfileid: "74299586"
---
# <a name="walkthrough-creating-an-n-tier-data-application"></a>Exemplarische Vorgehensweise: Erstellen einer N-Tier-Datenanwendung
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

N-tier* data applications are applications that access data and are separated into multiple logical layers, or *tiers*. Die Aufteilung der Anwendungskomponenten in verschiedene Ebenen erhöht die Verwaltbarkeit und die Skalierbarkeit der Anwendung. Auf diese Weise wird das Einarbeiten neuer, eine einzelne Ebene betreffender Technologien vereinfacht, ein erneutes Entwerfen der Anwendung ist nicht notwendig. Zur N-Tier-Architektur gehören eine Präsentationsebene, eine mittlere Ebene und eine Datenebene. Die mittlere Ebene enthält eine Datenzugriffsschicht, eine Geschäftslogikschicht und gemeinsame Komponenten, wie beispielsweise Authentifizierung und Validierung. Die Datenschicht enthält eine relationale Datenbank. N-Tier-Anwendungen speichern vertrauliche Informationen in der Datenzugriffsschicht der mittleren Ebene, um diese von Endbenutzern, die auf die Präsentationsebene zugreifen, getrennt zu halten. For more information, see [N-Tier Data Applications Overview](../data-tools/n-tier-data-applications-overview.md).

 Eine Möglichkeit zum Trennen der verschiedenen Ebenen einer N-Tier-Anwendung besteht im Erstellen separater Projekte für jede Ebene, die in der Anwendung enthalten sein soll. Typisierte DataSets enthalten eine `DataSet Project`-Eigenschaft, mit der festgelegt wird, in welche Projekte der erzeugte DataSet-Code und der erzeugte `TableAdapter`-Code eingefügt werden.

 In dieser exemplarischen Vorgehensweise wird dargestellt, wie DataSet- und `TableAdapter`-Code mithilfe des **DataSet-Designers** in einzelne Klassenbibliotheksprojekte aufgeteilt werden. After you separate the dataset and TableAdapter code, you will create a [Windows Communication Foundation Services and WCF Data Services in Visual Studio](../data-tools/windows-communication-foundation-services-and-wcf-data-services-in-visual-studio.md) service to call into the data access tier. Abschließend wird eine Windows Forms-Anwendung als Präsentationsebene erstellt. Diese Ebene greift auf Daten des Datendiensts zu.

 Im Verlauf dieser exemplarischen Vorgehensweise führen Sie folgende Schritte aus:

- Erstellen einer neuen N-Tier-Projektmappe, die mehrere Projekte enthält.

- Hinzufügen von zwei Klassenbibliotheksprojekten zur N-Tier-Projektmappe.

- Erstellen eines typisierten DataSets mithilfe des **Assistenten zum Konfigurieren von Datenquellen**.

- Separate the generated [TableAdapters](https://msdn.microsoft.com/library/09416de9-134c-4dc7-8262-6c8d81e3f364) and dataset code into discrete projects.

- Erstellen eines WCF (Windows Communication Foundation)-Diensts für Aufrufe an die Datenzugriffsebene.

- Erstellen von Dienstfunktionen, um Daten von der Datenzugriffsebene abzurufen.

- Erstellen einer Windows Forms-Anwendung, die als Präsentationsebene dient.

- Erstellen von Windows Forms-Steuerelementen, die an die Datenquelle gebunden werden.

- Schreiben von Code zum Füllen der Datentabellen.

  ![link to video](../data-tools/media/playvideo.gif "PlayVideo") For a video version of this topic, see [Video How to: Creating an N-Tier Data Application](https://go.microsoft.com/fwlink/?LinkId=115188).

## <a name="prerequisites"></a>Erforderliche Voraussetzungen
 Um diese exemplarische Vorgehensweise nachzuvollziehen, benötigen Sie Folgendes:

- Zugriff auf die Beispieldatenbank Northwind.

## <a name="creating-the-n-tier-solution-and-class-library-to-hold-the-dataset-dataentitytier"></a>Erstellen der N-Tier-Projektmappe der Klassenbibliothek für das DataSet (DataEntityTier)
 Im ersten Schritt dieser exemplarischen Vorgehensweise werden eine Projektmappe und zwei Klassenbibliotheksprojekte erstellt. Die erste Klassenbibliothek enthält das DataSet (die generierte typisierte DataSet-Klasse und die DataTables für die Anwendungsdaten). Dieses Projekt wird als Datenentitätsschicht der Anwendung verwendet und befindet sich normalerweise in der mittleren Ebene. The Dataset Designer is used to create the initial dataset and automatically separate the code into the two class libraries.

> [!NOTE]
> Stellen Sie sicher, dass Projekt und Projektmappe ordnungsgemäß benannt wurden, bevor Sie auf **OK** klicken. Das erleichtert die Durchführung der exemplarischen Vorgehensweise.

#### <a name="to-create-the-n-tier-solution-and-dataentitytier-class-library"></a>So erstellen Sie die N-Tier-Projektmappe und die DataEntityTier-Klassenbibliothek

1. From the **File** menu, create a new project.

    > [!NOTE]
    > The **Dataset Designer** is supported in [!INCLUDE[vbprvb](../includes/vbprvb-md.md)] and C# projects. Erstellen Sie das neue Projekt in einer der beiden Sprachen.

2. In the **New Project** dialog box, in the **Project types** pane, click **Windows**.

3. Click the **Class Library** template.

4. Nennen Sie das Projekt **DataEntityTier**.

5. Name the solution **NTierWalkthrough**.

6. Klicken Sie auf **OK**.

     Eine Projektmappe NTierWalkthrough mit dem Projekt DataEntityTier wird erstellt und zum **Projektmappen-Explorer** hinzugefügt.

## <a name="creating-the-class-library-to-hold-the-tableadapters-dataaccesstier"></a>Erstellen der Klassenbibliothek für die TableAdapter (DataAccessTier)
 Nach dem Erstellen des Projekts DataEntityTier besteht der nächste Schritt darin, ein zweites Klassenbibliotheksprojekt zu erstellen. This project will hold the generated `TableAdapter`s and is called the *data access tier* of the application. Die Datenzugriffsebene enthält die zum Herstellen einer Verbindung mit der Datenbank notwendigen Informationen und befindet sich normalerweise in der mittleren Ebene.

#### <a name="to-create-the-new-class-library-for-the-tableadapters"></a>So erstellen Sie die neue Klassenbibliothek für die TableAdapter

1. From the **File** menu, add a new project to the NTierWalkthrough solution.

2. In the **New Project** dialog box, in the **Templates** pane, click **Class Library**.

3. Name the project **DataAccessTier** and click **OK**.

     Das Projekt DataAccessTier wird erstellt und zur Projektmappe NTierWalkthrough hinzugefügt.

## <a name="creating-the-dataset"></a>Erstellen des DataSets
 Der nächste Schritt besteht darin, ein typisiertes DataSet zu erstellen. Typisierte DataSets werden mit beiden DataSet-Klassen (einschließlich der DataTables-Klassen) und der `TableAdapter`-Klassen in einem einzelnen Projekt erstellt. (All classes are generated into a single file.) When you separate the dataset and `TableAdapter`s into different projects, it is the dataset class that is moved to the other project, leaving the `TableAdapter` classes in the original project. Erstellen Sie daher das DataSet in dem Projekt, das letztendlich die `TableAdapter` (das Projekt DataAccessTier) enthalten wird. You will create the dataset by using the **Data Source Configuration Wizard**.

> [!NOTE]
> Sie benötigen Zugriff auf die Beispieldatenbank Northwind, um die Verbindung herstellen zu können.

#### <a name="to-create-the-dataset"></a>So erstellen Sie das DataSet

1. Click DataAccessTier in **Solution Explorer**.

2. Klicken Sie im Menü **Daten** auf **Datenquellen anzeigen**.

3. In the **Data Sources** window, click **Add New Data Source** to start the **Data Source Configuration Wizard**.

4. On the **Choose a Data Source Type** page, click **Database** and then click **Next**.

5. Führen Sie auf der Seite **Wählen Sie Ihre Datenverbindung** eine der folgenden Aktionen aus:

     Wenn in der Dropdownliste eine Datenverbindung zur Beispieldatenbank Northwind verfügbar ist, klicken Sie auf diese.

     - oder -

     Click **New Connection** to open the **Add Connection** dialog box.

6. Sollte für die Datenbank ein Kennwort erforderlich sein, wählen Sie die Option für die Einbeziehung vertraulicher Daten aus, und klicken Sie anschließend auf **Weiter**.

    > [!NOTE]
    > Wenn Sie eine lokale Datenbankdatei ausgewählt haben (statt eine Verbindung mit SQL Server herzustellen), werden Sie möglicherweise gefragt, ob Sie die Datei zum Projekt hinzufügen möchten. Click **Yes** to add the database file to the project.

7. Click **Next** on the **Save the Connection String to the Application Configuration File** page.

8. Erweitern Sie auf der Seite **Datenbankobjekte auswählen** den Knoten **Tabellen** .

9. Click the check boxes for the **Customers** and **Orders** tables, and then click **Finish**.

     Das NorthwindDataSet wird zum DataAccessTier-Projekt hinzugefügt und im Fenster **Datenquellen** angezeigt.

## <a name="separating-the-tableadapters-from-the-dataset"></a>Trennen der TableAdapter vom DataSet
 Nach dem Erstellen des DataSets wird die generierte DataSet-Klasse von den TableAdaptern getrennt. Hierzu müssen Sie die **DataSet-Projekt**-Eigenschaft auf den Namen des Projekts festlegen, in dem die aufgeteilten DataSet-Klassen gespeichert werden sollen.

#### <a name="to-separate-the-tableadapters-from-the-dataset"></a>So trennen Sie die TableAdapter vom DataSet

1. Doppelklicken Sie im **Projektmappen-Explorer** auf **NorthwindDataSet.xsd**, um das DataSet im **DataSet-Designer** zu öffnen.

2. Klicken Sie im Designer auf einen leeren Bereich.

3. Suchen Sie den Knoten **DataSet-Projekt** im Fenster **Eigenschaften**.

4. In the **DataSet Project** list, click **DataEntityTier**.

5. Klicken Sie im Menü **Erstellen** auf **Projektmappe erstellen**.

   DataSet und TableAdapter werden in die zwei Klassenbibliotheksprojekte aufgeteilt. Das Projekt, in dem ursprünglich das gesamte DataSet (DataAccessTier) enthalten war, enthält jetzt nur noch die TableAdapter. The project designated in the **DataSet Project** property (DataEntityTier) contains the typed dataset: NorthwindDataSet.Dataset.Designer.vb (or NorthwindDataSet.Dataset.Designer.cs).

> [!NOTE]
> Bei einer Aufteilung von DataSets und TableAdapters (durch Festlegen der **DataSet-Projekt**-Eigenschaft) werden vorhandene partielle DataSet-Klassen in dem Projekt nicht automatisch verschoben. Vorhandene partielle DataSet-Klassen müssen manuell in das DataSet-Projekt verschoben werden.

## <a name="creating-a-new-service-application"></a>Erstellen einer neuen Dienstanwendung
 Da in dieser exemplarischen Vorgehensweise beschrieben wird, wie mithilfe eines WCF-Diensts auf die Datenzugriffsebene zugegriffen wird, muss eine neue WCF-Dienstanwendung erstellt werden.

#### <a name="to-create-a-new-wcf-service-application"></a>So erstellen Sie eine neue WCF-Dienstanwendung

1. From the **File** menu, add a new project to the NTierWalkthrough solution.

2. In the **New Project** dialog box, in the **Project types** pane, click **WCF**. In the **Templates** pane, click **WCF Service Library**.

3. Name the project **DataService** and click **OK**.

     Das Projekt DataService wird erstellt und zur Projektmappe NTierWalkthrough hinzugefügt.

## <a name="creating-methods-in-the-data-access-tier-to-return-the-customers-and-orders-data"></a>Erstellen von Methoden in der Datenzugriffsebene, um Customers- und Orders-Daten zurückzugeben
 Der Datendienst muss zwei Methoden in der Datenzugriffsebene aufrufen: GetCustomers und GetOrders. Diese Methoden geben die Northwind-Tabellen Customers und Orders zurück. Erstellen Sie im Projekt DataAccessTier die GetCustomers-Methode und die GetOrders-Methode.

#### <a name="to-create-a-method-in-the-data-access-tier-that-returns-the-customers-table"></a>So erstellen Sie eine Methode in der Datenzugriffsebene, die die Tabelle Customers zurückgibt

1. In **Solution Explorer**, double-click NorthwindDataset.xsd to open the dataset in the Dataset Designer.

2. Right-click CustomersTableAdapter and click **Add Query** to edit the Tableadapter.

3. Übernehmen Sie auf der Seite **Wählen Sie einen Befehlstyp aus** den Standardwert **SQL-Anweisungen verwenden**, und klicken Sie auf **Weiter**.

4. Übernehmen Sie auf der Seite **Abfragetyp auswählen** den Standardwert **SELECT-Anweisung, die Zeilen zurückgibt**, und klicken Sie auf **Weiter**.

5. Übernehmen Sie auf der Seite **SQL-SELECT-Anweisung angeben** die Standardabfrage, und klicken Sie auf **Weiter**.

6. Geben Sie auf der Seite **Zu generierende Methode auswählen** für den **Methodennamen** im Abschnitt **DataTable zurückgeben** die Zeichenfolge **GetCustomers** ein.

7. Klicken Sie auf **Fertig stellen**.

#### <a name="to-create-a-method-in-the-data-access-tier-that-returns-the-orders-table"></a>So erstellen Sie eine Methode in der Datenzugriffsebene, die die Tabelle Orders zurückgibt

1. Right-click OrdersTableAdapter and click **Add Query**.

2. Übernehmen Sie auf der Seite **Wählen Sie einen Befehlstyp aus** den Standardwert **SQL-Anweisungen verwenden**, und klicken Sie auf **Weiter**.

3. Übernehmen Sie auf der Seite **Abfragetyp auswählen** den Standardwert **SELECT-Anweisung, die Zeilen zurückgibt**, und klicken Sie auf **Weiter**.

4. Übernehmen Sie auf der Seite **SQL-SELECT-Anweisung angeben** die Standardabfrage, und klicken Sie auf **Weiter**.

5. Geben Sie auf der Seite **Zu generierende Methoden auswählen** für den **Methodennamen** im Abschnitt **DataTable zurückgeben** die Zeichenfolge **GetOrders** ein.

6. Klicken Sie auf **Fertig stellen**.

7. Klicken Sie im Menü **Erstellen** auf **Projektmappe erstellen**.

## <a name="adding-a-reference-to-the-data-entity-and-data-access-tiers-to-the-data-service"></a>Hinzufügen eines Verweises auf die Datenentitätsebene und die Datenzugriffsebene für den Datendienst
 Da der Datendienst Informationen von DataSet und TableAdaptern erfordert, müssen Verweise auf das Projekt DataEntityTier und das Projekt DataAccessTier hinzugefügt werden.

#### <a name="to-add-references-to-the-data-service"></a>So fügen Sie Verweise zum Datendienst hinzu

1. Right-click DataService in **Solution Explorer** and click **Add Reference**.

2. Klicken Sie im Dialogfeld **Verweis hinzufügen** auf die Registerkarte **Projekte**.

3. Wählen Sie sowohl das Projekt **DataAccessTier** als auch das Projekt **DataEntityTier** aus.

4. Klicken Sie auf **OK**.

## <a name="adding-functions-to-the-service-to-call-the-getcustomers-and-getorders-methods-in-the-data-access-tier"></a>Hinzufügen von Funktionen, mit denen der Dienst die GetCustomers-Methode und die GetOrders-Methode in der Datenzugriffsebene aufruft
 Nachdem die Datenzugriffsebene die Methoden zur Rückgabe der Daten enthält, müssen Sie im Datendienst Methoden erstellen, um die Methoden in der Datenzugriffsebene aufzurufen.

> [!NOTE]
> In C#-Projekten muss ein Verweis auf die `System.Data.DataSetExtensions`-Assembly für die Kompilierung des nachfolgenden Codes hinzugefügt werden.

#### <a name="to-create-the-getcustomers-and-getorders-functions-in-the-data-service"></a>So erstellen Sie im Datendienst die GetCustomers-Funktion und die GetOrders-Funktion

1. In the **DataService** project, double-click IService1.vb or IService1.cs.

2. Fügen Sie unter dem Kommentar **Hier Dienstvorgänge hinzufügen** folgenden Code hinzu:

    ```vb
    <OperationContract()> _
    Function GetCustomers() As DataEntityTier.NorthwindDataSet.CustomersDataTable

    <OperationContract()> _
    Function GetOrders() As DataEntityTier.NorthwindDataSet.OrdersDataTable
    ```

    ```csharp
    [OperationContract]
    DataEntityTier.NorthwindDataSet.CustomersDataTable GetCustomers();

    [OperationContract]
    DataEntityTier.NorthwindDataSet.OrdersDataTable GetOrders();

    ```

3. Doppelklicken Sie im Projekt DataService auf IService1.vb (oder IService1.cs).

4. Fügen Sie der Service1-Klasse den folgenden Code hinzu:

    ```vb
    Public Function GetCustomers() As DataEntityTier.NorthwindDataSet.CustomersDataTable Implements IService1.GetCustomers
        Dim CustomersTableAdapter1 As New DataAccessTier.NorthwindDataSetTableAdapters.CustomersTableAdapter
        Return CustomersTableAdapter1.GetCustomers()
    End Function

    Public Function GetOrders() As DataEntityTier.NorthwindDataSet.OrdersDataTable Implements IService1.GetOrders
        Dim OrdersTableAdapter1 As New DataAccessTier.NorthwindDataSetTableAdapters.OrdersTableAdapter
        Return OrdersTableAdapter1.GetOrders()
    End Function
    ```

    ```csharp
    public DataEntityTier.NorthwindDataSet.CustomersDataTable GetCustomers()
    {
        DataAccessTier.NorthwindDataSetTableAdapters.CustomersTableAdapter
             CustomersTableAdapter1
            = new DataAccessTier.NorthwindDataSetTableAdapters.CustomersTableAdapter();
        return CustomersTableAdapter1.GetCustomers();

    }
    public DataEntityTier.NorthwindDataSet.OrdersDataTable GetOrders()
    {
        DataAccessTier.NorthwindDataSetTableAdapters.OrdersTableAdapter
             OrdersTableAdapter1
            = new DataAccessTier.NorthwindDataSetTableAdapters.OrdersTableAdapter();
        return OrdersTableAdapter1.GetOrders();

    }
    ```

5. Klicken Sie im Menü **Erstellen** auf **Projektmappe erstellen**.

## <a name="creating-a-presentation-tier-to-display-data-from-the-data-service"></a>Erstellen einer Präsentationsebene zum Anzeigen von Daten des Datendiensts
 Nachdem die Projektmappe den Datendienst enthält, der über Methoden zum Aufrufen der Datenzugriffsebene verfügt, muss ein weiteres Projekt erstellt werden, das den Datendienst aufruft und den Benutzern die Daten anzeigt. Erstellen Sie für diese exemplarische Vorgehensweise eine Windows Forms-Anwendung als Präsentationsebene der N-Tier-Anwendung.

#### <a name="to-create-the-presentation-tier-project"></a>So erstellen Sie das Präsentationsebenenprojekt

1. From the **File** menu, add a new project to the NTierWalkthrough solution.

2. In the **New Project** dialog box, in the **Project types** pane, click **Windows**. Klicken Sie im Bereich **Vorlagen** auf **Windows Forms-Anwendung**.

3. Nennen Sie das Projekt **PresentationTier**, und klicken Sie auf **OK**.

4. Das Projekt PresentationTier wird erstellt und zur Projektmappe NTierWalkthrough hinzugefügt.

## <a name="setting-the-presentationtier-project-as-the-startup-project"></a>Festlegen des Projekts PresentationTier als Startprojekt
 Da die Präsentationsebene die aktuelle Clientanwendung zum Präsentieren der Daten und zum interaktiven Arbeiten mit den Daten darstellt, muss das Projekt PresentationTier als Startprojekt festgelegt werden.

#### <a name="to-set-the-new-presentation-tier-project-as-the-startup-project"></a>So legen Sie das neue Präsentationsebenenprojekt als Startprojekt fest

- Klicken Sie im **Projektmappen-Explorer** mit der rechten Maustaste auf **PresentationTier**, und klicken Sie anschließend auf **Als Startprojekt festlegen**.

## <a name="adding-references-to-the-presentation-tier"></a>Hinzufügen von Verweisen auf die Präsentationsebene
 Die PresentationTier der Clientanwendung erfordert einen Dienstverweis auf den Datendienst, um auf die Methoden des Diensts zugreifen zu können. Außerdem ist ein Verweis auf das DataSet erforderlich, um die Typfreigabe des WCF-Diensts zu aktivieren. Bis zur Aktivierung der Typfreigabe durch den Datendienst ist zu partiellen DataSet-Klassen hinzugefügter Code nicht auf der Präsentationsebene verfügbar. Da in der Regel Code, wie beispielsweise die Validierung, zu den Spalten- und Zeilenänderungsereignissen der Datentabelle hinzugefügt wird, erfolgt der Zugriff auf diesen Code wahrscheinlich vom Client aus.

#### <a name="to-add-a-reference-to-the-presentation-tier"></a>So fügen Sie einen Verweis auf die Präsentationsebene hinzu

1. In **Solution Explorer**, right-click PresentationTier and click **Add Reference**.

2. In the **Add Reference** dialog box, click the **Projects** tab.

3. Select **DataEntityTier** and click **OK**.

#### <a name="to-add-a-service-reference-to-the-presentation-tier"></a>So fügen Sie einen Dienstverweis auf die Präsentationsebene hinzu

1. In **Solution Explorer**, right-click PresentationTier and click **Add Service Reference**.

2. Klicken Sie im Dialogfeld **Dienstverweis hinzufügen** auf **Ermitteln**.

3. Select **Service1** and click **OK**.

    > [!NOTE]
    > Wenn der aktuelle Computer über mehrere Dienste verfügt, wählen Sie den zuvor in dieser exemplarischen Vorgehensweise erstellten Dienst aus (der Dienst, der die GetCustomers-Methode und die GetOrders-Methode enthält).

## <a name="adding-datagridviews-to-the-form-to-display-the-data-returned-by-the-data-service"></a>Hinzufügen von DataGridViews zum Formular, um die vom Datendienst zurückgegebenen Daten anzuzeigen.
 Nachdem der Dienstverweis zum Datendienst hinzugefügt wurde, werden die vom Dienst zurückgegebenen Daten automatisch zum Fenster **Datenquellen** hinzugefügt.

#### <a name="to-add-two-data-bound-datagridviews-to-the-form"></a>So fügen Sie zwei datengebundene DataGridViews zum Formular hinzu

1. In **Solution Explorer**, select the PresentationTier project.

2. Erweitern Sie im Fenster **Datenquellen** das **NorthwindDataSet**, und suchen Sie den Knoten **Customers**.

3. Ziehen Sie den Knoten **Customers** auf Form1.

4. Erweitern Sie im Fenster **Datenquellen** den Knoten **Customers**, und suchen Sie den zugehörigen Knoten **Orders** (den im Knoten **Customers** geschachtelten Knoten **Orders**).

5. Ziehen Sie den zugehörigen Knoten **Orders** auf Form1.

6. Erstellen Sie einen `Form1_Load`-Ereignishandler, indem Sie auf einen leeren Bereich des Formulars doppelklicken.

7. Fügen Sie dem `Form1_Load`-Ereignishandler den folgenden Code hinzu.

    ```vb
    Dim DataSvc As New ServiceReference1.Service1Client
    NorthwindDataSet.Customers.Merge(DataSvc.GetCustomers)
    NorthwindDataSet.Orders.Merge(DataSvc.GetOrders)
    ```

    ```csharp
    ServiceReference1.Service1Client DataSvc =
        new ServiceReference1.Service1Client();
    northwindDataSet.Customers.Merge(DataSvc.GetCustomers());
    northwindDataSet.Orders.Merge(DataSvc.GetOrders());

    ```

## <a name="increasing-the-maximum-message-size-allowed-by-the-service"></a>Erhöhen der maximalen vom Dienst zugelassenen Nachrichtengröße
 Da der Dienst Daten aus den Tabellen Customers und Orders zurückgibt, ist der Standardwert von maxReceivedMessageSize nicht ausreichend und muss erhöht werden. Für diese exemplarische Vorgehensweise ändern Sie den Wert in 6553600. Durch die Änderung des Werts im Client wird der Dienstverweis automatisch aktualisiert.

> [!NOTE]
> Die niedrigere Standardgröße dient dazu, die Anfälligkeit für Denial-of-Service (DoS)-Angriffe zu verringern. Weitere Informationen finden Sie unter <xref:System.ServiceModel.WSHttpBindingBase.MaxReceivedMessageSize%2A>.

#### <a name="to-increase-the-maxreceivedmessagesize-value"></a>So erhöhen Sie den maxReceivedMessageSize-Wert

1. In **Solution Explorer**, double-click the app.config file in the PresentationTier project.

2. Suchen Sie das **maxReceivedMessage**-Größenattribut, und ändern Sie den Wert in `6553600`.

## <a name="testing-the-application"></a>Testen der Anwendung
 Führen Sie die Anwendung aus. Die Daten werden vom Datendienst abgerufen und im Formular angezeigt.

#### <a name="to-test-the-application"></a>So testen Sie die Anwendung

1. Drücken Sie F5.

2. Die Daten aus den Tabellen Customers und Orders werden vom Datendienst abgerufen und im Formular angezeigt.

## <a name="next-steps"></a>Nächste Schritte
 Abhängig von den Anforderungen Ihrer Anwendung können nach dem Speichern der verknüpften Daten in der Windows-Anwendung weitere Schritte sinnvoll sein. Beispielsweise können Sie der Anwendung folgende Erweiterungen hinzufügen:

- Hinzufügen der Validierung zum DataSet. For information, see [Walkthrough: Adding Validation to an N-Tier Data Application](https://msdn.microsoft.com/library/b35d072c-31f0-49ba-a225-69177592c265).

- Hinzufügen von zusätzlichen Methoden zum Dienst für das Aktualisieren der Daten in der Datenbank.

## <a name="see-also"></a>Siehe auch
 [Work with datasets in n-tier applications](../data-tools/work-with-datasets-in-n-tier-applications.md) [Hierarchical update](../data-tools/hierarchical-update.md) [Accessing data in Visual Studio](../data-tools/accessing-data-in-visual-studio.md)
