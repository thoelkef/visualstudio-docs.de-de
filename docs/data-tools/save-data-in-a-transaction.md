---
title: "Exemplarische Vorgehensweise: Speichern von Daten im Rahmen einer Transaktion | Microsoft Docs"
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
  - "Daten [Visual Studio], Speichern in einer Transaktion"
  - "Speichern von Daten"
  - "System.Transactions-Namespace"
  - "Transactions-Namespace"
  - "Transaktionen, Speichern von Daten"
ms.assetid: 80260118-08bc-4b37-bfe5-9422ee7a1e4e
caps.latest.revision: 15
caps.handback.revision: 11
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# Exemplarische Vorgehensweise: Speichern von Daten im Rahmen einer Transaktion
Diese exemplarische Vorgehensweise zeigt, wie man Daten in einer Transaktion mithilfe des <xref:System.Transactions> Namespace speichert.  In diesem Beispiel werden die Tabellen `Customers` und `Orders` aus der Beispieldatenbank Northwind verwendet.  
  
## Vorbereitungsmaßnahmen  
 Für diese exemplarische Vorgehensweise wird die Beispieldatenbank Northwind benötigt.  Informationen zum Einrichten der Beispieldatenbank Northwind finden Sie unter [Gewusst wie: Installieren von Beispieldatenbanken](../data-tools/how-to-install-sample-databases.md).  
  
## Erstellen einer Windows\-Anwendung  
 Im ersten Schritt wird eine **Windows\-Anwendung** erstellt.  
  
#### So erstellen Sie ein neues Windows\-Projekt  
  
1.  Erstellen Sie in Visual Studio im Menü **Datei** ein neues **Projekt**.  
  
2.  Geben Sie dem Projekt den Namen SavingDataInATransactionWalkthrough.  
  
3.  Wählen Sie **Windows\-Anwendung** aus, und klicken Sie auf **OK**.  Weitere Informationen finden Sie unter [Clientanwendungen](../Topic/Developing%20Client%20Applications%20with%20the%20.NET%20Framework.md).  
  
     Das Projekt **SavingDataInATransactionWalkthrough** wird erstellt und zum **Projektmappen\-Explorer** hinzugefügt.  
  
## Erstellen einer Datenbank\-Datenquelle  
 Dieser Schritt verwendet den [Assistent zum Konfigurieren von Datenquellen](../data-tools/media/data-source-configuration-wizard.png) auf Grundlage der Tabellen `Customers` und `Orders` in der Beispieldatenbank Northwind.  
  
#### So erstellen Sie die Datenquelle  
  
1.  Klicken Sie im Menü **Daten** auf **Datenquellen anzeigen**.  
  
2.  Wählen Sie im **Datenquellenfenster** die Option **Neue Datenquelle hinzufügen** aus, um den **Assistenten zum Konfigurieren von Datenquellen** zu starten.  
  
3.  Wählen Sie auf der Seite **Datenquellentyp auswählen** die Option **Datenbank** aus, und klicken Sie auf **Weiter**.  
  
4.  Führen Sie auf der Seite **Wählen Sie Ihre Datenverbindung** einen der folgenden Schritte aus:  
  
    -   Wenn in der Dropdownliste eine Datenverbindung zur Beispieldatenbank "Northwind" verfügbar ist, wählen Sie diese aus.  
  
         \- oder \-  
  
    -   Wählen Sie **Neue Verbindung**, starten Sie das Dialogfeld **Verbindung hinzufügen\/ändern** und erstellen Sie eine Verbindung mit der Datenbank Northwind.  
  
5.  Falls die Datenbank ein Kennwort erfordern sollte, aktivieren Sie die Option für die Einbeziehung vertraulicher Daten, und klicken Sie dann auf **Weiter**.  
  
6.  Klicken Sie auf der Seite **Verbindungszeichenfolge in der Programmkonfigurationsdatei speichern** auf **Weiter**.  
  
7.  Erweitern Sie auf der Seite **Datenbankobjekte auswählen** den Knoten **Tabellen**.  
  
8.  Wählen Sie die Tabellen `Customers` und `Orders` aus, und klicken Sie dann auf **Fertig stellen**.  
  
     Das **NorthwindDataSet** wird Ihrem Projekt hinzugefügt, und die Tabellen `Customers` und `Orders` werden im **Datenquellenfenster** angezeigt.  
  
## Hinzufügen von Steuerelementen zum Formular  
 Sie können die datengebundenen Steuerelemente erstellen, indem Sie Elemente aus dem **Datenquellenfenster** auf das Formular ziehen.  
  
#### So erstellen Sie datengebundene Steuerelemente auf dem Windows Form  
  
-   Erweitern Sie im **Datenquellenfenster** den Knoten **Customers**.  
  
-   Ziehen Sie den Hauptknoten **Customers** aus dem **Datenquellenfenster** auf **Form1**.  
  
     Auf dem Formular wird ein <xref:System.Windows.Forms.DataGridView>\-Steuerelement und ein Toolstrip \(<xref:System.Windows.Forms.BindingNavigator>\) für die Navigation in den Datensätzen angezeigt.  [NorthwindDataSet](../data-tools/dataset-tools-in-visual-studio.md), [CustomersTableAdapter](../data-tools/tableadapter-overview.md), <xref:System.Windows.Forms.BindingSource> und <xref:System.Windows.Forms.BindingNavigator> werden auf der Komponentenleiste angezeigt.  
  
-   Ziehen Sie den zugehörigen Knoten **Orders** \(der zugehörige untergeordnete Tabellenknoten unter der Spalte **Fax**, nicht der Hauptknoten **Orders**\) auf das Formular unter **CustomersDataGridView**.  
  
     Ein <xref:System.Windows.Forms.DataGridView> wird auf dem Formular angezeigt.  [OrdersTableAdapter](../data-tools/tableadapter-overview.md) und <xref:System.Windows.Forms.BindingSource> werden auf der Komponentenleiste angezeigt.  
  
## Hinzufügen einer Referenz zur Assembly system.transactions  
 Transaktionen verwenden den Namespace <xref:System.Transactions>.  Eine Projektverweis zur Assembly system.transactions wird standardmäßig nicht hinzugefügt. Sie müssen das also manuell tun.  
  
#### So fügen Sie einen Verweis zur DLL\-Datei System.Transactions hinzu  
  
1.  Wählen Sie im Menü **Projekt** den Punkt **Verweis hinzufügen**.  
  
2.  Wählen Sie**System.Transactions** \(auf der Registerkarte **.NET**\) und klicken Sie **OK**.  
  
     Dem Projekt wird ein Verweis auf **System.Transactions** hinzugefügt.  
  
## Den Code in der Schaltfläche BindingNavigator's SaveItem ändern  
 Standardmäßig wird für die erste auf dem Formular abgelegte Tabelle Code dem `click`\-Ereignis der Schaltfläche "Speichern" auf dem <xref:System.Windows.Forms.BindingNavigator> hinzugefügt.  Sie müssen für das Ändern weiterer Tabellen den Code manuell hinzufügen.  In dieser exemplarischen Vorgehensweise gestalten wir den vorhandenen Speichern\-Code aus dem Click\-Ereignishandler der Schaltfläche "Speichern" und erstellen ein paar weitere Methoden, um spezifische Änderungsfunktionalität abhängig davon zur Verfügung zu stellen, ob die Zeile hinzugefügt oder gelöscht werden soll.  
  
#### So ändern Sie automatisch generierten Speichern\-Code  
  
1.  Doppelklicken Sie die Schaltfläche **Speichern** auf dem **CustomersBindingNavigator** \(die Schaltfläche mit dem Diskettensymbol\).  
  
2.  Ersetzen Sie die `CustomersBindingNavigatorSaveItem_Click`\-Methode durch folgenden Code:  
  
     [!code-vb[VbRaddataSaving#4](../data-tools/codesnippet/VisualBasic/save-data-in-a-transaction_1.vb)]
     [!code-cs[VbRaddataSaving#4](../data-tools/codesnippet/CSharp/save-data-in-a-transaction_1.cs)]  
  
 Der Befehl für das Abgleichen zugehöriger Daten lautet wie folgt:  
  
-   Untergeordnete Datensätze löschen \(in diesem Fall: Datensätze aus der Tabelle `Orders` löschen\)  
  
-   Übergeordnete Datensätze löschen \(in diesem Fall: Datensätze aus der Tabelle `Customers` löschen\)  
  
-   Übergeordnete Datensätze einfügen \(in diesem Fall: Datensätze in die Tabelle `Customers` einfügen\)  
  
-   Untergeordnete Datensätze einfügen \(in diesem Fall: Datensätze in die Tabelle `Orders` einfügen\)  
  
#### So löschen Sie eine vorhandene Bestellungen  
  
-   Fügen Sie die folgende Methode `DeleteOrders` zu **Form1** hinzu:  
  
     [!code-vb[VbRaddataSaving#5](../data-tools/codesnippet/VisualBasic/save-data-in-a-transaction_2.vb)]
     [!code-cs[VbRaddataSaving#5](../data-tools/codesnippet/CSharp/save-data-in-a-transaction_2.cs)]  
  
#### So löschen Sie eine vorhandene Kunden  
  
-   Fügen Sie die folgende Methode `DeleteCustomers` zu **Form1** hinzu:  
  
     [!code-vb[VbRaddataSaving#6](../data-tools/codesnippet/VisualBasic/save-data-in-a-transaction_3.vb)]
     [!code-cs[VbRaddataSaving#6](../data-tools/codesnippet/CSharp/save-data-in-a-transaction_3.cs)]  
  
#### Neue Kunden hinzufügen  
  
-   Fügen Sie die folgende Methode `AddNewCustomers` zu **Form1** hinzu:  
  
     [!code-vb[VbRaddataSaving#7](../data-tools/codesnippet/VisualBasic/save-data-in-a-transaction_4.vb)]
     [!code-cs[VbRaddataSaving#7](../data-tools/codesnippet/CSharp/save-data-in-a-transaction_4.cs)]  
  
#### Neue Bestellungen hinzufügen  
  
-   Fügen Sie die folgende Methode `AddNewOrders` zu **Form1** hinzu:  
  
     [!code-vb[VbRaddataSaving#8](../data-tools/codesnippet/VisualBasic/save-data-in-a-transaction_5.vb)]
     [!code-cs[VbRaddataSaving#8](../data-tools/codesnippet/CSharp/save-data-in-a-transaction_5.cs)]  
  
## Ausführen der Anwendung  
  
#### So führen Sie die Anwendung aus  
  
-   Drücken Sie F5, um die Anwendung auszuführen.  
  
## Siehe auch  
 [Transaktionen und Parallelität](../Topic/Transactions%20and%20Concurrency.md)   
 [Verteilte Oracle\-Transaktionen](../Topic/Oracle%20Distributed%20Transactions.md)   
 [Gewusst wie: Speichern von Daten mithilfe von Transaktionen](../data-tools/save-data-by-using-a-transaction.md)   
 [System.Transactions\-Integration in SQL Server](../Topic/System.Transactions%20Integration%20with%20SQL%20Server.md)   
 [Herstellen von Datenverbindungen in Visual Studio](../data-tools/connecting-to-data-in-visual-studio.md)   
 [Vorbereiten der Anwendung auf den Empfang von Daten](../Topic/Preparing%20Your%20Application%20to%20Receive%20Data.md)   
 [Abrufen von Daten für die Anwendung](../data-tools/fetching-data-into-your-application.md)   
 [Binden von Steuerelementen an Daten in Visual Studio](../data-tools/bind-controls-to-data-in-visual-studio.md)   
 [Bearbeiten von Daten in der Anwendung](../data-tools/editing-data-in-your-application.md)   
 [Überprüfen von Daten](../Topic/Validating%20Data.md)   
 [Speichern von Daten](../data-tools/saving-data.md)