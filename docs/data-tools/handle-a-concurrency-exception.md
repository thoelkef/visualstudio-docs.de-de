---
title: Behandeln einer Parallelitätsausnahme
ms.date: 09/11/2017
ms.topic: conceptual
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- concurrency control, exceptions
- datasets [Visual Basic], errors
- exception handling, concurrency issues
- data concurrency, walkthroughs
- updating datasets, errors
- concurrency control, walkthroughs
ms.assetid: 73ee9759-0a90-48a9-bf7b-9d6fc17bff93
author: gewarren
ms.author: gewarren
manager: douge
ms.prod: visual-studio-dev15
ms.technology: vs-data-tools
ms.workload:
- data-storage
ms.openlocfilehash: 24338b2a6bc49a9a1a2a77e6395f60013c4465b7
ms.sourcegitcommit: e13e61ddea6032a8282abe16131d9e136a927984
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/26/2018
---
# <a name="handle-a-concurrency-exception"></a>Behandeln einer Parallelitätsausnahme
Parallelitätsausnahmen (<xref:System.Data.DBConcurrencyException>) werden ausgelöst, wenn zwei Benutzer gleichzeitig versuchen, dieselben Daten in einer Datenbank zu ändern. In dieser exemplarischen Vorgehensweise erstellen Sie eine Windows-Anwendung, die veranschaulicht, wie zum Abfangen einer <xref:System.Data.DBConcurrencyException>, wechseln Sie zu der Zeile, die den Fehler verursacht hat, und erfahren Sie, eine Strategie für deren Behandlung.

 Diese exemplarische Vorgehensweise enthält folgende Vorgänge:

1.  Erstellen Sie ein neues **Windows Forms-Anwendungsprojekt**.

2.  Erstellen eines neuen Datasets auf der Grundlage der Tabelle `Customers` der Datenbank Northwind.

3.  Erstellen eines Formulars mit einer <xref:System.Windows.Forms.DataGridView> für die Anzeige der Daten.

4.  Füllen eines Datasets mit Daten aus der Tabelle `Customers` in der Datenbank Northwind.

5.  Verwenden der **Tabellendaten anzeigen** Funktion **Server-Explorer** für den Zugriff auf die `Customers` Daten und ändern Sie einen Datensatz der Tabelle.

6.  Ändern Sie den gleichen Datensatz auf einen anderen Wert, aktualisieren Sie das Dataset und versuchen Sie, die Änderungen in der Datenbank zu schreiben, was zu einem Parallelitätsfehler führt.

7.  Fangen Sie den Fehler ab, und zeigen Sie anschließend die verschiedenen Versionen des Datensatzes an, um festzulegen, ob die Aktualisierung der Datenbank fortgesetzt oder abgebrochen werden soll.

## <a name="prerequisites"></a>Erforderliche Komponenten
In dieser exemplarischen Vorgehensweise werden die SQL Server Express LocalDB und der Beispieldatenbank Northwind verwendet.

1.  Wenn Sie nicht über SQL Server Express LocalDB verfügen, installieren Sie es entweder aus der [Downloadseite für SQL Server Express](https://www.microsoft.com/sql-server/sql-server-editions-express), oder über die **Installer für Visual Studio**. In der Visual Studio-Installer können SQL Server Express LocalDB installiert werden als Teil der **datenspeicherung und Verarbeitung** arbeitsauslastung oder als eine einzelne Komponente.

2.  Installieren Sie die Beispieldatenbank Northwind, indem folgende Schritte:

    1. Öffnen Sie in Visual Studio die **Objekt-Explorer von SQL Server** Fenster. (Objekt-Explorer von SQL Server installiert ist, als Teil der **datenspeicherung und Verarbeitung** arbeitsauslastung in der Visual Studio-Installer.) Erweitern Sie die **SQL Server** Knoten. Rechtsklicken Sie auf der LocalDB-Instanz, und wählen Sie **neue Abfrage...** .

       Ein Abfrage-Editorfenster wird geöffnet.

    2. Kopieren der [Northwind Transact-SQL-Skript](https://github.com/MicrosoftDocs/visualstudio-docs/blob/master/docs/data-tools/samples/northwind.sql?raw=true) in die Zwischenablage. Dieses T-SQL-Skript die Northwind-Datenbank von Grund auf neu erstellt und mit Daten aufgefüllt.

    3. Fügen Sie das T-SQL-Skript im Abfrage-Editor, und wählen Sie dann die **Execute** Schaltfläche.

       Nach kurzer Zeit die Abfrage die Ausführung abgeschlossen ist, und die Northwind-Datenbank wird erstellt.

> [!NOTE]
>  Die angezeigten Dialogfelder und Menübefehle, die Sie sehen möglicherweise unterscheiden sich von denen je nach Ihren aktiven Einstellungen oder der Edition, die Sie verwenden in der Hilfe beschriebenen. Klicken Sie im Menü **Extras** auf **Einstellungen importieren und exportieren** , um die Einstellungen zu ändern. Weitere Informationen finden Sie unter [Personalisieren von Visual Studio-IDE](../ide/personalizing-the-visual-studio-ide.md).

## <a name="create-a-new-project"></a>Erstellt ein neues Projekt
 Sie zunächst dieser exemplarischen Vorgehensweise erstellen eine neue Windows Forms-Anwendung.

#### <a name="to-create-a-new-windows-forms-application-project"></a>So erstellen Sie ein neues Windows Forms-Anwendungsprojekt

1. In Visual Studio auf die **Datei** klicken Sie im Menü **neu**, **Projekt...** .

2. Erweitern Sie entweder **Visual C#-** oder **Visual Basic** im linken Bereich, und wählen Sie dann **klassische Windows-Desktop**.

3. Wählen Sie im mittleren Bereich die **Windows Forms-App** Projekttyp.

4. Nennen Sie das Projekt **ConcurrencyWalkthrough**, und wählen Sie dann **OK**.

     Die **ConcurrencyWalkthrough** Projekt wird erstellt und hinzugefügt **Projektmappen-Explorer**, und ein neues Formular im Designer geöffnet.

## <a name="create-the-northwind-dataset"></a>Erstellen des Datasets Northwind
 In diesem Abschnitt erstellen Sie ein Dataset namens `NorthwindDataSet`.

#### <a name="to-create-the-northwinddataset"></a>So erstellen Sie das NorthwindDataset

1.  Auf der **Daten** Menü wählen **neue Datenquelle hinzufügen**.

     Die [Data Source Configuration Wizard](../data-tools/media/data-source-configuration-wizard.png) wird geöffnet.

2.  Auf der **wählen Sie einen Datenquellentyp** wählen **Datenbank**.

3.  Wählen Sie aus der Liste der verfügbaren Verbindungen eine Verbindung zur Beispieldatenbank Northwind. Wenn die Verbindung nicht in der Liste der Verbindungen verfügbar ist, wählen Sie **neue Verbindung**

    > [!NOTE]
    >  Wenn Sie eine Verbindung mit einer lokalen Datenbankdatei herstellen, wählen Sie **keine** Wenn Sie gefragt, wenn Sie möchten, möchten Sie die Datei dem Projekt hinzufügen.

4.  Auf der **Verbindungszeichenfolge in der Programmkonfigurationsdatei speichern** wählen **Weiter**.

5.  Erweitern Sie die **Tabellen** Knoten, und wählen die `Customers` Tabelle. Der Standardname für das Dataset sollte `NorthwindDataSet` sein.

6.  Wählen Sie **Fertig stellen** des Datasets zum Projekt hinzufügen.

## <a name="create-a-data-bound-datagridview-control"></a>Erstellen einer datengebundenen DataGridView-Steuerelement
 In diesem Abschnitt erstellen Sie eine <xref:System.Windows.Forms.DataGridView> durch Ziehen der **Kunden** Element aus der **Datenquellen** auf das Windows-Formular.

#### <a name="to-create-a-datagridview-control-that-is-bound-to-the-customers-table"></a>So erstellen Sie ein DataGridView-Steuerelement, das an die Tabelle Customers gebunden ist

1.  Auf der **Daten** Menü Wählen Sie **Datenquellen anzeigen** So öffnen die **Datenquellenfenster**.

2.  In der **Datenquellen** Fenster, erweitern Sie die **NorthwindDataSet** Knoten, und wählen Sie dann die **Kunden** Tabelle.

3.  Wählen Sie den nach unten zeigenden Pfeil des Tabellenknotens, und wählen Sie dann **DataGridView** in der Dropdown-Liste.

4.  Ziehen Sie die Tabelle auf einen leeren Bereich des Formulars.

     Ein <xref:System.Windows.Forms.DataGridView> Steuerelement namens `CustomersDataGridView` und ein <xref:System.Windows.Forms.BindingNavigator> mit dem Namen `CustomersBindingNavigator` werden hinzugefügt, um das Formular, das gebunden ist die <xref:System.Windows.Forms.BindingSource>. Dies ist in Turn gebunden ist die `Customers` -Tabelle in der `NorthwindDataSet`.

## <a name="test-the-form"></a>Testen Sie das Formular
 Sie können das Formular jetzt testen, um sicherzustellen, dass das Verhalten bisher wie erwartet ausfällt.

#### <a name="to-test-the-form"></a>So testen Sie das Formular

1.  Wählen Sie **F5** zum Ausführen der Anwendung

     Das Formular wird mit einem <xref:System.Windows.Forms.DataGridView> Steuerelement darauf, das mit Daten gefüllt ist die `Customers` Tabelle.

2.  Auf der **Debuggen** klicken Sie im Menü **Beenden des Debuggens**.

## <a name="handle-concurrency-errors"></a>Behandeln von Parallelitätsfehlern
 Wie Sie Fehler behandeln, hängt von den jeweiligen Geschäftsregeln, die Ihre Anwendung steuern. In dieser exemplarischen Vorgehensweise verwenden wir die folgende Strategie zum Behandeln des parallelitätsfehlers beispielhaft.

 Die Anwendung stellt die Benutzer drei Versionen des Datensatzes zur Verfügung:

-   Der aktuelle Datensatz in der Datenbank

-   Der ursprüngliche Datensatz, der in das Dataset geladen werden

-   Die vorgeschlagenen Änderungen im dataset

Der Benutzer kann dann die Datenbank mit der vorgeschlagenen Version überschreiben oder das Update Abbrechen und das Dataset mit den neuen Werten aus der Datenbank aktualisieren.

#### <a name="to-enable-the-handling-of-concurrency-errors"></a>So aktivieren Sie die Behandlung von Parallelitätsfehlern

1.  Erstellen Sie einen benutzerdefinierten Fehlerhandler.

2.  Zeigen Sie die Auswahloptionen für den Benutzer an.

3.  Verarbeiten Sie die Eingabe des Benutzers.

4.  Senden Sie die Aktualisierung erneut, oder setzen Sie die Daten im Dataset zurück.

### <a name="add-code-to-handle-the-concurrency-exception"></a>Fügen Sie Code zum Behandeln von Parallelitätsausnahmen
 Wenn Sie versuchen, ein Update ausführen und eine Ausnahme ausgelöst wird, möchten Sie in der Regel etwas mit den Informationen, die von der ausgelösten Ausnahme bereitgestellt wird.

 In diesem Abschnitt fügen Sie Code, der versucht, die Datenbank zu aktualisieren. Sie können auch behandeln jede <xref:System.Data.DBConcurrencyException> ausgelöste, sowie alle anderen Ausnahmen.

> [!NOTE]
>  Die `CreateMessage`-Methode und die `ProcessDialogResults`-Methode werden zu einem späteren Zeitpunkt in dieser exemplarischen Vorgehensweise hinzugefügt.

##### <a name="to-add-error-handling-for-the-concurrency-error"></a>So fügen Sie Fehlerbehandlungscode für den Parallelitätsfehler hinzu

1.  Fügen Sie unter der `Form1_Load`-Methode folgenden Code hinzu:

     [!code-csharp[VbRaddataConcurrency#1](../data-tools/codesnippet/CSharp/handle-a-concurrency-exception_1.cs)]
     [!code-vb[VbRaddataConcurrency#1](../data-tools/codesnippet/VisualBasic/handle-a-concurrency-exception_1.vb)]

2.  Ersetzen Sie die `CustomersBindingNavigatorSaveItem_Click`-Methode, um die `UpdateDatabase`-Methode aufzurufen, sodass sich Folgendes ergibt:

     [!code-csharp[VbRaddataConcurrency#2](../data-tools/codesnippet/CSharp/handle-a-concurrency-exception_2.cs)]
     [!code-vb[VbRaddataConcurrency#2](../data-tools/codesnippet/VisualBasic/handle-a-concurrency-exception_2.vb)]

### <a name="display-choices-to-the-user"></a>Zeigen Sie die Auswahloptionen für den Benutzer
 Durch den soeben geschriebenen Code wird die `CreateMessage`-Prozedur aufgerufen, um Fehlerinformationen für den Benutzer anzuzeigen. In dieser exemplarischen Vorgehensweise verwenden Sie ein Meldungsfeld an, um die verschiedenen Versionen des Datensatzes für den Benutzer anzuzeigen. Dadurch kann der Benutzer auswählen, ob den Datensatz mit den Änderungen überschreibt oder die Bearbeitung abbricht. Wenn der Benutzer durch Klicken auf eine Schaltfläche eine Option im Meldungsfeld ausgewählt hat, wird die Antwort an die `ProcessDialogResult`-Methode übergeben.

##### <a name="to-create-the-message-to-display-to-the-user"></a>So erstellen Sie die Meldung, die dem Benutzer angezeigt wird

-   Erstellen Sie die Nachricht durch den folgenden Code Hinzufügen der **Code-Editor**. Geben Sie diesen Code unter der `UpdateDatabase`-Methode ein.

     [!code-csharp[VbRaddataConcurrency#4](../data-tools/codesnippet/CSharp/handle-a-concurrency-exception_3.cs)]
     [!code-vb[VbRaddataConcurrency#4](../data-tools/codesnippet/VisualBasic/handle-a-concurrency-exception_3.vb)]

### <a name="process-the-users-response"></a>Verarbeitet die Antwort des Benutzers
 Darüber hinaus benötigen Sie Code zum Verarbeiten der Antwort des Benutzers in der MessageBox. Die Optionen sind entweder auf den aktuellen Datensatz in der Datenbank mit der vorgeschlagenen Änderung überschreiben oder die lokalen Änderungen verwerfen und die Datentabelle mit dem Datensatz, die aktuell in der Datenbank zu aktualisieren. Wenn der Benutzer möchte, die <xref:System.Data.DataTable.Merge%2A> -Methode aufgerufen wird und die *PreserveChanges* Argument festgelegt wird, um `true`. Dies bewirkt, dass den Update-Versuch erfolgreich ist, werden, da die ursprüngliche Version des Datensatzes nun den Datensatz in der Datenbank entspricht.

##### <a name="to-process-the-user-input-from-the-message-box"></a>So verarbeiten Sie die Benutzereingabe aus dem Meldungsfeld

-   Fügen Sie den folgenden Code unter dem Code, der im vorherigen Abschnitt hinzugefügt wurde.

     [!code-csharp[VbRaddataConcurrency#3](../data-tools/codesnippet/CSharp/handle-a-concurrency-exception_4.cs)]
     [!code-vb[VbRaddataConcurrency#3](../data-tools/codesnippet/VisualBasic/handle-a-concurrency-exception_4.vb)]

## <a name="test-the-form"></a>Testen Sie das Formular
 Sie können das Formular jetzt testen, um sicherzustellen, dass das Verhalten wie erwartet ausfällt. Um eine Parallelitätsverletzung zu simulieren, müssen Sie Daten in der Datenbank ändern, nachdem Sie das NorthwindDataSet gefüllt haben.

#### <a name="to-test-the-form"></a>So testen Sie das Formular

1.  Wählen Sie **F5** um die Anwendung auszuführen.

2.  Wenn das Formular angezeigt wird, führen Sie es weiterhin, und wechseln Sie zur Visual Studio-IDE.

3.  Auf der **Ansicht** Menü wählen **Server-Explorer**.

4.  In **Server-Explorer**, erweitern Sie die Verbindung Ihrer Anwendung verwenden, und erweitern Sie dann die **Tabellen** Knoten.

5.  Mit der rechten Maustaste die **Kunden** Tabelle, und wählen Sie dann **Tabellendaten anzeigen**.

6.  Im ersten Datensatz (`ALFKI`) ändern `ContactName` auf `Maria Anders2`.

    > [!NOTE]
    >  Navigieren Sie zu einer anderen Zeile, um einen Commit für die Änderung auszuführen.

7.  Wechseln Sie zum Formular `ConcurrencyWalkthrough`, das immer noch ausgeführt wird.

8.  Im ersten Datensatz auf dem Formular (`ALFKI`), ändern Sie`ContactName` auf `Maria Anders1`.

9. Wählen Sie die **speichern** Schaltfläche.

     Der Parallelitätsfehler wird ausgelöst, und das Meldungsfeld wird angezeigt.

10. Auswählen von **keine** wird die Aktualisierung abgebrochen und das Dataset mit den Werten, die derzeit in der Datenbank werden aktualisiert. Auswählen von **Ja** den vorgeschlagenen Wert in die Datenbank geschrieben.

## <a name="see-also"></a>Siehe auch

- [Rückspeichern von Daten in der Datenbank](../data-tools/save-data-back-to-the-database.md)