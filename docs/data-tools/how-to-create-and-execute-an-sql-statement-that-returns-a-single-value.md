---
title: "Gewusst wie: Erstellen und Ausf&#252;hren einer SQL-Anweisung, die einen einzelnen Wert zur&#252;ckgibt | Microsoft Docs"
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
  - "Datenbefehle, Zurückgeben von Skalarwerten"
  - "Datenleseprogramm"
  - "DataReader-Objekt"
  - "Skalarwerte"
  - "SQL-Anweisungen, Datenbefehle"
  - "Gespeicherte Prozeduren, Zurückgeben eines einzelnen Wertes"
ms.assetid: eb366496-69e5-4462-8683-653054165c5c
caps.latest.revision: 24
caps.handback.revision: 24
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
robots: noindex,nofollow
---
# Gewusst wie: Erstellen und Ausf&#252;hren einer SQL-Anweisung, die einen einzelnen Wert zur&#252;ckgibt
Zum Ausführen einer SQL\-Anweisung, die einen einzelnen Wert zurückgibt, können Sie eine TableAdapter\-Abfrage ausführen, die so konfiguriert ist, dass sie eine SQL\-Anweisung ausführt \(z. B. `CustomersTableAdapter.CustomerCount()`\).  
  
 Wenn in Ihrer Anwendung keine TableAdapters verwendet werden, rufen Sie die `ExecuteScalar`\-Methode für ein Befehlsobjekt auf und legen seine `CommandType`\-Eigenschaft auf <xref:System.Data.CommandType> fest.  \(Der Begriff "Befehlsobjekt" bezieht sich auf den spezifischen Befehl für den [.NET Framework\-Datenanbieter](../Topic/.NET%20Framework%20Data%20Providers.md), den die Anwendung verwendet.  Wenn in Ihrer Anwendung z. B. der .NET Framework\-Datenanbieter für SQL Server verwendet wird, lautet das Befehlsobjekt <xref:System.Data.SqlClient.SqlCommand>.\)  
  
 Die folgenden Beispiele veranschaulichen die Ausführung von SQL\-Anweisungen, die unter Verwendung von TableAdapters oder Befehlsobjekten einzelne Werte aus einer Datenbank zurückgeben.  Weitere Informationen zu Abfragen mit TableAdapters und Befehlen finden Sie unter [Auffüllen von Datasets mit Daten](../data-tools/fill-datasets-by-using-tableadapters.md).  
  
 [!INCLUDE[note_settings_general](../data-tools/includes/note_settings_general_md.md)]  
  
## Ausführen von SQL\-Anweisungen, die unter Verwendung eines TableAdapter einzelne Werte zurückgeben  
 Dieses Beispiel veranschaulicht das Erstellen einer TableAdapter\-Abfrage mit dem [TableAdapter\-Abfragekonfigurations\-Assistent](../data-tools/editing-tableadapters.md). Darüber hinaus enthält es Informationen zum Deklarieren einer Instanz des TableAdapter und zum Ausführen der Abfrage.  
  
#### So erstellen Sie eine SQL\-Anweisung, die unter Verwendung eines TableAdapter einen einzelnen Wert zurückgibt  
  
1.  Öffnen Sie ein Dataset im **Dataset\-Designer**.  Weitere Informationen finden Sie unter [Gewusst wie: Öffnen eines Datasets im DataSet\-Designer](../Topic/How%20to:%20Open%20a%20Dataset%20in%20the%20Dataset%20Designer.md).  
  
2.  Erstellen Sie einen TableAdapter, falls noch keiner vorhanden ist.  Weitere Informationen zum Erstellen von TableAdapters finden Sie unter [Gewusst wie: Erstellen von TableAdapters](../data-tools/create-and-configure-tableadapters.md).  
  
3.  Wenn bereits eine Abfrage für den TableAdapter vorhanden ist, in der eine SQL\-Anweisung zur Rückgabe einzelner Werte verwendet wird, fahren Sie mit der nächsten Prozedur "So deklarieren Sie eine Instanz des TableAdapter und führen die Abfrage aus" fort. Fahren Sie andernfalls mit Schritt 4 fort, und erstellen Sie eine neue Abfrage, die einen einzelnen Wert zurückgibt.  
  
4.  Klicken Sie mit der rechten Maustaste auf den gewünschten TableAdapter, und verwenden Sie das Kontextmenü, um eine Abfrage hinzuzufügen.  
  
     Der **Konfigurations\-Assistent für TableAdapter\-Abfragen** wird geöffnet.  
  
5.  Behalten Sie den Standardwert von **SQL\-Anweisungen verwenden** bei, und klicken Sie auf **Weiter**.  
  
6.  Wählen Sie die Option **SELECT\-Anweisung, die einen einzelnen Wert zurückgibt** aus, und klicken Sie dann auf **Weiter**.  
  
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
        >  TableAdapters befinden sich nicht tatsächlich in den zugeordneten Datasetklassen.  Jedes Dataset besitzt eine entsprechende TableAdapter\-Auflistung im eigenen Namespace.  Wenn beispielsweise das Dataset `SalesDataSet` vorliegt, dann ist ein `SalesDataSetTableAdapters`\-Namespace mit dem zugehörigen TableAdapter vorhanden.  
  
2.  Rufen Sie die Abfrage genauso auf, wie Sie auch alle andere Methoden im Code aufrufen.  Die Abfrage ist eine Methode für den TableAdapter.  Ersetzen Sie den folgenden Code durch den Namen des TableAdapter und der Abfrage.  Sie müssen auch alle für die Abfrage erforderlichen Parameter übergeben. Führen Sie darüber hinaus auch eine Aktion für den Rückgabewert aus \(weisen Sie ihn z. B. einer Variablen zu\).  Wenn Sie sich nicht sicher sind, ob die Abfrage Parameterangaben erfordert und welche Parameter erforderlich sind, finden Sie die erforderliche Abfragesignatur in IntelliSense.  In Abhängigkeit davon, ob für die Abfrage Parameter erforderlich sind, entspricht der Code einem der folgenden Beispiele:  
  
     `TableAdapter.Query()`  
  
     `TableAdapter.Query(Parameters)`  
  
3.  Sie müssen den von der Abfrage zurückgegebenen Wert wahrscheinlich einer Variablen zuweisen.  TableAdapter\-Abfragen, die einen einzelnen Wert zurückgeben, geben einen auf der Abfrage basierenden Datentyp zurück \(im Gegensatz zur `ExecuteScalar`\-Methode, die ein Objekt zurückgibt\).  Wenn beispielsweise bei der TableAdapter\-Abfrage eine einzelne Spalte ausgewählt wird, deren Datentyp eine ganze Zahl ist, ist auch der Rückgabewert der Abfrage eine ganze Zahl.  Wenn in der Spalte NULL\-Werte zulässig sind, entspricht auch der Rückgabewert einem Typ, der auf NULL festgelegt werden kann \(z. B. `Nullable(Of Integer)`\).  Weitere Informationen zu Typen, die auf Null festgelegt werden können, finden Sie unter <xref:System.Nullable>.  Der vollständige Code zum Deklarieren einer Instanz des TableAdapter sowie zum Ausführen der Abfrage sollte folgendermaßen aussehen \(in diesem Beispiel wird davon ausgegangen, dass der Rückgabewert eine ganze Zahl ist. Passen Sie den Code entsprechend dem von der Abfrage zurückgegebenen Datentyp an\):  
  
     [!code-cs[VbRaddataFillingAndExecuting#9](../data-tools/codesnippet/CSharp/how-to-create-and-execute-an-sql-statement-that-returns-a-single-value_1.cs)]
     [!code-vb[VbRaddataFillingAndExecuting#9](../data-tools/codesnippet/VisualBasic/how-to-create-and-execute-an-sql-statement-that-returns-a-single-value_1.vb)]  
  
## Ausführen von SQL\-Anweisungen, die unter Verwendung eines Befehlsobjekts einzelne Werte zurückgeben  
 Im folgenden Beispiel wird veranschaulicht, wie Sie einen Befehl erstellen und eine SQL\-Anweisung ausführen, die einen einzelnen Wert zurückgibt.  Informationen zum Festlegen und Abrufen von Parameterwerten für einen Befehl finden Sie unter [Gewusst wie: Festlegen und Abrufen von Parametern für Befehlsobjekte](../Topic/How%20to:%20Set%20and%20Get%20Parameters%20for%20Command%20Objects.md).  
  
 In diesem Beispiel wird das <xref:System.Data.SqlClient.SqlCommand>\-Objekt verwendet, und Folgendes ist erforderlich:  
  
-   Verweise auf die Namespaces <xref:System>, <xref:System.Data> und <xref:System.Xml>.  
  
-   Eine Datenverbindung mit der Bezeichnung `SqlConnection1`.  
  
-   Eine Tabelle mit der Bezeichnung `Customers` in der Datenquelle, mit der `SqlConnection1` verbunden ist.  \(Andernfalls benötigen Sie eine gültige SQL\-Anweisung für die Datenquelle.\)  
  
#### So führen Sie eine SQL\-Anweisung aus, die unter Verwendung eines DataCommand einen einzelnen Wert zurückgibt  
  
-   Fügen Sie den folgenden Code zu einer Methode hinzu, aus der Sie den Code ausführen möchten.  Sie geben einen einzelnen Wert zurück, indem Sie die `ExecuteScalar`\-Methode eines Befehls aufrufen \(z. B. <xref:System.Data.SqlClient.SqlCommand.ExecuteScalar%2A>\).  Die Daten werden in einem <xref:System.Object> zurückgegeben.  
  
     [!code-cs[VbRaddataFillingAndExecuting#10](../data-tools/codesnippet/CSharp/how-to-create-and-execute-an-sql-statement-that-returns-a-single-value_2.cs)]
     [!code-vb[VbRaddataFillingAndExecuting#10](../data-tools/codesnippet/VisualBasic/how-to-create-and-execute-an-sql-statement-that-returns-a-single-value_2.vb)]  
  
## .NET Framework-Sicherheit  
 Die Anwendung muss über die Berechtigung zum Zugreifen auf die Datenbank und zum Ausführen der SQL\-Anweisung verfügen.  
  
## Siehe auch  
 <xref:System.Data.SqlClient.SqlCommand.ExecuteScalar%2A?displayProperty=fullName>   
 <xref:System.Data.OleDb.OleDbCommand.ExecuteScalar%2A?displayProperty=fullName>   
 <xref:System.Data.Odbc.OdbcCommand.ExecuteScalar%2A?displayProperty=fullName>   
 <xref:System.Data.OracleClient.OracleCommand.ExecuteScalar%2A?displayProperty=fullName>   
 [Gewusst wie: Erstellen von TableAdapter\-Abfragen](../data-tools/how-to-create-tableadapter-queries.md)   
 [Gewusst wie: Bearbeiten von TableAdapter\-Abfragen](../data-tools/how-to-edit-tableadapter-queries.md)   
 [Gewusst wie: Füllen eines Datasets mit Daten](../data-tools/how-to-fill-a-dataset-with-data.md)   
 [Auffüllen von Datasets mit Daten](../data-tools/fill-datasets-by-using-tableadapters.md)   
 [Gewusst wie: Festlegen und Abrufen von Parametern für Befehlsobjekte](../Topic/How%20to:%20Set%20and%20Get%20Parameters%20for%20Command%20Objects.md)