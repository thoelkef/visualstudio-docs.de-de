---
title: "Einfügen neuer Datensätze in einer Datenbank | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
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
caps.latest.revision: "11"
author: gewarren
ms.author: gewarren
manager: ghogen
ms.technology: vs-data-tools
ms.openlocfilehash: 2450ed950227b6755b57f20f3520a1e75034aafe
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 10/31/2017
---
# <a name="insert-new-records-into-a-database"></a>Fügen Sie neuer Datensätze in einer Datenbank ein
Zum Einfügen neuer Datensätze in einer Datenbank können Sie die `TableAdapter.Update` -Methode oder eine der DBDirect-Methoden des TableAdapter (insbesondere der `TableAdapter.Insert` Methode). Weitere Informationen finden Sie unter [TableAdapter](../data-tools/create-and-configure-tableadapters.md).  
  
 Wenn Ihre Anwendung nicht TableAdapters verwendet, können Sie Befehlsobjekte verwenden (z. B. <xref:System.Data.SqlClient.SqlCommand>) zum Einfügen neuer Datensätze in der Datenbank.
  
 Wenn Ihre Anwendung Datasets verwendet, um Daten zu speichern, verwenden Sie die `TableAdapter.Update` Methode. Die `Update` -Methode sendet alle Änderungen (Updates, einfügungen und löschungen) an die Datenbank.  
  
 Wenn Ihre Anwendung Objekte verwendet, um Daten zu speichern, oder verwenden Sie ggf. eine genauere Steuerung über das Erstellen neuer Datensätze in der Datenbank die `TableAdapter.Insert` Methode.  
  
 Wenn keine der TableAdapter eine `Insert` -Methode, dies bedeutet, dass entweder die TableAdapter konfiguriert ist, um gespeicherte Prozeduren oder den zugehörigen `GenerateDBDirectMethods` -Eigenschaftensatz auf `false`. Festlegen des TableAdapter versuchen `GenerateDBDirectMethods` Eigenschaft `true` innerhalb der **Dataset-Designer**, und speichern Sie das Dataset. Dadurch wird der TableAdapter neu generiert werden. Wenn der TableAdapter noch kein `Insert` -Methode, und klicken Sie dann auf die Tabelle wahrscheinlich bietet keine genügend Schemainformationen zum unterscheiden zwischen einzelnen Zeilen (z. B. möglicherweise keine primären Schlüsselsatzes in der Tabelle).  
  
## <a name="insert-new-records-by-using-tableadapters"></a>Fügen Sie neuer Datensätze mithilfe von TableAdapters ein  
 TableAdapters ermöglichen verschiedene Methoden zum Einfügen neuer Datensätze in einer Datenbank, abhängig von den Anforderungen Ihrer Anwendung.  
  
 Wenn Ihre Anwendung Datasets zum Speichern von Daten verwendet, Sie können einfach neue Datensätze hinzufügen, um die gewünschte <xref:System.Data.DataTable> in das Dataset, und rufen Sie dann die `TableAdapter.Update` Methode. Die `TableAdapter.Update` Methode sendet die Änderungen in der <xref:System.Data.DataTable> mit der Datenbank (einschließlich geänderten und gelöschten Datensätze).  
  
#### <a name="to-insert-new-records-into-a-database-by-using-the-tableadapterupdate-method"></a>Zum Einfügen neuer Datensätze in einer Datenbank mithilfe der TableAdapter.Update-Methode  
  
1.  Neue Datensätze hinzufügen, um die gewünschte <xref:System.Data.DataTable> durch Erstellen eines neuen <xref:System.Data.DataRow> und Hinzufügen zu der <xref:System.Data.DataTable.Rows%2A> Auflistung. 
  
2.  Nachdem die neuen Zeilen hinzugefügt werden die <xref:System.Data.DataTable>, rufen Sie die `TableAdapter.Update` Methode. Sie können steuern, die Menge der Daten zu aktualisieren, indem Sie entweder eine gesamte übergeben <xref:System.Data.DataSet>, <xref:System.Data.DataTable>, ein Array von <xref:System.Data.DataRow>s oder eine einzelne <xref:System.Data.DataRow>.  
  
 Der folgende Code zeigt, wie Sie einen neuen Datensatz hinzufügen einer <xref:System.Data.DataTable> und rufen Sie anschließend die `TableAdapter.Update` Methode, um die neue Zeile in der Datenbank zu speichern. (Dieses Beispiel verwendet die `Region` Tabelle in der Northwind-Datenbank.)  
  
 [!code-vb[VbRaddataSaving#14](../data-tools/codesnippet/VisualBasic/insert-new-records-into-a-database_1.vb)]
 [!code-csharp[VbRaddataSaving#14](../data-tools/codesnippet/CSharp/insert-new-records-into-a-database_1.cs)]  
  
#### <a name="to-insert-new-records-into-a-database-by-using-the-tableadapterinsert-method"></a>Zum Einfügen neuer Datensätze in einer Datenbank mithilfe der TableAdapter.Insert-Methode  
Wenn Ihre Anwendung Objekte verwendet, um Daten zu speichern, können Sie mithilfe der `TableAdapter.Insert` Methode, um neue Zeilen direkt in der Datenbank zu erstellen. Die `Insert` Methode akzeptiert die einzelnen Werte für jede Spalte als Parameter. Aufrufen der Methode fügt einen neuen Datensatz in die Datenbank mit der übergebenen Parameterwerte.  
  
- Rufen Sie die `Insert` -Methode, die Werte für jede Spalte als Parameter übergeben.  

 Das folgende Verfahren veranschaulicht die Verwendung der `TableAdapter.Insert` Methode zum Einfügen von Zeilen. In diesem Beispiel fügt Daten in der `Region` Tabelle in der Northwind-Datenbank.  
  
 > [!NOTE]
 >  Wenn Sie keine Instanz zur Verfügung instanziieren Sie den TableAdapter, die Sie verwenden möchten.  
  
 [!code-vb[VbRaddataSaving#15](../data-tools/codesnippet/VisualBasic/insert-new-records-into-a-database_2.vb)]
 [!code-csharp[VbRaddataSaving#15](../data-tools/codesnippet/CSharp/insert-new-records-into-a-database_2.cs)]  
  
## <a name="insert-new-records-by-using-command-objects"></a>Fügen Sie neuer Datensätze mithilfe von Befehlsobjekte ein  
Sie können neue Datensätze direkt in einer Datenbank mithilfe von Befehlsobjekte einfügen.    
  
#### <a name="to-insert-new-records-into-a-database-by-using-command-objects"></a>Zum Einfügen neuer Datensätze in einer Datenbank mithilfe von Befehlsobjekte  
  
-   Erstellen Sie ein neues Command-Objekt, und legen Sie dessen `Connection`, `CommandType`, und `CommandText` Eigenschaften.  

 Das folgende Beispiel veranschaulicht das Einfügen von Datensätzen in einer Datenbank mithilfe von Command-Objekt. Fügt Daten in der `Region` Tabelle in der Northwind-Datenbank.
  
 [!code-vb[VbRaddataSaving#16](../data-tools/codesnippet/VisualBasic/insert-new-records-into-a-database_3.vb)]
 [!code-csharp[VbRaddataSaving#16](../data-tools/codesnippet/CSharp/insert-new-records-into-a-database_3.cs)]  
  
## <a name="net-framework-security"></a>.NET Framework-Sicherheit  
 Sie benötigen Zugriff auf die Datenbank für die Verbindung gewünschte als auch über die Berechtigung zum Durchführen von einfügungen in die gewünschte Tabelle.  
  
## <a name="see-also"></a>Siehe auch  
 [Rückspeichern von Daten in der Datenbank](../data-tools/save-data-back-to-the-database.md)