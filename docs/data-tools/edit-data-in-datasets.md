---
title: Bearbeiten von Daten in Datasets
ms.date: 11/04/2016
ms.topic: conceptual
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- datasets [Visual Basic], editing data
- data [Visual Studio], editing in datasets
ms.assetid: 50d5c580-fbf7-408f-be70-e63ac4f4d0eb
author: gewarren
ms.author: gewarren
manager: douge
ms.prod: visual-studio-dev15
ms.technology: vs-data-tools
ms.workload:
- data-storage
ms.openlocfilehash: c1ad74243c70b4ca7aaa8460759abbc898d30bb9
ms.sourcegitcommit: 30f653d9625ba763f6b58f02fb74a24204d064ea
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 06/25/2018
ms.locfileid: "36757148"
---
# <a name="edit-data-in-datasets"></a>Bearbeiten von Daten in Datasets
Ähnlich wie Sie die Daten in einer Tabelle in einer beliebigen Datenbank bearbeiten, bearbeiten Sie die Daten in Tabellen. Der Prozess kann enthalten, einfügen, aktualisieren und Löschen von Datensätzen in der Tabelle. In einem datengebundenen Formular können Sie angeben, welche Felder Benutzer bearbeitbare sind. In diesen Fällen behandelt die Infrastruktur für die Datenbindung an, alle der änderungsnachverfolgung, damit die Änderungen später an die Datenbank gesendet werden können. Wenn Sie programmgesteuert Änderungen an Daten vornehmen und diese Änderungen an die Datenbank gesendet werden sollen, müssen Sie verwenden die Objekte und Methoden, die die änderungsnachverfolgung für die Sie ausführen.

Sie können auch Abfragen, zusätzlich zum Ändern der tatsächlichen Daten, eine <xref:System.Data.DataTable> um bestimmte Datenzeilen zurückzugeben. Beispielsweise können Sie Abfragen für einzelne Zeilen, bestimmte Versionen von Zeilen (ursprüngliche und vorgesehene), geänderte Zeilen oder Zeilen mit Fehlern.

## <a name="to-edit-rows-in-a-dataset"></a>So bearbeiten Sie die Zeilen in einem dataset
So bearbeiten Sie eine vorhandene Zeile in einer <xref:System.Data.DataTable>, gesucht werden soll die <xref:System.Data.DataRow> bearbeiten, und klicken Sie dann die gewünschten Spalten die aktualisierten Werte zuweisen möchten.

Wenn Sie nicht, dass den Index der Zeile wissen soll, bearbeiten, verwenden Sie die `FindBy` Methode zum Suchen nach dem Primärschlüssel:

[!code-csharp[VbRaddataEditing#3](../data-tools/codesnippet/CSharp/edit-data-in-datasets_1.cs)]
[!code-vb[VbRaddataEditing#3](../data-tools/codesnippet/VisualBasic/edit-data-in-datasets_1.vb)]

Wenn Sie wissen, dass der Index der Zeile, Sie können auf zugreifen und Zeilen wie folgt bearbeitet:

[!code-csharp[VbRaddataEditing#5](../data-tools/codesnippet/CSharp/edit-data-in-datasets_2.cs)]
[!code-vb[VbRaddataEditing#5](../data-tools/codesnippet/VisualBasic/edit-data-in-datasets_2.vb)]

## <a name="to-insert-new-rows-into-a-dataset"></a>Um neue Zeilen in ein Dataset einfügen
Anwendungen, die von datengebundenen Steuerelementen in der Regel verwenden neue Datensätze durch Hinzufügen der **Add New** Schaltfläche eine [BindingNavigator-Steuerelement](/dotnet/framework/winforms/controls/bindingnavigator-control-windows-forms).

Um neue Datensätze zu einem Dataset manuell hinzuzufügen, erstellen Sie eine neue Datenzeile durch Aufrufen der Methode in der DataTable-Objekt. Fügen Sie dann auf die Zeile an die <xref:System.Data.DataRow> Auflistung (<xref:System.Data.DataTable.Rows%2A>) von der <xref:System.Data.DataTable>:

[!code-csharp[VbRaddataEditing#1](../data-tools/codesnippet/CSharp/edit-data-in-datasets_3.cs)]
[!code-vb[VbRaddataEditing#1](../data-tools/codesnippet/VisualBasic/edit-data-in-datasets_3.vb)]

Um die Daten beizubehalten, dass das Dataset Updates an der Datenquelle zu senden muss, verwenden Sie die <xref:System.Data.DataRow.Delete%2A> Methode, um Zeilen in einer Datentabelle zu entfernen. Wenn Ihre Anwendung einen TableAdapter verwendet z. B. (oder <xref:System.Data.Common.DataAdapter>), TableAdapters `Update` Methode löscht Zeilen in der Datenbank, die eine <xref:System.Data.DataRow.RowState%2A> von <xref:System.Data.DataRowState.Deleted>.

Wenn Ihre Anwendung nicht zum Senden von Updates in einer Datenquelle benötigt, ist es möglich, Datensätze durch direkten Zugriff auf die Datensammlung für die Zeile zu entfernen (<xref:System.Data.DataRowCollection.Remove%2A>).

#### <a name="to-delete-records-from-a-data-table"></a>Zum Löschen von Datensätzen aus einer Datentabelle

-   Rufen Sie die <xref:System.Data.DataRow.Delete%2A> Methode eine <xref:System.Data.DataRow>.

     Diese Methode den Datensatz nicht physisch entfernt werden. Stattdessen wird den Datensatz für die Löschung markiert.

    > [!NOTE]
    >  Wenn Sie die Count-Eigenschaft des erhalten eine <xref:System.Data.DataRowCollection>, das Rekursionsergebnis enthält Datensätze, die für die Löschung markiert wurden. Um eine genaue Anzahl der Datensätze zu erhalten, die zum Löschen markiert sind nicht, können Sie eine Schleife mit dem Blick auf die Auflistung der <xref:System.Data.DataRow.RowState%2A> Eigenschaft jedes Datensatzes. (Zum Löschen markierte Einträge enthalten ein <xref:System.Data.DataRow.RowState%2A> von <xref:System.Data.DataRowState.Deleted>.) Alternativ können Sie erstellen eine Datenansicht eines Datasets, die Filter auf die Zeile (Zustand) basieren, und erhalten von dort aus die Count-Eigenschaft.

Das folgende Beispiel zeigt das Aufrufen der <xref:System.Data.DataRow.Delete%2A> Methode zum Kennzeichnen der ersten Zeile in der `Customers` Tabelle als gelöscht:

[!code-csharp[VbRaddataEditing#8](../data-tools/codesnippet/CSharp/edit-data-in-datasets_4.cs)]
[!code-vb[VbRaddataEditing#8](../data-tools/codesnippet/VisualBasic/edit-data-in-datasets_4.vb)]

## <a name="determine-if-there-are-changed-rows"></a>Bestimmen Sie, ob geänderte Zeilen vorhanden sind
Wenn Änderungen an Datensätzen in einem Dataset vorgenommen werden, werden die Informationen zu diesen Änderungen gespeichert, bis ein Commit ausgeführt wird. Übernehmen Sie die Änderungen beim Aufrufen der `AcceptChanges` -Methode von einem Dataset oder eine Datentabelle oder beim Aufrufen der `Update` -Methode eines TableAdapter oder Datenadapters.

Änderungen sind nachverfolgte zwei Möglichkeiten für jede Datenzeile:

-   Jede Datenzeile enthält Informationen, die im Zusammenhang mit der <xref:System.Data.DataRow.RowState%2A> (z. B. <xref:System.Data.DataRowState.Added>, <xref:System.Data.DataRowState.Modified>, <xref:System.Data.DataRowState.Deleted>, oder <xref:System.Data.DataRowState.Unchanged>).

-   Jede geänderte Datenzeile enthält mehrere Versionen der Zeile (<xref:System.Data.DataRowVersion>), die Originalversion (vor der Änderung) und die aktuelle Version (nach der Änderung). Während des Zeitraums, wenn eine Änderung aussteht (die Zeit, wenn Sie auf reagieren, die <xref:System.Data.DataTable.RowChanging> Ereignis), eine dritte Version – die vorläufige Version – ist ebenfalls verfügbar.

Wenn das Dataset geändert wurde, gibt die <xref:System.Data.DataSet.HasChanges%2A>-Methode eines Datasets den Wert `true` zurück. Nachdem festgestellt wurde, dass geänderte Zeilen vorhanden sind, können Sie die `GetChanges`-Methode eines <xref:System.Data.DataSet> oder einer <xref:System.Data.DataTable> aufrufen, um die Gruppe der geänderten Zeilen zurückzugeben.

#### <a name="to-determine-if-changes-have-been-made-to-any-rows"></a>Um festzustellen, ob Änderungen an den Zeilen vorgenommen wurden

-   Rufen Sie die <xref:System.Data.DataSet.HasChanges%2A>-Methode eines Datasets auf, um geänderte Zeilen zu suchen.

Das folgende Beispiel zeigt, wie Sie den Rückgabewert überprüfen die <xref:System.Data.DataSet.HasChanges%2A> -Methode feststellen, ob geänderten Zeilen vorhanden, in einem Dataset mit dem Namen sind `NorthwindDataset1`:

[!code-csharp[VbRaddataEditing#12](../data-tools/codesnippet/CSharp/edit-data-in-datasets_5.cs)]
[!code-vb[VbRaddataEditing#12](../data-tools/codesnippet/VisualBasic/edit-data-in-datasets_5.vb)]

## <a name="determine-the-type-of-changes"></a>Bestimmen Sie den Typ der Änderungen
Sie können auch überprüfen, um festzustellen, welche Art von Änderungen wurden in einem Dataset durch Übergeben eines Werts aus der <xref:System.Data.DataRowState> Enumeration, um die <xref:System.Data.DataSet.HasChanges%2A> Methode.

#### <a name="to-determine-what-type-of-changes-have-been-made-to-a-row"></a>So stellen Sie fest, welche Art von Änderungen an einer Zeile vorgenommen wurden

-   Übergeben Sie einen <xref:System.Data.DataRowState>-Wert an die <xref:System.Data.DataSet.HasChanges%2A>-Methode.

Das folgende Beispiel zeigt, wie Sie ein Dataset namens überprüfen `NorthwindDataset1` zu bestimmen, ob alle neuen Zeilen zuerst darauf hinzugefügt wurden:

[!code-csharp[VbRaddataEditing#13](../data-tools/codesnippet/CSharp/edit-data-in-datasets_6.cs)]
[!code-vb[VbRaddataEditing#13](../data-tools/codesnippet/VisualBasic/edit-data-in-datasets_6.vb)]

## <a name="to-locate-rows-that-have-errors"></a>Um Zeilen zu finden, die Fehler enthalten
Bei der Arbeit mit einzelnen Spalten und Zeilen mit Daten können Fehler auftreten. Sehen Sie sich die `HasErrors` Eigenschaft, um zu bestimmen, ob Fehler vorhanden, in sind einem <xref:System.Data.DataSet>, <xref:System.Data.DataTable>, oder <xref:System.Data.DataRow>.

1.  Überprüfen Sie die `HasErrors` Eigenschaft, um festzustellen, ob Fehler im Dataset vorhanden sind.

2.  Wenn die `HasErrors` -Eigenschaft ist `true`, durchlaufen die Auflistungen von Tabellen, und klicken Sie dann die mit die Zeilen, die Zeile mit dem Fehler finden.

[!code-csharp[VbRaddataEditing#23](../data-tools/codesnippet/CSharp/edit-data-in-datasets_7.cs)]
[!code-vb[VbRaddataEditing#23](../data-tools/codesnippet/VisualBasic/edit-data-in-datasets_7.vb)]

## <a name="see-also"></a>Siehe auch

- [Datasettools in Visual Studio](../data-tools/dataset-tools-in-visual-studio.md)