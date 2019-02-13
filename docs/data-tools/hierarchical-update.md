---
title: Hierarchisches Update
ms.date: 11/04/2016
ms.topic: conceptual
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- saving data, changed data
- data [Visual Basic], hierarchical update
- saving updated data
- datasets [Visual Basic], hierarchical update
- hierarchical update
- saving data, hierarchical update
- modified data saving
- updated data saving
- related tables, saving
ms.assetid: 68bae3f6-ec9b-45ee-a33a-69395029f54c
author: gewarren
ms.author: gewarren
manager: jillfra
ms.workload:
- data-storage
ms.openlocfilehash: aaaa9b5f30844e9d23b35ec9304a70edcd2b6139
ms.sourcegitcommit: 21d667104199c2493accec20c2388cf674b195c3
ms.translationtype: MTE95
ms.contentlocale: de-DE
ms.lasthandoff: 02/08/2019
ms.locfileid: "55933249"
---
# <a name="hierarchical-update"></a>Hierarchisches Update

*Hierarchische Aktualisierung* bezieht sich auf das Zurückspeichern der aktualisierten Daten (aus einem Dataset mit zwei oder mehr verknüpfte Tabellen) in einer Datenbank beim Verwalten von Regeln für die referenzielle Integrität. *Referenzielle Integrität* bezieht sich auf die Konsistenzregeln, angegeben durch die Einschränkungen in einer Datenbank, die das Verhalten des einfügen, aktualisieren und Löschen von verknüpften Datensätzen zu steuern. Beispielsweise ist es an der referenziellen Integrität, der die Erstellung eines Kundendatensatzes vor Aufträge erstellt werden für diesen Kunden erzwingt.  Weitere Informationen zu Beziehungen in Datasets, finden Sie unter [Beziehungen in Datasets](../data-tools/relationships-in-datasets.md).

Die hierarchische Aktualisierung-Funktion verwendet einen `TableAdapterManager` zum Verwalten der `TableAdapter`s in einem typisierten Dataset. Die `TableAdapterManager` Komponente ist eine Visual Studio generierten Klasse, sodass es nicht Teil der [!INCLUDE[dnprdnshort](../code-quality/includes/dnprdnshort_md.md)]. Beim Ziehen einer Tabelle aus der **Datenquellen** Fenster mit einer Windows Form oder WPF-Seite, Visual Studio fügt eine Variable vom Typ TableAdapterManager in das Formular oder die Seite, und es im Designer auf der Komponentenleiste angezeigt. Ausführliche Informationen zu den `TableAdapterManager` Klasse, finden Sie im Abschnitt TableAdapterManager-Verweis [TableAdapters](../data-tools/create-and-configure-tableadapters.md).

Standardmäßig behandelt ein Dataset verknüpfte Tabellen als "nur für Beziehungen" Was bedeutet, dass sie keine foreign Key-Einschränkungen erzwingen. Sie können diese Einstellung zur Entwurfszeit ändern, indem Sie mit der **Dataset-Designer**. Wählen Sie die Zeile der Beziehung zwischen zwei Tabellen, um die **Beziehung** Dialogfeld. Bestimmt die Änderungen, die Sie hier vornehmen wie die `TableAdapterManager` verhält, wenn sie senden die Änderungen in den zugehörigen Tabellen in der Datenbank.

## <a name="enable-hierarchical-update-in-a-dataset"></a>Aktivieren der hierarchischen Aktualisierung in einem dataset

Standardmäßig wird die hierarchische Aktualisierung für alle neuen DataSets aktiviert, die in einem Projekt hinzugefügt oder erstellt werden. Aktivieren oder deaktivieren Sie hierarchische Aktualisierung, durch Festlegen der **hierarchische Aktualisierung** Eigenschaft eines typisierten Datasets im Dataset, **"true"** oder **"false"**:

![Hierarchische Aktualisierung festlegen](../data-tools/media/hierarchical-update-setting.png)

## <a name="create-a-new-relation-between-tables"></a>Erstellen Sie eine neue Beziehung zwischen Tabellen

Um eine neue Beziehung zwischen zwei Tabellen zu erstellen, wählen Sie in der Dataset-Designer die Titelleiste jeder Tabelle, klicken Sie dann mit der rechten Maustaste und wählen Sie **Beziehung hinzufügen**.

![Hierarchische Aktualisierung, Relation-Menü "hinzufügen"](../data-tools/media/hierarchical-update-add-relation-menu.png)

## <a name="understand-foreign-key-constraints-cascading-updates-and-deletes"></a>Verstehen der foreign Key-Einschränkungen, updateweitergaben und löschungen

Es ist wichtig, dass Sie nachvollziehen können, wie die Fremdschlüsseleinschränkungen und das Weitergabeverhalten in der Datenbank im generierten DataSet-Code erstellt werden.

Standardmäßig werden die Datentabellen in einem DataSet mit Beziehungen (<xref:System.Data.DataRelation>) generiert, die den Beziehungen in der Datenbank entsprechen. Jedoch wird die Beziehung im DataSet nicht als Fremdschlüsseleinschränkung generiert. Die <xref:System.Data.DataRelation> als konfiguriert ist, **nur Beziehung** ohne <xref:System.Data.ForeignKeyConstraint.UpdateRule%2A> oder <xref:System.Data.ForeignKeyConstraint.DeleteRule%2A> in Kraft.

Standardmäßig sind Aktualisierungs- und Löschweitergaben deaktiviert, auch wenn Aktualisierungs- und/oder Löschweitergaben für die Datenbankbeziehung aktiviert sind. Beispielsweise können ein neuer Kunde und einen neuen Auftrag erstellen und dann versucht wird, zum Speichern der Daten einen Konflikt verursachen mit foreign Key-Einschränkungen, die in der Datenbank definiert sind. Weitere Informationen finden Sie unter [Deaktivieren von Einschränkungen beim Auffüllen von Datasets](turn-off-constraints-while-filling-a-dataset.md).

## <a name="set-the-order-to-perform-updates"></a>Legen Sie die Reihenfolge zum Durchführen von Aktualisierungen

Festlegen der Reihenfolge zum Durchführen von Aktualisierungen legt die Reihenfolge der Person, die eingefügt, aktualisiert und gelöscht, müssen alle geänderten Daten in allen Tabellen eines Datasets zu speichern. Wenn das hierarchische Update aktiviert ist, werden zuerst die Einfüge-, dann die Update- und anschließend die Löschvorgänge durchgeführt. Der `TableAdapterManager` stellt die `UpdateOrder`-Eigenschaft bereit, die Sie setzen können, um zuerst die Updates und dann die Einfüge- und Löschvorgänge durchzuführen.

> [!NOTE]
> Es ist wichtig zu verstehen, dass die Aktualisierungsreihenfolge für alle Vorgänge gilt. D. h. wenn Updates ausgeführt werden, einfügungen und Löschen für alle Tabellen im Dataset erfolgen.

Festlegen der `UpdateOrder` -Eigenschaft, nach dem Ziehen von Elementen aus der [Fensters "Datenquellen"](add-new-data-sources.md#data-sources-window) auf ein Formular, wählen Sie die `TableAdapterManager` in der Komponentenleiste, und legen Sie dann die `UpdateOrder` -Eigenschaft in der **Eigenschaften** Fenster.

## <a name="create-a-backup-copy-of-a-dataset-before-performing-a-hierarchical-update"></a>Erstellen Sie eine Sicherungskopie der ein Dataset vor dem Durchführen einer hierarchischen Aktualisierung

Beim Speichern von Daten (durch Aufrufen der `TableAdapterManager.UpdateAll()`-Methode) aktualisiert der `TableAdapterManager` die Daten für jede Tabelle in einer einzelnen Transaktion. Wenn ein Teil der Aktualisierung für eine Tabelle fehlschlägt, wird für die gesamte Transaktion ein Rollback ausgeführt. In den meisten Fällen gibt das Rollback Ihrer Anwendung in seinen ursprünglichen Zustand zurück.

Manchmal möchten Sie das DataSet jedoch möglicherweise aus der Sicherungskopie wiederherstellen, Ein Beispiel dafür auftreten, wenn es sich bei Verwendung von automatisch inkrementierten Werten. Angenommen, einen Vorgang nicht erfolgreich ist, automatisch inkrementierten Werten im Dataset nicht zurückgesetzt und weiterhin, dass das Dataset automatisch inkrementierten Werten erstellen. Dadurch wird eine Lücke in den Nummerierung, die möglicherweise nicht in der Anwendung. Für Fälle, in denen dies zu einem Problem führt, stellt der `TableAdapterManager` die `BackupDataSetBeforeUpdate`-Eigenschaft bereit, durch die das vorhandene DataSet beim Fehlschlagen der Transaktion durch eine Sicherungskopie ersetzt wird.

> [!NOTE]
> Die Sicherungskopie ist nur im Arbeitsspeicher, während die `TableAdapterManager.UpdateAll` Methode ausgeführt wird. Daher keinen programmgesteuerten Zugriff auf dieses gesicherte Dataset vorhanden ist, da sie das ursprüngliche Dataset ersetzt oder den Gültigkeitsbereich verlässt, sobald die `TableAdapterManager.UpdateAll` Methode die Ausführung abgeschlossen ist.

## <a name="modify-the-generated-save-code-to-perform-the-hierarchical-update"></a>Ändern Sie den generierten speichern-Code, um die hierarchische Aktualisierung ausgeführt wird

Speichern Sie die Änderungen der verknüpften Tabellen im Dataset in der Datenbank, indem Sie die Methode `TableAdapterManager.UpdateAll` aufrufen und den Namen des Datasets übergeben, der die verknüpften Tabellen enthält. Führen Sie zum Beispiel die Methode `TableAdapterManager.UpdateAll(NorthwindDataset)` aus, um Aktualisierungen von allen Tabellen im NorthwindDataset zur Back-End-Datenbank zu senden.

Nachdem Sie die Elemente aus dem Fenster **Datenquellen** abgelegt haben, wird der Code automatisch dem `Form_Load`-Ereignis für das Füllen jeder Tabelle hinzugefügt (den `TableAdapter.Fill`-Methoden). Es wird auch Code zum Click-Ereignis der Schaltfläche **Speichern** des <xref:System.Windows.Forms.BindingNavigator> hinzugefügt, sodass die Daten des Datasets wieder in der Datenbank gespeichert werden (der `TableAdapterManager.UpdateAll`-Methode).

Der generierte Speichern-Code enthält eine Codezeile, die die Methode `CustomersBindingSource.EndEdit` aufruft. Genauer gesagt ruft der <xref:System.Windows.Forms.BindingSource.EndEdit%2A> Methode des ersten <xref:System.Windows.Forms.BindingSource>zum Formular hinzugefügt wird. Dieser Code wird also nur generiert, für die erste Tabelle, die von gezogen wird die **Datenquellen** auf das Formular. Der Aufruf <xref:System.Windows.Forms.BindingSource.EndEdit%2A> führt ein Commit aller Änderungen durch, die in irgendeinem datengebundenen Steuerelement ablaufen, das derzeit bearbeitet wird. Wenn also ein datengebundenes Steuerelement den Fokus noch besitzt und Sie auf **Speichern** klicken, werden alle ausstehenden Bearbeitungen in diesem Steuerelement committet, bevor der eigentliche Speichervorgang durchgeführt wird (die `TableAdapterManager.UpdateAll`-Methode).

> [!NOTE]
> Die **Dataset-Designer** fügt nur die `BindingSource.EndEdit` Code für die erste Tabelle, die auf dem Formular abgelegt wird. Sie müssen deshalb eine Codezeile zum Aufruf der `BindingSource.EndEdit`-Methode für jede verknüpfte Tabelle auf dem Formular hinzufügen. Für diese exemplarische Vorgehensweise heißt das, dass Sie einen Aufruf zur `OrdersBindingSource.EndEdit`-Methode hinzufügen müssen.

### <a name="to-update-the-code-to-commit-changes-to-the-related-tables-before-saving"></a>So aktualisieren Sie den Code für einen Commit der Änderungen zu den verknüpften Tabellen vor dem Speichern

1.  Doppelklicken Sie auf <xref:System.Windows.Forms.BindingNavigator> auf **Speichern**, um **Form1** im Code-Editor zu öffnen.

2.  Fügen Sie eine Codezeile ein, um die `OrdersBindingSource.EndEdit`-Methode nach der Zeile aufzurufen, die die `CustomersBindingSource.EndEdit`-Methode aufruft. Der Code im Click-Ereignis **Speichern** sollte etwa wie folgt aussehen:

     [!code-vb[VSProDataOrcasHierarchicalUpdate#1](../data-tools/codesnippet/VisualBasic/hierarchical-update_1.vb)]
     [!code-csharp[VSProDataOrcasHierarchicalUpdate#1](../data-tools/codesnippet/CSharp/hierarchical-update_1.cs)]

Neben dem Commit für Änderungen an einer verknüpften untergeordneten Tabelle vor dem Speichern in einer Datenbank müssen Sie vielleicht einen Commit der neue erstellten übergeordneten Datensätze durchführen, ehe Sie neue untergeordnete Datensätze dem Dataset hinzufügen. Das heißt, Sie müssen möglicherweise den neuen übergeordneten Datensatz hinzufügen (`Customer`) auf das Dataset vor dem Aktivieren der foreign Key-Einschränkungen neue untergeordnete Datensätze (`Orders`) dem Dataset hinzugefügt werden. Das erreichen Sie, indem Sie das untergeordnete `BindingSource.AddingNew`-Ereignis verwenden.

> [!NOTE]
> Müssen Sie den commit übergeordneter Datensätze je nach für den Typ des Steuerelements, das zum Binden an die Datenquelle verwendet wird. In dieser exemplarischen Vorgehensweise verwenden Sie einzelne Steuerelemente, zum Binden an die übergeordnete Tabelle. Dies erfordert zusätzlichen Code, um den neuen übergeordneten Datensatz zu übernehmen. Wenn die übergeordneten Datensätze stattdessen, in einem komplexen Bindungssteuerelement angezeigt wurden wie der <xref:System.Windows.Forms.DataGridView>, ist dieser zusätzliche <xref:System.Windows.Forms.BindingSource.EndEdit%2A> aufrufen, für der übergeordneten Datensatz nicht erforderlich sein würde. Das liegt daran, dass die zugrunde liegende Datenbindungsfunktion des Steuerelements den Commit neuer Datensätze übernimmt.

### <a name="to-add-code-to-commit-parent-records-in-the-dataset-before-adding-new-child-records"></a>So fügen Sie Code für den Commit übergeordneter Datensätze hinzu, ehe untergeordnete Datensätze hinzufügt werden

1.  Erstellen Sie einen Ereignishandler für das `OrdersBindingSource.AddingNew`-Ereignis.

    -   Open **Form1** wählen Sie in der Entwurfsansicht **OrdersBindingSource** wählen Sie in der Komponentenleiste **Ereignisse** in die **Eigenschaften** Fenster und Doppelklicken Sie dann auf die **AddingNew** Ereignis.

2.  Fügen Sie eine einzige Zeile Code an den Ereignishandler, die Aufrufe der `CustomersBindingSource.EndEdit` Methode. Der Code im Ereignis `OrdersBindingSource_AddingNew` sollte etwa folgendermaßen aussehen:

     [!code-vb[VSProDataOrcasHierarchicalUpdate#2](../data-tools/codesnippet/VisualBasic/hierarchical-update_2.vb)]
     [!code-csharp[VSProDataOrcasHierarchicalUpdate#2](../data-tools/codesnippet/CSharp/hierarchical-update_2.cs)]

## <a name="tableadaptermanager-reference"></a>TableAdapterManager-Verweis

Standardmäßig eine `TableAdapterManager` Klasse wird generiert, wenn Sie ein Dataset erstellen, die verknüpfte Tabellen enthält. Um zu verhindern, dass die Klasse generiert wird, ändern Sie den Wert von der `Hierarchical Update` -Eigenschaft des Datasets auf "false". Wenn Sie eine Tabelle, die eine Beziehung auf die Entwurfsoberfläche, ein Windows-Formulars oder einer WPF-Seite verfügt ziehen, wird Visual Studio eine Membervariable der Klasse deklariert. Wenn Sie die Datenbindung nicht verwenden, müssen Sie manuell die Variable zu deklarieren.

Die `TableAdapterManager` -Klasse ist nicht Teil der [!INCLUDE[dnprdnshort](../code-quality/includes/dnprdnshort_md.md)]. Aus diesem Grund können keine Sie es in der Dokumentation nachschlagen. Er wird zur Entwurfszeit im Rahmen des Erstellungsprozesses des Datasets erstellt.

Im folgenden sind die häufig verwendeten Methoden und Eigenschaften von den `TableAdapterManager` Klasse:

|Member|Beschreibung|
|------------|-----------------|
|`UpdateAll`-Methode|Speichert alle Daten aus allen Datentabellen an.|
|`BackUpDataSetBeforeUpdate` -Eigenschaft|Bestimmt, ob eine Sicherungskopie des Datasets vor dem Ausführen erstellen den `TableAdapterManager.UpdateAll` Methode. Boolescher Wert.|
|*TableName* `TableAdapter` Eigenschaft|Stellt eine `TableAdapter`. Die generierte `TableAdapterManager` enthält eine Eigenschaft für jede `TableAdapter` verwaltet. Beispielsweise wird ein Dataset mit den Tabellen Customers und Orders mit generiert eine `TableAdapterManager` , enthält `CustomersTableAdapter` und `OrdersTableAdapter` Eigenschaften.|
|`UpdateOrder` -Eigenschaft|Steuert die Reihenfolge von den einzelnen INSERT-, Update- und Delete-Befehle. Legen Sie diese Einstellung auf einen der Werte in der `TableAdapterManager.UpdateOrderOption` Enumeration.<br /><br /> In der Standardeinstellung die `UpdateOrder` nastaven NA hodnotu **InsertUpdateDelete**. Dies bedeutet, die einfügungen, dann aktualisiert und löscht dann erfolgen für alle Tabellen im Dataset.|

## <a name="see-also"></a>Siehe auch

- [Rückspeichern von Daten in der Datenbank](../data-tools/save-data-back-to-the-database.md)
