---
title: Bearbeiten von Daten in Datasets | Microsoft Docs
ms.custom: ''
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
ms.technology: vs-data-tools
ms.workload:
- data-storage
ms.openlocfilehash: a72949ad06b9140faa3e5013a8fd07e98b4db172
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/16/2018
---
# <a name="edit-data-in-datasets"></a>Bearbeiten von Daten in datasets
Ähnlich wie die Daten in einer Tabelle in einer Datenbank zu bearbeiten, bearbeiten Sie die Daten in Datentabellen. Der Prozess kann enthalten, einfügen, aktualisieren und Löschen von Datensätzen in der Tabelle. In einem datengebundenen Formular können Sie angeben, welche Felder Benutzer bearbeitet werden. In diesen Fällen behandelt die Infrastruktur für die Datenbindung alle der änderungsnachverfolgung, damit die Änderungen später wieder in die Datenbank gesendet werden können. Wenn Sie programmgesteuert Bearbeitungen, um Daten vornehmen und die Änderungen zurück an die Datenbank gesendet werden sollen, müssen Sie verwenden, die Objekte und Methoden, die die änderungsnachverfolgung für Sie übernimmt.  
  
Sie können auch Abfragen, zusätzlich zum Ändern der tatsächlichen Daten, eine <xref:System.Data.DataTable> bestimmte Datenzeilen zurückgegeben. Beispielsweise können Sie Abfragen für einzelne Zeilen, bestimmte Versionen von Zeilen (ursprüngliche und vorgesehene), geänderte Zeilen oder Zeilen mit Fehlern.  
  
## <a name="to-edit-rows-in-a-dataset"></a>So bearbeiten Sie die Zeilen in einem dataset  
So bearbeiten Sie eine vorhandene Zeile in einer <xref:System.Data.DataTable>, müssen Sie zum Suchen der <xref:System.Data.DataRow> Sie bearbeiten, und klicken Sie dann die gewünschten Spalten die aktualisierten Werte zuweisen möchten.  
  
Wenn Sie nicht, dass den Index der Zeile wissen möchten Sie bearbeiten, verwenden Sie die `FindBy` Methode, durch den primären Schlüssel gesucht werden soll:  
  
[!code-csharp[VbRaddataEditing#3](../data-tools/codesnippet/CSharp/edit-data-in-datasets_1.cs)]
[!code-vb[VbRaddataEditing#3](../data-tools/codesnippet/VisualBasic/edit-data-in-datasets_1.vb)]  
  
Wenn Sie wissen, dass der Index der Zeile, Sie können auf zugreifen und Zeilen wie folgt bearbeitet:  
  
[!code-csharp[VbRaddataEditing#5](../data-tools/codesnippet/CSharp/edit-data-in-datasets_2.cs)]
[!code-vb[VbRaddataEditing#5](../data-tools/codesnippet/VisualBasic/edit-data-in-datasets_2.vb)]  
  
## <a name="to-insert-new-rows-into-a-dataset"></a>So fügen Sie ein Dataset neue Zeilen  
Anwendungen, die von datengebundenen Steuerelementen in der Regel verwenden neue Datensätze durch Hinzufügen der **hinzufügen** auf die Schaltfläche ein [BindingNavigator-Steuerelement](/dotnet/framework/winforms/controls/bindingnavigator-control-windows-forms).  
  
Um neue Datensätze zu einem Dataset manuell hinzuzufügen, erstellen Sie eine neue Datenzeile durch Aufrufen der Methode in das DataTable-Objekt. Fügen Sie dann auf die Zeile an die <xref:System.Data.DataRow> Auflistung (<xref:System.Data.DataTable.Rows%2A>) von der <xref:System.Data.DataTable>:  
  
[!code-csharp[VbRaddataEditing#1](../data-tools/codesnippet/CSharp/edit-data-in-datasets_3.cs)]
[!code-vb[VbRaddataEditing#1](../data-tools/codesnippet/VisualBasic/edit-data-in-datasets_3.vb)]  
  
Um die Daten beizubehalten, dass das Dataset Updates mit der Datenquelle zu senden muss, verwenden die <xref:System.Data.DataRow.Delete%2A> Methode, um Zeilen in einer Datentabelle zu entfernen. Angenommen, Ihre Anwendung einen TableAdapter verwendet (oder <xref:System.Data.Common.DataAdapter>), TableAdapters `Update` Methode löscht Zeilen in der Datenbank mit einer <xref:System.Data.DataRow.RowState%2A> von <xref:System.Data.DataRowState.Deleted>.  
  
Wenn Ihre Anwendung nicht zum Senden von Updates an einer Datenquelle erforderlich ist, dann es ist möglich, Datensätze zu entfernen, indem Sie direkten Zugriff auf die datenzeilenauflistung (<xref:System.Data.DataRowCollection.Remove%2A>).  
  
#### <a name="to-delete-records-from-a-data-table"></a>Zum Löschen von Datensätzen aus einer Datentabelle  
  
-   Rufen Sie die <xref:System.Data.DataRow.Delete%2A> Methode von einer <xref:System.Data.DataRow>.  
  
     Diese Methode den Datensatz nicht physisch entfernt werden. Stattdessen wird es der Datensatz für die Löschung gekennzeichnet.  
  
    > [!NOTE]
    >  Wenn Sie die Count-Eigenschaft des erhalten eine <xref:System.Data.DataRowCollection>, das Rekursionsergebnis enthält Datensätze, die zum Löschen markiert wurden. Um eine genaue Anzahl von Datensätzen zu erhalten, die für die Löschung markiert werden, können Sie eine Schleife durch die Auflistung der <xref:System.Data.DataRow.RowState%2A> Eigenschaft jedes Datensatzes. (Zum Löschen markierte Einträge enthalten eine <xref:System.Data.DataRow.RowState%2A> von <xref:System.Data.DataRowState.Deleted>.) Alternativ können Sie Erstellen einer Datenansicht eines Datasets, auf denen Zeilenstatus Filter basiert und die Count-Eigenschaft von dort abrufen.  
  
Im folgende Beispiel wird gezeigt, wie zum Aufrufen der <xref:System.Data.DataRow.Delete%2A> Methode zum Kennzeichnen der ersten Zeile in der `Customers` Tabelle als gelöscht:  
  
[!code-csharp[VbRaddataEditing#8](../data-tools/codesnippet/CSharp/edit-data-in-datasets_4.cs)]
[!code-vb[VbRaddataEditing#8](../data-tools/codesnippet/VisualBasic/edit-data-in-datasets_4.vb)]  
  
## <a name="determine-if-there-are-changed-rows"></a>Bestimmen Sie, ob geänderte Zeilen vorhanden sind  
Wenn Änderungen an Datensätzen in einem Dataset vorgenommen werden, werden die Informationen zu diesen Änderungen gespeichert, bis ein Commit ausgeführt wird. Wenn Sie aufrufen, übertragen Sie die Änderungen der `AcceptChanges` Methode einer Datasets oder einer Tabelle oder beim Aufrufen der `Update` -Methode eines TableAdapter oder Datenadapters.  
  
Änderungen für nachverfolgte zweierlei in jeder Datenzeile:  
  
-   Jede Datenzeile enthält Informationen, die im Zusammenhang mit der <xref:System.Data.DataRow.RowState%2A> (z. B. <xref:System.Data.DataRowState.Added>, <xref:System.Data.DataRowState.Modified>, <xref:System.Data.DataRowState.Deleted>, oder <xref:System.Data.DataRowState.Unchanged>).  
  
-   Jede geänderte Datenzeile enthält mehrere Versionen der betreffenden Zeile (<xref:System.Data.DataRowVersion>), die ursprüngliche Version (vor den Änderungen) und die aktuelle Version (nach den Änderungen). Während des Zeitraums, wenn eine Änderung aussteht (die Zeit, wenn Sie auf reagieren können, die <xref:System.Data.DataTable.RowChanging> Ereignis), eine dritte Version – die vorläufige Version – ist verfügbar. 
  
Wenn das Dataset geändert wurde, gibt die <xref:System.Data.DataSet.HasChanges%2A>-Methode eines Datasets den Wert `true` zurück. Nachdem festgestellt wurde, dass geänderte Zeilen vorhanden sind, können Sie die `GetChanges`-Methode eines <xref:System.Data.DataSet> oder einer <xref:System.Data.DataTable> aufrufen, um die Gruppe der geänderten Zeilen zurückzugeben.   
  
#### <a name="to-determine-if-changes-have-been-made-to-any-rows"></a>Um festzustellen, ob Änderungen an den Zeilen vorgenommen wurden  
  
-   Rufen Sie die <xref:System.Data.DataSet.HasChanges%2A>-Methode eines Datasets auf, um geänderte Zeilen zu suchen.  
  
Das folgende Beispiel zeigt, wie den Rückgabewert überprüft die <xref:System.Data.DataSet.HasChanges%2A> -Methode feststellen, ob alle geänderten Zeilen vorhanden, in einem Dataset mit dem Namen sind `NorthwindDataset1`:  
  
[!code-csharp[VbRaddataEditing#12](../data-tools/codesnippet/CSharp/edit-data-in-datasets_5.cs)]
[!code-vb[VbRaddataEditing#12](../data-tools/codesnippet/VisualBasic/edit-data-in-datasets_5.vb)]  
  
## <a name="determine-the-type-of-changes"></a>Bestimmen Sie die Art der Änderungen  
Sie können auch überprüfen, um festzustellen, welche Art von Änderungen vorgenommen wurden in einem Dataset durch Übergeben eines Werts aus der <xref:System.Data.DataRowState> -Enumeration der <xref:System.Data.DataSet.HasChanges%2A> Methode.  
  
#### <a name="to-determine-what-type-of-changes-have-been-made-to-a-row"></a>So stellen Sie fest, welche Art von Änderungen an einer Zeile vorgenommen wurden  
  
-   Übergeben Sie einen <xref:System.Data.DataRowState>-Wert an die <xref:System.Data.DataSet.HasChanges%2A>-Methode.  
  
Das folgende Beispiel zeigt, wie Sie ein Dataset namens `NorthwindDataset1` zu bestimmen, ob sie alle neuen Zeilen hinzugefügt wurden:  
  
[!code-csharp[VbRaddataEditing#13](../data-tools/codesnippet/CSharp/edit-data-in-datasets_6.cs)]
[!code-vb[VbRaddataEditing#13](../data-tools/codesnippet/VisualBasic/edit-data-in-datasets_6.vb)]  
  
## <a name="to-locate-rows-that-have-errors"></a>Um Zeilen zu suchen, die Fehler enthalten  
Bei der Arbeit mit den einzelnen Spalten und Zeilen mit Daten können Fehler auftreten. Sehen Sie sich die `HasErrors` Eigenschaft, um zu bestimmen, ob Fehler vorhanden, in sind einem <xref:System.Data.DataSet>, <xref:System.Data.DataTable>, oder <xref:System.Data.DataRow>.  
  
1.  Überprüfen Sie die `HasErrors` Eigenschaft, um festzustellen, ob Fehler im Dataset vorhanden sind.  
  
2.  Wenn die `HasErrors` Eigenschaft ist `true`, durchlaufen die Auflistungen von Tabellen, und klicken Sie dann das mit die Zeilen, die Zeile mit dem Fehler finden.  

[!code-csharp[VbRaddataEditing#23](../data-tools/codesnippet/CSharp/edit-data-in-datasets_7.cs)]
[!code-vb[VbRaddataEditing#23](../data-tools/codesnippet/VisualBasic/edit-data-in-datasets_7.vb)]

## <a name="see-also"></a>Siehe auch
[Datasettools in Visual Studio](../data-tools/dataset-tools-in-visual-studio.md)