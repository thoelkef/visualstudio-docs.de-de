---
title: Einfügen neuer Datensätze in einer Datenbank | Microsoft-Dokumentation
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
- TableAdapters, inserting new records into
- data [Visual Studio], saving
- databases, inserting new records into
- records, inserting
- saving data
ms.assetid: ea118fff-69b1-4675-b79a-e33374377f04
caps.latest.revision: 14
author: gewarren
ms.author: gewarren
manager: ghogen
ms.openlocfilehash: c0ae1272820b7d8ec5ef124aaaa77d44a1285dde
ms.sourcegitcommit: 9ceaf69568d61023868ced59108ae4dd46f720ab
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 10/12/2018
ms.locfileid: "49297400"
---
# <a name="insert-new-records-into-a-database"></a>Einfügen neuer Datensätze in eine Datenbank
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

  
Zum Einfügen neuer Datensätze in einer Datenbank können Sie die `TableAdapter.Update` Methode oder eines der TableAdapter-DBDirect-Methoden (insbesondere die `TableAdapter.Insert` Methode). Weitere Informationen finden Sie unter [TableAdapter Overview](../data-tools/tableadapter-overview.md).  
  
 Wenn Ihre Anwendung TableAdapters nicht verwendet werden, können Sie Befehlsobjekte verwenden (z. B. <xref:System.Data.SqlClient.SqlCommand>) zum Einfügen neuer Datensätze in der Datenbank.  
  
 Wenn Ihre Anwendung Datasets verwendet, um Daten zu speichern, verwenden Sie die `TableAdapter.Update` Methode. Die `Update` Methode sendet alle Änderungen (Updates, einfügungen und löschungen), mit der Datenbank.  
  
 Wenn Ihre Anwendung Objekte verwendet, Daten, oder speichern eine genauere Steuerung der Erstellung neuer Datensätze in der Datenbank, verwenden Sie die `TableAdapter.Insert` Methode.  
  
 Wenn keine der TableAdapter eine `Insert` -Methode, es bedeutet, dass entweder der TableAdapter konfiguriert ist, um gespeicherte Prozeduren zu verwenden oder den zugehörigen `GenerateDBDirectMethods` -Eigenschaftensatz auf `false`. Legen Sie der TableAdapters `GenerateDBDirectMethods` Eigenschaft `true` innerhalb der [Dataset-Designer](../data-tools/creating-and-editing-typed-datasets.md), und speichern Sie das Dataset. Hierdurch wird den TableAdapter neu generiert. Wenn der TableAdapter immer noch kein `Insert` -Methode, und klicken Sie dann auf die Tabelle möglicherweise bietet keine ausreichende Schemainformationen zur Unterscheidung zwischen den einzelnen Zeilen (z. B. möglicherweise keine primären Schlüsselsatz für die Tabelle).  
  
## <a name="insert-new-records-by-using-tableadapters"></a>Fügen Sie neue Datensätze mit TableAdapters  
 TableAdapters bieten verschiedene Möglichkeiten zum Einfügen neuer Datensätze in einer Datenbank, abhängig von den Anforderungen Ihrer Anwendung.  
  
 Wenn Ihre Anwendung Datasets verwendet, um Daten zu speichern, können Sie einfach neue Datensätze hinzufügen, um die gewünschte <xref:System.Data.DataTable> in das Dataset, und rufen Sie dann die `TableAdapter.Update` Methode. Die `TableAdapter.Update` Methode sendet die Änderungen in der <xref:System.Data.DataTable> in der Datenbank (einschließlich geänderte und gelöschte Datensätze).  
  
#### <a name="to-insert-new-records-into-a-database-by-using-the-tableadapterupdate-method"></a>Zum Einfügen neuer Datensätze in einer Datenbank mithilfe der TableAdapter.Update-Methode  
  
1.  Neue Datensätze hinzufügen, um die gewünschte <xref:System.Data.DataTable> durch Erstellen eines neuen <xref:System.Data.DataRow> und zum Hinzufügen der <xref:System.Data.DataTable.Rows%2A> Auflistung. Weitere Informationen finden Sie unter [Vorgehensweise: Hinzufügen von Zeilen zu einer DataTable](http://msdn.microsoft.com/library/78ebbb43-c402-49cf-81da-0715289487bf).  
  
2.  Nachdem die neuen Zeilen hinzugefügt wurden die <xref:System.Data.DataTable>, rufen Sie die `TableAdapter.Update` Methode. Sie können steuern, die Menge der Daten zu aktualisieren, indem Sie entweder eine gesamte übergeben <xref:System.Data.DataSet>, <xref:System.Data.DataTable>, ein Array von <xref:System.Data.DataRow>s oder eine einzelne <xref:System.Data.DataRow>.  
  
     Der folgende Code zeigt, wie Sie einen neuen Eintrag Hinzufügen einer <xref:System.Data.DataTable> und rufen Sie dann die `TableAdapter.Update` Methode, um die neue Zeile in der Datenbank zu speichern. (Dieses Beispiel verwendet die `Region` Tabelle in der Northwind-Datenbank.)  
  
     [!code-csharp[VbRaddataSaving#14](../snippets/csharp/VS_Snippets_VBCSharp/VbRaddataSaving/CS/Form5.cs#14)]
     [!code-vb[VbRaddataSaving#14](../snippets/visualbasic/VS_Snippets_VBCSharp/VbRaddataSaving/VB/Form5.vb#14)]  
  
 Wenn Ihre Anwendung Objekte verwendet, um Daten zu speichern, können Sie mithilfe der `TableAdapter.Insert` Methode, um neue Zeilen direkt in der Datenbank zu erstellen. Die `Insert` -Methode akzeptiert die einzelnen Werte für jede Spalte als Parameter. Aufrufen der Methode fügt einen neuen Datensatz in die Datenbank mit der übergebenen Parameterwerte.  
  
 Im folgenden Verfahren wird die `Region` Tabelle in der Northwind-Datenbank als Beispiel.  
  
#### <a name="to-insert-new-records-into-a-database-by-using-the-tableadapterinsert-method"></a>Zum Einfügen neuer Datensätze in einer Datenbank mithilfe der TableAdapter.Insert-Methode  
  
-   Rufen Sie die `Insert` -Methode, die Werte für jede Spalte als Parameter übergeben.  
  
    > [!NOTE]
    >  Wenn Sie nicht über eine verfügbare Instanz verfügen, instanziieren Sie den TableAdapter, die Sie verwenden möchten.  
  
     [!code-csharp[VbRaddataSaving#15](../snippets/csharp/VS_Snippets_VBCSharp/VbRaddataSaving/CS/Class1.cs#15)]
     [!code-vb[VbRaddataSaving#15](../snippets/visualbasic/VS_Snippets_VBCSharp/VbRaddataSaving/VB/Class1.vb#15)]  
  
## <a name="insert-new-records-by-using-command-objects"></a>Fügen Sie neue Datensätze mit Befehlsobjekte  
 Das folgende Beispiel fügt neue Datensätze direkt in eine Datenbank mithilfe von Befehlsobjekten. Weitere Informationen zur Verwendung von Befehlsobjekten zum Ausführen von Befehlen und gespeicherten Prozeduren finden Sie unter [Abrufen von Daten in Ihrer Anwendung](../data-tools/fetching-data-into-your-application.md).  
  
 Im folgenden Verfahren wird die `Region` Tabelle in der Northwind-Datenbank als Beispiel.  
  
#### <a name="to-insert-new-records-into-a-database-by-using-command-objects"></a>Zum Einfügen neuer Datensätze in einer Datenbank mithilfe von Befehlsobjekten  
  
-   Erstellen Sie ein neues Befehlsobjekt aus, und legen Sie dann die `Connection`, `CommandType`, und `CommandText` Eigenschaften.  
  
     [!code-csharp[VbRaddataSaving#16](../snippets/csharp/VS_Snippets_VBCSharp/VbRaddataSaving/CS/Class1.cs#16)]
     [!code-vb[VbRaddataSaving#16](../snippets/visualbasic/VS_Snippets_VBCSharp/VbRaddataSaving/VB/Class1.vb#16)]  
  
## <a name="net-framework-security"></a>.NET Framework-Sicherheit  
 Benötigen Sie Zugriff auf die Datenbank, die Sie herstellen möchten, sowie Berechtigung zum Durchführen von einfügungen in die gewünschte Tabelle.  
  
## <a name="see-also"></a>Siehe auch  
 [Rückspeichern von Daten in der Datenbank](../data-tools/save-data-back-to-the-database.md)

