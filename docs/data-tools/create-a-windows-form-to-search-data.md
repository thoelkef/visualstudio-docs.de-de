---
title: Erstellen von Windows Forms zum Suchen von Daten | Microsoft Docs
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- Windows Forms, searching data
- Windows Forms, displaying data
- parameters, displaying filtered data
- data [Visual Studio], parameterizing queries
- data [Visual Studio], searching
ms.assetid: 65ca79a9-7458-466c-af55-978cd24c549e
caps.latest.revision: "28"
author: gewarren
ms.author: gewarren
manager: ghogen
ms.technology: vs-data-tools
ms.workload: data-storage
ms.openlocfilehash: fd882c536fefde9a9eb6ab546d6049d1f1216771
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 12/22/2017
---
# <a name="create-a-windows-form-to-search-data"></a>Erstellen von Windows Forms zum Suchen von Daten
Es kommt häufig vor, dass ausgewählte Daten auf einem Formular angezeigt werden, Angenommen, Sie möchten die Bestellungen für einen bestimmten Kunden oder die Details für eine bestimmte Bestellung anzeigen. In diesem Szenario gibt der Benutzer zunächst Informationen in ein Formular ein. Anschließend wird eine Abfrage mit der Eingabe des Benutzers als Parameter ausgeführt, d. h. die Daten werden auf der Grundlage einer parametrisierten Abfrage ausgewählt. Die Abfrage gibt nur die Daten zurück, die den vom Benutzer eingegebenen Kriterien entsprechen. Diese exemplarische Vorgehensweise veranschaulicht das Erstellen einer Abfrage, die Kunden in einer bestimmten Stadt zurückgibt, sowie das Anpassen der Benutzeroberfläche, damit Benutzer eine Stadt eingeben und zum Ausführen der Abfrage auf eine Schaltfläche klicken können.  
  
 Durch die Verwendung parametrisierter Abfragen wird die Effizienz der Anwendung erhöht, weil die Datenbank die Arbeit ausführt, für die sie optimiert ist, nämlich die schnelle Filterung von Datensätzen. Im Gegensatz dazu Wenn Sie eine ganze Datenbanktabelle anfordern, ihn über das Netzwerk übertragen, und klicken Sie dann mit der Anwendungslogik, die gewünschten Datensätze suchen, kann die Anwendung langsam und ineffizient sein.  
  
 Sie können alle TableAdapter (und Steuerelemente Parameterwerte annehmen und Ausführen der Abfrage), verwenden parametrisierte Abfragen hinzufügen der **Suchkriterien-Generator** (Dialogfeld). Öffnen Sie das Dialogfeld durch Auswählen der **Abfrage hinzufügen** Befehl die **Daten** Menü (oder in einem TableAdapter-Smarttag).  
  
 In dieser exemplarischen Vorgehensweise werden u. a. folgende Aufgaben veranschaulicht:  
  
-   Erstellen ein neues Windows Forms-Anwendungsprojekt.  
  
-   Erstellen und konfigurieren die Datenquelle in Ihrer Anwendung mit der **Datenquellenkonfiguration** Assistenten.  
  
-   Festlegen der Drop-Typ der Elemente in der **Datenquellen**Fenster.  
  
-   Erstellen Steuerelemente zur Anzeige von Daten durch Ziehen von Elementen aus der **Datenquellen** auf das Formular.  
  
-   Hinzufügen von Steuerelementen zum Anzeigen der Daten auf dem Formular.  
  
-   Abschließen der **Suchkriterien-Generator** (Dialogfeld).  
  
-   Eingeben von Parametern in das Formular und Ausführen der parametrisierten Abfrage.  
  
## <a name="prerequisites"></a>Erforderliche Komponenten  
In dieser exemplarischen Vorgehensweise werden die SQL Server Express LocalDB und der Beispieldatenbank Northwind verwendet.  
  
1.  Wenn Sie nicht über SQL Server Express LocalDB verfügen, installieren Sie es entweder aus der [Downloadseite für SQL Server-Editionen](https://www.microsoft.com/en-us/server-cloud/Products/sql-server-editions/sql-server-express.aspx), oder über die **Installer für Visual Studio**. In der Visual Studio-Installer können SQL Server Express LocalDB installiert werden als Teil der **datenspeicherung und Verarbeitung** arbeitsauslastung oder als eine einzelne Komponente.  
  
2.  Installieren Sie die Beispieldatenbank Northwind, indem folgende Schritte:  

    1. Öffnen Sie in Visual Studio die **Objekt-Explorer von SQL Server** Fenster. (Objekt-Explorer von SQL Server installiert ist, als Teil der **datenspeicherung und Verarbeitung** arbeitsauslastung in der Visual Studio-Installer.) Erweitern Sie die **SQL Server** Knoten. Rechtsklicken Sie auf der LocalDB-Instanz, und wählen Sie **neue Abfrage...** .  

       Ein Abfrage-Editorfenster wird geöffnet.  

    2. Kopieren der [Northwind Transact-SQL-Skript](https://github.com/MicrosoftDocs/visualstudio-docs/blob/master/docs/data-tools/samples/northwind.sql?raw=true) in die Zwischenablage. Dieses T-SQL-Skript die Northwind-Datenbank von Grund auf neu erstellt und mit Daten aufgefüllt.  

    3. Fügen Sie das T-SQL-Skript im Abfrage-Editor, und wählen Sie dann die **Execute** Schaltfläche.  

       Nach kurzer Zeit die Abfrage die Ausführung abgeschlossen ist, und die Northwind-Datenbank wird erstellt.  
  
## <a name="create-the-windows-forms-application"></a>Erstellen Sie die Windows Forms-Anwendung  
 Der erste Schritt ist die Erstellung einer **Windows Forms-Anwendung**. An dieser Stelle optional wird dem Projekt einen Namen zuzuweisen, aber Sie erhalten sie hier einen Namen, da Sie das Projekt später speichern müssen.  
  
#### <a name="to-create-the-new-windows-forms-application-project"></a>Um das neue Windows Forms-Anwendungsprojekt zu erstellen.  
  
1. In Visual Studio auf die **Datei** klicken Sie im Menü **neu**, **Projekt...** .  
  
2. Erweitern Sie entweder **Visual C#-** oder **Visual Basic** im linken Bereich, und wählen Sie dann **klassische Windows-Desktop**.  

3. Wählen Sie im mittleren Bereich die **Windows Forms-App** Projekttyp.  

4. Nennen Sie das Projekt **WindowsSearchForm**, und wählen Sie dann **OK**. 
  
     Die **WindowsSearchForm** Projekt wird erstellt und hinzugefügt **Projektmappen-Explorer**.  
  
## <a name="create-the-data-source"></a>Die Datenquelle erstellen  
Dieser Schritt erstellt eine Datenquelle aus einer Datenbank mithilfe der **Datenquellenkonfiguration** Assistenten.  
  
#### <a name="to-create-the-data-source"></a>So erstellen Sie die Datenquelle  
  
1.  Klicken Sie im Menü **Daten** auf **Datenquellen anzeigen**.  
  
2.  In der **Datenquellen** wählen **neue Datenquelle hinzufügen** zum Starten der **Datenquellenkonfiguration** Assistenten.  
  
3.  Wählen Sie auf der Seite **Datenquellentyp auswählen** die Option **Datenbank** aus, und klicken Sie auf **Weiter**.  
  
4.  Auf der **wählen Sie Ihre Datenverbindung** Seite führen Sie einen der folgenden:  
  
    -   Wenn in der Dropdownliste eine Datenverbindung zur Beispieldatenbank „Northwind“ verfügbar ist, wählen Sie diese aus.  
  
    -   Wählen Sie **neue Verbindung** zum Starten der **Verbindung hinzufügen/ändern** (Dialogfeld).  
  
5.  Wenn die Datenbank ein Kennwort erfordern sollte, wählen Sie die Option auf Einbeziehung vertraulicher Daten, und klicken Sie dann auf **Weiter**.  
  
6.  Auf der **Verbindungszeichenfolge in der Programmkonfigurationsdatei speichern** auf **Weiter**.  
  
7.  Auf der **Datenbankobjekte auswählen** Seite, erweitern Sie die **Tabellen** Knoten.  
  
8.  Wählen Sie die **Kunden** Tabelle, und klicken Sie dann auf **Fertig stellen**.  
  
     Die **NorthwindDataSet** wird dem Projekt hinzugefügt und die **Kunden** Tabelle wird angezeigt, der **Datenquellen** Fenster.  
  
## <a name="create-the-form"></a>Erstellen Sie das Formular  
 Sie können die datengebundenen Steuerelemente erstellen, durch Ziehen von Elementen aus der **Datenquellen** auf das Formular.  
  
#### <a name="to-create-data-bound-controls-on-the-form"></a>So erstellen Sie datengebundene Steuerelemente auf dem Formular  
  
1.  Erweitern Sie die **Kunden** Knoten in der **Datenquellen** Fenster.  
  
2.  Ziehen Sie die **Kunden** Knoten aus der **Datenquellen** auf das Formular.  
  
     Auf dem Formular werden <xref:System.Windows.Forms.DataGridView> und ein ToolStrip-Element (<xref:System.Windows.Forms.BindingNavigator>) angezeigt, mit denen Sie durch die Datensätze auf dem Formular navigieren können. Ein [NorthwindDataSet](../data-tools/dataset-tools-in-visual-studio.md), CustomersTableAdapter <xref:System.Windows.Forms.BindingSource>, und <xref:System.Windows.Forms.BindingNavigator> auf der Komponentenleiste angezeigt.  
  
## <a name="add-parameterization-search-functionality-to-the-query"></a>Hinzufügen von Parametrisierung (Suchfunktionen) zur Abfrage  
 Sie können eine WHERE-Klausel hinzufügen, um die ursprüngliche Abfrage mit der **Suchkriterien-Generator** (Dialogfeld).  
  
#### <a name="to-create-a-parameterized-query-and-controls-to-enter-the-parameters"></a>So erstellen Sie eine parametrisierte Abfrage sowie Steuerelemente zur Eingabe der Parameter  
  
1.  Wählen Sie die <xref:System.Windows.Forms.DataGridView> steuern, und wählen Sie dann **Abfrage hinzufügen** auf die **Daten** Menü.  
  
2.  Typ `FillByCity` in der **Neuer Abfragename** Bereich auf die **Suchkriterien-Generator** (Dialogfeld).  
  
3.  Hinzufügen `WHERE City = @City` an die Abfrage in der **Abfragetext** Bereich.  
  
     Die Abfrage müsste ungefähr wie folgt aussehen:  
  
     ```sql
     SELECT CustomerID, CompanyName, ContactName, ContactTitle,  
          Address, City, Region, PostalCode, Country, Phone, Fax  
     FROM Customers
     WHERE City = @City  
     ```
  
    > [!NOTE]
    >  Zugriff und OLE DB-Datenquellen verwenden das Fragezeichen ("?") zur Angabe von Parametern, sodass die WHERE-Klausel wie folgt aussehen würde: `WHERE City = ?`.  
  
4.  Klicken Sie auf **OK** schließen die **Suchkriterien-Generator** (Dialogfeld).  
  
     Ein **FillByCityToolStrip** dem Formular hinzugefügt wird.  
  
## <a name="testing-the-application"></a>Testen der Anwendung  
 Beim Ausführen der Anwendung wird das Formular geöffnet, das zur Übernahme der Parametereingabe bereit ist.  
  
#### <a name="to-test-the-application"></a>So testen Sie die Anwendung  
  
1.  Drücken Sie F5, um die Anwendung auszuführen.  
  
2.  Typ **London** in der **City** Textfeld, und klicken Sie dann auf **FillByCity**.  
  
     Das Datenraster wird mit den Kunden gefüllt, die die Kriterien erfüllen. In diesem Beispiel zeigt das Datenblatt nur Kunden, die den Wert **London** in ihre **City** Spalte.  
  
## <a name="next-steps"></a>Nächste Schritte  
 Je nach den Anforderungen der Anwendung können nach dem Erstellen eines parametrisierten Formulars weitere Schritte sinnvoll sein. Sie können an dieser exemplarischen Vorgehensweise beispielsweise folgende Verbesserungen vornehmen:  
  
-   Hinzufügen von Steuerelementen, die verknüpfte Daten anzeigen. Weitere Informationen finden Sie unter [Beziehungen in Datasets](relationships-in-datasets.md).  
  
-   Hinzufügen oder Entfernen von Datenbankobjekten aus dem Dataset durch Bearbeiten. Weitere Informationen finden Sie unter [Erstellen und Konfigurieren von Datasets in Visual Studio](../data-tools/create-and-configure-datasets-in-visual-studio.md).  
  
## <a name="see-also"></a>Siehe auch  
 [Binden von Windows Forms-Steuerelementen an Daten in Visual Studio](../data-tools/bind-windows-forms-controls-to-data-in-visual-studio.md)