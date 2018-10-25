---
title: 'Vorgehensweise: Löschen von Datensätzen in einer Datenbank | Microsoft-Dokumentation'
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
- data [Visual Studio], saving
- records, deleting
- TableAdapter.Delete method
- databases, deleting records
- deleting data
- TableAdapter.Update method
- saving data
ms.assetid: d74d2130-9732-4648-abea-241059c4a372
caps.latest.revision: 11
author: gewarren
ms.author: gewarren
manager: ghogen
robots: noindex,nofollow
ms.openlocfilehash: 87ab5ccde2c1100fbd0efc5f4272efe27803b717
ms.sourcegitcommit: 240c8b34e80952d00e90c52dcb1a077b9aff47f6
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 10/23/2018
ms.locfileid: "49938616"
---
# <a name="how-to-delete-records-in-a-database"></a>Gewusst wie: Löschen von Datensätzen in einer Datenbank
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Um Datensätze aus einer Datenbank zu löschen, verwenden die `TableAdapter.Update` Methode oder der `TableAdapter.Delete` Methode. Oder, wenn Ihre Anwendung keine TableAdapters verwendet werden, können Sie Befehlsobjekte verwenden, zum Löschen von Datensätzen aus einer Datenbank (z. B. <xref:System.Data.SqlClient.SqlCommand.ExecuteNonQuery%2A>).  
  
 Die `TableAdapter.Update` Methode wird normalerweise verwendet, wenn Ihre Anwendung Datasets verwendet, um Daten zu speichern, während die `TableAdapter.Delete` Methode wird normalerweise verwendet, wenn Ihre Anwendung Objekte verwendet, um Daten zu speichern.  
  
 Wenn der TableAdapter keine `Delete` -Methode, es bedeutet, dass entweder ist so konfiguriert, um gespeicherte Prozeduren zu verwenden oder den zugehörigen `GenerateDBDirectMethods` -Eigenschaftensatz auf `false`. Legen Sie der TableAdapters `GenerateDBDirectMethods` Eigenschaft `true` innerhalb der [Dataset-Designer](../data-tools/creating-and-editing-typed-datasets.md) und speichern Sie das Dataset, um den TableAdapter neu zu generieren. Wenn der TableAdapter noch keine `Delete` -Methode, und klicken Sie dann auf die Tabelle möglicherweise bietet keine ausreichende Schemainformationen zur Unterscheidung zwischen den einzelnen Zeilen (z. B. keinen primärer Schlüssel für die Tabelle festgelegt ist).  
  
## <a name="delete-records-using-tableadapters"></a>Löschen von Datensätzen, die mithilfe von TableAdapters  
 TableAdapters bieten verschiedene Möglichkeiten zum Löschen von Datensätzen aus einer Datenbank abhängig von den Anforderungen Ihrer Anwendung.  
  
 Wenn die Anwendung mithilfe von Datasets zum Speichern von Daten können Sie einfach Datensätze löschen, aus der gewünschten <xref:System.Data.DataTable> in die <xref:System.Data.DataSet>, und rufen Sie dann die `TableAdapter.Update` Methode. Die `TableAdapter.Update` Methode akzeptiert alle Änderungen in der Datentabelle und sendet diese Änderungen an der Datenbank (einschließlich eingefügten, aktualisierten und gelöschten Datensätze).  
  
#### <a name="to-delete-records-from-a-database-using-the-tableadapterupdate-method"></a>Zum Löschen von Datensätzen aus einer Datenbank mithilfe der TableAdapter.Update-Methode  
  
- Löschen von Datensätzen in die gewünschte <xref:System.Data.DataTable> löschen <xref:System.Data.DataRow> Objekte aus der Tabelle. Weitere Informationen finden Sie unter [Vorgehensweise: Löschen von Zeilen in einer "DataTable"](http://msdn.microsoft.com/library/add481e5-08c7-4923-9276-f036ae29d31e). Nach dem Löschen der Zeilen aus der <xref:System.Data.DataTable>, rufen Sie die `TableAdapter.Update` Methode. Sie können steuern, die Menge der Daten durch die Übergabe in einem ganzen aktualisieren <xref:System.Data.DataSet>, <xref:System.Data.DataTable>, ein Array von <xref:System.Data.DataRow>s oder eine einzelne <xref:System.Data.DataRow>. Der folgende Code zeigt, wie Sie das Löschen eines Datensatzes von einem <xref:System.Data.DataTable> und rufen Sie dann die `TableAdapter.Update` Methode, um die Änderung zu kommunizieren, und löschen Sie die Zeile aus der Datenbank. (Dieses Beispiel verwendet der Datenbank Northwind `Region` Tabelle.)  
  
   [!code-csharp[VbRaddataSaving#20](../snippets/csharp/VS_Snippets_VBCSharp/VbRaddataSaving/CS/Form5.cs#20)]
   [!code-vb[VbRaddataSaving#20](../snippets/visualbasic/VS_Snippets_VBCSharp/VbRaddataSaving/VB/Form5.vb#20)]  
  
  Wenn Ihre Anwendung Objekte verwendet, um die Daten in Ihrer Anwendung zu speichern, können Sie die TableAdapter DBDirect-Methoden, um Daten direkt aus der Datenbank zu löschen. Aufrufen der `Delete` Methode entfernt Einträge aus der Datenbank, die basierend auf dem übergebenen Parameterwerte.  
  
#### <a name="to-delete-records-from-a-database-using-the-tableadapterdelete-method"></a>Zum Löschen von Datensätzen aus einer Datenbank mithilfe der TableAdapter.Delete-Methode  
  
-   Rufen Sie die `Delete` -Methode, die Werte für jede Spalte als Parameter übergeben die `Delete` Methode. (Dieses Beispiel verwendet der Datenbank Northwind `Region` Tabelle.)  
  
    > [!NOTE]
    >  Wenn Sie nicht über eine verfügbare Instanz verfügen, instanziieren Sie den TableAdapter, die Sie verwenden möchten.  
  
     [!code-csharp[VbRaddataSaving#21](../snippets/csharp/VS_Snippets_VBCSharp/VbRaddataSaving/CS/Class1.cs#21)]
     [!code-vb[VbRaddataSaving#21](../snippets/visualbasic/VS_Snippets_VBCSharp/VbRaddataSaving/VB/Class1.vb#21)]  
  
## <a name="delete-records-using-command-objects"></a>Löschen von Datensätzen, die mithilfe von Befehlsobjekten  
 Das folgende Beispiel löscht Datensätze direkt aus einer Datenbank mithilfe von Befehlsobjekten. Weitere Informationen zur Verwendung von Befehlsobjekten zum Ausführen von Befehlen und gespeicherten Prozeduren finden Sie unter [Abrufen von Daten in Ihrer Anwendung](../data-tools/fetching-data-into-your-application.md).  
  
#### <a name="to-delete-records-from-a-database-using-command-objects"></a>Zum Löschen von Datensätzen aus einer Datenbank mithilfe von Befehlsobjekten  
  
-   Erstellen Sie ein neues Befehlsobjekt, legen Sie dessen `Connection`, `CommandType`, und `CommandText` Eigenschaften. (Dieses Beispiel verwendet der Datenbank Northwind `Region` Tabelle.)  
  
     [!code-csharp[VbRaddataSaving#22](../snippets/csharp/VS_Snippets_VBCSharp/VbRaddataSaving/CS/Class1.cs#22)]
     [!code-vb[VbRaddataSaving#22](../snippets/visualbasic/VS_Snippets_VBCSharp/VbRaddataSaving/VB/Class1.vb#22)]  
  
## <a name="net-framework-security"></a>.NET Framework-Sicherheit  
 Benötigen Sie Zugriff auf die Datenbank, die Sie versuchen für die Verbindung als auch über die Berechtigung zum Löschen von Datensätzen aus die gewünschte Tabelle.  
  
## <a name="see-also"></a>Siehe auch  
 [Übersicht über TableAdapters](../data-tools/tableadapter-overview.md)   
 [Fügen Sie neuer Datensätze in einer Datenbank ein](../data-tools/insert-new-records-into-a-database.md)   
 [Vorgehensweise: Aktualisieren von Datensätzen in einer Datenbank](../data-tools/how-to-update-records-in-a-database.md)   
 [Speichern von Daten aus einem Objekt in einer Datenbank](../data-tools/save-data-from-an-object-to-a-database.md)   
 [Übersicht über Datenanwendungen in Visual Studio](../data-tools/overview-of-data-applications-in-visual-studio.md)   
 [Herstellen einer Verbindung mit Daten in Visual Studio](../data-tools/connecting-to-data-in-visual-studio.md)   
 [Vorbereiten der Anwendung zum Empfangen von Daten](http://msdn.microsoft.com/library/c17bdb7e-c234-4f2f-9582-5e55c27356ad)   
 [Abrufen von Daten für Ihre Anwendung](../data-tools/fetching-data-into-your-application.md)   
 [Binden von Steuerelementen an Daten in Visual Studio](../data-tools/bind-controls-to-data-in-visual-studio.md)   
 [Bearbeiten von Daten in Ihrer Anwendung](../data-tools/editing-data-in-your-application.md)   
 [Überprüfen von Daten](http://msdn.microsoft.com/library/b3a9ee4e-5d4d-4411-9c56-c811f2b4ee7e)   
 [Speichern von Daten](../data-tools/saving-data.md)