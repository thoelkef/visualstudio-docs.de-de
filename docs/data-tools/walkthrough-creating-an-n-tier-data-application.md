---
title: "Exemplarische Vorgehensweise: Erstellen einer N-Tier-Datenanwendung | Microsoft Docs"
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
  - "N-Tier-Anwendungen, Erstellen"
  - "N-Tier-Anwendungen, Exemplarische Vorgehensweisen"
ms.assetid: d15e4d31-2839-48d9-9e0e-2e73404d82a2
caps.latest.revision: 48
caps.handback.revision: 48
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# Exemplarische Vorgehensweise: Erstellen einer N-Tier-Datenanwendung
*N\-Tier*\-Datenanwendungen sind Anwendungen, die auf Daten zugreifen und in mehrere logische Ebenen \(oder *Tiers*\) aufgeteilt sind.  Die Aufteilung der Anwendungskomponenten in verschiedene Ebenen erhöht die Verwaltbarkeit und die Skalierbarkeit der Anwendung.  Auf diese Weise wird das Einarbeiten neuer, eine einzelne Ebene betreffender Technologien vereinfacht, ein erneutes Entwerfen der Anwendung ist nicht notwendig.  Zur N\-Tier\-Architektur gehören eine Präsentationsebene, eine mittlere Ebene und eine Datenebene.  Die mittlere Ebene enthält eine Datenzugriffsschicht, eine Geschäftslogikschicht und gemeinsame Komponenten, wie beispielsweise Authentifizierung und Validierung.  Die Datenebene enthält eine relationale Datenbank.  N\-Tier\-Anwendungen speichern vertrauliche Informationen in der Datenzugriffsschicht der mittleren Ebene, um diese von Endbenutzern, die auf die Präsentationsebene zugreifen, getrennt zu halten.  Weitere Informationen finden Sie unter [Übersicht über N\-Tier\-Datenanwendungen](../data-tools/n-tier-data-applications-overview.md).  
  
 Eine Möglichkeit zum Trennen der verschiedenen Ebenen einer N\-Tier\-Anwendung besteht im Erstellen separater Projekte für jede Ebene, die in der Anwendung enthalten sein soll.  Typisierte DataSets enthalten eine `DataSet Project`\-Eigenschaft, mit der festgelegt wird, in welche Projekte der erzeugte DataSet\-Code und der erzeugte `TableAdapter`\-Code eingefügt werden.  
  
 In dieser exemplarischen Vorgehensweise wird dargestellt, wie DataSet\- und `TableAdapter`\-Code mithilfe des **DataSet\-Designers** in einzelne Klassenbibliotheksprojekte getrennt werden.  Nach der Trennung von DataSet\- und TableAdapter\-Code wird ein [Windows Communication Foundation Services and WCF Data Services in Visual Studio](../data-tools/windows-communication-foundation-services-and-wcf-data-services-in-visual-studio.md)\-Dienst für Aufrufe an die Datenzugriffsebene erstellt.  Abschließend wird eine Windows Forms\-Anwendung als Präsentationsebene erstellt.  Diese Ebene greift auf Daten des Datendiensts zu.  
  
 Im Verlauf dieser exemplarischen Vorgehensweise führen Sie folgende Schritte aus:  
  
-   Erstellen einer neuen N\-Tier\-Projektmappe, die mehrere Projekte enthält.  
  
-   Hinzufügen von zwei Klassenbibliotheksprojekten zur N\-Tier\-Projektmappe.  
  
-   Erstellen eines typisierten DataSets mithilfe des **Assistenten zum Konfigurieren von Datenquellen**.  
  
-   Trennen von generierten [TableAdapters](../Topic/TableAdapters.md) und DataSet\-Code in einzelne Projekte.  
  
-   Erstellen eines WCF \(Windows Communication Foundation\)\-Diensts für Aufrufe an die Datenzugriffsebene.  
  
-   Erstellen von Dienstfunktionen, um Daten von der Datenzugriffsebene abzurufen.  
  
-   Erstellen einer Windows Forms\-Anwendung, die als Präsentationsebene dient.  
  
-   Erstellen von Windows Forms\-Steuerelementen, die an die Datenquelle gebunden werden.  
  
-   Schreiben von Code zum Füllen der Datentabellen.  
  
 ![Link zu Video](~/data-tools/media/playvideo.gif "PlayVideo") Eine Videoversion dieses Themas finden Sie unter [Video How to: Creating an N\-Tier Data Application](http://go.microsoft.com/fwlink/?LinkId=115188).  
  
## Vorbereitungsmaßnahmen  
 Um diese exemplarische Vorgehensweise nachzuvollziehen, benötigen Sie Folgendes:  
  
-   Zugriff auf die Beispieldatenbank Northwind.  Weitere Informationen finden Sie unter [Gewusst wie: Installieren von Beispieldatenbanken](../data-tools/how-to-install-sample-databases.md).  
  
## Erstellen der N\-Tier\-Projektmappe der Klassenbibliothek für das DataSet \(DataEntityTier\)  
 Im ersten Schritt dieser exemplarischen Vorgehensweise werden eine Projektmappe und zwei Klassenbibliotheksprojekte erstellt.  Die erste Klassenbibliothek enthält das DataSet \(die generierte typisierte DataSet\-Klasse und die DataTables für die Anwendungsdaten\).  Dieses Projekt wird als Datenentitätsschicht der Anwendung verwendet und befindet sich normalerweise in der mittleren Ebene.  Der [Erstellen und Bearbeiten von typisierten Datasets](../data-tools/creating-and-editing-typed-datasets.md) wird verwendet, um das ursprüngliche DataSet zu erstellen und den Code automatisch in zwei Klassenbibliotheken aufzuteilen.  
  
> [!NOTE]
>  Stellen Sie sicher, das Projekt und Projektmappe ordnungsgemäß benannt wurden, bevor Sie auf **OK** klicken.  Das erleichtert die Durchführung der exemplarischen Vorgehensweise.  
  
#### So erstellen Sie die N\-Tier\-Projektmappe und die DataEntityTier\-Klassenbibliothek  
  
1.  Erstellen Sie über das Menü **Datei** ein neues Projekt.  
  
    > [!NOTE]
    >  Der **DataSet\-Designer** wird in [!INCLUDE[vbprvb](../code-quality/includes/vbprvb_md.md)]\-Projekten und C\#\-Projekten unterstützt.  Erstellen Sie das neue Projekt in einer der beiden Sprachen.  
  
2.  Klicken Sie im Dialogfeld **Neues Projekt** im Bereich **Projekttypen** auf **Windows**.  
  
3.  Klicken Sie auf die Vorlage für die **Klassenbibliothek**.  
  
4.  Nennen Sie das Projekt DataEntityTier.  
  
5.  Nennen Sie die Projektmappe NTierWalkthrough.  
  
6.  Klicken Sie auf **OK**.  
  
     Eine Projektmappe NTierWalkthrough mit dem Projekt DataEntityTier wird erstellt und zum **Projektmappen\-Explorer** hinzugefügt.  
  
## Erstellen der Klassenbibliothek für die TableAdapter \(DataAccessTier\)  
 Nach dem Erstellen des Projekts DataEntityTier besteht der nächste Schritt darin, ein zweites Klassenbibliotheksprojekt zu erstellen.  Dieses Projekt enthält die generierten `TableAdapter` und wird als *Datenzugriffsebene* bezeichnet.  Die Datenzugriffsebene enthält die zum Herstellen einer Verbindung mit der Datenbank notwendigen Informationen und befindet sich normalerweise in der mittleren Ebene.  
  
#### So erstellen Sie die neue Klassenbibliothek für die TableAdapter  
  
1.  Fügen Sie im Menü **Datei** ein neues Projekt zur NTierWalkthrough\-Projektmappe hinzu.  
  
2.  Klicken Sie im Dialogfeld **Neues Projekt** im Bereich **Vorlagen** auf **Klassenbibliothek**.  
  
3.  Nennen Sie das Projekt "DataAccessTier", und klicken Sie auf **OK**.  
  
     Das Projekt DataAccessTier wird erstellt und zur Projektmappe NTierWalkthrough hinzugefügt.  
  
## Erstellen des DataSets  
 Der nächste Schritt besteht darin, ein typisiertes DataSet zu erstellen.  Typisierte DataSets werden mit beiden DataSet\-Klassen \(einschließlich der DataTables\-Klassen\) und der `TableAdapter`\-Klassen in einem einzelnen Projekt erstellt.  \(Jede Klasse wird in einer einzelnen Datei generiert.\) Beim Trennen des DataSets und der `TableAdapter` in einzelne Projekte, wird die DataSet\-Klasse in ein anderes Projekt verschoben, während die `TableAdapter`\-Klassen im ursprünglichen Projekt verbleiben.  Erstellen Sie daher das DataSet in dem Projekt, das letztendlich die `TableAdapter` \(das Projekt DataAccessTier\) enthalten wird.  Das DataSet wird mithilfe des **Assistenten zum Konfigurieren von Datenquellen** erstellt.  
  
> [!NOTE]
>  Sie benötigen Zugriff auf die Beispieldatenbank Northwind, um die Verbindung herstellen zu können.  Informationen zum Einrichten der Beispieldatenbank Northwind finden Sie unter [Gewusst wie: Installieren von Beispieldatenbanken](../data-tools/how-to-install-sample-databases.md).  
  
#### So erstellen Sie das DataSet  
  
1.  Klicken Sie im **Projektmappen\-Explorer** auf DataAccessTier.  
  
2.  Klicken Sie im Menü **Daten** auf **Datenquellen anzeigen**.  
  
3.  Wählen Sie im **Datenquellenfenster** die Option **Neue Datenquelle hinzufügen** aus, um den **Assistenten zum Konfigurieren von Datenquellen** zu starten.  
  
4.  Klicken Sie auf der Seite **Datenquellentyp auswählen** auf **Datenbank** und anschließend auf **Weiter**.  
  
5.  Führen Sie auf der Seite **Wählen Sie Ihre Datenverbindung** eine der folgenden Aktionen aus:  
  
     Wenn in der Dropdownliste eine Datenverbindung zur Beispieldatenbank Northwind verfügbar ist, klicken Sie auf diese.  
  
     \- oder \-  
  
     Klicken Sie auf **Neue Verbindung**, um das Dialogfeld **Verbindung hinzufügen** zu öffnen.  
  
6.  Sollte für die Datenbank ein Kennwort erforderlich sein, wählen Sie die Option für die Einbeziehung vertraulicher Daten aus, und klicken Sie anschließend auf **Weiter**.  
  
    > [!NOTE]
    >  Wenn Sie eine lokale Datenbankdatei ausgewählt haben \(statt eine Verbindung mit SQL Server herzustellen\), werden Sie möglicherweise gefragt, ob Sie die Datei zum Projekt hinzufügen möchten.  Klicken Sie auf **Ja**, um die Datenbankdatei zum Projekt hinzuzufügen.  
  
7.  Klicken Sie auf der Seite **Verbindungszeichenfolge in der Programmkonfigurationsdatei speichern** auf **Weiter**.  
  
8.  Erweitern Sie auf der Seite **Datenbankobjekte auswählen** den Knoten **Tabellen**.  
  
9. Aktivieren Sie die Kontrollkästchen für die Tabellen **Customers** und **Orders**, und klicken Sie dann auf **Fertig stellen**.  
  
     Das NorthwindDataSet wird zur DataAccessTier hinzugefügt und im Fenster **Datenquellen** angezeigt.  
  
## Trennen der TableAdapter vom DataSet  
 Nach dem Erstellen des DataSets wird die generierte DataSet\-Klasse von den TableAdaptern getrennt.  Hierzu müssen Sie die **DataSet\-Projekt**\-Eigenschaft auf den Namen des Projekts festlegen, in dem die getrennten DataSet\-Klassen gespeichert werden sollen.  
  
#### So trennen Sie die TableAdapter vom DataSet  
  
1.  Doppelklicken Sie im **Projektmappen\-Explorer** auf **NorthwindDataSet.xsd**, um das DataSet im **DataSet\-Designer** zu öffnen.  
  
2.  Klicken Sie im Designer auf einen leeren Bereich.  
  
3.  Suchen Sie den Knoten **DataSet\-Projekt** im Fenster **Eigenschaften**.  
  
4.  Klicken Sie in der Liste **DataSet\-Projekt** auf **DataEntityTier**.  
  
5.  Klicken Sie im Menü **Erstellen** auf **Projektmappe erstellen**.  
  
 DataSet und TableAdapter werden in die zwei Klassenbibliotheksprojekte aufgeteilt.  Das Projekt, in dem ursprünglich das gesamte DataSet \(DataAccessTier\) enthalten war, enthält jetzt nur noch die TableAdapter.  Das in der **DataSet\-Projekt**\-Eigenschaft angegebene Projekt \(DataEntityTier\) enthält das typisierte DataSet: NorthwindDataSet.Dataset.Designer.vb \(oder NorthwindDataSet.Dataset.Designer.cs\).  
  
> [!NOTE]
>  Bei einer Aufteilung von DataSets und TableAdaptern \(durch Festlegen der **DataSet\-Projekt**\-Eigenschaft\) werden vorhandene partielle DataSet\-Klassen in dem Projekt nicht automatisch verschoben.  Vorhandene partielle DataSet\-Klassen müssen manuell in das DataSet\-Projekt verschoben werden.  
  
## Erstellen einer neuen Dienstanwendung  
 Da in dieser exemplarischen Vorgehensweise beschrieben wird, wie mithilfe eines WCF\-Diensts auf die Datenzugriffsebene zugegriffen wird, muss eine neue WCF\-Dienstanwendung erstellt werden.  
  
#### So erstellen Sie eine neue WCF\-Dienstanwendung  
  
1.  Fügen Sie im Menü **Datei** ein neues Projekt zur NTierWalkthrough\-Projektmappe hinzu.  
  
2.  Klicken Sie im Dialogfeld **Neues Projekt** im Bereich **Projekttypen** auf **WCF**.  Klicken Sie im Bereich **Vorlagen** auf **WCF\-Dienstbibliothek**.  
  
3.  Nennen Sie das Projekt "DataService", und klicken Sie auf **OK**.  
  
     Das Projekt DataService wird erstellt und zur Projektmappe NTierWalkthrough hinzugefügt.  
  
## Erstellen von Methoden in der Datenzugriffsebene, um Customers\- und Orders\-Daten zurückzugeben  
 Der Datendienst muss zwei Methoden in der Datenzugriffsebene aufrufen: GetCustomers und GetOrders.  Diese Methoden geben die Northwind\-Tabellen Customers und Orders zurück.  Erstellen Sie im Projekt DataAccessTier die GetCustomers\-Methode und die GetOrders\-Methode.  
  
#### So erstellen Sie eine Methode in der Datenzugriffsebene, die die Tabelle Customers zurückgibt  
  
1.  Doppelklicken Sie im **Projektmappen\-Explorer** auf NorthwindDataset.xsd, um das DataSet im [Erstellen und Bearbeiten von typisierten Datasets](../data-tools/creating-and-editing-typed-datasets.md) zu öffnen.  
  
2.  Klicken Sie mit der rechten Maustaste auf CustomersTableAdapter, und klicken Sie auf **Abfrage hinzufügen**, um den [TableAdapter\-Abfragekonfigurations\-Assistent](../data-tools/editing-tableadapters.md) zu öffnen.  
  
3.  Übernehmen Sie auf der Seite **Wählen Sie einen Befehlstyp aus** den Standardwert **SQL\-Anweisungen verwenden**, und klicken Sie auf **Weiter**.  
  
4.  Übernehmen Sie auf der Seite **Abfragetyp auswählen** den Standardwert **SELECT\-Anweisung, die Zeilen zurückgibt**, und klicken Sie auf **Weiter**.  
  
5.  Übernehmen Sie auf der Seite **SQL\-SELECT\-Anweisung angeben** die Standardabfrage, und klicken Sie auf **Weiter**.  
  
6.  Geben Sie auf der Seite **Zu generierende Methode auswählen** für den **Methodennamen** im Abschnitt **DataTable zurückgeben** die Zeichenfolge "GetCustomers" ein.  
  
7.  Klicken Sie auf **Fertig stellen**.  
  
#### So erstellen Sie eine Methode in der Datenzugriffsebene, die die Tabelle Orders zurückgibt  
  
1.  Klicken Sie mit der rechten Maustaste auf OrdersTableAdapter, und klicken Sie auf **Abfrage hinzufügen**.  
  
2.  Übernehmen Sie auf der Seite **Wählen Sie einen Befehlstyp aus** den Standardwert **SQL\-Anweisungen verwenden**, und klicken Sie auf **Weiter**.  
  
3.  Übernehmen Sie auf der Seite **Abfragetyp auswählen** den Standardwert **SELECT\-Anweisung, die Zeilen zurückgibt**, und klicken Sie auf **Weiter**.  
  
4.  Übernehmen Sie auf der Seite **SQL\-SELECT\-Anweisung angeben** die Standardabfrage, und klicken Sie auf **Weiter**.  
  
5.  Geben Sie auf der Seite **Zu generierende Methode auswählen** für den **Methodennamen** im Abschnitt **DataTable zurückgeben** die Zeichenfolge "GetOrders" ein.  
  
6.  Klicken Sie auf **Fertig stellen**.  
  
7.  Klicken Sie im Menü **Erstellen** auf **Projektmappe erstellen**.  
  
## Hinzufügen eines Verweises auf die Datenentitätsebene und die Datenzugriffsebene für den Datendienst  
 Da der Datendienst Informationen von DataSet und TableAdaptern erfordert, müssen Verweise auf das Projekt DataEntityTier und das Projekt DataAccessTier hinzugefügt werden.  
  
#### So fügen Sie Verweise zum Datendienst hinzu  
  
1.  Klicken Sie im **Projektmappen\-Explorer** mit der rechten Maustaste auf DataService, und klicken Sie anschließend auf **Verweis hinzufügen**.  
  
2.  Klicken Sie im Dialogfeld **Verweis hinzufügen** auf die Registerkarte **Projekte**.  
  
3.  Wählen Sie sowohl das Projekt **DataAccessTier** als auch das Projekt **DataEntityTier** aus.  
  
4.  Klicken Sie auf **OK**.  
  
## Hinzufügen von Funktionen, mit denen der Dienst die GetCustomers\-Methode und die GetOrders\-Methode in der Datenzugriffsebene aufruft  
 Nachdem die Datenzugriffsebene die Methoden zur Rückgabe der Daten enthält, müssen Sie im Datendienst Methoden erstellen, um die Methoden in der Datenzugriffsebene aufzurufen.  
  
> [!NOTE]
>  In C\#\-Projekten muss ein Verweis auf die `System.Data.DataSetExtensions`\-Assembly für die Kompilierung des nachfolgenden Codes hinzugefügt werden.  
  
#### So erstellen Sie im Datendienst die GetCustomers\-Funktion und die GetOrders\-Funktion  
  
1.  Doppelklicken Sie im Projekt **DataService** auf IService1.vb oder IService1.cs.  
  
2.  Fügen Sie unter dem Kommentar **Hier Dienstvorgänge hinzufügen** folgenden Code hinzu:  
  
    ```vb#  
    <OperationContract()> _  
    Function GetCustomers() As DataEntityTier.NorthwindDataSet.CustomersDataTable  
  
    <OperationContract()> _  
    Function GetOrders() As DataEntityTier.NorthwindDataSet.OrdersDataTable  
    ```  
  
    ```c#  
    [OperationContract]  
    DataEntityTier.NorthwindDataSet.CustomersDataTable GetCustomers();  
  
    [OperationContract]  
    DataEntityTier.NorthwindDataSet.OrdersDataTable GetOrders();  
  
    ```  
  
3.  Doppelklicken Sie im Projekt DataService auf IService1.vb \(oder IService1.cs\).  
  
4.  Fügen Sie der Service1\-Klasse den folgenden Code hinzu:  
  
    ```vb#  
    Public Function GetCustomers() As DataEntityTier.NorthwindDataSet.CustomersDataTable Implements IService1.GetCustomers  
        Dim CustomersTableAdapter1 As New DataAccessTier.NorthwindDataSetTableAdapters.CustomersTableAdapter  
        Return CustomersTableAdapter1.GetCustomers()  
    End Function  
  
    Public Function GetOrders() As DataEntityTier.NorthwindDataSet.OrdersDataTable Implements IService1.GetOrders  
        Dim OrdersTableAdapter1 As New DataAccessTier.NorthwindDataSetTableAdapters.OrdersTableAdapter  
        Return OrdersTableAdapter1.GetOrders()  
    End Function  
    ```  
  
    ```c#  
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
  
5.  Klicken Sie im Menü **Erstellen** auf **Projektmappe erstellen**.  
  
## Erstellen einer Präsentationsebene zum Anzeigen von Daten des Datendiensts  
 Nachdem die Projektmappe den Datendienst enthält, der über Methoden zum Aufrufen der Datenzugriffsebene verfügt, muss ein weiteres Projekt erstellt werden, das den Datendienst aufruft und den Benutzern die Daten anzeigt.  Erstellen Sie für diese exemplarische Vorgehensweise eine Windows Forms\-Anwendung als Präsentationsebene der N\-Tier\-Anwendung.  
  
#### So erstellen Sie das Präsentationsebenenprojekt  
  
1.  Fügen Sie im Menü **Datei** ein neues Projekt zur NTierWalkthrough\-Projektmappe hinzu.  
  
2.  Klicken Sie im Dialogfeld **Neues Projekt** im Bereich **Projekttypen** auf **Windows**.  Klicken Sie im Bereich **Vorlagen** auf **Windows Forms\-Anwendung**.  
  
3.  Nennen Sie das Projekt "PresentationTier", und klicken Sie auf **OK**.  
  
4.  Das Projekt PresentationTier wird erstellt und zur Projektmappe NTierWalkthrough hinzugefügt.  
  
## Festlegen des Projekts PresentationTier als Startprojekt  
 Da die Präsentationsebene die aktuelle Clientanwendung zum Präsentieren der Daten und zum interaktiven Arbeiten mit den Daten darstellt, muss das Projekt PresentationTier als Startprojekt festgelegt werden.  
  
#### So legen Sie das neue Präsentationsebenenprojekt als Startprojekt fest  
  
-   Klicken Sie im **Projektmappen\-Explorer** mit der rechten Maustaste auf **PresentationTier**, und klicken Sie anschließend auf **Als Startprojekt festlegen**.  
  
## Hinzufügen von Verweisen auf die Präsentationsebene  
 Die PresentationTier der Clientanwendung erfordert einen Dienstverweis auf den Datendienst, um auf die Methoden des Diensts zugreifen zu können.  Außerdem ist ein Verweis auf das DataSet erforderlich, um die Typfreigabe des WCF\-Diensts zu aktivieren.  Bis zur Aktivierung der Typfreigabe durch den Datendienst ist zu partiellen DataSet\-Klassen hinzugefügter Code nicht auf der Präsentationsebene verfügbar.  Da in der Regel Code, wie beispielsweise die Validierung, zu den Spalten\- und Zeilenänderungsereignissen der Datentabelle hinzugefügt wird, erfolgt der Zugriff auf diesen Code wahrscheinlich vom Client aus.  
  
#### So fügen Sie einen Verweis auf die Präsentationsebene hinzu  
  
1.  Klicken Sie im **Projektmappen\-Explorer** mit der rechten Maustaste auf PresentationTier, und klicken Sie anschließend auf **Verweis hinzufügen**.  
  
2.  Klicken Sie im Dialogfeld **Verweis hinzufügen** auf die Registerkarte **Projekte**.  
  
3.  Wählen Sie **DataEntityTier** aus, und klicken Sie auf **OK**.  
  
#### So fügen Sie einen Dienstverweis auf die Präsentationsebene hinzu  
  
1.  Klicken Sie im **Projektmappen\-Explorer** mit der rechten Maustaste auf PresentationTier, und klicken Sie auf **Dienstverweis hinzufügen**.  
  
2.  Klicken Sie im Dialogfeld **Dienstverweis hinzufügen** auf **Ermitteln**.  
  
3.  Wählen Sie **Service1** aus, und klicken Sie auf **OK**.  
  
    > [!NOTE]
    >  Wenn der aktuelle Computer über mehrere Dienste verfügt, wählen Sie den zuvor in dieser exemplarischen Vorgehensweise erstellten Dienst aus \(der Dienst, der die GetCustomers\-Methode und die GetOrders\-Methode enthält\).  
  
## Hinzufügen von DataGridViews zum Formular, um die vom Datendienst zurückgegebenen Daten anzuzeigen.  
 Nachdem der Dienstverweis zum Datendienst hinzugefügt wurde, werden die vom Dienst zurückgegebenen Daten automatisch zum Fenster **Datenquellen** hinzugefügt.  
  
#### So fügen Sie zwei datengebundene DataGridViews zum Formular hinzu  
  
1.  Wählen Sie im **Projektmappen\-Explorer** das Projekt PresentationTier aus.  
  
2.  Erweitern Sie im Fenster **Datenquellen** das **NorthwindDataSet**, und suchen Sie den Knoten **Customers**.  
  
3.  Ziehen Sie den Knoten **Customers** auf Form1.  
  
4.  Erweitern Sie im Fenster **Datenquellen** den Knoten **Customers**, und suchen Sie den zugehörigen Knoten **Orders** \(den im Knoten **Customers** geschachtelten Knoten **Orders**\).  
  
5.  Ziehen Sie den zugehörigen Knoten **Orders** auf Form1.  
  
6.  Erstellen Sie einen `Form1_Load`\-Ereignishandler, indem Sie auf einen leeren Bereich des Formulars doppelklicken.  
  
7.  Fügen Sie dem `Form1_Load`\-Ereignishandler den folgenden Code hinzu.  
  
    ```vb#  
    Dim DataSvc As New ServiceReference1.Service1Client  
    NorthwindDataSet.Customers.Merge(DataSvc.GetCustomers)  
    NorthwindDataSet.Orders.Merge(DataSvc.GetOrders)  
    ```  
  
    ```c#  
    ServiceReference1.Service1Client DataSvc =   
        new ServiceReference1.Service1Client();  
    northwindDataSet.Customers.Merge(DataSvc.GetCustomers());  
    northwindDataSet.Orders.Merge(DataSvc.GetOrders());  
  
    ```  
  
## Erhöhen der maximalen vom Dienst zugelassenen Nachrichtengröße  
 Da der Dienst Daten aus den Tabellen Customers und Orders zurückgibt, ist der Standardwert von maxReceivedMessageSize nicht ausreichend und muss erhöht werden.  Für diese exemplarische Vorgehensweise ändern Sie den Wert in 6553600.  Durch die Änderung des Werts im Client wird der Dienstverweis automatisch aktualisiert.  
  
> [!NOTE]
>  Die niedrigere Standardgröße dient dazu, die Anfälligkeit für Denial\-of\-Service \(DoS\)\-Angriffe zu verringern.  Weitere Informationen finden Sie unter <xref:System.ServiceModel.WSHttpBindingBase.MaxReceivedMessageSize%2A>.  
  
#### So erhöhen Sie den maxReceivedMessageSize\-Wert  
  
1.  Doppelklicken Sie im **Projektmappen\-Explorer** im Projekt PresentationTier auf die Datei app.config.  
  
2.  Suchen Sie das **maxReceivedMessage**\-Größenattribut, und ändern Sie den Wert in `6553600`.  
  
## Testen der Anwendung  
 Führen Sie die Anwendung aus.  Die Daten werden vom Datendienst abgerufen und im Formular angezeigt.  
  
#### So testen Sie die Anwendung  
  
1.  Drücken Sie F5.  
  
2.  Die Daten aus den Tabellen Customers und Orders werden vom Datendienst abgerufen und im Formular angezeigt.  
  
## Nächste Schritte  
 Abhängig von den Anforderungen Ihrer Anwendung können nach dem Speichern der verknüpften Daten in der Windows\-Anwendung weitere Schritte sinnvoll sein.  Beispielsweise können Sie der Anwendung folgende Erweiterungen hinzufügen:  
  
-   Hinzufügen der Validierung zum DataSet.  Weitere Informationen finden Sie unter [Exemplarische Vorgehensweise: Hinzufügen von Validierungen zu einer N\-Tier\-Datenanwendung](../Topic/Walkthrough:%20Adding%20Validation%20to%20an%20N-Tier%20Data%20Application.md).  
  
-   Hinzufügen von zusätzlichen Methoden zum Dienst für das Aktualisieren der Daten in der Datenbank.  
  
## Siehe auch  
 [Arbeiten mit Datasets in N\-Tier\-Anwendungen](../data-tools/work-with-datasets-in-n-tier-applications.md)   
 [Hierarchische Aktualisierung](../data-tools/hierarchical-update.md)   
 [Zugreifen auf Daten in Visual Studio](../data-tools/accessing-data-in-visual-studio.md)