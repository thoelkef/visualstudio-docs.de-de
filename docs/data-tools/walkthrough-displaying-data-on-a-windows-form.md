---
title: "Exemplarische Vorgehensweise: Anzeigen von Daten in einem Windows Form | Microsoft Docs"
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
  - "Datenbindung, Windows Forms"
  - "Anzeigen von Daten auf Formularen, Exemplarische Vorgehensweisen"
  - "Formulare, Anzeigen von Daten"
  - "Windows-Anwendungen, Anzeigen von Daten"
  - "Windows Forms, Anzeigen von Daten"
ms.assetid: f6e08c2c-c792-43de-adf3-3e52c0100225
caps.latest.revision: 20
caps.handback.revision: 20
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
robots: noindex,nofollow
---
# Exemplarische Vorgehensweise: Anzeigen von Daten in einem Windows Form
Eines der häufigsten Szenarios bei der Anwendungsentwicklung ist das Anzeigen von Daten in einem Formular in einer Windows\-Anwendung.  Sie können Daten in einem Formular anzeigen, indem Sie Elemente aus dem [Datenquellenfenster](../Topic/Data%20Sources%20Window.md) auf das Formular ziehen.  In dieser exemplarischen Vorgehensweise wird ein einfaches Formular erstellt, das Daten aus einer einzelnen Tabelle in jeweils verschiedenen Steuerelementen anzeigt.  In diesem Beispiel wird die Tabelle `Customers` der Beispieldatenbank Northwind verwendet.  
  
 In dieser exemplarischen Vorgehensweise werden u. a. folgende Aufgaben veranschaulicht:  
  
-   Erstellen eines neuen Projekts vom Typ **Windows\-Anwendung**.  
  
-   Erstellen und Konfigurieren eines Datasets mithilfe von [Assistent zum Konfigurieren von Datenquellen](../data-tools/media/data-source-configuration-wizard.png).  
  
-   Auswählen des Steuerelements, das für das Formular erstellt werden soll, wenn Elemente aus dem **Datenquellenfenster** gezogen werden.  Weitere Informationen finden Sie unter [Festlegen des Steuerelements, das beim Ziehen aus dem Datenquellenfenster erstellt werden soll](../data-tools/set-the-control-to-be-created-when-dragging-from-the-data-sources-window.md).  
  
-   Erstellen eines datengebundenen Steuerelements, indem Elemente aus dem **Datenquellenfenster** auf das Formular gezogen werden.  
  
## Vorbereitungsmaßnahmen  
 Für die Durchführung dieser exemplarischen Vorgehensweise benötigen Sie Folgendes:  
  
-   Zugriff auf die Beispieldatenbank Northwind.  Weitere Informationen finden Sie unter [Gewusst wie: Installieren von Beispieldatenbanken](../data-tools/how-to-install-sample-databases.md).  
  
## Erstellen der Windows\-Anwendung  
 Im ersten Schritt wird ein Projekt vom Typ **Windows\-Anwendung** erstellt.  
  
#### So erstellen Sie das neue Windows\-Anwendungsprojekt  
  
1.  Erstellen Sie über das Menü **Datei** ein neues Projekt.  
  
2.  Geben Sie dem Projekt den Namen `DisplayingDataonaWindowsForm`.  
  
3.  Wählen Sie **Windows\-Anwendung** aus, und klicken Sie auf **OK**.  Weitere Informationen finden Sie unter [Clientanwendungen](../Topic/Developing%20Client%20Applications%20with%20the%20.NET%20Framework.md).  
  
     Das Projekt **DisplayingDataonaWindowsForm** wird erstellt und dem **Projektmappen\-Explorer** hinzugefügt.  
  
## Erstellen der Datenquelle  
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
  
## Festlegen der zu erstellenden Steuerelemente  
 In dieser exemplarischen Vorgehensweise befinden sich die Daten in einem **Details**\-Layout, in der die Daten in einzelnen Steuerelementen angezeigt werden.  \(Einen anderen Ansatz bietet das **Raster**\-Standardlayout, in dem die Daten in einem <xref:System.Windows.Forms.DataGridView>\-Steuerelement angezeigt werden.\)  
  
#### So legen Sie den Ablagetyp für die Elemente im Datenquellenfenster fest  
  
1.  Erweitern Sie im **Datenquellenfenster** den Knoten **Customers**.  
  
2.  Ändern Sie den Ablagetyp für die Tabelle **Customers** in **Details**, indem Sie in der Dropdownliste für den Knoten **Customers** die Option **Details** auswählen.  Weitere Informationen finden Sie unter [Festlegen des Steuerelements, das beim Ziehen aus dem Datenquellenfenster erstellt werden soll](../data-tools/set-the-control-to-be-created-when-dragging-from-the-data-sources-window.md).  
  
3.  Ändern Sie den Ablagetyp der Spalte **CustomerID** in eine Bezeichnung, indem Sie in der Dropdownliste für den Knoten **CustomerID** die Option **Bezeichnung** auswählen.  
  
## Erstellen des Formulars  
 Erstellen Sie die datengebundenen Steuerelemente, indem Sie Elemente aus dem **Datenquellenfenster** auf das Formular ziehen.  
  
#### So erstellen Sie datengebundene Steuerelemente auf dem Formular  
  
-   Ziehen Sie den Hauptknoten **Customers** aus dem **Datenquellenfenster** in das Formular.  
  
     Auf dem Formular werden datengebundene Steuerelemente mit beschreibenden Bezeichnungen sowie ein Toolstrip \(<xref:System.Windows.Forms.BindingNavigator>\) für die Navigation in den Datensätzen angezeigt.  [NorthwindDataSet](../data-tools/dataset-tools-in-visual-studio.md), [CustomersTableAdapter](../data-tools/tableadapter-overview.md), <xref:System.Windows.Forms.BindingSource> und <xref:System.Windows.Forms.BindingNavigator> werden auf der Komponentenleiste angezeigt.  
  
## Testen der Anwendung  
  
#### So führen Sie die Anwendung aus  
  
-   Drücken Sie F5.  
  
-   Durchsuchen Sie die Datensätze mithilfe des <xref:System.Windows.Forms.BindingNavigator>\-Steuerelements.  
  
## Nächste Schritte  
 Entsprechend den Anforderungen an Ihre Anwendung können Sie nach der Erstellung eines datengebundenen Windows Forms noch weitere Schritte ausführen.  Sie können an dieser exemplarischen Vorgehensweise beispielsweise folgende Verbesserungen vornehmen:  
  
-   Fügen Sie dem Formular Suchfunktionalität hinzu.  Weitere Informationen finden Sie unter [Gewusst wie: Hinzufügen einer parametrisierten Abfrage zu einem Formular in einer Windows Forms\-Anwendung](../Topic/How%20to:%20Add%20a%20Parameterized%20Query%20to%20a%20Windows%20Forms%20Application.md).  
  
-   Fügen Sie eine Funktion hinzu, um Aktualisierungen an die Datenbank zurückzusenden.  Weitere Informationen finden Sie unter [Exemplarische Vorgehensweise: Speichern von Daten in einer Datenbank \(eine Tabelle\)](../Topic/Walkthrough:%20Saving%20Data%20to%20a%20Database%20\(Single%20Table\).md).  
  
-   Fügen Sie dem Dataset die Tabelle `Orders` hinzu, indem Sie im **Datenquellenfenster** die Option **DataSet mit Assistent konfigurieren** wählen.  Fügen Sie anschließend Steuerelemente hinzu, die die zugehörigen Daten anzeigen, indem Sie den Knoten **Orders** \(den Knoten in der Tabelle **Customers** unterhalb der Spalte **Fax**\) auf das Formular ziehen.  Weitere Informationen finden Sie unter [Gewusst wie: Anzeigen von verknüpften Daten in einer Windows Forms\-Anwendung](../data-tools/how-to-display-related-data-in-a-windows-forms-application.md).  
  
## Siehe auch  
 [Exemplarische Vorgehensweisen zur Arbeit mit Daten](../Topic/Data%20Walkthroughs.md)   
 [Binden von Windows Forms\-Steuerelementen an Daten in Visual Studio](../data-tools/bind-windows-forms-controls-to-data-in-visual-studio.md)   
 [Übersicht über Datenquellen](../data-tools/add-new-data-sources.md)   
 [Übersicht über TableAdapters](../data-tools/tableadapter-overview.md)