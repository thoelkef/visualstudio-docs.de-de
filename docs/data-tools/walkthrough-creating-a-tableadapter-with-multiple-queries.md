---
title: "Exemplarische Vorgehensweise: Erstellen eines TableAdapter mit mehreren Abfragen | Microsoft Docs"
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
  - "Daten [Visual Studio], TableAdapters"
  - "Daten [Visual Studio], Exemplarische Vorgehensweisen"
  - "Abfragen [Visual Studio], TableAdapters"
  - "TableAdapter-Abfragen, Erstellen"
  - "TableAdapters, Erstellen"
ms.assetid: f784dc4d-d514-4ade-8226-f8271c5b1ed8
caps.latest.revision: 18
caps.handback.revision: 18
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
robots: noindex,nofollow
---
# Exemplarische Vorgehensweise: Erstellen eines TableAdapter mit mehreren Abfragen
In dieser exemplarischen Vorgehensweise erstellen Sie mit dem [Assistent zum Konfigurieren von Datenquellen](../data-tools/media/data-source-configuration-wizard.png) einen TableAdapter in einem Dataset.  In dieser exemplarischen Vorgehensweise werden die Schritte zum Erstellen einer zweiten Abfrage im [TableAdapter](../data-tools/tableadapter-overview.md) mithilfe von [TableAdapter\-Abfragekonfigurations\-Assistent](../data-tools/editing-tableadapters.md) im [Dataset\-Designer](../data-tools/creating-and-editing-typed-datasets.md) erläutert.  
  
 In dieser exemplarischen Vorgehensweise werden u. a. folgende Aufgaben veranschaulicht:  
  
-   Erstellen eines neuen Projekts vom Typ **Windows\-Anwendung**.  
  
-   Erstellen und Konfigurieren einer Datenquelle in der Anwendung, indem mit dem **Assistenten zum Konfigurieren von Datenquellen** ein Dataset erstellt wird.  
  
-   Öffnen des neuen Datasets im **Dataset\-Designer**.  
  
-   Hinzufügen von Abfragen zum TableAdapter mit dem **TableAdapter\-Konfigurations\-Assistenten**.  
  
## Vorbereitungsmaßnahmen  
 Für die Durchführung dieser exemplarischen Vorgehensweise benötigen Sie Folgendes:  
  
-   Zugriff auf die Beispieldatenbank Northwind \(SQL Server\- oder Access\-Version\).  Weitere Informationen finden Sie unter [Gewusst wie: Installieren von Beispieldatenbanken](../data-tools/how-to-install-sample-databases.md).  
  
## Erstellen einer neuen Windows\-Anwendung.  
 Im ersten Schritt wird eine Windows\-Anwendung erstellt.  
  
#### So erstellen Sie ein neues Windows\-Anwendungsprojekt  
  
1.  Erstellen Sie in [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] über das Menü **Datei** ein neues Projekt.  
  
2.  Wählen Sie im Bereich **Projekttypen** eine Programmiersprache aus.  
  
3.  Klicken Sie im Bereich **Vorlagen** auf **Windows\-Anwendung**.  
  
4.  Nennen Sie das Projekt `TableAdapterQueriesWalkthrough`, und klicken Sie anschließend auf **OK**.  
  
     Visual Studio fügt das Projekt dem **Projektmappen\-Explorer** hinzu und zeigt im Designer ein neues Formular an.  
  
## Erstellen einer Datenbank\-Datenquelle mit einem TableAdapter  
 In diesem Schritt wird mit dem **Assistent zum Konfigurieren von Datenquellen** eine Datenquelle erstellt, die auf der Tabelle `Customers` der Beispieldatenbank Northwind basiert.  Sie benötigen Zugriff auf die Beispieldatenbank Northwind, um die Verbindung herstellen zu können.  Informationen zum Einrichten der Beispieldatenbank Northwind finden Sie unter [Gewusst wie: Installieren von Beispieldatenbanken](../data-tools/how-to-install-sample-databases.md).  
  
#### So erstellen Sie die Datenquelle  
  
1.  Klicken Sie im Menü **Daten** auf **Datenquellen anzeigen**.  
  
2.  Wählen Sie im **Datenquellenfenster** die Option **Neue Datenquelle hinzufügen** aus, um den **Assistenten zum Konfigurieren von Datenquellen** zu starten.  
  
3.  Wählen Sie auf der Seite **Datenquellentyp auswählen** die Option **Datenbank** aus, und klicken Sie auf **Weiter**.  
  
4.  Führen Sie auf der Seite **Wählen Sie Ihre Datenverbindung** einen der folgenden Schritte aus:  
  
    -   Wenn in der Dropdownliste eine Datenverbindung zur Beispieldatenbank "Northwind" verfügbar ist, wählen Sie diese aus.  
  
         \- oder \-  
  
    -   Wählen Sie **Neue Verbindung**, um das Dialogfeld **Verbindung hinzufügen\/ändern** zu öffnen.  
  
5.  Falls die Datenbank ein Kennwort erfordern sollte, aktivieren Sie die Option für die Einbeziehung vertraulicher Daten, und klicken Sie dann auf **Weiter**.  
  
6.  Klicken Sie auf der Seite **Verbindungszeichenfolge in der Programmkonfigurationsdatei speichern** auf **Weiter**.  
  
7.  Erweitern Sie auf der Seite **Datenbankobjekte auswählen** den Knoten **Tabellen**.  
  
8.  Wählen Sie die Tabelle **Customers** aus, und klicken Sie anschließend auf **Fertig stellen**.  
  
     **NorthwindDataSet** wird dem Projekt hinzugefügt, und die **Customers**\-Tabelle wird im **Datenquellenfenster** angezeigt.  
  
## Öffnen des Datasets im Dataset\-Designer  
  
#### So öffnen Sie das Dataset im Dataset\-Designer.  
  
1.  Klicken Sie im **Datenquellenfenster** mit der rechten Maustaste auf **NorthwindDataset**.  
  
2.  Klicken Sie im Kontextmenü auf **DataSet mit Designer bearbeiten**.  
  
     Das Dataset NorthwindDataset wird im **Dataset\-Designer** geöffnet.  
  
## Hinzufügen einer zweiten Abfrage zu CustomersTableAdapter  
 Der Assistent hat das Dataset mit einer Datentabelle **Customers** und dem **CustomersTableAdapter** erstellt.  In diesem Abschnitt der exemplarischen Vorgehensweise wird dem **CustomersTableAdapter** eine zweite Abfrage hinzugefügt.  
  
#### So fügen Sie dem CustomersTableAdapter eine Abfrage hinzu  
  
1.  Ziehen Sie in der **Toolbox** aus der Registerkarte **DataSet** eine **Abfrage** auf die Tabelle **Customers**.  
  
     Der [TableAdapter\-Abfragekonfigurations\-Assistent](../data-tools/editing-tableadapters.md) wird geöffnet.  
  
2.  Wählen Sie **SQL\-Anweisungen verwenden** aus, und klicken Sie anschließend auf **Weiter**.  
  
3.  Wählen Sie **SELECT\-Anweisung, die Zeilen zurückgibt** aus, und klicken Sie dann auf **Weiter**.  
  
4.  Fügen Sie der Abfrage eine WHERE\-Klausel hinzu, sodass sie wie folgt aussieht:  
  
    ```  
    SELECT CustomerID, CompanyName, ContactName, ContactTitle, Address, City, Region, PostalCode, Country, Phone, Fax   
    FROM Customers   
    WHERE City = @City  
    ```  
  
    > [!NOTE]
    >  Wenn Sie die Access\-Version der Northwind\-Datenbank verwenden, ersetzen Sie den Parameter @City durch ein Fragezeichen.  \(`SELECT CustomerID, CompanyName, ContactName, ContactTitle, Address, City, Region, PostalCode, Country, Phone, Fax FROM Customers WHERE City = ?`\)  
  
5.  Geben Sie auf der Seite **Methode zum Generieren auswählen** der **DataTable füllen**\-Methode den Namen `FillByCity`.  
  
    > [!NOTE]
    >  Die Methode für **DataTable zurückgeben** wird in dieser exemplarischen Vorgehensweise nicht verwendet. Daher kann das entsprechende Kontrollkästchen deaktiviert oder der Standardname beibehalten werden.  
  
6.  Klicken Sie auf **Weiter**, und beenden Sie den Assistenten.  
  
     Dem **CustomersTableAdapter** wird die **FillByCity**\-Abfrage hinzugefügt.  
  
## Hinzufügen von Code zum Ausführen der zusätzlichen Abfrage im Formular  
  
#### So führen Sie die Abfrage aus  
  
1.  Wählen Sie im **Projektmappen\-Explorer** die Option **Form1** aus, und klicken Sie auf **Ansicht\-Designer**.  
  
2.  Ziehen Sie den Knoten **Customers** aus dem **Datenquellenfenster** auf **Form1**.  
  
3.  Ändern Sie die Codeansicht, indem Sie im Menü **Ansicht** die Option **Code** auswählen.  
  
4.  Ersetzen Sie den Code im `Form1_Load`\-Ereignishandler durch Folgendes, um die `FillByCity`\-Abfrage auszuführen.  
  
     [!code-vb[VbRaddataTableAdapters#1](../data-tools/codesnippet/VisualBasic/walkthrough-creating-a-tableadapter-with-multiple-queries_1.vb)]
     [!code-cs[VbRaddataTableAdapters#1](../data-tools/codesnippet/CSharp/walkthrough-creating-a-tableadapter-with-multiple-queries_1.cs)]  
  
## Ausführen der Anwendung  
  
#### So führen Sie die Anwendung aus  
  
-   Drücken Sie F5.  
  
-   Das Raster wird mit Kunden mit einem `City`\-Wert von `Seattle` gefüllt.  
  
## Nächste Schritte  
  
### So fügen Sie der Anwendung Funktionalität hinzu  
  
-   Fügen Sie ein <xref:System.Windows.Forms.TextBox>\-Steuerelement und ein <xref:System.Windows.Forms.Button>\-Steuerelement hinzu, und übergeben Sie den Wert im Textfeld an die Abfrage.  \(`CustomersTableAdapter.FillByCity(NorthwindDataSet.Customers, TextBox1.Text)`\).  
  
-   Fügen Sie dem <xref:System.Data.DataTable.ColumnChanging>\-Ereignis oder dem <xref:System.Data.DataTable.RowChanging>\-Ereignis der Datentabellen im Dataset eine Validierungslogik hinzu.  Weitere Informationen finden Sie unter [Überprüfen von Daten in Datasets](../data-tools/validate-data-in-datasets.md).  
  
## Siehe auch  
 [Übersicht über TableAdapters](../data-tools/tableadapter-overview.md)   
 [Gewusst wie: Erstellen von TableAdapters](../data-tools/create-and-configure-tableadapters.md)   
 [Gewusst wie: Erstellen von TableAdapter\-Abfragen](../data-tools/how-to-create-tableadapter-queries.md)   
 [Exemplarische Vorgehensweisen zur Arbeit mit Daten](../Topic/Data%20Walkthroughs.md)   
 [Herstellen von Datenverbindungen in Visual Studio](../data-tools/connecting-to-data-in-visual-studio.md)   
 [Vorbereiten der Anwendung auf den Empfang von Daten](../Topic/Preparing%20Your%20Application%20to%20Receive%20Data.md)   
 [Abrufen von Daten für die Anwendung](../data-tools/fetching-data-into-your-application.md)   
 [Binden von Steuerelementen an Daten in Visual Studio](../data-tools/bind-controls-to-data-in-visual-studio.md)   
 [Bearbeiten von Daten in der Anwendung](../data-tools/editing-data-in-your-application.md)