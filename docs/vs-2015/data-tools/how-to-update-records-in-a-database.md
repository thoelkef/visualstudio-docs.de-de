---
title: 'Vorgehensweise: Aktualisieren von Datensätzen in einer Datenbank | Microsoft-Dokumentation'
ms.custom: ''
ms.date: 2018-06-30
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
- records, updating
- data [Visual Studio], saving
- records, editing
- databases, updating
- TableAdapter.Update method
ms.assetid: cdc8a8e4-a5fa-40dd-9221-97b8571d802a
caps.latest.revision: 10
author: gewarren
ms.author: gewarren
manager: ghogen
robots: noindex,nofollow
ms.openlocfilehash: 73ca33f9fb30a178addab6dee136d3b441bd81d6
ms.sourcegitcommit: 55f7ce2d5d2e458e35c45787f1935b237ee5c9f8
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 08/22/2018
ms.locfileid: "47509600"
---
# <a name="how-to-update-records-in-a-database"></a>Gewusst wie: Aktualisieren von Datensätzen in einer Datenbank
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Sie können die `TableAdapter.Update` Methode, um Datensätze in einer Datenbank aktualisieren (Bearbeiten). Die `TableAdapter.Update` Methode bietet mehrere Überladungen, die verschiedene Vorgänge abhängig von den Parametern übergeben. Es ist wichtig zu verstehen, die Ergebnisse des Aufrufs dieser Methodensignaturen.  
  
> [!NOTE]
>  Wenn Ihre Anwendung verwendet nicht die TableAdapters, können Sie Befehlsobjekte zum Aktualisieren von Datensätzen in der Datenbank (z. B. <xref:System.Data.SqlClient.SqlCommand.ExecuteNonQuery%2A>). Weitere Informationen zum Aktualisieren von Daten mit Befehlsobjekte finden Sie unter "Aktualisieren von Datensätzen mithilfe von Befehlsobjekten" unten.  
  
 Die folgende Tabelle beschreibt das Verhalten der verschiedenen `TableAdapter.Update` Methoden:  
  
|Methode|Beschreibung|  
|------------|-----------------|  
|`TableAdapter.Update(DataTable)`|Versucht, speichern alle Änderungen in der <xref:System.Data.DataTable> in der Datenbank. (Dies schließt das Entfernen von Zeilen aus der Tabelle, Hinzufügen von Zeilen in die Tabelle eingefügt, und aktualisieren alle Zeilen in der Tabelle, die geändert wurden gelöscht.)|  
|`TableAdapter.Update(DataSet)`|Obwohl der Parameter ein Dataset akzeptiert, die TableAdapter-versucht, alle Änderungen zu speichern, in dem TableAdapter zugeordnete <xref:System.Data.DataTable> in der Datenbank. (Dies schließt das Entfernen von Zeilen aus der Tabelle, Hinzufügen von Zeilen in der Tabelle eingefügt, und aktualisieren alle Zeilen in der Tabelle, die geändert wurden gelöscht.) **Hinweis:** ein TableAdapter zugeordnete <xref:System.Data.DataTable> ist die <xref:System.Data.DataTable> erstellt, wenn der TableAdapter ursprünglich konfiguriert wurde.|  
|`TableAdapter.Update(DataRow)`|Versucht, Änderungen zu speichern, in das angezeigte <xref:System.Data.DataRow> in der Datenbank.|  
|`TableAdapter.Update(DataRows())`|Versucht, Änderungen zu speichern, in eine beliebige Zeile in das Array von <xref:System.Data.DataRow>s in der Datenbank.|  
|`TableAdapter.Update("new column values", "original column values")`|Versucht, Änderungen in einer einzelnen Zeile zu speichern, die von den ursprünglichen Spaltenwerten identifiziert wird.|  
  
 In der Regel die `TableAdapter.Update` Methode, eine <xref:System.Data.DataSet>, <xref:System.Data.DataTable>, oder <xref:System.Data.DataRow>(s), wenn die Anwendung ausschließlich zum Speichern von Daten verwendet.  
  
 In der Regel die `TableAdapter.Update` Methode, die Spaltenwerte annimmt, wenn Ihre Anwendung Objekte verwendet, um Daten zu speichern.  
  
 Wenn der TableAdapter kein `Update` Methode, die die Werte der annimmt, bedeutet das, dass entweder der TableAdapter konfiguriert ist, um gespeicherte Prozeduren zu verwenden oder den zugehörigen `GenerateDBDirectMethods` -Eigenschaftensatz auf `false`. Legen Sie der TableAdapters `GenerateDBDirectMethods` Eigenschaft `true` innerhalb der [Dataset-Designer](../data-tools/creating-and-editing-typed-datasets.md) und speichern Sie das Dataset, um den TableAdapter neu zu generieren. Wenn der TableAdapter noch kein `Update` -Methode, die wahrscheinlich Spaltenwerte, und klicken Sie dann auf die Tabelle akzeptiert, bietet keine ausreichende Schemainformationen zur Unterscheidung zwischen den einzelnen Zeilen (z. B. keinen primärer Schlüssel für die Tabelle festgelegt ist).  
  
## <a name="update-existing-records-using-tableadapters"></a>Aktualisieren von vorhandenen Datensätzen mithilfe von TableAdapters  
 TableAdapters bieten verschiedene Möglichkeiten zum Aktualisieren von Datensätzen in einer Datenbank abhängig von den Anforderungen Ihrer Anwendung.  
  
 Wenn Ihre Anwendung Datasets verwendet, um Daten zu speichern, können Sie einfach die Datensätze in die gewünschte aktualisieren <xref:System.Data.DataTable> und rufen Sie dann die `TableAdapter.Update` -Methode und übergeben Sie entweder die <xref:System.Data.DataSet>, <xref:System.Data.DataTable>, <xref:System.Data.DataRow>, oder ein Array von <xref:System.Data.DataRow>s. Die obigen Tabelle beschreibt die verschiedenen `Update` Methoden.  
  
#### <a name="to-update-records-in-a-database-with-the-tableadapterupdate-method-that-takes-dataset-datatable-datarow-or-datarows"></a>Zum Aktualisieren von Datensätzen in einer Datenbank mit der TableAdapter.Update-Methode, die Datasets "," DataTable "," DataRow "oder" DataRows() verwendet wird.  
  
1.  Bearbeiten der Datensätze in die gewünschte <xref:System.Data.DataTable> durch direktes Bearbeiten der <xref:System.Data.DataRow> in die <xref:System.Data.DataTable>. Weitere Informationen finden Sie unter [Vorgehensweise: Bearbeiten von Zeilen in einer DataTable](http://msdn.microsoft.com/library/d5eea200-9bfa-4956-bf7c-08dd6fb6663c).  
  
2.  Nach dem die Zeilen im bearbeitet werden die <xref:System.Data.DataTable>, rufen Sie die `TableAdapter.Update` Methode. Sie können steuern, die Menge der Daten zu aktualisieren, indem Sie entweder eine gesamte übergeben <xref:System.Data.DataSet>, <xref:System.Data.DataTable>, ein Array von <xref:System.Data.DataRow>s oder eine einzelne <xref:System.Data.DataRow>.  
  
     Der folgende Code zeigt, wie Bearbeiten eines Datensatzes in einem <xref:System.Data.DataTable> und rufen Sie dann die `TableAdapter.Update` Methode, um die Änderungen in der Datenbank zu speichern. (In diesem Beispiel verwendet der Tabelle für die Region der Northwind-Datenbank.)  
  
     [!code-csharp[VbRaddataSaving#17](../snippets/csharp/VS_Snippets_VBCSharp/VbRaddataSaving/CS/Form5.cs#17)]
     [!code-vb[VbRaddataSaving#17](../snippets/visualbasic/VS_Snippets_VBCSharp/VbRaddataSaving/VB/Form5.vb#17)]  
  
 Wenn Ihre Anwendung Objekte verwendet, um die Daten in Ihrer Anwendung zu speichern, können Sie der TableAdapters `DBDirect` Methoden zum Senden von Daten aus Ihrer Objekte direkt an die Datenbank. Diese Methoden können Sie einzelne Werte für jede Spalte als Methodenparameter übergeben. Das Aufrufen dieser Methode aktualisiert einen vorhandenen Datensatz in der Datenbank mit den Spaltenwerten, die an die Methode übergeben.  
  
 Im folgenden Verfahren wird die Northwind `Region` Tabelle als Beispiel.  
  
#### <a name="to-update-records-in-a-database-using-the-tableadapterupdate-method-that-takes-column-values"></a>Zum Aktualisieren von Datensätzen in einer Datenbank mithilfe der TableAdapter.Update-Methode, die Spaltenwerte  
  
-   Rufen Sie die `Update` -Methode, die neuen und ursprünglichen Werte für jede Spalte als Parameter übergeben.  
  
    > [!NOTE]
    >  Wenn Sie nicht über eine verfügbare Instanz verfügen, instanziieren Sie den TableAdapter, die Sie verwenden möchten.  
  
     [!code-csharp[VbRaddataSaving#18](../snippets/csharp/VS_Snippets_VBCSharp/VbRaddataSaving/CS/Class1.cs#18)]
     [!code-vb[VbRaddataSaving#18](../snippets/visualbasic/VS_Snippets_VBCSharp/VbRaddataSaving/VB/Class1.vb#18)]  
  
## <a name="update-records-using-command-objects"></a>Aktualisieren von Datensätzen, die mithilfe von Befehlsobjekten  
 Das folgende Beispiel aktualisiert die vorhandene Datensätze direkt in einer Datenbank mithilfe von Befehlsobjekten. Weitere Informationen zur Verwendung von Befehlsobjekten zum Ausführen von Befehlen und gespeicherten Prozeduren finden Sie unter [Abrufen von Daten in Ihrer Anwendung](../data-tools/fetching-data-into-your-application.md).  
  
 Im folgenden Verfahren wird die Northwind `Region` Tabelle als Beispiel.  
  
#### <a name="to-update-existing-records-in-a-database-using-command-objects"></a>Zum Aktualisieren von vorhandener Datensätzen in einer Datenbank mithilfe von Befehlsobjekten  
  
-   Erstellen Sie ein neues Command-Objekt; Legen Sie seine `Connection`, `CommandType`, und `CommandText` Eigenschaften aus; klicken Sie dann eine Verbindung öffnen, und führen Sie den Befehl.  
  
     [!code-csharp[VbRaddataSaving#19](../snippets/csharp/VS_Snippets_VBCSharp/VbRaddataSaving/CS/Class1.cs#19)]
     [!code-vb[VbRaddataSaving#19](../snippets/visualbasic/VS_Snippets_VBCSharp/VbRaddataSaving/VB/Class1.vb#19)]  
  
## <a name="net-framework-security"></a>.NET Framework-Sicherheit  
 Benötigen Sie Zugriff auf die Datenbank, die Sie herstellen möchten, sowie über die Berechtigung zum Aktualisieren von Datensätzen in die gewünschte Tabelle.  
  
## <a name="see-also"></a>Siehe auch  
 [Übersicht über TableAdapters](../data-tools/tableadapter-overview.md)   
 [Vorgehensweise: Löschen von Datensätzen in einer Datenbank](../data-tools/how-to-delete-records-in-a-database.md)   
 [Fügen Sie neuer Datensätze in einer Datenbank ein](../data-tools/insert-new-records-into-a-database.md)   
 [Speichern von Daten aus einem Objekt in einer Datenbank](../data-tools/save-data-from-an-object-to-a-database.md)   
 [Übersicht über Datenanwendungen in Visual Studio](../data-tools/overview-of-data-applications-in-visual-studio.md)   
 [Herstellen einer Verbindung mit Daten in Visual Studio](../data-tools/connecting-to-data-in-visual-studio.md)   
 [Vorbereiten der Anwendung zum Empfangen von Daten](http://msdn.microsoft.com/library/c17bdb7e-c234-4f2f-9582-5e55c27356ad)   
 [Abrufen von Daten für Ihre Anwendung](../data-tools/fetching-data-into-your-application.md)   
 [Binden von Steuerelementen an Daten in Visual Studio](../data-tools/bind-controls-to-data-in-visual-studio.md)   
 [Bearbeiten von Daten in Ihrer Anwendung](../data-tools/editing-data-in-your-application.md)   
 [Überprüfen von Daten](http://msdn.microsoft.com/library/b3a9ee4e-5d4d-4411-9c56-c811f2b4ee7e)   
 [Speichern von Daten](../data-tools/saving-data.md)