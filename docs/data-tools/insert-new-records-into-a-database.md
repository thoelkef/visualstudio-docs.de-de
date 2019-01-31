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
author: gewarren
ms.author: gewarren
manager: jillfra
ms.prod: visual-studio-dev15
ms.workload:
- data-storage
ms.openlocfilehash: de9da74b8760a15ac55d5339aacacdd89deaef28
ms.sourcegitcommit: 2193323efc608118e0ce6f6b2ff532f158245d56
ms.translationtype: MTE95
ms.contentlocale: de-DE
ms.lasthandoff: 01/25/2019
ms.locfileid: "54966337"
---
# <a name="insert-new-records-into-a-database"></a>Einfügen neuer Datensätze in eine Datenbank

Zum Einfügen neuer Datensätze in einer Datenbank können Sie die `TableAdapter.Update` Methode oder eines der TableAdapter-DBDirect-Methoden (insbesondere die `TableAdapter.Insert` Methode). Weitere Informationen finden Sie unter [TableAdapter](../data-tools/create-and-configure-tableadapters.md).

Wenn Ihre Anwendung TableAdapters nicht verwendet werden, können Sie Befehlsobjekte verwenden (z. B. <xref:System.Data.SqlClient.SqlCommand>) zum Einfügen neuer Datensätze in der Datenbank.

Wenn Ihre Anwendung Datasets verwendet, um Daten zu speichern, verwenden Sie die `TableAdapter.Update` Methode. Die `Update` Methode sendet alle Änderungen (Updates, einfügungen und löschungen), mit der Datenbank.

Wenn Ihre Anwendung Objekte verwendet, Daten, oder speichern eine genauere Steuerung der Erstellung neuer Datensätze in der Datenbank, verwenden Sie die `TableAdapter.Insert` Methode.

Wenn keine der TableAdapter eine `Insert` -Methode, es bedeutet, dass entweder der TableAdapter konfiguriert ist, um gespeicherte Prozeduren zu verwenden oder den zugehörigen `GenerateDBDirectMethods` -Eigenschaftensatz auf `false`. Legen Sie der TableAdapters `GenerateDBDirectMethods` Eigenschaft `true` innerhalb der **Dataset-Designer**, und speichern Sie das Dataset. Hierdurch wird den TableAdapter neu generiert. Wenn der TableAdapter immer noch kein `Insert` -Methode in der Tabelle wahrscheinlich bietet keine ausreichende Schemainformationen zur Unterscheidung zwischen den einzelnen Zeilen (z. B. möglicherweise keine primären Schlüsselsatz für die Tabelle).

## <a name="insert-new-records-by-using-tableadapters"></a>Fügen Sie neue Datensätze mit TableAdapters

TableAdapters bieten verschiedene Möglichkeiten zum Einfügen neuer Datensätze in einer Datenbank, abhängig von den Anforderungen Ihrer Anwendung.

Wenn Ihre Anwendung Datasets verwendet, um Daten zu speichern, können Sie einfach neue Datensätze hinzufügen, um die gewünschte <xref:System.Data.DataTable> in das Dataset, und rufen Sie dann die `TableAdapter.Update` Methode. Die `TableAdapter.Update` Methode sendet die Änderungen in der <xref:System.Data.DataTable> in der Datenbank (einschließlich geänderte und gelöschte Datensätze).

### <a name="to-insert-new-records-into-a-database-by-using-the-tableadapterupdate-method"></a>Zum Einfügen neuer Datensätze in einer Datenbank mithilfe der TableAdapter.Update-Methode

1. Neue Datensätze hinzufügen, um die gewünschte <xref:System.Data.DataTable> durch Erstellen eines neuen <xref:System.Data.DataRow> und zum Hinzufügen der <xref:System.Data.DataTable.Rows%2A> Auflistung.

2. Nachdem die neuen Zeilen hinzugefügt wurden die <xref:System.Data.DataTable>, rufen Sie die `TableAdapter.Update` Methode. Sie können steuern, die Menge der Daten zu aktualisieren, indem Sie entweder eine gesamte übergeben <xref:System.Data.DataSet>, <xref:System.Data.DataTable>, ein Array von <xref:System.Data.DataRow>s oder eine einzelne <xref:System.Data.DataRow>.

   Der folgende Code zeigt, wie Sie einen neuen Eintrag Hinzufügen einer <xref:System.Data.DataTable> und rufen Sie dann die `TableAdapter.Update` Methode, um die neue Zeile in der Datenbank zu speichern. (Dieses Beispiel verwendet die `Region` Tabelle in der Northwind-Datenbank.)

   [!code-vb[VbRaddataSaving#14](../data-tools/codesnippet/VisualBasic/insert-new-records-into-a-database_1.vb)]
   [!code-csharp[VbRaddataSaving#14](../data-tools/codesnippet/CSharp/insert-new-records-into-a-database_1.cs)]

### <a name="to-insert-new-records-into-a-database-by-using-the-tableadapterinsert-method"></a>Zum Einfügen neuer Datensätze in einer Datenbank mithilfe der TableAdapter.Insert-Methode

Wenn Ihre Anwendung Objekte verwendet, um Daten zu speichern, können Sie mithilfe der `TableAdapter.Insert` Methode, um neue Zeilen direkt in der Datenbank zu erstellen. Die `Insert` -Methode akzeptiert die einzelnen Werte für jede Spalte als Parameter. Aufrufen der Methode fügt einen neuen Datensatz in die Datenbank mit der übergebenen Parameterwerte.

- Rufen Sie die `Insert` -Methode, die Werte für jede Spalte als Parameter übergeben.

Das folgende Verfahren veranschaulicht die Verwendung der `TableAdapter.Insert` Methode zum Einfügen von Zeilen. In diesem Beispiel fügt Daten in die `Region` Tabelle in der Northwind-Datenbank.

> [!NOTE]
> Wenn Sie nicht über eine verfügbare Instanz verfügen, instanziieren Sie den TableAdapter, die Sie verwenden möchten.

[!code-vb[VbRaddataSaving#15](../data-tools/codesnippet/VisualBasic/insert-new-records-into-a-database_2.vb)]
[!code-csharp[VbRaddataSaving#15](../data-tools/codesnippet/CSharp/insert-new-records-into-a-database_2.cs)]

## <a name="insert-new-records-by-using-command-objects"></a>Fügen Sie neue Datensätze mit Befehlsobjekte

Sie können neue Datensätze einfügen, direkt in eine Datenbank mithilfe von Befehlsobjekten.

### <a name="to-insert-new-records-into-a-database-by-using-command-objects"></a>Zum Einfügen neuer Datensätze in einer Datenbank mithilfe von Befehlsobjekten

- Erstellen Sie ein neues Befehlsobjekt aus, und legen Sie dann die `Connection`, `CommandType`, und `CommandText` Eigenschaften.

Das folgende Beispiel zeigt Einfügen von Datensätzen in eine Datenbank mithilfe der Command-Objekt. Es fügt Daten in die `Region` Tabelle in der Northwind-Datenbank.

[!code-vb[VbRaddataSaving#16](../data-tools/codesnippet/VisualBasic/insert-new-records-into-a-database_3.vb)]
[!code-csharp[VbRaddataSaving#16](../data-tools/codesnippet/CSharp/insert-new-records-into-a-database_3.cs)]

## <a name="net-framework-security"></a>.NET Framework-Sicherheit

Benötigen Sie Zugriff auf die Datenbank, die Sie herstellen möchten, sowie Berechtigung zum Durchführen von einfügungen in die gewünschte Tabelle.

## <a name="see-also"></a>Siehe auch

- [Rückspeichern von Daten in der Datenbank](../data-tools/save-data-back-to-the-database.md)