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
ms.openlocfilehash: 4a0d248f59754d3f46e8fab0e0924c36a80b0d89
ms.sourcegitcommit: 81e9d90843ead658bc73b30c869f25921d99e116
ms.translationtype: MTE95
ms.contentlocale: de-DE
ms.lasthandoff: 11/26/2018
ms.locfileid: "52305545"
---
# <a name="pass-data-between-forms"></a>Übergeben von Daten zwischen Formularen

Diese exemplarische Vorgehensweise enthält eine Schritt-für-Schritt-Anleitung für die Datenübergabe von einem Formular zum anderen. Verwenden die Tabellen Customers und Orders von Northwind, ein Formular ermöglicht Benutzern, um einen Kunden auszuwählen, und eine zweite Form zeigt die ausgewählte Bestellungen des Kunden. In dieser exemplarischen Vorgehensweise zeigt, wie Sie eine Methode auf das zweite Formular erstellen, die Daten aus dem ersten Formular empfängt.

> [!NOTE]
> Diese exemplarische Vorgehensweise zeigt nur eine Möglichkeit der Datenübergabe zwischen Formularen. Es gibt andere Optionen zum Übergeben von Daten zu einem Formular, einschließlich der Erstellung eines zweiten Konstruktors, um Daten zu erhalten, oder erstellen eine öffentliche Eigenschaft, die mit Daten aus dem ersten Formular festgelegt werden.

In dieser exemplarischen Vorgehensweise werden u. a. folgende Aufgaben veranschaulicht:

-   Erstellen eines neuen Projekts vom Typ **Windows Forms-Anwendung**.

-   Erstellen und Konfigurieren eines Datasets mithilfe der [Assistenten zur Datenquellenkonfiguration](../data-tools/media/data-source-configuration-wizard.png).

-   Auswählen des Steuerelements, das für das Formular erstellt werden soll, wenn Elemente aus dem **Datenquellenfenster** gezogen werden. Weitere Informationen finden Sie unter [legen Sie das Steuerelement erstellt werden, beim Ziehen aus Datenquellenfenster](../data-tools/set-the-control-to-be-created-when-dragging-from-the-data-sources-window.md).

-   Erstellen eines datengebundenen Steuerelements durch Ziehen von Elementen aus dem **Datenquellenfenster** auf das Formular.

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

## <a name="create-the-windows-forms-app-project"></a>Erstellen Sie das Windows Forms-app-Projekt

1. In Visual Studio auf die **Datei** , wählen Sie im Menü **neu** > **Projekt**.

2. Erweitern Sie entweder **Visual C#**  oder **Visual Basic** wählen Sie im linken Bereich **Windows Desktop**.

3. Wählen Sie im mittleren Bereich die **Windows Forms-App** Projekttyp.

4. Nennen Sie das Projekt **PassingDataBetweenForms**, und wählen Sie dann **OK**.

     Das Projekt **PassingDataBetweenForms** wird erstellt und zum **Projektmappen-Explorer** hinzugefügt.

## <a name="create-the-data-source"></a>Erstellen der Datenquelle

1.  Zum Öffnen der **Datenquellen** Fenster auf die **Daten** Menü klicken Sie auf **Datenquellen anzeigen**.

2.  Klicken Sie im **Datenquellenfenster** auf **Neue Datenquelle hinzufügen**, um den **Assistenten zum Konfigurieren von Datenquellen** zu starten.

3.  Wählen Sie auf der Seite **Datenquellentyp auswählen** die Option **Datenbank** aus, und klicken Sie auf **Weiter**.

4.  Stellen Sie sicher, dass **Dataset** auf der Seite **Datenbankmodell auswählen** festgelegt ist, und klicken Sie dann auf **Weiter**.

5.  Führen Sie auf der Seite **Wählen Sie Ihre Datenverbindung aus** einen der folgenden Schritte aus:

    -   Wenn in der Dropdownliste eine Datenverbindung zur Beispieldatenbank „Northwind“ verfügbar ist, wählen Sie diese aus.

    -   Klicken Sie auf **Neue Verbindung**, um das Dialogfeld **Add/Modify Connection** (Verbindung hinzufügen/ändern) zu öffnen.

6.  Falls die Datenbank ein Kennwort erfordern sollte und die Option für die Einbeziehung vertraulicher Daten aktiviert ist, wählen Sie die Option aus, und klicken Sie dann auf **Weiter**.

7.  Klicken Sie auf der Seite **Save connection string to the Application Configuration file** (Verbindungszeichenfolge in der Programmkonfigurationsdatei speichern) auf **Weiter**.

8.  Erweitern Sie auf der Seite **Datenbankobjekte auswählen** den Knoten **Tabellen**.

9. Wählen Sie die Tabellen **Customers** und **Orders** aus, und klicken Sie dann auf **Fertig stellen**.

     Das **NorthwindDataSet** wird dem Projekt hinzugefügt, und die Tabellen **Customers** und **Orders** werden im **Datenquellenfenster** angezeigt.

## <a name="create-the-first-form-form1"></a>Erstellen Sie das erste Formular (Form1)

Sie können ein datengebundenes Raster erstellen (ein <xref:System.Windows.Forms.DataGridView>-Steuerelement), indem Sie den Knoten **Customers** aus dem **Datenquellenfenster** auf das Formular ziehen.

### <a name="to-create-a-data-bound-grid-on-the-form"></a>So erstellen Sie ein datengebundenes Raster auf dem Formular

-   Ziehen Sie den Hauptknoten **Customers** aus dem Fenster **Datenquellen** auf **Form1**.

     Eine <xref:System.Windows.Forms.DataGridView> und eine Toolleiste (<xref:System.Windows.Forms.BindingNavigator>) zum Navigieren durch Datensätze wird auf **Form1** angezeigt. [NorthwindDataSet](../data-tools/dataset-tools-in-visual-studio.md), CustomersTableAdapter, <xref:System.Windows.Forms.BindingSource> und <xref:System.Windows.Forms.BindingNavigator> werden auf der Komponentenleiste angezeigt.

## <a name="create-the-second-form"></a>Das zweite Formular erstellen

Erstellen Sie eine zweite Form zum Übergeben von Daten an.

1.  Wählen Sie aus dem Menü **Projekt** die Option **Windows Form hinzufügen** aus.

2.  Übernehmen Sie den Standardnamen **Form2**, und klicken Sie auf **Hinzufügen**.

3.  Ziehen Sie den Hauptknoten **Orders** aus dem **Datenquellenfenster** auf **Form2**.

     Eine <xref:System.Windows.Forms.DataGridView> und eine Toolleiste (<xref:System.Windows.Forms.BindingNavigator>) zum Navigieren durch Datensätze wird auf **Form2** angezeigt. [NorthwindDataSet](../data-tools/dataset-tools-in-visual-studio.md), CustomersTableAdapter, <xref:System.Windows.Forms.BindingSource> und <xref:System.Windows.Forms.BindingNavigator> werden auf der Komponentenleiste angezeigt.

4.  Löschen Sie **OrdersBindingNavigator** aus der Komponentenleiste.

     **OrdersBindingNavigator** wird von **Form2** entfernt.

## <a name="add-a-tableadapter-query"></a>Hinzufügen einer TableAdapter-Abfrage

Hinzufügen einer TableAdapter-Abfrage zu Form2 für das Laden der Bestellungen für den ausgewählten Kunden auf Form1.

1.  Doppelklicken Sie im **Projektmappen-Explorer** auf die Datei **NorthwindDataSet.xsd**.

2.  Klicken Sie mit der rechten Maustaste auf **OrdersTableAdapter**, und wählen Sie **Abfrage hinzufügen** aus.

3.  Übernehmen Sie die Standardeinstellung für **SQL-Anweisung verwenden**, und klicken Sie anschließend auf **Weiter**.

4.  Übernehmen Sie die Standardeinstellung für **SELECT-Anweisung, die Zeilen zurückgibt**, und klicken Sie anschließend auf **Weiter**.

5.  Fügen Sie eine WHERE-Klausel zur Abfrage hinzu, sodass `Orders` auf Grundlage der `CustomerID` zurückgeben wird. Die Abfrage müsste ungefähr wie folgt aussehen:

    ```sql
    SELECT OrderID, CustomerID, EmployeeID, OrderDate, RequiredDate, ShippedDate, ShipVia, Freight, ShipName, ShipAddress, ShipCity, ShipRegion, ShipPostalCode, ShipCountry
    FROM Orders
    WHERE CustomerID = @CustomerID
    ```

    > [!NOTE]
    > Überprüfen Sie die korrekte Parametersyntax für Ihre Datenbank. In Microsoft Access würde die WHERE-Klausel wie folgt aussehen: `WHERE CustomerID = ?`.

6.  Klicken Sie auf **Weiter**.

7.  Für die **Geben Sie einen Namen für die DataTableMethod**, Typ `FillByCustomerID`.

8.  Löschen Sie die Option **DataTable zurückgeben**, und klicken Sie anschließend **Weiter**.

9. Klicken Sie auf **Fertig stellen**.

## <a name="create-a-method-on-form2-to-pass-data-to"></a>Erstellen Sie eine Methode auf Form2 für das Übergeben von Daten an

1.  Klicken Sie mit der rechten Maustaste auf **Form2**, und klicken Sie auf **Code anzeigen**, um **Form2** im **Code-Editor** zu öffnen.

2.  Fügen Sie den folgenden Code zu **Form2** nach der `Form2_Load`-Methode hinzu:

     [!code-vb[VbRaddataDisplaying#1](../data-tools/codesnippet/VisualBasic/pass-data-between-forms_1.vb)]
     [!code-csharp[VbRaddataDisplaying#1](../data-tools/codesnippet/CSharp/pass-data-between-forms_1.cs)]

## <a name="create-a-method-on-form1-to-pass-data-and-display-form2"></a>Erstellen Sie eine Methode auf Form1 für das Übergeben von Daten und Anzeigen von Form2

1.  Klicken Sie in **Form1** mit der rechten Maustaste auf das Customer-Datenraster, und klicken Sie dann auf **Eigenschaften**.

2.  Klicken Sie im Fenster **Eigenschaften** auf **Ereignisse**.

3.  Doppelklicken Sie das Ereignis **CellDoubleClick**.

     Der Code-Editor wird angezeigt.

4.  Aktualisieren Sie die Methodendefinition, sodass sie dem folgenden Beispiel entspricht:

     [!code-csharp[VbRaddataDisplaying#2](../data-tools/codesnippet/CSharp/pass-data-between-forms_2.cs)]
     [!code-vb[VbRaddataDisplaying#2](../data-tools/codesnippet/VisualBasic/pass-data-between-forms_2.vb)]

## <a name="run-the-app"></a>Ausführen der App

-   Drücken Sie **F5**, um die Anwendung auszuführen.

-   Doppelklicken Sie einen Kundendatensatz in **Form1**, sodass dieser in **Form2** mit den Bestellungen dieses Kunden geöffnet wird.

## <a name="next-steps"></a>Nächste Schritte

Entsprechend den Anforderungen an Ihre Anwendung können Sie nach dem Übergeben der Daten zwischen den Formularen noch weitere Schritte ausführen. Sie können an dieser exemplarischen Vorgehensweise beispielsweise folgende Verbesserungen vornehmen:

-   Hinzufügen oder Entfernen von Datenbankobjekten aus dem Dataset durch Bearbeiten. Weitere Informationen finden Sie unter [Erstellen und Konfigurieren von Datasets in Visual Studio](../data-tools/create-and-configure-datasets-in-visual-studio.md).

-   Hinzufügen einer Funktion für das Zurückspeichern von Daten in der Datenbank. Weitere Informationen finden Sie unter [Rückspeichern von Daten in der Datenbank](../data-tools/save-data-back-to-the-database.md).

## <a name="see-also"></a>Siehe auch

- [Binden von Windows Forms-Steuerelementen an Daten in Visual Studio](../data-tools/bind-windows-forms-controls-to-data-in-visual-studio.md)