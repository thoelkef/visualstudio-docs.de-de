---
title: "Exemplarische Vorgehensweise: Erstellen eines Windows Forms zum Suchen von Daten | Microsoft Docs"
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
  - "Daten [Visual Studio], Parametrisieren von Abfragen"
  - "Daten [Visual Studio], Suchen"
  - "Parameter, Anzeigen von gefilterten Daten"
  - "Windows Forms, Anzeigen von Daten"
  - "Windows Forms, Suchen nach Daten"
ms.assetid: 65ca79a9-7458-466c-af55-978cd24c549e
caps.latest.revision: 28
caps.handback.revision: 25
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# Exemplarische Vorgehensweise: Erstellen eines Windows Forms zum Suchen von Daten
Es kommt häufig vor, dass ausgewählte Daten auf einem Formular angezeigt werden,  Angenommen, Sie möchten die Bestellungen für einen bestimmten Kunden oder die Details für eine bestimmte Bestellung anzeigen.  In diesem Szenario gibt der Benutzer zunächst Informationen in ein Formular ein. Anschließend wird eine Abfrage mit der Eingabe des Benutzers als Parameter ausgeführt, d. h. die Daten werden auf der Grundlage einer parametrisierten Abfrage ausgewählt.  Die Abfrage gibt nur die Daten zurück, die den vom Benutzer eingegebenen Kriterien entsprechen.  Diese exemplarische Vorgehensweise veranschaulicht das Erstellen einer Abfrage, die Kunden in einer bestimmten Stadt zurückgibt, sowie das Anpassen der Benutzeroberfläche, damit Benutzer eine Stadt eingeben und zum Ausführen der Abfrage auf eine Schaltfläche klicken können.  
  
 Durch die Verwendung parametrisierter Abfragen wird die Effizienz der Anwendung erhöht, weil die Datenbank die Arbeit ausführt, für die sie optimiert ist, nämlich die schnelle Filterung von Datensätzen.  Wenn Sie dagegen eine ganze Datenbanktabelle anfordern, sie über das Netzwerk übertragen und dann mit der Anwendungslogik die gewünschten Datensätze suchen, wird die Anwendung langsam und ineffizient.  
  
 Mit [Dialogfeld "Suchkriterien\-Generator"](../Topic/Search%20Criteria%20Builder%20Dialog%20Box.md) können Sie jedem TableAdapter parametrisierte Abfragen hinzufügen \(sowie Steuerelemente, die Parameterwerte annehmen und die Abfrage ausführen\).  Öffnen Sie das Dialogfeld, indem Sie im Menü **Daten** \(bzw. in einem TableAdapter\-Smarttag\) den Befehl **Abfrage hinzufügen** auswählen.  
  
 In dieser exemplarischen Vorgehensweise werden u. a. folgende Aufgaben veranschaulicht:  
  
-   Erstellen eines neuen Projekts vom Typ **Windows\-Anwendung**.  
  
-   Erstellen und Konfigurieren der Datenquelle in Ihrer Anwendung mit dem [Assistent zum Konfigurieren von Datenquellen](../data-tools/media/data-source-configuration-wizard.png).  
  
-   Festlegen des Ablagetyps von Elementen im [Datenquellenfenster](../Topic/Data%20Sources%20Window.md).  Weitere Informationen finden Sie unter [Festlegen des Steuerelements, das beim Ziehen aus dem Datenquellenfenster erstellt werden soll](../data-tools/set-the-control-to-be-created-when-dragging-from-the-data-sources-window.md).  
  
-   Erstellen von Steuerelementen, mit denen Daten angezeigt werden, indem Elemente aus dem **Datenquellenfenster** auf ein Formular gezogen werden.  
  
-   Hinzufügen von Steuerelementen zum Anzeigen der Daten auf dem Formular.  
  
-   Abschließen von [Dialogfeld "Suchkriterien\-Generator"](../Topic/Search%20Criteria%20Builder%20Dialog%20Box.md).  
  
-   Eingeben von Parametern in das Formular und Ausführen der parametrisierten Abfrage.  
  
## Vorbereitungsmaßnahmen  
 Für die Durchführung dieser exemplarischen Vorgehensweise benötigen Sie Folgendes:  
  
-   Zugriff auf die Beispieldatenbank Northwind.  Weitere Informationen finden Sie unter [Gewusst wie: Installieren von Beispieldatenbanken](../data-tools/how-to-install-sample-databases.md).  
  
## Erstellen der Windows\-Anwendung  
 Im ersten Schritt wird eine **Windows\-Anwendung** erstellt.  Zu diesem Zeitpunkt ist es nicht erforderlich, dem Projekt einen Namen zuzuweisen. Wir führen diesen Schritt dennoch aus, weil wir das Projekt später speichern möchten.  
  
#### So erstellen Sie das neue Windows\-Anwendungsprojekt  
  
1.  Erstellen Sie über das Menü **Datei** ein neues Projekt.  
  
2.  Weisen Sie dem Projekt den Namen `WindowsSearchForm` zu.  
  
3.  Wählen Sie **Windows\-Anwendung** aus, und klicken Sie auf **OK**.  Weitere Informationen finden Sie unter [Clientanwendungen](../Topic/Developing%20Client%20Applications%20with%20the%20.NET%20Framework.md).  
  
     Das Projekt **WindowsSearchForm** wird erstellt und dem **Projektmappen\-Explorer** hinzugefügt.  
  
## Erstellen der Datenquelle  
 Bei diesem Schritt wird eine Datenquelle aus einer Datenbank erstellt. Hierbei wird der **Assistent zum Konfigurieren von Datenquellen** verwendet.  Sie benötigen Zugriff auf die Beispieldatenbank Northwind, um die Verbindung herstellen zu können.  Informationen zum Einrichten der Beispieldatenbank Northwind finden Sie unter [Gewusst wie: Installieren von Beispieldatenbanken](../data-tools/how-to-install-sample-databases.md).  
  
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
  
## Erstellen des Formulars  
 Sie können die datengebundenen Steuerelemente erstellen, indem Sie Elemente aus dem **Datenquellenfenster** auf das Formular ziehen.  
  
#### So erstellen Sie datengebundene Steuerelemente auf dem Formular  
  
1.  Erweitern Sie im **Datenquellenfenster** den Knoten **Customers**.  
  
2.  Ziehen Sie den Knoten **Customers** aus dem **Datenquellenfenster** auf das Formular.  
  
     Auf dem Formular werden <xref:System.Windows.Forms.DataGridView> und ein ToolStrip\-Element \(<xref:System.Windows.Forms.BindingNavigator>\) angezeigt, mit denen Sie durch die Datensätze auf dem Formular navigieren können.  [NorthwindDataSet](../data-tools/dataset-tools-in-visual-studio.md), [CustomersTableAdapter](../data-tools/tableadapter-overview.md), <xref:System.Windows.Forms.BindingSource> und <xref:System.Windows.Forms.BindingNavigator> werden auf der Komponentenleiste angezeigt.  
  
## Hinzufügen von Parametrisierung \(Suchfunktionen\) zur Abfrage  
 Sie können der ursprünglichen Abfrage mithilfe von [Dialogfeld "Suchkriterien\-Generator"](../Topic/Search%20Criteria%20Builder%20Dialog%20Box.md) eine WHERE\-Klausel hinzufügen.  
  
#### So erstellen Sie eine parametrisierte Abfrage sowie Steuerelemente zur Eingabe der Parameter  
  
1.  Wählen Sie das <xref:System.Windows.Forms.DataGridView>\-Steuerelement aus. Wählen Sie anschließend im Menü **Daten** die Option **Abfrage hinzufügen** aus.  
  
2.  Geben Sie im [Dialogfeld "Suchkriterien\-Generator"](../Topic/Search%20Criteria%20Builder%20Dialog%20Box.md) im Bereich **Neuer Abfragename** die Zeichenfolge `FillByCity` ein.  
  
3.  Fügen Sie der Abfrage im Bereich **Abfragetext** die Zeichenfolge `WHERE City = @City` hinzu.  
  
     Die Abfrage müsste ungefähr wie folgt aussehen:  
  
     `SELECT CustomerID, CompanyName, ContactName, ContactTitle, Address, City, Region, PostalCode, Country, Phone, Fax`  
  
     `FROM Customers`  
  
     `WHERE City = @City`  
  
    > [!NOTE]
    >  Access\- und OleDb\-Datenquellen verwenden das Fragezeichen \(?\) zur Angabe von Parametern, sodass die WHERE\-Klausel wie folgt aussieht: `WHERE City = ?`.  
  
4.  Klicken Sie auf **OK**, um das Dialogfeld **Suchkriterien\-Generator** zu schließen.  
  
     Dem Formular wird ein **FillByCityToolStrip** hinzugefügt.  
  
## Testen der Anwendung  
 Beim Ausführen der Anwendung wird das Formular geöffnet, das zur Übernahme der Parametereingabe bereit ist.  
  
#### So testen Sie die Anwendung  
  
1.  Drücken Sie F5, um die Anwendung auszuführen.  
  
2.  Geben Sie London in das Textfeld **City** ein, und klicken Sie dann auf **FillByCity**.  
  
     Das Datenblatt wird mit den Kunden gefüllt, die die Parametrisierungskriterien erfüllen.  In diesem Beispiel zeigt das Datenblatt nur Kunden an, die den Wert **London** in der Spalte **City** aufweisen.  
  
## Nächste Schritte  
 Je nach den Anforderungen der Anwendung können nach dem Erstellen eines parametrisierten Formulars weitere Schritte sinnvoll sein.  Sie können an dieser exemplarischen Vorgehensweise beispielsweise folgende Verbesserungen vornehmen:  
  
-   Hinzufügen von Steuerelementen, die verknüpfte Daten anzeigen.  Weitere Informationen finden Sie unter [Gewusst wie: Anzeigen von verknüpften Daten in einer Windows Forms\-Anwendung](../data-tools/how-to-display-related-data-in-a-windows-forms-application.md).  
  
-   Hinzufügen oder Entfernen von Datenbankobjekten aus dem Dataset durch Bearbeiten.  Weitere Informationen finden Sie unter [Gewusst wie: Bearbeiten eines Datasets](../Topic/How%20to:%20Edit%20a%20Dataset.md).  
  
## Siehe auch  
 [Exemplarische Vorgehensweisen zur Arbeit mit Daten](../Topic/Data%20Walkthroughs.md)   
 [Binden von Windows Forms\-Steuerelementen an Daten in Visual Studio](../data-tools/bind-windows-forms-controls-to-data-in-visual-studio.md)   
 [Übersicht über Datenquellen](../data-tools/add-new-data-sources.md)   
 [Übersicht über TableAdapters](../data-tools/tableadapter-overview.md)   
 [Übersicht über die BindingSource\-Komponente](../Topic/BindingSource%20Component%20Overview.md)   
 [Übersicht über das BindingNavigator\-Steuerelement](../Topic/BindingNavigator%20Control%20Overview%20\(Windows%20Forms\).md)