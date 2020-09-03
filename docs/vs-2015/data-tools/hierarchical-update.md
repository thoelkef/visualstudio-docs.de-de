---
title: Hierarchische Aktualisierung | Microsoft-Dokumentation
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
caps.latest.revision: 29
author: jillre
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: 99e19bce34c2bc8578a062c87aaef10302589075
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 09/02/2020
ms.locfileid: "72670019"
---
# <a name="hierarchical-update"></a>Hierarchisches Update
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Hierarchische Aktualisierung * bezieht sich auf den Prozess, bei dem aktualisierte Daten (aus einem DataSet mit zwei oder mehr verknüpften Tabellen) zurück in eine Datenbank gespeichert werden, während referenzielle Integritäts Regeln beibehalten werden. *Referenzielle Integrität* bezieht sich auf die Konsistenzregeln, die von den Einschränkungen in einer Datenbank bereitgestellt werden, die das Verhalten beim Einfügen, aktualisieren und Löschen verwandter Datensätze steuern. Beispielsweise ist es eine referenzielle Integrität, die die Erstellung eines Kundendatensatzes erzwingt, bevor Aufträge für diesen Kunden erstellt werden können.  Weitere Informationen zu Beziehungen in Datasets finden Sie unter [Beziehungen in Datasets](../data-tools/relationships-in-datasets.md) .

 Das hierarchische Update Feature verwendet einen `TableAdapterManager` , um die `TableAdapter` s in einem typisierten DataSet zu verwalten. Bei der `TableAdapterManager` Komponente handelt [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] es sich um eine von generierte Klasse, die nicht Teil von ist [!INCLUDE[dnprdnshort](../includes/dnprdnshort-md.md)] . Wenn Sie eine Tabelle aus dem Datenquellen Fenster auf eine Windows Form-oder WPF-Seite ziehen, fügt Visual Studio dem Formular oder der Seite eine Variable vom Typ TableAdapterManager hinzu, und Sie sehen Sie im Designer in der Komponenten Leiste. Ausführliche Informationen zur- `TableAdapterManager` Klasse finden Sie im Abschnitt "TableAdapterManager-Referenz" unter [Übersicht über TableAdapterManager](https://msdn.microsoft.com/library/33076d42-6b41-491a-ac11-6c6339aea650).

 Standardmäßig behandelt ein Dataset verknüpfte Tabellen als "Beziehungen", was bedeutet, dass keine FOREIGN KEY-Einschränkungen erzwungen werden. Sie können diese Einstellung zur Entwurfszeit ändern, indem Sie die DataSet-Designer verwenden. Wählen Sie die Beziehungs Linie zwischen zwei Tabellen aus, um das Dialogfeld " **Beziehung** " aufzubringen. Durch die Änderungen, die Sie hier vornehmen, wird festgelegt, wie sich der TableAdapterManager verhält, wenn die Änderungen in den verknüpften Tabellen zurück an die Datenbank gesendet werden.

## <a name="enablehierarchical-update-in-a-dataset"></a>Enablehierarchisch-Update in einem DataSet
 Standardmäßig wird die hierarchische Aktualisierung für alle neuen DataSets aktiviert, die in einem Projekt hinzugefügt oder erstellt werden. Aktivieren bzw. deaktivieren Sie die hierarchische Aktualisierung, indem Sie die Eigenschaft **hierarchische Aktualisierung** eines typisierten Datasets im DataSet-Designer auf **true** oder **false**festlegen:

 ![Einstellung für hierarchische Aktualisierung](../data-tools/media/hierarchical-update-setting.png "Einstellung für hierarchische Aktualisierung")

## <a name="create-a-new-relation-between-tables"></a>Erstellen einer neuen Beziehung zwischen Tabellen
 Wenn Sie eine neue Beziehung zwischen zwei Tabellen erstellen möchten, wählen Sie im DataSet-Designer die Titelleiste der einzelnen Tabellen aus, klicken Sie dann mit der rechten Maustaste, und wählen Sie**Beziehung hinzufügen**aus.

 ![Hierarchisches Update Add Relation-Menü](../data-tools/media/hierarchical-update-add-relation-menu.png "Hierarchisches Update Add Relation-Menü")

## <a name="understand-foreign-key-constraints-cascading-updates-and-deletes"></a>Verstehen von Foreign Key-Einschränkungen, kaskadierenden Updates und Löschungen
 Es ist wichtig, dass Sie nachvollziehen können, wie die Fremdschlüsseleinschränkungen und das Weitergabeverhalten in der Datenbank im generierten DataSet-Code erstellt werden.

 Standardmäßig werden die Datentabellen in einem DataSet mit Beziehungen (<xref:System.Data.DataRelation>) generiert, die den Beziehungen in der Datenbank entsprechen. Jedoch wird die Beziehung im DataSet nicht als Fremdschlüsseleinschränkung generiert. Die <xref:System.Data.DataRelation> wird **nur dann als Beziehung** ohne <xref:System.Data.ForeignKeyConstraint.UpdateRule%2A> oder <xref:System.Data.ForeignKeyConstraint.DeleteRule%2A> wirksam konfiguriert.

 Standardmäßig sind Aktualisierungs- und Löschweitergaben deaktiviert, auch wenn Aktualisierungs- und/oder Löschweitergaben für die Datenbankbeziehung aktiviert sind. Wenn Sie z. b. einen neuen Kunden und eine neue Bestellung erstellen und dann versuchen, die Daten zu speichern, kann dies zu einem Konflikt mit den Foreign Key-Einschränkungen führen, die in der Datenbank definiert sind. Weitere Informationen finden Sie unter Gewusst [wie: Konfigurieren von Foreign Key-Einschränkungen in einem DataSet](https://msdn.microsoft.com/library/3954c388-e209-4a67-a34e-5ca106282f8e).

## <a name="set-the-order-to-perform-updates"></a>Festlegen der Reihenfolge für die Durchführung von Updates
 Durch Festlegen der Reihenfolge für die Durchführung von Updates wird die Reihenfolge der einzelnen Einfügungen, Updates und Löschvorgänge festgelegt, die erforderlich sind, um alle geänderten Daten in allen Tabellen eines Datasets zu speichern. Wenn das hierarchische Update aktiviert ist, werden zuerst die Einfüge-, dann die Update- und anschließend die Löschvorgänge durchgeführt. Der `TableAdapterManager` stellt die `UpdateOrder`-Eigenschaft bereit, die Sie setzen können, um zuerst die Updates und dann die Einfüge- und Löschvorgänge durchzuführen.

> [!NOTE]
> Es ist wichtig zu verstehen, dass die Aktualisierungs Reihenfolge alle inklusiv ist. Das heißt, wenn Updates ausgeführt werden, werden Einfügungen und Löschvorgänge für alle Tabellen im DataSet durchgeführt.

 Wenn Sie die-Eigenschaft festlegen möchten `UpdateOrder` , wählen Sie nach dem Ziehen von Elementen aus dem [Datenquellen Fenster](https://msdn.microsoft.com/library/0d20f699-cc95-45b3-8ecb-c7edf1f67992) auf ein Formular das `TableAdapterManager` in der Komponenten Leiste aus, und legen Sie dann `UpdateOrder` im **Eigenschaften** Fenster die-Eigenschaft fest. Weitere Informationen finden Sie unter Gewusst [wie: Festlegen der Reihenfolge beim Ausführen eines hierarchischen Updates](https://msdn.microsoft.com/library/a0734935-78dd-4c0b-80d7-5e7925789c83).

## <a name="create-a-backup-copy-of-a-dataset-before-performing-a-hierarchical-update"></a>Erstellen einer Sicherungskopie eines Datasets vor dem Durchführen einer hierarchischen Aktualisierung
 Beim Speichern von Daten (durch Aufrufen der `TableAdapterManager.UpdateAll()`-Methode) aktualisiert der `TableAdapterManager` die Daten für jede Tabelle in einer einzelnen Transaktion. Wenn ein Teil der Aktualisierung für eine Tabelle fehlschlägt, wird für die gesamte Transaktion ein Rollback ausgeführt. In den meisten Fällen gibt der Rollback Ihre Anwendung in den ursprünglichen Zustand zurück.

 Manchmal möchten Sie das DataSet jedoch möglicherweise aus der Sicherungskopie wiederherstellen, Ein Beispiel hierfür kann auftreten, wenn Sie Werte für die automatische Inkrement verwenden. Wenn beispielsweise ein Speichervorgang nicht erfolgreich ist, werden Werte für automatische inkrementellen nicht im Dataset zurückgesetzt, und das DataSet erstellt weiterhin automatisch inkrementellen Werte. Dadurch bleibt eine Lücke bei der Nummerierung, die in Ihrer Anwendung möglicherweise nicht zulässig ist. Für Fälle, in denen dies zu einem Problem führt, stellt der `TableAdapterManager` die `BackupDataSetBeforeUpdate`-Eigenschaft bereit, durch die das vorhandene DataSet beim Fehlschlagen der Transaktion durch eine Sicherungskopie ersetzt wird.

> [!NOTE]
> Die Sicherungskopie befindet sich nur im Arbeitsspeicher, während die- `TableAdapterManager.UpdateAll` Methode ausgeführt wird. Daher ist kein Programm gesteuerter Zugriff auf dieses Sicherungs Dataset möglich, da es entweder das ursprüngliche DataSet ersetzt oder den Gültigkeitsbereich verlässt, sobald die `TableAdapterManager.UpdateAll` Ausführung der Methode abgeschlossen ist.

## <a name="modify-the-generated-save-code-to-perform-the-hierarchical-update"></a>Ändern des generierten Speicher Codes zum Durchführen der hierarchischen Aktualisierung
 Speichern Sie die Änderungen der verknüpften Tabellen im Dataset in der Datenbank, indem Sie die Methode `TableAdapterManager.UpdateAll` aufrufen und den Namen des Datasets übergeben, der die verknüpften Tabellen enthält. Führen Sie zum Beispiel die Methode `TableAdapterManager.UpdateAll(NorthwindDataset)` aus, um Aktualisierungen von allen Tabellen im NorthwindDataset zur Back-End-Datenbank zu senden.

 Nachdem Sie die Elemente aus dem Fenster **Datenquellen** abgelegt haben, wird der Code automatisch dem `Form_Load`-Ereignis für das Füllen jeder Tabelle hinzugefügt (den `TableAdapter.Fill`-Methoden). Es wird auch Code zum Click-Ereignis der Schaltfläche **Speichern** des <xref:System.Windows.Forms.BindingNavigator> hinzugefügt, sodass die Daten des Datasets wieder in der Datenbank gespeichert werden (der `TableAdapterManager.UpdateAll`-Methode).

 Der generierte Speichern-Code enthält eine Codezeile, die die Methode `CustomersBindingSource.EndEdit` aufruft. Genauer gesagt, ruft Sie die- <xref:System.Windows.Forms.BindingSource.EndEdit%2A> Methode der ersten <xref:System.Windows.Forms.BindingSource> auf, die dem Formular hinzugefügt wird. Dies bedeutet, dass dieser Code nur für die erste Tabelle generiert wird, die aus dem **Datenquellen** Fenster auf das Formular gezogen wird. Der Aufruf <xref:System.Windows.Forms.BindingSource.EndEdit%2A> führt ein Commit aller Änderungen durch, die in irgendeinem datengebundenen Steuerelement ablaufen, das derzeit bearbeitet wird. Wenn also ein datengebundenes Steuerelement den Fokus noch besitzt und Sie auf **Speichern** klicken, werden alle ausstehenden Bearbeitungen in diesem Steuerelement committet, bevor der eigentliche Speichervorgang durchgeführt wird (die `TableAdapterManager.UpdateAll`-Methode).

> [!NOTE]
> Der DataSet-Designer fügt nur den `BindingSource.EndEdit` Code für die erste Tabelle, die auf dem Formular abgelegt wird, hinzu. Sie müssen deshalb eine Codezeile zum Aufruf der `BindingSource.EndEdit`-Methode für jede verknüpfte Tabelle auf dem Formular hinzufügen. Für diese exemplarische Vorgehensweise heißt das, dass Sie einen Aufruf zur `OrdersBindingSource.EndEdit`-Methode hinzufügen müssen.

#### <a name="to-update-the-code-to-commit-changes-to-the-related-tables-before-saving"></a>So aktualisieren Sie den Code für einen Commit der Änderungen zu den verknüpften Tabellen vor dem Speichern

1. Doppelklicken Sie auf <xref:System.Windows.Forms.BindingNavigator> auf **Speichern**, um **Form1** im Code-Editor zu öffnen.

2. Fügen Sie eine Codezeile ein, um die `OrdersBindingSource.EndEdit`-Methode nach der Zeile aufzurufen, die die `CustomersBindingSource.EndEdit`-Methode aufruft. Der Code im Click-Ereignis **Speichern** sollte etwa wie folgt aussehen:

    [!code-csharp[VSProDataOrcasHierarchicalUpdate#1](../snippets/csharp/VS_Snippets_VBCSharp/VSProDataOrcasHierarchicalUpdate/CS/Form1.cs#1)]
    [!code-vb[VSProDataOrcasHierarchicalUpdate#1](../snippets/visualbasic/VS_Snippets_VBCSharp/VSProDataOrcasHierarchicalUpdate/VB/Form1.vb#1)]

   Neben dem Commit für Änderungen an einer verknüpften untergeordneten Tabelle vor dem Speichern in einer Datenbank müssen Sie vielleicht einen einen Commit der neue erstellten übergeordneten Datensätze durchführen, ehe Sie neue untergeordnete Datensätze dem Dataset hinzufügen. Anders ausgedrückt müssen Sie möglicherweise den neuen übergeordneten Datensatz (Customer) dem Dataset hinzufügen, ehe es die Fremdschlüsseleinschränkungen ermöglichen, dass dem Dataset neue untergeordnete Datensätze (Bestellungen) hinzugefügt werden können. Das erreichen Sie, indem Sie das untergeordnete `BindingSource.AddingNew`-Ereignis verwenden.

> [!NOTE]
> Ob Sie einen Commit für neue übergeordnete Datensätze durchsetzen müssen, hängt vom Typ des Steuer Elements ab, das zum Binden an die Datenquelle verwendet wird. In dieser exemplarischen Vorgehensweise verwenden Sie einzelne Steuerelemente, um eine Bindung an die übergeordnete Tabelle herzustellen. Hierfür ist zusätzlicher Code erforderlich, um einen Commit für den neuen übergeordneten Datensatz durchzusetzen. Wenn die übergeordneten Datensätze stattdessen in einem komplexen Bindungs Steuerelement wie dem angezeigt werden <xref:System.Windows.Forms.DataGridView> , ist dieser zusätzliche-Befehl <xref:System.Windows.Forms.BindingSource.EndEdit%2A> für den übergeordneten Datensatz nicht erforderlich. Das liegt daran, dass die zugrunde liegende Datenbindungsfunktion des Steuerelements den Commit neuer Datensätze übernimmt.

#### <a name="to-add-code-to-commit-parent-records-in-the-dataset-before-adding-new-child-records"></a>So fügen Sie Code für den Commit übergeordneter Datensätze hinzu, ehe untergeordnete Datensätze hinzufügt werden

1. Erstellen Sie einen Ereignishandler für das `OrdersBindingSource.AddingNew`-Ereignis.

    - Öffnen Sie **Form1** in der Entwurfs Ansicht, wählen Sie **OrdersBindingSource** in der Komponenten Leiste aus, wählen Sie im Fenster **Eigenschaften** die Option **Ereignisse** aus, und doppelklicken Sie dann auf das **AddingNew** -Ereignis.

2. Fügen Sie dem Ereignishandler, der die-Methode aufruft, eine Codezeile hinzu `CustomersBindingSource.EndEdit` . Der Code im Ereignis `OrdersBindingSource_AddingNew` sollte etwa folgendermaßen aussehen:

     [!code-csharp[VSProDataOrcasHierarchicalUpdate#2](../snippets/csharp/VS_Snippets_VBCSharp/VSProDataOrcasHierarchicalUpdate/CS/Form1.cs#2)]
     [!code-vb[VSProDataOrcasHierarchicalUpdate#2](../snippets/visualbasic/VS_Snippets_VBCSharp/VSProDataOrcasHierarchicalUpdate/VB/Form1.vb#2)]

## <a name="tableadaptermanager-reference"></a>TableAdapterManager-Referenz
 Standardmäßig wird eine- `TableAdapterManager` Klasse generiert, wenn Sie ein Dataset erstellen, das verknüpfte Tabellen enthält. Um zu verhindern, dass die Klasse generiert wird, ändern Sie den Wert der- `Hierarchical Update` Eigenschaft des Datasets in false. Wenn Sie eine Tabelle, die eine Beziehung aufweist, auf die Entwurfs Oberfläche einer Windows Forms-oder WPF-Seite ziehen, deklariert Visual Studio eine Member-Variable der-Klasse. Wenn Sie DataBinding nicht verwenden, müssen Sie die Variable manuell deklarieren.

 Die- `TableAdapterManager` Klasse ist nicht Teil des [!INCLUDE[dnprdnshort](../includes/dnprdnshort-md.md)] . Daher können Sie Sie nicht in der Dokumentation nachschlagen. Sie wird zur Entwurfszeit im Rahmen des dataseterstellungs Prozesses erstellt.

 Im folgenden finden Sie die häufig verwendeten Methoden und Eigenschaften der- `TableAdapterManager` Klasse:

|Member|BESCHREIBUNG|
|------------|-----------------|
|`UpdateAll`-Methode|Speichert alle Daten aus allen Datentabellen.|
|`BackUpDataSetBeforeUpdate`-Eigenschaft|Bestimmt, ob vor dem Ausführen der-Methode eine Sicherungskopie des Datasets erstellt wird `TableAdapterManager.UpdateAll` . Booleschen.|
|*TableName* `TableAdapter` Property|Stellt einen dar `TableAdapter` . Der generierte `TableAdapterManager` enthält eine-Eigenschaft für jeden, der von `TableAdapter` ihm verwaltet wird. Beispielsweise wird ein DataSet mit einer Customers-und Orders-Tabelle mit einem generiert, `TableAdapterManager` das die-Eigenschaft und die-Eigenschaft enthält `CustomersTableAdapter` `OrdersTableAdapter` .|
|`UpdateOrder`-Eigenschaft|Steuert die Reihenfolge der einzelnen INSERT-, Update-und DELETE-Befehle. Legen Sie diesen Wert auf einen der Werte in der- `TableAdapterManager.UpdateOrderOption` Enumeration fest.<br /><br /> Standardmäßig `UpdateOrder` ist auf **InsertUpdateDelete**festgelegt. Dies bedeutet, dass Einfügungen, Updates und Löschungen für alle Tabellen im DataSet durchgeführt werden. Weitere Informationen finden Sie unter Gewusst [wie: Festlegen der Reihenfolge beim Ausführen eines hierarchischen Updates](https://msdn.microsoft.com/library/a0734935-78dd-4c0b-80d7-5e7925789c83).|

## <a name="see-also"></a>Weitere Informationen
 [Rückspeichern von Daten in der Datenbank](../data-tools/save-data-back-to-the-database.md)
