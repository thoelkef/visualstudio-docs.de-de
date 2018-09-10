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
ms.openlocfilehash: 6aca4815672d700fbea9d489f6316b8b0337f8df
ms.sourcegitcommit: 3a11feebad45a0dd4ac45efcbfdf172fce46e1de
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 08/07/2018
ms.locfileid: "39582332"
---
# <a name="handle-a-concurrency-exception"></a>Behandeln einer Parallelitätsausnahme

Parallelitätsausnahmen (<xref:System.Data.DBConcurrencyException?displayProperty=fullName>) werden ausgelöst, wenn zwei Benutzer gleichzeitig versuchen, dieselben Daten in einer Datenbank zu ändern. In dieser exemplarischen Vorgehensweise erstellen Sie eine Windows-Anwendung, die veranschaulicht, wie zum Abfangen einer <xref:System.Data.DBConcurrencyException>, suchen Sie die Zeile, die den Fehler verursacht hat, und erfahren Sie, eine Strategie zum verarbeiten.

Diese exemplarische Vorgehensweise enthält folgende Vorgänge:

1. Erstellen Sie ein neues **Windows Forms-Anwendungsprojekt**.

2. Erstellen Sie ein neues Dataset basierend auf der Northwind-Kundentabelle.

3. Erstellen eines Formulars mit einer <xref:System.Windows.Forms.DataGridView> für die Anzeige der Daten.

4. Füllen eines Datasets mit Daten aus der Customers-Tabelle in der Datenbank Northwind.

5. Verwenden der **Tabellendaten anzeigen** feature **Server-Explorer** Zugriff auf Daten der Customers-Tabelle und einen Datensatz zu ändern.

6. Ändern Sie den gleichen Datensatz auf einen anderen Wert, aktualisieren Sie das Dataset und versuchen Sie, die Änderungen in der Datenbank zu schreiben, was zu einem Parallelitätsfehler führt.

7. Fangen Sie den Fehler, und anzuzeigen Sie die verschiedenen Versionen des Datensatzes, damit der Benutzer bestimmen, ob weiterhin, und Aktualisieren der Datenbank, oder Abbrechen Sie das Update.

## <a name="prerequisites"></a>Erforderliche Komponenten

In dieser exemplarischen Vorgehensweise verwendet SQL Server Express LocalDB und der Beispieldatenbank Northwind.

1. Wenn Sie SQL Server Express LocalDB nicht haben, installieren Sie es entweder über die [Downloadseite für SQL Server Express](https://www.microsoft.com/sql-server/sql-server-editions-express), oder über die **Visual Studio-Installer**. In der **Visual Studio-Installer**, können Sie SQL Server Express LocalDB installieren, als Teil der **datenspeicherung und-Verarbeitung** Workload oder als eine einzelne Komponente.

2. Installieren der Northwind-Beispieldatenbank mit folgenden Schritten:

    1. Öffnen Sie in Visual Studio die **Objekt-Explorer von SQL Server** Fenster. (Objekt-Explorer von SQL Server installiert ist, als Teil der **datenspeicherung und-Verarbeitung** Workload im Visual Studio-Installer.) Erweitern Sie die **SQL Server** Knoten. Mit der rechten Maustaste auf der LocalDB-Instanz, und wählen Sie **neue Abfrage**.

       Ein Abfrage-Editor-Fenster wird geöffnet.

    2. Kopieren der [Northwind Transact-SQL-Skript](https://github.com/MicrosoftDocs/visualstudio-docs/blob/master/docs/data-tools/samples/northwind.sql?raw=true) in die Zwischenablage. Dieses T-SQL-Skript wird die Northwind-Datenbank von Grund auf neu erstellt und mit Daten aufgefüllt.

    3. Fügen Sie das T-SQL-Skript im Abfrage-Editor, und wählen Sie dann die **Execute** Schaltfläche.

       Klicken Sie nach kurzer Zeit die Ausführung die Abfrage abgeschlossen ist, und die Northwind-Datenbank wird erstellt.

> [!NOTE]
> Die angezeigten Dialogfelder und Befehle im Menü angezeigten unterscheiden sich von den in der Hilfe beschriebenen, je nach Ihren aktiven Einstellungen oder die Edition, die Sie verwenden. Klicken Sie im Menü **Extras** auf **Einstellungen importieren und exportieren** , um die Einstellungen zu ändern. Weitere Informationen finden Sie unter [Personalisieren von Visual Studio-IDE](../ide/personalizing-the-visual-studio-ide.md).

## <a name="create-a-new-project"></a>Erstellt ein neues Projekt

Beginnen Sie mit der Erstellung einer neuen Windows Forms-Anwendung:

1. In Visual Studio auf die **Datei** , wählen Sie im Menü **neu** > **Projekt**.

2. Erweitern Sie entweder **Visual C#-** oder **Visual Basic** wählen Sie im linken Bereich **Windows Desktop**.

3. Wählen Sie im mittleren Bereich die **Windows Forms-App** Projekttyp.

4. Nennen Sie das Projekt **ConcurrencyWalkthrough**, und wählen Sie dann **OK**.

     Die **ConcurrencyWalkthrough** Projekt wird erstellt und hinzugefügt **Projektmappen-Explorer**, und ein neues Formular im Designer geöffnet.

## <a name="create-the-northwind-dataset"></a>Erstellen des Datasets Northwind

Als Nächstes erstellen Sie ein Dataset namens **NorthwindDataSet**:

1. Auf der **Daten** Menü wählen **neue Datenquelle hinzufügen**.

   Der Konfigurations-Assistent wird geöffnet.

2. Auf der **wählen Sie einen Datenquellentyp** auf **Datenbank**.

   ![Datenquellen-Assistenten in Visual Studio-Konfiguration](media/data-source-configuration-wizard.png)

3. Wählen Sie eine Verbindung mit der Northwind-Beispieldatenbank an, aus der Liste der verfügbaren Verbindungen. Wenn die Verbindung nicht in der Liste der Verbindungen verfügbar ist, wählen Sie **neue Verbindung**.

    > [!NOTE]
    > Wenn Sie eine Verbindung mit einer lokalen Datenbankdatei herstellen, wählen Sie **keine** Wenn gefragt werden, wenn Sie dies tun würden Sie die Datei zu Ihrem Projekt hinzufügen möchten.

4. Auf der **Verbindungszeichenfolge in der Anwendungskonfigurationsdatei speichern** auf **Weiter**.

5. Erweitern Sie die **Tabellen** Knoten, und wählen die **Kunden** Tabelle. Der Standardname für das Dataset muss **NorthwindDataSet**.

6. Wählen Sie **Fertig stellen** des Datasets zum Projekt hinzufügen.

## <a name="create-a-data-bound-datagridview-control"></a>Erstellen von einem datengebundenen DataGridView-Steuerelement

In diesem Abschnitt erstellen Sie eine <xref:System.Windows.Forms.DataGridView?displayProperty=nameWithType> durch Ziehen der **Kunden** Element aus der **Datenquellen** auf das Windows-Formular.

1. Auf der **Daten** im Menü wählen **Datenquellen anzeigen** zum Öffnen der **Fensters "Datenquellen"**.

2. In der **Datenquellen** Fenster, erweitern Sie die **NorthwindDataSet** Knoten, und wählen Sie dann die **Kunden** Tabelle.

3. Wählen Sie den Pfeil nach unten für den Tabellenknoten, und wählen Sie dann **DataGridView** in der Dropdown-Liste.

4. Ziehen Sie die Tabelle auf einen leeren Bereich des Formulars.

     Ein <xref:System.Windows.Forms.DataGridView> Steuerelement mit dem Namen **CustomersDataGridView**, und ein <xref:System.Windows.Forms.BindingNavigator> mit dem Namen **CustomersBindingNavigator**, werden hinzugefügt, um das Formular, das gebunden ist die <xref:System.Windows.Forms.BindingSource>. Dies wird wiederum zur Customers-Tabelle im NorthwindDataSet gebunden.

## <a name="test-the-form"></a>Testen Sie das Formular

Sie können nun testen, dass das Formular, um sicherzustellen, dass sie sich bis zu diesem Zeitpunkt erwartungsgemäß verhält:

1. Wählen Sie **F5** zum Ausführen der Anwendung.

     Das Formular wird mit einem <xref:System.Windows.Forms.DataGridView> Steuerelement, das mit Daten aus der Customers-Tabelle gefüllt wird.

2. Auf der **Debuggen** , wählen Sie im Menü **Debuggen beenden**.

## <a name="handle-concurrency-errors"></a>Behandeln von Parallelitätsfehlern

Wie Sie Fehler behandeln, hängt von den jeweiligen Geschäftsregeln, die Ihre Anwendung steuern. In dieser exemplarischen Vorgehensweise verwenden wir die folgende Strategie als Beispiel für das Behandeln des parallelitätsfehlers.

Die Anwendung stellt dem Benutzer drei Versionen des Datensatzes:

- Der aktuelle Datensatz in der Datenbank

- Der ursprüngliche Datensatz, der in das Dataset geladen wird

- Die vorgeschlagenen Änderungen im dataset

Der Benutzer kann dann die Datenbank mit der vorgeschlagenen Version überschreiben oder die Aktualisierung abzubrechen und das Dataset mit den neuen Werten aus der Datenbank aktualisieren.

### <a name="to-enable-the-handling-of-concurrency-errors"></a>So aktivieren Sie die Behandlung von Parallelitätsfehlern

1. Erstellen Sie einen benutzerdefinierten Fehlerhandler.

2. Zeigen Sie die Auswahloptionen für den Benutzer an.

3. Verarbeiten Sie die Eingabe des Benutzers.

4. Senden Sie die Aktualisierung erneut, oder setzen Sie die Daten im Dataset zurück.

### <a name="add-code-to-handle-the-concurrency-exception"></a>Hinzufügen von Code zum Behandeln von Parallelitätsausnahmen

Wenn Sie versuchen, ein Update ausführen und eine Ausnahme ausgelöst wird, möchten Sie in der Regel etwas mit den Informationen, die mit der ausgelösten Ausnahme bereitgestellt wird. In diesem Abschnitt fügen Sie Code, der versucht, die zum Aktualisieren der Datenbank hinzu. Sie können auch behandeln alle <xref:System.Data.DBConcurrencyException> , die möglicherweise ausgelöst werden, sowie alle anderen Ausnahmen.

> [!NOTE]
> Die `CreateMessage` und `ProcessDialogResults` Methoden werden weiter unten in dieser exemplarischen Vorgehensweise hinzugefügt.

1. Fügen Sie unter der `Form1_Load`-Methode folgenden Code hinzu:

     [!code-csharp[VbRaddataConcurrency#1](../data-tools/codesnippet/CSharp/handle-a-concurrency-exception_1.cs)]
     [!code-vb[VbRaddataConcurrency#1](../data-tools/codesnippet/VisualBasic/handle-a-concurrency-exception_1.vb)]

2. Ersetzen Sie die `CustomersBindingNavigatorSaveItem_Click`-Methode, um die `UpdateDatabase`-Methode aufzurufen, sodass sich Folgendes ergibt:

     [!code-csharp[VbRaddataConcurrency#2](../data-tools/codesnippet/CSharp/handle-a-concurrency-exception_2.cs)]
     [!code-vb[VbRaddataConcurrency#2](../data-tools/codesnippet/VisualBasic/handle-a-concurrency-exception_2.vb)]

### <a name="display-choices-to-the-user"></a>Optionen für den Benutzer anzeigen

Durch den soeben geschriebenen Code wird die `CreateMessage`-Prozedur aufgerufen, um Fehlerinformationen für den Benutzer anzuzeigen. In dieser exemplarischen Vorgehensweise verwenden Sie ein Meldungsfeld, um die verschiedenen Versionen des Datensatzes für den Benutzer anzuzeigen. Dadurch kann der Benutzer auswählen, ob der Datensatz mit den Änderungen überschreiben oder die Bearbeitung abbricht. Wenn der Benutzer durch Klicken auf eine Schaltfläche eine Option im Meldungsfeld ausgewählt hat, wird die Antwort an die `ProcessDialogResult`-Methode übergeben.

Erstellen der Nachricht durch den folgenden Code zum Hinzufügen der **Code-Editor**. Geben Sie diesen Code unter der `UpdateDatabase` Methode:

     [!code-csharp[VbRaddataConcurrency#4](../data-tools/codesnippet/CSharp/handle-a-concurrency-exception_3.cs)]
     [!code-vb[VbRaddataConcurrency#4](../data-tools/codesnippet/VisualBasic/handle-a-concurrency-exception_3.vb)]

### <a name="process-the-users-response"></a>Verarbeitet die Antwort des Benutzers

Außerdem benötigen Sie Code zum Verarbeiten der Antwort des Benutzers in der MessageBox. Die Optionen sind entweder auf den aktuellen Datensatz in der Datenbank mit der vorgeschlagenen Änderung überschreiben oder die lokalen Änderungen verwerfen und aktualisieren Sie die Datentabelle mit dem Datensatz, der derzeit in der Datenbank vorhanden ist. Wenn der Benutzer **Ja**, wird die <xref:System.Data.DataTable.Merge%2A> Methode wird aufgerufen, mit der *PreserveChanges* Argument festgelegt wird, um **"true"**. Dies bewirkt, dass den Updateversuch, die erfolgreich ist, muss, da die ursprüngliche Version des Datensatzes nun der Eintrag in der Datenbank übereinstimmt.

Fügen Sie den folgenden Code unter dem Code, der im vorherigen Abschnitt hinzugefügt wurde:

     [!code-csharp[VbRaddataConcurrency#3](../data-tools/codesnippet/CSharp/handle-a-concurrency-exception_4.cs)]
     [!code-vb[VbRaddataConcurrency#3](../data-tools/codesnippet/VisualBasic/handle-a-concurrency-exception_4.vb)]

## <a name="test-the-form"></a>Testen Sie das Formular

Sie können das Formular jetzt testen, um sicherzustellen, dass das Verhalten wie erwartet ausfällt. Um eine parallelitätsverletzung zu simulieren, ändern Sie Daten in der Datenbank, nachdem Sie das NorthwindDataSet gefüllt.

1. Wählen Sie **F5** zum Ausführen der Anwendung.

2. Wenn das Formular angezeigt wird, führen Sie es weiterhin, und wechseln Sie zur Visual Studio-IDE.

3. Auf der **Ansicht** Menü wählen **Server-Explorer**.

4. In **Server-Explorer**, erweitern Sie die Verbindung Ihrer Anwendung verwenden, und erweitern Sie dann die **Tabellen** Knoten.

5. Mit der rechten Maustaste die **Kunden** Tabelle, und wählen Sie dann **Tabellendaten anzeigen**.

6. Im ersten Datensatz (**ALFKI**), ändern Sie **ContactName** zu **Maria Anders2**.

    > [!NOTE]
    > Navigieren Sie zu einer anderen Zeile, um einen Commit für die Änderung auszuführen.

7. Wechseln Sie zu dem Formular die ConcurrencyWalkthrough ausgeführt wird.

8. Im ersten Datensatz auf dem Formular (**ALFKI**), ändern Sie **ContactName** zu **Maria Anders1**.

9. Wählen Sie die **speichern** Schaltfläche.

     Der Parallelitätsfehler wird ausgelöst, und das Meldungsfeld wird angezeigt.

   Auswählen von **keine** wird die Aktualisierung abgebrochen und das Dataset mit den Werten, die derzeit in der Datenbank werden aktualisiert. Auswählen von **Ja** den vorgeschlagenen Wert in die Datenbank geschrieben.

## <a name="see-also"></a>Siehe auch

- [Rückspeichern von Daten in der Datenbank](../data-tools/save-data-back-to-the-database.md)