---
title: Behandeln einer Parallelitätsausnahme | Microsoft-Dokumentation
ms.custom: ''
ms.date: 2018-06-30
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
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
author: gewarren
ms.author: gewarren
manager: ghogen
ms.openlocfilehash: d174aeb48170f1232aa0830bd2532897e7cb6f5f
ms.sourcegitcommit: 55f7ce2d5d2e458e35c45787f1935b237ee5c9f8
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 08/22/2018
ms.locfileid: "47511842"
---
# <a name="handle-a-concurrency-exception"></a>Behandeln einer Parallelitätsausnahme
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Die neueste Version dieses Themas finden Sie unter [Behandeln einer Parallelitätsausnahme](https://docs.microsoft.com/visualstudio/data-tools/handle-a-concurrency-exception).  
  
  
Parallelitätsausnahmen (<xref:System.Data.DBConcurrencyException>) werden ausgelöst, wenn zwei Benutzer gleichzeitig versuchen, dieselben Daten in einer Datenbank zu ändern. In dieser exemplarischen Vorgehensweise erstellen Sie eine Windows-Anwendung, die veranschaulicht, wie zum Abfangen einer <xref:System.Data.DBConcurrencyException>, suchen Sie die Zeile, die den Fehler verursacht hat, und erfahren Sie, eine Strategie zum verarbeiten.  
  
 Diese exemplarische Vorgehensweise enthält folgende Vorgänge:  
  
1.  Erstellen Sie ein neues **Windows-Anwendung** Projekt.  
  
2.  Erstellen eines neuen Datasets auf der Grundlage der Tabelle `Customers` der Datenbank Northwind.  
  
3.  Erstellen eines Formulars mit einer <xref:System.Windows.Forms.DataGridView> für die Anzeige der Daten.  
  
4.  Füllen eines Datasets mit Daten aus der Tabelle `Customers` in der Datenbank Northwind.  
  
5.  Verwenden der [Visual Database Tools](http://msdn.microsoft.com/en-us/6b145922-2f00-47db-befc-bf351b4809a1) in Visual Studio den direkten Zugriff auf die `Customers` Datentabelle und einen Datensatz zu ändern.  
  
6.  Ändern Sie den gleichen Datensatz auf einen anderen Wert, aktualisieren Sie das Dataset und versuchen Sie, die Änderungen in der Datenbank zu schreiben, was zu einem Parallelitätsfehler führt.  
  
7.  Fangen Sie den Fehler ab, und zeigen Sie anschließend die verschiedenen Versionen des Datensatzes an, um festzulegen, ob die Aktualisierung der Datenbank fortgesetzt oder abgebrochen werden soll.  
  
## <a name="prerequisites"></a>Erforderliche Komponenten  
 Für die Durchführung dieser exemplarischen Vorgehensweise benötigen Sie Folgendes:  
  
-   Zugriff auf die Beispieldatenbank Northwind mit der Berechtigung zum Durchführen von Aktualisierungen. Weitere Informationen finden Sie unter [Vorgehensweise: Installieren von Beispieldatenbanken](../data-tools/how-to-install-sample-databases.md).  
  
> [!NOTE]
>  Die angezeigten Dialogfelder und Befehle im Menü angezeigten unterscheiden sich von den in der Hilfe beschriebenen, je nach Ihren aktiven Einstellungen oder die Edition, die Sie verwenden. Klicken Sie im Menü **Extras** auf **Einstellungen importieren und exportieren** , um die Einstellungen zu ändern. Weitere Informationen finden Sie unter [Anpassen der Entwicklungseinstellungen in Visual Studio](http://msdn.microsoft.com/en-us/22c4debb-4e31-47a8-8f19-16f328d7dcd3).  
  
## <a name="create-a-new-project"></a>Erstellt ein neues Projekt  
 Erstellen Sie in dieser exemplarischen Vorgehensweise zunächst eine neue Windows-Anwendung.  
  
#### <a name="to-create-a-new-windows-application-project"></a>Um ein neues Windows-Anwendungsprojekt zu erstellen.  
  
1.  Auf der **Datei** Menü ein neues Projekt erstellen.  
  
2.  In der **Projekttypen** Bereich Programmiersprache auswählen.  
  
3.  In der **Vorlagen** wählen Sie im Bereich **Windows-Anwendung**.  
  
4.  Nennen Sie das Projekt `ConcurrencyWalkthrough`, und wählen Sie dann**OK**.  
  
     Visual Studio fügt das Projekt in **Projektmappen-Explorer** und ein neues Formular im Designer angezeigt.  
  
## <a name="create-the-northwind-dataset"></a>Erstellen des Datasets Northwind  
 In diesem Abschnitt erstellen Sie ein Dataset namens `NorthwindDataSet`.  
  
#### <a name="to-create-the-northwinddataset"></a>So erstellen Sie das NorthwindDataset  
  
1.  Auf der **Daten** Menü wählen **neue Datenquelle hinzufügen**.  
  
     Die [Assistenten zur Datenquellenkonfiguration](http://msdn.microsoft.com/library/c4df7de5-5da0-4064-940c-761dd6d9e28f) wird geöffnet.  
  
2.  Auf der **wählen Sie einen Datenquellentyp**auf **Datenbank**.  
  
3.  Wählen Sie eine Verbindung mit der Northwind-Beispieldatenbank an, aus der Liste der verfügbaren Verbindungen. Wenn die Verbindung nicht in der Liste der Verbindungen verfügbar ist, wählen Sie**neue Verbindung**  
  
    > [!NOTE]
    >  Wenn Sie die zu einer lokalen Datenbankdatei herstellen, wählen Sie **keine** Wenn gefragt werden, wenn Sie dies tun würden Sie die Datei zu Ihrem Projekt hinzufügen möchten.  
  
4.  Auf der **Verbindungszeichenfolge in der Anwendungskonfigurationsdatei speichern**auf **Weiter**.  
  
5.  Erweitern Sie die **Tabellen** Knoten, und wählen die `Customers` Tabelle. Der Standardname für das Dataset sollte `NorthwindDataSet` sein.  
  
6.  Wählen Sie**Fertig stellen** des Datasets zum Projekt hinzufügen.  
  
## <a name="create-a-data-bound-datagridview-control"></a>Erstellen von einem datengebundenen DataGridView-Steuerelement  
 In diesem Abschnitt erstellen Sie eine <xref:System.Windows.Forms.DataGridView> durch Ziehen der **Kunden** Element aus der **Datenquellen** auf das Windows-Formular.  
  
#### <a name="to-create-a-datagridview-control-that-is-bound-to-the-customers-table"></a>So erstellen Sie ein DataGridView-Steuerelement, das an die Tabelle Customers gebunden ist  
  
1.  Auf der **Daten** im Menü wählen **Datenquellen anzeigen** zum Öffnen der **Fensters "Datenquellen"**.  
  
2.  In der **Datenquellen** Fenster, erweitern Sie die **NorthwindDataSet** Knoten, und wählen Sie dann die **Kunden** Tabelle.  
  
3.  Wählen Sie den Pfeil nach unten für den Tabellenknoten, und wählen Sie dann **DataGridView**in der Dropdown-Liste.  
  
4.  Ziehen Sie die Tabelle auf einen leeren Bereich des Formulars.  
  
     Ein <xref:System.Windows.Forms.DataGridView> Steuerelement mit dem Namen `CustomersDataGridView` und <xref:System.Windows.Forms.BindingNavigator> mit dem Namen `CustomersBindingNavigator` werden hinzugefügt, um das Formular, das gebunden ist die <xref:System.Windows.Forms.BindingSource>. Dies ist, aktivieren Sie gebunden ist die `Customers` -Tabelle in der `NorthwindDataSet`.  
  
## <a name="test-the-form"></a>Testen Sie das Formular  
 Sie können das Formular jetzt testen, um sicherzustellen, dass das Verhalten bisher wie erwartet ausfällt.  
  
#### <a name="to-test-the-form"></a>So testen Sie das Formular  
  
1.  Wählen Sie**F5** zum Ausführen der Anwendung  
  
     Das Formular wird mit einem <xref:System.Windows.Forms.DataGridView> Steuerelement, das mit Daten gefüllt wird der `Customers` Tabelle.  
  
2.  Auf der **Debuggen** , wählen Sie im Menü**Debuggen beenden**.  
  
## <a name="handleconcurrency-errors"></a>Handleconcurrency-Fehler  
 Wie Sie Fehler behandeln hängt von den jeweiligen Geschäftsregeln, die Ihre Anwendung steuern. In dieser exemplarischen Vorgehensweise verwenden wir die folgende Strategie als Beispiel zur Tohandle des parallelitätsfehlers.  
  
 Die dem Benutzer drei Versionen des Datensatzes für die Applicationpresents:  
  
-   Der aktuelle Datensatz in der Datenbank  
  
-   Der ursprüngliche Datensatz, der in das Dataset geladen wird  
  
-   Die vorgeschlagenen Änderungen im dataset  
  
 Der Benutzer kann dann die Datenbank mit der vorgeschlagenen Version überschreiben oder die Aktualisierung abzubrechen und das Dataset mit den neuen Werten aus der Datenbank aktualisieren.  
  
#### <a name="to-enable-the-handling-of-concurrency-errors"></a>So aktivieren Sie die Behandlung von Parallelitätsfehlern  
  
1.  Erstellen Sie einen benutzerdefinierten Fehlerhandler.  
  
2.  Zeigen Sie die Auswahloptionen für den Benutzer an.  
  
3.  Verarbeiten Sie die Eingabe des Benutzers.  
  
4.  Senden Sie die Aktualisierung erneut, oder setzen Sie die Daten im Dataset zurück.  
  
### <a name="addcode-to-handle-the-concurrency-exception"></a>Addcode zum Behandeln von Parallelitätsausnahmen  
 Wenn Sie versuchen, ein Update ausführen und eine Ausnahme ausgelöst wird, möchten Sie in der Regel etwas mit den Informationen, die mit der ausgelösten Ausnahme bereitgestellt wird.  
  
 In diesem Abschnitt fügen Sie Code, der versucht, die zum Aktualisieren der Datenbank hinzu. Sie können auch behandeln alle <xref:System.Data.DBConcurrencyException> ausgelöste, sowie alle anderen Ausnahmen.  
  
> [!NOTE]
>  Die `CreateMessage`-Methode und die `ProcessDialogResults`-Methode werden zu einem späteren Zeitpunkt in dieser exemplarischen Vorgehensweise hinzugefügt.  
  
##### <a name="to-add-error-handling-for-the-concurrency-error"></a>So fügen Sie Fehlerbehandlungscode für den Parallelitätsfehler hinzu  
  
1.  Fügen Sie unter der `Form1_Load`-Methode folgenden Code hinzu:  
  
     [!code-csharp[VbRaddataConcurrency#1](../snippets/csharp/VS_Snippets_VBCSharp/VbRaddataConcurrency/CS/Form1.cs#1)]
     [!code-vb[VbRaddataConcurrency#1](../snippets/visualbasic/VS_Snippets_VBCSharp/VbRaddataConcurrency/VB/Form1.vb#1)]  
  
2.  Ersetzen Sie die `CustomersBindingNavigatorSaveItem_Click`-Methode, um die `UpdateDatabase`-Methode aufzurufen, sodass sich Folgendes ergibt:  
  
     [!code-csharp[VbRaddataConcurrency#2](../snippets/csharp/VS_Snippets_VBCSharp/VbRaddataConcurrency/CS/Form1.cs#2)]
     [!code-vb[VbRaddataConcurrency#2](../snippets/visualbasic/VS_Snippets_VBCSharp/VbRaddataConcurrency/VB/Form1.vb#2)]  
  
### <a name="displaychoices-to-the-user"></a>Displaychoices für den Benutzer  
 Durch den soeben geschriebenen Code wird die `CreateMessage`-Prozedur aufgerufen, um Fehlerinformationen für den Benutzer anzuzeigen. In dieser exemplarischen Vorgehensweise verwenden Sie ein Meldungsfeld, um die verschiedenen Versionen des Datensatzes für den Benutzer anzuzeigen. Dadurch kann der Benutzer auswählen, ob der Datensatz mit den Änderungen überschreiben oder die Bearbeitung abbricht. Wenn der Benutzer durch Klicken auf eine Schaltfläche eine Option im Meldungsfeld ausgewählt hat, wird die Antwort an die `ProcessDialogResult`-Methode übergeben.  
  
##### <a name="to-create-the-message-to-display-to-the-user"></a>So erstellen Sie die Meldung, die dem Benutzer angezeigt wird  
  
-   Erstellen der Nachricht durch den folgenden Code zum Hinzufügen der **Code-Editor**. Geben Sie diesen Code unter der `UpdateDatabase`-Methode ein.  
  
     [!code-csharp[VbRaddataConcurrency#4](../snippets/csharp/VS_Snippets_VBCSharp/VbRaddataConcurrency/CS/Form1.cs#4)]
     [!code-vb[VbRaddataConcurrency#4](../snippets/visualbasic/VS_Snippets_VBCSharp/VbRaddataConcurrency/VB/Form1.vb#4)]  
  
### <a name="process-the-users-response"></a>Verarbeitet die Antwort des Benutzers  
 Außerdem benötigen Sie Code zum Verarbeiten der Antwort des Benutzers in der MessageBox. Die Optionen sind entweder auf den aktuellen Datensatz in der Datenbank mit der vorgeschlagenen Änderung überschreiben oder die lokalen Änderungen verwerfen und aktualisieren Sie die Datentabelle mit dem Datensatz, der derzeit in der Datenbank vorhanden ist. Wenn der Benutzer "Ja", die <xref:System.Data.DataTable.Merge%2A> Methode wird aufgerufen, mit der *PreserveChanges* Argument festgelegt wird, um `true`. Dies bewirkt, dass den Updateversuch, die erfolgreich ist, muss, da die ursprüngliche Version des Datensatzes nun der Eintrag in der Datenbank übereinstimmt.  
  
##### <a name="to-process-the-user-input-from-the-message-box"></a>So verarbeiten Sie die Benutzereingabe aus dem Meldungsfeld  
  
-   Fügen Sie den folgenden Code unter dem Code, der im vorherigen Abschnitt hinzugefügt wurde.  
  
     [!code-csharp[VbRaddataConcurrency#3](../snippets/csharp/VS_Snippets_VBCSharp/VbRaddataConcurrency/CS/Form1.cs#3)]
     [!code-vb[VbRaddataConcurrency#3](../snippets/visualbasic/VS_Snippets_VBCSharp/VbRaddataConcurrency/VB/Form1.vb#3)]  
  
## <a name="test-the-form"></a>Testen Sie das Formular  
 Sie können das Formular jetzt testen, um sicherzustellen, dass das Verhalten wie erwartet ausfällt. Um eine Parallelitätsverletzung zu simulieren, müssen Sie Daten in der Datenbank ändern, nachdem Sie das NorthwindDataSet gefüllt haben.  
  
#### <a name="to-test-the-form"></a>So testen Sie das Formular  
  
1.  Wählen Sie**F5** zum Ausführen der Anwendung.  
  
2.  Wenn das Formular angezeigt wird, führen Sie es weiterhin, und wechseln Sie zur Visual Studio-IDE.  
  
3.  Auf der **Ansicht** Menü wählen **Server-Explorer**.  
  
4.  In **Server-Explorer**, erweitern Sie die Verbindung Ihrer Anwendung verwenden, und erweitern Sie dann die **Tabellen** Knoten.  
  
5.  Mit der rechten Maustaste die **Kunden** Tabelle, und wählen Sie dann **Tabellendaten anzeigen**.  
  
6.  Im ersten Datensatz (`ALFKI`) ändern `ContactName` zu `Maria Anders2`.  
  
    > [!NOTE]
    >  Navigieren Sie zu einer anderen Zeile, um einen Commit für die Änderung auszuführen.  
  
7.  Wechseln Sie zum Formular `ConcurrencyWalkthrough`, das immer noch ausgeführt wird.  
  
8.  Im ersten Datensatz auf dem Formular (`ALFKI`), ändern Sie`ContactName` zu `Maria Anders1`.  
  
9. Wählen Sie die **speichern** Schaltfläche.  
  
     Der Parallelitätsfehler wird ausgelöst, und das Meldungsfeld wird angezeigt.  
  
10. Auswählen von**keine** wird die Aktualisierung abgebrochen und das Dataset mit den Werten, die derzeit in der Datenbank werden aktualisiert. Auswählen von**Ja** den vorgeschlagenen Wert in die Datenbank geschrieben.  
  
## <a name="see-also"></a>Siehe auch  
 [Rückspeichern von Daten in der Datenbank](../data-tools/save-data-back-to-the-database.md)

