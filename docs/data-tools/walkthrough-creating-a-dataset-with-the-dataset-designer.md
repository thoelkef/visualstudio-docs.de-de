---
title: 'Exemplarische Vorgehensweise: Erstellen eines Datasets mit dem DataSet-Designer'
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
ms.technology: vs-data-tools
ms.workload:
- data-storage
ms.openlocfilehash: 67fcfb001dab733ae53e0b16a78858f94b5b8e23
ms.sourcegitcommit: 42ea834b446ac65c679fa1043f853bea5f1c9c95
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/19/2018
---
# <a name="walkthrough-creating-a-dataset-with-the-dataset-designer"></a>Exemplarische Vorgehensweise: Erstellen eines Datasets mit dem DataSet-Designer

In dieser exemplarischen Vorgehensweise erstellen Sie ein Dataset mithilfe der **Dataset-Designer**. Sie gelangen Sie durch den Prozess zum Erstellen eines neuen Projekts und Hinzufügen eines neuen **DataSet** wird. Sie erfahren, wie Sie auf den Tabellen einer Datenbank basierende Tabellen erstellen können, ohne einen Assistenten zu verwenden.

In dieser exemplarischen Vorgehensweise werden u. a. folgende Aufgaben veranschaulicht:

-   Erstellen eines neuen **Windows Forms-Anwendung** Projekt.

-   Hinzufügen eines leeren **DataSet** Element aus, um das Projekt.

-   Erstellen und Konfigurieren einer Datenquelle in Ihrer Anwendung durch Erstellung eines Datasets mit dem **Dataset-Designer**.

-   Erstellen einer Verbindung mit der Datenbank Northwind im **Server-Explorer**.

-   Erstellen von Tabellen mit TableAdapters im Dataset, auf der Grundlage von Tabellen der Datenbank

[!INCLUDE[note_settings_general](../data-tools/includes/note_settings_general_md.md)]

## <a name="prerequisites"></a>Voraussetzungen
In dieser exemplarischen Vorgehensweise werden die SQL Server Express LocalDB und der Beispieldatenbank Northwind verwendet.

1.  Wenn Sie nicht über SQL Server Express LocalDB verfügen, installieren Sie es entweder aus der [Downloadseite für SQL Server Express](https://www.microsoft.com/sql-server/sql-server-editions-express), oder über die **Installer für Visual Studio**. In der Visual Studio-Installer können SQL Server Express LocalDB installiert werden als Teil der **datenspeicherung und Verarbeitung** arbeitsauslastung oder als eine einzelne Komponente.

2.  Installieren Sie die Beispieldatenbank Northwind, indem folgende Schritte:

    1. Öffnen Sie in Visual Studio die **Objekt-Explorer von SQL Server** Fenster. (Objekt-Explorer von SQL Server installiert ist, als Teil der **datenspeicherung und Verarbeitung** arbeitsauslastung in der Visual Studio-Installer.) Erweitern Sie die **SQL Server** Knoten. Rechtsklicken Sie auf der LocalDB-Instanz, und wählen Sie **neue Abfrage...** .

       Ein Abfrage-Editorfenster wird geöffnet.

    2. Kopieren der [Northwind Transact-SQL-Skript](https://github.com/MicrosoftDocs/visualstudio-docs/blob/master/docs/data-tools/samples/northwind.sql?raw=true) in die Zwischenablage. Dieses T-SQL-Skript die Northwind-Datenbank von Grund auf neu erstellt und mit Daten aufgefüllt.

    3. Fügen Sie das T-SQL-Skript im Abfrage-Editor, und wählen Sie dann die **Execute** Schaltfläche.

       Nach kurzer Zeit die Abfrage die Ausführung abgeschlossen ist, und die Northwind-Datenbank wird erstellt.

## <a name="creating-a-new-windows-forms-application-project"></a>Erstellen ein neues Windows Forms-Anwendungsprojekt

#### <a name="to-create-a-new-windows-forms-application-project"></a>So erstellen ein neues Windows Forms-Anwendungsprojekt

1. In Visual Studio auf die **Datei** klicken Sie im Menü **neu**, **Projekt...** .

2. Erweitern Sie entweder **Visual C#-** oder **Visual Basic** im linken Bereich, und wählen Sie dann **klassische Windows-Desktop**.

3. Wählen Sie im mittleren Bereich die **Windows Forms-App** Projekttyp.

4. Nennen Sie das Projekt **DatasetDesignerWalkthrough**, und wählen Sie dann **OK**.

     Fügt das Projekt in Visual Studio **Projektmappen-Explorer** und ein neues Formular im Designer anzuzeigen.

## <a name="adding-a-new-dataset-to-the-application"></a>Hinzufügen eines neuen Datasets zur Anwendung

#### <a name="to-add-a-new-dataset-item-to-the-project"></a>So fügen Sie dem Projekt ein neues Dataset-Element hinzu

1.  Auf der **Projekt** klicken Sie im Menü **neues Element hinzufügen...** .

     Das Dialogfeld **Neues Element hinzufügen** wird angezeigt.

2.  Wählen Sie im linken Bereich **Daten**, und wählen Sie dann **DataSet** im mittleren Bereich.

3.  Nennen Sie das Dataset **NorthwindDataset**, und wählen Sie dann **hinzufügen**.

     Visual Studio fügt eine Datei namens **NorthwindDataset.xsd** auf das Projekt und öffnet sie in der **Dataset-Designer**.

## <a name="creating-a-data-connection-in-server-explorer"></a>Erstellen einer Datenverbindung im Server-Explorer

#### <a name="to-create-a-connection-to-the-northwind-database"></a>So stellen Sie eine Verbindung mit der Datenbank Northwind her

1.  Auf der **Ansicht** Menü klicken Sie auf **Server-Explorer**.

2.  In **Server-Explorer**, klicken Sie auf die **mit Datenbank verbinden** Schaltfläche.

3.  Erstellen Sie eine Verbindung mit der Beispieldatenbank Northwind.

## <a name="creating-the-tables-in-the-dataset"></a>Erstellen von Tabellen im Dataset
In diesem Abschnitt wird erläutert, wie dem Dataset Tabellen hinzugefügt werden.

#### <a name="to-create-the-customers-table"></a>So erstellen Sie die Tabelle Customers

1.  Erweitern Sie die Datenverbindung, die Sie erstellt, im haben **Server-Explorer**, und erweitern Sie dann die **Tabellen** Knoten.

2.  Ziehen Sie die **Kunden** aus Tabelle **Server-Explorer** auf die **Dataset-Designer**.

     Ein **Kunden** Datentabelle und **CustomersTableAdapter** zum Dataset hinzugefügt werden.

#### <a name="to-create-the-orders-table"></a>So erstellen Sie die Tabelle Orders

-   Ziehen Sie die **Aufträge** aus Tabelle **Server-Explorer** auf die **Dataset-Designer**.

     Ein **Aufträge** Datentabelle **OrdersTableAdapter**, und eine datenbeziehung zwischen den **Kunden** und **Aufträge** Tabellen hinzugefügt werden die das DataSet.

#### <a name="to-create-the-orderdetails-table"></a>So erstellen Sie die Tabelle OrderDetails

-   Ziehen Sie die **Bestelldetails** aus Tabelle **Server-Explorer** auf die **Dataset-Designer**.

     Ein **Bestelldetails** Datentabelle **OrderDetailsTableAdapter**, und eine datenbeziehung zwischen den **Aufträge** und **OrderDetails** Tabellen werden zum Dataset hinzugefügt.

## <a name="next-steps"></a>Nächste Schritte

### <a name="to-add-functionality-to-your-application"></a>So fügen Sie der Anwendung Funktionalität hinzu

-   Speichern Sie das DataSet.

-   Wählen Sie Elemente in der **Datenquellen** Fenster ein Formular ziehen. Weitere Informationen finden Sie unter [Binden von Windows Forms-Steuerelementen an Daten in Visual Studio](../data-tools/bind-windows-forms-controls-to-data-in-visual-studio.md).

-   Fügen Sie den TableAdapters weitere Abfragen hinzu.

-   Fügen Sie dem <xref:System.Data.DataTable.ColumnChanging>-Ereignis oder dem <xref:System.Data.DataTable.RowChanging>-Ereignis der im Dataset enthaltenen Datentabellen Anweisungen für eine Validierung hinzu. Weitere Informationen finden Sie unter [Validieren von Daten in Datasets](../data-tools/validate-data-in-datasets.md).

## <a name="see-also"></a>Siehe auch

- [Erstellen und Konfigurieren von Datasets in Visual Studio](../data-tools/create-and-configure-datasets-in-visual-studio.md)
- [Binden von Windows Forms-Steuerelementen an Daten in Visual Studio](../data-tools/bind-windows-forms-controls-to-data-in-visual-studio.md)
- [Binden von Steuerelementen an Daten in Visual Studio](../data-tools/bind-controls-to-data-in-visual-studio.md)
- [Überprüfen von Daten](../data-tools/validate-data-in-datasets.md)
- [Speichern von Daten](../data-tools/saving-data.md)