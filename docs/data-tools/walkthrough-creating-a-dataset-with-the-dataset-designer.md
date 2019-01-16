---
title: 'Exemplarische Vorgehensweise: Erstellen eines Datasets mit Dataset-Designer'
ms.date: 09/11/2017
ms.topic: conceptual
helpviewer_keywords:
- datasets [Visual Basic], walkthroughs
- XML schemas, creating datasets
- data [Visual Studio], Dataset Designer
- Dataset Designer, walkthroughs
- datasets [Visual Basic], creating
author: gewarren
ms.author: gewarren
manager: douge
ms.prod: visual-studio-dev15
ms.workload:
- data-storage
ms.openlocfilehash: e79646609bf592b7a8d71d3e0ba8660c65520715
ms.sourcegitcommit: 37fb7075b0a65d2add3b137a5230767aa3266c74
ms.translationtype: MTE95
ms.contentlocale: de-DE
ms.lasthandoff: 01/02/2019
ms.locfileid: "53868516"
---
# <a name="walkthrough-create-a-dataset-with-the-dataset-designer"></a>Exemplarische Vorgehensweise: Erstellen Sie ein Dataset mit dem Dataset-Designer

In dieser exemplarischen Vorgehensweise erstellen Sie ein Dataset mithilfe der **Dataset-Designer**. Der Artikel führt Sie durch den Prozess der Erstellung eines neuen Projekts und Hinzufügen eines neuen **DataSet** wird. Sie erfahren, wie Tabellen, die basierend auf Tabellen in einer Datenbank ohne mithilfe eines Assistenten erstellen können.

## <a name="prerequisites"></a>Erforderliche Komponenten

In dieser exemplarischen Vorgehensweise verwendet SQL Server Express LocalDB und der Beispieldatenbank Northwind.

1.  Wenn Sie SQL Server Express LocalDB nicht haben, installieren Sie es entweder über die [Downloadseite für SQL Server Express](https://www.microsoft.com/sql-server/sql-server-editions-express), oder über die **Visual Studio-Installer**. In Visual Studio-Installer, SQL Server Express LocalDB installiert werden können, als Teil der **datenspeicherung und-Verarbeitung** Workload oder als eine einzelne Komponente.

2.  Installieren der Northwind-Beispieldatenbank mit folgenden Schritten:

    1. Öffnen Sie in Visual Studio die **Objekt-Explorer von SQL Server** Fenster. (Objekt-Explorer von SQL Server installiert ist, als Teil der **datenspeicherung und-Verarbeitung** Workload im Visual Studio-Installer.) Erweitern Sie die **SQL Server** Knoten. Mit der rechten Maustaste auf der LocalDB-Instanz, und wählen Sie **neue Abfrage**.

       Ein Abfrage-Editor-Fenster wird geöffnet.

    2. Kopieren der [Northwind Transact-SQL-Skript](https://github.com/MicrosoftDocs/visualstudio-docs/blob/master/docs/data-tools/samples/northwind.sql?raw=true) in die Zwischenablage. Dieses T-SQL-Skript wird die Northwind-Datenbank von Grund auf neu erstellt und mit Daten aufgefüllt.

    3. Fügen Sie das T-SQL-Skript im Abfrage-Editor, und wählen Sie dann die **Execute** Schaltfläche.

       Klicken Sie nach kurzer Zeit die Ausführung die Abfrage abgeschlossen ist, und die Northwind-Datenbank wird erstellt.

## <a name="create-a-new-windows-forms-application-project"></a>Erstellen eines neuen Windows Forms-Anwendungsprojekts

1. In Visual Studio auf die **Datei** , wählen Sie im Menü **neu** > **Projekt**.

2. Erweitern Sie entweder **Visual C#**  oder **Visual Basic** wählen Sie im linken Bereich **Windows Desktop**.

3. Wählen Sie im mittleren Bereich die **Windows Forms-App** Projekttyp.

4. Nennen Sie das Projekt **DatasetDesignerWalkthrough**, und wählen Sie dann **OK**.

     Visual Studio fügt das Projekt in **Projektmappen-Explorer** und ein neues Formular im Designer anzuzeigen.

## <a name="add-a-new-dataset-to-the-application"></a>Hinzufügen eines neuen Datasets zur Anwendung

1.  Wählen Sie im Menü **Projekt** die Option **Neues Element hinzufügen** aus.

     Das Dialogfeld **Neues Element hinzufügen** wird angezeigt.

2.  Wählen Sie im linken Bereich **Daten**, und wählen Sie dann **DataSet** im mittleren Bereich.

3.  Nennen Sie das Dataset **NorthwindDataset**, und wählen Sie dann **hinzufügen**.

     Visual Studio fügt eine Datei namens **NorthwindDataset.xsd** auf das Projekt und öffnet sie in der **Dataset-Designer**.

## <a name="create-a-data-connection-in-server-explorer"></a>Erstellen Sie eine Datenverbindung im Server-Explorer

1.  Klicken Sie im Menü **Ansicht** auf **Server-Explorer**.

2.  Klicken Sie im **Server-Explorer** auf die Schaltfläche **Mit Datenbank verbinden**.

3.  Erstellen Sie eine Verbindung mit der Beispieldatenbank Northwind.

## <a name="create-the-tables-in-the-dataset"></a>Erstellen Sie die Tabellen im Dataset

In diesem Abschnitt wird erläutert, wie das Dataset Tabellen hinzugefügt.

### <a name="to-create-the-customers-table"></a>So erstellen Sie die Tabelle Customers

1.  Erweitern Sie die Datenverbindung, die Sie im **Server-Explorer** erstellt haben, und erweitern Sie dann den Knoten **Tabellen**.

2.  Ziehen Sie die Tabelle **Customers** aus dem **Server-Explorer** auf den **DataSet-Designer**.

     Dem Dataset werden die Datentabelle **Customers** und ein **CustomersTableAdapter** hinzugefügt.

### <a name="to-create-the-orders-table"></a>So erstellen Sie die Tabelle Orders

-   Ziehen Sie die Tabelle **Orders** aus dem **Server-Explorer** auf den **DataSet-Designer**.

     Dem Dataset werden die Datentabelle **Orders**, ein **OrdersTableAdapter** und eine Datenbeziehung zwischen den Tabellen **Customers** und **Orders** hinzugefügt.

### <a name="to-create-the-orderdetails-table"></a>So erstellen Sie die Tabelle OrderDetails

-   Ziehen Sie die Tabelle **Order Details** aus dem **Server-Explorer** auf den **DataSet-Designer**.

     Ein **Bestelldetails** Datentabelle **OrderDetailsTableAdapter**, und eine datenbeziehung zwischen den **Bestellungen** und **OrderDetails** Tabellen dem Dataset hinzugefügt werden.

## <a name="next-steps"></a>Nächste Schritte

-   Speichern Sie das DataSet.

-   Wählen Sie im Fenster **Datenquellen** Elemente aus, und ziehen Sie sie auf ein Formular. Weitere Informationen finden Sie unter [Binden von Windows Forms-Steuerelementen an Daten in Visual Studio](../data-tools/bind-windows-forms-controls-to-data-in-visual-studio.md).

-   Fügen Sie den TableAdapters weitere Abfragen hinzu.

-   Fügen Sie dem <xref:System.Data.DataTable.ColumnChanging>-Ereignis oder dem <xref:System.Data.DataTable.RowChanging>-Ereignis der im Dataset enthaltenen Datentabellen Anweisungen für eine Validierung hinzu. Weitere Informationen finden Sie unter [Überprüfen von Daten in Datasets](../data-tools/validate-data-in-datasets.md).

## <a name="see-also"></a>Siehe auch

- [Erstellen und Konfigurieren von Datasets in Visual Studio](../data-tools/create-and-configure-datasets-in-visual-studio.md)
- [Binden von Windows Forms-Steuerelementen an Daten in Visual Studio](../data-tools/bind-windows-forms-controls-to-data-in-visual-studio.md)
- [Binden von Steuerelementen an Daten in Visual Studio](../data-tools/bind-controls-to-data-in-visual-studio.md)
- [Überprüfen von Daten](../data-tools/validate-data-in-datasets.md)