---
title: Erstellen eines Windows Forms zum Suchen von Daten
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- Windows Forms, searching data
- Windows Forms, displaying data
- parameters, displaying filtered data
- data [Visual Studio], parameterizing queries
- data [Visual Studio], searching
ms.assetid: 65ca79a9-7458-466c-af55-978cd24c549e
author: gewarren
ms.author: gewarren
manager: jillfra
ms.workload:
- data-storage
ms.openlocfilehash: aa8b91ccdf4aaa5b46f167673007723938fc62ef
ms.sourcegitcommit: 5af29226aef0a3b4a506b69a08a97cfd21049521
ms.translationtype: MTE95
ms.contentlocale: de-DE
ms.lasthandoff: 03/20/2019
ms.locfileid: "58268785"
---
# <a name="create-a-windows-form-to-search-data"></a>Erstellen eines Windows Forms zum Suchen von Daten

Es kommt häufig vor, dass ausgewählte Daten auf einem Formular angezeigt werden, Angenommen, Sie möchten die Bestellungen für einen bestimmten Kunden oder die Details für eine bestimmte Bestellung anzeigen. In diesem Szenario gibt der Benutzer zunächst Informationen in ein Formular ein. Anschließend wird eine Abfrage mit der Eingabe des Benutzers als Parameter ausgeführt, d. h. die Daten werden auf der Grundlage einer parametrisierten Abfrage ausgewählt. Die Abfrage gibt nur die Daten zurück, die den vom Benutzer eingegebenen Kriterien entsprechen. Diese exemplarische Vorgehensweise veranschaulicht das Erstellen einer Abfrage, die Kunden in einer bestimmten Stadt zurückgibt, sowie das Anpassen der Benutzeroberfläche, damit Benutzer eine Stadt eingeben und zum Ausführen der Abfrage auf eine Schaltfläche klicken können.

Durch die Verwendung parametrisierter Abfragen wird die Effizienz der Anwendung erhöht, weil die Datenbank die Arbeit ausführt, für die sie optimiert ist, nämlich die schnelle Filterung von Datensätzen. Wenn Sie dagegen eine ganze Datenbanktabelle anfordern, sie über das Netzwerk übertragen und dann mit der Anwendungslogik die gewünschten Datensätze suchen, wird die Anwendung langsam und ineffizient.

Sie können alle TableAdapter (und Steuerelemente Parameterwerte annehmen und Ausführen der Abfrage), mit parametrisierte Abfragen hinzufügen der **Suchkriterien-Generator** Dialogfeld. Öffnen Sie das Dialogfeld, indem Sie im Menü **Daten** (bzw. in einem TableAdapter-Smarttag) den Befehl **Abfrage hinzufügen** auswählen.

In dieser exemplarischen Vorgehensweise werden u. a. folgende Aufgaben veranschaulicht:

- Erstellen und konfigurieren die Datenquelle in Ihrer Anwendung mit der **Datenquellenkonfiguration** Assistenten.

- Festlegen des Ablagetyps der Elemente in der **Datenquellen** Fenster.

- Erstellen von Steuerelementen, mit denen Daten angezeigt werden, indem Elemente aus dem **Datenquellenfenster** auf ein Formular gezogen werden.

- Hinzufügen von Steuerelementen zum Anzeigen der Daten auf dem Formular.

- Abschließen der **Suchkriterien-Generator** Dialogfeld.

- Eingeben von Parametern in das Formular und Ausführen der parametrisierten Abfrage.

## <a name="prerequisites"></a>Erforderliche Komponenten

In dieser exemplarischen Vorgehensweise verwendet SQL Server Express LocalDB und der Beispieldatenbank Northwind.

1. Wenn Sie SQL Server Express LocalDB nicht haben, installieren Sie es entweder über die [Downloadseite für SQL Server Express](https://www.microsoft.com/sql-server/sql-server-editions-express), oder über die **Visual Studio-Installer**. In der **Visual Studio-Installer**, können Sie SQL Server Express LocalDB installieren, als Teil der **datenspeicherung und-Verarbeitung** Workload oder als eine einzelne Komponente.

2. Installieren der Northwind-Beispieldatenbank mit folgenden Schritten:

    1. Öffnen Sie in Visual Studio die **Objekt-Explorer von SQL Server** Fenster. (Objekt-Explorer von SQL Server installiert ist, als Teil der **datenspeicherung und-Verarbeitung** arbeitsauslastung in der **Visual Studio-Installer**.) Erweitern Sie die **SQL Server** Knoten. Mit der rechten Maustaste auf der LocalDB-Instanz, und wählen Sie **neue Abfrage**.

       Ein Abfrage-Editor-Fenster wird geöffnet.

    2. Kopieren der [Northwind Transact-SQL-Skript](https://github.com/MicrosoftDocs/visualstudio-docs/blob/master/docs/data-tools/samples/northwind.sql?raw=true) in die Zwischenablage. Dieses T-SQL-Skript wird die Northwind-Datenbank von Grund auf neu erstellt und mit Daten aufgefüllt.

    3. Fügen Sie das T-SQL-Skript im Abfrage-Editor, und wählen Sie dann die **Execute** Schaltfläche.

       Klicken Sie nach kurzer Zeit die Ausführung die Abfrage abgeschlossen ist, und die Northwind-Datenbank wird erstellt.

## <a name="create-the-windows-forms-application"></a>Erstellen Sie die Windows Forms-Anwendung

Erstellen Sie ein neues **Windows Forms-App** Projekt entweder C# oder Visual Basic. Weisen Sie dem Projekt den Namen **WindowsSearchForm** zu.

## <a name="create-the-data-source"></a>Erstellen der Datenquelle

Bei diesem Schritt wird eine Datenquelle aus einer Datenbank erstellt. Hierbei wird der **Assistent zum Konfigurieren von Datenquellen** verwendet:

1.  Zum Öffnen der **Datenquellen** Fenster auf die **Daten** Menü klicken Sie auf **Datenquellen anzeigen**.

2.  Klicken Sie im **Datenquellenfenster** auf **Neue Datenquelle hinzufügen**, um den **Assistenten zum Konfigurieren von Datenquellen** zu starten.

3.  Wählen Sie auf der Seite **Datenquellentyp auswählen** die Option **Datenbank** aus, und klicken Sie auf **Weiter**.

4.  Führen Sie auf der Seite **Wählen Sie Ihre Datenverbindung** einen der folgenden Schritte aus:

    - Wenn in der Dropdownliste eine Datenverbindung zur Beispieldatenbank „Northwind“ verfügbar ist, wählen Sie diese aus.

    - Klicken Sie auf **Neue Verbindung**, um das Dialogfeld **Add/Modify Connection** (Verbindung hinzufügen/ändern) zu öffnen.

5.  Falls die Datenbank ein Kennwort erfordern sollte, aktivieren Sie die Option für die Einbeziehung vertraulicher Daten, und klicken Sie dann auf **Weiter**.

6.  Klicken Sie auf der Seite **Save connection string to the Application Configuration file** (Verbindungszeichenfolge in der Programmkonfigurationsdatei speichern) auf **Weiter**.

7.  Erweitern Sie auf der Seite **Datenbankobjekte auswählen** den Knoten **Tabellen**.

8.  Wählen Sie die Tabelle **Customers** aus, und klicken Sie anschließend auf **Fertig stellen**.

     **NorthwindDataSet** wird dem Projekt hinzugefügt, und die **Customers**-Tabelle wird im **Datenquellenfenster** angezeigt.

## <a name="create-the-form"></a>Erstellen Sie das Formular

Sie können die datengebundenen Steuerelemente erstellen, indem Sie Elemente aus dem **Datenquellenfenster** auf das Formular ziehen:

1.  Erweitern Sie im **Datenquellenfenster** den Knoten **Customers**.

2.  Ziehen Sie den Knoten **Customers** aus dem **Datenquellenfenster** auf das Formular.

     Auf dem Formular werden <xref:System.Windows.Forms.DataGridView> und ein ToolStrip-Element (<xref:System.Windows.Forms.BindingNavigator>) angezeigt, mit denen Sie durch die Datensätze auf dem Formular navigieren können. [NorthwindDataSet](../data-tools/dataset-tools-in-visual-studio.md), CustomersTableAdapter, <xref:System.Windows.Forms.BindingSource> und <xref:System.Windows.Forms.BindingNavigator> werden auf der Komponentenleiste angezeigt.

## <a name="add-parameterization-search-functionality-to-the-query"></a>Hinzufügen von Parametrisierung (Suchfunktionen) zur Abfrage

Sie können eine WHERE-Klausel hinzufügen, um die ursprüngliche Abfrage mithilfe der **Suchkriterien-Generator** Dialogfeld:

1.  Wählen Sie das Steuerelement <xref:System.Windows.Forms.DataGridView> aus. Wählen Sie anschließend im Menü **Daten** die Option **Abfrage hinzufügen** aus.

2.  Typ **FillByCity** in die **Neuer Abfragename** Bereich auf die **Suchkriterien-Generator** Dialogfeld.

3.  Fügen Sie der Abfrage im Bereich **Abfragetext** die Zeichenfolge `WHERE City = @City` hinzu.

     Die Abfrage müsste ungefähr wie folgt aussehen:

     ```sql
     SELECT CustomerID, CompanyName, ContactName, ContactTitle,
          Address, City, Region, PostalCode, Country, Phone, Fax
     FROM Customers
     WHERE City = @City
     ```

    > [!NOTE]
    > Zugriff und OLE DB-Datenquellen verwenden das Fragezeichen ("?") zur Angabe von Parametern, sodass die WHERE-Klausel wie folgt aussehen würde: `WHERE City = ?`.

4.  Klicken Sie auf **OK**, um das Dialogfeld **Suchkriterien-Generator** zu schließen.

     Dem Formular wird ein **FillByCityToolStrip** hinzugefügt.

## <a name="test-the-application"></a>Testen der Anwendung

Ausführen der Anwendung wird das Formular geöffnet, und erleichtert die bereit für den Parameter als Eingabe sind:

1.  Drücken Sie **F5**, um die Anwendung auszuführen.

2.  Geben Sie **London** in das Textfeld **City** ein, und klicken Sie dann auf **FillByCity**.

     Das Datenraster wird mit den Kunden gefüllt, die die Kriterien erfüllen. In diesem Beispiel zeigt das Datenraster nur Kunden an, die den Wert **London** in der Spalte **City** aufweisen.

## <a name="next-steps"></a>Nächste Schritte

Je nach den Anforderungen der Anwendung können nach dem Erstellen eines parametrisierten Formulars weitere Schritte sinnvoll sein. Sie können an dieser exemplarischen Vorgehensweise beispielsweise folgende Verbesserungen vornehmen:

- Hinzufügen von Steuerelementen, die verknüpfte Daten anzeigen. Weitere Informationen finden Sie unter [Beziehungen in Datasets](relationships-in-datasets.md).

- Hinzufügen oder Entfernen von Datenbankobjekten aus dem Dataset durch Bearbeiten. Weitere Informationen finden Sie unter [Erstellen und Konfigurieren von Datasets in Visual Studio](../data-tools/create-and-configure-datasets-in-visual-studio.md).

## <a name="see-also"></a>Siehe auch

- [Binden von Windows Forms-Steuerelementen an Daten in Visual Studio](../data-tools/bind-windows-forms-controls-to-data-in-visual-studio.md)
