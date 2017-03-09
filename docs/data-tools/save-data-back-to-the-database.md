---
title: "Speichern von Daten in Datasets | Microsoft Docs"
ms.custom: ""
ms.date: "12/14/2016"
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
  - "Daten [Visual Studio], Speichern"
  - "Datenvalidierung, Datasets"
  - "Datasets [Visual Basic], Informationen über Datasets"
  - "Datasets [Visual Basic], Einschränkungen"
  - "Datasets [Visual Basic], Zusammenführen"
  - "Datasets [Visual Basic], Validieren von Daten"
  - "Zeilenversion"
  - "Speichern von Daten, Informationen über das Speichern von Daten"
  - "TableAdapters"
  - "Aktualisierungen, Einschränkungen in Datasets"
  - "Aktualisieren von Datasets, Einschränkungen"
ms.assetid: afe6cb8a-dc6a-428b-b07b-903ac02c890b
caps.latest.revision: 27
caps.handback.revision: 18
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# Speichern von Daten in Datasets
Das Speichern von Daten bezeichnet den Vorgang der Sicherung geänderter Daten aus einer Anwendung in den ursprünglichen Datenspeicher, in der Regel eine relationale Datenbank wie SQL Sever.  
  
 Da es sich bei einem Dataset tatsächlich um eine im Arbeitsspeicher zwischengespeicherte Kopie handelt, gibt es für das Schreiben von Informationen in die ursprüngliche Datenquelle und die Änderung von Daten im Dataset zwei völlig getrennte Verfahren.  Sie können aktualisierte Daten in Datasets an die Datenbank zurücksenden, indem Sie eine der `Update`\-Methoden eines TableAdapter oder eine der DBDirect\-Methoden des TableAdapter aufrufen.  
  
 Weitere Informationen zum Zurücksenden der in einem Dataset vorgenommenen Änderungen an die Datenbank finden Sie unter [Gewusst wie: Aktualisieren von Daten mit einem TableAdapter](../data-tools/update-data-by-using-a-tableadapter.md) und [Gewusst wie: Speichern von Datasetänderungen in einer Datenbank](../data-tools/how-to-save-dataset-changes-to-a-database.md).  
  
 Visual Studio verfügt über eine `TableAdapterManager`\-Komponente zur Unterstützung bei Speichervorgängen, wenn Daten in verknüpften Tabellen gespeichert werden.  Durch diese Komponente wird sichergestellt, dass die durchgeführten Speichervorgänge in der ordnungsgemäßen Reihenfolge auf Grundlage der in der Datenbank definierten Fremdschlüsseleinschränkungen erfolgen.  Weitere Informationen finden Sie unter [Übersicht über die hierarchische Aktualisierung](../Topic/Hierarchical%20Update%20Overview.md).  
  
 Informationen zum Ändern von Daten im Dataset finden Sie unter [Bearbeiten von Daten in der Anwendung](../data-tools/editing-data-in-your-application.md).  
  
## Zweistufige Aktualisierungen  
 Die Aktualisierung einer Datenquelle mithilfe eines Datasets umfasst zwei Schritte.  Im ersten Schritt wird das Dataset mit neuen Informationen, z. B. neuen, geänderten oder gelöschten Datensätzen, aktualisiert.  Falls die Anwendung lediglich auf das Dataset beschränkt ist – beispielsweise, wenn das Dataset nach der Aktualisierung an eine andere Anwendung gesendet und dort weiter verarbeitet wird – ist die Aktualisierung hier abgeschlossen.  
  
> [!NOTE]
>  In Windows Forms werden Änderungen an datengebundenen Steuerelementen aufgrund der Datenbindungsarchitektur automatisch an das Dataset gesendet, sodass es nicht explizit mit eigenem Code aktualisiert werden muss.  Weitere Informationen finden Sie unter [Datenbindung in Web Forms](../Topic/Windows%20Forms%20Data%20Binding.md).  
  
 Wenn Sie eine Datenquelle \(z. B. eine Datenbank\) aktualisieren, besteht der zweite Schritt darin, die Änderungen am Dataset an die ursprüngliche Datenquelle zu senden.  Dies bedeutet, dass bei der Aktualisierung des Datasets Änderungen nicht automatisch in eine zugrunde liegende Datenquelle fortgeschrieben werden. Vielmehr muss dieser zweite Schritt explizit ausgeführt werden.  Normalerweise rufen Sie dazu die Update\-Methode des TableAdapter \(oder Datenadapters\) auf, der auch zum Auffüllen des Datasets mit Daten verwendet wurde. Sie können jedoch auch andere Adapter verwenden, z. B. zum Verschieben von Daten von einer Datenquelle in eine andere oder zum Aktualisieren mehrerer Datenquellen.  
  
 ![Visual Basic&#45;DataSet&#45;Aktualisierungen](../data-tools/media/vbdatasetupdates.gif "vbDatasetUpdates")  
Zweistufiger Aktualisierungsprozess und die Bedeutung von "DataRowVersion" in einer erfolgreichen Aktualisierung  
  
 Strukturell gesehen stellt ein Dataset Daten in Form von Auflistungsgruppen zur Verfügung.  Datasets umfassen tabellarische Auflistungen.  Tabellen bestehen wiederum aus Rowsets.  Tabellen werden als Auflistung des <xref:System.Data.DataSet>\-Objekts verfügbar gemacht, und Datensätze sind in der <xref:System.Data.DataTable.Rows%2A>\-Auflistung von <xref:System.Data.DataTable>\-Objekten verfügbar.  Auch wenn Sie Daten in einem Dataset ändern können, indem Sie diese Auflistungen mithilfe der grundlegenden Auflistungsmethoden bearbeiten, müssen Sie für die Aktualisierung einer zugrunde liegenden Datenquelle Methoden verwenden, die speziell für die Änderung von Datasets entwickelt wurden.  
  
 Um beispielsweise einen Datensatz aus einer Datentabelle zu entfernen, können Sie die [RemoveAt](https://msdn.microsoft.com/en-us/library/system.data.datarowcollection.removeat.aspx)\-Methode der tabellenspezifischen <xref:System.Data.DataTable.Rows%2A>\-Auflistung aufrufen. Bei dieser Vorgehensweise wird der Datensatz physisch aus dem Dataset gelöscht.  Falls Sie das Dataset lediglich als strukturierten Datenspeicher verwenden und keine Änderungsinformationen auf eine andere Anwendung übertragen müssen, ist diese Bearbeitungsmethode für Auflistungsdaten eine akzeptable Möglichkeit, um ein Dataset zu aktualisieren.  
  
 Wenn Sie jedoch beabsichtigen, Änderungen auf eine Datenquelle oder eine andere Anwendung zu übertragen, müssen Änderungsinformationen \(d. h. Metadaten\) zu jeder Aktualisierung nachverfolgt werden.  Wenn Sie später Änderungen an die Datenquelle oder Anwendung senden, verfügt der Prozess über die Informationen, die zum Auffinden und Aktualisieren der erforderlichen Datensätze nötig sind.  Wenn Sie zum Beispiel einen Datensatz im Dataset löschen, müssen im Dataset Informationen zum gelöschten Datensatz beibehalten werden.  Auf diese Weise sind bei einem Aufruf von `DeleteCommand` des TableAdapter genügend Informationen zur Versionsgeschichte vorhanden, um den ursprünglichen Datensatz in der Datenquelle zu finden, sodass dieser gelöscht werden kann.  Weitere Informationen finden Sie unten im Abschnitt "Verwalten von Änderungsinformationen".  
  
## Zusammenführen von Datasets  
 Sie können den Inhalt eines Datasets aktualisieren, indem Sie Inhalte *zusammenführen*. Dabei kopieren Sie den Inhalt eines Datasets \(des sogenannten *Quell*\-Datasets\) in das aufrufende Dataset \(das sogenannte *Ziel*\-Dataset\).  Beim Zusammenführen von Datasets werden neue Datensätze aus dem Quell\-Dataset in das Ziel\-Dataset eingefügt.  Darüber hinaus werden dem Ziel\-Dataset zusätzliche Spalten aus dem Quell\-Dataset hinzugefügt.  Das Zusammenführen von Datasets ist besonders sinnvoll, wenn ein lokales Dataset vorhanden ist und ein zweites Dataset aus einer anderen Anwendung oder einer Komponente, z. B. einem XML\-Webdienst, hinzugefügt wird.  Diese Vorgehensweise ist auch sinnvoll, wenn Sie Daten aus mehreren Datasets integrieren müssen.  
  
 Beim Zusammenführen von Datasets kann ein optionales boolesches Argument \(`preserveChanges`\) übergeben werden. Durch dieses Argument kann die <xref:System.Data.DataSet.Merge%2A>\-Methode feststellen, ob bestehende Änderungen im Ziel\-Dataset beibehalten werden sollen.  Da Datasets mehrere Datensatzversionen verwalten, darf nicht außer Acht gelassen werden, dass auch mehrere Datensatzversionen zusammengeführt werden.  In der folgenden Tabelle sehen Sie Datensätze aus zwei Datasets, die zusammengeführt werden:  
  
|DataRowVersion|Ziel\-Dataset|Quell\-Dataset|  
|--------------------|-------------------|--------------------|  
|Ursprünglich|James Wilson|James C.  Wilson|  
|Aktuell|Jim Wilson|James C.  Wilson|  
  
 Durch den Aufruf der <xref:System.Data.DataSet.Merge%2A>\-Methode für die oben dargestellte Tabelle mit `preserveChanges=false targetDataset.Merge(sourceDataset)` erzielen Sie das folgende Ergebnis:  
  
|DataRowVersion|Ziel\-Dataset|Quell\-Dataset|  
|--------------------|-------------------|--------------------|  
|Ursprünglich|James C.  Wilson|James C.  Wilson|  
|Aktuell|James C.  Wilson|James C.  Wilson|  
  
 Durch den Aufruf der <xref:System.Data.DataSet.Merge%2A>\-Methode mit `preserveChanges = true targetDataset.Merge(sourceDataset, true)` erzielen Sie das folgende Ergebnis:  
  
|DataRowVersion|Ziel\-Dataset|Quell\-Dataset|  
|--------------------|-------------------|--------------------|  
|Ursprünglich|James C.  Wilson|James C.  Wilson|  
|Aktuell|Jim Wilson|James C.  Wilson|  
  
> [!CAUTION]
>  Wenn im `preserveChanges = true`\-Szenario die <xref:System.Data.DataSet.RejectChanges%2A>\-Methode für einen Datensatz im Ziel\-Dataset aufgerufen wird, werden die Daten auf die ursprünglichen Daten im *Quell*\-Dataset zurückgesetzt.  Wenn Sie also versuchen, die ursprüngliche Datenquelle mit dem Ziel\-Dataset zu aktualisieren, wird die ursprüngliche zu aktualisierende Zeile u. U. nicht gefunden.  Sie können jedoch eine Parallelitätsverletzung vermeiden, indem Sie ein anderes Dataset mit den aktualisierten Datensätzen auffüllen und anschließend eine Zusammenführung ausführen. \(Eine Parallelitätsverletzung liegt vor, wenn ein anderer Benutzer einen Datensatz in der Datenquelle ändert, nachdem das Dataset aufgefüllt wurde.\)  
  
## Einschränkungen bei der Aktualisierung  
 Um Änderungen an einer vorhandenen Datenzeile vorzunehmen, werden Daten in einzelnen Spalten hinzugefügt oder aktualisiert.  Wenn das Dataset Einschränkungen unterliegt \(z. B. Fremdschlüsseln oder Einschränkungen, die nicht auf NULL festgelegt werden können\), kann sich ein Datensatz während der Aktualisierung vorübergehend in einem Fehlerzustand befinden. Dies gilt für den Zeitpunkt, nachdem Sie eine Spalte aktualisiert haben, aber noch nicht zur nächsten Spalte gewechselt sind.  
  
 Um vorzeitige Verletzungen dieser Einschränkungen zu vermeiden, können Sie sie vorübergehend außer Kraft setzen.  Bei diesem Verfahren werden zwei Ziele verfolgt:  
  
-   Es wird verhindert, dass ein Fehler ausgelöst wird, wenn Sie eine Spalte aktualisieren, bevor Sie zur nächsten wechseln.  
  
-   Bestimmte \(häufig für Validierungen verwendete\) Aktualisierungsereignisse werden nicht ausgelöst.  
  
 Nachdem die Aktualisierung abgeschlossen ist, können Sie die Überprüfung von Einschränkungen wieder aktivieren, wodurch auch Aktualisierungsereignisse wieder aktiviert und ausgelöst werden.  
  
> [!NOTE]
>  In Windows Forms wird die Überprüfung von Einschränkungen durch die in das Datenraster integrierte Datenbindungsarchitektur unterbunden, bis der Fokus auf eine andere Zeile übergeht. Daher müssen die Methoden <xref:System.Data.DataRow.BeginEdit%2A>, <xref:System.Data.DataRow.EndEdit%2A> oder <xref:System.Data.DataRow.CancelEdit%2A> nicht explizit aufgerufen werden.  
  
 Beim Aufruf der <xref:System.Data.DataSet.Merge%2A>\-Methode für ein Dataset werden Einschränkungen automatisch deaktiviert.  Wenn nach erfolgreicher Zusammenführung weiterhin Einschränkungen für das Dataset bestehen, die nicht deaktiviert werden können, wird eine <xref:System.Data.ConstraintException> ausgelöst.  In einer solchen Situation ist die <xref:System.Data.DataSet.EnforceConstraints%2A>\-Eigenschaft auf `false` festgelegt, und alle Einschränkungsverletzungen müssen vor dem Zurücksetzen der <xref:System.Data.DataSet.EnforceConstraints%2A>\-Eigenschaft auf `true` aufgelöst werden.  
  
 Nachdem die Aktualisierung abgeschlossen ist, können Sie die Überprüfung von Einschränkungen wieder aktivieren, wodurch auch Aktualisierungsereignisse wieder aktiviert und ausgelöst werden.  
  
 Weitere Informationen zum Aufheben von Ereignissen finden Sie unter [Gewusst wie: Deaktivieren von Einschränkungen beim Auffüllen von Datasets](../data-tools/turn-off-constraints-while-filling-a-dataset.md).  
  
## Fehler bei der Dataset\-Aktualisierung  
 Bei der Aktualisierung von Datensätzen in einen Dataset können Fehler auftreten.  Beispielsweise können versehentlich Daten in eine Spalte geschrieben werden, die über den falschen Datentyp verfügt, zu lang ist oder ein anderes Integritätsproblem verursacht.  Darüber hinaus werden u. U. anwendungsspezifische Validierungen durchgeführt, die in jeder Phase eines Aktualisierungsereignisses benutzerdefinierte Fehler auslösen können.  Weitere Informationen finden Sie unter [Überprüfen von Daten in Datasets](../data-tools/validate-data-in-datasets.md).  
  
## Verwalten von Änderungsinformationen  
 Informationen zu Änderungen in einem Dataset werden auf zweifache Weise verwaltet: durch eine Zeilenkennzeichnung, die angibt, ob die Zeile geändert wurde \(<xref:System.Data.DataRow.RowState%2A>\), und durch die Speicherung mehrerer Kopien eines Datensatzes \(<xref:System.Data.DataRowVersion>\).  Mithilfe dieser Informationen können die geänderten Daten im Dataset vom Prozess ermittelt und die entsprechenden Aktualisierungen an die Datenquelle gesendet werden.  
  
### RowState\-Eigenschaft  
 Die <xref:System.Data.DataRow.RowState%2A>\-Eigenschaft eines <xref:System.Data.DataRow>\-Objekts stellt einen Wert dar, der Informationen zum Status einer bestimmten Datenzeile bereitstellt.  
  
 In der folgenden Tabelle sind die möglichen Werte für die <xref:System.Data.DataRowState>\-Enumeration aufgeführt:  
  
|DataRowState\-Wert|Beschreibung|  
|------------------------|------------------|  
|<xref:System.Data.DataRowState>|Die Zeile wurde einer <xref:System.Data.DataRowCollection> als Element hinzugefügt. \(Eine Zeile mit diesem Zustand hat keine entsprechende ursprüngliche Version, da sie beim Aufruf der letzten <xref:System.Data.DataRow.AcceptChanges%2A>\-Methode noch nicht vorhanden war\).|  
|<xref:System.Data.DataRowState>|Die Zeile wurde mit <xref:System.Data.DataRow.Delete%2A> eines <xref:System.Data.DataRow>\-Objekts gelöscht.|  
|<xref:System.Data.DataRowState>|Die Zeile wurde zwar erstellt, gehört aber keiner <xref:System.Data.DataRowCollection> an.  Ein <xref:System.Data.DataRow>\-Objekt befindet sich in diesem Zustand, unmittelbar nachdem es erstellt wurde und bevor es einer Auflistung hinzugefügt wird oder aber nachdem es aus einer Auflistung entfernt wurde.|  
|<xref:System.Data.DataRowState>|Ein Spaltenwert in der Zeile wurde beliebig geändert.|  
|<xref:System.Data.DataRowState>|Die Zeile wurde seit dem letzten Aufruf von <xref:System.Data.DataRow.AcceptChanges%2A> nicht geändert.|  
  
### DataRowVersion\-Enumeration  
 In Datasets werden mehrere Datensatzversionen verwaltet.  Die <xref:System.Data.DataRowVersion>\-Enumeration eines <xref:System.Data.DataRow>\-Objekts stellt einen Wert dar, der zum Zurückgeben einer bestimmten Version eines <xref:System.Data.DataRow>\-Objekts verwendet werden kann.  
  
 In der folgenden Tabelle sind die möglichen Werte für die <xref:System.Data.DataRowVersion>\-Enumeration aufgeführt:  
  
|DataRowVersion\-Wert|Beschreibung|  
|--------------------------|------------------|  
|<xref:System.Data.DataRowVersion>|Die aktuelle Version eines Datensatzes enthält alle Änderungen, die seit dem letzten Aufruf von <xref:System.Data.DataRow.AcceptChanges%2A> am Datensatz vorgenommen wurden.  Falls die Zeile gelöscht wurde, ist keine aktuelle Version vorhanden.|  
|<xref:System.Data.DataRowVersion>|Der Standardwert eines Datensatzes, wie er durch das Dataset\-Schema oder die Datenquelle definiert wurde.|  
|<xref:System.Data.DataRowVersion>|Die ursprüngliche Version eines Datensatzes ist eine Kopie des Datensatzes zu dem Zeitpunkt, zu dem zuletzt ein Commit für Dataset\-Änderungen ausgeführt wurde.  Praktisch entspricht dies meist der Version eines Datensatzes, die aus einer Datenquelle gelesen wurde.|  
|<xref:System.Data.DataRowVersion>|Die vorläufige Version eines Datensatzes ist während der laufenden Aktualisierung vorübergehend verfügbar, d. h. nach dem Aufruf der <xref:System.Data.DataRow.BeginEdit%2A>\-Methode und vor dem Aufruf der <xref:System.Data.DataRow.EndEdit%2A>\-Methode.  Auf die vorläufige Version eines Datensatzes greifen Sie i. d. R. in einem Ereignishandler zu, z. B. <xref:System.Data.DataTable.RowChanging>.  Durch den Aufruf der <xref:System.Data.DataRow.CancelEdit%2A>\-Methode werden die Änderungen rückgängig gemacht und die vorläufige Version aus der Datenzeile gelöscht.|  
  
 Die ursprüngliche und die aktuelle Version sind hilfreich, wenn Aktualisierungsinformationen an eine Datenquelle übertragen werden.  Wenn eine Aktualisierung an die Datenquelle gesendet wird, befinden sich die neuen Informationen für die Datenbank i. d. R. in der aktuellen Version des Datensatzes.  Anhand von Informationen aus der ursprünglichen Version wird der zu aktualisierende Datensatz gesucht.  Wenn der Primärschlüssel eines Datensatzes beispielsweise geändert wird, müssen Sie eine Möglichkeit haben, den richtigen Datensatz in der Datenquelle aufzufinden, damit die Daten entsprechend den Änderungen aktualisiert werden können.  Wenn keine ursprüngliche Version vorhanden ist, wird der Datensatz höchstwahrscheinlich an die Datenquelle angefügt. Daraus resultiert dann nicht nur ein ungewollter zusätzlicher, sondern auch ungenauer und nicht mehr aktueller Datensatz.  Die beiden Versionen werden außerdem in der Parallelitätssteuerung verwendet. Sie können die ursprüngliche Version mit einem Datensatz in der Datenquelle vergleichen, um festzustellen, ob der Datensatz geändert wurde, seitdem er zuletzt in das Dataset geladen wurde.  
  
 Die vorläufige Version ist von Nutzen, wenn Sie eine Validierung durchführen müssen, bevor die Änderungen am Dataset endgültig bestätigt werden.  
  
 Selbst wenn Datensätze geändert wurden, ist nicht immer eine ursprüngliche oder aktuelle Version der betreffenden Zeile verfügbar.  Wenn Sie eine neue Zeile in die Tabelle einfügen, existiert keine ursprüngliche, sondern nur eine aktuelle Version.  Auch wenn Sie eine Zeile durch den Aufruf der tabellenspezifischen `Delete`\-Methode löschen, ist eine ursprüngliche, aber keine aktuelle Version vorhanden.  
  
 Durch Abfrage der <xref:System.Data.DataRow.HasVersion%2A>\-Methode der Datenzeile können Sie überprüfen, ob eine bestimmte Version eines Datensatzes vorhanden ist.  Um auf eine der verschiedenen Datensatzversionen zuzugreifen, übergeben Sie einen <xref:System.Data.DataRowVersion>\-Enumerationswert als optionales Argument, wenn Sie den Wert einer Spalte anfordern.  
  
## Abrufen geänderter Datensätze  
 In der Regel wird nicht jeder Datensatz in einem Dataset aktualisiert.  Beispielsweise kann ein Benutzer mit einem <xref:System.Windows.Forms.DataGridView>\-Steuerelement von Windows Forms arbeiten, durch das zahlreiche Datensätze angezeigt werden.  Der Benutzer aktualisiert jedoch vielleicht nur einige wenige Datensätze, löscht einen Datensatz und fügt einen neuen ein.  Datasets und Datentabellen bieten eine Methode \(`GetChanges`\), mit deren Hilfe ausschließlich die geänderten Zeilen zurückgegeben werden können.  
  
 Sie können Teilmengen der geänderten Datensätze erstellen, indem Sie entweder die `GetChanges`\-Methode der Datentabelle \(<xref:System.Data.DataTable.GetChanges%2A>\) oder des Datasets selbst \(<xref:System.Data.DataSet.GetChanges%2A>\) verwenden.  Wenn Sie die Methode für die Datentabelle aufrufen, wird eine Kopie der Tabelle zurückgegeben, die lediglich die geänderten Datensätze enthält.  Ähnlich verhält es sich, wenn Sie die Methode für den Dataset aufrufen: Sie erhalten ein neues Dataset, das nur geänderte Datensätze enthält.  `GetChanges` gibt alle geänderten Datensätze zurück.  Im Gegensatz dazu können Sie durch Übergeben des gewünschten <xref:System.Data.DataRowState> als Parameter an die `GetChanges`\-Methode die gewünschte Teilmenge der geänderten Datensätze angeben: neu hinzugefügte Datensätze, zum Löschen markierte Datensätze, abgetrennte Datensätze oder geänderte Datensätze.  
  
 Eine Teilmenge der geänderten Datensätze abzurufen, ist besonders hilfreich, wenn Datensätze zur Verarbeitung an eine andere Komponente gesendet werden sollen.  Anstatt das gesamte Dataset zu übertragen, können Sie die Kommunikation mit der anderen Komponente gering halten, indem Sie lediglich die Datensätze abrufen, die von der Komponente benötigt werden.  Weitere Informationen finden Sie unter [Gewusst wie: Abrufen von geänderten Zeilen](../Topic/How%20to:%20Retrieve%20Changed%20Rows.md).  
  
## Ausführen eines Commit für Änderungen in einem Dataset  
 Während Sie Änderungen im Dataset vornehmen, wird die <xref:System.Data.DataRow.RowState%2A>\-Eigenschaft der geänderten Zeilen festgelegt.  Die ursprünglichen und aktuellen Datensatzversionen werden von der <xref:System.Data.DataRowView.RowVersion%2A>\-Eigenschaft eingerichtet, verwaltet und verfügbar gemacht.  Diese Eigenschaften stellen Änderungen dar. Die in den Eigenschaften gespeicherten Metadaten sind erforderlich, um die richtigen Aktualisierungen an die Datenquelle zu senden.  
  
 Wenn die Änderungen den aktuellen Zustand der Datenquelle widerspiegeln, müssen diese Informationen nicht länger beibehalten werden.  Es gibt in der Regel zwei Situationen, in denen das Dataset und seine Quelle synchron sind:  
  
-   Unmittelbar nach dem Laden von Informationen in das Dataset, z. B., wenn Sie Daten aus der Quelle einlesen.  
  
-   Nachdem Änderungen vom Dataset an die Datenquelle gesendet wurden \(jedoch nicht vorher, da die Änderungsinformationen, die zum Übertragen der Änderungen an die Datenbank erforderlich sind, ansonsten verloren gehen würden\).  
  
 Sie können für die ausstehenden Änderungen im Dataset ein Commit ausführen, indem Sie die <xref:System.Data.DataSet.AcceptChanges%2A>\-Methode aufrufen.  <xref:System.Data.DataSet.AcceptChanges%2A> wird i. d. R. in den folgenden Situationen in der Anwendung aufgerufen.  
  
-   Nachdem das Dataset geladen wurde.  Wenn Sie ein Dataset laden, indem Sie die `Fill`\-Methode eines TableAdapter aufrufen, führt der Adapter automatisch ein Commit für die Änderungen aus.  Wenn ein Dataset jedoch geladen wird, indem Sie ein anderes Dataset mit ihm zusammenführen, müssen Sie den Commit für die Änderungen manuell ausführen.  
  
    > [!NOTE]
    >  Sie können verhindern, dass der Adapter beim Aufrufen der `Fill`\-Methode den Commit für Änderungen automatisch ausführt, indem Sie die `AcceptChangesDuringFill`\-Eigenschaft des Adapters auf `false` festlegen.  Wenn sie auf `false` festgelegt ist, wird der <xref:System.Data.DataRow.RowState%2A> jeder während des Auffüllens eingefügten Zeile auf <xref:System.Data.DataRowState> festgelegt.  
  
-   Nachdem Datasetänderungen an einen anderen Prozess, z. B. an einen XML\-Webdienst, gesendet wurden.  
  
    > [!CAUTION]
    >  Wenn ein Commit für Änderungen auf diese Weise ausgeführt wird, werden sämtliche Änderungsinformationen gelöscht.  Der Commit für Änderungen sollte erst ausgeführt werden, nachdem alle Operationen abgeschlossen sind, bei denen für die Anwendung erkennbar sein muss, welche Änderungen im Dataset vorgenommen wurden.  
  
 Diese Methode umfasst folgende Schritte:  
  
-   Die <xref:System.Data.DataRowVersion>\-Version eines Datensatzes wird in seine <xref:System.Data.DataRowVersion>\-Version geschrieben, wobei die ursprüngliche Version überschrieben wird.  
  
-   Entfernt alle Zeilen, deren <xref:System.Data.DataRow.RowState%2A>\-Eigenschaft auf <xref:System.Data.DataRowState> festgelegt ist.  
  
-   Legt die <xref:System.Data.DataRow.RowState%2A>\-Eigenschaft eines Datensatzes auf <xref:System.Data.DataRowState> fest.  
  
 Die <xref:System.Data.DataSet.AcceptChanges%2A>\-Methode ist auf drei Ebenen verfügbar.  Sie kann für ein <xref:System.Data.DataRow>\-Objekt aufgerufen werden, wobei der für Änderungen ausgeführte Commit nur diese Zeile betrifft.  Sie können die Methode auch für ein <xref:System.Data.DataTable>\-Objekt aufrufen, um einen Commit für alle Zeilen in einer Tabelle auszuführen, oder für das <xref:System.Data.DataSet>\-Objekt, um einen Commit für alle ausstehenden Änderungen in sämtlichen Datensätzen aller im Dataset enthaltenen Tabellen auszuführen.  
  
 In der folgenden Tabelle wird basierend auf dem Objekt, für das die Methode aufgerufen wird, beschrieben, für welche Änderungen ein Commit ausgeführt wird.  
  
|Methode|Ergebnis|  
|-------------|--------------|  
|<xref:System.Data.DataRow.AcceptChanges%2A?displayProperty=fullName>|Ein Commit wird nur für Änderungen in der spezifischen Zeile ausgeführt.|  
|<xref:System.Data.DataTable.AcceptChanges%2A?displayProperty=fullName>|Ein Commit wird für Änderungen in allen Zeilen der spezifischen Tabelle ausgeführt.|  
|<xref:System.Data.DataSet.AcceptChanges%2A?displayProperty=fullName>|Ein Commit wird für Änderungen in allen Zeilen der Datasettabellen ausgeführt.|  
  
> [!NOTE]
>  Wenn Sie ein Dataset laden, indem Sie die `Fill`\-Methode eines TableAdapter aufrufen, müssen Änderungen nicht explizit angenommen werden; die `Fill`\-Methode ruft in der Standardeinstellung die `AcceptChanges`\-Methode auf, nachdem die Datentabelle mit Daten aufgefüllt wurde.  
  
 Eine verwandte Methode, `RejectChanges`, hebt die Auswirkungen der Änderungen auf, indem die <xref:System.Data.DataRowVersion>\-Version wieder in die <xref:System.Data.DataRowVersion>\-Version der Datensätze kopiert werden und der <xref:System.Data.DataRow.RowState%2A> der einzelnen Datensätze auf <xref:System.Data.DataRowState> zurückgesetzt wird.  
  
## Datenvalidierung  
 Um sicherzustellen, dass die in der Anwendung enthaltenen Daten die Anforderungen des Prozesses erfüllen, an den sie übergeben werden, sind oftmals Validierungen erforderlich.  Dabei wird z. B. überprüft, ob die Benutzereingaben in einem Formular oder die von einer anderen Anwendung an die Anwendung gesendeten Daten korrekt sind, oder es kann auch getestet werden, ob die innerhalb der Komponente berechneten Informationen die Einschränkungen der Datenquelle sowie die Anforderungen der Anwendung erfüllen.  
  
 Daten können auf verschiedene Weisen überprüft werden:  
  
-   In der Geschäftsschicht, indem der Anwendung Code für Datenüberprüfungen hinzugefügt wird.  Dieses Vorgehen ist nur im Dataset möglich.  Das Dataset bietet einige Vorteile der Back\-End\-Validierung, z. B. die Möglichkeit, Änderungen an Spalten\- und Zeilenwerten zu überprüfen.  Weitere Informationen finden Sie unter [Überprüfen von Daten in Datasets](../data-tools/validate-data-in-datasets.md).  
  
-   In der Präsentationsschicht, indem Formularen Validierungen hinzugefügt werden.  Weitere Informationen finden Sie unter [Validierung von Benutzereingaben in Windows Forms](../Topic/User%20Input%20Validation%20in%20Windows%20Forms.md).  
  
-   Im Back\-End der Datenschicht. Daten werden an die Datenquelle, z. B. die Datenbank, gesendet, und die Datenbank kann diese Daten annehmen oder ablehnen.  Bei Verwendung einer Datenbank, die hochentwickelte Datenüberprüfungsmechanismen besitzt und Fehlerinformationen bereitstellt, ist dieser Ansatz durchaus überlegenswert, da Daten unabhängig von ihrer Herkunft überprüft werden können.  Möglicherweise werden dabei jedoch keine anwendungsspezifischen Anforderungen in Bezug auf die Validierung berücksichtigt.  Darüber hinaus können aus der Datenüberprüfung durch die Datenquelle zahlreiche wiederholte Zugriffe auf die Datenquelle resultieren. Dies hängt davon ab, wie die vom Back\-End ausgelösten Validierungsfehler von der Anwendung behandelt werden.  
  
    > [!IMPORTANT]
    >  Wenn Sie Datenbefehle mit einer <xref:System.Data.SqlClient.SqlCommand.CommandType%2A>\-Eigenschaft mit dem Wert <xref:System.Data.CommandType> verwenden, müssen Sie die von einem Client gesendeten Informationen sorgfältig überprüfen, bevor Sie diese an die Datenbank übergeben.  Böswillige Benutzer könnten versuchen, veränderte oder zusätzliche SQL\-Anweisungen zu senden \(einzufügen\), um unautorisierten Zugriff zu erhalten oder die Datenbank zu beschädigen.  Bevor Sie Benutzereingaben an eine Datenbank übergeben, müssen Sie immer die Zulässigkeit der Informationen überprüfen. Es wird empfohlen, möglichst immer parametrisierte Abfragen oder gespeicherte Prozeduren zu verwenden.  Weitere Informationen finden Sie unter [Script Exploits Overview](../Topic/Script%20Exploits%20Overview.md).  
  
 Nachdem ein Dataset geändert wurde, können Sie die Änderungen an eine Datenquelle übertragen.  In den meisten Fällen rufen Sie dazu die `Update`\-Methode eines TableAdapter \(oder Datenadapters\) auf.  Die Methode führt einen Schleifendurchlauf durch jeden Datensatz in einer Datentabelle durch, ermittelt den ggf. erforderlichen Aktualisierungstyp \(Aktualisierung, Einfügung oder Löschvorgang\) und führt anschließend den geeigneten Befehl aus.  
  
## Übertragung einer Aktualisierung an die Datenquelle  
 Um sich die Funktionsweise einer Aktualisierung zu vergegenwärtigen, stellen Sie sich vor, dass Ihre Anwendung ein Dataset mit einer einzelnen Datentabelle verwendet.  Die Anwendung ruft zwei Zeilen aus der Datenbank ab.  Nach dem Abruf sieht die Datentabelle im Arbeitsspeicher wie folgt aus:  
  
```  
(RowState)     CustomerID   Name             Status  
(Unchanged)    c200         Robert Lyon      Good  
(Unchanged)    c400         Nancy Buchanan    Pending  
```  
  
 Die Anwendung ändert Nancy Buchanans Status in "Preferred". Durch diese Änderung wird der Wert der <xref:System.Data.DataRow.RowState%2A>\-Eigenschaft von <xref:System.Data.DataRowState> in <xref:System.Data.DataRowState> geändert.  Der Wert der <xref:System.Data.DataRow.RowState%2A>\-Eigenschaft für die erste Zeile behält den Wert <xref:System.Data.DataRowState> bei.  Die Datentabelle sieht nun wie folgt aus:  
  
```  
(RowState)     CustomerID   Name             Status  
(Unchanged)    c200         Robert Lyon      Good  
(Modified)     c400         Nancy Buchanan    Preferred  
```  
  
 Anschließend ruft die Anwendung die `Update`\-Methode auf, um das Dataset an die Datenbank zu übertragen.  Durch die Methode werden wieder die einzelnen Zeilen untersucht.  Für die erste Zeile überträgt die Methode keine SQL\-Anweisung an die Datenbank, da diese Zeile seit dem ursprünglichen Abruf aus der Datenbank nicht geändert wurde.  
  
 Für die zweite Zeile ruft die `Update`\-Methode jedoch automatisch den geeigneten Datenbefehl auf und überträgt ihn an die Datenbank.  Die spezifische Syntax der SQL\-Anweisung richtet sich nach der SQL\-Sprachvariante, die vom zugrunde liegenden Datenspeicher unterstützt wird.  Die folgenden allgemeinen Merkmale der übertragenen SQL\-Anweisung sollten jedoch beachtet werden:  
  
-   Die übertragene SQL\-Anweisung ist eine **UPDATE**\-Anweisung.  Da der Wert der <xref:System.Data.DataRow.RowState%2A>\-Eigenschaft <xref:System.Data.DataRowState> ist, ist es für Adapter offensichtlich, dass sie eine UPDATE\-Anweisung verwenden müssen.  
  
-   Die übertragene SQL\-Anweisung schließt eine **WHERE**\-Klausel ein, die als Ziel der **UPDATE**\-Anweisung die Zeile angibt, deren Wert `CustomerID = 'c400'` lautet.  Durch diesen Teil der SELECT\-Anweisung wird die Zielzeile von allen anderen Zeilen unterschieden, da die `CustomerID` der Primärschlüssel der Zieltabelle ist.  Für den Fall, dass Werte erforderlich sind, um festzustellen, ob Zeilen geändert wurden, werden die Informationen für die **WHERE**\-Klausel von der ursprünglichen Datensatzversion \(`DataRowVersion.Original`\) abgeleitet.  
  
-   Die übertragene SQL\-Anweisung umfasst eine **SET**\-Klausel, mit der der neue Wert geänderter Spalten festgelegt wird.  
  
    > [!NOTE]
    >  Wenn die `UpdateCommand`\-Eigenschaft des TableAdapter auf den Namen einer gespeicherten Prozedur festgelegt wurde, erstellt der Adapter keine SQL\-Anweisung.  Stattdessen wird die gespeicherte Prozedur mit den entsprechenden übergebenen Parametern aufgerufen.  
  
## Übergeben von Parametern  
 Werte für die zu aktualisierenden Datensätze in der Datenbank werden in der Regel mit Parametern übergeben.  Wenn von der `Update`\-Methode des TableAdapter eine UPDATE\-Anweisung ausgeführt wird, müssen die entsprechenden Parameterwerte ausgefüllt werden.  Die benötigten Werte werden aus der `Parameters`\-Auflistung des jeweiligen Datenbefehls abgerufen, in diesem Fall ist dies das `UpdateCommand`\-Objekt im TableAdapter.  
  
 Wenn der Datenadapter mithilfe der Visual Studio\-Tools generiert wurde, enthält das `UpdateCommand`\-Objekt eine Auflistung mit Parametern, die dem jeweiligen Parameterplatzhalter in der Anweisung entsprechen.  
  
 Die <xref:System.Data.SqlClient.SqlParameter.SourceColumn%2A?displayProperty=fullName>\-Eigenschaft der einzelnen Parameter zeigt auf eine Spalte in der Datentabelle.  Beispiel: Die `SourceColumn`\-Eigenschaft für den `au_id`\-Parameter und den `Original_au_id`\-Parameter wird auf die Spalte in der Datentabelle festgelegt, die die Autor\-ID enthält.  Wenn die `Update`\-Methode des Adapters ausgeführt wird, wird die Spalte mit der Autor\-ID aus dem aktualisierten Datensatz gelesen, und die Werte werden in die Anweisung eingetragen.  
  
 In einer **UPDATE**\-Anweisung müssen sowohl die neuen Werte \(die in den Datensatz geschrieben werden\) als auch die alten Werte angegeben werden \(damit der zu aktualisierende Datensatz in der Datenbank gefunden werden kann\).  Daher verfügt jeder Wert über zwei Parameter: einen für die **SET**\-Klausel und einen anderen für die **WHERE**\-Klausel.  Durch beide Parameter werden Daten aus dem aktualisierten Datensatz gelesen; sie erhalten jedoch unterschiedliche Versionen des Spaltenwerts, die auf der [SqlParameter.SourceVersion\-Eigenschaft](https://msdn.microsoft.com/en-us/library/system.data.sqlclient.sqlparameter.sourceversion.aspx) des Parameters basieren.  Für den Parameter der **SET**\-Klausel wird die aktuelle Version und für den Parameter der **WHERE**\-Klausel die ursprüngliche Version abgerufen.  
  
> [!NOTE]
>  Sie können auch selbst Werte für die `Parameters`\-Auflistung im Code festlegen. Dies erfolgt in der Regel in einem Ereignishandler für das <xref:System.Data.DataTable.RowChanging>\-Ereignis des Datenadapters.  
  
## Aktualisieren verknüpfter Tabellen  
 Wenn das Dataset mehrere Tabellen umfasst, müssen Sie diese einzeln aktualisieren, indem Sie die `Update`\-Methode der einzelnen Datenadapter separat aufrufen.  Falls die Tabellen über eine Parent\-Child\-Beziehung verfügen, müssen die Aktualisierungen wahrscheinlich in einer bestimmten Reihenfolge an die Datenbank gesendet werden.  Häufig kommt es vor, dass sowohl übergeordnete als auch verknüpfte untergeordnete Datensätze in ein Dataset eingefügt werden, z. B. ein neuer Kundendatensatz und ein oder mehrere verknüpfte Bestelldatensätze.  Wenn in der Datenbank relationale Integrität erzwungen wird, werden Fehler ausgelöst, wenn die neuen untergeordneten Datensätze an die Datenbank übertragen werden, bevor der übergeordnete Datensatz überhaupt erstellt wurde.  
  
 Wenn Sie verknüpfte Datensätze im Dataset löschen, müssen Aktualisierungen dagegen grundsätzlich in umgekehrter Reihenfolge übertragen werden: zuerst an die untergeordnete und dann an die übergeordnete Tabelle.  Andernfalls löst die Datenbank wahrscheinlich einen Fehler aus, da die referenziellen Integritätsregeln verhindern, dass ein übergeordneter Datensatz gelöscht wird, solange untergeordnete Datensätze vorhanden sind.  
  
 Grundsätzlich sollte beim Übertragen von Aktualisierungen für verknüpfte Tabellen die nachstehende Reihenfolge eingehalten werden:  
  
1.  Untergeordnete Tabelle: Datensätze löschen.  
  
2.  Übergeordnete Tabelle: Datensätze einfügen, aktualisieren und löschen.  
  
3.  Untergeordnete Tabelle: Datensätze einfügen und aktualisieren.  
  
4.  Weitere Informationen finden Sie unter [Exemplarische Vorgehensweise: Speichern von Daten in einer Datenbank \(mehrere Tabellen\)](../data-tools/save-data-to-a-database-multiple-tables.md).  
  
## Parallelitätssteuerung  
 Da Datasets von der Datenquelle getrennt sind, unterliegen die Datensätze in der Datenquelle keiner Sperrung.  Falls Sie die Datenbank aktualisieren möchten und die Parallelitätssteuerung für die Anwendung berücksichtigt werden muss, müssen Sie die Datensätze im Dataset daher mit denen in der Datenbank abgleichen.  Möglicherweise stellen Sie fest, dass die Datensätze in der Datenbank geändert wurden, seit das Dataset zuletzt aufgefüllt wurde.  In diesem Fall müssen Sie die anwendungsspezifische Logik ausführen, um festzulegen, wie der Datenbankdatensatz oder der geänderte Datensatz in Ihrem Dataset behandelt werden soll.  
  
## Siehe auch  
 [Übersicht über TableAdapters](../data-tools/tableadapter-overview.md)   
 [Gewusst wie: Aktualisieren von Daten mit einem TableAdapter](../data-tools/update-data-by-using-a-tableadapter.md)   
 [Übersicht über Datenanwendungen in Visual Studio](../data-tools/overview-of-data-applications-in-visual-studio.md)   
 [Herstellen von Datenverbindungen in Visual Studio](../data-tools/connecting-to-data-in-visual-studio.md)   
 [Vorbereiten der Anwendung auf den Empfang von Daten](../Topic/Preparing%20Your%20Application%20to%20Receive%20Data.md)   
 [Abrufen von Daten für die Anwendung](../data-tools/fetching-data-into-your-application.md)   
 [Binden von Steuerelementen an Daten in Visual Studio](../data-tools/bind-controls-to-data-in-visual-studio.md)   
 [Bearbeiten von Daten in der Anwendung](../data-tools/editing-data-in-your-application.md)   
 [Überprüfen von Daten](../Topic/Validating%20Data.md)   
 [Speichern von Daten](../data-tools/saving-data.md)