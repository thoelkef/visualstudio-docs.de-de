---
title: Rückspeichern von Daten in der Datenbank
ms.date: 11/04/2016
ms.topic: conceptual
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
author: gewarren
ms.author: gewarren
manager: douge
ms.prod: visual-studio-dev15
ms.technology: vs-data-tools
ms.workload:
- data-storage
ms.openlocfilehash: 3ef60be5002c5d99f8947bfa770665fa3535a20e
ms.sourcegitcommit: 0aafcfa08ef74f162af2e5079be77061d7885cac
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 06/01/2018
ms.locfileid: "34691133"
---
# <a name="save-data-back-to-the-database"></a>Rückspeichern von Daten in der Datenbank
Das Dataset ist ein in-Memory-Kopie der Daten. Wenn Sie diese Daten ändern, ist es empfiehlt sich, diese Änderungen in der Datenbank zu speichern. Sie dazu auf eine der drei Arten:

-   Durch einen Aufruf der Update-Methoden eines TableAdapters

-   Durch eine der DBDirect-Methoden des TableAdapter aufrufen

-   Durch Aufrufen der UpdateAll-Methode auf TableAdapterManager, die Visual Studio für Sie generiert, wenn Sie das Dataset Tabellen enthält, die auf andere Tabellen im Dataset verknüpft sind

Wenn Sie Daten an Steuerelemente in einem Windows Form oder Verwendung von XAML-Seite Dataset-Tabellen binden, übernimmt die Datenbindungsarchitektur die gesamte Arbeit für Sie.

Wenn Sie mit TableAdapters vertraut sind, können Sie direkt auf einen der folgenden Themen wechseln:

|Thema|Beschreibung|
|-----------|-----------------|
|[Gewusst wie: Einfügen neuer Datensätze in eine Datenbank](../data-tools/insert-new-records-into-a-database.md)|Gewusst wie: Ausführen aktualisiert und fügt mithilfe von TableAdapters oder Befehl Objekte|
|[Gewusst wie: Aktualisieren von Daten mit einem TableAdapter](../data-tools/update-data-by-using-a-tableadapter.md)|Gewusst wie: Ausführen von Updates mit TableAdapters|
|[Hierarchische Aktualisierung](../data-tools/hierarchical-update.md)|Gewusst wie: Ausführen von Updates aus einem Dataset mit zwei oder mehr verknüpfte Tabellen|
|[Behandeln einer Parallelitätsausnahme](../data-tools/handle-a-concurrency-exception.md)|Gewusst wie: Behandeln von Ausnahmen, wenn zwei Benutzer versuchen, dieselben Daten in einer Datenbank zur gleichen Zeit zu ändern.|
|[Vorgehensweise: Speichern von Daten mithilfe von Transaktionen](../data-tools/save-data-by-using-a-transaction.md)|Gewusst wie: Speichern von Daten in einer Transaktion, die mithilfe von System.Transactions-Namespace und ein Objekt von "TransactionScope"|
|[Exemplarische Vorgehensweise: Speichern von Daten im Rahmen einer Transaktion](../data-tools/save-data-in-a-transaction.md)|Exemplarische Vorgehensweise, die eine Windows Forms-Anwendung zum Speichern von Daten in einer Datenbank innerhalb einer Transaktion veranschaulichen erstellt|
|[Speichern von Daten in einer Datenbank (mehrere Tabellen)](../data-tools/save-data-to-a-database-multiple-tables.md)|Zum Bearbeiten von Datensätzen und Speichern von Änderungen in mehreren Tabellen in der Datenbank|
|[Gewusst wie: Speichern von Daten aus einem Objekt in einer Datenbank](../data-tools/save-data-from-an-object-to-a-database.md)|Wie Daten aus einem Objekt zu übergeben, die nicht in ein Dataset mit einer Datenbank mithilfe einer TableAdapter-DbDirect-Methode|
|[Speichern von Daten mit den TableAdapter-DBDirect-Methoden](../data-tools/save-data-with-the-tableadapter-dbdirect-methods.md)|Gewusst wie: Verwenden der TableAdapter SQL-Abfragen direkt an die Datenbank zu senden|
|[Speichern eines Datasets als XML](../data-tools/save-a-dataset-as-xml.md)|Wie Sie ein Dataset in ein XML-Dokument zu speichern.|

## <a name="two-stage-updates"></a>Zweistufige Aktualisierungen
 Aktualisieren einer Datenquelle ist ein zweistufiger Prozess. Der erste Schritt besteht darin das Dataset mit neuen Datensätze, geänderten Datensätze oder gelöschte Datensätze zu aktualisieren. Wenn Ihre Anwendung diese Änderungen nie wieder an die Datenquelle sendet, werden Sie mit dem Update nicht mehr benötigen.

 Wenn Sie die Änderungen zurück an die Datenbank senden, ist ein zweiter Schritt erforderlich. Wenn Sie datengebundene Steuerelemente verwenden, müssen Sie manuell die TableAdapter (oder Datenadapters) die Update-Methode aufzurufen, mit denen Sie das Dataset zu füllen. Allerdings können Sie verschiedene Adaptern, z. B. auch zum Verschieben von Daten aus einer Datenquelle in eine andere oder zum Aktualisieren mehrerer Datenquellen verwenden. Wenn Sie sind nicht mit der Datenbindung und Änderungen für verknüpfte Tabellen speichern, müssen Sie manuell eine Variable, der automatisch generierten TableAdapterManager-Klasse instanziieren, und rufen Sie ihre UdpateAll-Methode.

 ![Visual Basic-Dataset-Aktualisierungen](../data-tools/media/vbdatasetupdates.gif "VbDatasetUpdates") einem zweistufigen Prozess und die Rolle des "DataRowVersion" in einer erfolgreichen Aktualisierung zu aktualisieren

 Ein Dataset enthält Auflistungen von Tabellen, die eine Sammlung von Zeilen enthalten. Wenn Sie beabsichtigen, eine zugrunde liegende Datenquelle später aktualisieren, müssen Sie die Methoden für die Eigenschaft DataTable.DataRowCollection beim Hinzufügen oder Entfernen von Zeilen verwenden. Diese Methoden führen Sie das Nachverfolgen von Änderungen, das zum Aktualisieren der Datenquelle erforderlich ist. Wenn Sie auf der Rows-Eigenschaft die Auflistung RemoveAt aufrufen, wird nicht die Löschung an die Datenbank übermittelt werden.

## <a name="merge-datasets"></a>Zusammenführen von datasets
 Sie können den Inhalt eines Datasets aktualisieren *zusammenführen* mit einem anderen Dataset. Dies umfasst das Kopieren der Inhalte einer *Quelle* Dataset in das aufrufende Dataset (als bezeichnet den *Ziel* Dataset). Beim Zusammenführen von Datasets werden neue Datensätze aus dem Quell-Dataset in das Ziel-Dataset eingefügt. Darüber hinaus werden dem Ziel-Dataset zusätzliche Spalten aus dem Quell-Dataset hinzugefügt. Zusammenführen von Datasets ist nützlich, wenn ein lokales Dataset vorhanden ist und Sie ein zweites Dataset aus einer anderen Anwendung erhalten. Es ist auch nützlich, wenn Sie ein zweites Dataset aus einer Komponente, wie z. B. einen XML-Webdienst abrufen, oder wenn Sie Daten aus mehreren Datasets integrieren müssen.

 Beim Zusammenführen von Datasets können Sie übergeben ein boolesches Argument (`preserveChanges`), informiert der <xref:System.Data.DataSet.Merge%2A> Methode angibt, ob bestehende Änderungen im Ziel-Dataset beibehalten werden sollen. Da Datasets mehrere Datensatzversionen verwalten, ist es wichtig zu bedenken, dass mehrere Versionen der Datensätze zusammengeführt werden. Die folgende Tabelle zeigt, wie Datensätze aus zwei Datasets zusammengeführt werden:

|DataRowVersion|Ziel-Dataset|Quell-Dataset|
|--------------------|--------------------|--------------------|
|Ursprünglich|James Wilson|James C. Wilson|
|Aktuell|Jim Wilson|James C. Wilson|

 Aufrufen der <xref:System.Data.DataSet.Merge%2A> Methode in der obigen Tabelle mit `preserveChanges=false targetDataset.Merge(sourceDataset)` Folgendes:

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
>  In der `preserveChanges = true` Szenario, wenn die <xref:System.Data.DataSet.RejectChanges%2A> Methode für einen Datensatz im Ziel-Dataset aufgerufen wird, und es wird auf die ursprünglichen Daten zurückgesetzt der *Quelle* Dataset. Dies bedeutet, wenn Sie versuchen, die ursprüngliche Datenquelle mit dem Ziel-Dataset zu aktualisieren, es finden, die ursprüngliche zu aktualisierende Zeile u. u. nicht. Sie können eine parallelitätsverletzung vermeiden, indem ein anderes Dataset mit Daten aus der Datenquelle den aktualisierten Datensätzen Auffüllen und anschließend eine Zusammenführung, um zu verhindern, dass eine parallelitätsverletzung ausführen. (Eine Parallelitätsverletzung liegt vor, wenn ein anderer Benutzer einen Datensatz in der Datenquelle ändert, nachdem das Dataset aufgefüllt wurde.)

## <a name="update-constraints"></a>Einschränkungen bei der Aktualisierung
 Um Änderungen an einer vorhandenen Datenzeile vorzunehmen, hinzufügen oder Aktualisieren von Daten in einzelnen Spalten. Wenn das Dataset Einschränkungen (z. B. Fremdschlüsseln oder NULL-Einschränkungen) enthält, ist es möglich, dass der Datensatz vorübergehend im Status "Fehler" sein kann, wie Sie es aktualisieren. D. h., kann es im Status "Fehler" sein, nachdem Sie eine Spalte aktualisiert, aber bevor Sie mit dem nächsten abrufen.

 Um vorzeitige Verletzungen dieser Einschränkungen zu vermeiden, können Sie sie vorübergehend außer Kraft setzen. Bei diesem Verfahren werden zwei Ziele verfolgt:

-   Es wird verhindert, dass einen Fehler ausgelöst wird, nach dem Update einer Spalte wurde jedoch noch nicht gestartet wurde, aktualisieren eine andere.

-   Es wird verhindert, dass bestimmte Update ausgelöst (Ereignisse, die häufig für Validierungen verwendete).

> [!NOTE]
>  In Windows Forms, hält die, die in das Datenraster integrierte Datenbindungsarchitektur einschränkungsüberprüfung bis Fokus außerhalb einer Zeile, und Sie nicht explizit aufrufen müssen, die <xref:System.Data.DataRow.BeginEdit%2A>, <xref:System.Data.DataRow.EndEdit%2A>, oder <xref:System.Data.DataRow.CancelEdit%2A> Methoden.

 Beim Aufruf der <xref:System.Data.DataSet.Merge%2A>-Methode für ein Dataset werden Einschränkungen automatisch deaktiviert. Wenn die Zusammenführung abgeschlossen ist, wenn es Einschränkungen für das Dataset, das aktiviert werden kann gibt, wird eine <xref:System.Data.ConstraintException> ausgelöst wird. In einer solchen Situation ist die <xref:System.Data.DataSet.EnforceConstraints%2A>-Eigenschaft auf `false,` festgelegt, und alle Einschränkungsverletzungen müssen vor dem Zurücksetzen der <xref:System.Data.DataSet.EnforceConstraints%2A>-Eigenschaft auf `true` aufgelöst werden.

 Nachdem Sie ein Update abgeschlossen haben, können Sie erneut aktivieren einschränkungsüberprüfung, wodurch auch Aktualisierungsereignisse wieder aktiviert und ausgelöst werden.

 Weitere Informationen zum Aufheben von Ereignissen finden Sie unter [Deaktivieren von Einschränkungen beim Auffüllen von Datasets](../data-tools/turn-off-constraints-while-filling-a-dataset.md).

## <a name="dataset-update-errors"></a>DataSet-Aktualisierungsfehler
 Bei der Aktualisierung von Datensätzen in einen Dataset können Fehler auftreten. Sie können z. B. versehentlich schreiben, Daten des falschen Typs an eine Spalte oder Daten, die zu lang sind oder Daten, die ein anderes Integritätsproblem verursacht hat. Oder Sie verfügen möglicherweise über anwendungsspezifische Überprüfungen, die jeder Phase eines Aktualisierungsereignisses benutzerdefinierte Fehler auslösen können. Weitere Informationen finden Sie unter [Validieren von Daten in Datasets](../data-tools/validate-data-in-datasets.md).

## <a name="maintaining-information-about-changes"></a>Verwalten von Informationen über Änderungen
 Informationen zu den Änderungen in einem Dataset ist auf zweifache Weise verwaltet: durch das Kennzeichnen von Zeilen, die darauf hinweisen, dass sie geändert wurden (<xref:System.Data.DataRow.RowState%2A>), und durch die Speicherung mehrerer Kopien eines Datensatzes (<xref:System.Data.DataRowVersion>). Mithilfe dieser Informationen können die geänderten Daten im Dataset vom Prozess ermittelt und die entsprechenden Aktualisierungen an die Datenquelle gesendet werden.

### <a name="rowstate-property"></a>RowState-Eigenschaft
 Die <xref:System.Data.DataRow.RowState%2A>-Eigenschaft eines <xref:System.Data.DataRow>-Objekts stellt einen Wert dar, der Informationen zum Status einer bestimmten Datenzeile bereitstellt.

 In der folgenden Tabelle sind die möglichen Werte für die <xref:System.Data.DataRowState>-Enumeration aufgeführt:

|DataRowState-Wert|Beschreibung|
|------------------------|-----------------|
|<xref:System.Data.DataRowState.Added>|Die Zeile wurde einer <xref:System.Data.DataRowCollection> als Element hinzugefügt. (Eine Zeile in diesem Status keine entsprechende ursprüngliche Version, da sie nicht vorhanden war bei der letzten <xref:System.Data.DataRow.AcceptChanges%2A> Methode wurde aufgerufen).|
|<xref:System.Data.DataRowState.Deleted>|Die Zeile wurde mit <xref:System.Data.DataRow.Delete%2A> eines <xref:System.Data.DataRow>-Objekts gelöscht.|
|<xref:System.Data.DataRowState.Detached>|Die Zeile wurde zwar erstellt, gehört aber keiner <xref:System.Data.DataRowCollection> an. Ein <xref:System.Data.DataRow> Objekt ist in diesem Zustand, unmittelbar nachdem es erstellt wurde, bevor sie einer Sammlung hinzugefügt wurde, und nachdem es aus einer Auflistung entfernt wurde.|
|<xref:System.Data.DataRowState.Modified>|Ein Spaltenwert in der Zeile wurde in irgendeiner Form geändert.|
|<xref:System.Data.DataRowState.Unchanged>|Die Zeile wurde seit dem letzten Aufruf von <xref:System.Data.DataRow.AcceptChanges%2A> nicht geändert.|

### <a name="datarowversion-enumeration"></a>DataRowVersion-Enumeration
In Datasets werden mehrere Datensatzversionen verwaltet. Die <xref:System.Data.DataRowVersion> Felder können verwendet werden, wenn das Abrufen des Werts im gefunden eine <xref:System.Data.DataRow> mithilfe der <xref:System.Data.DataRow.Item%2A> Eigenschaft oder die <xref:System.Data.DataRow.GetChildRows%2A> Methode der <xref:System.Data.DataRow> Objekt.

In der folgenden Tabelle sind die möglichen Werte für die <xref:System.Data.DataRowVersion>-Enumeration aufgeführt:

|DataRowVersion-Wert|Beschreibung|
|--------------------------|-----------------|
|<xref:System.Data.DataRowVersion.Current>|Die aktuelle Version eines Datensatzes enthält alle Änderungen, die für den Datensatz, seit der letzten Ausführung ausgeführt wurden <xref:System.Data.DataRow.AcceptChanges%2A> aufgerufen wurde. Wenn die Zeile gelöscht wurde, sollten Sie die keine aktuelle Version vorhanden ist.|
|<xref:System.Data.DataRowVersion.Default>|Der Standardwert eines Datensatzes, wie er durch das Dataset-Schema oder die Datenquelle definiert wurde.|
|<xref:System.Data.DataRowVersion.Original>|Die ursprüngliche Version eines Datensatzes ist eine Kopie des Datensatzes zu dem Zeitpunkt, zu dem zuletzt ein Commit für Dataset-Änderungen ausgeführt wurde. Praktisch entspricht dies meist der Version eines Datensatzes, die aus einer Datenquelle gelesen wurde.|
|<xref:System.Data.DataRowVersion.Proposed>|Die vorläufige Version eines Datensatzes, der vorübergehend, während Sie in der Mitte eines Updates sind verfügbar ist – d. h. zwischen dem Zeitpunkt aufgerufen der <xref:System.Data.DataRow.BeginEdit%2A> Methode und die <xref:System.Data.DataRow.EndEdit%2A> Methode. Auf die vorläufige Version eines Datensatzes greifen Sie i. d. R. in einem Ereignishandler zu, z. B. <xref:System.Data.DataTable.RowChanging>. Durch den Aufruf der <xref:System.Data.DataRow.CancelEdit%2A>-Methode werden die Änderungen rückgängig gemacht und die vorläufige Version aus der Datenzeile gelöscht.|

 Die ursprüngliche und die aktuelle Version sind hilfreich, wenn Aktualisierungsinformationen an eine Datenquelle übertragen werden. Wenn eine Aktualisierung an die Datenquelle gesendet wird, befinden sich die neuen Informationen für die Datenbank i. d. R. in der aktuellen Version des Datensatzes. Anhand von Informationen aus der ursprünglichen Version wird der zu aktualisierende Datensatz gesucht.

 In einem Fall, in denen der Primärschlüssel eines Datensatzes geändert wird, benötigen Sie z. B. eine Möglichkeit, den richtigen Datensatz in der Datenquelle zu finden, um die Änderungen zu aktualisieren. Wenn keine ursprüngliche Version vorhanden ist, wird der Datensatz höchstwahrscheinlich an die Datenquelle angefügt. Daraus resultiert dann nicht nur ein ungewollter zusätzlicher, sondern auch ungenauer und nicht mehr aktueller Datensatz. Die beiden Versionen werden auch in der parallelitätssteuerung verwendet. Sie können die ursprüngliche Version mit einem Datensatz in der Datenquelle, um festzustellen, ob der Datensatz geändert wurde, da es in das Dataset geladen wurde, vergleichen.

 Die vorläufige Version ist von Nutzen, wenn Sie eine Validierung durchführen müssen, bevor die Änderungen am Dataset endgültig bestätigt werden.

 Selbst wenn Datensätze geändert wurden, ist nicht immer eine ursprüngliche oder aktuelle Version der betreffenden Zeile verfügbar. Wenn Sie eine neue Zeile in die Tabelle einfügen, existiert keine ursprüngliche, sondern nur eine aktuelle Version. Auch wenn Sie eine Zeile durch den Aufruf der tabellenspezifischen `Delete`-Methode löschen, ist eine ursprüngliche, aber keine aktuelle Version vorhanden.

 Durch Abfrage der <xref:System.Data.DataRow.HasVersion%2A>-Methode der Datenzeile können Sie überprüfen, ob eine bestimmte Version eines Datensatzes vorhanden ist. Um auf eine der verschiedenen Datensatzversionen zuzugreifen, übergeben Sie einen <xref:System.Data.DataRowVersion>-Enumerationswert als optionales Argument, wenn Sie den Wert einer Spalte anfordern.

## <a name="getting-changed-records"></a>Beim Abrufen der geänderten Datensätze
 Es ist üblich, dass jeder Datensatz in einem Dataset aktualisiert. Beispielsweise kann ein Benutzer mit einem <xref:System.Windows.Forms.DataGridView>-Steuerelement von Windows Forms arbeiten, durch das zahlreiche Datensätze angezeigt werden. Der Benutzer aktualisiert jedoch vielleicht nur einige wenige Datensätze, löscht einen Datensatz und fügt einen neuen ein. Datasets und Datentabellen bieten eine Methode (`GetChanges`), mit deren Hilfe ausschließlich die geänderten Zeilen zurückgegeben werden können.

 Sie können Teilmengen der geänderten Datensätze erstellen, indem Sie entweder die `GetChanges`-Methode der Datentabelle (<xref:System.Data.DataTable.GetChanges%2A>) oder des Datasets selbst (<xref:System.Data.DataSet.GetChanges%2A>) verwenden. Wenn Sie die Methode für die Datentabelle aufrufen, wird eine Kopie der Tabelle zurückgegeben, die lediglich die geänderten Datensätze enthält. Ähnlich verhält es sich, wenn Sie die Methode für den Dataset aufrufen: Sie erhalten ein neues Dataset, das nur geänderte Datensätze enthält.

 `GetChanges` allein gibt Sie alle geänderten Datensätze zurück. Im Gegensatz dazu, indem Sie die gewünschte übergeben <xref:System.Data.DataRowState> als Parameter an die `GetChanges` -Methode, Sie können angeben, welche Teilmenge der geänderten Datensätze werden sollen: neu hinzugefügte Datensätze, Datensätze, die zum Löschen markiert sind, abgetrennte Datensätze oder geänderte Datensätze.

 Abrufen einer Teilmenge der geänderten Datensätze eignet sich Datensätze an eine andere Komponente für die Verarbeitung zu senden. Anstatt das gesamte Dataset zu übertragen, können Sie die Kommunikation mit der anderen Komponente gering halten, indem Sie lediglich die Datensätze abrufen, die von der Komponente benötigt werden.

## <a name="committing-changes-in-the-dataset"></a>Ausführen eines Commits für Änderungen in einem dataset
 Während Sie Änderungen im Dataset vornehmen, wird die <xref:System.Data.DataRow.RowState%2A>-Eigenschaft der geänderten Zeilen festgelegt. Die ursprünglichen und aktuellen Versionen von Datensätzen eingerichtet, verwaltet und zur Verfügung gestellt, um Sie von der <xref:System.Data.DataRowView.RowVersion%2A> Eigenschaft. Die Metadaten, die in den Eigenschaften dieser geänderten Zeilen gespeichert ist ist erforderlich für die richtigen Updates an die Datenquelle gesendet.

 Wenn die Änderungen den aktuellen Zustand der Datenquelle widerspiegeln, müssen diese Informationen nicht länger beibehalten werden. In der Regel, es gibt zwei Situationen, wenn das Dataset und seine Quelle synchron sind:

-   Unmittelbar nach dem Laden von Informationen in das Dataset, z. B., wenn Sie Daten aus der Quelle einlesen.

-   Nach dem Senden von Änderungen aus dem Dataset mit der Datenquelle (jedoch nicht vorher, da die Änderungsinformationen ansonsten verloren gehen würden, die zum Senden von Änderungen an der Datenbank erforderlich ist).

Sie können für die ausstehenden Änderungen im Dataset ein Commit ausführen, indem Sie die <xref:System.Data.DataSet.AcceptChanges%2A>-Methode aufrufen. In der Regel <xref:System.Data.DataSet.AcceptChanges%2A> zu folgenden Zeiten aufgerufen wird:

-   Nach dem Laden Sie des Datasets. Wenn Sie ein Dataset laden, indem Sie die `Fill`-Methode eines TableAdapter aufrufen, führt der Adapter automatisch ein Commit für die Änderungen aus. Wenn ein Dataset jedoch geladen wird, indem Sie ein anderes Dataset mit ihm zusammenführen, müssen Sie den Commit für die Änderungen manuell ausführen.

    > [!NOTE]
    >  Sie können verhindern, dass der Adapter automatisch die Änderungen festgeschrieben, beim Aufrufen der `Fill` Methode durch Festlegen der `AcceptChangesDuringFill` Eigenschaft des Adapters auf `false`. Wenn sie, um festgelegt ist `false`, die <xref:System.Data.DataRow.RowState%2A> der jede Zeile, die während des Auffüllens eingefügten festgelegt ist <xref:System.Data.DataRowState.Added>.

-   Nachdem Datasetänderungen an einen anderen Prozess, z. B. ein XML-Webdienst gesendet wird.

    > [!CAUTION]
    >  Wenn ein Commit für Änderungen auf diese Weise ausgeführt wird, werden sämtliche Änderungsinformationen gelöscht. Keine Änderungen erst nach dem führen Sie Ausführen von Vorgängen, die erfordern die Anwendung zu wissen, welche Änderungen im Dataset vorgenommen wurden abgeschlossen.

Diese Methode umfasst folgende Schritte:

-   Schreibt die <xref:System.Data.DataRowVersion.Current> Version eines Datensatzes in die <xref:System.Data.DataRowVersion.Original> Version und die ursprüngliche Version überschrieben werden.

-   Entfernt jede Zeile, in dem die <xref:System.Data.DataRow.RowState%2A> -Eigenschaftensatz auf <xref:System.Data.DataRowState.Deleted>.

-   Legt die <xref:System.Data.DataRow.RowState%2A>-Eigenschaft eines Datensatzes auf <xref:System.Data.DataRowState.Unchanged> fest.

Die <xref:System.Data.DataSet.AcceptChanges%2A>-Methode ist auf drei Ebenen verfügbar. Sie können auf Aufrufen einer <xref:System.Data.DataRow> Objekt mit Commits ändert nur diese Zeile. Sie können es auch aufrufen, auf ein <xref:System.Data.DataTable> Objekt, um alle Zeilen in einer Tabelle zu übernehmen. Schließlich können Sie es auf Aufrufen der <xref:System.Data.DataSet> Objekt, um alle ausstehenden Änderungen in sämtlichen Datensätzen aller Tabellen des Datasets zu übernehmen.

In der folgenden Tabelle wird basierend auf dem Objekt, für das die Methode aufgerufen wird, beschrieben, für welche Änderungen ein Commit ausgeführt wird.

|Methode|Ergebnis|
|------------|------------|
|<xref:System.Data.DataRow.AcceptChanges%2A?displayProperty=fullName>|Änderungen werden nur auf die Zeile ein Commit ausgeführt.|
|<xref:System.Data.DataTable.AcceptChanges%2A?displayProperty=fullName>|Änderungen werden auf alle Zeilen der spezifischen Tabelle ein Commit ausgeführt.|
|<xref:System.Data.DataSet.AcceptChanges%2A?displayProperty=fullName>|Änderungen werden in allen Zeilen der Datasettabellen ein Commit ausgeführt.|

> [!NOTE]
>  Wenn Sie ein Dataset laden, indem Sie eines TableAdapter aufrufen `Fill` -Methode, müssen Sie nicht explizit Änderungen zu übernehmen. Wird standardmäßig die `Fill` Methodenaufrufe der `AcceptChanges` Methode nach der Fertigstellung der Datentabelle mit Daten aufgefüllt.

 Eine verwandte Methode <xref:System.Data.DataSet.RejectChanges%2A>, macht die Auswirkungen der Änderungen durch Kopieren der <xref:System.Data.DataRowVersion.Original> Version wieder in die <xref:System.Data.DataRowVersion.Current> Version von Datensätzen. Außerdem wird die <xref:System.Data.DataRow.RowState%2A> des jeder Datensatz wieder an <xref:System.Data.DataRowState.Unchanged>.

## <a name="data-validation"></a>Überprüfen von Daten
 Um sicherzustellen, dass die in der Anwendung enthaltenen Daten die Anforderungen des Prozesses erfüllen, an den sie übergeben werden, sind oftmals Validierungen erforderlich. Dies kann das stellt sicher, dass Benutzereingaben in einem Formular richtig ist, Überprüfen von Daten, die von einer anderen Anwendung an die Anwendung gesendet wird, oder auch überprüfen, dass die innerhalb der Komponente berechneten Informationen die Einschränkungen der Datenquelle liegt umfassen und anwendungsanforderungen.

 Daten können auf verschiedene Weisen überprüft werden:

-   In der Geschäftsschicht, indem der Anwendung Code für Datenüberprüfungen hinzugefügt wird. Dieses Vorgehen ist nur im Dataset möglich. Das Dataset bietet einige Vorteile der Back-End-Validierung, z. B. die Möglichkeit, Änderungen an Spalten- und Zeilenwerten zu überprüfen. Weitere Informationen finden Sie unter [Validieren von Daten in Datasets](../data-tools/validate-data-in-datasets.md).

-   In der Präsentationsschicht, indem Formularen Validierungen hinzugefügt werden. Weitere Informationen finden Sie unter [User Input Validation in Windows Forms](/dotnet/framework/winforms/user-input-validation-in-windows-forms).

-   Im Back-End der Datenschicht. Daten werden an die Datenquelle, z. B. die Datenbank, gesendet, und die Datenbank kann diese Daten annehmen oder ablehnen. Bei Verwendung einer Datenbank, die hochentwickelte Datenüberprüfungsmechanismen besitzt und Fehlerinformationen bereitstellt, ist dieser Ansatz durchaus überlegenswert, da Daten unabhängig von ihrer Herkunft überprüft werden können. Dieser Ansatz kann jedoch nicht berücksichtigen anwendungsspezifische überprüfungsanforderungen zu erfüllen. Darüber hinaus kann die Datenquelle aus, überprüfen Sie die Daten führen, dass zahlreiche wiederholte Zugriffe auf die Datenquelle, je nachdem, wie die Auflösung der vom Back-End ausgelösten Validierungsfehler von der Anwendung behandelt.

    > [!IMPORTANT]
    >  Wenn Sie Datenbefehle mit einer <xref:System.Data.SqlClient.SqlCommand.CommandType%2A> Eigenschaft, um festgelegt wird <xref:System.Data.CommandType.Text>, sorgfältig prüfen von Informationen, die von einem Client gesendet wird, vor der Übergabe an die Datenbank. Böswillige Benutzer könnten versuchen, veränderte oder zusätzliche SQL-Anweisungen zu senden (einzufügen), um unautorisierten Zugriff zu erhalten oder die Datenbank zu beschädigen. Bevor Sie Benutzereingaben an eine Datenbank übertragen, immer Stellen Sie sicher, dass die Informationen gültig sind. Es wird empfohlen, parametrisierte Abfragen oder gespeicherte Prozeduren, die nach Möglichkeit immer zu verwenden.

## <a name="transmitting-updates-to-the-data-source"></a>Senden von Updates mit der Datenquelle
Nachdem ein Dataset geändert wurde, können Sie die Änderungen an eine Datenquelle übertragen. In den meisten Fällen rufen Sie dazu die `Update`-Methode eines TableAdapter (oder Datenadapters) auf. Die Methode führt einen Schleifendurchlauf durch jeden Datensatz in einer Datentabelle bestimmt, welche Art von Update erforderlich ist (aktualisieren, einfügen oder löschen), sofern vorhanden, und führt dann den entsprechenden Befehl.

 Als eine Abbildung wie Aktualisierungen durchgeführt werden nehmen Sie an, dass Ihre Anwendung ein Dataset verwendet, die eine einzelnen Tabelle enthält. Die Anwendung ruft zwei Zeilen aus der Datenbank ab. Nach dem Abruf sieht die Datentabelle im Arbeitsspeicher wie folgt aus:

```sql
(RowState)     CustomerID   Name             Status
(Unchanged)    c200         Robert Lyon      Good
(Unchanged)    c400         Nancy Buchanan    Pending
```

 Die Anwendung ändert Nancy Buchanans Status in "Preferred". Durch diese Änderung wird der Wert der <xref:System.Data.DataRow.RowState%2A>-Eigenschaft von <xref:System.Data.DataRowState.Unchanged> in <xref:System.Data.DataRowState.Modified> geändert. Der Wert der <xref:System.Data.DataRow.RowState%2A>-Eigenschaft für die erste Zeile behält den Wert <xref:System.Data.DataRowState.Unchanged> bei. Die Datentabelle sieht nun wie folgt aus:

```sql
(RowState)     CustomerID   Name             Status
(Unchanged)    c200         Robert Lyon      Good
(Modified)     c400         Nancy Buchanan    Preferred
```

 Anschließend ruft die Anwendung die `Update`-Methode auf, um das Dataset an die Datenbank zu übertragen. Durch die Methode werden wieder die einzelnen Zeilen untersucht. Für die erste Zeile überträgt die Methode keine SQL-Anweisung mit der Datenbank, da diese Zeile seit dem ursprünglichen, aus der Datenbank Abruf wurde nicht geändert.

 Für die zweite Zeile der `Update` Methode automatisch die richtigen Daten-Befehl ruft auf und überträgt ihn an die Datenbank. Die spezifische Syntax der SQL-Anweisung hängt von der Dialekt von SQL Server, die vom zugrunde liegenden Datenspeicher unterstützt wird. Die folgenden allgemeinen Merkmale der übertragenen SQL-Anweisung sollten jedoch beachtet werden:

-   Die übertragene SQL-Anweisung ist eine UPDATE-Anweisung. Da der Wert der <xref:System.Data.DataRow.RowState%2A>-Eigenschaft <xref:System.Data.DataRowState.Modified> ist, ist es für Adapter offensichtlich, dass sie eine UPDATE-Anweisung verwenden müssen.

-   Die übertragene SQL-Anweisung enthält eine WHERE-Klausel gibt an, dass das Ziel der UPDATE-Anweisung der Zeile ist, in dem `CustomerID = 'c400'`. Durch diesen Teil der SELECT-Anweisung wird die Zielzeile von allen anderen Zeilen unterschieden, da die `CustomerID` der Primärschlüssel der Zieltabelle ist. Die Informationen für die ursprüngliche Version des Datensatzes die WHERE-Klausel abgeleitet ist (`DataRowVersion.Original`), für den Fall, dass die Werte, die erforderlich sind, zur Identifikation der Zeile geändert haben.

-   Die übertragene SQL-Anweisung umfasst eine SET-Klausel, mit der der neue Wert geänderter Spalten festgelegt wird.

    > [!NOTE]
    > Wenn die `UpdateCommand`-Eigenschaft des TableAdapter auf den Namen einer gespeicherten Prozedur festgelegt wurde, erstellt der Adapter keine SQL-Anweisung. Stattdessen wird die gespeicherte Prozedur mit den entsprechenden übergebenen Parametern aufgerufen.

## <a name="passing-parameters"></a>Übergeben von Parametern
 Sie verwenden in der Regel Parameter, um die Übergabe der Werte für Datensätze, die in der Datenbank aktualisiert werden soll.  Wenn der TableAdapter `Update` Methode führt eine UPDATE-Anweisung, die Parameterwerte ausgefüllt werden muss. Die benötigten Werte werden aus der `Parameters`-Auflistung des jeweiligen Datenbefehls abgerufen, in diesem Fall ist dies das `UpdateCommand`-Objekt im TableAdapter.

 Wenn Sie Visual Studio-Tools verwendet haben, um einen Datenadapter generieren die `UpdateCommand` Objekt enthält eine Auflistung von Parametern, die dem jeweiligen Parameterplatzhalter in der Anweisung entsprechen.

 Die <xref:System.Data.SqlClient.SqlParameter.SourceColumn%2A?displayProperty=fullName>-Eigenschaft der einzelnen Parameter zeigt auf eine Spalte in der Datentabelle. Beispiel: Die `SourceColumn`-Eigenschaft für den `au_id`-Parameter und den `Original_au_id`-Parameter wird auf die Spalte in der Datentabelle festgelegt, die die Autor-ID enthält. Wenn des Adapters `Update` Methode ausgeführt wird, liest der Autor-ID-Spalte, aus dem Datensatz, der aktualisiert wird und die Werte in die Anweisung eingetragen.

 In einer UPDATE-Anweisung müssen Sie sowohl die neuen Werte (diejenigen, die der Datensatz geschrieben wird) als auch die alten Werte (so, dass der Datensatz in der Datenbank gefunden werden kann) angeben. Daher verfügt jeder Wert über zwei Parameter: einen für die SET-Klausel und einen anderen für die WHERE-Klausel. Beide Parameter Lesen von Daten aus dem Datensatz, der aktualisiert wird, aber erhalten sie unterschiedliche Versionen des Spaltenwerts auf Grundlage des Parameters <xref:System.Data.SqlClient.SqlParameter.SourceVersion> Eigenschaft. Für den Parameter der SET-Klausel wird die aktuelle Version und für den Parameter der WHERE-Klausel die ursprüngliche Version abgerufen.

> [!NOTE]
> Sie können auch selbst Werte für die `Parameters`-Auflistung im Code festlegen. Dies erfolgt in der Regel in einem Ereignishandler für das <xref:System.Data.DataTable.RowChanging>-Ereignis des Datenadapters.

## <a name="see-also"></a>Siehe auch

- [Datasettools in Visual Studio](../data-tools/dataset-tools-in-visual-studio.md)
- [Erstellen und Konfigurieren von TableAdapters](create-and-configure-tableadapters.md)
- [Gewusst wie: Aktualisieren von Daten mit einem TableAdapter](../data-tools/update-data-by-using-a-tableadapter.md)
- [Binden von Steuerelementen an Daten in Visual Studio](../data-tools/bind-controls-to-data-in-visual-studio.md)
- [Überprüfen von Daten](validate-data-in-datasets.md)
- [Speichern von Daten](../data-tools/saving-data.md)