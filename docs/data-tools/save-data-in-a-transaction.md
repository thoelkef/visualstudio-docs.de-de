---
title: 'Exemplarische Vorgehensweise: Speichern von Daten in einer Transaktion | Microsoft Docs'
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
- System.Transactions namespace
- data [Visual Studio], saving in a transaction
- transactions, saving data
- Transactions namespace
- saving data
ms.assetid: 80260118-08bc-4b37-bfe5-9422ee7a1e4e
caps.latest.revision: "15"
author: gewarren
ms.author: gewarren
manager: ghogen
ms.technology: vs-data-tools
ms.workload: data-storage
ms.openlocfilehash: 160cf1021e6b95dcfc6cf8ee97b20c4502f9099e
ms.sourcegitcommit: 49aa031cbebdd9c7ec070c713afb1a97d1ecb701
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 01/23/2018
---
# <a name="walkthrough-save-data-in-a-transaction"></a>Exemplarische Vorgehensweise: Speichern von Daten in einer Transaktion
Diese exemplarische Vorgehensweise veranschaulicht, wie zum Speichern von Daten in einer Transaktion mithilfe der <xref:System.Transactions> Namespace. In dieser exemplarischen Vorgehensweise erstellen Sie eine Windows Forms-Anwendung. Verwenden Sie den Konfigurations-Assistenten so erstellen ein Dataset für zwei Tabellen in der Northwind-Beispieldatenbank. Sie fügen datengebundene Steuerelemente auf einem Windows Form, und ändern Sie den Code für die BindingNavigators speichern Schaltfläche zum Aktualisieren der Datenbank innerhalb einer "TransactionScope".  
  
## <a name="prerequisites"></a>Erforderliche Komponenten  
In dieser exemplarischen Vorgehensweise werden die SQL Server Express LocalDB und der Beispieldatenbank Northwind verwendet.  
  
1.  Wenn Sie nicht über SQL Server Express LocalDB verfügen, installieren Sie es entweder aus der [Downloadseite für SQL Server Express](https://www.microsoft.com/sql-server/sql-server-editions-express), oder über die **Installer für Visual Studio**. In der Visual Studio-Installer können als Teil des SQL Server Express LocalDB installiert werden die **.NET Desktopentwicklung** arbeitsauslastung oder als eine einzelne Komponente.  
  
2.  Installieren Sie die Beispieldatenbank Northwind, indem folgende Schritte:  

    1. Öffnen Sie in Visual Studio die **Objekt-Explorer von SQL Server** Fenster. (Objekt-Explorer von SQL Server installiert ist, als Teil der **datenspeicherung und Verarbeitung** arbeitsauslastung in der Visual Studio-Installer.) Erweitern Sie die **SQL Server** Knoten. Rechtsklicken Sie auf der LocalDB-Instanz, und wählen Sie **neue Abfrage...** .  

       Ein Abfrage-Editorfenster wird geöffnet.  

    2. Kopieren der [Northwind Transact-SQL-Skript](https://github.com/MicrosoftDocs/visualstudio-docs/blob/master/docs/data-tools/samples/northwind.sql?raw=true) in die Zwischenablage. Dieses T-SQL-Skript die Northwind-Datenbank von Grund auf neu erstellt und mit Daten aufgefüllt.  

    3. Fügen Sie das T-SQL-Skript im Abfrage-Editor, und wählen Sie dann die **Execute** Schaltfläche.  

       Nach kurzer Zeit die Abfrage die Ausführung abgeschlossen ist, und die Northwind-Datenbank wird erstellt.  
  
## <a name="create-a-windows-forms-application"></a>Erstellen Sie eine Windows Forms-Anwendung  
 Der erste Schritt ist die Erstellung einer **Windows Forms-Anwendung**.  
  
#### <a name="to-create-the-new-windows-project"></a>So erstellen Sie ein neues Windows-Projekt  
  
1. In Visual Studio auf die **Datei** klicken Sie im Menü **neu**, **Projekt...** .  
  
2. Erweitern Sie entweder **Visual C#-** oder **Visual Basic** im linken Bereich, und wählen Sie dann **klassische Windows-Desktop**.  

3. Wählen Sie im mittleren Bereich die **Windows Forms-App** Projekttyp.  

4. Nennen Sie das Projekt **SavingDataInATransactionWalkthrough**, und wählen Sie dann **OK**. 
  
     Die **SavingDataInATransactionWalkthrough** Projekt wird erstellt und hinzugefügt **Projektmappen-Explorer**.  
  
## <a name="create-a-database-data-source"></a>Erstellen einer Datenbank-Datenquelle  
 Dieser Schritt wird mithilfe der **Datenquellen Konfigurations-Assistenten** So erstellen eine Datenquelle basierend auf der `Customers` und `Orders` Tabellen in der Northwind-Beispieldatenbank.  
  
#### <a name="to-create-the-data-source"></a>So erstellen Sie die Datenquelle  
  
1.  Auf der **Daten** klicken Sie im Menü **Datenquellen anzeigen**.  
  
2.  In der **Datenquellen** wählen **neue Datenquelle hinzufügen** zum Starten der **Datenquellen Konfigurations-Assistenten**.  
  
3.  Auf der **wählen Sie einen Datenquellentyp** wählen **Datenbank**, und wählen Sie dann **Weiter**.  
  
4.  Auf der **wählen Sie Ihre Datenverbindung** Bildschirm führen Sie einen der folgenden:  
  
    -   Wenn in der Dropdownliste eine Datenverbindung zur Beispieldatenbank „Northwind“ verfügbar ist, wählen Sie diese aus.  
  
         - oder -   
  
    -   Wählen Sie **neue Verbindung** zum Starten der **Verbindung hinzufügen/ändern** Dialogfeld Feld, und erstellen Sie eine Verbindung mit der Northwind-Datenbank.  
  
5.  Wenn die Datenbank ein Kennwort erfordern sollte, wählen Sie die Option auf Einbeziehung vertraulicher Daten, und wählen Sie dann **Weiter**.  
  
6.  Auf der **Verbindungszeichenfolge in der Programmkonfigurationsdatei speichern** wählen **Weiter**.  
  
7.  Auf der **Datenbankobjekte auswählen** Bildschirm, erweitern Sie die **Tabellen** Knoten.  
  
8.  Wählen Sie die `Customers` und `Orders` Tabellen, und wählen Sie dann **Fertig stellen**.  
  
     Die **NorthwindDataSet** wird dem Projekt hinzugefügt und die `Customers` und `Orders` Tabellen angezeigt werden, der **Datenquellen** Fenster.  
  
## <a name="add-controls-to-the-form"></a>Hinzufügen von Steuerelementen zum Formular  
 Sie können die datengebundenen Steuerelemente erstellen, durch Ziehen von Elementen aus der **Datenquellen** auf das Formular.  
  
#### <a name="to-create-data-bound-controls-on-the-windows-form"></a>So erstellen Sie datengebundene Steuerelemente auf dem Windows form  
  
-   In der **Datenquellen** Fenster, erweitern Sie die **Kunden** Knoten.  
  
-   Ziehen Sie den Hauptknoten **Kunden** Knoten aus der **Datenquellen** auf **Form1**.  
  
     Auf dem Formular wird ein <xref:System.Windows.Forms.DataGridView>-Steuerelement und ein Toolstrip (<xref:System.Windows.Forms.BindingNavigator>) für die Navigation in den Datensätzen angezeigt. Ein [NorthwindDataSet](../data-tools/dataset-tools-in-visual-studio.md), `CustomersTableAdapter`, <xref:System.Windows.Forms.BindingSource>, und <xref:System.Windows.Forms.BindingNavigator> auf der Komponentenleiste angezeigt.  
  
-   Ziehen Sie den zugehörigen **Aufträge** Knoten (nicht der Hauptknoten **Aufträge** Knoten, aber der zugehörige untergeordnete Tabellenknoten unter der **Fax** Spalte) auf das Formular unten die  **CustomersDataGridView**.  
  
     Ein <xref:System.Windows.Forms.DataGridView> wird auf dem Formular angezeigt. Ein `OrdersTableAdapter` und <xref:System.Windows.Forms.BindingSource> auf der Komponentenleiste angezeigt.  
  
## <a name="add-a-reference-to-the-systemtransactions-assembly"></a>Fügen Sie einen Verweis zur Assembly System.Transactions  
 Transaktionen verwenden den Namespace <xref:System.Transactions>. Eine Projektverweis zur Assembly system.transactions wird standardmäßig nicht hinzugefügt. Sie müssen das also manuell tun.  
  
#### <a name="to-add-a-reference-to-the-systemtransactions-dll-file"></a>So fügen Sie einen Verweis zur DLL-Datei System.Transactions hinzu  
  
1.  Auf der **Projekt** klicken Sie im Menü **Verweis hinzufügen**.  
  
2.  Wählen Sie **System.Transactions** (auf der **.NET** Registerkarte "), und wählen Sie dann **OK**.  
  
     Ein Verweis auf **System.Transactions** wird dem Projekt hinzugefügt.  
  
## <a name="modify-the-code-in-the-bindingnavigators-saveitem-button"></a>Ändern Sie den Code in der Schaltfläche BindingNavigator's SaveItem ändern  
 Für die erste auf dem Formular abgelegte Tabelle Code hinzugefügt, werden standardmäßig die `click` -Ereignis für das Speichern-Schaltfläche auf der <xref:System.Windows.Forms.BindingNavigator>. Sie müssen für das Ändern weiterer Tabellen den Code manuell hinzufügen. In dieser exemplarischen Vorgehensweise gestalten wir den vorhandenen speichern-Code aus den speichern Schaltfläche im click-Ereignishandler. Außerdem erstellen wir ein paar weitere Methoden zum Bereitstellen von spezifische änderungsfunktionalität auf, ob die Zeile hinzugefügt oder gelöscht werden muss.  
  
#### <a name="to-modify-the-auto-generated-save-code"></a>So ändern Sie automatisch generierten Speichern-Code  
  
1.  Wählen Sie die **speichern** Schaltfläche auf der **CustomersBindingNavigator** (die Schaltfläche mit dem Diskettensymbol).  
  
2.  Ersetzen Sie die `CustomersBindingNavigatorSaveItem_Click`-Methode durch folgenden Code:  
  
     [!code-vb[VbRaddataSaving#4](../data-tools/codesnippet/VisualBasic/save-data-in-a-transaction_1.vb)]
     [!code-csharp[VbRaddataSaving#4](../data-tools/codesnippet/CSharp/save-data-in-a-transaction_1.cs)]  
  
Der Befehl für das Abgleichen zugehöriger Daten lautet wie folgt:  
  
-   Löschen Sie untergeordnete Datensätze. (In diesem Fall Löschen von Datensätzen aus der `Orders` Tabelle.)  
  
-   Löschen Sie übergeordnete Datensätze. (In diesem Fall Löschen von Datensätzen aus der `Customers` Tabelle.)  
  
-   Übergeordnete Datensätze einfügen. (In diesem Fall Einfügen von Datensätzen in der `Customers` Tabelle.)  
  
-   Untergeordnete Datensätze einfügen. (In diesem Fall Einfügen von Datensätzen in der `Orders` Tabelle.)  
  
#### <a name="to-delete-existing-orders"></a>So löschen Sie eine vorhandene Bestellungen  
  
-   Fügen Sie die folgenden `DeleteOrders` aufzurufende Methode **Form1**:  
  
     [!code-vb[VbRaddataSaving#5](../data-tools/codesnippet/VisualBasic/save-data-in-a-transaction_2.vb)]
     [!code-csharp[VbRaddataSaving#5](../data-tools/codesnippet/CSharp/save-data-in-a-transaction_2.cs)]  
  
#### <a name="to-delete-existing-customers"></a>So löschen Sie eine vorhandene Kunden  
  
-   Fügen Sie die folgenden `DeleteCustomers` aufzurufende Methode **Form1**:  
  
     [!code-vb[VbRaddataSaving#6](../data-tools/codesnippet/VisualBasic/save-data-in-a-transaction_3.vb)]
     [!code-csharp[VbRaddataSaving#6](../data-tools/codesnippet/CSharp/save-data-in-a-transaction_3.cs)]  
  
#### <a name="to-add-new-customers"></a>Neue Kunden hinzufügen  
  
-   Fügen Sie die folgenden `AddNewCustomers` aufzurufende Methode **Form1**:  
  
     [!code-vb[VbRaddataSaving#7](../data-tools/codesnippet/VisualBasic/save-data-in-a-transaction_4.vb)]
     [!code-csharp[VbRaddataSaving#7](../data-tools/codesnippet/CSharp/save-data-in-a-transaction_4.cs)]  
  
#### <a name="to-add-new-orders"></a>Neue Bestellungen hinzufügen  
  
-   Fügen Sie die folgenden `AddNewOrders` aufzurufende Methode **Form1**:  
  
     [!code-vb[VbRaddataSaving#8](../data-tools/codesnippet/VisualBasic/save-data-in-a-transaction_5.vb)]
     [!code-csharp[VbRaddataSaving#8](../data-tools/codesnippet/CSharp/save-data-in-a-transaction_5.cs)]  
  
## <a name="run-the-application"></a>Ausführen der Anwendung  
  
#### <a name="to-run-the-application"></a>So führen Sie die Anwendung aus  
  
-   Wählen Sie **F5** um die Anwendung auszuführen.  
  
## <a name="see-also"></a>Siehe auch
[Vorgehensweise: Speichern von Daten mithilfe von Transaktionen](../data-tools/save-data-by-using-a-transaction.md)  
[Rückspeichern von Daten in der Datenbank](../data-tools/save-data-back-to-the-database.md)