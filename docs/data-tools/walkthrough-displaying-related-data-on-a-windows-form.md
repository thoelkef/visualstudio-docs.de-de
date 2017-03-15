---
title: "Exemplarische Vorgehensweise: Anzeigen verkn&#252;pfter Daten in einem Windows Form | Microsoft Docs"
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
  - "Daten [Visual Studio], Anzeigen in Windows Forms"
  - "Daten [Visual Studio], Master/Detail"
  - "Anzeigen von Daten auf Formularen, Exemplarische Vorgehensweisen"
  - "Anzeigen von Tabellendaten"
  - "Anzeigen von Tabelleninformationen"
  - "Anzeigen von Tabellen, Verwandte Daten"
  - "Master/Detail-Listen, Anzeigen in Windows Forms"
  - "Windows Forms, Anzeigen von Daten"
ms.assetid: fc4b9055-2bf3-4028-8aad-9489820d69f6
caps.latest.revision: 16
caps.handback.revision: 16
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
robots: noindex,nofollow
---
# Exemplarische Vorgehensweise: Anzeigen verkn&#252;pfter Daten in einem Windows Form
In vielen Anwendungsszenarios ist die Verwendung von Daten aus mehreren Tabellen und häufig von Daten aus verknüpften Tabellen erforderlich.  Das bedeutet, dass Sie mit einer Beziehung zwischen übergeordneten und untergeordneten Elementen arbeiten müssen.  Sie möchten z. B. ein Formular erstellen, in dem bei der Auswahl eines Kundendatensatzes die Aufträge dieses Kunden angezeigt werden.  Die verknüpften Datensätze im Formular können angezeigt werden, indem die <xref:System.Windows.Forms.BindingSource.DataSource%2A>\-Eigenschaft der untergeordneten<xref:System.Windows.Forms.BindingSource> auf die übergeordnete <xref:System.Windows.Forms.BindingSource> \(nicht auf die untergeordnete Tabelle\) festgelegt wird und indem die <xref:System.Windows.Forms.BindingSource.DataMember%2A>\-Eigenschaft der untergeordneten <xref:System.Windows.Forms.BindingSource> auf die Datenbeziehung festgelegt wird, die die über\- und untergeordneten Tabellen miteinander verknüpft.  
  
 In dieser exemplarischen Vorgehensweise werden u. a. folgende Aufgaben veranschaulicht:  
  
-   Erstellen eines Projekts vom Typ **Windows\-Anwendung**.  
  
-   Erstellen und Konfigurieren eines Datasets in der Anwendung auf der Grundlage der `Customers`\-Tabelle und `Orders`\-Tabelle in der Datenbank Northwind mithilfe von [Assistent zum Konfigurieren von Datenquellen](../data-tools/media/data-source-configuration-wizard.png).  
  
-   Hinzufügen von Steuerelementen zum Anzeigen von Daten aus der `Customers`\-Tabelle.  
  
-   Hinzufügen von Steuerelementen zum Anzeigen von `Orders` auf der Grundlage des ausgewählten `Customer`.  
  
-   Testen der Anwendung durch Auswählen verschiedener Kunden und Überprüfen der Anzeige der richtigen Aufträge für den ausgewählten Kunden.  
  
## Vorbereitungsmaßnahmen  
 Für die Durchführung dieser exemplarischen Vorgehensweise benötigen Sie Folgendes:  
  
-   Zugriff auf die Beispieldatenbank Northwind.  Informationen zum Installieren von Beispieldatenbanken finden Sie unter [Gewusst wie: Installieren von Beispieldatenbanken](../data-tools/how-to-install-sample-databases.md).  
  
## Erstellen des Projekts  
 Im ersten Schritt wird eine **Windows\-Anwendung** erstellt.  
  
#### So erstellen Sie ein Projekt vom Typ Windows\-Anwendung  
  
1.  Erstellen Sie über das Menü **Datei** ein neues Projekt.  
  
2.  Nennen Sie das Projekt `RelatedDataWalkthrough`.  
  
3.  Wählen Sie **Windows\-Anwendung** aus, und klicken Sie auf **OK**.  Weitere Informationen finden Sie unter [Clientanwendungen](../Topic/Developing%20Client%20Applications%20with%20the%20.NET%20Framework.md).  
  
     Das Projekt **RelatedDataWalkthrough** wird erstellt und dem **Projektmappen\-Explorer** hinzugefügt.  
  
## Erstellen der Datenquelle  
 In diesem Schritt wird auf der Grundlage der in der Beispieldatenbank Northwind enthaltenen `Customers`\-Tabelle und der `Orders`\-Tabelle ein Dataset erstellt.  
  
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
  
8.  Wählen Sie die Tabellen **Kunden** und **Bestellungen** aus, und klicken Sie dann auf **Fertig stellen**.  
  
     **NorthwindDataSet** wird dem Projekt hinzugefügt, und die **Customers**\-Tabelle wird im **Datenquellenfenster** angezeigt.  
  
## Erstellen von Steuerelementen zum Anzeigen von Daten aus der Customers\-Tabelle  
  
#### So erstellen Sie Steuerelemente zum Anzeigen der Kundendaten \(übergeordnete Datensätze\)  
  
1.  Wählen Sie im **Datenquellenfenster** die **Customers**\-Tabelle aus, und klicken Sie anschließend auf den Dropdownpfeil.  
  
2.  Wählen Sie im Menü die Option **Details** aus.  
  
3.  Ziehen Sie den **Customers**\-Hauptknoten aus dem **Datenquellenfenster** in den oberen Bereich von **Form1**.  
  
     Auf dem Formular werden datengebundene Steuerelemente mit beschreibenden Bezeichnungen sowie ein Toolstrip \(<xref:System.Windows.Forms.BindingNavigator>\) für die Navigation in den Datensätzen angezeigt.  [NorthwindDataSet](../data-tools/dataset-tools-in-visual-studio.md), [CustomersTableAdapter](../data-tools/tableadapter-overview.md), <xref:System.Windows.Forms.BindingSource> und <xref:System.Windows.Forms.BindingNavigator> werden auf der Komponentenleiste angezeigt.  
  
## Erstellen von Steuerelementen zum Anzeigen von Daten aus der Orders\-Tabelle  
 ![Relation im Datenquellenfenster](../data-tools/media/datasources2.gif "DataSources2")  
  
#### So erstellen Sie Steuerelemente zum Anzeigen der Aufträge der einzelnen Kunden \(untergeordnete Datensätze\)  
  
-   Erweitern Sie im **Datenquellenfenster** den **Customers**\-Knoten, und wählen Sie die letzte Spalte der **Customers**\-Tabelle aus. Diese stellt einen erweiterbaren **Orders**\-Knoten dar. Ziehen Sie die Spalte in den unteren Bereich von **Form1**.  
  
     Dem Formular wird eine <xref:System.Windows.Forms.DataGridView> hinzugefügt, und der Komponentenleiste werden eine neue <xref:System.Windows.Forms.BindingSource> \(`OrdersBindingSource`\) und ein neuer TableAdapter \(`OrdersTableAdapter`\) hinzugefügt.  
  
    > [!NOTE]
    >  Öffnen Sie das [Eigenschaftenfenster](../ide/reference/properties-window.md), und wählen Sie **OrdersBindingSource** aus.  Überprüfen Sie die <xref:System.Windows.Forms.BindingSource.DataSource%2A>\-Eigenschaft und <xref:System.Windows.Forms.BindingSource.DataMember%2A>\-Eigenschaft, um festzustellen, wie die Bindung konfiguriert wird, um verknüpfte Datensätze anzuzeigen.  <xref:System.Windows.Forms.BindingSource.DataSource%2A> wird auf `CustomersBindingSource` \(<xref:System.Windows.Forms.BindingSource> der übergeordneten Tabelle\) anstatt auf die `Orders`\-Tabelle festgelegt.  Die <xref:System.Windows.Forms.BindingSource.DataMember%2A>\-Eigenschaft ist auf `FK_Orders_Customers` festgelegt. Hierbei handelt es sich um den Namen des <xref:System.Data.DataRelation>\-Objekts, durch das die Tabellen miteinander verknüpft sind.  
  
## Testen der Anwendung  
  
#### So testen Sie die Anwendung  
  
1.  Drücken Sie F5, um die Anwendung auszuführen.  
  
2.  Wählen Sie mithilfe von **CustomersBindingNavigator** verschiedene Kunden aus, um sicherzustellen, dass in <xref:System.Windows.Forms.DataGridView> die richtigen Aufträge angezeigt werden.  
  
## Nächste Schritte  
 Entsprechend den Anforderungen an Ihre Anwendung können Sie nach der Erstellung eines Master\-Detail\-Formulars noch weitere Schritte ausführen.  Sie können an dieser exemplarischen Vorgehensweise beispielsweise folgende Verbesserung vornehmen:  
  
-   Filtern der `Customers`\-Datensätze, indem der `Customers`\-Tabelle Parametrisierung hinzugefügt wird.  Wählen Sie zu diesem Zweck alle Steuerelemente aus, die Daten aus der `Customers`\-Tabelle anzeigen, klicken Sie auf das Smarttag, und wählen Sie **Abfrage hinzufügen** aus.  Nehmen Sie im [Dialogfeld "Suchkriterien\-Generator"](../Topic/Search%20Criteria%20Builder%20Dialog%20Box.md) die gewünschten Angaben vor.  Weitere Informationen finden Sie unter [Gewusst wie: Hinzufügen einer parametrisierten Abfrage zu einem Formular in einer Windows Forms\-Anwendung](../Topic/How%20to:%20Add%20a%20Parameterized%20Query%20to%20a%20Windows%20Forms%20Application.md).  
  
## Siehe auch  
 [Exemplarische Vorgehensweisen zur Arbeit mit Daten](../Topic/Data%20Walkthroughs.md)   
 [Datenquellenfenster](../Topic/Data%20Sources%20Window.md)   
 [Binden von Windows Forms\-Steuerelementen an Daten in Visual Studio](../data-tools/bind-windows-forms-controls-to-data-in-visual-studio.md)   
 [Übersicht über Datenquellen](../data-tools/add-new-data-sources.md)   
 [Übersicht über TableAdapters](../data-tools/tableadapter-overview.md)   
 [Gewusst wie: Anzeigen von verknüpften Daten in einer Windows Forms\-Anwendung](../data-tools/how-to-display-related-data-in-a-windows-forms-application.md)   
 [Übersicht über die BindingSource\-Komponente](../Topic/BindingSource%20Component%20Overview.md)   
 [Übersicht über das BindingNavigator\-Steuerelement](../Topic/BindingNavigator%20Control%20Overview%20\(Windows%20Forms\).md)