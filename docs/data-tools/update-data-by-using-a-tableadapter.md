---
title: "Gewusst wie: Aktualisieren von Daten mit einem TableAdapter | Microsoft Docs"
ms.custom: ""
ms.date: "12/14/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
dev_langs: 
  - "VB"
  - "CSharp"
  - "C++"
  - "aspx"
helpviewer_keywords: 
  - "Daten [Visual Studio], Speichern"
  - "Daten [Visual Studio], TableAdapters"
  - "Daten [Visual Studio], Aktualisieren"
  - "Speichern von Daten"
  - "TableAdapters, Aktualisieren von Daten"
  - "Aktualisieren von Daten, TableAdapters"
ms.assetid: 5e32e10e-9bac-4969-9bdd-b8f6919d3516
caps.latest.revision: 15
caps.handback.revision: 11
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# Gewusst wie: Aktualisieren von Daten mit einem TableAdapter
Nachdem die Daten im Dataset geändert und überprüft wurden, möchten Sie die aktualisierten Daten möglicherweise an die Datenbank zurücksenden.  Um die geänderten Daten an eine Datenbank zu senden, rufen Sie die `Update`\-Methode für einen [TableAdapter](../data-tools/tableadapter-overview.md) auf.  Die `Update`\-Methode des Adapters aktualisiert eine einzelne Datentabelle und führt auf der Grundlage des <xref:System.Data.DataRow.RowState%2A> der einzelnen Datenzeilen in der Tabelle den entsprechenden Befehl \(INSERT, UPDATE oder DELETE\) aus.  Beim Speichern von Daten in verknüpften Tabellen wird von Visual Studio eine neue TableAdapterManager\-Komponente bereitgestellt, die beim Speichern in der korrekten Reihenfolge basierend auf den in der Datenbank festgelegten Fremdschlüsseleinschränkungen hilft.  Weitere Informationen finden Sie unter [Übersicht über die hierarchische Aktualisierung](../Topic/Hierarchical%20Update%20Overview.md).  
  
> [!NOTE]
>  Da bei dem Versuch, eine Datenquelle mit dem Inhalt eines DataSet zu aktualisieren, Fehler auftreten können, sollte der Code, der die `Update`\-Methode des Adapters aufruft, in einem `try`\/`catch`\-Block platziert werden.  
  
 Die genaue Verfahrensweise zum Aktualisieren einer Datenquelle kann je nach Unternehmensanforderungen variieren. Die folgenden Schritte sollten jedoch von der Anwendung ausgeführt werden:  
  
1.  Rufen Sie die `Update`\-Methode des Adapters in einem `try`\/`catch`\-Block auf.  
  
2.  Lokalisieren der fehlerhaften Datenzeile, falls eine Ausnahme abgefangen wird.  Weitere Informationen finden Sie unter [Gewusst wie: Suchen nach Zeilen mit Fehlern](../Topic/How%20to:%20Locate%20Rows%20that%20Have%20Errors.md).  
  
3.  Beheben Sie das Problem in der Datenzeile \(möglichst programmgesteuert oder indem die ungültige Zeile dem Benutzer zur Änderung angezeigt wird\), und wiederholen Sie dann den Aktualisierungsversuch \(<xref:System.Data.DataRow.HasErrors%2A>, <xref:System.Data.DataTable.GetErrors%2A>\).  
  
## Speichern von Daten in einer Datenbank  
 Rufen Sie die `Update`\-Methode eines TableAdapter auf, und übergeben Sie den Namen der Datentabelle, die die in die Datenbank zu schreibenden Werte enthält.  
  
#### So aktualisieren Sie eine Datenbank mit einem DataSet mithilfe eines TableAdapter  
  
-   Schließen Sie die `Update`\-Methode des Adapters in einen `try`\/`catch`\-Block ein.  Im folgenden Beispiel wird veranschaulicht, wie eine Aktualisierung mit dem Inhalt der `Customers`\-Tabelle in `NorthwindDataSet` innerhalb eines `try`\/`catch`\-Blocks versucht wird.  
  
     [!code-cs[VbRaddataSaving#9](../data-tools/codesnippet/CSharp/update-data-by-using-a-tableadapter_1.cs)]
     [!code-vb[VbRaddataSaving#9](../data-tools/codesnippet/VisualBasic/update-data-by-using-a-tableadapter_1.vb)]  
  
## Aktualisieren von zwei verknüpften Tabellen in einem Dataset mittels TableAdapter  
 Bei der Aktualisierung verknüpfter Tabellen in einem DatasSet muss die richtige Reihenfolge eingehalten werden, damit nicht unnötig Einschränkungen für die referenzielle Integrität verletzt werden.  Die in der Befehlsausführung verwendete Abfolge richtet sich zusätzlich nach den Indizes von <xref:System.Data.DataRowCollection> im Dataset.  Um zu verhindern, dass Integritätsfehler ausgelöst werden, wird bei der Aktualisierung der Datenbank die folgende Reihenfolge empfohlen:  
  
1.  Untergeordnete Tabelle: Datensätze löschen.  
  
2.  Übergeordnete Tabelle: Datensätze einfügen, aktualisieren und löschen.  
  
3.  Untergeordnete Tabelle: Datensätze einfügen und aktualisieren.  
  
    > [!NOTE]
    >  Wenn Sie zwei oder mehr verknüpfte Tabellen aktualisieren, muss die gesamte Aktualisierungslogik in einer Transaktion enthalten sein.  Eine Transaktion ist ein Prozess zum Sicherstellen, dass alle mit einer Datenbank verbundenen Änderungen erfolgreich sind, bevor ein Commit der Änderungen ausgeführt wird.  Weitere Informationen finden Sie unter [Transaktionen und Parallelität](../Topic/Transactions%20and%20Concurrency.md).  
  
#### So aktualisieren Sie zwei verknüpfte Tabellen mit einem TableAdapter  
  
1.  Erstellen Sie drei temporäre Datentabellen, die die unterschiedlichen Datensätze enthalten.  
  
2.  Rufen Sie die `Update`\-Methode für jede Teilmenge der Zeilen in einem `try`\/`catch`\-Block auf.  Wenn Aktualisierungsfehler auftreten, müssen diese durch eine Verzweigung behoben werden.  
  
3.  Übernehmen Sie die Änderungen in der Datenbank.  
  
4.  Löschen Sie die temporären Datentabellen, um die Ressourcen freizugeben.  
  
     Im folgenden Beispiel wird erläutert, wie Sie eine Datenquelle mit einem Dataset aktualisieren, das verknüpfte Tabellen enthält.  
  
     [!code-vb[VbRaddataSaving#27](../data-tools/codesnippet/VisualBasic/update-data-by-using-a-tableadapter_2.vb)]
     [!code-cs[VbRaddataSaving#27](../data-tools/codesnippet/CSharp/update-data-by-using-a-tableadapter_2.cs)]  
  
## Siehe auch  
 [Übersicht über TableAdapters](../data-tools/tableadapter-overview.md)   
 [Exemplarische Vorgehensweisen zur Arbeit mit Daten](../Topic/Data%20Walkthroughs.md)   
 [Binden von Windows Forms\-Steuerelementen an Daten in Visual Studio](../data-tools/bind-windows-forms-controls-to-data-in-visual-studio.md)   
 [Herstellen von Datenverbindungen in Visual Studio](../data-tools/connecting-to-data-in-visual-studio.md)   
 [Vorbereiten der Anwendung auf den Empfang von Daten](../Topic/Preparing%20Your%20Application%20to%20Receive%20Data.md)   
 [Abrufen von Daten für die Anwendung](../data-tools/fetching-data-into-your-application.md)   
 [Binden von Steuerelementen an Daten in Visual Studio](../data-tools/bind-controls-to-data-in-visual-studio.md)   
 [Bearbeiten von Daten in der Anwendung](../data-tools/editing-data-in-your-application.md)   
 [Überprüfen von Daten](../Topic/Validating%20Data.md)   
 [Speichern von Daten](../data-tools/saving-data.md)