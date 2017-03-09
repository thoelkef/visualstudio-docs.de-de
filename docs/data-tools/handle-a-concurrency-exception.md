---
title: "Exemplarische Vorgehensweise: Behandeln einer Parallelit&#228;tsausnahme | Microsoft Docs"
ms.custom: ""
ms.date: "09/21/2016"
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
  - "Parallelitätssteuerung, Ausnahmen"
  - "Parallelitätssteuerung, Exemplarische Vorgehensweisen"
  - "Datenparallelität, Exemplarische Vorgehensweisen"
  - "Datasets [Visual Basic], Fehler"
  - "Ausnahmebehandlung, Parallelitätsprobleme"
  - "Aktualisieren von Datasets, Fehler"
ms.assetid: 73ee9759-0a90-48a9-bf7b-9d6fc17bff93
caps.latest.revision: 23
caps.handback.revision: 19
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# Exemplarische Vorgehensweise: Behandeln einer Parallelit&#228;tsausnahme
Parallelitätsausnahmen \(<xref:System.Data.DBConcurrencyException>\) werden ausgelöst, wenn zwei Benutzer gleichzeitig versuchen, dieselben Daten in einer Datenbank zu ändern.  In dieser exemplarischen Vorgehensweise erstellen Sie eine Windows\-Anwendung zum Abfangen einer <xref:System.Data.DBConcurrencyException>, zum Ermitteln der Zeile, die den Fehler ausgelöst hat, und zum Anwenden einer Strategie zur Fehlerbehandlung.  
  
 Diese exemplarische Vorgehensweise enthält folgende Vorgänge:  
  
1.  Erstellen eines neuen Projekts vom Typ **Windows\-Anwendung**  
  
2.  Erstellen eines neuen Datasets auf der Grundlage der Tabelle `Customers` der Datenbank Northwind.  
  
3.  Erstellen eines Formulars mit einer <xref:System.Windows.Forms.DataGridView> für die Anzeige der Daten.  
  
4.  Füllen eines Datasets mit Daten aus der Tabelle `Customers` in der Datenbank Northwind.  
  
5.  Nach dem Füllen des Datasets verwenden Sie die [Visual Database Tools](http://msdn.microsoft.com/de-de/6b145922-2f00-47db-befc-bf351b4809a1) in Visual Studio, um direkt auf die Datentabelle `Customers` zuzugreifen und einen Datensatz zu ändern.  
  
6.  Ändern Sie im Formular dann einen Wert im gleichen Datensatz, aktualisieren Sie das Dataset und versuchen Sie, die Änderungen in die Datenbank zu schreiben. Dieser Vorgang führt zu einem Parallelitätsfehler.  
  
7.  Fangen Sie den Fehler ab, und zeigen Sie anschließend die verschiedenen Versionen des Datensatzes an, um festzulegen, ob die Aktualisierung der Datenbank fortgesetzt oder abgebrochen werden soll.  
  
## Vorbereitungsmaßnahmen  
 Für die Durchführung dieser exemplarischen Vorgehensweise benötigen Sie Folgendes:  
  
-   Zugriff auf die Beispieldatenbank Northwind mit der Berechtigung zum Durchführen von Aktualisierungen.  Weitere Informationen finden Sie unter [Gewusst wie: Installieren von Beispieldatenbanken](../data-tools/how-to-install-sample-databases.md).  
  
> [!NOTE]
>  Je nach den aktiven Einstellungen oder der Version unterscheiden sich die Dialogfelder und Menübefehle auf Ihrem Bildschirm möglicherweise von den in der Hilfe beschriebenen.  Klicken Sie im Menü **Extras** auf **Einstellungen importieren und exportieren**, um die Einstellungen zu ändern.  Weitere Informationen finden Sie unter [Customizing Development Settings in Visual Studio](http://msdn.microsoft.com/de-de/22c4debb-4e31-47a8-8f19-16f328d7dcd3).  
  
## Erstellen eines neuen Projekts  
 Erstellen Sie in dieser exemplarischen Vorgehensweise zunächst eine neue Windows\-Anwendung.  
  
#### So erstellen Sie ein neues Windows\-Anwendungsprojekt  
  
1.  Erstellen Sie im Menü **Datei** ein neues Projekt.  
  
2.  Wählen Sie im Bereich **Projekttypen** eine Programmiersprache aus.  
  
3.  Wählen Sie **Windows\-Anwendung** im Bereich **Vorlagen** aus.  
  
4.  Geben Sie dem Projekt den Namen `ConcurrencyWalkthrough`, und klicken Sie dann auf **OK**.  
  
     Visual Studio fügt das Projekt dem **Projektmappen\-Explorer** hinzu und zeigt im Designer ein neues Formular an.  
  
## Erstellen des Datasets Northwind  
 In diesem Abschnitt erstellen Sie ein Dataset mit dem Namen `NorthwindDataSet`.  
  
#### So erstellen Sie das NorthwindDataset  
  
1.  Wählen Sie im Menü **Daten** die Option **Neue Datenquelle hinzufügen** aus.  
  
     Der [Assistent zum Konfigurieren von Datenquellen](../data-tools/media/data-source-configuration-wizard.png) wird geöffnet.  
  
2.  Wählen Sie auf der Seite **Datenquellentyp auswählen** die Option **Datenbank** aus.  
  
3.  Wählen Sie in der Liste der verfügbaren Verbindungen eine Verbindung zur Beispieldatenbank Northwind aus, oder klicken Sie auf **Neue Verbindung**, falls die Verbindung nicht in der Liste verfügbar ist.  
  
    > [!NOTE]
    >  Beim Herstellen einer Verbindung zu einer lokalen Datenbankdatei wählen Sie **Nein**, wenn Sie gefragt werden, ob die Datei Ihrem Projekt hinzugefügt werden soll.  
  
4.  Klicken Sie auf der Seite **Verbindungszeichenfolge in der Programmkonfigurationsdatei speichern** auf **Weiter**.  
  
5.  Erweitern Sie den Knoten **Tabellen**, und wählen Sie die Tabelle `Customers` aus.  Der Standardname für das Dataset sollte `NorthwindDataSet` sein.  
  
6.  Klicken Sie auf **Fertig stellen**, um dem Projekt das Dataset hinzuzufügen.  
  
## Erstellen eines datengebundenen DataGridView\-Steuerelements  
 In diesem Abschnitt erstellen Sie ein <xref:System.Windows.Forms.DataGridView>, indem Sie das **Customers**\-Objekt aus dem **Datenquellenfenster** auf das Windows Form ziehen.  
  
#### So erstellen Sie ein DataGridView\-Steuerelement, das an die Tabelle Customers gebunden ist  
  
1.  Wählen Sie im Menü **Daten** den Befehl **Datenquellen anzeigen** aus, um das **Datenquellenfenster** zu öffnen.  
  
2.  Im **Datenquellenfenster** erweitern Sie den Knoten **NorthwindDataSet** und wählen Sie die Tabelle **Customers** aus.  
  
3.  Klicken Sie auf den nach unten zeigenden Pfeil des Tabellenknotens, und wählen Sie **DataGridView** in der Dropdownliste aus.  
  
4.  Ziehen Sie die Tabelle auf einen leeren Bereich des Formulars.  
  
     Dem Formular werden das <xref:System.Windows.Forms.DataGridView>\-Steuerelement `CustomersDataGridView` und das <xref:System.Windows.Forms.BindingNavigator> `CustomersBindingNavigator` hinzugefügt, die an die <xref:System.Windows.Forms.BindingSource> gebunden werden, die wiederum an die Tabelle `Customers` im `NorthwindDataSet` gebunden ist.  
  
## Checkpoint  
 Sie können das Formular jetzt testen, um sicherzustellen, dass das Verhalten bisher wie erwartet ausfällt.  
  
#### So testen Sie das Formular  
  
1.  Drücken Sie F5, um die Anwendung auszuführen.  
  
     Das Formular wird mit einem <xref:System.Windows.Forms.DataGridView>\-Steuerelement angezeigt, das mit Daten aus der Tabelle `Customers` gefüllt ist.  
  
2.  Wählen Sie im Menü **Debuggen** die Option **Debuggen beenden**.  
  
## Behandeln von Parallelitätsfehlern  
 Wie Sie Fehler behandeln, hängt von den jeweiligen Geschäftsregeln ab, nach denen die Anwendung abläuft.  In dieser exemplarischen Vorgehensweise wird zu Demonstrationszwecken nach dem Auslösen einer Parallelitätsverletzung die folgende Strategie zum Behandeln des Parallelitätsfehlers verwendet:  
  
 Die Anwendung bietet dem Benutzer drei Versionen des Datensatzes zur Auswahl:  
  
-   Den aktuellen Datensatz in der Datenbank  
  
-   Den ursprünglich in das Dataset geladenen Datensatz  
  
-   Die vorgeschlagenen Änderungen im Dataset  
  
 Der Benutzer kann dann die Datenbank mit der vorgeschlagenen Version überschreiben oder aber die Aktualisierung abbrechen und das Dataset mit den neuen Werten aus der Datenbank aktualisieren.  
  
#### So aktivieren Sie die Behandlung von Parallelitätsfehlern  
  
1.  Erstellen Sie einen benutzerdefinierten Fehlerhandler.  
  
2.  Zeigen Sie die Auswahloptionen für den Benutzer an.  
  
3.  Verarbeiten Sie die Eingabe des Benutzers.  
  
4.  Senden Sie die Aktualisierung erneut, oder setzen Sie die Daten im Dataset zurück.  
  
### Hinzufügen von Code zum Behandeln von Parallelitätsausnahmen  
 Wenn bei einem Aktualisierungsversuch eine Ausnahme ausgelöst wird, sind die Informationen, die zusammen mit der ausgelösten Ausnahme angezeigt werden, in der Regel sehr hilfreich.  
  
 In diesem Abschnitt fügen Sie Code hinzu, der versucht, die Datenbank zu aktualisieren, und behandeln jede ausgelöste <xref:System.Data.DBConcurrencyException> sowie alle anderen Ausnahmen.  
  
> [!NOTE]
>  Die `CreateMessage`\-Methode und die `ProcessDialogResults`\-Methode werden zu einem späteren Zeitpunkt in dieser exemplarischen Vorgehensweise hinzugefügt.  
  
##### So fügen Sie Fehlerbehandlungscode für den Parallelitätsfehler hinzu  
  
1.  Fügen Sie unter der `Form1_Load`\-Methode folgenden Code hinzu:  
  
     [!code-cs[VbRaddataConcurrency#1](../data-tools/codesnippet/CSharp/handle-a-concurrency-exception_1.cs)]
     [!code-vb[VbRaddataConcurrency#1](../data-tools/codesnippet/VisualBasic/handle-a-concurrency-exception_1.vb)]  
  
2.  Ersetzen Sie die `CustomersBindingNavigatorSaveItem_Click`\-Methode, um die `UpdateDatabase`\-Methode aufzurufen, sodass sich Folgendes ergibt:  
  
     [!code-cs[VbRaddataConcurrency#2](../data-tools/codesnippet/CSharp/handle-a-concurrency-exception_2.cs)]
     [!code-vb[VbRaddataConcurrency#2](../data-tools/codesnippet/VisualBasic/handle-a-concurrency-exception_2.vb)]  
  
### Anzeigen der Auswahloptionen für den Benutzer  
 Durch den soeben geschriebenen Code wird die `CreateMessage`\-Prozedur aufgerufen, um Fehlerinformationen für den Benutzer anzuzeigen.  In dieser exemplarischen Vorgehensweise wird ein Meldungsfeld verwendet, um dem Benutzer die verschiedenen Versionen des Datensatzes anzuzeigen. Er kann daraufhin auswählen, ob er den Datensatz mit den Änderungen überschreibt oder die Bearbeitung abbricht.  Wenn der Benutzer durch Klicken auf eine Schaltfläche eine Option im Meldungsfeld ausgewählt hat, wird die Antwort an die `ProcessDialogResult`\-Methode übergeben.  
  
##### So erstellen Sie die Meldung, die dem Benutzer angezeigt wird  
  
-   Erstellen Sie die Meldung, indem Sie dem **Code\-Editor** folgenden Code hinzufügen.  Geben Sie diesen Code unter der `UpdateDatabase`\-Methode ein.  
  
     [!code-cs[VbRaddataConcurrency#4](../data-tools/codesnippet/CSharp/handle-a-concurrency-exception_3.cs)]
     [!code-vb[VbRaddataConcurrency#4](../data-tools/codesnippet/VisualBasic/handle-a-concurrency-exception_3.vb)]  
  
### Verarbeiten der Eingabe des Benutzers  
 Sie benötigen außerdem Code, um die Reaktion des Benutzers auf das Meldungsfeld zu verarbeiten.  Der Benutzer kann entweder den aktuellen Datensatz in der Datenbank mit der vorgeschlagenen Änderung überschreiben oder die lokalen Änderungen verwerfen und die Datentabelle mit dem aktuell in der Datenbank vorhandenen Datensatz aktualisieren.  Wenn der Benutzer "Ja" auswählt, wird die <xref:System.Data.DataTable.Merge%2A>\-Methode mit dem *preserveChanges*\-Argument aufgerufen, das auf `true` festgelegt wird.  Der Aktualisierungsversuch verläuft somit erfolgreich, da die ursprüngliche Version des Datensatzes nun mit dem Datensatz in der Datenbank übereinstimmt.  
  
##### So verarbeiten Sie die Benutzereingabe aus dem Meldungsfeld  
  
-   Fügen Sie den folgenden Code unter dem im vorherigen Abschnitt hinzugefügten Code hinzu.  
  
     [!code-cs[VbRaddataConcurrency#3](../data-tools/codesnippet/CSharp/handle-a-concurrency-exception_4.cs)]
     [!code-vb[VbRaddataConcurrency#3](../data-tools/codesnippet/VisualBasic/handle-a-concurrency-exception_4.vb)]  
  
## Testen  
 Sie können das Formular jetzt testen, um sicherzustellen, dass das Verhalten wie erwartet ausfällt.  Um eine Parallelitätsverletzung zu simulieren, müssen Sie Daten in der Datenbank ändern, nachdem Sie das NorthwindDataSet gefüllt haben.  
  
#### So testen Sie das Formular  
  
1.  Drucken Sie F5, um die Anwendung auszuführen.  
  
2.  Wenn das Formular angezeigt wird, führen Sie es weiterhin, und wechseln Sie zur Visual Studio\-IDE.  
  
3.  Klicken Sie im Menü **Ansicht** auf **Server\-Explorer**.  
  
4.  Erweitern Sie im **Server\-Explorer** die Verbindung, die von der Anwendung verwendet wird, und erweitern Sie den Knoten **Tabellen**.  
  
5.  Klicken Sie mit der rechten Maustaste auf die Tabelle **Customers**, und wählen Sie **Tabellendaten anzeigen** aus.  
  
6.  Ändern Sie im ersten Datensatz \(`ALFKI`\) den `ContactName` in `Maria Anders2`.  
  
    > [!NOTE]
    >  Navigieren Sie zu einer anderen Zeile, um einen Commit für die Änderung auszuführen.  
  
7.  Wechseln Sie zum Formular `ConcurrencyWalkthrough`, das immer noch ausgeführt wird.  
  
8.  Ändern Sie im ersten Datensatz des Formulars \(`ALFKI`\) den `ContactName` in `Maria Anders1`.  
  
9. Klicken Sie auf die Schaltfläche **Speichern**.  
  
     Der Parallelitätsfehler wird ausgelöst, und das Meldungsfeld wird angezeigt.  
  
10. Wenn Sie auf **Nein** klicken, wird die Aktualisierung abgebrochen und das Dataset mit den aktuellen Werten in der Datenbank aktualisiert. Wenn Sie hingegen auf **Ja** klicken, wird der vorgeschlagene Wert in die Datenbank geschrieben.  
  
## Siehe auch  
 [Exemplarische Vorgehensweisen zur Arbeit mit Daten](../Topic/Data%20Walkthroughs.md)   
 [Binden von Windows Forms\-Steuerelementen an Daten in Visual Studio](../data-tools/bind-windows-forms-controls-to-data-in-visual-studio.md)   
 [Herstellen von Datenverbindungen in Visual Studio](../data-tools/connecting-to-data-in-visual-studio.md)   
 [Vorbereiten der Anwendung auf den Empfang von Daten](../Topic/Preparing%20Your%20Application%20to%20Receive%20Data.md)   
 [Abrufen von Daten für die Anwendung](../data-tools/fetching-data-into-your-application.md)   
 [Binden von Steuerelementen an Daten in Visual Studio](../data-tools/bind-controls-to-data-in-visual-studio.md)   
 [Bearbeiten von Daten in der Anwendung](../data-tools/editing-data-in-your-application.md)   
 [Überprüfen von Daten](../Topic/Validating%20Data.md)   
 [Speichern von Daten](../data-tools/saving-data.md)