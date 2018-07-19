---
title: Übergeben von Daten zwischen Formularen
ms.date: 11/04/2016
ms.topic: conceptual
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- walkthroughs [Windows Forms], data
- walkthroughs [Visual Studio], data
- data [Visual Studio], passing between forms
- forms, passing data between
- Windows Forms, walkthroughs
ms.assetid: 78bf038b-9296-4fbf-b0e8-d881d1aff0df
author: gewarren
ms.author: gewarren
manager: douge
ms.prod: visual-studio-dev15
ms.technology: vs-data-tools
ms.workload:
- data-storage
ms.openlocfilehash: c8d400f8fa46fa10876d1827205671b6d90a3e33
ms.sourcegitcommit: e9d1018a01af62c3dc5aeb6b325faba7e20bd496
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 06/28/2018
ms.locfileid: "37089437"
---
# <a name="pass-data-between-forms"></a>Übergeben von Daten zwischen Formularen
Diese exemplarische Vorgehensweise enthält eine Schritt-für-Schritt-Anleitung für die Datenübergabe von einem Formular zum anderen. Verwenden die Tabellen Customers und Orders von Northwind, ein Formular ermöglicht Benutzern, um einen Kunden auszuwählen, und eine zweite Form zeigt die ausgewählte Bestellungen des Kunden. In dieser exemplarischen Vorgehensweise zeigt, wie Sie eine Methode auf das zweite Formular erstellen, die Daten aus dem ersten Formular empfängt.

> [!NOTE]
>  Diese exemplarische Vorgehensweise zeigt nur eine Möglichkeit der Datenübergabe zwischen Formularen. Es gibt andere Optionen zum Übergeben von Daten zu einem Formular, einschließlich der Erstellung eines zweiten Konstruktors, um Daten zu erhalten, oder erstellen eine öffentliche Eigenschaft, die mit Daten aus dem ersten Formular festgelegt werden.

 In dieser exemplarischen Vorgehensweise werden u. a. folgende Aufgaben veranschaulicht:

-   Erstellen eines neuen **Windows Forms-Anwendung** Projekt.

-   Erstellen und Konfigurieren eines Datasets mithilfe der [Assistenten zur Datenquellenkonfiguration](../data-tools/media/data-source-configuration-wizard.png).

-   Auswählen des Steuerelements, auf dem Formular erstellt werden, beim Ziehen von Elementen aus der **Datenquellen** Fenster. Weitere Informationen finden Sie unter [legen Sie das Steuerelement erstellt werden, beim Ziehen aus Datenquellenfenster](../data-tools/set-the-control-to-be-created-when-dragging-from-the-data-sources-window.md).

-   Erstellen eines datengebundenen Steuerelements durch Ziehen von Elementen aus der **Datenquellen** auf das Formular.

-   Erstellen eines zweiten Formulars mit einem Raster für die Datenanzeige.

-   Erstellen einer TableAdapter-Abfrage für das Abrufen der Bestellungen eines bestimmten Kunden.

-   Übergeben von Daten zwischen Formularen.

## <a name="prerequisites"></a>Erforderliche Komponenten
In dieser exemplarischen Vorgehensweise verwendet SQL Server Express LocalDB und der Beispieldatenbank Northwind.

1.  Wenn Sie SQL Server Express LocalDB nicht haben, installieren Sie es entweder über die [Downloadseite für SQL Server Express](https://www.microsoft.com/sql-server/sql-server-editions-express), oder über die **Visual Studio-Installer**. In Visual Studio-Installer, SQL Server Express LocalDB installiert werden können, als Teil der **datenspeicherung und-Verarbeitung** Workload oder als eine einzelne Komponente.

2.  Installieren der Northwind-Beispieldatenbank mit folgenden Schritten:

    1. Öffnen Sie in Visual Studio die **Objekt-Explorer von SQL Server** Fenster. (Objekt-Explorer von SQL Server installiert ist, als Teil der **datenspeicherung und-Verarbeitung** Workload im Visual Studio-Installer.) Erweitern Sie die **SQL Server** Knoten. Mit der rechten Maustaste auf der LocalDB-Instanz, und wählen Sie **neue Abfrage**.

       Ein Abfrage-Editor-Fenster wird geöffnet.

    2. Kopieren der [Northwind Transact-SQL-Skript](https://github.com/MicrosoftDocs/visualstudio-docs/blob/master/docs/data-tools/samples/northwind.sql?raw=true) in die Zwischenablage. Dieses T-SQL-Skript wird die Northwind-Datenbank von Grund auf neu erstellt und mit Daten aufgefüllt.

    3. Fügen Sie das T-SQL-Skript im Abfrage-Editor, und wählen Sie dann die **Execute** Schaltfläche.

       Klicken Sie nach kurzer Zeit die Ausführung die Abfrage abgeschlossen ist, und die Northwind-Datenbank wird erstellt.

## <a name="create-the-windows-forms-application"></a>Erstellen Sie die Windows Forms-Anwendung

### <a name="to-create-the-new-windows-project"></a>So erstellen Sie ein neues Windows-Projekt

1. In Visual Studio auf die **Datei** , wählen Sie im Menü **neu** > **Projekt**.

2. Erweitern Sie entweder **Visual C#-** oder **Visual Basic** wählen Sie im linken Bereich **Windows Desktop**.

3. Wählen Sie im mittleren Bereich die **Windows Forms-App** Projekttyp.

4. Nennen Sie das Projekt **PassingDataBetweenForms**, und wählen Sie dann **OK**.

     Die **PassingDataBetweenForms** Projekt wird erstellt und hinzugefügt **Projektmappen-Explorer**.

## <a name="create-the-data-source"></a>Erstellen der Datenquelle

### <a name="to-create-the-data-source"></a>So erstellen Sie die Datenquelle

1.  Klicken Sie im Menü **Daten** auf **Datenquellen anzeigen**.

2.  In der **Datenquellen** wählen Sie im Fenster **neue Datenquelle hinzufügen** zum Starten der **Datenquellenkonfiguration** Assistenten.

3.  Wählen Sie auf der Seite **Datenquellentyp auswählen** die Option **Datenbank** aus, und klicken Sie auf **Weiter**.

4.  Auf der **Auswählen eines Datenbankmodells** überprüfen Sie, ob Seite **Dataset** angegeben ist, und klicken Sie dann auf **Weiter**.

5.  Auf der **wählen Sie Ihre Datenverbindung** eine der folgenden:

    -   Wenn in der Dropdownliste eine Datenverbindung zur Beispieldatenbank „Northwind“ verfügbar ist, wählen Sie diese aus.

    -   Wählen Sie **neue Verbindung** zum Starten der **Verbindung hinzufügen/ändern** Dialogfeld.

6.  Wenn Ihre Datenbank ein Kennwort erforderlich ist und die Option zum Einschließen von sensiblen Daten aktiviert ist, wählen Sie die Option, und klicken Sie dann auf **Weiter**.

7.  Auf der **Verbindungszeichenfolge in der Programmkonfigurationsdatei speichern** auf **Weiter**.

8.  Auf der **Datenbankobjekte auswählen** Seite, erweitern Sie die **Tabellen** Knoten.

9. Wählen Sie die **Kunden** und **Bestellungen** Tabellen, und klicken Sie dann auf **Fertig stellen**.

     Die **NorthwindDataSet** wird Ihrem Projekt hinzugefügt und die **Kunden** und **Bestellungen** Tabellen angezeigt werden, der **Datenquellen** Fenster.

## <a name="create-the-first-form-form1"></a>Erstellen Sie das erste Formular (Form1)
 Sie können ein datengebundenes Raster erstellen (eine <xref:System.Windows.Forms.DataGridView> Steuerelement), durch Ziehen der **Kunden** Knoten aus der **Datenquellen** auf das Formular.

### <a name="to-create-a-data-bound-grid-on-the-form"></a>So erstellen Sie ein datengebundenes Raster auf dem Formular

-   Ziehen Sie den Hauptknoten **Kunden** Knoten aus der **Datenquellen** auf **Form1**.

     Ein <xref:System.Windows.Forms.DataGridView> und eine Toolleiste (<xref:System.Windows.Forms.BindingNavigator>) für die Navigation angezeigt, auf **Form1**. Ein [NorthwindDataSet](../data-tools/dataset-tools-in-visual-studio.md), CustomersTableAdapter <xref:System.Windows.Forms.BindingSource>, und <xref:System.Windows.Forms.BindingNavigator> werden in der Komponentenleiste angezeigt.

## <a name="create-the-second-form-form2"></a>Erstellen Sie das zweite Formular (Form2)

### <a name="to-create-a-second-form-to-pass-the-data-to"></a>Erstellen eines zweiten Formulars, an das die Daten übergeben werden

1.  Wählen Sie aus dem Menü **Projekt** die Option **Windows Form hinzufügen** aus.

2.  Übernehmen Sie den Standardnamen der **Form2**, und klicken Sie auf **hinzufügen**.

3.  Ziehen Sie den Hauptknoten **Bestellungen** Knoten aus der **Datenquellen** auf **Form2**.

     Ein <xref:System.Windows.Forms.DataGridView> und eine Toolleiste (<xref:System.Windows.Forms.BindingNavigator>) für die Navigation angezeigt, auf **Form2**. Ein [NorthwindDataSet](../data-tools/dataset-tools-in-visual-studio.md), CustomersTableAdapter <xref:System.Windows.Forms.BindingSource>, und <xref:System.Windows.Forms.BindingNavigator> werden in der Komponentenleiste angezeigt.

4.  Löschen der **OrdersBindingNavigator** aus der Komponentenleiste.

     Die **OrdersBindingNavigator** nicht mehr auf **Form2**.

## <a name="add-a-tableadapter-query-to-form2-to-load-orders-for-the-selected-customer-on-form1"></a>Hinzufügen einer TableAdapter-Abfrage zu Form2 für das Laden der Bestellungen für den ausgewählten Kunden auf Form1

### <a name="to-create-a-tableadapter-query"></a>Zum Erstellen einer TableAdapter-Abfrage

1.  Doppelklicken Sie auf die **NorthwindDataSet.xsd** Datei **Projektmappen-Explorer**.

2.  Mit der rechten Maustaste die **OrdersTableAdapter**, und wählen Sie **Abfrage hinzufügen**.

3.  Lassen Sie die Standardoption **SQL-Anweisungen**, und klicken Sie dann auf **Weiter**.

4.  Lassen Sie die Standardoption **wählen Sie die Zeilen zurückgibt**, und klicken Sie dann auf **Weiter**.

5.  Hinzufügen eine WHERE-Klausel der Abfrage zurückzugebenden `Orders` basierend auf den `CustomerID`. Die Abfrage müsste ungefähr wie folgt aussehen:

    ```sql
    SELECT OrderID, CustomerID, EmployeeID, OrderDate, RequiredDate, ShippedDate, ShipVia, Freight, ShipName, ShipAddress, ShipCity, ShipRegion, ShipPostalCode, ShipCountry
    FROM Orders
    WHERE CustomerID = @CustomerID
    ```

    > [!NOTE]
    >  Überprüfen Sie die korrekte Parametersyntax für Ihre Datenbank. In Microsoft Access, würde die WHERE-Klausel beispielsweise wie folgt aussehen: `WHERE CustomerID = ?`.

6.  Klicken Sie auf **Weiter**.

7.  Für die **Geben Sie einen Namen für die DataTableMethod**, Typ `FillByCustomerID`.

8.  Deaktivieren der **DataTable zurückgeben** aus, und klicken Sie dann auf **Weiter**.

9. Klicken Sie auf **Fertig stellen**.

## <a name="create-a-method-on-form2-to-pass-data-to"></a>Erstellen Sie eine Methode auf Form2 für das Übergeben von Daten an

### <a name="to-create-a-method-to-pass-data-to"></a>Erstellen einer Methode für das Übergeben von Daten an

1.  Mit der rechten Maustaste **Form2**, und wählen Sie **Anzeigecode** öffnen **Form2** in die **Code-Editor**.

2.  Fügen Sie den folgenden Code **Form2** nach der `Form2_Load` Methode:

     [!code-vb[VbRaddataDisplaying#1](../data-tools/codesnippet/VisualBasic/pass-data-between-forms_1.vb)]
     [!code-csharp[VbRaddataDisplaying#1](../data-tools/codesnippet/CSharp/pass-data-between-forms_1.cs)]

## <a name="create-a-method-on-form1-to-pass-data-and-display-form2"></a>Erstellen Sie eine Methode auf Form1 für das Übergeben von Daten und Anzeigen von Form2

### <a name="to-create-a-method-to-pass-data-to-form2"></a>Erstellen einer Methode für das Übergeben von Daten an Form2

1.  In **Form1**mit der rechten Maustaste auf die Customer-Datenraster, und klicken Sie dann auf **Eigenschaften**.

2.  In der **Eigenschaften** Fenster, klicken Sie auf **Ereignisse**.

3.  Doppelklicken Sie auf die **CellDoubleClick** Ereignis.

     Der Code-Editor wird angezeigt.

4.  Aktualisieren Sie die Methodendefinition, sodass sie dem folgenden Beispiel entspricht:

     [!code-csharp[VbRaddataDisplaying#2](../data-tools/codesnippet/CSharp/pass-data-between-forms_2.cs)]
     [!code-vb[VbRaddataDisplaying#2](../data-tools/codesnippet/VisualBasic/pass-data-between-forms_2.vb)]

## <a name="run-the-application"></a>Ausführen der Anwendung

### <a name="to-run-the-application"></a>So führen Sie die Anwendung aus

-   Drücken Sie **F5**, um die Anwendung auszuführen.

-   Doppelklicken Sie auf einen Kundendatensatz in **Form1** öffnen **Form2** mit den Bestellungen dieses Kunden.

## <a name="next-steps"></a>Nächste Schritte

Entsprechend den Anforderungen an Ihre Anwendung können Sie nach dem Übergeben der Daten zwischen den Formularen noch weitere Schritte ausführen. Sie können an dieser exemplarischen Vorgehensweise beispielsweise folgende Verbesserungen vornehmen:

-   Hinzufügen oder Entfernen von Datenbankobjekten aus dem Dataset durch Bearbeiten. Weitere Informationen finden Sie unter [Erstellen und Konfigurieren von Datasets in Visual Studio](../data-tools/create-and-configure-datasets-in-visual-studio.md).

-   Hinzufügen einer Funktion für das Zurückspeichern von Daten in der Datenbank. Weitere Informationen finden Sie unter [Rückspeichern von Daten in der Datenbank](../data-tools/save-data-back-to-the-database.md).

## <a name="see-also"></a>Siehe auch

- [Binden von Windows Forms-Steuerelementen an Daten in Visual Studio](../data-tools/bind-windows-forms-controls-to-data-in-visual-studio.md)