---
title: 'Vorgehensweise: Erstellen und Ausführen eine SQL-Anweisung, die einen einzelnen Wert zurückgibt. | Microsoft-Dokumentation'
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
- data reader
- scalar values
- stored procedures, returning single value
- SQL statements, data commands
- DataReader object
- data commands, returning scalar values
ms.assetid: eb366496-69e5-4462-8683-653054165c5c
caps.latest.revision: 24
author: gewarren
ms.author: gewarren
manager: ghogen
robots: noindex,nofollow
ms.openlocfilehash: 762cf33bb739e4cf99e7b45d59b91df9e1a869c7
ms.sourcegitcommit: 55f7ce2d5d2e458e35c45787f1935b237ee5c9f8
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 08/22/2018
ms.locfileid: "47513037"
---
# <a name="how-to-create-and-execute-an-sql-statement-that-returns-a-single-value"></a>Gewusst wie: Erstellen und Ausführen einer SQL-Anweisung, die einen einzelnen Wert zurückgibt
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Um eine SQL-Anweisung auszuführen, die einen einzelnen Wert zurückgibt, können Sie eine TableAdapter-Abfrage, die konfiguriert ist, führen Sie eine SQL-Anweisung ausführen (z. B. `CustomersTableAdapter.CustomerCount()`).  
  
 Wenn Ihre Anwendung keine TableAdapters verwendet werden, rufen Sie die `ExecuteScalar` Methode für ein Command-Objekt, das Festlegen der `CommandType` Eigenschaft <xref:System.Data.CommandType>. ("Command-Objekt" bezieht sich auf den spezifischen Befehl für die [.NET Framework-Datenanbieter](http://msdn.microsoft.com/library/03a9fc62-2d24-491a-9fe6-d6bdb6dcb131) Ihre Anwendung verwendet. Beispielsweise wenn Ihre Anwendung die .NET Framework-Datenanbieter für SQL Server verwendet wird, das Befehlsobjekt wäre <xref:System.Data.SqlClient.SqlCommand>.)  
  
 Die folgenden Beispiele zeigen, wie Sie die Ausführung von SQL-Anweisungen, die einzelne Werte aus einer Datenbank unter Verwendung von TableAdapters zurückgeben oder Befehlsobjekten. Weitere Informationen zu Abfragen mit TableAdapters und Befehlen finden Sie unter [Füllen von Datasets mit TableAdapters](../data-tools/fill-datasets-by-using-tableadapters.md).  
  
 [!INCLUDE[note_settings_general](../includes/note-settings-general-md.md)]  
  
## <a name="executing-sql-statements-that-return-single-values-using-a-tableadapter"></a>Ausführen von SQL-Anweisungen, die einzelne Werte, die mit einem TableAdapter zurückgeben  
 In diesem Beispiel wird gezeigt, wie zum Erstellen einer TableAdapter-Abfrage mit der [Bearbeiten von TableAdapters](../data-tools/editing-tableadapters.md), und klicken Sie dann stellt Informationen zum Deklarieren einer Instanz des TableAdapter, und führen Sie die Abfrage.  
  
#### <a name="to-create-an-sql-statement-returning-a-single-value-using-a-tableadapter"></a>Erstellen Sie eine SQL-Anweisung, die einen einzelnen Wert, der mit einem TableAdapter zurückgibt  
  
1.  Öffnen Sie ein Dataset in den **Dataset-Designer**. Weitere Informationen finden Sie unter [Vorgehensweise: Öffnen Sie ein Dataset im Dataset-Designer](http://msdn.microsoft.com/library/36fc266f-365b-42cb-aebb-c993dc2c47c3).  
  
2.  Wenn Sie nicht bereits eine verfügen, erstellen Sie einen TableAdapter. Weitere Informationen zum Erstellen von TableAdapters finden Sie unter [erstellen und Konfigurieren eines TableAdapters](../data-tools/create-and-configure-tableadapters.md).  
  
3.  Wenn Sie bereits eine Abfrage für den TableAdapter, die eine SQL-Anweisung verwendet wird verfügen, um einen einzelnen Wert zurückgeben, fahren Sie mit dem nächsten Verfahren "So deklarieren Sie eine Instanz des TableAdapter, und führen Sie die Abfrage." Andernfalls fahren Sie mit Schritt 4, um eine neue Abfrage zu erstellen, die einen einzelnen Wert zurückgibt.  
  
4.  Mit der rechten Maustaste des TableAdapter, die Sie möchten, und verwenden Sie im Kontextmenü den Befehl zum Hinzufügen einer Abfrage.  
  
     Die **Konfigurations-Assistenten für TableAdapter-Abfragen** wird geöffnet.  
  
5.  Übernehmen Sie den Standardwert des **SQL-Anweisungen**, und klicken Sie dann auf **Weiter**.  
  
6.  Wählen Sie die **auswählen, die einen einzelnen Wert zurückgibt** aus, und klicken Sie dann auf **Weiter**.  
  
7.  Geben Sie die SQL-Anweisung, oder Verwenden der **Abfragegenerator** Unterstützung bei der Erstellung, und klicken Sie dann auf **Weiter**.  
  
8.  Geben Sie einen Namen für die Abfrage an.  
  
9. Schließen Sie den Assistenten; die Abfrage wird dem TableAdapter hinzugefügt.  
  
10. Erstellen Sie das Projekt.  
  
#### <a name="to-declare-an-instance-of-the-tableadapter-and-execute-the-query"></a>Deklarieren Sie eine Instanz des TableAdapter, und führen Sie die Abfrage  
  
1.  Deklarieren Sie eine Instanz des TableAdapter, die die Abfrage enthält, die Sie ausführen möchten.  
  
    -   Um eine Instanz mithilfe von Entwurfszeit-Tools zu erstellen, ziehen Sie den TableAdapter, die von sollen die **Toolbox**. (Komponenten in Ihrem Projekt jetzt angezeigt werden, der **Toolbox** unter einer Überschrift, die Projektnamen Ihres entspricht.) Wenn der TableAdapter nicht, in angezeigt wird der **Toolbox**, müssen Sie eventuell das Projekt zu erstellen.  
  
         - oder -   
  
    -   Ersetzen Sie den folgenden Code zum Erstellen einer Instanz im Code, mit den Namen Ihrer <xref:System.Data.DataSet> und TableAdapter-Klasse.  
  
         `Dim tableAdapter As New DataSetTableAdapters.TableAdapter`  
  
        > [!NOTE]
        >  TableAdapters tatsächlich in der verknüpften Dataset-Klassen befinden sich nicht. Jedes Dataset verfügt über eine entsprechende Sammlung von TableAdapter-Steuerelemente in einem eigenen Namespace. Angenommen, Sie haben ein Dataset namens `SalesDataSet`, dann wäre eine `SalesDataSetTableAdapters` Namespace, der die TableAdapters enthält.  
  
2.  Rufen Sie die Abfrage, wie Sie eine andere Methode im Code aufrufen. Ihre Abfrage ist eine Methode auf dem TableAdapter. Ersetzen Sie den folgenden Code, mit den Namen des TableAdapter und der Abfrage. Sie müssen auch alle von der Abfrage erforderlichen Parameter zu übergeben und mache etwas mit der Rückgabewert (z. B. weisen sie einer Variablen). Wenn Sie nicht sicher sind, wenn die Abfrage Parameter benötigt werden, oder welche Parameter erforderlich sind, überprüfen Sie, ob IntelliSense die erforderliche Signatur der Abfrage. Je nachdem, ob die Abfrage Parameter oder nicht verwendet würde der Code in den folgenden Beispielen ähnlich aussehen:  
  
     `TableAdapter.Query()`  
  
     `TableAdapter.Query(Parameters)`  
  
3.  Sie müssen sich wahrscheinlich um den Wert einer Variablen von der Abfrage zurückgegebenen zuzuweisen. TableAdapter-Abfragen, die einen einzelnen Wert zurückgeben einen Datentyp, der basierend auf der Abfrage zurück (im Gegensatz zu den `ExecuteScalar` -Methode, die ein Objekt zurückgibt). Z. B. wenn die TableAdapter-Abfrage eine einzelne Spalte auswählt, deren Datentyp eine ganze Zahl ist, ist der Rückgabewert der Abfrage eine ganze Zahl. Wenn die Spalte null-Werte zulässt, wird der Rückgabewert ist eine auf NULL festlegbarer Typen (z. B. `Nullable(Of Integer)`). Weitere Informationen zu nullable-Typen, finden Sie unter <xref:System.Nullable>. Der vollständige Code zum Deklarieren einer Instanz eines TableAdapter und Ausführen einer Abfrage sollte etwa wie folgt aussehen (in diesem Beispiel geht davon aus, die Rückgabe eine ganze Zahl, passen Sie Ihren Code entsprechend der von der Abfrage zurückgegebenen Datentyp):  
  
     [!code-csharp[VbRaddataFillingAndExecuting#9](../snippets/csharp/VS_Snippets_VBCSharp/VbRaddataFillingAndExecuting/CS/Form2.cs#9)]
     [!code-vb[VbRaddataFillingAndExecuting#9](../snippets/visualbasic/VS_Snippets_VBCSharp/VbRaddataFillingAndExecuting/VB/Form2.vb#9)]  
  
## <a name="executing-sql-statements-that-return-single-values-using-a-command-object"></a>Ausführen von SQL-Anweisungen, die einzelne Werte, die mit einem Befehlsobjekt zurückgeben  
 Das folgende Beispiel zeigt, wie Sie einen Befehl erstellen und Ausführen einer SQL­Anweisung, die einen einzelnen Wert zurückgibt. Informationen zum Festlegen und Abrufen von Parameterwerten für einen Befehl finden Sie unter [Vorgehensweise: festlegen und Abrufen von Parametern für Befehlsobjekte](http://msdn.microsoft.com/library/10110ecc-d2ed-4796-bb8f-74f2ecd40787).  
  
 Dieses Beispiel verwendet die <xref:System.Data.SqlClient.SqlCommand> Objekt und erfordert:  
  
-   Verweise auf die <xref:System>, <xref:System.Data>, und <xref:System.Xml> Namespaces.  
  
-   Eine Datenverbindung, die mit dem Namen `SqlConnection1`.  
  
-   Eine Tabelle namens `Customers` in der Datenquelle, `SqlConnection1` eine Verbindung mit her. (Andernfalls benötigen Sie eine gültige SQL­Anweisung für die Datenquelle).  
  
#### <a name="to-execute-an-sql-statement-returning-a-single-value-using-a-datacommand"></a>Zum Ausführen einer SQL-Anweisung, die einen einzelnen Wert, der unter Verwendung eines DataCommand zurückgibt  
  
-   Fügen Sie den folgenden Code an eine Methode, der den Code aus ausgeführt werden soll. Sie einen einzelnen Wert zurückgeben, durch den Aufruf der `ExecuteScalar` Methode eines Befehls (z. B. <xref:System.Data.SqlClient.SqlCommand.ExecuteScalar%2A>). Die Daten werden zurückgegeben, eine <xref:System.Object>.  
  
     [!code-csharp[VbRaddataFillingAndExecuting#10](../snippets/csharp/VS_Snippets_VBCSharp/VbRaddataFillingAndExecuting/CS/Form2.cs#10)]
     [!code-vb[VbRaddataFillingAndExecuting#10](../snippets/visualbasic/VS_Snippets_VBCSharp/VbRaddataFillingAndExecuting/VB/Form2.vb#10)]  
  
## <a name="net-framework-security"></a>.NET Framework-Sicherheit  
 Die Anwendung erfordert die Berechtigung zum Zugriff auf die Datenbank und SQL-Anweisung ausführen.  
  
## <a name="see-also"></a>Siehe auch  
 <xref:System.Data.SqlClient.SqlCommand.ExecuteScalar%2A?displayProperty=fullName>   
 <xref:System.Data.OleDb.OleDbCommand.ExecuteScalar%2A?displayProperty=fullName>   
 <xref:System.Data.Odbc.OdbcCommand.ExecuteScalar%2A?displayProperty=fullName>   
 <xref:System.Data.OracleClient.OracleCommand.ExecuteScalar%2A?displayProperty=fullName>   
 [Vorgehensweise: Erstellen von TableAdapter-Abfragen](../data-tools/how-to-create-tableadapter-queries.md)   
 [Vorgehensweise: Bearbeiten von TableAdapter-Abfragen](../data-tools/how-to-edit-tableadapter-queries.md)   
 [Gewusst wie: Füllen eines Datasets mit Daten](../data-tools/how-to-fill-a-dataset-with-data.md)   
 [Füllen von Datasets mit TableAdapters](../data-tools/fill-datasets-by-using-tableadapters.md)   
 [Vorgehensweise: festlegen und Abrufen von Parametern für Befehlsobjekte](http://msdn.microsoft.com/library/10110ecc-d2ed-4796-bb8f-74f2ecd40787)