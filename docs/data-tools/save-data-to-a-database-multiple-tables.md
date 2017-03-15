---
title: "Exemplarische Vorgehensweise: Speichern von Daten in einer Datenbank (mehrere Tabellen) | Microsoft Docs"
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
  - "Daten [Visual Studio], Speichern"
  - "Daten [Visual Studio], Aktualisieren"
  - "Speichern von Daten, Exemplarische Vorgehensweisen"
  - "Aktualisieren von Datasets, Exemplarische Vorgehensweisen"
ms.assetid: 7ebe03da-ce8c-4cbc-bac0-a2fde4ae4d07
caps.latest.revision: 24
caps.handback.revision: 20
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# Exemplarische Vorgehensweise: Speichern von Daten in einer Datenbank (mehrere Tabellen)
Eines der häufigsten Szenarios in der Anwendungsentwicklung ist das Anzeigen von Daten auf einem Formular in einer Windows\-Anwendung, das Bearbeiten der Daten und das Senden der aktualisierten Daten zurück an die Datenbank.  In dieser exemplarischen Vorgehensweise wird ein Formular erstellt, in dem Daten aus zwei verknüpften Tabellen angezeigt werden. Darüber hinaus wird gezeigt, wie Datensätze bearbeitet und Änderungen wieder in der Datenbank gespeichert werden.  In diesem Beispiel werden die Tabellen `Customers` und `Orders` aus der Beispieldatenbank Northwind verwendet.  
  
 Sie können Daten in der Anwendung wieder in der Datenbank speichern, indem Sie die `Update`\-Methode eines TableAdapter aufrufen.  Wenn Sie Elemente aus dem **Datenquellenfenster** ziehen, wird Code zum Speichern von Daten automatisch für die erste auf einem Formular abgelegte Tabelle hinzugefügt.  Für alle weiteren einem Formular hinzugefügten Tabellen muss der zum Speichern von Daten erforderliche Code manuell hinzugefügt werden.  In dieser exemplarischen Vorgehensweise wird veranschaulicht, wie Code hinzugefügt wird, um Aktualisierungen aus mehreren Tabellen zu speichern.  
  
> [!NOTE]
>  Je nach den aktiven Einstellungen oder der Version unterscheiden sich die Dialogfelder und Menübefehle auf Ihrem Bildschirm möglicherweise von den in der Hilfe beschriebenen.  Klicken Sie im Menü **Extras** auf **Einstellungen importieren und exportieren**, um die Einstellungen zu ändern.  Weitere Informationen finden Sie unter [Customizing Development Settings in Visual Studio](http://msdn.microsoft.com/de-de/22c4debb-4e31-47a8-8f19-16f328d7dcd3).  
  
 In dieser exemplarischen Vorgehensweise werden u. a. folgende Aufgaben veranschaulicht:  
  
-   Erstellen eines neuen Projekts vom Typ **Windows\-Anwendung**.  
  
-   Erstellen und Konfigurieren einer Datenquelle in der Anwendung mithilfe des [Assistent zum Konfigurieren von Datenquellen](../data-tools/media/data-source-configuration-wizard.png).  
  
-   Festlegen der Steuerelemente für die Elemente im [Datenquellenfenster](../Topic/Data%20Sources%20Window.md).  Weitere Informationen finden Sie unter [Festlegen des Steuerelements, das beim Ziehen aus dem Datenquellenfenster erstellt werden soll](../data-tools/set-the-control-to-be-created-when-dragging-from-the-data-sources-window.md).  
  
-   Erstellen datengebundener Steuerelemente durch Ziehen von Elementen aus dem **Datenquellenfenster** auf das Formular.  
  
-   Ändern mehrerer Datensätze in den einzelnen Tabellen im Dataset.  
  
-   Ändern von Code zum Zurücksenden der aktualisierten Daten des Datasets an die Datenbank.  
  
## Vorbereitungsmaßnahmen  
 Für die Durchführung dieser exemplarischen Vorgehensweise benötigen Sie Folgendes:  
  
-   Zugriff auf die Beispieldatenbank Northwind.  Weitere Informationen finden Sie unter [Gewusst wie: Installieren von Beispieldatenbanken](../data-tools/how-to-install-sample-databases.md).  
  
## Erstellen der Windows\-Anwendung  
 Im ersten Schritt wird eine **Windows\-Anwendung** erstellt.  Zu diesem Zeitpunkt ist es nicht erforderlich, dem Projekt einen Namen zuzuweisen. Wir führen diesen Schritt dennoch aus, weil wir das Projekt später speichern möchten.  
  
#### So erstellen Sie das neue Windows\-Anwendungsprojekt  
  
1.  Erstellen Sie über das Menü **Datei** ein neues Projekt.  
  
2.  Nennen Sie das Projekt `UpdateMultipleTablesWalkthrough`.  
  
3.  Wählen Sie **Windows\-Anwendung** aus, und klicken Sie auf **OK**.  Weitere Informationen finden Sie unter [Clientanwendungen](../Topic/Developing%20Client%20Applications%20with%20the%20.NET%20Framework.md).  
  
     Das Projekt **UpdateMultipleTablesWalkthrough** wird erstellt und dem **Projektmappen\-Explorer** hinzugefügt.  
  
## Erstellen der Datenquelle  
 In diesem Schritt wird mit dem **Assistenten zum Konfigurieren von Datenquellen** eine Datenquelle aus der Northwind\-Datenbank erstellt.  Sie benötigen Zugriff auf die Beispieldatenbank Northwind, um die Verbindung herstellen zu können.  Informationen zum Einrichten der Beispieldatenbank Northwind finden Sie unter [Gewusst wie: Installieren von Beispieldatenbanken](../data-tools/how-to-install-sample-databases.md).  
  
#### So erstellen Sie die Datenquelle  
  
1.  Klicken Sie im Menü **Daten** auf **Datenquellen anzeigen**.  
  
2.  Wählen Sie im **Datenquellenfenster** die Option **Neue Datenquelle hinzufügen** aus, um den **Assistenten zum Konfigurieren von Datenquellen** zu starten.  
  
3.  Wählen Sie auf der Seite **Datenquellentyp auswählen** die Option **Datenbank** aus, und klicken Sie auf **Weiter**.  
  
4.  Führen Sie auf der Seite **Wählen Sie Ihre Datenverbindung** einen der folgenden Schritte aus:  
  
    -   Wenn in der Dropdownliste eine Datenverbindung zur Beispieldatenbank "Northwind" verfügbar ist, wählen Sie diese aus.  
  
         \- oder \-  
  
    -   Wählen Sie **Neue Verbindung** aus, um das Dialogfeld **Verbindung hinzufügen\/ändern** zu öffnen.  
  
5.  Falls die Datenbank ein Kennwort erfordern sollte, aktivieren Sie die Option für die Einbeziehung vertraulicher Daten, und klicken Sie dann auf **Weiter**.  
  
6.  Klicken Sie auf der Seite **Verbindungszeichenfolge in der Programmkonfigurationsdatei speichern** auf **Weiter**.  
  
7.  Erweitern Sie auf der Seite **Datenbankobjekte auswählen** den Knoten **Tabellen**.  
  
8.  Wählen Sie die Tabellen **Kunden** und **Bestellungen** aus, und klicken Sie dann auf **Fertig stellen**.  
  
     **NorthwindDataSet** wird dem Projekt hinzugefügt. Die Tabellen werden im **Datenquellenfenster** angezeigt.  
  
## Festlegen der zu erstellenden Steuerelemente  
 In dieser exemplarischen Vorgehensweise befinden sich die Daten der `Customers`\-Tabelle in einem **Details**\-Layout, in dem die Daten in einzelnen Steuerelementen angezeigt werden.  Die Daten aus der Tabelle `Orders` befinden sich in einem **Rasterlayout**, das in einem <xref:System.Windows.Forms.DataGridView>\-Steuerelement angezeigt wird.  
  
#### So legen Sie den Ablagetyp für die Elemente im Datenquellenfenster fest  
  
1.  Erweitern Sie im **Datenquellenfenster** den Knoten **Customers**.  
  
2.  Ändern Sie das Steuerelement der Tabelle **Customers** in einzelne Steuerelemente, indem Sie **Details** in der Steuerelementliste des Knotens **Customers** auswählen.  Weitere Informationen finden Sie unter [Festlegen des Steuerelements, das beim Ziehen aus dem Datenquellenfenster erstellt werden soll](../data-tools/set-the-control-to-be-created-when-dragging-from-the-data-sources-window.md).  
  
## Erstellen des datengebundenen Formulars  
 Sie können die datengebundenen Steuerelemente erstellen, indem Sie Elemente aus dem **Datenquellenfenster** auf das Formular ziehen.  
  
#### So erstellen Sie datengebundene Steuerelemente auf dem Formular  
  
1.  Ziehen Sie den Hauptknoten **Customers** aus dem **Datenquellenfenster** auf **Form1**.  
  
     Auf dem Formular werden datengebundene Steuerelemente mit beschreibenden Bezeichnungen sowie ein Toolstrip \(<xref:System.Windows.Forms.BindingNavigator>\) für die Navigation in den Datensätzen angezeigt.  [NorthwindDataSet](../data-tools/dataset-tools-in-visual-studio.md), [CustomersTableAdapter](../data-tools/tableadapter-overview.md), <xref:System.Windows.Forms.BindingSource> und <xref:System.Windows.Forms.BindingNavigator> werden auf der Komponentenleiste angezeigt.  
  
2.  Ziehen Sie den Knoten **Orders** aus dem **Datenquellenfenster** in **Form1**.  
  
    > [!NOTE]
    >  Der verknüpfte Knoten **Orders** befindet sich unter der Spalte **Fax** und ist ein untergeordneter Knoten des Knotens **Customers**.  
  
     Auf dem Formular wird ein <xref:System.Windows.Forms.DataGridView>\-Steuerelement und ein Toolstrip \(<xref:System.Windows.Forms.BindingNavigator>\) für die Navigation in den Datensätzen angezeigt.  [OrdersTableAdapter](../data-tools/tableadapter-overview.md) und <xref:System.Windows.Forms.BindingSource> werden auf der Komponentenleiste angezeigt.  
  
## Hinzufügen von Code zum Aktualisieren der Datenbank  
 Sie können die Datenbank aktualisieren, indem Sie die `Update`\-Methoden der TableAdapters von **Customers** und **Orders** aufrufen.  Ein Ereignishandler für die <xref:System.Windows.Forms.BindingNavigator>\-Schaltfläche **Speichern** wird standardmäßig zum Code des Formulars hinzugefügt, damit Aktualisierungen an die Datenbank gesendet werden.  Mit dieser Prozedur wird der Code geändert und sichergestellt, dass Aktualisierungen in der richtigen Reihenfolge gesendet und mögliche Fehler der referenziellen Integrität verhindert werden.  Mit dem Code wird außerdem die Fehlerbehandlung implementiert, indem der Aktualisierungsaufruf mit einem Try\-Catch\-Block umschlossen wird.  Sie können den Code entsprechend den Anforderungen der Anwendung anpassen.  
  
> [!NOTE]
>  Aus Gründen der Übersichtlichkeit wird in dieser exemplarischen Vorgehensweise keine Transaktion verwendet. Wenn Sie jedoch zwei oder mehr verbundene Tabellen aktualisieren, müssen Sie die gesamte Aktualisierungslogik in eine Transaktion aufnehmen.  Eine Transaktion ist ein Prozess, der sicherstellt, dass alle zugehörigen Änderungen an einer Datenbank erfolgreich sind, bevor ein Commit für eine der Änderungen ausgeführt wird.  Weitere Informationen finden Sie unter [Transaktionen und Parallelität](../Topic/Transactions%20and%20Concurrency.md).  
  
#### So fügen Sie der Anwendung Aktualisierungslogik hinzu  
  
1.  Doppelklicken Sie auf dem <xref:System.Windows.Forms.BindingNavigator> auf die Schaltfläche **Speichern**, um den Code\-Editor für den `bindingNavigatorSaveItem_Click`\-Ereignishandler zu öffnen.  
  
2.  Ändern Sie den Code im Ereignishandler, sodass die `Update`\-Methoden der verknüpften TableAdapters aufgerufen werden.  Mit folgendem Code werden zunächst drei temporäre Datentabellen zum Speichern der aktualisierten Informationen für jeden <xref:System.Data.DataRowState> \(<xref:System.Data.DataRowState>, <xref:System.Data.DataRowState> und <xref:System.Data.DataRowState>\) erstellt.  Anschließend werden die Aktualisierungen in der richtigen Reihenfolge vorgenommen.  Der Code sollte wie folgt aussehen:  
  
     [!code-vb[VbRaddataSaving#10](../data-tools/codesnippet/VisualBasic/save-data-to-a-database-multiple-tables_1.vb)]
     [!code-cs[VbRaddataSaving#10](../data-tools/codesnippet/CSharp/save-data-to-a-database-multiple-tables_1.cs)]  
  
## Testen der Anwendung  
  
#### So testen Sie die Anwendung  
  
1.  Drücken Sie F5.  
  
2.  Nehmen Sie in jeder Tabelle einige Änderungen an den Daten eines oder mehrerer Datensätze vor.  
  
3.  Klicken Sie auf die Schaltfläche **Speichern**.  
  
4.  Überprüfen Sie die Werte in der Datenbank, um sicherzustellen, dass die Änderungen gespeichert wurden.  
  
## Nächste Schritte  
 Je nach den Anforderungen der Anwendung können nach dem Erstellen eines datengebundenen Formulars in der Windows\-Anwendung weitere Schritte sinnvoll sein.  Sie können an dieser exemplarischen Vorgehensweise beispielsweise folgende Verbesserungen vornehmen:  
  
-   Fügen Sie dem Formular Suchfunktionalität hinzu.  Weitere Informationen finden Sie unter [Gewusst wie: Hinzufügen einer parametrisierten Abfrage zu einem Formular in einer Windows Forms\-Anwendung](../Topic/How%20to:%20Add%20a%20Parameterized%20Query%20to%20a%20Windows%20Forms%20Application.md).  
  
-   Bearbeiten der Datenquelle zum Hinzufügen oder Entfernen von Datenbankobjekten.  Weitere Informationen finden Sie unter [Gewusst wie: Bearbeiten eines Datasets](../Topic/How%20to:%20Edit%20a%20Dataset.md).  
  
## Siehe auch  
 [Exemplarische Vorgehensweisen zur Arbeit mit Daten](../Topic/Data%20Walkthroughs.md)   
 [Binden von Windows Forms\-Steuerelementen an Daten in Visual Studio](../data-tools/bind-windows-forms-controls-to-data-in-visual-studio.md)   
 [Übersicht über Datenanwendungen in Visual Studio](../data-tools/overview-of-data-applications-in-visual-studio.md)   
 [Herstellen von Datenverbindungen in Visual Studio](../data-tools/connecting-to-data-in-visual-studio.md)   
 [Vorbereiten der Anwendung auf den Empfang von Daten](../Topic/Preparing%20Your%20Application%20to%20Receive%20Data.md)   
 [Abrufen von Daten für die Anwendung](../data-tools/fetching-data-into-your-application.md)   
 [Binden von Steuerelementen an Daten in Visual Studio](../data-tools/bind-controls-to-data-in-visual-studio.md)   
 [Bearbeiten von Daten in der Anwendung](../data-tools/editing-data-in-your-application.md)   
 [Überprüfen von Daten](../Topic/Validating%20Data.md)   
 [Speichern von Daten](../data-tools/saving-data.md)