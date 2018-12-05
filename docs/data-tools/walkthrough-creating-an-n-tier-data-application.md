---
title: 'Exemplarische Vorgehensweise: Erstellen einer N-Tier-Datenanwendung'
ms.date: 09/08/2017
ms.topic: conceptual
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- n-tier applications, creating
- n-tier applications, walkthroughs
ms.assetid: d15e4d31-2839-48d9-9e0e-2e73404d82a2
author: gewarren
ms.author: gewarren
manager: douge
ms.prod: visual-studio-dev15
ms.technology: vs-data-tools
ms.workload:
- data-storage
ms.openlocfilehash: 71c1c8dbaf34613d07ce29fa3f5e08d8e9c6961f
ms.sourcegitcommit: 81e9d90843ead658bc73b30c869f25921d99e116
ms.translationtype: MTE95
ms.contentlocale: de-DE
ms.lasthandoff: 11/26/2018
ms.locfileid: "52305701"
---
# <a name="walkthrough-create-an-n-tier-data-application"></a>Exemplarische Vorgehensweise: Erstellen einer N-Tier-Datenanwendung
*N-Tier*-Datenanwendungen sind Anwendungen, die auf Daten zugreifen und in mehrere logische Ebenen (oder *Tiers*) aufgeteilt sind. Die Aufteilung der Anwendungskomponenten in verschiedene Ebenen erhöht die Verwaltbarkeit und die Skalierbarkeit der Anwendung. Auf diese Weise wird das Einarbeiten neuer, eine einzelne Ebene betreffender Technologien vereinfacht, ein erneutes Entwerfen der Anwendung ist nicht notwendig. Zur N-Tier-Architektur gehören eine Präsentationsebene, eine mittlere Ebene und eine Datenebene. Die mittlere Ebene enthält eine Datenzugriffsschicht, eine Geschäftslogikschicht und gemeinsame Komponenten, wie beispielsweise Authentifizierung und Validierung. Die Datenebene enthält eine relationale Datenbank. N-Tier-Anwendungen speichern vertrauliche Informationen in der Datenzugriffsschicht der mittleren Ebene, um diese von Endbenutzern, die auf die Präsentationsebene zugreifen, getrennt zu halten. Weitere Informationen finden Sie unter [Übersicht über N-schichtige datenanwendungen](../data-tools/n-tier-data-applications-overview.md).

Eine Möglichkeit zum Trennen der verschiedenen Ebenen einer N-Tier-Anwendung besteht im Erstellen separater Projekte für jede Ebene, die in der Anwendung enthalten sein soll. Typisierte DataSets enthalten eine `DataSet Project`-Eigenschaft, mit der festgelegt wird, in welche Projekte der erzeugte DataSet-Code und der erzeugte `TableAdapter`-Code eingefügt werden.

In dieser exemplarischen Vorgehensweise wird dargestellt, wie DataSet- und `TableAdapter`-Code mithilfe des **DataSet-Designers** in einzelne Klassenbibliotheksprojekte aufgeteilt werden. Nachdem Sie das Dataset und TableAdapter-Code zu trennen, Sie erstellen eine [Windows Communication Foundation-Dienste und WCF Data Services in Visual Studio](../data-tools/windows-communication-foundation-services-and-wcf-data-services-in-visual-studio.md) Dienst in der Datenzugriffsebene aufrufen. Abschließend wird eine Windows Forms-Anwendung als Präsentationsebene erstellt. Diese Ebene greift auf Daten des Datendiensts zu.

Im Verlauf dieser exemplarischen Vorgehensweise führen Sie folgende Schritte aus:

-   Erstellen einer neuen N-Tier-Projektmappe, die mehrere Projekte enthält.

-   Hinzufügen von zwei Klassenbibliotheksprojekten zur N-Tier-Projektmappe.

-   Erstellen eines typisierten DataSets mithilfe des **Assistenten zum Konfigurieren von Datenquellen**.

-   Trennen von generierten [TableAdapters](create-and-configure-tableadapters.md) und Dataset-Code in einzelne Projekte.

-   Erstellen eines WCF (Windows Communication Foundation)-Diensts für Aufrufe an die Datenzugriffsebene.

-   Erstellen von Dienstfunktionen, um Daten von der Datenzugriffsebene abzurufen.

-   Erstellen einer Windows Forms-Anwendung, die als Präsentationsebene dient.

-   Erstellen von Windows Forms-Steuerelementen, die an die Datenquelle gebunden werden.

-   Schreiben von Code zum Füllen der Datentabellen.

![Link zum Video](../data-tools/media/playvideo.gif) eine Videoversion dieses Themas finden Sie unter [Video How to: Erstellen einer n-Tier-datenanwendung](http://go.microsoft.com/fwlink/?LinkId=115188).

## <a name="prerequisites"></a>Erforderliche Komponenten
In dieser exemplarischen Vorgehensweise verwendet SQL Server Express LocalDB und der Beispieldatenbank Northwind.

1. Wenn Sie SQL Server Express LocalDB nicht haben, installieren Sie es entweder über die [Downloadseite für SQL Server Express](https://www.microsoft.com/sql-server/sql-server-editions-express), oder über die **Visual Studio-Installer**. In der **Visual Studio-Installer**, können Sie SQL Server Express LocalDB installieren, als Teil der **.NET Desktopentwicklung** Workload oder als eine einzelne Komponente.

2. Installieren der Northwind-Beispieldatenbank mit folgenden Schritten:

    1. Öffnen Sie in Visual Studio die **Objekt-Explorer von SQL Server** Fenster. (**Objekt-Explorer von SQL Server** installiert ist, als Teil der **datenspeicherung und-Verarbeitung** Workload im Visual Studio-Installer.) Erweitern Sie die **SQL Server** Knoten. Mit der rechten Maustaste auf der LocalDB-Instanz, und wählen Sie **neue Abfrage**.

       In Abfrage-Editor-Fenster öffnen

    2. Kopieren der [Northwind Transact-SQL-Skript](https://github.com/MicrosoftDocs/visualstudio-docs/blob/master/docs/data-tools/samples/northwind.sql?raw=true) in die Zwischenablage. Dieses T-SQL-Skript wird die Northwind-Datenbank von Grund auf neu erstellt und mit Daten aufgefüllt.

    3. Fügen Sie das T-SQL-Skript im Abfrage-Editor, und wählen Sie dann die **Execute** Schaltfläche.

       Klicken Sie nach kurzer Zeit die Ausführung die Abfrage abgeschlossen ist, und die Northwind-Datenbank wird erstellt.

## <a name="create-the-n-tier-solution-and-class-library-to-hold-the-dataset-dataentitytier"></a>Erstellen der N-Tier-Projektmappe der Klassenbibliothek für das DataSet (DataEntityTier)
 Im ersten Schritt dieser exemplarischen Vorgehensweise werden eine Projektmappe und zwei Klassenbibliotheksprojekte erstellt. Die erste Klassenbibliothek enthält das Dataset (die generierte typisierte `DataSet` -Klasse und Datentabellen, die die Daten der Anwendung enthalten). Dieses Projekt wird als Datenentitätsschicht der Anwendung verwendet und befindet sich normalerweise in der mittleren Ebene. Der  wird verwendet, um das ursprüngliche DataSet zu erstellen und den Code automatisch in zwei Klassenbibliotheken aufzuteilen.

> [!NOTE]
> Stellen Sie sicher, dass Projekt und Projektmappe ordnungsgemäß benannt wurden, bevor Sie auf **OK** klicken. Das erleichtert die Durchführung der exemplarischen Vorgehensweise.

### <a name="to-create-the-n-tier-solution-and-dataentitytier-class-library"></a>So erstellen Sie die N-Tier-Projektmappe und die DataEntityTier-Klassenbibliothek

1. Klicken Sie in Visual Studio im Menü **Datei** auf **Neu** > **Projekt**.

2. Erweitern Sie entweder **Visual C#**  oder **Visual Basic** wählen Sie im linken Bereich **Windows Desktop**.

3. Wählen Sie im mittleren Bereich die **Klassenbibliothek** Projekttyp.

4. Nennen Sie das Projekt **DataEntityTier**.

5. Nennen Sie die Projektmappe **NTierWalkthrough**, und wählen Sie dann **OK**.

     Eine Projektmappe NTierWalkthrough mit dem Projekt DataEntityTier wird erstellt und zum **Projektmappen-Explorer** hinzugefügt.

## <a name="create-the-class-library-to-hold-the-tableadapters-dataaccesstier"></a>Erstellen der Klassenbibliothek für die TableAdapter (DataAccessTier)
 Nach dem Erstellen des Projekts DataEntityTier besteht der nächste Schritt darin, ein zweites Klassenbibliotheksprojekt zu erstellen. Dieses Projekt enthält die generierten  *und wird als Datenzugriffsebene* bezeichnet. Die Datenzugriffsebene enthält die zum Herstellen einer Verbindung mit der Datenbank notwendigen Informationen und befindet sich normalerweise in der mittleren Ebene.

### <a name="to-create-a-separate-class-library-for-the-tableadapters"></a>So erstellen Sie die neue Klassenbibliothek für die TableAdapter

1. Klicken Sie im **Projektmappen-Explorer** erst mit der rechten Maustaste auf den Knoten „Projektmappe“ und anschließend mit der Linken auf **Hinzufügen** > **Neues Projekt**.

2. In der **neues Projekt** im Dialogfeld im mittleren Bereich wählen **Klassenbibliothek**.

3. Nennen Sie das Projekt "DataAccessTier", und klicken Sie auf OK **.

     Das Projekt DataAccessTier wird erstellt und zur Projektmappe NTierWalkthrough hinzugefügt.

## <a name="create-the-dataset"></a>So erstellen Sie das DataSet
 Der nächste Schritt besteht darin, ein typisiertes DataSet zu erstellen. Typisierte Datasets werden mit beiden Dataset-Klassen erstellt (einschließlich `DataTables` Klassen) und die `TableAdapter` Klassen in einem einzelnen Projekt. Beim Trennen des DataSets und der `TableAdapter` in einzelne Projekte, wird die DataSet-Klasse in ein anderes Projekt verschoben, während die -Klassen im ursprünglichen Projekt verbleiben. Erstellen Sie daher das DataSet in dem Projekt, das letztendlich die  (das Projekt DataAccessTier) enthalten wird. Erstellen des DataSets mithilfe des Assistenten zum Konfigurieren von Datenquellen **.

> [!NOTE]
> Sie benötigen Zugriff auf die Beispieldatenbank Northwind, um die Verbindung herstellen zu können. Weitere Informationen zum Einrichten der Northwind-Beispieldatenbank, finden Sie unter [Vorgehensweise: Installieren von Beispieldatenbanken](../data-tools/installing-database-systems-tools-and-samples.md).

### <a name="to-create-the-dataset"></a>So erstellen Sie das DataSet

1. Klicken Sie im Projektmappen-Explorer** auf DataAccessTier.

2. Wählen Sie im Menü Daten**von** den Befehl Datenquellen anzeigen** aus.

   Das Fenster **Datenquellen** wird geöffnet.

3. Wählen Sie im Fenster **Datenquellen** die Option **Neue Datenquelle hinzufügen** aus, um den **Assistenten zum Konfigurieren von Datenquellen** zu starten.

4. Wählen Sie auf der Seite Datenquellentyp auswählen **die Option Datenbank** aus, und klicken Sie dann auf Weiter **.

5. Führen Sie auf der Seite **Wählen Sie Ihre Datenverbindung** eine der folgenden Aktionen aus:

     Wenn in der Dropdownliste eine Datenverbindung zur Beispieldatenbank „Northwind“ verfügbar ist, wählen Sie diese aus.

     - oder - 

     Klicken Sie auf Neue Verbindung **, um das Dialogfeld Verbindung hinzufügen** zu öffnen.

6. Sollte für die Datenbank ein Kennwort erforderlich sein, wählen Sie die Option für die Einbeziehung vertraulicher Daten aus, und klicken Sie anschließend auf **Weiter**.

    > [!NOTE]
    > Wenn Sie eine lokale Datenbankdatei ausgewählt haben (statt eine Verbindung mit SQL Server herzustellen), werden Sie möglicherweise gefragt, ob Sie die Datei zum Projekt hinzufügen möchten. Klicken Sie auf Ja **, um die Datenbankdatei zum Projekt hinzuzufügen.

7. Klicken Sie auf der Seite Verbindungszeichenfolge in der Programmkonfigurationsdatei speichern **auf Weiter**.

8. Erweitern Sie auf der Seite **Datenbankobjekte auswählen** den Knoten **Tabellen** .

9. Aktivieren Sie die Kontrollkästchen für die Tabellen Customers **und Orders**, und klicken Sie dann auf Fertig stellen **.

     Das NorthwindDataSet wird zum DataAccessTier-Projekt hinzugefügt und im Fenster **Datenquellen** angezeigt.

## <a name="separate-the-tableadapters-from-the-dataset"></a>So trennen Sie die TableAdapter vom DataSet
 Nach dem Erstellen des DataSets wird die generierte DataSet-Klasse von den TableAdaptern getrennt. Hierzu müssen Sie die **DataSet-Projekt**-Eigenschaft auf den Namen des Projekts festlegen, in dem die aufgeteilten DataSet-Klassen gespeichert werden sollen.

### <a name="to-separate-the-tableadapters-from-the-dataset"></a>So trennen Sie die TableAdapter vom DataSet

1. Doppelklicken Sie im **Projektmappen-Explorer** auf **NorthwindDataSet.xsd**, um das DataSet im **DataSet-Designer** zu öffnen.

2. Klicken Sie im Designer auf einen leeren Bereich.

3. Suchen Sie den Knoten **DataSet-Projekt** im Fenster **Eigenschaften**.

4. Klicken Sie in der Liste DataSet-Projekt **auf DataEntityTier**.

5. Klicken Sie im Menü **Erstellen** auf **Projektmappe erstellen**.

   DataSet und TableAdapter werden in die zwei Klassenbibliotheksprojekte aufgeteilt. Das Projekt, das ursprünglich das gesamte Dataset enthalten (`DataAccessTier`) enthält jetzt nur noch die TableAdapter. Das Projekt festgelegt wird, der **DataSet-Projekt** Eigenschaft (`DataEntityTier`) enthält das typisierte Dataset: *NorthwindDataSet.Dataset.Designer.vb* (oder  *NorthwindDataSet.Dataset.Designer.cs*).

> [!NOTE]
> Bei einer Aufteilung von DataSets und TableAdapters (durch Festlegen der **DataSet-Projekt**-Eigenschaft) werden vorhandene partielle DataSet-Klassen in dem Projekt nicht automatisch verschoben. Vorhandene partielle DataSet-Klassen müssen manuell in das DataSet-Projekt verschoben werden.

## <a name="create-a-new-service-application"></a>Erstellen einer neuen Dienstanwendung
Da in dieser exemplarischen Vorgehensweise beschrieben wird, wie mithilfe eines WCF-Diensts auf die Datenzugriffsebene zugegriffen wird, muss eine neue WCF-Dienstanwendung erstellt werden.

### <a name="to-create-a-new-wcf-service-application"></a>So erstellen Sie eine neue WCF-Dienstanwendung

1. Klicken Sie im **Projektmappen-Explorer** erst mit der rechten Maustaste auf den Knoten „Projektmappe“ und anschließend mit der Linken auf **Hinzufügen** > **Neues Projekt**.

2. In der **neues Projekt** im Dialogfeld im linken Bereich auf **WCF**. Wählen Sie im mittleren Bereich **WCF-Dienstbibliothek**.

3. Nennen Sie das Projekt "DataService", und klicken Sie auf OK **.

     Das Projekt DataService wird erstellt und zur Projektmappe NTierWalkthrough hinzugefügt.

## <a name="create-methods-in-the-data-access-tier-to-return-the-customers-and-orders-data"></a>Erstellen von Methoden in der Datenzugriffsebene, um Customers- und Orders-Daten zurückzugeben
 Der Datendienst muss zwei Methoden in der Datenzugriffsebene aufrufen: `GetCustomers` und `GetOrders`. Diese Methode gibt zurück, den Northwind `Customers` und `Orders` Tabellen. Erstellen der `GetCustomers` und `GetOrders` Methoden in der `DataAccessTier` Projekt.

### <a name="to-create-a-method-in-the-data-access-tier-that-returns-the-customers-table"></a>So erstellen Sie eine Methode in der Datenzugriffsebene, die die Tabelle Customers zurückgibt

1. Doppelklicken Sie im Projektmappen-Explorer**auf NorthwindDataset.xsd, um das DataSet im** zu öffnen.

2. Klicken Sie mit der rechten Maustaste auf CustomersTableAdapter, und klicken Sie auf Abfrage hinzufügen **, um den**  zu öffnen.

3. Übernehmen Sie auf der Seite **Wählen Sie einen Befehlstyp aus** den Standardwert **SQL-Anweisungen verwenden**, und klicken Sie auf **Weiter**.

4. Übernehmen Sie auf der Seite **Abfragetyp auswählen** den Standardwert **SELECT-Anweisung, die Zeilen zurückgibt**, und klicken Sie auf **Weiter**.

5. Übernehmen Sie auf der Seite **SQL-SELECT-Anweisung angeben** die Standardabfrage, und klicken Sie auf **Weiter**.

6. Geben Sie auf der Seite **Zu generierende Methode auswählen** für den **Methodennamen** im Abschnitt **DataTable zurückgeben** die Zeichenfolge **GetCustomers** ein.

7. Klicken Sie auf **Fertig stellen**.

### <a name="to-create-a-method-in-the-data-access-tier-that-returns-the-orders-table"></a>So erstellen Sie eine Methode in der Datenzugriffsebene, die die Tabelle Orders zurückgibt

1. Klicken Sie mit der rechten Maustaste auf **OrdersTableAdapter**, und klicken Sie auf **Abfrage hinzufügen**.

2. Übernehmen Sie auf der Seite **Wählen Sie einen Befehlstyp aus** den Standardwert **SQL-Anweisungen verwenden**, und klicken Sie auf **Weiter**.

3. Übernehmen Sie auf der Seite **Abfragetyp auswählen** den Standardwert **SELECT-Anweisung, die Zeilen zurückgibt**, und klicken Sie auf **Weiter**.

4. Übernehmen Sie auf der Seite **SQL-SELECT-Anweisung angeben** die Standardabfrage, und klicken Sie auf **Weiter**.

5. Geben Sie auf der Seite **Zu generierende Methoden auswählen** für den **Methodennamen** im Abschnitt **DataTable zurückgeben** die Zeichenfolge **GetOrders** ein.

6. Klicken Sie auf **Fertig stellen**.

7. Klicken Sie im Menü **Erstellen** auf **Projektmappe erstellen**.

## <a name="add-a-reference-to-the-data-entity-and-data-access-tiers-to-the-data-service"></a>Hinzufügen eines Verweises auf die Datenentitätsebene und die Datenzugriffsebene für den Datendienst
 Da der Datendienst Informationen von DataSet und TableAdapters erfordert, müssen Verweise auf das Projekt **DataEntityTier** und das Projekt **DataAccessTier** hinzugefügt werden.

### <a name="to-add-references-to-the-data-service"></a>So fügen Sie Verweise zum Datendienst hinzu

1. Klicken Sie im **Projektmappen-Explorer** mit der rechten Maustaste auf **DataService**, und klicken Sie anschließend auf **Verweis hinzufügen**.

2. Klicken Sie im Dialogfeld **Verweis hinzufügen** auf die Registerkarte **Projekte**.

3. Wählen Sie sowohl das Projekt **DataAccessTier** als auch das Projekt **DataEntityTier** aus.

4. Klicken Sie auf **OK**.

## <a name="add-functions-to-the-service-to-call-the-getcustomers-and-getorders-methods-in-the-data-access-tier"></a>Hinzufügen von Funktionen, mit denen der Dienst die GetCustomers-Methode und die GetOrders-Methode in der Datenzugriffsebene aufruft
 Nachdem die Datenzugriffsebene die Methoden zur Rückgabe der Daten enthält, müssen Sie im Datendienst Methoden erstellen, um die Methoden in der Datenzugriffsebene aufzurufen.

> [!NOTE]
> In C#-Projekten muss ein Verweis auf die `System.Data.DataSetExtensions`-Assembly für die Kompilierung des nachfolgenden Codes hinzugefügt werden.

### <a name="to-create-the-getcustomers-and-getorders-functions-in-the-data-service"></a>So erstellen Sie im Datendienst die GetCustomers-Funktion und die GetOrders-Funktion

1. Doppelklicken Sie im Projekt **DataService** auf **IService1.vb** oder **IService1.cs**.

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

3. Doppelklicken Sie im Projekt DataService auf **IService1.vb** (oder **IService1.cs**).

4. Fügen Sie der **Service1**-Klasse den folgenden Code hinzu:

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

## <a name="create-a-presentation-tier-to-display-data-from-the-data-service"></a>Erstellen einer Präsentationsebene zum Anzeigen von Daten des Datendiensts
 Nachdem die Projektmappe den Datendienst enthält, der über Methoden zum Aufrufen der Datenzugriffsebene verfügt, muss ein weiteres Projekt erstellt werden, das den Datendienst aufruft und den Benutzern die Daten anzeigt. Erstellen Sie für diese exemplarische Vorgehensweise eine Windows Forms-Anwendung als Präsentationsebene der N-Tier-Anwendung.

### <a name="to-create-the-presentation-tier-project"></a>So erstellen Sie das Präsentationsebenenprojekt

1. Klicken Sie im **Projektmappen-Explorer** erst mit der rechten Maustaste auf den Knoten „Projektmappe“ und anschließend mit der Linken auf **Hinzufügen** > **Neues Projekt**.

2. In der **neues Projekt** im Dialogfeld im linken Bereich auf **Windows Desktop**. Wählen Sie im mittleren Bereich **Windows Forms-App**.

3. Nennen Sie das Projekt **PresentationTier**, und klicken Sie auf **OK**.

    Das Projekt PresentationTier wird erstellt und zur Projektmappe NTierWalkthrough hinzugefügt.

## <a name="set-the-presentationtier-project-as-the-startup-project"></a>Festlegen des Projekts PresentationTier als Startprojekt
Legen wir die **PresentationTier** Projekt das Startprojekt für die Lösung sein, da es sich um die aktuelle Clientanwendung handelt, stellt und mit den Daten interagiert.

### <a name="to-set-the-new-presentation-tier-project-as-the-startup-project"></a>So legen Sie das neue Präsentationsebenenprojekt als Startprojekt fest

-   Klicken Sie im **Projektmappen-Explorer** mit der rechten Maustaste auf **PresentationTier**, und klicken Sie anschließend auf **Als Startprojekt festlegen**.

## <a name="add-references-to-the-presentation-tier"></a>Hinzufügen von Verweisen auf die Präsentationsebene
 Die PresentationTier der Clientanwendung erfordert einen Dienstverweis auf den Datendienst, um auf die Methoden des Diensts zugreifen zu können. Außerdem ist ein Verweis auf das DataSet erforderlich, um die Typfreigabe des WCF-Diensts zu aktivieren. Bis zur Aktivierung der Typfreigabe durch den Datendienst ist zu partiellen DataSet-Klassen hinzugefügter Code nicht auf der Präsentationsebene verfügbar. Da in der Regel Code, wie beispielsweise die Validierung, zu den Spalten- und Zeilenänderungsereignissen der Datentabelle hinzugefügt wird, erfolgt der Zugriff auf diesen Code wahrscheinlich vom Client aus.

### <a name="to-add-a-reference-to-the-presentation-tier"></a>So fügen Sie einen Verweis auf die Präsentationsebene hinzu

1. Klicken Sie im Projektmappen-Explorer **mit der rechten Maustaste auf PresentationTier, und klicken Sie anschließend auf Verweis hinzufügen**.

2. Klicken Sie im Dialogfeld **Verweis hinzufügen** auf die Registerkarte **Projekte**.

3. Wählen Sie DataEntityTier **aus, und klicken Sie auf OK**.

### <a name="to-add-a-service-reference-to-the-presentation-tier"></a>So fügen Sie einen Dienstverweis auf die Präsentationsebene hinzu

1. Klicken Sie im Projektmappen-Explorer **mit der rechten Maustaste auf PresentationTier, und klicken Sie auf Dienstverweis hinzufügen**.

2. Klicken Sie im Dialogfeld Dienstverweis hinzufügen **auf Ermitteln**.

3. Wählen Sie Service1 **aus, und klicken Sie auf OK**.

    > [!NOTE]
    > Wenn Sie mehrere Dienste auf dem aktuellen Computer verfügen, wählen Sie den Dienst, die Sie zuvor in dieser exemplarischen Vorgehensweise erstellt haben (der Dienst, enthält die `GetCustomers` und `GetOrders` Methoden).

## <a name="add-datagridviews-to-the-form-to-display-the-data-returned-by-the-data-service"></a>Hinzufügen von DataGridViews zum Formular, um die vom Datendienst zurückgegebenen Daten anzuzeigen.
 Nachdem der Dienstverweis zum Datendienst hinzugefügt wurde, werden die vom Dienst zurückgegebenen Daten automatisch zum Fenster **Datenquellen** hinzugefügt.

### <a name="to-add-two-data-bound-datagridviews-to-the-form"></a>So fügen Sie zwei datengebundene DataGridViews zum Formular hinzu

1. Wählen Sie im **Projektmappen-Explorer** das Projekt **PresentationTier** aus.

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

## <a name="increase-the-maximum-message-size-allowed-by-the-service"></a>Erhöhen der maximalen vom Dienst zugelassenen Nachrichtengröße
Der Standardwert für `maxReceivedMessageSize` ist nicht groß genug zum Speichern der Daten abgerufen, die von der `Customers` und `Orders` Tabellen. In den folgenden Schritten müssen Sie den Wert in 6553600 erhöhen. Ändern Sie den Wert auf dem Client den Dienstverweis automatisch aktualisiert.

> [!NOTE]
> Die niedrigere Standardgröße dient dazu, die Anfälligkeit für Denial-of-Service (DoS)-Angriffe zu verringern. Weitere Informationen finden Sie unter <xref:System.ServiceModel.WSHttpBindingBase.MaxReceivedMessageSize%2A>.

### <a name="to-increase-the-maxreceivedmessagesize-value"></a>So erhöhen Sie den maxReceivedMessageSize-Wert

1. Doppelklicken Sie im **Projektmappen-Explorer** im Projekt **PresentationTier** auf die Datei **app.config**.

2. Suchen Sie das **maxReceivedMessage**-Größenattribut, und ändern Sie den Wert in `6553600`.

## <a name="test-the-application"></a>Testen der Anwendung
Drücken Sie **F5**, um die Anwendung auszuführen. Die Daten aus der `Customers` und `Orders` Tabellen aus dem Datendienst abgerufen und im Formular angezeigt.

## <a name="next-steps"></a>Nächste Schritte
 Abhängig von den Anforderungen Ihrer Anwendung können nach dem Speichern der verknüpften Daten in der Windows-Anwendung weitere Schritte sinnvoll sein. Beispielsweise können Sie der Anwendung folgende Erweiterungen hinzufügen:

-   Hinzufügen der Validierung zum DataSet.

-   Hinzufügen von zusätzlichen Methoden zum Dienst für das Aktualisieren der Daten in der Datenbank.

## <a name="see-also"></a>Siehe auch

- [Arbeiten mit Datasets in N-Tier-Anwendungen](../data-tools/work-with-datasets-in-n-tier-applications.md)
- [Hierarchische Aktualisierung](../data-tools/hierarchical-update.md)
- [Zugreifen auf Daten in Visual Studio](../data-tools/accessing-data-in-visual-studio.md)