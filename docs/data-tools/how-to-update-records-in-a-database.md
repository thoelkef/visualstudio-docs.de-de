---
title: "Gewusst wie: Aktualisieren von Datens&#228;tzen in einer Datenbank | Microsoft Docs"
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
  - "Datenbanken, Aktualisieren"
  - "Datensätze, Bearbeiten"
  - "Datensätze, Aktualisieren"
  - "TableAdapter.Update-Methode"
ms.assetid: cdc8a8e4-a5fa-40dd-9221-97b8571d802a
caps.latest.revision: 10
caps.handback.revision: 10
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
robots: noindex,nofollow
---
# Gewusst wie: Aktualisieren von Datens&#228;tzen in einer Datenbank
Mithilfe der `TableAdapter.Update`\-Methode können Sie Datensätze in einer Datenbank aktualisieren \(bearbeiten\).  Die `TableAdapter.Update`\-Methode stellt mehrere Überladungen zur Verfügung, die abhängig von den übergebenen Parametern verschiedene Vorgänge ausführen.  Es ist wichtig, dass Sie wissen, zu welchen Ergebnissen das Aufrufen dieser Methodensignaturen führt.  
  
> [!NOTE]
>  Wenn die Anwendung keine TableAdapters verwendet, können Sie Datensätze in der Datenbank mit Befehlsobjekten aktualisieren \(z. B. <xref:System.Data.SqlClient.SqlCommand.ExecuteNonQuery%2A>\).  Weitere Informationen zum Aktualisieren von Daten mit Befehlsobjekten finden Sie weiter unten im Abschnitt "Aktualisieren von Datensätzen mithilfe von Befehlsobjekten".  
  
 In der folgenden Tabelle wird das Verhalten der verschiedenen `TableAdapter.Update`\-Methoden beschrieben:  
  
|Methode|Beschreibung|  
|-------------|------------------|  
|`TableAdapter.Update(DataTable)`|Versucht, alle an der <xref:System.Data.DataTable> vorgenommenen Änderungen in der Datenbank zu speichern.  \(Dazu zählt das Entfernen von aus der Tabelle gelöschten Zeilen, das Hinzufügen von in die Tabelle eingefügten Zeilen oder das Aktualisieren von geänderten Zeilen in der Tabelle.\)|  
|`TableAdapter.Update(DataSet)`|Obwohl ein Dataset als Parameter verwendet wird, versucht der TableAdapter, alle Änderungen an der mit dem TableAdapter verknüpften <xref:System.Data.DataTable> in der Datenbank zu speichern.  \(Dazu zählt das Entfernen von aus der Tabelle gelöschten Zeilen, das Hinzufügen von in die Tabelle eingefügten Zeilen oder das Aktualisieren von geänderten Zeilen in der Tabelle.\) **Note:**  Bei der mit einem TableAdapter verknüpften <xref:System.Data.DataTable> handelt es sich um die <xref:System.Data.DataTable>, die bei der ursprünglichen Konfiguration des TableAdapter erstellt wurde.|  
|`TableAdapter.Update(DataRow)`|Versucht, die an der angegebenen <xref:System.Data.DataRow> vorgenommenen Änderungen in der Datenbank zu speichern.|  
|`TableAdapter.Update(DataRows())`|Versucht, die an allen Zeilen im Array von <xref:System.Data.DataRow>s vorgenommenen Änderungen in der Datenbank zu speichern.|  
|`TableAdapter.Update("new column values", "original column values")`|Versucht, Änderungen an einer einzelnen Zeile zu speichern, die durch die ursprünglichen Spaltenwerte identifiziert wird.|  
  
 Wenn die Anwendung ausschließlich Datasets zum Speichern von Daten verwendet, wird in der Regel die `TableAdapter.Update`\-Methode verwendet, die ein <xref:System.Data.DataSet>, eine <xref:System.Data.DataTable> oder <xref:System.Data.DataRow>\(s\) entgegennimmt.  
  
 Wenn die Anwendung Objekte zum Speichern von Daten verwendet, wird in der Regel die `TableAdapter.Update`\-Methode verwendet, die Spaltenwerte entgegennimmt.  
  
 Wenn der TableAdapter nicht über eine `Update`\-Methode verfügt, die Spaltenwerte entgegennimmt, ist er entweder so konfiguriert, dass er gespeicherte Prozeduren verwendet, oder seine `GenerateDBDirectMethods`\-Eigenschaft ist auf `false` festgelegt.  Versuchen Sie, aus dem [DataSet\-Designer](../data-tools/creating-and-editing-typed-datasets.md) heraus die `GenerateDBDirectMethods`\-Eigenschaft des TableAdapter auf `true` festzulegen, und speichern Sie das Dataset, um den TableAdapter neu zu generieren.  Wenn der TableAdapter dann immer noch nicht über eine `Update`\-Methode verfügt, die Spaltenwerte verwendet, stellt die Tabelle wahrscheinlich keine ausreichenden Schemainformationen zum Unterscheiden zwischen einzelnen Zeilen zur Verfügung \(z. B. ist kein Primärschlüssel in der Tabelle festgelegt\).  
  
## Aktualisieren vorhandener Datensätze mithilfe von TableAdapters  
 TableAdapters bieten verschiedene Möglichkeiten, Datensätze in einer Datenbank abhängig von den Anforderungen der Anwendung zu aktualisieren.  
  
 Wenn die Anwendung Daten mithilfe von Datasets speichert, können Sie die Datensätze einfach in der gewünschten <xref:System.Data.DataTable> aktualisieren und anschließend die `TableAdapter.Update`\-Methode aufrufen und das <xref:System.Data.DataSet>, die <xref:System.Data.DataTable>, die <xref:System.Data.DataRow> oder ein Array von <xref:System.Data.DataRow>s übergeben.  Die verschiedenen `Update`\-Methoden werden in der vorstehenden Tabelle beschrieben.  
  
#### So aktualisieren Sie Datensätze in einer Datenbank mithilfe der TableAdapter.Update\-Methode, die DataSet, DataTable, DataRow oder DataRows\(\) verwendet  
  
1.  Bearbeiten Sie Datensätze in der gewünschten <xref:System.Data.DataTable>, indem Sie die <xref:System.Data.DataRow> direkt in der <xref:System.Data.DataTable> bearbeiten.  Weitere Informationen finden Sie unter [Gewusst wie: Bearbeiten von Zeilen in einer DataTable](../Topic/How%20to:%20Edit%20Rows%20in%20a%20DataTable.md).  
  
2.  Nachdem die Zeilen in der <xref:System.Data.DataTable> bearbeitet wurden, rufen Sie die `TableAdapter.Update`\-Methode auf.  Sie können die zu aktualisierende Datenmenge steuern, indem Sie ein <xref:System.Data.DataSet>, eine <xref:System.Data.DataTable>, ein Array von <xref:System.Data.DataRow>s oder eine einzelne <xref:System.Data.DataRow> übergeben.  
  
     Der folgende Code veranschaulicht, wie ein Datensatz in einer <xref:System.Data.DataTable> bearbeitet und anschließend die `TableAdapter.Update`\-Methode aufgerufen wird, um die Änderungen in der Datenbank zu speichern.  \(In diesem Beispiel wird die Tabelle Region der Datenbank Northwind verwendet.\)  
  
     [!code-vb[VbRaddataSaving#17](../data-tools/codesnippet/VisualBasic/how-to-update-records-in-a-database_1.vb)]
     [!code-cs[VbRaddataSaving#17](../data-tools/codesnippet/CSharp/how-to-update-records-in-a-database_1.cs)]  
  
 Wenn die Anwendung mithilfe von Objekten Daten in der Anwendung speichert, können Sie mit den `DBDirect`\-Methoden des TableAdapter Daten direkt aus den Objekten an die Datenbank senden.  Mithilfe dieser Methoden können Sie einzelne Werte für jede Spalte als Methodenparameter übergeben.  Durch das Aufrufen dieser Methode wird ein vorhandener Datensatz in der Datenbank mit den an die Methode übergebenen Spaltenwerten aktualisiert.  
  
 In der folgenden Prozedur wird als Beispiel die Tabelle `Region` der Datenbank Northwind verwendet.  
  
#### So aktualisieren Sie Datensätze in einer Datenbank mithilfe der TableAdapter.Update\-Methode, die Spaltenwerte verwendet  
  
-   Rufen Sie die `Update`\-Methode des TableAdapter auf, um die neuen und ursprünglichen Werte für jede Spalte als Parameter zu übergeben.  
  
    > [!NOTE]
    >  Wenn Ihnen keine Instanz zur Verfügung steht, instanziieren Sie den TableAdapter, den Sie verwenden möchten.  
  
     [!code-vb[VbRaddataSaving#18](../data-tools/codesnippet/VisualBasic/how-to-update-records-in-a-database_2.vb)]
     [!code-cs[VbRaddataSaving#18](../data-tools/codesnippet/CSharp/how-to-update-records-in-a-database_2.cs)]  
  
## Aktualisieren von Datensätzen mithilfe von Befehlsobjekten  
 Im folgenden Beispiel werden vorhandene Datensätze mithilfe von Befehlsobjekten direkt in einer Datenbank aktualisiert.  Weitere Informationen zum Verwenden von Befehlsobjekten, um Befehle und gespeicherte Prozeduren auszuführen, finden Sie unter [Abrufen von Daten für die Anwendung](../data-tools/fetching-data-into-your-application.md).  
  
 In der folgenden Prozedur wird als Beispiel die Tabelle `Region` der Datenbank Northwind verwendet.  
  
#### So aktualisieren Sie vorhandene Datensätze in einer Datenbank mithilfe von Befehlsobjekten  
  
-   Erstellen Sie ein neues Befehlsobjekt, legen Sie die Eigenschaften `Connection`, `CommandType` und `CommandText` fest, stellen Sie eine Verbindung her, und führen Sie den Befehl aus.  
  
     [!code-vb[VbRaddataSaving#19](../data-tools/codesnippet/VisualBasic/how-to-update-records-in-a-database_3.vb)]
     [!code-cs[VbRaddataSaving#19](../data-tools/codesnippet/CSharp/how-to-update-records-in-a-database_3.cs)]  
  
## .NET Framework-Sicherheit  
 Sie müssen über den Zugriff auf die Datenbank verfügen, zu der Sie eine Verbindung herstellen möchten. Außerdem müssen Sie über die Berechtigung zum Aktualisieren von Datensätzen in der gewünschten Tabelle verfügen.  
  
## Siehe auch  
 [Übersicht über TableAdapters](../data-tools/tableadapter-overview.md)   
 [Gewusst wie: Löschen von Datensätzen in einer Datenbank](../data-tools/how-to-delete-records-in-a-database.md)   
 [Gewusst wie: Einfügen neuer Datensätze in eine Datenbank](../data-tools/insert-new-records-into-a-database.md)   
 [Gewusst wie: Speichern von Daten aus einem Objekt in einer Datenbank](../data-tools/save-data-from-an-object-to-a-database.md)   
 [Übersicht über Datenanwendungen in Visual Studio](../data-tools/overview-of-data-applications-in-visual-studio.md)   
 [Herstellen von Datenverbindungen in Visual Studio](../data-tools/connecting-to-data-in-visual-studio.md)   
 [Vorbereiten der Anwendung auf den Empfang von Daten](../Topic/Preparing%20Your%20Application%20to%20Receive%20Data.md)   
 [Abrufen von Daten für die Anwendung](../data-tools/fetching-data-into-your-application.md)   
 [Binden von Steuerelementen an Daten in Visual Studio](../data-tools/bind-controls-to-data-in-visual-studio.md)   
 [Bearbeiten von Daten in der Anwendung](../data-tools/editing-data-in-your-application.md)   
 [Überprüfen von Daten](../Topic/Validating%20Data.md)   
 [Speichern von Daten](../data-tools/saving-data.md)