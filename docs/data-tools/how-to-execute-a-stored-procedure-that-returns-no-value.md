---
title: "Gewusst wie: Ausf&#252;hren einer gespeicherten Prozedur, die keinen Wert zur&#252;ckgibt | Microsoft Docs"
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
  - "ExecuteNonQuery-Methode"
  - "Gespeicherte Prozeduren, Erstellen"
  - "Gespeicherte Prozeduren, Ausführen"
ms.assetid: 8a929e96-2cf5-43a5-b5b7-c0a5a397bbc5
caps.latest.revision: 19
caps.handback.revision: 19
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
robots: noindex,nofollow
---
# Gewusst wie: Ausf&#252;hren einer gespeicherten Prozedur, die keinen Wert zur&#252;ckgibt
Zum Ausführen einer gespeicherten Prozedur, die keinen Wert zurückgibt, können Sie eine TableAdapter\-Abfrage ausführen, die für das Ausführen einer gespeicherten Prozedur konfiguriert ist \(z. B. `CustomersTableAdapter.UpdateTableData(CustomersDataTable)`\).  
  
 Wenn in Ihrer Anwendung keine TableAdapters verwendet werden, rufen Sie die `ExecuteNonQuery`\-Methode für ein Befehlsobjekt auf und legen seine `CommandType`\-Eigenschaft auf <xref:System.Data.CommandType> fest.  \(Der Begriff "Befehlsobjekt" bezieht sich auf den spezifischen Befehl für den [.NET Framework\-Datenanbieter](../Topic/.NET%20Framework%20Data%20Providers.md), den die Anwendung verwendet.  Wenn die Anwendung beispielsweise den .NET Framework\-Datenanbieter für SQL Server verwendet, ist das Befehlsobjekt <xref:System.Data.SqlClient.SqlCommand>.\)  
  
 Die folgenden Beispiele veranschaulichen die Ausführung von gespeicherten Prozeduren, die unter Verwendung von TableAdapters oder Befehlsobjekten keinen Wert aus einer Datenbank zurückgeben.  Weitere Informationen zu Abfragen mit TableAdapters und Befehlen finden Sie unter [Auffüllen von Datasets mit Daten](../data-tools/fill-datasets-by-using-tableadapters.md).  
  
 [!INCLUDE[note_settings_general](../data-tools/includes/note_settings_general_md.md)]  
  
## Ausführen von gespeicherten Prozeduren, die unter Verwendung eines TableAdapter keine Werte zurückgeben  
 Dieses Beispiel veranschaulicht das Erstellen einer TableAdapter\-Abfrage mit dem [TableAdapter\-Abfragekonfigurations\-Assistent](../data-tools/editing-tableadapters.md). Darüber hinaus enthält es Informationen zum Deklarieren einer Instanz des TableAdapter und zum Ausführen der Abfrage.  
  
#### So erstellen Sie eine gespeicherte Prozedur, die unter Verwendung eines TableAdapter keinen Wert zurückgibt  
  
1.  Öffnen Sie ein Dataset im **Dataset\-Designer**.  Weitere Informationen finden Sie unter [Gewusst wie: Öffnen eines Datasets im DataSet\-Designer](../Topic/How%20to:%20Open%20a%20Dataset%20in%20the%20Dataset%20Designer.md).  
  
2.  Erstellen Sie einen TableAdapter, falls noch keiner vorhanden ist.  Weitere Informationen zum Erstellen von TableAdapters finden Sie unter [Gewusst wie: Erstellen von TableAdapters](../data-tools/create-and-configure-tableadapters.md).  
  
3.  Wenn bereits eine Abfrage für den TableAdapter vorhanden ist, in der eine gespeicherte Prozedur verwendet wird, die keine Werte zurückgibt, wechseln Sie zum nächsten Vorgang "So deklarieren Sie eine Instanz des TableAdapter und führen die Abfrage aus". Fahren Sie andernfalls mit Schritt 4 fort, um eine neue Abfrage zu erstellen, die keinen Wert zurückgibt.  
  
4.  Klicken Sie mit der rechten Maustaste auf den gewünschten TableAdapter, und verwenden Sie das Kontextmenü, um eine Abfrage hinzuzufügen.  
  
     Der **Konfigurations\-Assistent für TableAdapter\-Abfragen** wird geöffnet.  
  
5.  Wählen Sie **Vorhandene gespeicherte Prozedur verwenden** aus, und klicken Sie auf **Weiter**.  
  
6.  Wählen Sie eine gespeicherte Prozedur aus der Dropdownliste aus, und klicken Sie dann auf **Weiter**.  
  
7.  Wählen Sie die Option **Kein Wert** aus, und klicken Sie auf **Weiter**.  
  
8.  Geben Sie einen Namen für die Abfrage an.  
  
9. Klicken Sie auf **Weiter** oder **Fertig stellen**, um den Assistenten fertig zu stellen. Die Abfrage wird dem TableAdapter hinzugefügt.  
  
10. Erstellen Sie das Projekt.  
  
#### So deklarieren Sie eine Instanz des TableAdapter und führen die Abfrage aus  
  
1.  Deklarieren Sie eine Instanz des TableAdapter, die die auszuführende Abfrage enthält.  
  
    -   Zum Erstellen einer Instanz mithilfe von Entwurfszeittools ziehen Sie den gewünschten TableAdapter aus der **Toolbox**.  \(Komponenten im Projekt werden jetzt in der **Toolbox** unter einer Überschrift angezeigt, die mit dem Projektnamen übereinstimmt.\) Falls der TableAdapter in der **Toolbox** nicht angezeigt wird, müssen Sie das Projekt möglicherweise neu erstellen.  
  
         \- oder \-  
  
    -   Um eine Instanz im Code zu erstellen, ersetzen Sie den folgenden Code durch die Namen des <xref:System.Data.DataSet> und des TableAdapter.  
  
         `Dim tableAdapter As New DataSetTableAdapters.TableAdapter`  
  
        > [!NOTE]
        >  TableAdapters befinden sich nicht tatsächlich in den zugeordneten Datasetklassen.  Jedes Dataset besitzt eine entsprechende TableAdapter\-Auflistung im eigenen Namespace.  Wenn beispielsweise das Dataset `SalesDataSet` vorliegt, dann ist ein `SalesDataSetTableAdapters`\-Namespace mit dem zugehörigen TableAdapter vorhanden.  
  
2.  Rufen Sie die Abfrage genauso auf, wie Sie auch alle andere Methoden im Code aufrufen.  Die Abfrage ist eine Methode für den TableAdapter.  Ersetzen Sie den folgenden Code durch den Namen des TableAdapter und der Abfrage.  Darüber hinaus müssen Sie auch alle für die Abfrage erforderlichen Parameter übergeben.  Wenn Sie sich nicht sicher sind, ob die Abfrage Parameterangaben erfordert und welche Parameter erforderlich sind, finden Sie die erforderliche Abfragesignatur in IntelliSense.  In Abhängigkeit davon, ob für die Abfrage Parameter erforderlich sind, entspricht der Code einem der folgenden Beispiele:  
  
     `TableAdapter.Query()`  
  
     `TableAdapter.Query(Parameters)`  
  
     Der vollständige Code zum Deklarieren einer Instanz des TableAdapter sowie zum Ausführen der Abfrage sollte folgendermaßen aussehen:  
  
     [!code-cs[VbRaddataFillingAndExecuting#11](../data-tools/codesnippet/CSharp/how-to-execute-a-stored-procedure-that-returns-no-value_1.cs)]
     [!code-vb[VbRaddataFillingAndExecuting#11](../data-tools/codesnippet/VisualBasic/how-to-execute-a-stored-procedure-that-returns-no-value_1.vb)]  
  
## Ausführen von gespeicherten Prozeduren, die unter Verwendung eines Befehlsobjekts keinen Wert zurückgeben  
 Das folgende Beispiel veranschaulicht das Erstellen eines Befehls und die Ausführung einer gespeicherten Prozedur, die keinen Wert zurückgibt.  Informationen zum Festlegen und Abrufen von Parameterwerten für einen Befehl finden Sie unter [Gewusst wie: Festlegen und Abrufen von Parametern für Befehlsobjekte](../Topic/How%20to:%20Set%20and%20Get%20Parameters%20for%20Command%20Objects.md).  
  
 In diesem Beispiel wird das <xref:System.Data.SqlClient.SqlCommand>\-Objekt verwendet, und Folgendes ist erforderlich:  
  
-   Verweise auf die Namespaces <xref:System>, <xref:System.Data> und <xref:System.Xml>.  
  
#### So führen Sie eine gespeicherte Prozedur aus, die unter Verwendung eines DataCommand keinen Wert zurückgibt  
  
-   Fügen Sie den folgenden Code zu einer Methode hinzu, aus der Sie die gespeicherte Prozedur ausführen möchten.  Rufen Sie die `ExecuteNonQuery`\-Methode eines Befehls auf, um keinen Wert zurückzugeben \(z. B.<xref:System.Data.SqlClient.SqlCommand.ExecuteNonQuery%2A>\).  
  
     [!code-cs[VbRaddataFillingAndExecuting#15](../data-tools/codesnippet/CSharp/how-to-execute-a-stored-procedure-that-returns-no-value_2.cs)]
     [!code-vb[VbRaddataFillingAndExecuting#15](../data-tools/codesnippet/VisualBasic/how-to-execute-a-stored-procedure-that-returns-no-value_2.vb)]  
  
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