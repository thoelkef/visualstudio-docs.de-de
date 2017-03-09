---
title: "Exemplarische Vorgehensweise: &#220;bergeben von Daten zwischen Windows Forms | Microsoft Docs"
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
  - "Daten [Visual Studio], Übergeben zwischen Formularen"
  - "Formulare, Übergeben von Daten zwischen"
  - "Exemplarische Vorgehensweisen [Visual Studio], Daten"
  - "Exemplarische Vorgehensweisen [Windows Forms], Daten"
  - "Windows Forms, Exemplarische Vorgehensweisen"
ms.assetid: 78bf038b-9296-4fbf-b0e8-d881d1aff0df
caps.latest.revision: 14
caps.handback.revision: 11
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# Exemplarische Vorgehensweise: &#220;bergeben von Daten zwischen Windows Forms
Diese exemplarische Vorgehensweise enthält eine Schritt\-für\-Schritt\-Anleitung für die Datenübergabe von einem Formular zum anderen.  Mit dem Verwenden der Tabellen Customers und Orders von Northwind können Benutzer mit einem Formular einen Kunden auswählen und mit einem zweiten die ausgewählte Bestellungen des Kunden anzeigen.  Diese exemplarische Vorgehensweise zeigt, wie Sie eine Methode auf einem Formular erstellen, die die Daten aus dem ersten Formular empfängt.  
  
> [!NOTE]
>  Diese exemplarische Vorgehensweise zeigt nur eine Möglichkeit der Datenübergabe zwischen Formularen.  Es gibt andere Optionen, mit denen sich Daten an ein Formular übergeben lassen, einschließlich folgender Ansätze: Sie können einen zweiten Konstruktor für den Datenempfang erstellen oder eine öffentliche Eigenschaft, in die Daten aus dem ersten Formular eingegeben werden können.  
  
 In dieser exemplarischen Vorgehensweise werden u. a. folgende Aufgaben veranschaulicht:  
  
-   Erstellen eines neuen Projekts vom Typ **Windows\-Anwendung**.  
  
-   Erstellen und Konfigurieren eines Datasets mithilfe von [Assistent zum Konfigurieren von Datenquellen](../data-tools/media/data-source-configuration-wizard.png).  
  
-   Auswählen des Steuerelements, das für das Formular erstellt werden soll, wenn Elemente aus dem **Datenquellenfenster** gezogen werden.  Weitere Informationen finden Sie unter [Festlegen des Steuerelements, das beim Ziehen aus dem Datenquellenfenster erstellt werden soll](../data-tools/set-the-control-to-be-created-when-dragging-from-the-data-sources-window.md).  
  
-   Erstellen eines datengebundenen Steuerelements durch Ziehen von Elementen aus dem **Datenquellenfenster** auf das Formular.  
  
-   Erstellen eines zweiten Formulars mit einem Raster für die Datenanzeige.  
  
-   Erstellen einer TableAdapter\-Abfrage für das Abrufen der Bestellungen eines bestimmten Kunden.  
  
-   Übergeben von Daten zwischen Formularen.  
  
## Vorbereitungsmaßnahmen  
 Für die Durchführung dieser exemplarischen Vorgehensweise benötigen Sie Folgendes:  
  
-   Zugriff auf die Beispieldatenbank Northwind.  Weitere Informationen finden Sie unter [Gewusst wie: Installieren von Beispieldatenbanken](../data-tools/how-to-install-sample-databases.md).  
  
## Erstellen der Windows\-Anwendung  
  
#### So erstellen Sie ein neues Windows\-Projekt  
  
1.  Erstellen Sie über das Menü **Datei** ein neues Projekt.  
  
2.  Geben Sie dem Projekt den Namen `PassingDataBetweenForms`.  
  
3.  Wählen Sie **Windows Forms\-Anwendung** aus, und klicken Sie auf **OK**.  Weitere Informationen finden Sie unter [Clientanwendungen](../Topic/Developing%20Client%20Applications%20with%20the%20.NET%20Framework.md).  
  
     Das Projekt **PassingDataBetweenForms** wird erstellt und zum **Projektmappen\-Explorer** hinzugefügt.  
  
## Erstellen der Datenquelle  
  
#### So erstellen Sie die Datenquelle  
  
1.  Klicken Sie im Menü **Daten** auf **Datenquellen anzeigen**.  
  
2.  Wählen Sie im **Datenquellenfenster** die Option **Neue Datenquelle hinzufügen** aus, um den **Assistenten zum Konfigurieren von Datenquellen** zu starten.  
  
3.  Wählen Sie auf der Seite **Datenquellentyp auswählen** die Option **Datenbank** aus, und klicken Sie auf **Weiter**.  
  
4.  Stellen Sie sicher, dass auf der Seite **Datenbankmodell auswählen Dataset** festgelegt ist und klicken Sie auf **Weiter**.  
  
5.  Führen Sie auf der Seite **Wählen Sie Ihre Datenverbindung** einen der folgenden Schritte aus:  
  
    -   Wenn in der Dropdownliste eine Datenverbindung zur Beispieldatenbank "Northwind" verfügbar ist, wählen Sie diese aus.  
  
         \- oder \-  
  
    -   Wählen Sie **Neue Verbindung**, um das Dialogfeld **Verbindung hinzufügen\/ändern** zu öffnen.  
  
6.  Falls die Datenbank ein Kennwort erfordern sollte und wenn die Option für die Einbeziehung vertraulicher Daten aktiviert ist, wählen Sie die Option und klicken Sie dann auf **Weiter**.  
  
7.  Klicken Sie auf der Seite **Verbindungszeichenfolge in der Programmkonfigurationsdatei speichern** auf **Weiter**.  
  
8.  Erweitern Sie auf der Seite **Datenbankobjekte auswählen** den Knoten **Tabellen**.  
  
9. Wählen Sie die Tabellen **Kunden** und **Bestellungen** aus, und klicken Sie dann auf **Fertig stellen**.  
  
     Das **NorthwindDataSet** wird dem Projekt hinzugefügt, und die Tabellen **Customers** und Orders werden im **Datenquellenfenster** angezeigt.  
  
## Das erste Formular erstellen \(Form1\)  
 Sie können ein datengebundenes Raster erstellen \(ein <xref:System.Windows.Forms.DataGridView>\-Steuerelement\), indem Sie den Knoten **Customers** aus dem **Datenquellenfenster** auf das Formular ziehen.  
  
#### So erstellen Sie ein datengebundenes Raster auf dem Formular  
  
-   Ziehen Sie den Hauptknoten **Customers** aus dem **Datenquellenfenster** auf **Form1**.  
  
     Eine <xref:System.Windows.Forms.DataGridView> und eine Toolleiste \(<xref:System.Windows.Forms.BindingNavigator>\) für das Navigieren durch Datensätze wird auf **Form1** angezeigt.  [NorthwindDataSet](../data-tools/dataset-tools-in-visual-studio.md), [CustomersTableAdapter](../data-tools/tableadapter-overview.md), <xref:System.Windows.Forms.BindingSource> und <xref:System.Windows.Forms.BindingNavigator> werden auf der Komponentenleiste angezeigt.  
  
## Das zweite Formular erstellen \(Form2\)  
  
#### Erstellen eines zweiten Formulars, an das die Daten übergeben werden  
  
1.  Wählen Sie im Menü **Projekt** den Punkt **Windows Form hinzufügen**.  
  
2.  Belassen Sie den Standardnamen **Form2** und klicken Sie **Hinzufügen**.  
  
3.  Ziehen Sie den Hauptknoten **Orders** aus dem **Datenquellenfenster** auf **Form2**.  
  
     Eine <xref:System.Windows.Forms.DataGridView> und eine Toolleiste \(<xref:System.Windows.Forms.BindingNavigator>\) für das Navigieren durch Datensätze wird auf **Form2** angezeigt.  [NorthwindDataSet](../data-tools/dataset-tools-in-visual-studio.md), [CustomersTableAdapter](../data-tools/tableadapter-overview.md), <xref:System.Windows.Forms.BindingSource> und <xref:System.Windows.Forms.BindingNavigator> werden auf der Komponentenleiste angezeigt.  
  
4.  Löschen Sie **OrdersBindingNavigator** aus der Komponentenleiste.  
  
     **OrdersBindingNavigator** wird von **Form2** entfernt.  
  
## Hinzufügen einer TableAdapter\-Abfrage zu Form2 für das Laden der Bestellungen ausgewählter Kunden auf Form1  
  
#### So erstellen Sie eine TableAdapter\-Abfrage  
  
1.  Doppelklicken Sie auf die Datei **NorthwindDataSet.xsd** in **Projektmappen\-Explorer**.  
  
2.  Klicken Sie mit der rechten Maustaste auf **OrdersTableAdapter** und wählen Sie **Abfrage hinzufügen**.  
  
3.  Lassen Sie die Standardeinstellung **SQL\-Anweisung verwenden** und klicken Sie anschließend auf **Weiter**.  
  
4.  Lassen Sie die Standardeinstellung **SELECT\-Anweisung, die Zeilen zurückgibt** und klicken Sie anschließend auf **Weiter**.  
  
5.  Fügen Sie eine WHERE\-Klausel zur Abfrage hinzu, sodass `Orders` auf Grundlage der `CustomerID` zurückgeben wird.  Die Abfrage müsste ungefähr wie folgt aussehen:  
  
    ```  
    SELECT OrderID, CustomerID, EmployeeID, OrderDate, RequiredDate, ShippedDate, ShipVia, Freight, ShipName, ShipAddress, ShipCity, ShipRegion, ShipPostalCode, ShipCountry  
    FROM Orders   
    WHERE CustomerID = @CustomerID  
    ```  
  
    > [!NOTE]
    >  Überprüfen Sie die korrekte Parametersyntax für Ihre Datenbank.  In Microsoft Access etwa würde die WHERE\-Klausel so aussehen: `WHERE CustomerID = ?`.  
  
6.  Klicken Sie auf **Weiter**.  
  
7.  Geben Sie für den **DataTable füllen**\-**Methodenname** `FillByCustomerID` ein.  
  
8.  Löschen Sie die Option **DataTable zurückgeben** und klicken Sie anschließend **Weiter**.  
  
9. Klicken Sie auf **Fertig stellen**.  
  
## Erstellen einer Methode auf Form2 für das Übergeben von Daten an  
  
#### Erstellen einer Methode für das Übergeben von Daten an  
  
1.  Klicken Sie mit der rechten Maustaste auf **Form2** und wählen Sie **Code anzeigen**, sodass **Form2** im **Code\-Editor** geöffnet wird.  
  
2.  Fügen Sie den folgenden Code zu **Form2** nach der `Form2_Load`\-Methode hinzu:  
  
     [!code-vb[VbRaddataDisplaying#1](../data-tools/codesnippet/VisualBasic/pass-data-between-forms_1.vb)]
     [!code-cs[VbRaddataDisplaying#1](../data-tools/codesnippet/CSharp/pass-data-between-forms_1.cs)]  
  
## Erstellen einer Methode auf Form1 für das Übergeben von Daten und das Anzeigen von Form2  
  
#### Erstellen einer Methode für das Übergeben von Daten an Form2  
  
1.  Klicken Sie in **Form1** mit der rechten Maustaste auf das Customer\-Datenraster und dann auf **Eigenschaften**.  
  
2.  Klicken Sie im Fenster **Eigenschaften** auf **Ereignisse**.  
  
3.  Doppelklicken Sie das Ereignis **CellDoubleClick**.  
  
     Der Code\-Editor wird angezeigt.  
  
4.  Aktualisieren Sie die Methodendefinition, sodass sie dem folgenden Beispiel entspricht:  
  
     [!code-cs[VbRaddataDisplaying#2](../data-tools/codesnippet/CSharp/pass-data-between-forms_2.cs)]
     [!code-vb[VbRaddataDisplaying#2](../data-tools/codesnippet/VisualBasic/pass-data-between-forms_2.vb)]  
  
## Ausführen der Anwendung  
  
#### So führen Sie die Anwendung aus  
  
-   Drücken Sie F5, um die Anwendung auszuführen.  
  
-   Doppelklicken Sie einen Kundendatensatz in **Form1**, sodass dieser in **Form2** mit den Bestellungen dieses Kunden geöffnet wird.  
  
## Nächste Schritte  
 Entsprechend den Anforderungen an Ihre Anwendung können Sie nach dem Übergeben der Daten zwischen den Formularen noch weitere Schritte ausführen.  Sie können an dieser exemplarischen Vorgehensweise beispielsweise folgende Verbesserungen vornehmen:  
  
-   Hinzufügen oder Entfernen von Datenbankobjekten aus dem Dataset durch Bearbeiten.  Weitere Informationen finden Sie unter [Gewusst wie: Bearbeiten eines Datasets](../Topic/How%20to:%20Edit%20a%20Dataset.md).  
  
-   Hinzufügen einer Funktion für das Zurückspeichern von Daten in der Datenbank.  Weitere Informationen finden Sie unter [Gewusst wie: Speichern von Datasetänderungen in einer Datenbank](../data-tools/how-to-save-dataset-changes-to-a-database.md).  
  
## Siehe auch  
 [Exemplarische Vorgehensweisen zur Arbeit mit Daten](../Topic/Data%20Walkthroughs.md)   
 [Binden von Windows Forms\-Steuerelementen an Daten in Visual Studio](../data-tools/bind-windows-forms-controls-to-data-in-visual-studio.md)   
 [Übersicht über Datenquellen](../data-tools/add-new-data-sources.md)   
 [Übersicht über TableAdapters](../data-tools/tableadapter-overview.md)   
 [Herstellen von Datenverbindungen in Visual Studio](../data-tools/connecting-to-data-in-visual-studio.md)   
 [Vorbereiten der Anwendung auf den Empfang von Daten](../Topic/Preparing%20Your%20Application%20to%20Receive%20Data.md)   
 [Abrufen von Daten für die Anwendung](../data-tools/fetching-data-into-your-application.md)   
 [Binden von Steuerelementen an Daten in Visual Studio](../data-tools/bind-controls-to-data-in-visual-studio.md)   
 [Bearbeiten von Daten in der Anwendung](../data-tools/editing-data-in-your-application.md)   
 [Überprüfen von Daten](../Topic/Validating%20Data.md)   
 [Speichern von Daten](../data-tools/saving-data.md)