---
title: Einfügen neuer Datensätze in eine Datenbank | Microsoft-Dokumentation
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
- TableAdapters, inserting new records into
- data [Visual Studio], saving
- databases, inserting new records into
- records, inserting
- saving data
ms.assetid: ea118fff-69b1-4675-b79a-e33374377f04
caps.latest.revision: 14
author: jillre
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: 3c686a764f42f50a3e59da3e8b37b219ddb7b11c
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 09/02/2020
ms.locfileid: "72651563"
---
# <a name="insert-new-records-into-a-database"></a>Einfügen neuer Datensätze in eine Datenbank
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Wenn Sie neue Datensätze in eine Datenbank einfügen möchten, können Sie die `TableAdapter.Update` -Methode oder eine der DBDirect-Methoden des TableAdapter (insbesondere die- `TableAdapter.Insert` Methode) verwenden.

 Wenn Ihre Anwendung keine TableAdapters verwendet, können Sie Befehls Objekte (z. b.  <xref:System.Data.SqlClient.SqlCommand> ) verwenden, um neue Datensätze in die Datenbank einzufügen.

 Wenn Ihre Anwendung Datasets verwendet, um Daten zu speichern, verwenden Sie die- `TableAdapter.Update` Methode. Die- `Update` Methode sendet alle Änderungen (Updates, Einfügungen und Löschungen) an die Datenbank.

 Wenn Ihre Anwendung Objekte zum Speichern von Daten verwendet oder Sie eine präzisere Kontrolle über das Erstellen neuer Datensätze in der Datenbank wünschen, verwenden Sie die- `TableAdapter.Insert` Methode.

 Wenn der TableAdapter nicht über eine- `Insert` Methode verfügt, bedeutet dies, dass entweder der TableAdapter für die Verwendung gespeicherter Prozeduren konfiguriert ist oder seine- `GenerateDBDirectMethods` Eigenschaft auf festgelegt ist `false` . Legen Sie die-Eigenschaft des TableAdapter in `GenerateDBDirectMethods` `true` der DataSet-Designer auf fest, und speichern Sie dann das DataSet. Dadurch wird der TableAdapter neu generiert. Wenn der TableAdapter immer noch nicht über eine- `Insert` Methode verfügt, bietet die Tabelle wahrscheinlich nicht genügend Schema Informationen, um zwischen einzelnen Zeilen zu unterscheiden (z. b. kann kein Primärschlüssel für die Tabelle festgelegt werden).

## <a name="insert-new-records-by-using-tableadapters"></a>Einfügen neuer Datensätze mithilfe von TableAdapters
 TableAdapters bieten verschiedene Möglichkeiten zum Einfügen neuer Datensätze in eine Datenbank, abhängig von den Anforderungen Ihrer Anwendung.

 Wenn Ihre Anwendung Datasets verwendet, um Daten zu speichern, können Sie einfach neue Datensätze zu den gewünschten <xref:System.Data.DataTable> im DataSet hinzufügen und dann die-Methode aufzurufen `TableAdapter.Update` . Die- `TableAdapter.Update` Methode sendet alle Änderungen im <xref:System.Data.DataTable> an die Datenbank (einschließlich der geänderten und gelöschten Datensätze).

#### <a name="to-insert-new-records-into-a-database-by-using-the-tableadapterupdate-method"></a>So fügen Sie mithilfe der TableAdapter. Update-Methode neue Datensätze in eine Datenbank ein

1. Fügen Sie der gewünschten neue Datensätze hinzu, <xref:System.Data.DataTable> indem Sie ein neues erstellen <xref:System.Data.DataRow> und es der-Auflistung hinzufügen <xref:System.Data.DataTable.Rows%2A> . Weitere Informationen finden Sie unter Gewusst [wie: Hinzufügen von Zeilen zu einer Daten](https://msdn.microsoft.com/library/78ebbb43-c402-49cf-81da-0715289487bf)Tabelle.

2. Nachdem die neuen Zeilen hinzugefügt <xref:System.Data.DataTable> wurden, wird die- `TableAdapter.Update` Methode aufgerufen. Sie können die zu Aktualisier Ende Datenmenge steuern, indem Sie entweder ein gesamtes <xref:System.Data.DataSet> , ein <xref:System.Data.DataTable> , ein Array von <xref:System.Data.DataRow> s oder einen einzelnen übergeben <xref:System.Data.DataRow> .

    Der folgende Code zeigt, wie ein neuer Datensatz zu einem hinzugefügt <xref:System.Data.DataTable> und anschließend die-Methode aufgerufen wird `TableAdapter.Update` , um die neue Zeile in der Datenbank zu speichern. (In diesem Beispiel wird die- `Region` Tabelle in der Northwind-Datenbank verwendet.)

    [!code-csharp[VbRaddataSaving#14](../snippets/csharp/VS_Snippets_VBCSharp/VbRaddataSaving/CS/Form5.cs#14)]
    [!code-vb[VbRaddataSaving#14](../snippets/visualbasic/VS_Snippets_VBCSharp/VbRaddataSaving/VB/Form5.vb#14)]

   Wenn Ihre Anwendung Objekte zum Speichern von Daten verwendet, können Sie die-Methode verwenden, `TableAdapter.Insert` um neue Zeilen direkt in der Datenbank zu erstellen. Die- `Insert` Methode akzeptiert die einzelnen Werte für jede Spalte als Parameter. Durch Aufrufen der-Methode wird ein neuer Datensatz in die Datenbank eingefügt, wobei die Parameterwerte übergeben werden.

   Im folgenden Verfahren wird die- `Region` Tabelle in der Northwind-Datenbank als Beispiel verwendet.

#### <a name="to-insert-new-records-into-a-database-by-using-the-tableadapterinsert-method"></a>So fügen Sie mithilfe der TableAdapter. Insert-Methode neue Datensätze in eine Datenbank ein

- Wenden Sie die-Methode des TableAdapter `Insert` an, und übergeben Sie die Werte für jede Spalte als Parameter.

    > [!NOTE]
    > Wenn keine Instanz verfügbar ist, instanziieren Sie den TableAdapter, den Sie verwenden möchten.

     [!code-csharp[VbRaddataSaving#15](../snippets/csharp/VS_Snippets_VBCSharp/VbRaddataSaving/CS/Class1.cs#15)]
     [!code-vb[VbRaddataSaving#15](../snippets/visualbasic/VS_Snippets_VBCSharp/VbRaddataSaving/VB/Class1.vb#15)]

## <a name="insert-new-records-by-using-command-objects"></a>Einfügen neuer Datensätze mithilfe von Befehls Objekten
 Im folgenden Beispiel werden neue Datensätze mithilfe von Befehls Objekten direkt in eine Datenbank eingefügt.

 Im folgenden Verfahren wird die- `Region` Tabelle in der Northwind-Datenbank als Beispiel verwendet.

#### <a name="to-insert-new-records-into-a-database-by-using-command-objects"></a>So fügen Sie mithilfe von Befehls Objekten neue Datensätze in eine Datenbank ein

- Erstellen Sie ein neues Befehls Objekt, und legen Sie dann die `Connection` `CommandType` Eigenschaften, und fest `CommandText` .

     [!code-csharp[VbRaddataSaving#16](../snippets/csharp/VS_Snippets_VBCSharp/VbRaddataSaving/CS/Class1.cs#16)]
     [!code-vb[VbRaddataSaving#16](../snippets/visualbasic/VS_Snippets_VBCSharp/VbRaddataSaving/VB/Class1.vb#16)]

## <a name="net-framework-security"></a>.NET Framework-Sicherheit
 Sie müssen Zugriff auf die Datenbank haben, mit der Sie eine Verbindung herstellen möchten, sowie die Berechtigung zum Ausführen von Einfügungen in die gewünschte Tabelle.

## <a name="see-also"></a>Weitere Informationen
 [Rückspeichern von Daten in der Datenbank](../data-tools/save-data-back-to-the-database.md)
