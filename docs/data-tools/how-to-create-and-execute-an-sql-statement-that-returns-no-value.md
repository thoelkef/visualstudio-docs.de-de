---
title: "Gewusst wie: Erstellen und Ausf&#252;hren einer SQL-Anweisung, die keinen Wert zur&#252;ckgibt | Microsoft Docs"
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
  - "Aufrufen von Methoden, Beispiele"
  - "Methodenaufrufe, Beispiele"
  - "SQL-Anweisungen, Erstellen"
  - "SQL-Anweisungen, Ausführen"
ms.assetid: 612d3046-0cfa-4d90-be6e-c4d6bcbd5aee
caps.latest.revision: 23
caps.handback.revision: 23
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
robots: noindex,nofollow
---
# Gewusst wie: Erstellen und Ausf&#252;hren einer SQL-Anweisung, die keinen Wert zur&#252;ckgibt
Zum Ausführen einer SQL\-Anweisung, die keinen Wert zurückgibt, können Sie eine TableAdapter\-Abfrage ausführen, die so konfiguriert ist, dass sie eine SQL\-Anweisung ausführt \(beispielsweise `CustomersTableAdapter.UpdateTableData(CustomersDataTable)`\).  
  
 Wenn die Anwendung keine TableAdapters verwendet, rufen Sie die `ExecuteNonQuery`\-Methode eines Befehlsobjekts auf, und legen Sie für dessen `CommandType`\-Eigenschaft <xref:System.Data.CommandType> fest.  \(Der Begriff "Befehlsobjekt" bezieht sich auf den spezifischen Befehl für den [.NET Framework\-Datenanbieter](../Topic/.NET%20Framework%20Data%20Providers.md), den die Anwendung verwendet.  Wenn in Ihrer Anwendung z. B. der .NET Framework\-Datenanbieter für SQL Server verwendet wird, lautet das Befehlsobjekt <xref:System.Data.SqlClient.SqlCommand>.\)  
  
 Die folgenden Beispiele zeigen, wie SQL\-Anweisungen ausgeführt werden, die mithilfe von TableAdapter\-Objekten oder Befehlsobjekten keinen Datenbankwert zurückgeben.  Weitere Informationen zu Abfragen mit TableAdapters und Befehlen finden Sie unter [Auffüllen von Datasets mit Daten](../data-tools/fill-datasets-by-using-tableadapters.md).  
  
## Ausführen von SQL\-Anweisungen, die keine Werte zurückgeben, mit einem TableAdapter  
 Dieses Beispiel veranschaulicht das Erstellen einer TableAdapter\-Abfrage mit dem [TableAdapter\-Abfragekonfigurations\-Assistent](../data-tools/editing-tableadapters.md). Darüber hinaus enthält es Informationen zum Deklarieren einer Instanz des TableAdapter und zum Ausführen der Abfrage.  
  
 [!INCLUDE[note_settings_general](../data-tools/includes/note_settings_general_md.md)]  
  
#### So erstellen Sie eine SQL\-Anweisung, die keinen Wert zurückgibt, mit einem TableAdapter  
  
1.  Öffnen Sie ein Dataset im **Dataset\-Designer**.  Weitere Informationen finden Sie unter [Gewusst wie: Öffnen eines Datasets im DataSet\-Designer](../Topic/How%20to:%20Open%20a%20Dataset%20in%20the%20Dataset%20Designer.md).  
  
2.  Erstellen Sie einen TableAdapter, falls noch keiner vorhanden ist.  Weitere Informationen zum Erstellen von TableAdapters finden Sie unter [Gewusst wie: Erstellen von TableAdapters](../data-tools/create-and-configure-tableadapters.md).  
  
3.  Wenn im TableAdapter bereits eine Abfrage vorhanden ist, die unter Verwendung einer SQL\-Anweisung keinen Wert zurückgibt, fahren Sie mit der nächsten Verfahrensanweisung im Abschnitt "So deklarieren Sie eine Instanz des TableAdapter und führen die Abfrage aus" fort. Fahren Sie andernfalls mit Schritt 4 fort, um eine neue Abfrage zu erstellen, die keinen Wert zurückgibt.  
  
4.  Klicken Sie mit der rechten Maustaste auf den gewünschten TableAdapter, und verwenden Sie das Kontextmenü, um eine Abfrage hinzuzufügen.  
  
     Der **Konfigurations\-Assistent für TableAdapter\-Abfragen** wird geöffnet.  
  
5.  Behalten Sie den Standardwert von **SQL\-Anweisungen verwenden** bei, und klicken Sie auf **Weiter**.  
  
6.  Wählen Sie die Option **UPDATE**, **INSERT** oder **DELETE** aus, und klicken Sie dann auf **Weiter**.  
  
7.  Geben Sie die SQL\-Anweisung ein, oder verwenden Sie den **Abfrage\-Generator**, wenn Sie beim Erstellen Hilfe benötigen. Klicken Sie anschließend auf **Weiter**.  
  
8.  Geben Sie einen Namen für die Abfrage an.  
  
9. Stellen Sie den Assistenten fertig. Die Abfrage wird dem TableAdapter hinzugefügt.  
  
10. Erstellen Sie das Projekt.  
  
#### So deklarieren Sie eine Instanz des TableAdapter und führen die Abfrage aus  
  
1.  Deklarieren Sie eine Instanz des TableAdapter, die die auszuführende Abfrage enthält.  
  
    -   Zum Erstellen einer Instanz mithilfe von Entwurfszeittools ziehen Sie den gewünschten TableAdapter aus der **Toolbox**.  \(Komponenten im Projekt werden jetzt in der **Toolbox** unter einer Überschrift angezeigt, die mit dem Projektnamen übereinstimmt.\) Falls der TableAdapter in der **Toolbox** nicht angezeigt wird, müssen Sie das Projekt möglicherweise neu erstellen.  
  
         \- oder \-  
  
    -   Um eine Instanz im Code zu erstellen, ersetzen Sie den folgenden Code durch die Namen des <xref:System.Data.DataSet> und des TableAdapter.  
  
         `Dim tableAdapter As New DataSetTableAdapters.TableAdapter`  
  
        > [!NOTE]
        >  TableAdapters befinden sich nicht tatsächlich in den zugeordneten Datasetklassen.  Jedes Dataset besitzt eine entsprechende TableAdapter\-Auflistung im eigenen Namespace.  Ein Dataset mit der Bezeichnung `SalesDataSet` verfügt z. B. über einen `SalesDataSetTableAdapters`\-Namespace, der die entsprechenden TableAdapters enthält.  
  
2.  Rufen Sie die Abfrage genauso auf, wie Sie auch alle andere Methoden im Code aufrufen.  Die Abfrage ist eine Methode für den TableAdapter.  Ersetzen Sie den folgenden Code durch den Namen des TableAdapter und der Abfrage.  Darüber hinaus müssen Sie auch alle für die Abfrage erforderlichen Parameter übergeben.  Wenn Sie sich nicht sicher sind, ob die Abfrage Parameterangaben erfordert und welche Parameter erforderlich sind, finden Sie die erforderliche Abfragesignatur in IntelliSense.  In Abhängigkeit davon, ob für die Abfrage Parameter erforderlich sind, entspricht der Code einem der folgenden Beispiele:  
  
     `TableAdapter.Query()`  
  
     `TableAdapter.Query(Parameters)`  
  
     Abfragen, von denen angenommen wird, dass sie keinen Wert zurückgeben, geben doch einen Wert zurück – eine ganze Zahl, die die Anzahl der von der Abfrage betroffenen Zeilen enthält.  Der vollständige Code zum Deklarieren einer TableAdapter\-Instanz und zum Ausführen einer Abfrage müsste ungefähr wie folgt aussehen:  
  
     [!code-cs[VbRaddataFillingAndExecuting#11](../data-tools/codesnippet/CSharp/how-to-create-and-execute-an-sql-statement-that-returns-no-value_1.cs)]
     [!code-vb[VbRaddataFillingAndExecuting#11](../data-tools/codesnippet/VisualBasic/how-to-create-and-execute-an-sql-statement-that-returns-no-value_1.vb)]  
  
## Ausführen von SQL\-Anweisungen, die keinen Wert zurückgeben, mit einem Befehlsobjekt  
 Im folgenden Beispiel wird gezeigt, wie ein Befehl erstellt und eine SQL\-Anweisung ausgeführt wird, die keinen Wert zurückgibt.  Informationen zum Festlegen und Abrufen von Parameterwerten für einen Befehl finden Sie unter [Gewusst wie: Festlegen und Abrufen von Parametern für Befehlsobjekte](../Topic/How%20to:%20Set%20and%20Get%20Parameters%20for%20Command%20Objects.md).  
  
 In diesem Beispiel wird das <xref:System.Data.SqlClient.SqlCommand>\-Objekt verwendet, und Folgendes ist erforderlich:  
  
-   Verweise auf die Namespaces <xref:System>, <xref:System.Data> und <xref:System.Xml>.  
  
-   Eine Datenverbindung mit der Bezeichnung `SqlConnection1`.  
  
-   Eine Tabelle mit der Bezeichnung `Customers` in der Datenquelle, mit der `SqlConnection1` verbunden ist.  \(Andernfalls benötigen Sie eine gültige SQL\-Anweisung für die Datenquelle.\)  
  
#### So führen Sie mit einem DataCommand eine SQL\-Anweisung aus, die keinen Wert zurückgibt  
  
-   Fügen Sie den folgenden Code einer Methode hinzu, über die Sie die SQL\-Anweisung ausführen möchten.  Rufen Sie die `ExecuteNonQuery`\-Methode eines Befehls auf, wenn kein Wert zurückgegeben werden soll \(z. B. <xref:System.Data.SqlClient.SqlCommand.ExecuteNonQuery%2A?displayProperty=fullName>\).  
  
     [!code-cs[VbRaddataFillingAndExecuting#12](../data-tools/codesnippet/CSharp/how-to-create-and-execute-an-sql-statement-that-returns-no-value_2.cs)]
     [!code-vb[VbRaddataFillingAndExecuting#12](../data-tools/codesnippet/VisualBasic/how-to-create-and-execute-an-sql-statement-that-returns-no-value_2.vb)]  
  
## .NET Framework-Sicherheit  
 Die Anwendung muss über die Berechtigung zum Zugreifen auf die Datenbank und zum Ausführen der SQL\-Anweisung verfügen.  
  
## Siehe auch  
 <xref:System.Data.SqlClient.SqlCommand.ExecuteNonQuery%2A?displayProperty=fullName>   
 <xref:System.Data.OleDb.OleDbCommand.ExecuteNonQuery%2A?displayProperty=fullName>   
 <xref:System.Data.Odbc.OdbcCommand.ExecuteNonQuery%2A?displayProperty=fullName>   
 <xref:System.Data.OracleClient.OracleCommand.ExecuteNonQuery%2A?displayProperty=fullName>   
 [Gewusst wie: Erstellen von TableAdapter\-Abfragen](../data-tools/how-to-create-tableadapter-queries.md)   
 [Gewusst wie: Bearbeiten von TableAdapter\-Abfragen](../data-tools/how-to-edit-tableadapter-queries.md)   
 [Gewusst wie: Füllen eines Datasets mit Daten](../data-tools/how-to-fill-a-dataset-with-data.md)   
 [Auffüllen von Datasets mit Daten](../data-tools/fill-datasets-by-using-tableadapters.md)   
 [Gewusst wie: Festlegen und Abrufen von Parametern für Befehlsobjekte](../Topic/How%20to:%20Set%20and%20Get%20Parameters%20for%20Command%20Objects.md)