---
title: Hierarchische Aktualisierung
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
manager: douge
ms.prod: visual-studio-dev15
ms.technology: vs-data-tools
ms.workload:
- data-storage
ms.openlocfilehash: 442d6cd60597219c25b41f26ad8c2dc2151248ee
ms.sourcegitcommit: 58052c29fc61c9a1ca55a64a63a7fdcde34668a4
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 06/04/2018
ms.locfileid: "34747468"
---
# <a name="hierarchical-update"></a>Hierarchische Aktualisierung
*Hierarchische Aktualisierung* bezieht sich auf das Zurückspeichern der aktualisierten Daten (aus einem Dataset mit zwei oder mehr verknüpfte Tabellen) in einer Datenbank beim Verwalten von Regeln für die referenzielle Integrität. *Referenzielle Integrität* bezieht sich auf die Konsistenzregeln, angegeben durch die Einschränkungen in einer Datenbank, die das Verhalten des einfügen, aktualisieren und Löschen von verknüpften Datensätzen zu steuern. Beispielsweise ist es die referenzielle Integrität, der die Erstellung eines Kundendatensatzes zuzulassen Aufträge erstellt werden für diesen Kunden erzwingt.  Weitere Informationen zu Beziehungen in Datasets, finden Sie unter [Beziehungen in Datasets](../data-tools/relationships-in-datasets.md)

 Die hierarchische Aktualisierung-Funktion verwendet eine `TableAdapterManager` zum Verwalten der `TableAdapter`s in einem typisierten Dataset. Die `TableAdapterManager` Komponente ist eine [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)]-generierte Klasse, daher ist es nicht Teil der [!INCLUDE[dnprdnshort](../code-quality/includes/dnprdnshort_md.md)]. Wenn Sie eine Tabelle aus dem Datenquellenfenster in einem Windows Form oder eine WPF-Seite ziehen, Visual Studio fügt eine Variable vom Typ TableAdapterManager in das Formular oder die Seite, und Sie im Designer auf der Komponentenleiste angezeigt. Ausführliche Informationen zu den `TableAdapterManager` Klasse, finden Sie unter dem Abschnitt "TableAdapterManager-Referenz" [TableAdapters](../data-tools/create-and-configure-tableadapters.md).

 Standardmäßig behandelt ein Dataset verknüpfte Tabellen als "nur Beziehungen" Was bedeutet, dass sie foreign Key-Einschränkungen erzwingen, nicht. Sie können diese Einstellung zur Entwurfszeit mithilfe des Dataset-Designers ändern. Wählen Sie die Beziehungslinie zwischen zwei Tabellen, um die **Beziehung** (Dialogfeld). Die Änderungen, die Sie hier vornehmen, wenn verhält sich wie die TableAdapterManager bestimmt die Änderungen in den zugehörigen Tabellen zurück an die Datenbank senden.

## <a name="enable-hierarchical-update-in-a-dataset"></a>Aktivieren der hierarchischen Aktualisierung in einem dataset
 Standardmäßig wird die hierarchische Aktualisierung für alle neuen DataSets aktiviert, die in einem Projekt hinzugefügt oder erstellt werden. Aktivieren oder deaktivieren Sie hierarchische Aktualisierung, durch Festlegen der **hierarchische Aktualisierung** Eigenschaft eines typisierten Datasets im Dataset **"true"** oder **"false"**:

 ![Hierarchische Aktualisierung-Einstellung](../data-tools/media/hierarchical-update-setting.png)

## <a name="create-a-new-relation-between-tables"></a>Erstellen Sie eine neue Beziehung zwischen Tabellen
 Um eine neue Beziehung zwischen zwei Tabellen zu erstellen, wählen Sie in der Dataset-Designer die Titelleiste jeder Tabelle, klicken Sie dann mit der rechten Maustaste und wählen Sie **Beziehung hinzufügen**.

 ![Hierarchische Aktualisierung, Relation-Menü "hinzufügen"](../data-tools/media/hierarchical-update-add-relation-menu.png)

## <a name="understand-foreign-key-constraints-cascading-updates-and-deletes"></a>Verstehen der foreign Key-Einschränkungen, updateweitergaben und löschungen
 Es ist wichtig zu verstehen, wie foreign Key-Einschränkungen und weitergabeverhalten in der Datenbank in den generierten Dataset-Code erstellt werden.

 Standardmäßig werden die Datentabellen in einem DataSet mit Beziehungen (<xref:System.Data.DataRelation>) generiert, die den Beziehungen in der Datenbank entsprechen. Jedoch wird die Beziehung im DataSet nicht als Fremdschlüsseleinschränkung generiert. Die <xref:System.Data.DataRelation> konfiguriert ist, als **nur Beziehung** ohne <xref:System.Data.ForeignKeyConstraint.UpdateRule%2A> oder <xref:System.Data.ForeignKeyConstraint.DeleteRule%2A> wirksam.

 Standardmäßig sind Aktualisierungs- und Löschweitergaben deaktiviert, auch wenn Aktualisierungs- und/oder Löschweitergaben für die Datenbankbeziehung aktiviert sind. Beispielsweise können ein neuer Kunde und einen neuen Auftrag erstellen und dann versucht wird, die Daten speichern einen Konflikt verursachen mit foreign Key-Einschränkungen, die in der Datenbank definiert sind. Weitere Informationen finden Sie unter [Deaktivieren von Einschränkungen beim Auffüllen von Datasets](turn-off-constraints-while-filling-a-dataset.md).

## <a name="set-the-order-to-perform-updates"></a>Legen Sie die Reihenfolge zum Durchführen von Aktualisierungen
 Festlegen der Reihenfolge zum Durchführen von Aktualisierungen legt die Reihenfolge der einzelnen eingefügt, aktualisiert und gelöscht, müssen Sie alle geänderten Daten in allen Tabellen eines Datasets zu speichern. Wenn hierarchische Aktualisierung aktiviert ist, fügt werden zuerst ausgeführt und dann aktualisiert, und löscht dann. Die `TableAdapterManager` bietet eine `UpdateOrder` -Eigenschaft, die Set zum Durchführen von Aktualisierungen zuerst Einfügevorgänge und dann gelöscht werden kann.

> [!NOTE]
>  Es ist wichtig zu verstehen, dass die Aktualisierungsreihenfolge für alle Vorgänge gilt. D. h., wenn Updates ausgeführt werden, einfügen und löschen Sie dann für alle Tabellen im Dataset erfolgen.

 Festlegen der `UpdateOrder` -Eigenschaft, nach dem Ziehen von Elementen aus der [Datenquellenfenster](add-new-data-sources.md) wählen Sie auf ein Formular der `TableAdapterManager` in der Komponentenleiste, und legen Sie anschließend die `UpdateOrder` Eigenschaft in der **Eigenschaften** Fenster.

## <a name="create-a-backup-copy-of-a-dataset-before-performing-a-hierarchical-update"></a>Erstellen Sie eine Sicherungskopie der ein Dataset vor dem Durchführen einer hierarchischen Aktualisierung
 Beim Speichern von Daten (durch Aufrufen der `TableAdapterManager.UpdateAll()`-Methode) aktualisiert der `TableAdapterManager` die Daten für jede Tabelle in einer einzelnen Transaktion. Wenn ein Teil der Aktualisierung für eine Tabelle fehlschlägt, wird für die gesamte Transaktion ein Rollback ausgeführt. In den meisten Fällen gibt das Rollback die Anwendung auf den ursprünglichen Zustand zurück.

 Manchmal möchten Sie das DataSet jedoch möglicherweise aus der Sicherungskopie wiederherstellen, Dazu zählt beispielsweise der kann auftreten, wenn es sich bei Verwendung von automatisch inkrementierten Werten. Angenommen, ein Speichervorgang Vorgang nicht erfolgreich ist, automatisch inkrementierten Werte im Dataset nicht zurückgesetzt werden und weiterhin, dass das Dataset automatisch inkrementierten Werten zu erstellen. Dies bewirkt, dass eine Lücke im Nummerierung, die möglicherweise nicht in der Anwendung. Für Fälle, in denen dies zu einem Problem führt, stellt der `TableAdapterManager` die `BackupDataSetBeforeUpdate`-Eigenschaft bereit, durch die das vorhandene DataSet beim Fehlschlagen der Transaktion durch eine Sicherungskopie ersetzt wird.

> [!NOTE]
>  Die Sicherungskopie ist nur im Arbeitsspeicher, während die `TableAdapterManager.UpdateAll` Methode ausgeführt wird. Aus diesem Grund keinen programmgesteuerten Zugriff auf dieses gesicherte Dataset vorhanden ist, da er das ursprüngliche Dataset ersetzt oder in den Gültigkeitsbereich verlässt, sobald die `TableAdapterManager.UpdateAll` Methode die Ausführung beendet ist.

## <a name="modify-the-generated-save-code-to-perform-the-hierarchical-update"></a>Ändern Sie den generierten speichern-Code, um die hierarchische Aktualisierung ausgeführt wird
 Speichern Sie die Änderungen der verknüpften Tabellen im Dataset in der Datenbank, indem Sie die Methode `TableAdapterManager.UpdateAll` aufrufen und den Namen des Datasets übergeben, der die verknüpften Tabellen enthält. Führen Sie zum Beispiel die Methode `TableAdapterManager.UpdateAll(NorthwindDataset)` aus, um Aktualisierungen von allen Tabellen im NorthwindDataset zur Back-End-Datenbank zu senden.

 Nachdem Sie Elemente aus dem Löschen der **Datenquellen** Fenster Code automatisch hinzugefügt der `Form_Load` Ereignis, um das Füllen jeder Tabelle (die `TableAdapter.Fill` Methoden). Code wird ebenfalls hinzugefügt der **speichern** click-Ereignis von der <xref:System.Windows.Forms.BindingNavigator> zum Speichern von Daten aus dem Dataset zurück in die Datenbank (die `TableAdapterManager.UpdateAll` Methode).

 Der generierte Speichern-Code enthält eine Codezeile, die die Methode `CustomersBindingSource.EndEdit` aufruft. Genauer gesagt ruft er die <xref:System.Windows.Forms.BindingSource.EndEdit%2A> Methode des ersten <xref:System.Windows.Forms.BindingSource>, die dem Formular hinzugefügt wird. Dieser Code wird also nur generiert, für die erste Tabelle, die von gezogen wird die **Datenquellen** auf das Formular. Der Aufruf <xref:System.Windows.Forms.BindingSource.EndEdit%2A> führt ein Commit aller Änderungen durch, die in irgendeinem datengebundenen Steuerelement ablaufen, das derzeit bearbeitet wird. Aus diesem Grund, wenn ein datengebundenes Steuerelement noch einen Fokus hat und Sie klicken die **speichern** Schaltfläche alle ausstehenden Bearbeitungen insofern, dass Steuerelement werden vor dem eigentlichen speichern durchgeführt (die `TableAdapterManager.UpdateAll` Methode).

> [!NOTE]
>  Der Dataset-Designer fügt nur die `BindingSource.EndEdit` Code für die erste Tabelle, die auf dem Formular abgelegt wird. Sie müssen deshalb eine Codezeile zum Aufruf der `BindingSource.EndEdit`-Methode für jede verknüpfte Tabelle auf dem Formular hinzufügen. Für diese exemplarische Vorgehensweise heißt das, dass Sie einen Aufruf zur `OrdersBindingSource.EndEdit`-Methode hinzufügen müssen.

#### <a name="to-update-the-code-to-commit-changes-to-the-related-tables-before-saving"></a>So aktualisieren Sie den Code für einen Commit der Änderungen zu den verknüpften Tabellen vor dem Speichern

1.  Doppelklicken Sie auf die **speichern** Schaltfläche auf der <xref:System.Windows.Forms.BindingNavigator> öffnen **Form1** im Code-Editor.

2.  Fügen Sie eine Codezeile ein, um die `OrdersBindingSource.EndEdit`-Methode nach der Zeile aufzurufen, die die `CustomersBindingSource.EndEdit`-Methode aufruft. Der Code in der **speichern** Schaltflächen-Klickereignis Ereignis sollte etwa folgendermaßen aussehen:

     [!code-vb[VSProDataOrcasHierarchicalUpdate#1](../data-tools/codesnippet/VisualBasic/hierarchical-update_1.vb)]
     [!code-csharp[VSProDataOrcasHierarchicalUpdate#1](../data-tools/codesnippet/CSharp/hierarchical-update_1.cs)]

Neben dem Commit für Änderungen an einer verknüpften untergeordneten Tabelle vor dem Speichern in einer Datenbank müssen Sie vielleicht einen Commit der neue erstellten übergeordneten Datensätze durchführen, ehe Sie neue untergeordnete Datensätze dem Dataset hinzufügen. Anders ausgedrückt müssen Sie möglicherweise den neuen übergeordneten Datensatz (Customer) dem Dataset hinzufügen, ehe es die Fremdschlüsseleinschränkungen ermöglichen, dass dem Dataset neue untergeordnete Datensätze (Bestellungen) hinzugefügt werden können. Das erreichen Sie, indem Sie das untergeordnete `BindingSource.AddingNew`-Ereignis verwenden.

> [!NOTE]
> Ob Sie den commit übergeordneter Datensätze müssen hängt vom Typ des Steuerelements ab, das auf die Datenquelle zu binden. In dieser exemplarischen Vorgehensweise verwenden Sie einzelne Steuerelemente zum Binden an die übergeordnete Tabelle. Dies erfordert zusätzlichen Code für den commit des neuen übergeordneten Datensatzes. Wenn die übergeordneten Datensätze stattdessen, in einem komplexen Bindungssteuerelement angezeigt wurden wie der <xref:System.Windows.Forms.DataGridView>, dieser zusätzlichen <xref:System.Windows.Forms.BindingSource.EndEdit%2A> -Aufruf für der übergeordneten Datensatz nicht erforderlich wäre. Das liegt daran, dass die zugrunde liegende Datenbindungsfunktion des Steuerelements den Commit neuer Datensätze übernimmt.

#### <a name="to-add-code-to-commit-parent-records-in-the-dataset-before-adding-new-child-records"></a>So fügen Sie Code für den Commit übergeordneter Datensätze hinzu, ehe untergeordnete Datensätze hinzufügt werden

1.  Erstellen Sie einen Ereignishandler für das `OrdersBindingSource.AddingNew`-Ereignis.

    -   Open **Form1** wählen Sie in der Entwurfsansicht **OrdersBindingSource** wählen Sie auf der Komponentenleiste **Ereignisse** in der **Eigenschaften** Fenster, und Doppelklicken Sie dann auf die **AddingNew** Ereignis.

2.  Fügen Sie eine Codezeile an den Ereignishandler, die Aufrufe der `CustomersBindingSource.EndEdit` Methode. Der Code im Ereignis `OrdersBindingSource_AddingNew` sollte etwa folgendermaßen aussehen:

     [!code-vb[VSProDataOrcasHierarchicalUpdate#2](../data-tools/codesnippet/VisualBasic/hierarchical-update_2.vb)]
     [!code-csharp[VSProDataOrcasHierarchicalUpdate#2](../data-tools/codesnippet/CSharp/hierarchical-update_2.cs)]

## <a name="tableadaptermanager-reference"></a>TableAdapterManager-Verweis
 Standardmäßig eine `TableAdapterManager` Klasse wird generiert, wenn Sie ein Dataset erstellen, die verknüpfte Tabellen enthält. Um zu verhindern, dass die Klasse generiert wird, ändern Sie den Wert von der `Hierarchical Update` Eigenschaft des Datasets auf "false". Wenn Sie eine Tabelle, die eine auf die Entwurfsoberfläche der Windows Forms oder WPF-Seite ziehen Beziehung, deklariert Visual Studio eine Membervariable der Klasse. Wenn Sie Databinding nicht verwenden, müssen Sie manuell die Variable zu deklarieren.

 Die `TableAdapterManager` Klasse ist nicht Teil der [!INCLUDE[dnprdnshort](../code-quality/includes/dnprdnshort_md.md)]. Aus diesem Grund können keine Sie es in der Dokumentation nachschlagen. Sie wird zur Entwurfszeit im Rahmen des Erstellungsprozesses des Datasets erstellt.

 Im folgenden werden die häufig verwendeten Methoden und Eigenschaften von der `TableAdapterManager` Klasse:

|Member|Beschreibung|
|------------|-----------------|
|`UpdateAll`-Methode|Speichert alle Daten aus allen Tabellen.|
|`BackUpDataSetBeforeUpdate`-Eigenschaft|Bestimmt, ob erstellen Sie eine Sicherungskopie des Datasets vor dem Ausführen der `TableAdapterManager.UpdateAll` Methode. Boolescher Wert.|
|*TableName* `TableAdapter` Eigenschaft|Stellt eine `TableAdapter`. Die generierte `TableAdapterManager` enthält eine Eigenschaft für jede `TableAdapter` verwaltet. Beispielsweise wird ein Dataset mit einer Customers und Orders-Tabelle generiert, mit einem `TableAdapterManager` enthält `CustomersTableAdapter` und `OrdersTableAdapter` Eigenschaften.|
|`UpdateOrder`-Eigenschaft|Steuert die Reihenfolge von den einzelnen INSERT-, Update- und Delete-Befehle. Legen Sie diese Einstellung auf einen der Werte in der `TableAdapterManager.UpdateOrderOption` Enumeration.<br /><br /> Wird standardmäßig die `UpdateOrder` festgelegt ist, um **InsertUpdateDelete**. Das bedeutet, die eingefügt, aktualisiert und löscht dann werden für alle Tabellen im Dataset ausgeführt.|

## <a name="see-also"></a>Siehe auch

- [Rückspeichern von Daten in der Datenbank](../data-tools/save-data-back-to-the-database.md)