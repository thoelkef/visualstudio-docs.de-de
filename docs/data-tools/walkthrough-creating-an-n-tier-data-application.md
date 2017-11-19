---
title: 'Exemplarische Vorgehensweise: Erstellen einer N-Tier-Datenanwendung | Microsoft Docs'
ms.custom: 
ms.date: 09/08/2017
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- n-tier applications, creating
- n-tier applications, walkthroughs
ms.assetid: d15e4d31-2839-48d9-9e0e-2e73404d82a2
caps.latest.revision: "48"
author: gewarren
ms.author: gewarren
manager: ghogen
ms.technology: vs-data-tools
ms.openlocfilehash: 22ea6a58453de8c28703dbe0252ab6370be55bf3
ms.sourcegitcommit: ee42a8771f0248db93fd2e017a22e2506e0f9404
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 11/09/2017
---
# <a name="walkthrough-creating-an-n-tier-data-application"></a>Exemplarische Vorgehensweise: Erstellen einer N-Tier-Datenanwendung
*N-Tier-* -datenanwendungen sind Anwendungen, die auf Daten zugreifen und werden in mehrere logische Ebenen unterteilt oder *Ebenen*. Die Aufteilung der Anwendungskomponenten in verschiedene Ebenen erhöht die Verwaltbarkeit und die Skalierbarkeit der Anwendung. Auf diese Weise wird das Einarbeiten neuer, eine einzelne Ebene betreffender Technologien vereinfacht, ein erneutes Entwerfen der Anwendung ist nicht notwendig. Zur N-Tier-Architektur gehören eine Präsentationsebene, eine mittlere Ebene und eine Datenebene. Die mittlere Ebene enthält eine Datenzugriffsschicht, eine Geschäftslogikschicht und gemeinsame Komponenten, wie beispielsweise Authentifizierung und Validierung. Die Datenebene enthält eine relationale Datenbank. N-Tier-Anwendungen speichern vertrauliche Informationen in der Datenzugriffsschicht der mittleren Ebene, um diese von Endbenutzern, die auf die Präsentationsebene zugreifen, getrennt zu halten. Weitere Informationen finden Sie unter [Übersicht über N-Tier Applications](../data-tools/n-tier-data-applications-overview.md).  
  
Eine Möglichkeit zum Trennen der verschiedenen Ebenen einer N-Tier-Anwendung besteht im Erstellen separater Projekte für jede Ebene, die in der Anwendung enthalten sein soll. Typisierte DataSets enthalten eine `DataSet Project`-Eigenschaft, mit der festgelegt wird, in welche Projekte der erzeugte DataSet-Code und der erzeugte `TableAdapter`-Code eingefügt werden.  
  
Diese exemplarische Vorgehensweise veranschaulicht, wie zum Trennen von Datasets und `TableAdapter` Code in einzelne Klassenbibliotheksprojekte mithilfe der **Dataset-Designer**. Nachdem Sie das Dataset und TableAdapter Code trennen, erstellen Sie eine [Windows Communication Foundation-Dienste und WCF Data Services in Visual Studio](../data-tools/windows-communication-foundation-services-and-wcf-data-services-in-visual-studio.md) Dienst in der Datenzugriffsebene aufrufen. Abschließend wird eine Windows Forms-Anwendung als Präsentationsebene erstellt. Diese Ebene greift auf Daten des Datendiensts zu.  
  
Im Verlauf dieser exemplarischen Vorgehensweise führen Sie folgende Schritte aus:  
  
-   Erstellen einer neuen N-Tier-Projektmappe, die mehrere Projekte enthält.  
  
-   Hinzufügen von zwei Klassenbibliotheksprojekten zur N-Tier-Projektmappe.  
  
-   Erstellen eines typisierten Datasets mithilfe der **Datenquellen Konfigurations-Assistenten**.  
  
-   Trennen Sie die generierte [TableAdapters](create-and-configure-tableadapters.md) und Dataset-Code in gesonderten Projekten.  
  
-   Erstellen eines WCF (Windows Communication Foundation)-Diensts für Aufrufe an die Datenzugriffsebene.  
  
-   Erstellen von Dienstfunktionen, um Daten von der Datenzugriffsebene abzurufen.  
  
-   Erstellen einer Windows Forms-Anwendung, die als Präsentationsebene dient.  
  
-   Erstellen von Windows Forms-Steuerelementen, die an die Datenquelle gebunden werden.  
  
-   Schreiben von Code zum Füllen der Datentabellen.  
  
![Link zu Video](../data-tools/media/playvideo.gif "PlayVideo") eine Videoversion dieses Themas, finden Sie unter [Video How to: Erstellen einer N-Tier-Datenanwendung](http://go.microsoft.com/fwlink/?LinkId=115188).  
  
## <a name="prerequisites"></a>Erforderliche Komponenten  
In dieser exemplarischen Vorgehensweise werden die SQL Server Express LocalDB und der Beispieldatenbank Northwind verwendet.  
  
1.  Wenn Sie nicht über SQL Server Express LocalDB verfügen, installieren Sie es entweder aus der [Downloadseite für SQL Server-Editionen](https://www.microsoft.com/en-us/server-cloud/Products/sql-server-editions/sql-server-express.aspx), oder über die **Installer für Visual Studio**. In der Visual Studio-Installer können als Teil des SQL Server Express LocalDB installiert werden die **.NET Desktopentwicklung** arbeitsauslastung oder als eine einzelne Komponente.  
  
2.  Installieren Sie die Beispieldatenbank Northwind, indem folgende Schritte:  

    1. Öffnen Sie in Visual Studio die **Objekt-Explorer von SQL Server** Fenster. (Objekt-Explorer von SQL Server installiert ist, als Teil der **datenspeicherung und Verarbeitung** arbeitsauslastung in der Visual Studio-Installer.) Erweitern Sie die **SQL Server** Knoten. Rechtsklicken Sie auf der LocalDB-Instanz, und wählen Sie **neue Abfrage...** .  

       Ein Abfrage-Editorfenster wird geöffnet.  

    2. Kopieren der [Northwind Transact-SQL-Skript](https://github.com/MicrosoftDocs/visualstudio-docs/blob/master/docs/data-tools/samples/northwind.sql?raw=true) in die Zwischenablage. Dieses T-SQL-Skript die Northwind-Datenbank von Grund auf neu erstellt und mit Daten aufgefüllt.  

    3. Fügen Sie das T-SQL-Skript im Abfrage-Editor, und wählen Sie dann die **Execute** Schaltfläche.  

       Nach kurzer Zeit die Abfrage die Ausführung abgeschlossen ist, und die Northwind-Datenbank wird erstellt.  
  
## <a name="creating-the-n-tier-solution-and-class-library-to-hold-the-dataset-dataentitytier"></a>Erstellen der N-Tier-Projektmappe der Klassenbibliothek für das DataSet (DataEntityTier)  
 Im ersten Schritt dieser exemplarischen Vorgehensweise werden eine Projektmappe und zwei Klassenbibliotheksprojekte erstellt. Die erste Klassenbibliothek enthält das DataSet (die generierte typisierte DataSet-Klasse und die DataTables für die Anwendungsdaten). Dieses Projekt wird als Datenentitätsschicht der Anwendung verwendet und befindet sich normalerweise in der mittleren Ebene. Die Datasetis verwendet, um das ursprüngliche Dataset zu erstellen und den Code automatisch in zwei Klassenbibliotheken aufzuteilen.  
  
> [!NOTE]
>  Achten Sie darauf, dass Sie das Projekt und Projektmappe ordnungsgemäß benannt wurden, bevor Sie auf **OK**. Das erleichtert die Durchführung der exemplarischen Vorgehensweise.  
  
#### <a name="to-create-the-n-tier-solution-and-dataentitytier-class-library"></a>So erstellen Sie die N-Tier-Projektmappe und die DataEntityTier-Klassenbibliothek  

1. In Visual Studio auf die **Datei** klicken Sie im Menü **neu**, **Projekt...** .  
  
2. Erweitern Sie entweder **Visual C#-** oder **Visual Basic** im linken Bereich, und wählen Sie dann **klassische Windows-Desktop**.  

3. Wählen Sie im mittleren Bereich die **-Klassenbibliothek** Projekttyp.  
  
4. Nennen Sie das Projekt **DataEntityTier**.  
  
5. Nennen Sie die Projektmappe **NTierWalkthrough**, und wählen Sie dann **OK**.  
  
     Eine Projektmappe NTierWalkthrough mit dem Projekt DataEntityTier wird erstellt und hinzugefügt **Projektmappen-Explorer**.  
  
## <a name="creating-the-class-library-to-hold-the-tableadapters-dataaccesstier"></a>Erstellen der Klassenbibliothek für die TableAdapter (DataAccessTier)  
 Nach dem Erstellen des Projekts DataEntityTier besteht der nächste Schritt darin, ein zweites Klassenbibliotheksprojekt zu erstellen. Dieses Projekt enthält die generierte `TableAdapter`s und heißt die *Datenzugriffsebene* der Anwendung. Die Datenzugriffsebene enthält die zum Herstellen einer Verbindung mit der Datenbank notwendigen Informationen und befindet sich normalerweise in der mittleren Ebene.  
  
#### <a name="to-create-a-separate-class-library-for-the-tableadapters"></a>So erstellen Sie eine separaten Klassenbibliothek für die TableAdapter  
  
1.  Mit der rechten Maustaste auf die Projektmappe im Projektmappen-Explorer, und wählen Sie **hinzufügen**, **neues Projekt...** .  
  
2.  In der **neues Projekt** in der Mitte, wählen Sie im Dialogfeld **-Klassenbibliothek**.  
  
3.  Nennen Sie das Projekt **DataAccessTier** , und wählen Sie **OK**.  
  
     Das Projekt DataAccessTier wird erstellt und zur Projektmappe NTierWalkthrough hinzugefügt.  
  
## <a name="creating-the-dataset"></a>Erstellen des DataSets  
 Der nächste Schritt besteht darin, ein typisiertes DataSet zu erstellen. Typisierte DataSets werden mit beiden DataSet-Klassen (einschließlich der DataTables-Klassen) und der `TableAdapter`-Klassen in einem einzelnen Projekt erstellt. (Jede Klasse wird in einer einzelnen Datei generiert.) Beim Trennen des DataSets und der `TableAdapter` in einzelne Projekte, wird die DataSet-Klasse in ein anderes Projekt verschoben, während die `TableAdapter`-Klassen im ursprünglichen Projekt verbleiben. Erstellen Sie daher das DataSet in dem Projekt, das letztendlich die `TableAdapter` (das Projekt DataAccessTier) enthalten wird. Erstellen Sie das Dataset mithilfe der **Datenquellen Konfigurations-Assistenten**.  
  
> [!NOTE]
>  Sie benötigen Zugriff auf die Beispieldatenbank Northwind, um die Verbindung herstellen zu können. Informationen zum Einrichten der Northwind-Beispieldatenbank, finden Sie unter [Vorgehensweise: Installieren von Beispieldatenbanken](../data-tools/installing-database-systems-tools-and-samples.md).  
  
#### <a name="to-create-the-dataset"></a>So erstellen Sie das DataSet  
  
1.  Wählen Sie im DataAccessTier **Projektmappen-Explorer**.  
  
2.  Auf der **Daten** klicken Sie im Menü **Datenquellen anzeigen**.  
  
3.  In der **Datenquellen** wählen **neue Datenquelle hinzufügen** zum Starten der **Datenquellen Konfigurations-Assistenten**.  
  
4.  Auf der **wählen Sie einen Datenquellentyp** Seite **Datenbank** und wählen Sie dann **Weiter**.  
  
5.  Auf der **wählen Sie Ihre Datenverbindung** Seite, führen Sie eine der folgenden Aktionen:  
  
     Wenn in der Dropdownliste eine Datenverbindung zur Beispieldatenbank „Northwind“ verfügbar ist, wählen Sie diese aus.  
  
     - oder -   
  
     Wählen Sie **neue Verbindung** So öffnen die **Verbindung hinzufügen** (Dialogfeld).  
  
6.  Wenn die Datenbank ein Kennwort erforderlich ist, wählen Sie die Option auf Einbeziehung vertraulicher Daten, und wählen Sie dann **Weiter**.  
  
    > [!NOTE]
    >  Wenn Sie eine lokale Datenbankdatei ausgewählt haben (statt eine Verbindung mit SQL Server herzustellen), werden Sie möglicherweise gefragt, ob Sie die Datei zum Projekt hinzufügen möchten. Wählen Sie **Ja** die Datenbankdatei zum Projekt hinzufügen.  
  
7.  Wählen Sie **Weiter** auf die **Verbindungszeichenfolge in der Anwendungskonfigurationsdatei speichern** Seite.  
  
8.  Erweitern Sie auf der Seite **Datenbankobjekte auswählen** den Knoten **Tabellen** .  
  
9.  Wählen Sie die Kontrollkästchen für die **Kunden** und **Aufträge** -Tabelle aus, und wählen Sie dann **Fertig stellen**.  
  
     NorthwindDataSet wird zur DataAccessTier hinzugefügt und wird in der **Datenquellen** Fenster.  
  
## <a name="separating-the-tableadapters-from-the-dataset"></a>Trennen der TableAdapter vom DataSet  
 Nach dem Erstellen des DataSets wird die generierte DataSet-Klasse von den TableAdaptern getrennt. Sie dazu die **DataSet-Projekt** -Eigenschaft auf den Namen des Projekts, in dem die getrennten Dataset-Klassen gespeichert.  
  
#### <a name="to-separate-the-tableadapters-from-the-dataset"></a>So trennen Sie die TableAdapter vom DataSet  
  
1.  Doppelklicken Sie auf **NorthwindDataSet.xsd** in **Projektmappen-Explorer** , öffnen Sie das Dataset in die **Dataset-Designer**.  
  
2.  Wählen Sie einen leeren Bereich des Designers.  
  
3.  Suchen Sie die **DataSet-Projekt** Knoten in der **Eigenschaften** Fenster.  
  
4.  In der **DataSet-Projekt** Liste **DataEntityTier**.  
  
5.  Auf der **erstellen** klicken Sie im Menü **Projektmappe**.  
  
 DataSet und TableAdapter werden in die zwei Klassenbibliotheksprojekte aufgeteilt. Das Projekt, in dem ursprünglich das gesamte DataSet (DataAccessTier) enthalten war, enthält jetzt nur noch die TableAdapter. Das Projekt festgelegt wird, der **DataSet-Projekt** Eigenschaft (DataEntityTier) enthält das typisierte Dataset: NorthwindDataSet.Dataset.Designer.vb (oder NorthwindDataSet.Dataset.Designer.cs).  
  
> [!NOTE]
>  Beim Trennen von Datasets und TableAdaptern (durch Festlegen der **DataSet-Projekt** Eigenschaft), werden vorhandene partielle Dataset-Klassen im Projekt nicht automatisch verschoben werden. Vorhandene partielle DataSet-Klassen müssen manuell in das DataSet-Projekt verschoben werden.  
  
## <a name="creating-a-new-service-application"></a>Erstellen einer neuen Dienstanwendung  
Diese exemplarische Vorgehensweise veranschaulicht, wie auf die Datenzugriffsebene mit einem WCF-Dienst zugreifen kann, wir erstellen eine neue WCF-dienstanwendung.  
  
#### <a name="to-create-a-new-wcf-service-application"></a>So erstellen Sie eine neue WCF-Dienstanwendung  
  
1.  Mit der rechten Maustaste auf die Projektmappe im Projektmappen-Explorer, und wählen Sie **hinzufügen**, **neues Projekt...** .  
  
2.  In der **neues Projekt** im linken Bereich, wählen Sie im Dialogfeld **WCF**.  Wählen Sie im mittleren Bereich **WCF-Dienstbibliothek**.  
  
3.  Nennen Sie das Projekt **"DataService"** , und wählen Sie **OK**.  
  
     Das Projekt DataService wird erstellt und zur Projektmappe NTierWalkthrough hinzugefügt.  
  
## <a name="creating-methods-in-the-data-access-tier-to-return-the-customers-and-orders-data"></a>Erstellen von Methoden in der Datenzugriffsebene, um Customers- und Orders-Daten zurückzugeben  
 Der Datendienst muss zwei Methoden in der Datenzugriffsebene aufrufen: GetCustomers und GetOrders. Diese Methoden geben die Northwind-Tabellen Customers und Orders zurück. Erstellen Sie im Projekt DataAccessTier die GetCustomers-Methode und die GetOrders-Methode.  
  
#### <a name="to-create-a-method-in-the-data-access-tier-that-returns-the-customers-table"></a>So erstellen Sie eine Methode in der Datenzugriffsebene, die die Tabelle Customers zurückgibt  
  
1.  In **Projektmappen-Explorer**, doppelklicken Sie auf NorthwindDataset.xsd, um das Dataset zu öffnen.
  
2.  Mit der rechten Maustaste CustomersTableAdapter, und klicken Sie auf **Abfrage hinzufügen**.  
  
3.  Auf der **wählen Sie einen Befehlstyp** Seite, behalten Sie den Standardwert des **SQL-Anweisungen** , und klicken Sie auf **Weiter**.  
  
4.  Auf der **wählen Sie eine Abfrageart** Seite, behalten Sie den Standardwert des **auswählen, welche Zeilen zurückgegeben, die** , und klicken Sie auf **Weiter**.  
  
5.  Auf der **Geben Sie eine SQL SELECT-Anweisung** Seite, lassen Sie die Standardabfrage, und klicken Sie auf **Weiter**.  
  
6.  Auf der **zu generierende Methode auswählen** geben **GetCustomers** für die **Methodennamen** in der **DataTable zurückgeben** Abschnitt.  
  
7.  Klicken Sie auf **Fertig stellen**.  
  
#### <a name="to-create-a-method-in-the-data-access-tier-that-returns-the-orders-table"></a>So erstellen Sie eine Methode in der Datenzugriffsebene, die die Tabelle Orders zurückgibt  
  
1.  Maustaste auf OrdersTableAdapter, und klicken Sie auf **Abfrage hinzufügen**.  
  
2.  Auf der **wählen Sie einen Befehlstyp** Seite, behalten Sie den Standardwert des **SQL-Anweisungen** , und klicken Sie auf **Weiter**.  
  
3.  Auf der **wählen Sie eine Abfrageart** Seite, behalten Sie den Standardwert des **auswählen, welche Zeilen zurückgegeben, die** , und klicken Sie auf **Weiter**.  
  
4.  Auf der **Geben Sie eine SQL SELECT-Anweisung** Seite, lassen Sie die Standardabfrage, und klicken Sie auf **Weiter**.  
  
5.  Auf der **zu generierende Methode auswählen** geben **GetOrders** für die **Methodennamen** in der **DataTable zurückgeben** Abschnitt.  
  
6.  Klicken Sie auf **Fertig stellen**.  
  
7.  Klicken Sie im Menü **Erstellen** auf **Projektmappe erstellen**.  
  
## <a name="adding-a-reference-to-the-data-entity-and-data-access-tiers-to-the-data-service"></a>Hinzufügen eines Verweises auf die Datenentitätsebene und die Datenzugriffsebene für den Datendienst  
 Da der Datendienst Informationen von DataSet und TableAdaptern erfordert, müssen Verweise auf das Projekt DataEntityTier und das Projekt DataAccessTier hinzugefügt werden.  
  
#### <a name="to-add-references-to-the-data-service"></a>So fügen Sie Verweise zum Datendienst hinzu  
  
1.  Mit der rechten Maustaste "DataService" in **Projektmappen-Explorer** , und klicken Sie auf **Verweis hinzufügen**.  
  
2.  Klicken Sie auf die **Projekte** Registerkarte der **Verweis hinzufügen** (Dialogfeld).  
  
3.  Wählen Sie sowohl die **DataAccessTier** und **DataEntityTier** Projekte.  
  
4.  Klicken Sie auf **OK**.  
  
## <a name="adding-functions-to-the-service-to-call-the-getcustomers-and-getorders-methods-in-the-data-access-tier"></a>Hinzufügen von Funktionen, mit denen der Dienst die GetCustomers-Methode und die GetOrders-Methode in der Datenzugriffsebene aufruft  
 Nachdem die Datenzugriffsebene die Methoden zur Rückgabe der Daten enthält, müssen Sie im Datendienst Methoden erstellen, um die Methoden in der Datenzugriffsebene aufzurufen.  
  
> [!NOTE]
>  In C#-Projekten muss ein Verweis auf die `System.Data.DataSetExtensions`-Assembly für die Kompilierung des nachfolgenden Codes hinzugefügt werden.  
  
#### <a name="to-create-the-getcustomers-and-getorders-functions-in-the-data-service"></a>So erstellen Sie im Datendienst die GetCustomers-Funktion und die GetOrders-Funktion  
  
1.  In der **"DataService"** Projekt, doppelklicken Sie auf "IService1.vb" oder "IService1.cs".  
  
2.  Fügen Sie den folgenden Code unter der **Hier Dienstvorgänge hinzufügen** Kommentar:  
  
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
  
3.  Doppelklicken Sie im Projekt DataService auf IService1.vb (oder IService1.cs).  
  
4.  Fügen Sie der Service1-Klasse den folgenden Code hinzu:  
  
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
  
5.  Klicken Sie im Menü **Erstellen** auf **Projektmappe erstellen**.  
  
## <a name="creating-a-presentation-tier-to-display-data-from-the-data-service"></a>Erstellen einer Präsentationsebene zum Anzeigen von Daten des Datendiensts  
 Nachdem die Projektmappe den Datendienst enthält, der über Methoden zum Aufrufen der Datenzugriffsebene verfügt, muss ein weiteres Projekt erstellt werden, das den Datendienst aufruft und den Benutzern die Daten anzeigt. Erstellen Sie für diese exemplarische Vorgehensweise eine Windows Forms-Anwendung als Präsentationsebene der N-Tier-Anwendung.  
  
#### <a name="to-create-the-presentation-tier-project"></a>So erstellen Sie das Präsentationsebenenprojekt  
  
1.  Mit der rechten Maustaste auf die Projektmappe im Projektmappen-Explorer, und wählen Sie **hinzufügen**, **neues Projekt...** .  
  
2.  In der **neues Projekt** im linken Bereich, wählen Sie im Dialogfeld **klassische Windows-Desktop**. Wählen Sie im mittleren Bereich **Windows Forms-Anwendung**.  
  
3.  Nennen Sie das Projekt **PresentationTier** , und klicken Sie auf **OK**.  
  
    Das Projekt PresentationTier wird erstellt und zur Projektmappe NTierWalkthrough hinzugefügt.  
  
## <a name="setting-the-presentationtier-project-as-the-startup-project"></a>Festlegen des Projekts PresentationTier als Startprojekt  
Setzen wir das Projekt PresentationTier als Startprojekt für die Projektmappe, da es sich um die tatsächliche Client-Anwendung handelt, die zum darstellen und interagieren mit den Daten verwendet wird.  
  
#### <a name="to-set-the-new-presentation-tier-project-as-the-startup-project"></a>So legen Sie das neue Präsentationsebenenprojekt als Startprojekt fest  
  
-   In **Projektmappen-Explorer**, mit der rechten Maustaste **PresentationTier** , und klicken Sie auf **als Startprojekt festlegen**.  
  
## <a name="adding-references-to-the-presentation-tier"></a>Hinzufügen von Verweisen auf die Präsentationsebene  
 Die PresentationTier der Clientanwendung erfordert einen Dienstverweis auf den Datendienst, um auf die Methoden des Diensts zugreifen zu können. Außerdem ist ein Verweis auf das DataSet erforderlich, um die Typfreigabe des WCF-Diensts zu aktivieren. Bis zur Aktivierung der Typfreigabe durch den Datendienst ist zu partiellen DataSet-Klassen hinzugefügter Code nicht auf der Präsentationsebene verfügbar. Da in der Regel Code, wie beispielsweise die Validierung, zu den Spalten- und Zeilenänderungsereignissen der Datentabelle hinzugefügt wird, erfolgt der Zugriff auf diesen Code wahrscheinlich vom Client aus.  
  
#### <a name="to-add-a-reference-to-the-presentation-tier"></a>So fügen Sie einen Verweis auf die Präsentationsebene hinzu  
  
1.  In **Projektmappen-Explorer**mit der rechten Maustaste auf PresentationTier, und wählen Sie **Verweis hinzufügen**.  
  
2.  In der **Verweis hinzufügen** wählen Sie im Dialogfeld die **Projekte** Registerkarte.  
  
3.  Wählen Sie **DataEntityTier** , und wählen Sie **OK**.  
  
#### <a name="to-add-a-service-reference-to-the-presentation-tier"></a>So fügen Sie einen Dienstverweis auf die Präsentationsebene hinzu  
  
1.  In **Projektmappen-Explorer**mit der rechten Maustaste auf PresentationTier, und wählen Sie **Hinzufügen eines Dienstverweises**.  
  
2.  In der **Hinzufügen eines Dienstverweises** wählen Sie im Dialogfeld **Discover**.  
  
3.  Wählen Sie **"Service1"** , und wählen Sie **OK**.  
  
    > [!NOTE]
    >  Wenn der aktuelle Computer über mehrere Dienste verfügt, wählen Sie den zuvor in dieser exemplarischen Vorgehensweise erstellten Dienst aus (der Dienst, der die GetCustomers-Methode und die GetOrders-Methode enthält).  
  
## <a name="adding-datagridviews-to-the-form-to-display-the-data-returned-by-the-data-service"></a>Hinzufügen von DataGridViews zum Formular, um die vom Datendienst zurückgegebenen Daten anzuzeigen.  
 Nach dem Hinzufügen des Dienstverweises an den Datendienst den **Datenquellen** Fenster wird automatisch aufgefüllt, mit den Daten, die vom Dienst zurückgegeben wird.  
  
#### <a name="to-add-two-data-bound-datagridviews-to-the-form"></a>So fügen Sie zwei datengebundene DataGridViews zum Formular hinzu  
  
1.  In **Projektmappen-Explorer**, wählen Sie das Projekt PresentationTier aus.  
  
2.  In der **Datenquellen** Fenster, erweitern Sie **NorthwindDataSet** und suchen Sie die **Kunden** Knoten.  
  
3.  Ziehen Sie die **Kunden** Knoten auf Form1.  
  
4.  In der **Datenquellen** Fenster, erweitern Sie die **Kunden** Knoten und suchen Sie den zugehörigen **Aufträge** Knoten (die **Aufträge** geschachtelten Knoten in der  **Kunden** Knoten).  
  
5.  Ziehen Sie den zugehörigen **Aufträge** Knoten auf Form1.  
  
6.  Erstellen Sie einen `Form1_Load`-Ereignishandler, indem Sie auf einen leeren Bereich des Formulars doppelklicken.  
  
7.  Fügen Sie dem `Form1_Load`-Ereignishandler den folgenden Code hinzu.  
  
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
Der Standardwert von MaxReceivedMessageSize ist nicht groß genug zum Speichern der Daten aus den Tabellen Customers und Orders abgerufen. In den folgenden Schritten fügen Sie den Wert in 6553600 erhöhen. Sie ändern den Wert auf dem Client, die den Dienstverweis automatisch aktualisiert.  
  
> [!NOTE]
>  Die niedrigere Standardgröße dient dazu, die Anfälligkeit für Denial-of-Service (DoS)-Angriffe zu verringern. Weitere Informationen finden Sie unter <xref:System.ServiceModel.WSHttpBindingBase.MaxReceivedMessageSize%2A>.  
  
#### <a name="to-increase-the-maxreceivedmessagesize-value"></a>So erhöhen Sie den maxReceivedMessageSize-Wert  
  
1.  In **Projektmappen-Explorer**, doppelklicken Sie auf die Datei "App.config" in das Projekt PresentationTier aus.  
  
2.  Suchen Sie die **MaxReceivedMessage** Größenattribut, und ändern Sie den Wert auf `6553600`.  
  
## <a name="testing-the-application"></a>Testen der Anwendung  
Führen Sie die Anwendung durch Drücken von **F5**. Die Daten aus den Tabellen Customers und Orders werden vom Datendienst abgerufen und im Formular angezeigt.  
  
## <a name="next-steps"></a>Nächste Schritte  
 Abhängig von den Anforderungen Ihrer Anwendung können nach dem Speichern der verknüpften Daten in der Windows-Anwendung weitere Schritte sinnvoll sein. Beispielsweise können Sie der Anwendung folgende Erweiterungen hinzufügen:  
  
-   Hinzufügen der Validierung zum DataSet. 
  
-   Hinzufügen von zusätzlichen Methoden zum Dienst für das Aktualisieren der Daten in der Datenbank.  
  
## <a name="see-also"></a>Siehe auch  
 [Arbeiten Sie mit Datasets in n-Tier-Anwendungen](../data-tools/work-with-datasets-in-n-tier-applications.md)   
 [Hierarchische Aktualisierung](../data-tools/hierarchical-update.md)   
 [Zugreifen auf Daten in Visual Studio](../data-tools/accessing-data-in-visual-studio.md)