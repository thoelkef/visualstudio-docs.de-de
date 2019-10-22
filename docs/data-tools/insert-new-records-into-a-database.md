---
title: Einfügen neuer Datensätze in eine Datenbank
ms.date: 11/04/2016
ms.topic: conceptual
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- TableAdapters, inserting new records into
- data [Visual Studio], saving
- databases, inserting new records into
- records, inserting
- saving data
ms.assetid: ea118fff-69b1-4675-b79a-e33374377f04
author: jillre
ms.author: jillfra
manager: jillfra
ms.workload:
- data-storage
ms.openlocfilehash: aaca23e6aa81fab958fc813fa5e2331f8906a562
ms.sourcegitcommit: a8e8f4bd5d508da34bbe9f2d4d9fa94da0539de0
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 10/19/2019
ms.locfileid: "72648318"
---
# <a name="insert-new-records-into-a-database"></a>Einfügen neuer Datensätze in eine Datenbank

Wenn Sie neue Datensätze in eine Datenbank einfügen möchten, können Sie die `TableAdapter.Update`-Methode oder eine der DBDirect-Methoden des TableAdapter (insbesondere die `TableAdapter.Insert`-Methode) verwenden. Weitere Informationen finden Sie unter [TableAdapter](../data-tools/create-and-configure-tableadapters.md).

Wenn Ihre Anwendung keine TableAdapters verwendet, können Sie Befehls Objekte (z. b. <xref:System.Data.SqlClient.SqlCommand>) verwenden, um neue Datensätze in die Datenbank einzufügen.

Wenn Ihre Anwendung Datasets verwendet, um Daten zu speichern, verwenden Sie die `TableAdapter.Update`-Methode. Die `Update`-Methode sendet alle Änderungen (Updates, Einfügungen und Löschungen) an die Datenbank.

Wenn Ihre Anwendung Objekte zum Speichern von Daten verwendet, oder wenn Sie eine präzisere Kontrolle über das Erstellen neuer Datensätze in der Datenbank wünschen, verwenden Sie die `TableAdapter.Insert`-Methode.

Wenn Ihr TableAdapter nicht über eine `Insert`-Methode verfügt, bedeutet dies, dass entweder der TableAdapter für die Verwendung gespeicherter Prozeduren konfiguriert ist oder dessen `GenerateDBDirectMethods`-Eigenschaft auf `false` festgelegt ist. Legen Sie die `GenerateDBDirectMethods`-Eigenschaft des TableAdapter auf `true` innerhalb des **DataSet-Designer**fest, und speichern Sie dann das DataSet. Dadurch wird der TableAdapter neu generiert. Wenn der TableAdapter immer noch keine `Insert` Methode hat, bietet die Tabelle wahrscheinlich nicht genügend Schema Informationen, um zwischen einzelnen Zeilen zu unterscheiden (es kann z. b. kein Primärschlüssel für die Tabelle festgelegt werden).

## <a name="insert-new-records-by-using-tableadapters"></a>Einfügen neuer Datensätze mithilfe von TableAdapters

TableAdapters bieten verschiedene Möglichkeiten zum Einfügen neuer Datensätze in eine Datenbank, abhängig von den Anforderungen Ihrer Anwendung.

Wenn Ihre Anwendung Datasets verwendet, um Daten zu speichern, können Sie der gewünschten <xref:System.Data.DataTable> im Dataset einfach neue Datensätze hinzufügen und dann die `TableAdapter.Update`-Methode aufzurufen. Die `TableAdapter.Update`-Methode sendet alle Änderungen im <xref:System.Data.DataTable> an die Datenbank (einschließlich der geänderten und gelöschten Datensätze).

### <a name="to-insert-new-records-into-a-database-by-using-the-tableadapterupdate-method"></a>So fügen Sie mithilfe der TableAdapter. Update-Methode neue Datensätze in eine Datenbank ein

1. Fügen Sie der gewünschten <xref:System.Data.DataTable> neue Datensätze hinzu, indem Sie eine neue <xref:System.Data.DataRow> erstellen und Sie der <xref:System.Data.DataTable.Rows%2A> Auflistung hinzufügen.

2. Nachdem die neuen Zeilen der <xref:System.Data.DataTable> hinzugefügt wurden, können Sie die `TableAdapter.Update`-Methode aufzurufen. Sie können die zu Aktualisier Ende Datenmenge steuern, indem Sie entweder einen vollständigen <xref:System.Data.DataSet>, eine <xref:System.Data.DataTable>, ein Array <xref:System.Data.DataRow>s oder eine einzelne <xref:System.Data.DataRow> übergeben.

   Der folgende Code zeigt, wie ein neuer Datensatz zu einem <xref:System.Data.DataTable> hinzugefügt und anschließend die `TableAdapter.Update`-Methode aufgerufen wird, um die neue Zeile in der Datenbank zu speichern. (In diesem Beispiel wird die `Region` Tabelle in der Northwind-Datenbank verwendet.)

   [!code-vb[VbRaddataSaving#14](../data-tools/codesnippet/VisualBasic/insert-new-records-into-a-database_1.vb)]
   [!code-csharp[VbRaddataSaving#14](../data-tools/codesnippet/CSharp/insert-new-records-into-a-database_1.cs)]

### <a name="to-insert-new-records-into-a-database-by-using-the-tableadapterinsert-method"></a>So fügen Sie mithilfe der TableAdapter. Insert-Methode neue Datensätze in eine Datenbank ein

Wenn Ihre Anwendung Objekte zum Speichern von Daten verwendet, können Sie die `TableAdapter.Insert`-Methode verwenden, um neue Zeilen direkt in der Datenbank zu erstellen. Die `Insert`-Methode akzeptiert die einzelnen Werte für jede Spalte als Parameter. Durch Aufrufen der-Methode wird ein neuer Datensatz in die Datenbank eingefügt, wobei die Parameterwerte übergeben werden.

- Nennen Sie die `Insert`-Methode des TableAdapter, und übergeben Sie die Werte für jede Spalte als Parameter.

Das folgende Verfahren veranschaulicht die Verwendung der `TableAdapter.Insert`-Methode zum Einfügen von Zeilen. In diesem Beispiel werden Daten in die `Region` Tabelle in der Northwind-Datenbank eingefügt.

> [!NOTE]
> Wenn keine Instanz verfügbar ist, instanziieren Sie den TableAdapter, den Sie verwenden möchten.

[!code-vb[VbRaddataSaving#15](../data-tools/codesnippet/VisualBasic/insert-new-records-into-a-database_2.vb)]
[!code-csharp[VbRaddataSaving#15](../data-tools/codesnippet/CSharp/insert-new-records-into-a-database_2.cs)]

## <a name="insert-new-records-by-using-command-objects"></a>Einfügen neuer Datensätze mithilfe von Befehls Objekten

Mithilfe von Befehls Objekten können Sie neue Datensätze direkt in eine Datenbank einfügen.

### <a name="to-insert-new-records-into-a-database-by-using-command-objects"></a>So fügen Sie mithilfe von Befehls Objekten neue Datensätze in eine Datenbank ein

- Erstellen Sie ein neues Befehls Objekt, und legen Sie dann die Eigenschaften `Connection`, `CommandType` und `CommandText` fest.

Im folgenden Beispiel wird veranschaulicht, wie Datensätze mithilfe des Befehls Objekts in eine Datenbank eingefügt werden. Daten werden in die `Region` Tabelle in der Northwind-Datenbank eingefügt.

[!code-vb[VbRaddataSaving#16](../data-tools/codesnippet/VisualBasic/insert-new-records-into-a-database_3.vb)]
[!code-csharp[VbRaddataSaving#16](../data-tools/codesnippet/CSharp/insert-new-records-into-a-database_3.cs)]

## <a name="net-security"></a>.NET-Sicherheit

Sie müssen Zugriff auf die Datenbank haben, mit der Sie eine Verbindung herstellen möchten, sowie die Berechtigung zum Ausführen von Einfügungen in die gewünschte Tabelle.

## <a name="see-also"></a>Siehe auch

- [Rückspeichern von Daten in der Datenbank](../data-tools/save-data-back-to-the-database.md)