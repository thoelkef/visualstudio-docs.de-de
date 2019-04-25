---
title: Rückspeichern von Daten in der Datenbank | Microsoft-Dokumentation
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
- datasets [Visual Basic], validating data
- data validation, datasets
- data [Visual Studio], saving
- row version
- updating datasets, constraints
- datasets [Visual Basic], about datasets
- datasets [Visual Basic], merging
- updates, constraints in datasets
- saving data, about saving data
- datasets [Visual Basic], constraints
- TableAdapters
ms.assetid: afe6cb8a-dc6a-428b-b07b-903ac02c890b
caps.latest.revision: 31
author: gewarren
ms.author: gewarren
manager: jillfra
ms.openlocfilehash: b0489dec1c2d6cb3d7559a2bdd029ccab6c3ce5f
ms.sourcegitcommit: 1fc6ee928733e61a1f42782f832ead9f7946d00c
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/22/2019
ms.locfileid: "60056808"
---
# <a name="save-data-back-to-the-database"></a>Rückspeichern von Daten in der Datenbank
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Das Dataset ist eine in-Memory-Kopie der Daten. Wenn Sie diese Daten ändern, ist es empfiehlt sich, diese Änderungen in der Datenbank zu speichern. Sie führen dies in einer von drei Methoden:  
  
- Durch Aufrufen einer der `Update` Methoden eines TableAdapters  
  
- Indem Sie eine der DBDirect-Methoden des TableAdapter aufrufen  
  
- Durch die UpdateAll-Methode aufrufen, für die `TableAdapterManager` , die von Visual Studio für Sie generiert, wenn der Dataset Tabellen enthält, die auf andere Tabellen im Dataset verknüpft sind  
  
  Wenn Sie Daten an Steuerelemente auf einer Windows Form oder XAML-Seite zu Dataset-Tabellen binden, funktioniert die Datenbindungsarchitektur alle die für Sie.  
  
  Wenn Sie mit TableAdapters vertraut sind, können Sie direkt auf einen der folgenden Themen springen:  
  
|Thema|Beschreibung|  
|-----------|-----------------|  
|[Gewusst wie: Einfügen neuer Datensätze in eine Datenbank](../data-tools/insert-new-records-into-a-database.md)|Gewusst wie: Ausführen aktualisiert und fügt mit TableAdapters oder Befehl Objekte|  
|[Gewusst wie: Aktualisieren von Daten mit einem TableAdapter](../data-tools/update-data-by-using-a-tableadapter.md)|Gewusst wie: Ausführen von Aktualisierungen mit TableAdapters|  
|[Hierarchische Aktualisierung](../data-tools/hierarchical-update.md)|Gewusst wie: Ausführen von Updates aus einem Dataset mit zwei oder mehr verknüpfte Tabellen|  
|[Behandeln einer Parallelitätsausnahme](../data-tools/handle-a-concurrency-exception.md)|Wie Ausnahmen behandelt, wenn zwei Benutzer versuchen, dieselben Daten in einer Datenbank zur gleichen Zeit zu ändern.|  
|[Gewusst wie: Speichern von Daten mithilfe von Transaktionen](../data-tools/save-data-by-using-a-transaction.md)|Gewusst wie: Speichern von Daten in einer Transaktion mit System.Transactions-Namespace und die TransactionScope-Objekt|  
|[Speichern von Daten in einer Transaktion](../data-tools/save-data-in-a-transaction.md)|Gewusst wie: Speichern von Daten in einer Transaktion mit System.Transactions-namespace|  
|[Speichern von Daten in einer Datenbank (mehrere Tabellen)](../data-tools/save-data-to-a-database-multiple-tables.md)|Wie Sie Datensätze bearbeiten und Speichern von Änderungen in mehreren Tabellen in der Datenbank|  
|[Gewusst wie: Speichern von Daten aus einem Objekt in einer Datenbank](../data-tools/save-data-from-an-object-to-a-database.md)|Wie Sie Daten aus einem Objekt zu übergeben, die nicht in einem Dataset mit einer Datenbank mithilfe einer TableAdapter-DbDirect-Methode|  
|[Speichern von Daten mit den TableAdapter-DBDirect-Methoden](../data-tools/save-data-with-the-tableadapter-dbdirect-methods.md)|Wie der TableAdapter verwenden, um SQL-Abfragen direkt an die Datenbank zu senden.|  
|[Speichern eines Datasets als XML](../data-tools/save-a-dataset-as-xml.md)|Wie Sie ein Dataset in ein XML-Dokument zu speichern.|  
  
## <a name="two-stage-updates"></a>Zweistufige Aktualisierungen  
 Aktualisieren einer Datenquelle ist ein zweistufiger Prozess. Der erste Schritt ist das Dataset mit neuen Datensätzen, geänderten Datensätze oder gelöschten Datensätze zu aktualisieren. Wenn Ihre Anwendung diese Änderungen nicht zurück an die Datenquelle gesendet werden, sind Sie das Update nicht mehr benötigen.  
  
 Wenn Sie die Änderungen zurück in die Datenbank senden, ist ein zweiter Schritt erforderlich. Wenn Sie nicht von datengebundenen Steuerelementen verwenden, müssen Sie manuell die TableAdapter (oder Datenadapters) die Update-Methode aufrufen, mit denen Sie das Dataset zu füllen. Allerdings können Sie verschiedene Adaptern, z. B. auch zum Verschieben von Daten aus einer Datenquelle in eine andere oder zum Aktualisieren mehrerer Datenquellen verwenden. Wenn Sie sind nicht mit der Datenbindung und Änderungen an verknüpften Tabellen speichern, müssen Sie eine Variable, der automatisch generierten TableAdapterManager-Klasse manuell instanziieren und rufen Sie dann die UpdateAll-Methode.  
  
 ![Visual Basic-Dataset-Aktualisierungen](../data-tools/media/vbdatasetupdates.gif "VbDatasetUpdates")  
Zweistufiger Aktualisierungsprozess und die Bedeutung von "DataRowVersion" in einer erfolgreichen Aktualisierung  
  
 Ein Dataset enthält Auflistungen, die eine Auflistung von Zeilen enthalten. Wenn Sie eine zugrunde liegende Datenquelle später aktualisieren möchten, müssen Sie die Methoden auf die DataTable.DataRowCollection-Eigenschaft, die beim Hinzufügen oder Entfernen von Zeilen verwenden. Diese Methoden führen Sie das Nachverfolgen von Änderungen, das für die Aktualisierung der Datenquelle erforderlich ist. Wenn Sie die RemoveAt-Auflistung für die Rows-Eigenschaft aufrufen, wird nicht das Löschen an die Datenbank übermittelt werden.  
  
## <a name="merge-datasets"></a>Zusammenführen von datasets  
 Sie können den Inhalt eines Datasets aktualisieren *zusammenführen* mit einem anderen Dataset. Dies umfasst das Kopieren der Inhalte von einer *Quelle* Dataset in das aufrufende Dataset (genannt die *Ziel* Dataset). Beim Zusammenführen von Datasets werden neue Datensätze aus dem Quell-Dataset in das Ziel-Dataset eingefügt. Darüber hinaus werden dem Ziel-Dataset zusätzliche Spalten aus dem Quell-Dataset hinzugefügt. Zusammenführen von Datasets ist nützlich, wenn Sie ein lokales Dataset haben und Sie ein zweites Dataset aus einer anderen Anwendung erhalten. Es ist auch nützlich, wenn Sie ein zweites Dataset aus einer Komponente, z. B. eine XML-Webdienst abrufen, oder wenn Sie Daten aus mehreren Datasets integrieren müssen.  
  
 Beim Zusammenführen von Datasets können Sie ein boolesches Argument übergeben (`preserveChanges`), informiert die <xref:System.Data.DataSet.Merge%2A> Methode angibt, ob bestehende Änderungen im Ziel-Dataset beibehalten werden sollen. Da Datasets mehrere Datensatzversionen verwalten, darf nicht außer Acht gelassen werden, dass auch mehrere Datensatzversionen zusammengeführt werden. Die folgende Tabelle zeigt, wie ein Datensatz in beiden Datasets zusammengeführt werden:  
  
|DataRowVersion|Ziel-Dataset|Quell-Dataset|  
|--------------------|--------------------|--------------------|  
|Ursprünglich|James Wilson|James C. Wilson|  
|Aktuell|Jim Wilson|James C. Wilson|  
  
 Aufrufen der <xref:System.Data.DataSet.Merge%2A> Methode in der vorherigen Tabelle mit `preserveChanges=false targetDataset.Merge(sourceDataset)` ergibt die folgende:  
  
|DataRowVersion|Ziel-Dataset|Quell-Dataset|  
|--------------------|--------------------|--------------------|  
|Ursprünglich|James C. Wilson|James C. Wilson|  
|Aktuell|James C. Wilson|James C. Wilson|  
  
 Durch den Aufruf der <xref:System.Data.DataSet.Merge%2A>-Methode mit `preserveChanges = true targetDataset.Merge(sourceDataset, true)` erzielen Sie das folgende Ergebnis:  
  
|DataRowVersion|Ziel-Dataset|Quell-Dataset|  
|--------------------|--------------------|--------------------|  
|Ursprünglich|James C. Wilson|James C. Wilson|  
|Aktuell|Jim Wilson|James C. Wilson|  
  
> [!CAUTION]
>  In der `preserveChanges = true` Szenario, wenn die <xref:System.Data.DataSet.RejectChanges%2A> Methode wird aufgerufen, für einen Datensatz im Ziel-Dataset, und es wird auf die ursprünglichen Daten zurückgesetzt, die *Quelle* Dataset. Dies bedeutet, dass wenn Sie versuchen, die ursprüngliche Datenquelle mit dem Ziel-Dataset zu aktualisieren, es nicht die ursprüngliche zu aktualisierende Zeile zu finden. Sie können eine parallelitätsverletzung verhindern, indem Sie ein anderes Dataset mit den aktualisierten Datensätzen aus der Datenquelle füllen und anschließend einen Merge, um zu verhindern, dass eine parallelitätsverletzung ausführen. (Eine Parallelitätsverletzung liegt vor, wenn ein anderer Benutzer einen Datensatz in der Datenquelle ändert, nachdem das Dataset aufgefüllt wurde.)  
  
## <a name="update-constraints"></a>Einschränkungen bei der Aktualisierung  
 Um Änderungen an einer vorhandenen Datenzeile vorzunehmen, hinzufügen oder Aktualisieren von Daten in die einzelnen Spalten aus. Wenn der Dataset Einschränkungen (z. B. Fremdschlüsseln oder NULL-Einschränkungen) enthält, ist es möglich, dass der Datensatz in einem Fehlerzustand vorübergehend sein kann, wie Sie sie aktualisieren. Das heißt, kann es in einem Fehlerzustand sein, klicken Sie nach dem Update einer Spalte, aber bevor Sie zur nächsten erhalten.  
  
 Um vorzeitige Verletzungen dieser Einschränkungen zu vermeiden, können Sie sie vorübergehend außer Kraft setzen. Bei diesem Verfahren werden zwei Ziele verfolgt:  
  
- Es wird verhindert, dass einen Fehler ausgelöst wird, nachdem Sie haben das Update einer Spalte wurde abgeschlossen, jedoch noch nicht gestartet, aktualisieren einen anderen.  
  
- Es wird verhindert, dass bestimmte Updates werden nicht ausgelöst (Ereignisse, die häufig für die Überprüfung verwendet werden).  
  
  Nachdem Sie eine Aktualisierung abgeschlossen ist, können Sie erneut aktivieren Überprüfung von Einschränkungen, die auch Aktualisierungsereignisse wieder aktiviert und ausgelöst werden.  
  
> [!NOTE]
>  In Windows Forms, hält der Architektur für die Datenbindung, die in das DataGrid-Steuerelement basiert einschränkungsüberprüfung, bis der Fokus aus eine Zeile aus, und Sie nicht explizit aufrufen müssen, die <xref:System.Data.DataRow.BeginEdit%2A>, <xref:System.Data.DataRow.EndEdit%2A>, oder <xref:System.Data.DataRow.CancelEdit%2A> Methoden.  
  
 Beim Aufruf der <xref:System.Data.DataSet.Merge%2A>-Methode für ein Dataset werden Einschränkungen automatisch deaktiviert. Wenn die Zusammenführung abgeschlossen ist, wenn alle Einschränkungen für das Dataset, das nicht aktiviert werden kann, es gibt eine <xref:System.Data.ConstraintException> ausgelöst. In einer solchen Situation ist die <xref:System.Data.DataSet.EnforceConstraints%2A>-Eigenschaft auf `false,` festgelegt, und alle Einschränkungsverletzungen müssen vor dem Zurücksetzen der <xref:System.Data.DataSet.EnforceConstraints%2A>-Eigenschaft auf `true` aufgelöst werden.  
  
 Nachdem Sie eine Aktualisierung abgeschlossen ist, können Sie erneut aktivieren Überprüfung von Einschränkungen, die auch Aktualisierungsereignisse wieder aktiviert und ausgelöst werden.  
  
 Weitere Informationen zum Aufheben von Ereignissen finden Sie unter [Deaktivieren von Einschränkungen beim Auffüllen von Datasets](../data-tools/turn-off-constraints-while-filling-a-dataset.md).  
  
## <a name="dataset-update-errors"></a>Fehler bei der Datasetaktualisierung  
 Bei der Aktualisierung von Datensätzen in einen Dataset können Fehler auftreten. Sie können z. B. versehentlich schreiben Daten des falschen Typs an eine Spalte, oder Daten, die zu lang ist oder Daten, die ein anderes Integritätsproblem verursacht hat. Sie können auch anwendungsspezifische Überprüfungen, die während jeder Phase eines Aktualisierungsereignisses benutzerdefinierte Fehler auslösen können. Weitere Informationen finden Sie unter [Überprüfen von Daten in Datasets](../data-tools/validate-data-in-datasets.md).  
  
## <a name="maintaining-information-about-changes"></a>Verwalten von Informationen über Änderungen  
 Informationen zu den Änderungen in einem Dataset wird auf zwei Arten verwaltet: durch das Kennzeichnen von Zeilen, die angeben, dass sie geändert haben (<xref:System.Data.DataRow.RowState%2A>), und durch die Speicherung mehrerer Kopien eines Datensatzes (<xref:System.Data.DataRowVersion>). Mithilfe dieser Informationen können die geänderten Daten im Dataset vom Prozess ermittelt und die entsprechenden Aktualisierungen an die Datenquelle gesendet werden.  
  
### <a name="rowstate-property"></a>RowState-Eigenschaft  
 Die <xref:System.Data.DataRow.RowState%2A>-Eigenschaft eines <xref:System.Data.DataRow>-Objekts stellt einen Wert dar, der Informationen zum Status einer bestimmten Datenzeile bereitstellt.  
  
 In der folgenden Tabelle sind die möglichen Werte für die <xref:System.Data.DataRowState>-Enumeration aufgeführt:  
  
|DataRowState-Wert|Beschreibung|  
|------------------------|-----------------|  
|<xref:System.Data.DataRowState>|Die Zeile wurde einer <xref:System.Data.DataRowCollection> als Element hinzugefügt. (Eine Zeile in diesem Status keine entsprechende ursprüngliche Version, da sie nicht vorhanden war bei der letzten <xref:System.Data.DataRow.AcceptChanges%2A> Methode wurde aufgerufen).|  
|<xref:System.Data.DataRowState>|Die Zeile wurde mit <xref:System.Data.DataRow.Delete%2A> eines <xref:System.Data.DataRow>-Objekts gelöscht.|  
|<xref:System.Data.DataRowState>|Die Zeile wurde zwar erstellt, gehört aber keiner <xref:System.Data.DataRowCollection> an. Ein <xref:System.Data.DataRow> Objekt befindet sich in diesem Zustand, unmittelbar nachdem es erstellt wurde, bevor sie zu einer Auflistung hinzugefügt wurde, und nachdem er aus einer Auflistung entfernt wurde.|  
|<xref:System.Data.DataRowState>|Ein Spaltenwert in der Zeile wurde in irgendeiner Weise geändert.|  
|<xref:System.Data.DataRowState>|Die Zeile wurde seit dem letzten Aufruf von <xref:System.Data.DataRow.AcceptChanges%2A> nicht geändert.|  
  
### <a name="datarowversion-enumeration"></a>DataRowVersion-Enumeration  
 In Datasets werden mehrere Datensatzversionen verwaltet. Die <xref:System.Data.DataRowVersion>-Enumeration eines <xref:System.Data.DataRow>-Objekts stellt einen Wert dar, der zum Zurückgeben einer bestimmten Version eines <xref:System.Data.DataRow>-Objekts verwendet werden kann.  
  
 In der folgenden Tabelle sind die möglichen Werte für die <xref:System.Data.DataRowVersion>-Enumeration aufgeführt:  
  
|DataRowVersion-Wert|Beschreibung|  
|--------------------------|-----------------|  
|<xref:System.Data.DataRowVersion>|Die aktuelle Version eines Datensatzes enthält alle Änderungen, die für den Datensatz seit dem letzten ausgeführt wurden <xref:System.Data.DataRow.AcceptChanges%2A> aufgerufen wurde. Falls die Zeile gelöscht wurde, ist keine aktuelle Version vorhanden.|  
|<xref:System.Data.DataRowVersion>|Der Standardwert eines Datensatzes, wie er durch das Dataset-Schema oder die Datenquelle definiert wurde.|  
|<xref:System.Data.DataRowVersion>|Die ursprüngliche Version eines Datensatzes ist eine Kopie des Datensatzes zu dem Zeitpunkt, zu dem zuletzt ein Commit für Dataset-Änderungen ausgeführt wurde. Praktisch entspricht dies meist der Version eines Datensatzes, die aus einer Datenquelle gelesen wurde.|  
|<xref:System.Data.DataRowVersion>|Die vorläufige Version eines Datensatzes ist während der laufenden Aktualisierung vorübergehend verfügbar, d.h. nach dem Aufruf der <xref:System.Data.DataRow.BeginEdit%2A>-Methode und vor dem Aufruf der <xref:System.Data.DataRow.EndEdit%2A>-Methode. Auf die vorläufige Version eines Datensatzes greifen Sie i. d. R. in einem Ereignishandler zu, z. B. <xref:System.Data.DataTable.RowChanging>. Durch den Aufruf der <xref:System.Data.DataRow.CancelEdit%2A>-Methode werden die Änderungen rückgängig gemacht und die vorläufige Version aus der Datenzeile gelöscht.|  
  
 Die ursprüngliche und die aktuelle Version sind hilfreich, wenn Aktualisierungsinformationen an eine Datenquelle übertragen werden. Wenn eine Aktualisierung an die Datenquelle gesendet wird, befinden sich die neuen Informationen für die Datenbank i. d. R. in der aktuellen Version des Datensatzes. Anhand von Informationen aus der ursprünglichen Version wird der zu aktualisierende Datensatz gesucht.  
  
 In einem Fall, in denen der Primärschlüssel eines Datensatzes geändert wird, benötigen Sie z. B. eine Möglichkeit, den richtigen Datensatz in der Datenquelle zu finden, um die Änderungen zu aktualisieren. Wenn keine ursprüngliche Version vorhanden ist, wird der Datensatz höchstwahrscheinlich an die Datenquelle angefügt. Daraus resultiert dann nicht nur ein ungewollter zusätzlicher, sondern auch ungenauer und nicht mehr aktueller Datensatz. Die beiden Versionen werden auch in der parallelitätssteuerung verwendet. Sie können vergleichen, die ursprüngliche Version mit einem Datensatz in der Datenquelle, um festzustellen, ob der Datensatz geändert wurde, seit es in das Dataset geladen wurde.  
  
 Die vorläufige Version ist von Nutzen, wenn Sie eine Validierung durchführen müssen, bevor die Änderungen am Dataset endgültig bestätigt werden.  
  
 Selbst wenn Datensätze geändert wurden, ist nicht immer eine ursprüngliche oder aktuelle Version der betreffenden Zeile verfügbar. Wenn Sie eine neue Zeile in die Tabelle einfügen, existiert keine ursprüngliche, sondern nur eine aktuelle Version. Auch wenn Sie eine Zeile durch den Aufruf der tabellenspezifischen `Delete`-Methode löschen, ist eine ursprüngliche, aber keine aktuelle Version vorhanden.  
  
 Durch Abfrage der <xref:System.Data.DataRow.HasVersion%2A>-Methode der Datenzeile können Sie überprüfen, ob eine bestimmte Version eines Datensatzes vorhanden ist. Um auf eine der verschiedenen Datensatzversionen zuzugreifen, übergeben Sie einen <xref:System.Data.DataRowVersion>-Enumerationswert als optionales Argument, wenn Sie den Wert einer Spalte anfordern.  
  
## <a name="getting-changed-records"></a>Beim Abrufen der geänderten Datensätze  
 Es ist üblich, nicht zu jeder Datensatz in einem Dataset zu aktualisieren. Beispielsweise kann ein Benutzer mit einem <xref:System.Windows.Forms.DataGridView>-Steuerelement von Windows Forms arbeiten, durch das zahlreiche Datensätze angezeigt werden. Der Benutzer aktualisiert jedoch vielleicht nur einige wenige Datensätze, löscht einen Datensatz und fügt einen neuen ein. Datasets und Datentabellen bieten eine Methode (`GetChanges`), mit deren Hilfe ausschließlich die geänderten Zeilen zurückgegeben werden können.  
  
 Sie können Teilmengen der geänderten Datensätze erstellen, indem Sie entweder die `GetChanges`-Methode der Datentabelle (<xref:System.Data.DataTable.GetChanges%2A>) oder des Datasets selbst (<xref:System.Data.DataSet.GetChanges%2A>) verwenden. Wenn Sie die Methode für die Datentabelle aufrufen, wird eine Kopie der Tabelle zurückgegeben, die lediglich die geänderten Datensätze enthält. Ähnlich verhält es sich, wenn Sie die Methode für den Dataset aufrufen: Sie erhalten ein neues Dataset, das nur geänderte Datensätze enthält.  
  
 `GetChanges` selbst gibt Sie alle geänderten Datensätze zurück. Im Gegensatz dazu, indem Sie die gewünschte übergeben <xref:System.Data.DataRowState> als Parameter an die `GetChanges` -Methode, Sie können angeben, welche Teilmengen der geänderten Datensätze werden sollen: neu hinzugefügte Datensätze, Datensätze, die zum Löschen markiert sind, abgetrennte Datensätze oder geänderte Datensätze.  
  
 Abrufen einer Teilmenge der geänderten Datensätze ist nützlich, wenn Sie Datensätze an eine andere Komponente für die Verarbeitung senden möchten. Anstatt das gesamte Dataset zu übertragen, können Sie die Kommunikation mit der anderen Komponente gering halten, indem Sie lediglich die Datensätze abrufen, die von der Komponente benötigt werden. Weitere Informationen finden Sie unter [Vorgehensweise: Abrufen von geänderten Zeilen](http://msdn.microsoft.com/library/6ff0cbd0-5253-48e7-888a-144d56c2e0a9).  
  
## <a name="committing-changes-in-the-dataset"></a>Ausführen eines Commits für Änderungen in einem dataset  
 Während Sie Änderungen im Dataset vornehmen, wird die <xref:System.Data.DataRow.RowState%2A>-Eigenschaft der geänderten Zeilen festgelegt. Die ursprünglichen und aktuellen Datensatzversionen eingerichtet, verwaltet und Zweck zur Verfügung gestellt werden die <xref:System.Data.DataRowView.RowVersion%2A> Eigenschaft. Die Metadaten, die in den Eigenschaften dieser geänderten Zeilen gespeichert sind, ist für die senden die richtigen Updates an der Datenquelle erforderlich.  
  
 Wenn die Änderungen den aktuellen Zustand der Datenquelle widerspiegeln, müssen diese Informationen nicht länger beibehalten werden. Es gibt in der Regel zwei Situationen, in denen das Dataset und seine Quelle synchron sind:  
  
- Unmittelbar nach dem Laden von Informationen in das Dataset, z. B., wenn Sie Daten aus der Quelle einlesen.  
  
- Nach dem Senden von Änderungen aus dem Dataset mit der Datenquelle (jedoch nicht vorher, da Sie die neuen Daten verlieren würden, die zum Senden von Änderungen an der Datenbank erforderlich ist).  
  
  Sie können für die ausstehenden Änderungen im Dataset ein Commit ausführen, indem Sie die <xref:System.Data.DataSet.AcceptChanges%2A>-Methode aufrufen. In der Regel <xref:System.Data.DataSet.AcceptChanges%2A> wird bei den folgenden Situationen in Ihrer Anwendung aufgerufen.  
  
- Nach dem Laden Sie des Datasets. Wenn Sie ein Dataset laden, indem Sie die `Fill`-Methode eines TableAdapter aufrufen, führt der Adapter automatisch ein Commit für die Änderungen aus. Wenn ein Dataset jedoch geladen wird, indem Sie ein anderes Dataset mit ihm zusammenführen, müssen Sie den Commit für die Änderungen manuell ausführen.  
  
  > [!NOTE]
  >  Sie können verhindern, dass den Adapter automatisch Commit für Änderungen beim Aufrufen der `Fill` Methode durch Festlegen der `AcceptChangesDuringFill` Eigenschaft des Adapters zum `false`. Wenn sie, um festgelegt ist `false`, und klicken Sie dann die <xref:System.Data.DataRow.RowState%2A> jeder Zeile, die während des Auffüllens eingefügt wird festgelegt ist <xref:System.Data.DataRowState>.  
  
- Nachdem Sie Datasetänderungen an einem anderen Prozess, z. B. eine XML-Webdienst gesendet.  
  
  > [!CAUTION]
  >  Wenn ein Commit für Änderungen auf diese Weise ausgeführt wird, werden sämtliche Änderungsinformationen gelöscht. Keine Änderungen erst nach dem führen Sie Ausführen von Vorgängen, die erfordern, dass Ihre Anwendung wissen, welche Änderungen im Dataset vorgenommen wurden abgeschlossen.  
  
  Diese Methode umfasst folgende Schritte:  
  
- Schreibt die <xref:System.Data.DataRowVersion> Version eines Datensatzes in die <xref:System.Data.DataRowVersion> Version und die ursprüngliche Version überschrieben.  
  
- Entfernt jede Zeile, in denen die <xref:System.Data.DataRow.RowState%2A> -Eigenschaftensatz auf <xref:System.Data.DataRowState>.  
  
- Legt die <xref:System.Data.DataRow.RowState%2A>-Eigenschaft eines Datensatzes auf <xref:System.Data.DataRowState> fest.  
  
  Die <xref:System.Data.DataSet.AcceptChanges%2A>-Methode ist auf drei Ebenen verfügbar. Sie erreichen ihn auf eine <xref:System.Data.DataRow> Objekt, das Commits ändert sich nur diese Zeile. Sie können es auch aufrufen, auf eine <xref:System.Data.DataTable> Objekt, um alle Zeilen in einer Tabelle zu übernehmen. Schließlich können Sie ihn aufrufen auf der <xref:System.Data.DataSet> Objekt, um alle ausstehenden Änderungen in sämtlichen Datensätzen aller Tabellen des Datasets zu übernehmen.  
  
  In der folgenden Tabelle wird basierend auf dem Objekt, für das die Methode aufgerufen wird, beschrieben, für welche Änderungen ein Commit ausgeführt wird.  
  
|Methode|Ergebnis|  
|------------|------------|  
|<xref:System.Data.DataRow.AcceptChanges%2A?displayProperty=fullName>|Ein Commit wird nur für Änderungen in der spezifischen Zeile ausgeführt.|  
|<xref:System.Data.DataTable.AcceptChanges%2A?displayProperty=fullName>|Ein Commit wird für Änderungen in allen Zeilen der spezifischen Tabelle ausgeführt.|  
|<xref:System.Data.DataSet.AcceptChanges%2A?displayProperty=fullName>|Ein Commit wird für Änderungen in allen Zeilen der Datasettabellen ausgeführt.|  
  
> [!NOTE]
>  Wenn Sie ein Dataset laden, durch den Aufruf des TableAdapter `Fill` -Methode, Sie müssen keine Änderungen zu übernehmen. In der Standardeinstellung die `Fill` Methodenaufrufe der `AcceptChanges` Methode nach der Fertigstellung der Datentabelle mit Daten aufgefüllt.  
  
 Eine verwandte Methode, `RejectChanges`, macht die Auswirkungen der Änderungen durch Kopieren der <xref:System.Data.DataRowVersion> -Version wieder in die <xref:System.Data.DataRowVersion> Version von Datensätzen. Außerdem wird die <xref:System.Data.DataRow.RowState%2A> des jedes Datensatzes wieder an <xref:System.Data.DataRowState>.  
  
## <a name="data-validation"></a>Datenvalidierung  
 Um sicherzustellen, dass die in der Anwendung enthaltenen Daten die Anforderungen des Prozesses erfüllen, an den sie übergeben werden, sind oftmals Validierungen erforderlich. Dabei wird z. B. überprüfen, ob die Eingabe eines Benutzers in einem Formular richtig ist, Überprüfen von Daten, die für Ihre Anwendung von einer anderen Anwendung gesendet wird, oder überprüfen auch, dass die innerhalb der Komponente berechneten Informationen innerhalb der Einschränkungen der Datenquelle liegt und anwendungsanforderungen.  
  
 Daten können auf verschiedene Weisen überprüft werden:  
  
- In der Geschäftsschicht, indem der Anwendung Code für Datenüberprüfungen hinzugefügt wird. Dieses Vorgehen ist nur im Dataset möglich. Der DataSet-Designer bietet einige Vorteile der Back-End-Validierung, z. B. die Möglichkeit zur Überprüfung von Änderungen, wie Spalten-und Zeilenwerten geändert werden. Weitere Informationen finden Sie unter [Überprüfen von Daten in Datasets](../data-tools/validate-data-in-datasets.md).  
  
- In der Präsentationsschicht, indem Formularen Validierungen hinzugefügt werden. Weitere Informationen finden Sie unter [User Input Validation in Windows Forms](http://msdn.microsoft.com/library/4ec07681-1dee-4bf9-be5e-718f635a33a1).  
  
- Im Back-End der Datenschicht. Daten werden an die Datenquelle, z. B. die Datenbank, gesendet, und die Datenbank kann diese Daten annehmen oder ablehnen. Bei Verwendung einer Datenbank, die hochentwickelte Datenüberprüfungsmechanismen besitzt und Fehlerinformationen bereitstellt, ist dieser Ansatz durchaus überlegenswert, da Daten unabhängig von ihrer Herkunft überprüft werden können. Allerdings kann dieser Ansatz nicht anwendungsspezifische validierungsanforderungen Rechnung tragen. Darüber hinaus kann die Datenquelle aus, überprüfen Sie die Daten dazu führen, dass in zahlreiche Roundtrips an die Datenquelle, je nachdem, wie die Auflösung der vom Back-End ausgelösten Validierungsfehler von der Anwendung behandelt.  
  
  > [!IMPORTANT]
  >  Wenn Sie Datenbefehle mit einer <xref:System.Data.SqlClient.SqlCommand.CommandType%2A> Eigenschaft, um festgelegt wird <xref:System.Data.CommandType>, sorgfältig überprüfen, die von einem Client gesendet wird, vor der Übergabe an die Datenbank. Böswillige Benutzer könnten versuchen, veränderte oder zusätzliche SQL-Anweisungen zu senden (einzufügen), um unautorisierten Zugriff zu erhalten oder die Datenbank zu beschädigen. Bevor Sie Benutzereingaben in einer Datenbank übertragen, immer überprüfen, ob die Informationen gültig sind. Es wird empfohlen, parametrisierte Abfragen oder gespeicherte Prozeduren, die nach Möglichkeit immer zu verwenden. Weitere Informationen finden Sie unter [Übersicht über Skriptangriffe](http://msdn.microsoft.com/library/772c7312-211a-4eb3-8d6e-eec0aa1dcc07).  
  
  Nachdem ein Dataset geändert wurde, können Sie die Änderungen an eine Datenquelle übertragen. In den meisten Fällen rufen Sie dazu die `Update`-Methode eines TableAdapter (oder Datenadapters) auf. Die Methode durchläuft jeden Datensatz in einer Datentabelle, bestimmt, welche Art von Update erforderlich ist (zu aktualisieren, einfügen oder löschen), sofern vorhanden, und führt dann den entsprechenden Befehl.  
  
## <a name="transmitting-updates-to-the-data-source"></a>Übertragen von Updates mit der Datenquelle  
 Eine Abbildung, wie Updates vorgenommen werden nehmen Sie an, dass Ihre Anwendung ein Dataset verwendet, die eine einzelnen Datentabelle enthält. Die Anwendung ruft zwei Zeilen aus der Datenbank ab. Nach dem Abruf sieht die Datentabelle im Arbeitsspeicher wie folgt aus:  
  
```  
(RowState)     CustomerID   Name             Status  
(Unchanged)    c200         Robert Lyon      Good  
(Unchanged)    c400         Nancy Buchanan    Pending  
```  
  
 Die Anwendung ändert Nancy Buchanans Status in "Preferred". Durch diese Änderung wird der Wert der <xref:System.Data.DataRow.RowState%2A>-Eigenschaft von <xref:System.Data.DataRowState> in <xref:System.Data.DataRowState> geändert. Der Wert der <xref:System.Data.DataRow.RowState%2A>-Eigenschaft für die erste Zeile behält den Wert <xref:System.Data.DataRowState> bei. Die Datentabelle sieht nun wie folgt aus:  
  
```  
(RowState)     CustomerID   Name             Status  
(Unchanged)    c200         Robert Lyon      Good  
(Modified)     c400         Nancy Buchanan    Preferred  
```  
  
 Anschließend ruft die Anwendung die `Update`-Methode auf, um das Dataset an die Datenbank zu übertragen. Durch die Methode werden wieder die einzelnen Zeilen untersucht. Für die erste Zeile überträgt die Methode keine SQL-Anweisung an die Datenbank, da diese Zeile seit dem ursprünglichen Abruf aus der Datenbank nicht geändert wurde.  
  
 Für die zweite Zeile, jedoch die `Update` Methode automatisch Ruft den Befehl für die richtigen Daten und überträgt ihn an die Datenbank. Die spezielle Syntax der SQL-Anweisung hängt von der SQL-Dialekt der, die von den zugrunde liegenden Datenspeicher unterstützt wird. Die folgenden allgemeinen Merkmale der übertragenen SQL-Anweisung sollten jedoch beachtet werden:  
  
- Die übertragene SQL-Anweisung ist eine UPDATE-Anweisung. Da der Wert der <xref:System.Data.DataRow.RowState%2A>-Eigenschaft <xref:System.Data.DataRowState> ist, ist es für Adapter offensichtlich, dass sie eine UPDATE-Anweisung verwenden müssen.  
  
- Die übertragene SQL-Anweisung schließt eine WHERE-Klausel ein, die als Ziel der UPDATE-Anweisung die Zeile angibt, deren Wert `CustomerID = 'c400'` lautet. Durch diesen Teil der SELECT-Anweisung wird die Zielzeile von allen anderen Zeilen unterschieden, da die `CustomerID` der Primärschlüssel der Zieltabelle ist. Die Informationen für die ursprüngliche Version des Datensatzes die WHERE-Klausel abgeleitet wird (`DataRowVersion.Original`), für den Fall, dass die Werte, die erforderlich sind, um die Zeile identifizieren geändert haben.  
  
- Die übertragene SQL-Anweisung umfasst eine SET-Klausel, mit der der neue Wert geänderter Spalten festgelegt wird.  
  
    > [!NOTE]
    >  Wenn die `UpdateCommand`-Eigenschaft des TableAdapter auf den Namen einer gespeicherten Prozedur festgelegt wurde, erstellt der Adapter keine SQL-Anweisung. Stattdessen wird die gespeicherte Prozedur mit den entsprechenden übergebenen Parametern aufgerufen.  
  
## <a name="passing-parameters"></a>Übergeben von Parametern  
 In der Regel verwenden Sie Parameter, um die Werte für Datensätze zu übergeben, die in der Datenbank aktualisiert werden sollen.  Wenn der TableAdapters `Update` Methode ausgeführt wird, eine UPDATE-Anweisung, die Parameterwerte ausgefüllt werden muss. Die benötigten Werte werden aus der `Parameters`-Auflistung des jeweiligen Datenbefehls abgerufen, in diesem Fall ist dies das `UpdateCommand`-Objekt im TableAdapter.  
  
 Wenn Sie Visual Studio-Tools verwendet haben, um einen Datenadapter zu generieren. die `UpdateCommand` Objekt enthält eine Auflistung von Parametern, die dem jeweiligen Parameterplatzhalter in der Anweisung entsprechen.  
  
 Die <xref:System.Data.SqlClient.SqlParameter.SourceColumn%2A?displayProperty=fullName>-Eigenschaft der einzelnen Parameter zeigt auf eine Spalte in der Datentabelle. Beispiel: Die `SourceColumn`-Eigenschaft für den `au_id`-Parameter und den `Original_au_id`-Parameter wird auf die Spalte in der Datentabelle festgelegt, die die Autor-ID enthält. Wenn des Adapters die `Update` Methode ausgeführt wird, liest der Autor-Id-Spalte, aus dem Datensatz, der aktualisiert wird und die Werte in die Anweisung eingetragen.  
  
 In einer UPDATE-Anweisung müssen Sie sowohl die neuen Werte (diejenigen, die der Datensatz geschrieben wird) als auch die alten Werte (so, dass der Datensatz in der Datenbank gefunden werden kann) angeben. Daher verfügt jeder Wert über zwei Parameter: einen für die SET-Klausel und einen anderen für die WHERE-Klausel. Beide Parameter lesen Daten aus dem Datensatz, der aktualisiert wird. allerdings erhalten sie verschiedene Versionen des Spaltenwerts auf Grundlage des Parameters des [SqlParameter.SourceVersion-Eigenschaft](https://msdn.microsoft.com/library/system.data.sqlclient.sqlparameter.sourceversion.aspx). Für den Parameter der SET-Klausel wird die aktuelle Version und für den Parameter der WHERE-Klausel die ursprüngliche Version abgerufen.  
  
> [!NOTE]
>  Sie können auch selbst Werte für die `Parameters`-Auflistung im Code festlegen. Dies erfolgt in der Regel in einem Ereignishandler für das <xref:System.Data.DataTable.RowChanging>-Ereignis des Datenadapters.  
  
## <a name="see-also"></a>Siehe auch  
 [Aktualisieren von Daten mit einem TableAdapter](../data-tools/update-data-by-using-a-tableadapter.md)   
 [Vorbereiten der Anwendung auf den Empfang von Daten](http://msdn.microsoft.com/library/c17bdb7e-c234-4f2f-9582-5e55c27356ad)   
 [Binden von Steuerelementen an Daten in Visual Studio](../data-tools/bind-controls-to-data-in-visual-studio.md)   
 [Überprüfen von Daten](http://msdn.microsoft.com/library/b3a9ee4e-5d4d-4411-9c56-c811f2b4ee7e)   
