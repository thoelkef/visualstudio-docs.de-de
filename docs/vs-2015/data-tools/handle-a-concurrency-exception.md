---
title: Behandeln einer Parallelitäts Ausnahme | Microsoft-Dokumentation
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-data-tools
ms.topic: conceptual
dev_langs:
- VB
- CSharp
- C++
- aspx
helpviewer_keywords:
- concurrency control, exceptions
- datasets [Visual Basic], errors
- exception handling, concurrency issues
- data concurrency, walkthroughs
- updating datasets, errors
- concurrency control, walkthroughs
ms.assetid: 73ee9759-0a90-48a9-bf7b-9d6fc17bff93
caps.latest.revision: 27
author: jillre
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: 1b3f9bdaf5107f805100b938212128d42c0263dd
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 09/02/2020
ms.locfileid: "72670041"
---
# <a name="handle-a-concurrency-exception"></a>Behandeln einer Parallelitätsausnahme
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Parallelitätsausnahmen (<xref:System.Data.DBConcurrencyException>) werden ausgelöst, wenn zwei Benutzer gleichzeitig versuchen, dieselben Daten in einer Datenbank zu ändern. In dieser exemplarischen Vorgehensweise erstellen Sie eine Windows-Anwendung, die veranschaulicht, wie Sie ein Abfangen <xref:System.Data.DBConcurrencyException> , die Zeile, die den Fehler verursacht hat, finden und eine Strategie zur Behandlung der Anwendung erlernen.

 Diese exemplarische Vorgehensweise enthält folgende Vorgänge:

1. Erstellen Sie ein neues **Windows-Anwendungs** Projekt.

2. Erstellen eines neuen Datasets auf der Grundlage der Tabelle `Customers` der Datenbank Northwind.

3. Erstellen eines Formulars mit einer <xref:System.Windows.Forms.DataGridView> für die Anzeige der Daten.

4. Füllen eines Datasets mit Daten aus der Tabelle `Customers` in der Datenbank Northwind.

5. Verwenden Sie die [Visual Database Tools](https://msdn.microsoft.com/6b145922-2f00-47db-befc-bf351b4809a1) in Visual Studio, um direkt auf die `Customers` Datentabelle zuzugreifen und einen Datensatz zu ändern.

6. Ändern Sie denselben Datensatz in einen anderen Wert, aktualisieren Sie das DataSet, und versuchen Sie, die Änderungen in die Datenbank zu schreiben, was zu einem Parallelitäts Fehler führt.

7. Fangen Sie den Fehler ab, und zeigen Sie anschließend die verschiedenen Versionen des Datensatzes an, um festzulegen, ob die Aktualisierung der Datenbank fortgesetzt oder abgebrochen werden soll.

## <a name="prerequisites"></a>Voraussetzungen
 Für die Durchführung dieser exemplarischen Vorgehensweise benötigen Sie Folgendes:

- Zugriff auf die Beispieldatenbank Northwind mit der Berechtigung zum Durchführen von Aktualisierungen.

> [!NOTE]
> Die angezeigten Dialogfelder und Menübefehle können sich je nach den aktiven Einstellungen oder der von Ihnen verwendeten Edition von den in der Hilfe beschriebenen unterscheiden. Klicken Sie im Menü **Extras** auf **Einstellungen importieren und exportieren** , um die Einstellungen zu ändern. Weitere Informationen finden Sie unter [Anpassen der Entwicklungseinstellungen in Visual Studio](https://msdn.microsoft.com/22c4debb-4e31-47a8-8f19-16f328d7dcd3).

## <a name="create-a-new-project"></a>Erstellen eines neuen Projekts
 Erstellen Sie in dieser exemplarischen Vorgehensweise zunächst eine neue Windows-Anwendung.

#### <a name="to-create-a-new-windows-application-project"></a>So erstellen Sie ein neues Windows-Anwendungsprojekt

1. Erstellen Sie im Menü **Datei** ein neues Projekt.

2. Wählen Sie im Bereich **Projekttypen** eine Programmiersprache aus.

3. Wählen Sie im Bereich **Vorlagen** die Option **Windows-Anwendung** aus.

4. Benennen Sie das Projekt `ConcurrencyWalkthrough` , und wählen Sie dann **OK**aus.

     Visual Studio fügt das Projekt **Projektmappen-Explorer** hinzu und zeigt im Designer ein neues Formular an.

## <a name="create-the-northwind-dataset"></a>Erstellen des Northwind-Datasets
 In diesem Abschnitt erstellen Sie ein DataSet mit dem Namen `NorthwindDataSet` .

#### <a name="to-create-the-northwinddataset"></a>So erstellen Sie das NorthwindDataset

1. Wählen Sie im Menü **Daten** die Option **neue Datenquelle hinzufügen**aus.

     Der [Assistent zum Konfigurieren von Datenquellen](https://msdn.microsoft.com/library/c4df7de5-5da0-4064-940c-761dd6d9e28f) wird geöffnet.

2. Wählen Sie auf dem Bildschirm **Daten Quellentyp auswählen**die Option **Datenbank**aus.

3. Wählen Sie in der Liste der verfügbaren Verbindungen eine Verbindung mit der Beispieldatenbank Northwind aus. Wenn die Verbindung in der Liste der Verbindungen nicht verfügbar ist, wählen Sie**neue Verbindung** aus.

    > [!NOTE]
    > Wenn Sie eine Verbindung mit einer lokalen Datenbankdatei herstellen, wählen Sie **Nein** aus, wenn Sie gefragt werden, ob Sie die Datei dem Projekt hinzufügen möchten.

4. Wählen Sie auf der Seite **Verbindungs Zeichenfolge in der Anwendungs Konfigurationsdatei speichern**die Option **weiter**aus.

5. Erweitern Sie den Knoten **Tabellen** , und wählen Sie die `Customers` Tabelle aus. Der Standardname für das Dataset sollte `NorthwindDataSet` sein.

6. Wählen Sie **Fertig** stellen aus, um das DataSet dem Projekt hinzuzufügen.

## <a name="create-a-data-bound-datagridview-control"></a>Erstellen eines Daten gebundenen DataGridView-Steuer Elements
 In diesem Abschnitt erstellen Sie einen, <xref:System.Windows.Forms.DataGridView> indem Sie das **Customers** -Element aus dem **Datenquellen** Fenster auf das Windows Form ziehen.

#### <a name="to-create-a-datagridview-control-that-is-bound-to-the-customers-table"></a>So erstellen Sie ein DataGridView-Steuerelement, das an die Tabelle Customers gebunden ist

1. Wählen Sie im Menü **Daten** die Option **Datenquellen anzeigen** aus, um das **Fenster Datenquellen**zu öffnen.

2. Erweitern Sie im Fenster **Datenquellen** den Knoten **NorthwindDataSet** , und wählen Sie dann die Tabelle **Customers** aus.

3. Wählen Sie im Tabellen Knoten den Pfeil nach unten aus, und wählen Sie dann in der Dropdown Liste die Option **DataGridView** aus.

4. Ziehen Sie die Tabelle auf einen leeren Bereich des Formulars.

     Ein <xref:System.Windows.Forms.DataGridView> -Steuerelement mit dem Namen `CustomersDataGridView` und ein <xref:System.Windows.Forms.BindingNavigator> `CustomersBindingNavigator` benanntes werden dem Formular hinzugefügt, das an den gebunden ist <xref:System.Windows.Forms.BindingSource> . Diese ist in, wird wiederum an die- `Customers` Tabelle im gebunden `NorthwindDataSet` .

## <a name="test-the-form"></a>Testen des Formulars
 Sie können das Formular jetzt testen, um sicherzustellen, dass das Verhalten bisher wie erwartet ausfällt.

#### <a name="to-test-the-form"></a>So testen Sie das Formular

1. Drücken Sie **F5** , um die Anwendung auszuführen.

     Das Formular wird mit einem-Steuerelement angezeigt <xref:System.Windows.Forms.DataGridView> , das mit Daten aus der-Tabelle gefüllt ist `Customers` .

2. Wählen Sie im Menü **Debuggen** die Option**Debuggen Abbrechen**.

## <a name="handleconcurrency-errors"></a>Fehler bei der typparallelität
 Die Art und Weise, wie Sie Fehler behandeln, hängt von den spezifischen Geschäftsregeln ab, die Ihre Anwendung steuern. In dieser exemplarischen Vorgehensweise verwenden wir die folgende Strategie als Beispiel für die Behandlung des Parallelitäts Fehlers.

 Die applicationpräsentiert den Benutzer mit drei Versionen des Datensatzes:

- Den aktuellen Datensatz in der Datenbank

- Der ursprüngliche Datensatz, der in das DataSet geladen wird.

- Die vorgeschlagenen Änderungen im Dataset

  Der Benutzer kann dann die Datenbank mit der vorgeschlagenen Version überschreiben oder aber die Aktualisierung abbrechen und das Dataset mit den neuen Werten aus der Datenbank aktualisieren.

#### <a name="to-enable-the-handling-of-concurrency-errors"></a>So aktivieren Sie die Behandlung von Parallelitätsfehlern

1. Erstellen Sie einen benutzerdefinierten Fehlerhandler.

2. Zeigen Sie die Auswahloptionen für den Benutzer an.

3. Verarbeiten Sie die Eingabe des Benutzers.

4. Senden Sie die Aktualisierung erneut, oder setzen Sie die Daten im Dataset zurück.

### <a name="addcode-to-handle-the-concurrency-exception"></a>Addcode zur Behandlung der Parallelitäts Ausnahme
 Wenn Sie versuchen, ein Update auszuführen, und eine Ausnahme ausgelöst wird, sollten Sie in der Regel mit den Informationen arbeiten, die von der ausgelöste Ausnahme bereitgestellt werden.

 In diesem Abschnitt fügen Sie Code hinzu, mit dem versucht wird, die Datenbank zu aktualisieren. Sie können auch alle ausgelösten <xref:System.Data.DBConcurrencyException> Ausnahmen sowie alle anderen Ausnahmen verarbeiten.

> [!NOTE]
> Die `CreateMessage`-Methode und die `ProcessDialogResults`-Methode werden zu einem späteren Zeitpunkt in dieser exemplarischen Vorgehensweise hinzugefügt.

##### <a name="to-add-error-handling-for-the-concurrency-error"></a>So fügen Sie Fehlerbehandlungscode für den Parallelitätsfehler hinzu

1. Fügen Sie unter der `Form1_Load`-Methode folgenden Code hinzu:

     [!code-csharp[VbRaddataConcurrency#1](../snippets/csharp/VS_Snippets_VBCSharp/VbRaddataConcurrency/CS/Form1.cs#1)]
     [!code-vb[VbRaddataConcurrency#1](../snippets/visualbasic/VS_Snippets_VBCSharp/VbRaddataConcurrency/VB/Form1.vb#1)]

2. Ersetzen Sie die `CustomersBindingNavigatorSaveItem_Click`-Methode, um die `UpdateDatabase`-Methode aufzurufen, sodass sich Folgendes ergibt:

     [!code-csharp[VbRaddataConcurrency#2](../snippets/csharp/VS_Snippets_VBCSharp/VbRaddataConcurrency/CS/Form1.cs#2)]
     [!code-vb[VbRaddataConcurrency#2](../snippets/visualbasic/VS_Snippets_VBCSharp/VbRaddataConcurrency/VB/Form1.vb#2)]

### <a name="displaychoices-to-the-user"></a>Display Choices für den Benutzer
 Durch den soeben geschriebenen Code wird die `CreateMessage`-Prozedur aufgerufen, um Fehlerinformationen für den Benutzer anzuzeigen. In dieser exemplarischen Vorgehensweise verwenden Sie ein Meldungs Feld, um die verschiedenen Versionen des Datensatzes für den Benutzer anzuzeigen. Dadurch kann der Benutzer auswählen, ob der Datensatz mit den Änderungen überschrieben oder der Bearbeitungsvorgang abgebrochen werden soll. Wenn der Benutzer durch Klicken auf eine Schaltfläche eine Option im Meldungsfeld ausgewählt hat, wird die Antwort an die `ProcessDialogResult`-Methode übergeben.

##### <a name="to-create-the-message-to-display-to-the-user"></a>So erstellen Sie die Meldung, die dem Benutzer angezeigt wird

- Erstellen Sie die Meldung, indem Sie dem **Code-Editor** folgenden Code hinzufügen. Geben Sie diesen Code unter der `UpdateDatabase`-Methode ein.

     [!code-csharp[VbRaddataConcurrency#4](../snippets/csharp/VS_Snippets_VBCSharp/VbRaddataConcurrency/CS/Form1.cs#4)]
     [!code-vb[VbRaddataConcurrency#4](../snippets/visualbasic/VS_Snippets_VBCSharp/VbRaddataConcurrency/VB/Form1.vb#4)]

### <a name="process-the-users-response"></a>Verarbeiten der Antwort des Benutzers
 Außerdem benötigen Sie Code, um die Antwort des Benutzers auf das Meldungs Feld zu verarbeiten. Die Optionen lauten entweder, um den aktuellen Datensatz in der Datenbank mit der vorgeschlagenen Änderung zu überschreiben, oder die lokalen Änderungen verwerfen und die Datentabelle mit dem Datensatz aktualisieren, der sich derzeit in der Datenbank befindet. Wenn der Benutzer ja auswählt, <xref:System.Data.DataTable.Merge%2A> wird die-Methode mit dem *preserveChanges* -Argument aufgerufen, das auf festgelegt ist `true` . Dies bewirkt, dass der Aktualisierungs Versuch erfolgreich ist, da die ursprüngliche Version des Datensatzes jetzt mit dem Datensatz in der Datenbank übereinstimmt.

##### <a name="to-process-the-user-input-from-the-message-box"></a>So verarbeiten Sie die Benutzereingabe aus dem Meldungsfeld

- Fügen Sie unter dem Code, der im vorherigen Abschnitt hinzugefügt wurde, den folgenden Code hinzu.

     [!code-csharp[VbRaddataConcurrency#3](../snippets/csharp/VS_Snippets_VBCSharp/VbRaddataConcurrency/CS/Form1.cs#3)]
     [!code-vb[VbRaddataConcurrency#3](../snippets/visualbasic/VS_Snippets_VBCSharp/VbRaddataConcurrency/VB/Form1.vb#3)]

## <a name="test-the-form"></a>Testen des Formulars
 Sie können das Formular jetzt testen, um sicherzustellen, dass das Verhalten wie erwartet ausfällt. Um eine Parallelitätsverletzung zu simulieren, müssen Sie Daten in der Datenbank ändern, nachdem Sie das NorthwindDataSet gefüllt haben.

#### <a name="to-test-the-form"></a>So testen Sie das Formular

1. Drücken Sie **F5** , um die Anwendung auszuführen.

2. Wenn das Formular angezeigt wird, führen Sie es weiterhin, und wechseln Sie zur Visual Studio-IDE.

3. Wählen Sie im Menü **Ansicht** den Eintrag **Server-Explorer** aus.

4. Erweitern Sie im **Server-Explorer** die Verbindung, die von der Anwendung verwendet wird, und erweitern Sie den Knoten **Tabellen**.

5. Klicken Sie mit der rechten Maustaste auf die Tabelle **Customers** , und wählen Sie dann **Tabellendaten anzeigen**aus.

6. Ändern Sie im ersten Datensatz ( `ALFKI` ) `ContactName` in `Maria Anders2` .

    > [!NOTE]
    > Navigieren Sie zu einer anderen Zeile, um einen Commit für die Änderung auszuführen.

7. Wechseln Sie zum Formular `ConcurrencyWalkthrough`, das immer noch ausgeführt wird.

8. Ändern Sie im ersten Datensatz im Formular ( `ALFKI` ) in `ContactName` `Maria Anders1` .

9. Klicken Sie auf die Schaltfläche **Speichern**.

     Der Parallelitätsfehler wird ausgelöst, und das Meldungsfeld wird angezeigt.

10. Wenn Sie **Nein** auswählen, wird das Update abgebrochen, und das DataSet wird mit den Werten aktualisiert, die derzeit in der Datenbank gespeichert sind. Wenn Sie **Ja** auswählen, wird der vorgeschlagene Wert in die Datenbank geschrieben.

## <a name="see-also"></a>Weitere Informationen

- [Rückspeichern von Daten in der Datenbank](../data-tools/save-data-back-to-the-database.md)