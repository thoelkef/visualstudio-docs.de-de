---
title: "Gewusst wie: L&#246;schen von Datens&#228;tzen in einer Datenbank | Microsoft Docs"
ms.custom: ""
ms.date: "09/21/2016"
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
  - "Datenbanken, Löschen von Datensätzen"
  - "Löschen von Daten"
  - "Datensätze, Löschen"
  - "Speichern von Daten"
  - "TableAdapter.Delete-Methode"
  - "TableAdapter.Update-Methode"
ms.assetid: d74d2130-9732-4648-abea-241059c4a372
caps.latest.revision: 11
caps.handback.revision: 11
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
robots: noindex,nofollow
---
# Gewusst wie: L&#246;schen von Datens&#228;tzen in einer Datenbank
Verwenden Sie zum Löschen von Datensätzen aus einer Datenbank die `TableAdapter.Update`\-Methode oder die `TableAdapter.Delete`\-Methode.  Wenn die Anwendung keine TableAdapters verwendet, können Sie Datensätze auch mit Befehlsobjekten aus der Datenbank löschen \(z. B. <xref:System.Data.SqlClient.SqlCommand.ExecuteNonQuery%2A>\).  
  
 Die `TableAdapter.Update`\-Methode wird i. d. R. verwendet, wenn die Anwendung Daten mithilfe von Datasets speichert, während die `TableAdapter.Delete`\-Methode normalerweise verwendet wird, wenn die Anwendung Objekte zum Speichern verwendet.  
  
 Wenn der TableAdapter nicht über eine `Delete`\-Methode verfügt, ist er entweder so konfiguriert, dass er gespeicherte Prozeduren verwendet, oder seine `GenerateDBDirectMethods`\-Eigenschaft ist auf `false` festgelegt.  Versuchen Sie, aus dem [DataSet\-Designer](../data-tools/creating-and-editing-typed-datasets.md) heraus die `GenerateDBDirectMethods`\-Eigenschaft des TableAdapter auf `true` festzulegen, und speichern Sie das Dataset, um den TableAdapter neu zu generieren.  Wenn der TableAdapter dann immer noch nicht über eine `Delete`\-Methode verfügt, stellt die Tabelle wahrscheinlich keine ausreichenden Schemainformationen zum Unterscheiden zwischen einzelnen Zeilen zur Verfügung \(z. B. ist kein Primärschlüssel in der Tabelle festgelegt\).  
  
## Löschen von Datensätzen mithilfe von TableAdapters  
 TableAdapters bieten verschiedene Möglichkeiten, Datensätze abhängig von den Anforderungen der Anwendung aus einer Datenbank zu löschen.  
  
 Wenn die Anwendung Daten mithilfe von Datasets speichert, können Sie die Datensätze einfach aus der gewünschten <xref:System.Data.DataTable> im <xref:System.Data.DataSet> löschen und dann die `TableAdapter.Update`\-Methode aufrufen.  Die `TableAdapter.Update`\-Methode überträgt alle an der Datentabelle vorgenommenen Änderungen in die Datenbank \(z. B. eingefügte, aktualisierte und gelöschte Datensätze\).  
  
#### So löschen Sie Datensätze mithilfe der TableAdapter.Update\-Methode aus einer Datenbank  
  
-   Löschen Sie Datensätze aus der gewünschten <xref:System.Data.DataTable>, indem Sie <xref:System.Data.DataRow>\-Objekte aus der Tabelle löschen.  Weitere Informationen finden Sie unter [Gewusst wie: Löschen von Zeilen in einer DataTable](../Topic/How%20to:%20Delete%20Rows%20in%20a%20DataTable.md).  Nachdem die Zeilen aus der <xref:System.Data.DataTable> gelöscht wurden, rufen Sie die `TableAdapter.Update`\-Methode auf.  Sie können die zu aktualisierende Datenmenge steuern, indem Sie ein <xref:System.Data.DataSet>, eine <xref:System.Data.DataTable>, ein Array von <xref:System.Data.DataRow>s oder eine einzelne <xref:System.Data.DataRow> übergeben.  Der folgende Code veranschaulicht, wie ein Datensatz aus einer <xref:System.Data.DataTable> gelöscht und anschließend die `TableAdapter.Update`\-Methode aufgerufen wird, um die Änderung mitzuteilen und die Zeile aus der Datenbank zu löschen.  \(In diesem Beispiel wird die Tabelle `Region` der Datenbank Northwind verwendet.\)  
  
     [!code-vb[VbRaddataSaving#20](../data-tools/codesnippet/VisualBasic/how-to-delete-records-in-a-database_1.vb)]
     [!code-cs[VbRaddataSaving#20](../data-tools/codesnippet/CSharp/how-to-delete-records-in-a-database_1.cs)]  
  
 Wenn die Anwendung Daten mithilfe von Objekten in der Anwendung speichert, können Sie mit den DBDirect\-Methoden des TableAdapter Daten direkt aus der Datenbank löschen.  Beim Aufrufen der `Delete`\-Methode werden Datensätze basierend auf den übergebenen Parameterwerten aus der Datenbank entfernt.  
  
#### So löschen Sie Datensätze mithilfe der TableAdapter.Delete\-Methode aus einer Datenbank  
  
-   Rufen Sie die `Delete`\-Methode des TableAdapter auf, und übergeben Sie der `Delete`\-Methode die Werte für alle Spalten als Parameter.  \(In diesem Beispiel wird die Tabelle `Region` der Datenbank Northwind verwendet.\)  
  
    > [!NOTE]
    >  Wenn Ihnen keine Instanz zur Verfügung steht, instanziieren Sie den TableAdapter, den Sie verwenden möchten.  
  
     [!code-vb[VbRaddataSaving#21](../data-tools/codesnippet/VisualBasic/how-to-delete-records-in-a-database_2.vb)]
     [!code-cs[VbRaddataSaving#21](../data-tools/codesnippet/CSharp/how-to-delete-records-in-a-database_2.cs)]  
  
## Löschen von Datensätzen mithilfe von Befehlsobjekten  
 Im folgenden Beispiel werden Datensätze mithilfe von Befehlsobjekten direkt aus einer Datenbank gelöscht.  Weitere Informationen zum Verwenden von Befehlsobjekten, um Befehle und gespeicherte Prozeduren auszuführen, finden Sie unter [Abrufen von Daten für die Anwendung](../data-tools/fetching-data-into-your-application.md).  
  
#### So löschen Sie Datensätze mithilfe von Befehlsobjekten aus einer Datenbank  
  
-   Erstellen Sie ein neues Befehlsobjekt, und legen Sie die entsprechenden Eigenschaften `Connection`, `CommandType` und `CommandText` fest.  \(In diesem Beispiel wird die Tabelle `Region` der Datenbank Northwind verwendet.\)  
  
     [!code-vb[VbRaddataSaving#22](../data-tools/codesnippet/VisualBasic/how-to-delete-records-in-a-database_3.vb)]
     [!code-cs[VbRaddataSaving#22](../data-tools/codesnippet/CSharp/how-to-delete-records-in-a-database_3.cs)]  
  
## .NET Framework-Sicherheit  
 Sie müssen über Zugriff auf die Datenbank verfügen, mit der Sie eine Verbindung herstellen möchten. Außerdem müssen Sie über die Berechtigung zum Löschen von Datensätzen aus der gewünschten Tabelle verfügen.  
  
## Siehe auch  
 [Übersicht über TableAdapters](../data-tools/tableadapter-overview.md)   
 [Gewusst wie: Einfügen neuer Datensätze in eine Datenbank](../data-tools/insert-new-records-into-a-database.md)   
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