---
title: 'Exemplarische Vorgehensweise: Speichern von Daten im Rahmen einer Transaktion'
ms.date: 09/08/2017
ms.topic: conceptual
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- System.Transactions namespace
- data [Visual Studio], saving in a transaction
- transactions, saving data
- Transactions namespace
- saving data
ms.assetid: 80260118-08bc-4b37-bfe5-9422ee7a1e4e
author: gewarren
ms.author: gewarren
manager: jillfra
ms.workload:
- data-storage
ms.openlocfilehash: fc2626ba0efab60921ed721b9f06fec28c66f58b
ms.sourcegitcommit: 21d667104199c2493accec20c2388cf674b195c3
ms.translationtype: MTE95
ms.contentlocale: de-DE
ms.lasthandoff: 02/08/2019
ms.locfileid: "55932273"
---
# <a name="walkthrough-save-data-in-a-transaction"></a>Exemplarische Vorgehensweise: Speichern von Daten im Rahmen einer Transaktion

In dieser exemplarischen Vorgehensweise wird veranschaulicht, wie zum Speichern von Daten in einer Transaktion mithilfe der <xref:System.Transactions> Namespace. In dieser exemplarischen Vorgehensweise erstellen Sie eine Windows Forms-Anwendung. Verwenden Sie den Konfigurations-Assistenten zum Erstellen eines Datasets für zwei Tabellen in der Beispieldatenbank Northwind. Fügen Sie datengebundene Steuerelemente zu einem Windows-Formular, und ändern Sie den Code für des BindingNavigator Schaltfläche "Speichern" beim Aktualisieren der Datenbank in ein TransactionScope-Objekt.

## <a name="prerequisites"></a>Erforderliche Komponenten

In dieser exemplarischen Vorgehensweise verwendet SQL Server Express LocalDB und der Beispieldatenbank Northwind.

1.  Wenn Sie SQL Server Express LocalDB nicht haben, installieren Sie es entweder über die [Downloadseite für SQL Server Express](https://www.microsoft.com/sql-server/sql-server-editions-express), oder über die **Visual Studio-Installer**. In Visual Studio-Installer, SQL Server Express LocalDB installiert werden können, als Teil der **.NET Desktopentwicklung** Workload oder als eine einzelne Komponente.

2.  Installieren der Northwind-Beispieldatenbank mit folgenden Schritten:

    1. Öffnen Sie in Visual Studio die **Objekt-Explorer von SQL Server** Fenster. (Objekt-Explorer von SQL Server installiert ist, als Teil der **datenspeicherung und-Verarbeitung** Workload im Visual Studio-Installer.) Erweitern Sie die **SQL Server** Knoten. Mit der rechten Maustaste auf der LocalDB-Instanz, und wählen Sie **neue Abfrage**.

       Ein Abfrage-Editor-Fenster wird geöffnet.

    2. Kopieren der [Northwind Transact-SQL-Skript](https://github.com/MicrosoftDocs/visualstudio-docs/blob/master/docs/data-tools/samples/northwind.sql?raw=true) in die Zwischenablage. Dieses T-SQL-Skript wird die Northwind-Datenbank von Grund auf neu erstellt und mit Daten aufgefüllt.

    3. Fügen Sie das T-SQL-Skript im Abfrage-Editor, und wählen Sie dann die **Execute** Schaltfläche.

       Klicken Sie nach kurzer Zeit die Ausführung die Abfrage abgeschlossen ist, und die Northwind-Datenbank wird erstellt.

## <a name="create-a-windows-forms-application"></a>Erstellen einer Windows Forms-Anwendung

Der erste Schritt ist die Erstellung einer **Windows Forms-Anwendung**.

1. In Visual Studio auf die **Datei** , wählen Sie im Menü **neu** > **Projekt**.

2. Erweitern Sie entweder **Visual C#**  oder **Visual Basic** wählen Sie im linken Bereich **Windows Desktop**.

3. Wählen Sie im mittleren Bereich die **Windows Forms-App** Projekttyp.

4. Nennen Sie das Projekt **SavingDataInATransactionWalkthrough**, und wählen Sie dann **OK**.

     Das Projekt **SavingDataInATransactionWalkthrough** wird erstellt und zum **Projektmappen-Explorer** hinzugefügt.

## <a name="create-a-database-data-source"></a>Erstellen einer Datenbank-Datenquelle

Dieser Schritt verwendet den **Assistenten zur Datenquellenkonfiguration** zum Erstellen einer Datenquelle basierend auf den `Customers` und `Orders` Tabellen in der Beispieldatenbank Northwind.

1.  Zum Öffnen der **Datenquellen** Fenster auf die **Daten** , wählen Sie im Menü **Datenquellen anzeigen**.

2.  Wählen Sie im **Datenquellenfenster** die Option **Neue Datenquelle hinzufügen** aus, um den **Assistenten zum Konfigurieren von Datenquellen** zu starten.

3.  Auf der **wählen Sie einen Datenquellentyp** auf **Datenbank**, und wählen Sie dann **Weiter**.

4.  Auf der **wählen Sie Ihre Datenverbindung** Bildschirm führen Sie einen der folgenden:

    -   Wenn in der Dropdownliste eine Datenverbindung zur Beispieldatenbank „Northwind“ verfügbar ist, wählen Sie diese aus.

         - oder - 

    -   Klicken Sie auf **neue Verbindung**, um das Dialogfeld **Add/Modify Connection** (Verbindung hinzufügen/ändern) zu starten und eine Verbindung mit der Datenbank Northwind herzustellen.

5.  Wenn Ihre Datenbank ein Kennwort erfordert, wählen Sie die Option Einbeziehung vertraulicher Daten, und wählen Sie dann **Weiter**.

6.  Auf der **Verbindungszeichenfolge in der Programmkonfigurationsdatei speichern** auf **Weiter**.

7.  Auf der **Datenbankobjekte auswählen** Bildschirm, erweitern Sie die **Tabellen** Knoten.

8.  Wählen Sie die `Customers` und `Orders` Tabellen, und wählen Sie dann **Fertig stellen**.

     Das **NorthwindDataSet** wird Ihrem Projekt hinzugefügt, und die Tabellen `Customers` und `Orders` werden im Fenster **Datenquellen** angezeigt.

## <a name="add-controls-to-the-form"></a>Hinzufügen von Steuerelementen zu dem Formular

Sie können die datengebundenen Steuerelemente erstellen, indem Sie Elemente aus dem Fenster **Datenquellen** auf das Formular ziehen.

1. In der **Datenquellen** Fenster, erweitern Sie die **Kunden** Knoten.

2. Ziehen Sie den Hauptknoten **Customers** aus dem Fenster **Datenquellen** auf **Form1**.

   Auf dem Formular wird ein <xref:System.Windows.Forms.DataGridView>-Steuerelement und ein Toolstrip (<xref:System.Windows.Forms.BindingNavigator>) für die Navigation in den Datensätzen angezeigt. Ein [NorthwindDataSet](../data-tools/dataset-tools-in-visual-studio.md), `CustomersTableAdapter`, <xref:System.Windows.Forms.BindingSource>, und <xref:System.Windows.Forms.BindingNavigator> werden in der Komponentenleiste angezeigt.

3. Ziehen Sie den zugehörigen **Bestellungen** Knoten (nicht der Hauptknoten **Bestellungen** Knoten, aber die verknüpfte untergeordnete Tabellenknoten unter der **Fax** Spalte) auf das Formular unten die  **CustomersDataGridView**.

   Ein <xref:System.Windows.Forms.DataGridView> wird auf dem Formular angezeigt. Ein `OrdersTableAdapter` und <xref:System.Windows.Forms.BindingSource> werden in der Komponentenleiste angezeigt.

## <a name="add-a-reference-to-the-systemtransactions-assembly"></a>Fügen Sie einen Verweis zur Assembly System.Transactions

Transaktionen verwenden den Namespace <xref:System.Transactions>. Eine Projektverweis zur Assembly system.transactions wird standardmäßig nicht hinzugefügt. Sie müssen das also manuell tun.

### <a name="to-add-a-reference-to-the-systemtransactions-dll-file"></a>So fügen Sie einen Verweis zur DLL-Datei System.Transactions hinzu

1.  Auf der **Projekt** , wählen Sie im Menü **Verweis hinzufügen**.

2.  Wählen Sie **System.Transactions** (auf der **.NET** Registerkarte), und wählen Sie dann **OK**.

     Dem Projekt wird ein Verweis auf **System.Transactions** hinzugefügt.

## <a name="modify-the-code-in-the-bindingnavigators-saveitem-button"></a>Ändern Sie den Code in die SaveItem-Schaltfläche

Für die erste auf dem Formular abgelegte Tabelle Code hinzugefügt, werden standardmäßig die `click` Ereignis speichern-Schaltfläche auf der <xref:System.Windows.Forms.BindingNavigator>. Sie müssen für das Ändern weiterer Tabellen den Code manuell hinzufügen. In dieser exemplarischen Vorgehensweise gestalten wir den vorhandenen speichern-Code aus der Save-click-Ereignishandler der Schaltfläche. Außerdem erstellen wir ein paar weitere Methoden zum Bereitstellen von spezifische änderungsfunktionalität basierend auf, ob die Zeile hinzugefügt oder gelöscht werden muss.

### <a name="to-modify-the-auto-generated-save-code"></a>So ändern Sie automatisch generierten Speichern-Code

1.  Wählen Sie die **speichern** Schaltfläche der **CustomersBindingNavigator** (die Schaltfläche mit dem Diskettensymbol).

2.  Ersetzen Sie die `CustomersBindingNavigatorSaveItem_Click`-Methode durch folgenden Code:

     [!code-vb[VbRaddataSaving#4](../data-tools/codesnippet/VisualBasic/save-data-in-a-transaction_1.vb)]
     [!code-csharp[VbRaddataSaving#4](../data-tools/codesnippet/CSharp/save-data-in-a-transaction_1.cs)]

Der Befehl für das Abgleichen zugehöriger Daten lautet wie folgt:

-   Löschen Sie untergeordnete Datensätze. (In diesem Fall Löschen von Datensätzen aus der `Orders` Tabelle.)

-   Löschen Sie übergeordnete Datensätze. (In diesem Fall Löschen von Datensätzen aus der `Customers` Tabelle.)

-   Übergeordnete Datensätze einfügen. (In diesem Fall Einfügen von Datensätzen in der `Customers` Tabelle.)

-   Untergeordnete Datensätze einfügen. (In diesem Fall Einfügen von Datensätzen in der `Orders` Tabelle.)

### <a name="to-delete-existing-orders"></a>So löschen Sie eine vorhandene Bestellungen

-   Fügen Sie die folgende Methode `DeleteOrders` zu **Form1** hinzu:

     [!code-vb[VbRaddataSaving#5](../data-tools/codesnippet/VisualBasic/save-data-in-a-transaction_2.vb)]
     [!code-csharp[VbRaddataSaving#5](../data-tools/codesnippet/CSharp/save-data-in-a-transaction_2.cs)]

### <a name="to-delete-existing-customers"></a>So löschen Sie eine vorhandene Kunden

-   Fügen Sie die folgende Methode `DeleteCustomers` zu **Form1** hinzu:

     [!code-vb[VbRaddataSaving#6](../data-tools/codesnippet/VisualBasic/save-data-in-a-transaction_3.vb)]
     [!code-csharp[VbRaddataSaving#6](../data-tools/codesnippet/CSharp/save-data-in-a-transaction_3.cs)]

### <a name="to-add-new-customers"></a>Neue Kunden hinzufügen

-   Fügen Sie die folgende Methode `AddNewCustomers` zu **Form1** hinzu:

     [!code-vb[VbRaddataSaving#7](../data-tools/codesnippet/VisualBasic/save-data-in-a-transaction_4.vb)]
     [!code-csharp[VbRaddataSaving#7](../data-tools/codesnippet/CSharp/save-data-in-a-transaction_4.cs)]

### <a name="to-add-new-orders"></a>Neue Bestellungen hinzufügen

-   Fügen Sie die folgende Methode `AddNewOrders` zu **Form1** hinzu:

     [!code-vb[VbRaddataSaving#8](../data-tools/codesnippet/VisualBasic/save-data-in-a-transaction_5.vb)]
     [!code-csharp[VbRaddataSaving#8](../data-tools/codesnippet/CSharp/save-data-in-a-transaction_5.cs)]

## <a name="run-the-application"></a>Ausführen der Anwendung

Drücken Sie **F5**, um die Anwendung auszuführen.

## <a name="see-also"></a>Siehe auch

- [How to: save data by using a transaction (Vorgehensweise: Speichern von Daten mithilfe einer Transaktion)](../data-tools/save-data-by-using-a-transaction.md)
- [Rückspeichern von Daten in der Datenbank](../data-tools/save-data-back-to-the-database.md)