---
title: 'Vorgehensweise: Speichern von Datasetänderungen in einer Datenbank | Microsoft-Dokumentation'
ms.custom: ''
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
f1_keywords:
- DbDataAdapter.Update
dev_langs:
- VB
- CSharp
- C++
- aspx
helpviewer_keywords:
- data [Visual Studio], saving
- databases, updating
- updating datasets, writing changes to data source
ms.assetid: c9970150-b71b-4c9d-a355-5efb6b510dca
caps.latest.revision: 14
author: gewarren
ms.author: gewarren
manager: ghogen
robots: noindex,nofollow
ms.openlocfilehash: 60bb855202cfb333820fe2292fedc0b31608c5c6
ms.sourcegitcommit: 240c8b34e80952d00e90c52dcb1a077b9aff47f6
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 10/23/2018
ms.locfileid: "49949018"
---
# <a name="how-to-save-dataset-changes-to-a-database"></a>Gewusst wie: Speichern von Datasetänderungen in einer Datenbank
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Nachdem die Daten im Dataset geändert und überprüft wurden, möchten Sie die aktualisierten Daten möglicherweise an die Datenbank zurücksenden. Um die geänderten Daten in einer Datenbank zu senden, rufen Sie die `Update` Methode eine [TableAdapter](../data-tools/tableadapter-overview.md) oder Datenadapters. Die `Update`-Methode des Adapters aktualisiert eine einzelne Datentabelle und führt auf der Grundlage des <xref:System.Data.DataRow.RowState%2A> der einzelnen Datenzeilen in der Tabelle den korrekten Befehl (INSERT, UPDATE oder DELETE) aus.  
  
 Beim Speichern von Daten in verknüpften Tabellen wird von Visual Studio eine neue TableAdapterManager-Komponente bereitgestellt, die Hilfe beim Speichern in der richtigen Reihenfolge basierend auf den in der Datenbank festgelegten Fremdschlüsseleinschränkungen bietet. Weitere Informationen finden Sie unter [Übersicht über hierarchische Update](http://msdn.microsoft.com/library/c4f8e8b9-e4a5-4a02-8462-d03d1e8222d6).  
  
> [!NOTE]
>  Da es wird versucht, eine Datenquelle mit dem Inhalt eines Datasets aktualisieren zu Fehlern führen kann, sollten Sie den Code, des Adapters aufruft, platzieren `Update` -Methode in der ein `try` / `catch` Block.  
  
 Die genaue Verfahrensweise zum Aktualisieren einer Datenquelle kann je nach Unternehmensanforderungen variieren. Die folgenden Schritte sollten jedoch von der Anwendung ausgeführt werden:  
  
1.  Ausführen von Code, der versucht, das Senden von Aktualisierungen an die Datenbank in eine `try` / `catch` Block.  
  
2.  Lokalisieren der fehlerhaften Datenzeile, falls eine Ausnahme abgefangen wird. Weitere Informationen finden Sie unter [wie: Suchen von Zeilen, dass Fehler haben](http://msdn.microsoft.com/library/1fa907c5-fe66-4f29-a253-2b97b900050c).  
  
3.  Stimmen Sie das Problem in der Datenzeile ab (möglichst programmgesteuert oder, indem die ungültige Zeile dem Benutzer zur Änderung angezeigt wird), und wiederholen Sie dann die Aktualisierung (<xref:System.Data.DataRow.HasErrors%2A>-Eigenschaft, <xref:System.Data.DataTable.GetErrors%2A>-Methode).  
  
## <a name="saving-data-to-a-database"></a>Speichern von Daten in einer Datenbank  
 Rufen Sie die `Update`-Methode eines TableAdapter oder Datenadapters auf, indem Sie den Namen der Datentabelle übergeben, in der die Werte enthalten sind, die in die Datenbank geschrieben werden sollen. Weitere Informationen zum Speichern von Daten aus einer einzelnen Datentabelle in einer Datenbank finden Sie unter [Exemplarische Vorgehensweise: Speichern von Daten in einer Datenbank (eine Tabelle)](http://msdn.microsoft.com/library/68befa96-7463-43e8-abcf-dc2f42ccd53d).  
  
#### <a name="to-update-a-database-with-a-dataset-using-a-tableadapter"></a>So aktualisieren Sie eine Datenbank mit einem Dataset mithilfe eines TableAdapter  
  
-   Schließen Sie die `TableAdapter.Update` Methode innerhalb einer `try` / `catch` Block. Im folgenden Beispiel wird veranschaulicht, wie eine Aktualisierung mit dem Inhalt der `Customers`-Tabelle in `NorthwindDataSet` ausgeführt werden kann.  
  
     [!code-csharp[VbRaddataSaving#9](../snippets/csharp/VS_Snippets_VBCSharp/VbRaddataSaving/CS/Form3.cs#9)]
     [!code-vb[VbRaddataSaving#9](../snippets/visualbasic/VS_Snippets_VBCSharp/VbRaddataSaving/VB/Form3.vb#9)]  
  
#### <a name="to-update-a-database-with-a-dataset-using-a-data-adapter"></a>So aktualisieren Sie eine Datenbank mit einem Dataset mithilfe eines Datenadapters  
  
-   Schließen Sie die `DataAdapter.Update` Methode innerhalb einer `try` / `catch` Block. Im folgenden Beispiel wird veranschaulicht, wie eine Datenquelle mit dem Inhalt von `Table1` in `DataSet1` aktualisiert werden kann.  
  
     [!code-csharp[VbRaddataSaving#26](../snippets/csharp/VS_Snippets_VBCSharp/VbRaddataSaving/CS/Class1.cs#26)]
     [!code-vb[VbRaddataSaving#26](../snippets/visualbasic/VS_Snippets_VBCSharp/VbRaddataSaving/VB/Class1.vb#26)]  
  
## <a name="updating-two-related-tables-in-a-dataset"></a>Aktualisieren von zwei verknüpften Tabellen in einem Dataset  
 Bei der Aktualisierung verknüpfter Tabellen in einem Dataset ist es wichtig, die richtige Reihenfolge einzuhalten, um nicht unnötig Einschränkungen für die referenzielle Integrität zu verletzen. Die in der Befehlsausführung verwendete Abfolge richtet sich zusätzlich nach den Indizes von <xref:System.Data.DataRowCollection> im Dataset. Um zu verhindern, dass Integritätsfehler ausgelöst werden, wird bei der Aktualisierung der Datenbank die folgende Reihenfolge empfohlen:  
  
1. Untergeordnete Tabelle: Datensätze löschen.  
  
2. Übergeordnete Tabelle: Datensätze einfügen, aktualisieren und löschen.  
  
3. Untergeordnete Tabelle: Datensätze einfügen und aktualisieren.  
  
   Ausführliche Informationen zum Speichern von Daten aus mehreren Tabellen finden Sie unter [Speichern von Daten in einer Datenbank (mehrere Tabellen)](../data-tools/save-data-to-a-database-multiple-tables.md).  
  
   Wenn Sie zwei oder mehr verknüpfte Tabellen aktualisieren, dann müssen Sie die gesamte Aktualisierungslogik einer Transaktion miteinbeziehen. Eine Transaktion ist ein Prozess, der sicherstellt, dass alle zugehörigen Änderungen an einer Datenbank erfolgreich sind, bevor ein Commit für eine der Änderungen ausgeführt wird. Weitere Informationen finden Sie unter [Transaktionen und Parallelität](http://msdn.microsoft.com/library/f46570de-9e50-4fe6-8710-a8c31fa8569b).  
  
#### <a name="to-update-two-related-tables-using-a-tableadapter"></a>So aktualisieren Sie zwei verknüpfte Tabellen mit einem TableAdapter  
  
1.  Erstellen Sie drei temporäre <xref:System.Data.DataTable> für die unterschiedlichen Datensätze.  
  
2.  Rufen Sie die `Update` Methode für jede Teilmenge der Zeilen in einer `try` / `catch` Block. Falls Aktualisierungsfehler auftreten, empfiehlt es sich, die Fehler durch einen Branch zu beheben.  
  
3.  Übertragen Sie die Änderungen vom Dataset in die Datenbank.  
  
4.  Löschen Sie die temporären Datentabellen, um die Ressourcen freizugeben.  
  
     [!code-csharp[VbRaddataSaving#27](../snippets/csharp/VS_Snippets_VBCSharp/VbRaddataSaving/CS/Form2.cs#27)]
     [!code-vb[VbRaddataSaving#27](../snippets/visualbasic/VS_Snippets_VBCSharp/VbRaddataSaving/VB/Form2.vb#27)]  
  
#### <a name="to-update-two-related-tables-using-a-data-adapter"></a>So aktualisieren Sie zwei verknüpfte Tabellen mit einem Datenadapter  
  
-   Rufen Sie die `Update`-Methode jedes Datenadapters auf.  
  
     Im folgenden Beispiel wird erläutert, wie Sie eine Datenquelle mit einem Dataset aktualisieren, das verknüpfte Tabellen enthält. Damit die oben angegebene Reihenfolge eingehalten wird, werden drei temporäre <xref:System.Data.DataTable> für die unterschiedlichen Datensätze erstellt. Die `Update` aufgerufene Methode für jede Teilmenge von Zeilen innerhalb einer `try` / `catch` Block. Falls Aktualisierungsfehler auftreten, empfiehlt es sich, die Fehler durch einen Branch zu beheben. Anschließend führt das Dataset einen Commit für die Änderungen aus. Löschen Sie abschließend die temporären Datentabellen, um die Ressourcen freizugeben.  
  
     [!code-csharp[VbRaddataSaving#28](../snippets/csharp/VS_Snippets_VBCSharp/VbRaddataSaving/CS/Class1.cs#28)]
     [!code-vb[VbRaddataSaving#28](../snippets/visualbasic/VS_Snippets_VBCSharp/VbRaddataSaving/VB/Class1.vb#28)]  
  
## <a name="see-also"></a>Siehe auch  
 [Exemplarische Vorgehensweisen für Daten](http://msdn.microsoft.com/library/15a88fb8-3bee-4962-914d-7a1f8bd40ec4)   
 [Binden von Windows Forms-Steuerelementen an Daten in Visual Studio](../data-tools/bind-windows-forms-controls-to-data-in-visual-studio.md)   
 [Herstellen einer Verbindung mit Daten in Visual Studio](../data-tools/connecting-to-data-in-visual-studio.md)   
 [Vorbereiten der Anwendung zum Empfangen von Daten](http://msdn.microsoft.com/library/c17bdb7e-c234-4f2f-9582-5e55c27356ad)   
 [Abrufen von Daten für Ihre Anwendung](../data-tools/fetching-data-into-your-application.md)   
 [Binden von Steuerelementen an Daten in Visual Studio](../data-tools/bind-controls-to-data-in-visual-studio.md)   
 [Bearbeiten von Daten in Ihrer Anwendung](../data-tools/editing-data-in-your-application.md)   
 [Überprüfen von Daten](http://msdn.microsoft.com/library/b3a9ee4e-5d4d-4411-9c56-c811f2b4ee7e)   
 [Speichern von Daten](../data-tools/saving-data.md)