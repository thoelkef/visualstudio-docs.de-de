---
title: "Gewusst wie: Speichern von Dataset&#228;nderungen in einer Datenbank | Microsoft Docs"
ms.custom: ""
ms.date: "12/14/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "DbDataAdapter.Update"
dev_langs: 
  - "VB"
  - "CSharp"
  - "C++"
  - "aspx"
helpviewer_keywords: 
  - "Daten [Visual Studio], Speichern"
  - "Datenbanken, Aktualisieren"
  - "Aktualisieren von Datasets, Schreiben von Änderungen in die Datenquelle"
ms.assetid: c9970150-b71b-4c9d-a355-5efb6b510dca
caps.latest.revision: 14
caps.handback.revision: 14
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
robots: noindex,nofollow
---
# Gewusst wie: Speichern von Dataset&#228;nderungen in einer Datenbank
Nachdem die Daten im Dataset geändert und überprüft wurden, möchten Sie die aktualisierten Daten möglicherweise an die Datenbank zurücksenden.  Wenn die geänderten Daten an die Datenbank gesendet werden sollen, rufen Sie die `Update`\-Methode eines [TableAdapter](../data-tools/tableadapter-overview.md) oder Datenadapters auf.  Die `Update`\-Methode des Adapters aktualisiert eine einzelne Datentabelle und führt auf der Grundlage des <xref:System.Data.DataRow.RowState%2A> der einzelnen Datenzeilen in der Tabelle den korrekten Befehl \(INSERT, UPDATE oder DELETE\) aus.  
  
 Beim Speichern von Daten in verknüpften Tabellen wird von Visual Studio eine neue TableAdapterManager\-Komponente bereitgestellt, die Hilfe beim Speichern in der richtigen Reihenfolge basierend auf den in der Datenbank festgelegten Fremdschlüsseleinschränkungen bietet.  Weitere Informationen finden Sie unter [Übersicht über die hierarchische Aktualisierung](../Topic/Hierarchical%20Update%20Overview.md).  
  
> [!NOTE]
>  Weil bei dem Versuch der Aktualisierung einer Datenquelle mit dem Inhalt eines Datasets Fehler auftreten können, sollte der Code, der die `Update`\-Methode des Adapters aufruft, in einem `try`\/`catch`\-Block platziert werden.  
  
 Die genaue Verfahrensweise zum Aktualisieren einer Datenquelle kann je nach Unternehmensanforderungen variieren. Die folgenden Schritte sollten jedoch von der Anwendung ausgeführt werden:  
  
1.  Führen Sie Code aus, der versucht, Aktualisierungen an die Datenbank in einem `try`\/`catch`\-Block zu senden.  
  
2.  Lokalisieren der fehlerhaften Datenzeile, falls eine Ausnahme abgefangen wird.  Weitere Informationen finden Sie unter [Gewusst wie: Suchen nach Zeilen mit Fehlern](../Topic/How%20to:%20Locate%20Rows%20that%20Have%20Errors.md).  
  
3.  Beheben Sie das Problem in der Datenzeile \(möglichst programmgesteuert oder indem die ungültige Zeile dem Benutzer zur Änderung angezeigt wird\), und wiederholen Sie dann die Aktualisierung \(<xref:System.Data.DataRow.HasErrors%2A>\-Eigenschaft, <xref:System.Data.DataTable.GetErrors%2A>\-Methode\).  
  
## Speichern von Daten in einer Datenbank  
 Rufen Sie die `Update`\-Methode eines TableAdapter oder Datenadapters auf, indem Sie den Namen der Datentabelle übergeben, in der die Werte enthalten sind, die in die Datenbank geschrieben werden sollen.  Weitere Informationen zum Speichern von Daten aus einer einzelnen Datentabelle in einer Datenbank finden Sie unter [Exemplarische Vorgehensweise: Speichern von Daten in einer Datenbank \(eine Tabelle\)](../Topic/Walkthrough:%20Saving%20Data%20to%20a%20Database%20\(Single%20Table\).md).  
  
#### So aktualisieren Sie eine Datenbank mit einem Dataset mithilfe eines TableAdapter  
  
-   Schließen Sie die `TableAdapter.Update`\-Methode in einem `try`\/`catch`\-Block ein.  Im folgenden Beispiel wird veranschaulicht, wie eine Aktualisierung mit dem Inhalt der `Customers`\-Tabelle in `NorthwindDataSet` ausgeführt werden kann.  
  
     [!code-cs[VbRaddataSaving#9](../data-tools/codesnippet/CSharp/how-to-save-dataset-changes-to-a-database_1.cs)]
     [!code-vb[VbRaddataSaving#9](../data-tools/codesnippet/VisualBasic/how-to-save-dataset-changes-to-a-database_1.vb)]  
  
#### So aktualisieren Sie eine Datenbank mit einem Dataset mithilfe eines Datenadapters  
  
-   Schließen Sie die `DataAdapter.Update`\-Methode in einem `try`\/`catch`\-Block ein.  Im folgenden Beispiel wird veranschaulicht, wie eine Datenquelle mit dem Inhalt von `Table1` in `DataSet1` aktualisiert werden kann.  
  
     [!code-vb[VbRaddataSaving#26](../data-tools/codesnippet/VisualBasic/how-to-save-dataset-changes-to-a-database_2.vb)]
     [!code-cs[VbRaddataSaving#26](../data-tools/codesnippet/CSharp/how-to-save-dataset-changes-to-a-database_2.cs)]  
  
## Aktualisieren von zwei verknüpften Tabellen in einem Dataset  
 Bei der Aktualisierung verknüpfter Tabellen in einem Dataset ist es wichtig, die richtige Reihenfolge einzuhalten, um nicht unnötig Einschränkungen für die referenzielle Integrität zu verletzen.  Die in der Befehlsausführung verwendete Abfolge richtet sich zusätzlich nach den Indizes von <xref:System.Data.DataRowCollection> im Dataset.  Um zu verhindern, dass Integritätsfehler ausgelöst werden, wird bei der Aktualisierung der Datenbank die folgende Reihenfolge empfohlen:  
  
1.  Untergeordnete Tabelle: Datensätze löschen.  
  
2.  Übergeordnete Tabelle: Datensätze einfügen, aktualisieren und löschen.  
  
3.  Untergeordnete Tabelle: Datensätze einfügen und aktualisieren.  
  
 Ausführliche Informationen zum Speichern von Daten aus mehreren Tabellen finden Sie unter [Exemplarische Vorgehensweise: Speichern von Daten in einer Datenbank \(mehrere Tabellen\)](../data-tools/save-data-to-a-database-multiple-tables.md).  
  
 Wenn Sie zwei oder mehr verknüpfte Tabellen aktualisieren, dann müssen Sie die gesamte Aktualisierungslogik einer Transaktion miteinbeziehen.  Durch den Prozess der Transaktion wird sichergestellt, dass alle mit einer Datenbank verbundenen Änderungen erfolgreich sind, bevor ein Commit der Änderungen ausgeführt wird.  Weitere Informationen finden Sie unter [Transaktionen und Parallelität](../Topic/Transactions%20and%20Concurrency.md).  
  
#### So aktualisieren Sie zwei verknüpfte Tabellen mit einem TableAdapter  
  
1.  Erstellen Sie drei temporäre <xref:System.Data.DataTable> für die unterschiedlichen Datensätze.  
  
2.  Rufen Sie die `Update`\-Methode für jede Teilmenge der Zeilen in einem `try`\/`catch`\-Block auf.  Falls Aktualisierungsfehler auftreten, empfiehlt es sich, die Fehler durch eine Verzweigung zu beheben.  
  
3.  Übertragen Sie die Änderungen vom Dataset in die Datenbank.  
  
4.  Löschen Sie die temporären Datentabellen, um die Ressourcen freizugeben.  
  
     [!code-vb[VbRaddataSaving#27](../data-tools/codesnippet/VisualBasic/how-to-save-dataset-changes-to-a-database_3.vb)]
     [!code-cs[VbRaddataSaving#27](../data-tools/codesnippet/CSharp/how-to-save-dataset-changes-to-a-database_3.cs)]  
  
#### So aktualisieren Sie zwei verknüpfte Tabellen mit einem Datenadapter  
  
-   Rufen Sie die `Update`\-Methode jedes Datenadapters auf.  
  
     Im folgenden Beispiel wird erläutert, wie Sie eine Datenquelle mit einem Dataset aktualisieren, das verknüpfte Tabellen enthält.  Damit die oben angegebene Reihenfolge eingehalten wird, werden drei temporäre <xref:System.Data.DataTable> für die unterschiedlichen Datensätze erstellt.  Anschließend wird die `Update`\-Methode für jede Teilmenge von Zeilen in einem `try`\/`catch`\-Block aufgerufen.  Falls Aktualisierungsfehler auftreten, empfiehlt es sich, die Fehler durch eine Verzweigung zu beheben.  Anschließend führt das Dataset einen Commit für die Änderungen aus.  Löschen Sie abschließend die temporären Datentabellen, um die Ressourcen freizugeben.  
  
     [!code-vb[VbRaddataSaving#28](../data-tools/codesnippet/VisualBasic/how-to-save-dataset-changes-to-a-database_4.vb)]
     [!code-cs[VbRaddataSaving#28](../data-tools/codesnippet/CSharp/how-to-save-dataset-changes-to-a-database_4.cs)]  
  
## Siehe auch  
 [Exemplarische Vorgehensweisen zur Arbeit mit Daten](../Topic/Data%20Walkthroughs.md)   
 [Binden von Windows Forms\-Steuerelementen an Daten in Visual Studio](../data-tools/bind-windows-forms-controls-to-data-in-visual-studio.md)   
 [Herstellen von Datenverbindungen in Visual Studio](../data-tools/connecting-to-data-in-visual-studio.md)   
 [Vorbereiten der Anwendung auf den Empfang von Daten](../Topic/Preparing%20Your%20Application%20to%20Receive%20Data.md)   
 [Abrufen von Daten für die Anwendung](../data-tools/fetching-data-into-your-application.md)   
 [Binden von Steuerelementen an Daten in Visual Studio](../data-tools/bind-controls-to-data-in-visual-studio.md)   
 [Bearbeiten von Daten in der Anwendung](../data-tools/editing-data-in-your-application.md)   
 [Überprüfen von Daten](../Topic/Validating%20Data.md)   
 [Speichern von Daten](../data-tools/saving-data.md)