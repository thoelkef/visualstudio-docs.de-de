---
title: "Gewusst wie: Einf&#252;gen neuer Datens&#228;tze in eine Datenbank | Microsoft Docs"
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
  - "Datenbanken, Einfügen neuer Datensätze in"
  - "Datensätze, Einfügen"
  - "Speichern von Daten"
  - "TableAdapters, Einfügen neuer Datensätze in"
ms.assetid: ea118fff-69b1-4675-b79a-e33374377f04
caps.latest.revision: 11
caps.handback.revision: 8
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# Gewusst wie: Einf&#252;gen neuer Datens&#228;tze in eine Datenbank
Sie können neue Datensätze mithilfe der `TableAdapter.Update`\-Methode oder einer der DBDirect\-Methoden des TableAdapter \(insbesondere der `TableAdapter.Insert`\-Methode\) in eine Datenbank einfügen.  Weitere Informationen finden Sie unter [Übersicht über TableAdapters](../data-tools/tableadapter-overview.md).  
  
 Wenn die Anwendung keine TableAdapters verwendet, können Sie mithilfe von Befehlsobjekten interagieren und Datensätze in die Datenbank einfügen \(z. B. <xref:System.Data.SqlClient.SqlCommand>\).  
  
 Verwenden Sie die `TableAdapter.Update`\-Methode, wenn die Anwendung Datasets zum Speichern von Daten verwendet.  Die `Update`\-Methode überträgt alle Änderungen \(Aktualisierungen, Einfügungen und Löschvorgänge\) in die Datenbank.  
  
 Verwenden Sie die `TableAdapter.Insert`\-Methode, wenn die Anwendung zum Speichern von Daten Objekte verwendet, oder wenn Sie das Erstellen von Datensätzen in der Datenbank detailliert steuern möchten.  
  
 Wenn der TableAdapter nicht über eine `Insert`\-Methode verfügt, ist er entweder so konfiguriert, dass er gespeicherte Prozeduren verwendet, oder seine `GenerateDBDirectMethods`\-Eigenschaft ist auf `false` festgelegt.  Versuchen Sie, aus dem [DataSet\-Designer](../data-tools/creating-and-editing-typed-datasets.md) heraus die `GenerateDBDirectMethods`\-Eigenschaft des TableAdapter auf `true` festzulegen, und speichern Sie das Dataset, um den TableAdapter neu zu generieren.  Wenn der TableAdapter dann immer noch nicht über eine `Insert`\-Methode verfügt, stellt die Tabelle wahrscheinlich keine ausreichenden Schemainformationen zum Unterscheiden zwischen einzelnen Zeilen zur Verfügung \(z. B. ist kein Primärschlüssel in der Tabelle festgelegt\).  
  
## Einfügen neuer Datensätze mithilfe von TableAdapters  
 TableAdapters bieten verschiedene Möglichkeiten, neue Datensätze abhängig von den Anforderungen der Anwendung in eine Datenbank einzufügen.  
  
 Wenn die Anwendung Daten mithilfe von Datasets speichert, können Sie die Datensätze einfach der gewünschten <xref:System.Data.DataTable> im Dataset hinzufügen und dann die `TableAdapter.Update`\-Methode aufrufen.  Die `TableAdapter.Update`\-Methode nimmt alle an der <xref:System.Data.DataTable> vorgenommenen Änderungen entgegen und überträgt die Änderungen in die Datenbank \(z. B. geänderte und gelöschte Datensätze\).  
  
#### So fügen Sie neue Datensätze mithilfe der TableAdapter.Update\-Methode in eine Datenbank ein  
  
1.  Fügen Sie der gewünschten <xref:System.Data.DataTable> neue Datensätze hinzu, indem Sie eine neue <xref:System.Data.DataRow> erstellen und sie der <xref:System.Data.DataTable.Rows%2A>\-Auflistung hinzufügen.  Weitere Informationen finden Sie unter [Gewusst wie: Hinzufügen von Zeilen zu einer DataTable](../Topic/How%20to:%20Add%20Rows%20to%20a%20DataTable.md).  
  
2.  Nachdem die neuen Zeilen der <xref:System.Data.DataTable> hinzugefügt wurden, rufen Sie die `TableAdapter.Update`\-Methode auf.  Sie können die zu aktualisierende Datenmenge steuern, indem Sie ein <xref:System.Data.DataSet>, eine <xref:System.Data.DataTable>, ein Array von <xref:System.Data.DataRow>s oder eine einzelne <xref:System.Data.DataRow> übergeben.  
  
     Der folgende Code veranschaulicht, wie einer <xref:System.Data.DataTable> ein neuer Datensatz hinzugefügt und anschließend die `TableAdapter.Update`\-Methode aufgerufen wird, um die neue Zeile in der Datenbank zu speichern.  \(In diesem Beispiel wird die Tabelle `Region` der Datenbank Northwind verwendet.\)  
  
     [!code-vb[VbRaddataSaving#14](../data-tools/codesnippet/VisualBasic/insert-new-records-into-a-database_1.vb)]
     [!code-cs[VbRaddataSaving#14](../data-tools/codesnippet/CSharp/insert-new-records-into-a-database_1.cs)]  
  
 Wenn die Anwendung Daten mithilfe von Objekten in der Anwendung speichert, können Sie mit der `TableAdapter.Insert`\-Methode Zeilen direkt in der Datenbank erstellen.  Die `Insert`\-Methode nimmt die einzelnen Werte für jede Spalte als Parameter an.  Beim Aufrufen der Methode wird ein neuer Datensatz mit den übergebenen Parameterwerten in die Datenbank eingefügt.  
  
 In der folgenden Prozedur wird als Beispiel die Tabelle `Region` der Datenbank Northwind verwendet.  
  
#### So fügen Sie neue Datensätze mithilfe der TableAdapter.Insert\-Methode in eine Datenbank ein  
  
-   Rufen Sie die `Insert`\-Methode des TableAdapter auf, und übergeben Sie die Werte für jede Spalte als Parameter.  
  
    > [!NOTE]
    >  Wenn Ihnen keine Instanz zur Verfügung steht, instanziieren Sie den TableAdapter, den Sie verwenden möchten.  
  
     [!code-vb[VbRaddataSaving#15](../data-tools/codesnippet/VisualBasic/insert-new-records-into-a-database_2.vb)]
     [!code-cs[VbRaddataSaving#15](../data-tools/codesnippet/CSharp/insert-new-records-into-a-database_2.cs)]  
  
## Einfügen neuer Datensätze mithilfe von Befehlsobjekten  
 Im folgenden Beispiel werden mithilfe von Befehlsobjekten neue Datensätze direkt in eine Datenbank eingefügt.  Weitere Informationen zum Verwenden von Befehlsobjekten, um Befehle und gespeicherte Prozeduren auszuführen, finden Sie unter [Abrufen von Daten für die Anwendung](../data-tools/fetching-data-into-your-application.md).  
  
 In der folgenden Prozedur wird als Beispiel die Tabelle `Region` der Datenbank Northwind verwendet.  
  
#### So fügen Sie neue Datensätze mithilfe von Befehlsobjekten in eine Datenbank ein  
  
-   Erstellen Sie ein neues Befehlsobjekt, und legen Sie die entsprechenden Eigenschaften `Connection`, `CommandType` und `CommandText` fest.  
  
     [!code-vb[VbRaddataSaving#16](../data-tools/codesnippet/VisualBasic/insert-new-records-into-a-database_3.vb)]
     [!code-cs[VbRaddataSaving#16](../data-tools/codesnippet/CSharp/insert-new-records-into-a-database_3.cs)]  
  
## .NET Framework-Sicherheit  
 Sie müssen über den Zugriff auf die Datenbank verfügen, zu der Sie eine Verbindung herstellen möchten. Außerdem müssen Sie über die Berechtigung zum Einfügen von Datensätzen in die gewünschte Tabelle verfügen.  
  
## Siehe auch  
 [Gewusst wie: Löschen von Datensätzen in einer Datenbank](../data-tools/how-to-delete-records-in-a-database.md)   
 [Gewusst wie: Aktualisieren von Datensätzen in einer Datenbank](../data-tools/how-to-update-records-in-a-database.md)   
 [Gewusst wie: Speichern von Daten aus einem Objekt in einer Datenbank](../data-tools/save-data-from-an-object-to-a-database.md)   
 [Übersicht über Datenanwendungen in Visual Studio](../data-tools/overview-of-data-applications-in-visual-studio.md)   
 [Herstellen von Datenverbindungen in Visual Studio](../data-tools/connecting-to-data-in-visual-studio.md)   
 [Vorbereiten der Anwendung auf den Empfang von Daten](../Topic/Preparing%20Your%20Application%20to%20Receive%20Data.md)   
 [Abrufen von Daten für die Anwendung](../data-tools/fetching-data-into-your-application.md)   
 [Binden von Steuerelementen an Daten in Visual Studio](../data-tools/bind-controls-to-data-in-visual-studio.md)   
 [Bearbeiten von Daten in der Anwendung](../data-tools/editing-data-in-your-application.md)   
 [Überprüfen von Daten](../Topic/Validating%20Data.md)   
 [Speichern von Daten](../data-tools/saving-data.md)   
 [Abrufen von Identitäts\- oder AutoWert\-Werten](../Topic/Retrieving%20Identity%20or%20Autonumber%20Values.md)