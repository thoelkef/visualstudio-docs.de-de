---
title: Bearbeiten von Daten in Datasets | Microsoft-Dokumentation
ms.custom: ''
ms.date: 11/15/2016
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
- datasets [Visual Basic], editing data
- data [Visual Studio], editing in datasets
ms.assetid: 50d5c580-fbf7-408f-be70-e63ac4f4d0eb
caps.latest.revision: 18
author: gewarren
ms.author: gewarren
manager: ghogen
ms.openlocfilehash: c4a24b088922de30f421621a5f367287b84e3ddc
ms.sourcegitcommit: 9ceaf69568d61023868ced59108ae4dd46f720ab
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 10/12/2018
ms.locfileid: "49184846"
---
# <a name="edit-data-in-datasets"></a>Bearbeiten von Daten in Datasets
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

  
Ähnlich wie Sie die Daten in einer Tabelle in einer beliebigen Datenbank bearbeiten, bearbeiten Sie die Daten in Tabellen. Der Prozess kann enthalten, einfügen, aktualisieren und Löschen von Datensätzen in der Tabelle. In einem datengebundenen Formular können Sie angeben, welche Felder Benutzer bearbeitbare sind. In diesen Fällen behandelt die Infrastruktur für die Datenbindung an, alle der änderungsnachverfolgung, damit die Änderungen später an die Datenbank gesendet werden können. Wenn Sie programmgesteuert Änderungen an Daten vornehmen und diese Änderungen an die Datenbank gesendet werden sollen, müssen Sie verwenden die Objekte und Methoden, die die änderungsnachverfolgung für die Sie ausführen.  
  
 Sie können auch Abfragen, zusätzlich zum Ändern der tatsächlichen Daten, eine <xref:System.Data.DataTable> um bestimmte Datenzeilen zurückzugeben. Beispielsweise können Sie Abfragen für einzelne Zeilen, bestimmte Versionen von Zeilen (ursprüngliche und vorgesehene), geänderte Zeilen oder Zeilen mit Fehlern.  
  
## <a name="to-edit-rows-in-a-dataset"></a>So bearbeiten Sie die Zeilen in einem dataset  
 So bearbeiten Sie eine vorhandene Zeile in einer <xref:System.Data.DataTable>, gesucht werden soll die <xref:System.Data.DataRow> bearbeiten, und klicken Sie dann die gewünschten Spalten die aktualisierten Werte zuweisen möchten.  
  
 Wenn Sie nicht, dass den Index der Zeile wissen soll, bearbeiten, verwenden Sie die `FindBy` Methode zum Suchen nach dem Primärschlüssel:  
  
 [!code-csharp[VbRaddataEditing#3](../snippets/csharp/VS_Snippets_VBCSharp/VbRaddataEditing/CS/Form1.cs#3)]
 [!code-vb[VbRaddataEditing#3](../snippets/visualbasic/VS_Snippets_VBCSharp/VbRaddataEditing/VB/Form1.vb#3)]  
  
 Wenn Sie wissen, dass der Index der Zeile, Sie können auf zugreifen und Zeilen wie folgt bearbeitet:  
  
 [!code-csharp[VbRaddataEditing#5](../snippets/csharp/VS_Snippets_VBCSharp/VbRaddataEditing/CS/Form1.cs#5)]
 [!code-vb[VbRaddataEditing#5](../snippets/visualbasic/VS_Snippets_VBCSharp/VbRaddataEditing/VB/Form1.vb#5)]  
  
## <a name="to-insert-new-rows-into-a-dataset"></a>Um neue Zeilen in ein Dataset einfügen  
 Anwendungen, die von datengebundenen Steuerelementen in der Regel verwenden neue Datensätze durch Hinzufügen der **Add New** Schaltfläche eine [BindingNavigator-Steuerelement](http://msdn.microsoft.com/library/18c1e2a5-9834-40d3-9b2e-2b545e4e769e).  
  
 Um neue Datensätze zu einem Dataset manuell hinzuzufügen, erstellen Sie eine neue Datenzeile durch Aufrufen der Methode in der DataTable-Objekt. Klicken Sie dann die Zeile zum Hinzufügen der <xref:System.Data.DataRow> Auflistung (<xref:System.Data.DataTable.Rows%2A>) von der <xref:System.Data.DataTable>:  
  
 [!code-csharp[VbRaddataEditing#1](../snippets/csharp/VS_Snippets_VBCSharp/VbRaddataEditing/CS/Form1.cs#1)]
 [!code-vb[VbRaddataEditing#1](../snippets/visualbasic/VS_Snippets_VBCSharp/VbRaddataEditing/VB/Form1.vb#1)]  
  
 Um die Daten beizubehalten, dass das Dataset Updates an der Datenquelle zu senden muss, verwenden Sie die <xref:System.Data.DataRow.Delete%2A> Methode, um Zeilen in einer Datentabelle zu entfernen. Wenn Ihre Anwendung einen TableAdapter verwendet z. B. (oder <xref:System.Data.Common.DataAdapter>), TableAdapters `Update` Methode löscht Zeilen in der Datenbank, die eine <xref:System.Data.DataRow.RowState%2A> von <xref:System.Data.DataRowState>.  
  
 Wenn Ihre Anwendung nicht zum Senden von Updates in einer Datenquelle erforderlich ist, klicken Sie dann es ist möglich, Datensätze durch direkten Zugriff auf die Datensammlung für die Zeile zu entfernen (<xref:System.Data.DataRowCollection.Remove%2A>).  
  
#### <a name="to-delete-records-from-a-data-table"></a>Zum Löschen von Datensätzen aus einer Datentabelle  
  
-   Rufen Sie die <xref:System.Data.DataRow.Delete%2A> Methode eine <xref:System.Data.DataRow>.  
  
     Diese Methode den Datensatz nicht physisch entfernt werden. Stattdessen wird den Datensatz für die Löschung markiert.  
  
    > [!NOTE]
    >  Wenn Sie die Count-Eigenschaft des erhalten eine <xref:System.Data.DataRowCollection>, das Rekursionsergebnis enthält Datensätze, die für die Löschung markiert wurden. Um eine genaue Anzahl der Datensätze zu erhalten, die zum Löschen markiert sind nicht, können Sie eine Schleife mit dem Blick auf die Auflistung der <xref:System.Data.DataRow.RowState%2A> Eigenschaft jedes Datensatzes. (Zum Löschen markierte Einträge enthalten ein <xref:System.Data.DataRow.RowState%2A> von <xref:System.Data.DataRowState>.) Alternativ können Sie erstellen eine Datenansicht eines Datasets, die Filter auf die Zeile (Zustand) basieren, und erhalten von dort aus die Count-Eigenschaft.  
  
     Das folgende Beispiel zeigt das Aufrufen der <xref:System.Data.DataRow.Delete%2A> Methode zum Kennzeichnen der ersten Zeile in der `Customers` Tabelle als gelöscht:  
  
     [!code-csharp[VbRaddataEditing#8](../snippets/csharp/VS_Snippets_VBCSharp/VbRaddataEditing/CS/Form1.cs#8)]
     [!code-vb[VbRaddataEditing#8](../snippets/visualbasic/VS_Snippets_VBCSharp/VbRaddataEditing/VB/Form1.vb#8)]  
  
## <a name="determine-if-there-are-changed-rows"></a>Bestimmen Sie, ob geänderte Zeilen vorhanden sind  
 Wenn Änderungen an Datensätzen in einem Dataset vorgenommen werden, werden die Informationen zu diesen Änderungen gespeichert, bis ein Commit ausgeführt wird. Übernehmen Sie die Änderungen beim Aufrufen der `AcceptChanges` -Methode von einem Dataset oder eine Datentabelle oder beim Aufrufen der `Update` -Methode eines TableAdapter oder Datenadapters.  
  
 Änderungen sind nachverfolgte zwei Möglichkeiten für jede Datenzeile:  
  
-   Jede Datenzeile enthält Informationen zu dessen <xref:System.Data.DataRow.RowState%2A> (z. B. <xref:System.Data.DataRowState>, <xref:System.Data.DataRowState>, <xref:System.Data.DataRowState>, oder <xref:System.Data.DataRowState>).  
  
-   Jede geänderte Datenzeile enthält mehrere Versionen der Zeile (<xref:System.Data.DataRowVersion>), die Originalversion (vor der Änderung), und die aktuelle Version (nach der Änderung). Während des Zeitraums, wenn eine Änderung aussteht (die Zeit, wenn Sie auf reagieren, die <xref:System.Data.DataTable.RowChanging> Ereignis), eine dritte Version – die vorläufige Version – ist ebenfalls verfügbar. Weitere Informationen finden Sie unter [Vorgehensweise: Abrufen spezifischer Versionen einer DataRow](../data-tools/how-to-get-specific-versions-of-a-datarow.md).  
  
 Wenn das Dataset geändert wurde, gibt die <xref:System.Data.DataSet.HasChanges%2A>-Methode eines Datasets den Wert `true` zurück. Nachdem festgestellt wurde, dass geänderte Zeilen vorhanden sind, können Sie die `GetChanges`-Methode eines <xref:System.Data.DataSet> oder einer <xref:System.Data.DataTable> aufrufen, um die Gruppe der geänderten Zeilen zurückzugeben. Weitere Informationen finden Sie unter [Vorgehensweise: Abrufen von geänderten Zeilen](http://msdn.microsoft.com/library/6ff0cbd0-5253-48e7-888a-144d56c2e0a9).  
  
#### <a name="to-determine-if-changes-have-been-made-to-any-rows"></a>Um festzustellen, ob Änderungen an den Zeilen vorgenommen wurden  
  
-   Rufen Sie die <xref:System.Data.DataSet.HasChanges%2A>-Methode eines Datasets auf, um geänderte Zeilen zu suchen.  
  
     Das folgende Beispiel zeigt, wie Sie den Rückgabewert überprüfen die <xref:System.Data.DataSet.HasChanges%2A> -Methode feststellen, ob geänderten Zeilen vorhanden, in einem Dataset mit dem Namen sind `NorthwindDataset1`:  
  
     [!code-csharp[VbRaddataEditing#12](../snippets/csharp/VS_Snippets_VBCSharp/VbRaddataEditing/CS/Form1.cs#12)]
     [!code-vb[VbRaddataEditing#12](../snippets/visualbasic/VS_Snippets_VBCSharp/VbRaddataEditing/VB/Form1.vb#12)]  
  
## <a name="determine-the-type-of-changes"></a>Bestimmen Sie den Typ der Änderungen  
 Sie können auch überprüfen, um festzustellen, welche Art von Änderungen wurden in einem Dataset durch Übergeben eines Werts aus der <xref:System.Data.DataRowState> Enumeration, um die <xref:System.Data.DataSet.HasChanges%2A> Methode.  
  
#### <a name="to-determine-what-type-of-changes-have-been-made-to-a-row"></a>So stellen Sie fest, welche Art von Änderungen an einer Zeile vorgenommen wurden  
  
-   Übergeben Sie einen <xref:System.Data.DataRowState>-Wert an die <xref:System.Data.DataSet.HasChanges%2A>-Methode.  
  
     Das folgende Beispiel zeigt, wie Sie ein Dataset namens überprüfen `NorthwindDataset1` zu bestimmen, ob alle neuen Zeilen zuerst darauf hinzugefügt wurden:  
  
     [!code-csharp[VbRaddataEditing#13](../snippets/csharp/VS_Snippets_VBCSharp/VbRaddataEditing/CS/Form1.cs#13)]
     [!code-vb[VbRaddataEditing#13](../snippets/visualbasic/VS_Snippets_VBCSharp/VbRaddataEditing/VB/Form1.vb#13)]  
  
## <a name="to-locate-rows-that-have-errors"></a>Um Zeilen zu finden, die Fehler enthalten  
 Bei der Arbeit mit einzelnen Spalten und Zeilen mit Daten können Fehler auftreten. Sehen Sie sich die `HasErrors` Eigenschaft, um zu bestimmen, ob Fehler vorhanden, in sind einem <xref:System.Data.DataSet>, <xref:System.Data.DataTable>, oder <xref:System.Data.DataRow>.  
  
1.  Überprüfen Sie die `HasErrors` Eigenschaft, um festzustellen, ob Fehler im Dataset vorhanden sind.  
  
2.  Wenn die `HasErrors` -Eigenschaft ist `true`, durchlaufen die Auflistungen von Tabellen, und klicken Sie dann die mit die Zeilen, die Zeile mit dem Fehler finden.  
  
     [!code-csharp[VbRaddataEditing#23](../snippets/csharp/VS_Snippets_VBCSharp/VbRaddataEditing/CS/Form1.cs#23)]
     [!code-vb[VbRaddataEditing#23](../snippets/visualbasic/VS_Snippets_VBCSharp/VbRaddataEditing/VB/Form1.vb#23)]

