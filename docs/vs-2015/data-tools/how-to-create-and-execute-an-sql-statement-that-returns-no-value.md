---
title: 'Vorgehensweise: Erstellen und Ausführen eine SQL-Anweisung, die keinen Wert zurückgibt | Microsoft-Dokumentation'
ms.custom: ''
ms.date: 11/15/2016
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
- method calls, examples
- calling methods, examples
- SQL statements, executing
- SQL statements, creating
ms.assetid: 612d3046-0cfa-4d90-be6e-c4d6bcbd5aee
caps.latest.revision: 23
author: gewarren
ms.author: gewarren
manager: ghogen
robots: noindex,nofollow
ms.openlocfilehash: 1768db097d2555726b17862c9c4a4b82a3e2a6a8
ms.sourcegitcommit: 9ceaf69568d61023868ced59108ae4dd46f720ab
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 10/12/2018
ms.locfileid: "49188603"
---
# <a name="how-to-create-and-execute-an-sql-statement-that-returns-no-value"></a>Gewusst wie: Erstellen und Ausführen einer SQL-Anweisung, die keinen Wert zurückgibt
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Um eine SQL-Anweisung auszuführen, die keinen Wert zurückgibt, können Sie eine TableAdapter-Abfrage, die konfiguriert ist, führen Sie eine SQL-Anweisung ausführen (z. B. `CustomersTableAdapter.UpdateTableData(CustomersDataTable)`).  
  
 Wenn Ihre Anwendung keine TableAdapters verwendet werden, rufen Sie die `ExecuteNonQuery` Methode für ein Command-Objekt, das Festlegen der `CommandType` Eigenschaft <xref:System.Data.CommandType>. ("Command-Objekt" bezieht sich auf den spezifischen Befehl für die [.NET Framework-Datenanbieter](http://msdn.microsoft.com/library/03a9fc62-2d24-491a-9fe6-d6bdb6dcb131) Ihre Anwendung verwendet. Beispielsweise wenn Ihre Anwendung die .NET Framework-Datenanbieter für SQL Server verwendet wird, das Befehlsobjekt wäre <xref:System.Data.SqlClient.SqlCommand>.)  
  
 Die folgenden Beispiele zeigen, wie Sie zum Ausführen von SQL-Anweisungen, die aus einer Datenbank unter Verwendung von TableAdapters keinen Wert zurückgeben oder Befehlsobjekte. Weitere Informationen zu Abfragen mit TableAdapters und Befehlen finden Sie unter [Füllen von Datasets mit TableAdapters](../data-tools/fill-datasets-by-using-tableadapters.md).  
  
## <a name="executing-sql-statements-that-return-no-values-using-a-tableadapter"></a>Ausführen von SQL-Anweisungen, die keine Werte, die mit einem TableAdapter zurückgeben  
 In diesem Beispiel wird gezeigt, wie zum Erstellen einer TableAdapter-Abfrage mit der [Bearbeiten von TableAdapters](../data-tools/editing-tableadapters.md), und klicken Sie dann stellt Informationen zum Deklarieren einer Instanz des TableAdapter, und führen Sie die Abfrage.  
  
 [!INCLUDE[note_settings_general](../includes/note-settings-general-md.md)]  
  
#### <a name="to-create-an-sql-statement-that-returns-no-value-using-a-tableadapter"></a>Um eine SQL-Anweisung zu erstellen, die keinen Wert, der mit einem TableAdapter zurückgibt  
  
1.  Öffnen Sie ein Dataset in den **Dataset-Designer**. Weitere Informationen finden Sie unter [Vorgehensweise: Öffnen Sie ein Dataset im Dataset-Designer](http://msdn.microsoft.com/library/36fc266f-365b-42cb-aebb-c993dc2c47c3).  
  
2.  Wenn Sie nicht bereits eine verfügen, erstellen Sie einen TableAdapter. Weitere Informationen zum Erstellen von TableAdapters finden Sie unter [erstellen und Konfigurieren eines TableAdapters](../data-tools/create-and-configure-tableadapters.md).  
  
3.  Wenn Sie bereits eine Abfrage für den TableAdapter, die eine SQL-Anweisung verwendet, die keinen Wert zurückgibt verfügen, fahren Sie mit dem nächsten Verfahren "So deklarieren Sie eine Instanz des TableAdapter, und führen Sie die Abfrage." Andernfalls fahren Sie mit Schritt 4, um eine neue Abfrage zu erstellen, die keinen Wert zurückgibt.  
  
4.  Mit der rechten Maustaste des TableAdapter, die Sie möchten, und verwenden Sie im Kontextmenü den Befehl zum Hinzufügen einer Abfrage.  
  
     Die **Konfigurations-Assistenten für TableAdapter-Abfragen** wird geöffnet.  
  
5.  Übernehmen Sie den Standardwert des **SQL-Anweisungen**, und klicken Sie dann auf **Weiter**.  
  
6.  Wählen Sie die **UPDATE**, **einfügen** oder **löschen** aus, und klicken Sie dann auf **Weiter**.  
  
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
        >  TableAdapters tatsächlich in der verknüpften Dataset-Klassen befinden sich nicht. Jedes Dataset verfügt über eine entsprechende Sammlung von TableAdapter-Steuerelemente in einem eigenen Namespace. Angenommen, Sie haben ein Dataset namens `SalesDataSet`, gäbe es einen `SalesDataSetTableAdapters` Namespace, der die TableAdapters enthält.  
  
2.  Rufen Sie die Abfrage, wie Sie eine andere Methode im Code aufrufen. Ihre Abfrage ist eine Methode auf dem TableAdapter. Ersetzen Sie den folgenden Code, mit den Namen des TableAdapter und der Abfrage. Sie müssen auch alle von der Abfrage erforderlichen Parameter zu übergeben. Wenn Sie nicht sicher sind, wenn die Abfrage Parameter benötigt werden, oder welche Parameter erforderlich sind, überprüfen Sie, ob IntelliSense die erforderliche Signatur der Abfrage. Je nachdem, ob die Abfrage Parameter oder nicht verwendet würde der Code in den folgenden Beispielen ähnlich aussehen:  
  
     `TableAdapter.Query()`  
  
     `TableAdapter.Query(Parameters)`  
  
     Abfragen, die wir vorstellen keinen Wert zurückgeben können tatsächlich geben einen Wert zurück – eine Ganzzahl, die die Anzahl der von der Abfrage betroffenen Zeilen enthält. Der vollständige Code zum Deklarieren einer Instanz eines TableAdapter und Ausführen einer Abfrage sollte in etwa wie folgt aussehen:  
  
     [!code-csharp[VbRaddataFillingAndExecuting#11](../snippets/csharp/VS_Snippets_VBCSharp/VbRaddataFillingAndExecuting/CS/Form2.cs#11)]
     [!code-vb[VbRaddataFillingAndExecuting#11](../snippets/visualbasic/VS_Snippets_VBCSharp/VbRaddataFillingAndExecuting/VB/Form2.vb#11)]  
  
## <a name="executing-sql-statements-that-return-no-value-using-a-command-object"></a>Ausführen von SQL-Anweisungen, die unter Verwendung eines Befehlsobjekts keinen Wert zurückgeben  
 Das folgende Beispiel zeigt, wie Sie einen Befehl erstellen und Ausführen einer SQL­Anweisung, die keinen Wert zurückgibt. Informationen zum Festlegen und Abrufen von Parameterwerten für einen Befehl finden Sie unter [Vorgehensweise: festlegen und Abrufen von Parametern für Befehlsobjekte](http://msdn.microsoft.com/library/10110ecc-d2ed-4796-bb8f-74f2ecd40787).  
  
 Dieses Beispiel verwendet die <xref:System.Data.SqlClient.SqlCommand> Objekt und erfordert:  
  
-   Verweise auf die <xref:System>, <xref:System.Data>, und <xref:System.Xml> Namespaces.  
  
-   Eine Datenverbindung, die mit dem Namen `SqlConnection1`.  
  
-   Eine Tabelle namens `Customers` in der Datenquelle, `SqlConnection1` eine Verbindung mit her. (Andernfalls benötigen Sie eine gültige SQL­Anweisung für die Datenquelle).  
  
#### <a name="to-execute-an-sql-statement-that-returns-no-value-using-a-datacommand"></a>Eine SQL-Anweisung ausführen, die keinen Wert unter Verwendung eines DataCommand zurückgibt  
  
-   Fügen Sie den folgenden Code an eine Methode, der die SQL-Anweisung ausgeführt werden soll. Rufen Sie die `ExecuteNonQuery` Methode für einen Befehl auf keinen Wert zurückgeben (z. B. <xref:System.Data.SqlClient.SqlCommand.ExecuteNonQuery%2A?displayProperty=fullName>).  
  
     [!code-csharp[VbRaddataFillingAndExecuting#12](../snippets/csharp/VS_Snippets_VBCSharp/VbRaddataFillingAndExecuting/CS/Form2.cs#12)]
     [!code-vb[VbRaddataFillingAndExecuting#12](../snippets/visualbasic/VS_Snippets_VBCSharp/VbRaddataFillingAndExecuting/VB/Form2.vb#12)]  
  
## <a name="net-framework-security"></a>.NET Framework-Sicherheit  
 Die Anwendung erfordert die Berechtigung zum Zugriff auf die Datenbank und SQL-Anweisung ausführen.  
  
## <a name="see-also"></a>Siehe auch  
 <xref:System.Data.SqlClient.SqlCommand.ExecuteNonQuery%2A?displayProperty=fullName>   
 <xref:System.Data.OleDb.OleDbCommand.ExecuteNonQuery%2A?displayProperty=fullName>   
 <xref:System.Data.Odbc.OdbcCommand.ExecuteNonQuery%2A?displayProperty=fullName>   
 <xref:System.Data.OracleClient.OracleCommand.ExecuteNonQuery%2A?displayProperty=fullName>   
 [Vorgehensweise: Erstellen von TableAdapter-Abfragen](../data-tools/how-to-create-tableadapter-queries.md)   
 [Vorgehensweise: Bearbeiten von TableAdapter-Abfragen](../data-tools/how-to-edit-tableadapter-queries.md)   
 [Gewusst wie: Füllen eines Datasets mit Daten](../data-tools/how-to-fill-a-dataset-with-data.md)   
 [Füllen von Datasets mit TableAdapters](../data-tools/fill-datasets-by-using-tableadapters.md)   
 [Vorgehensweise: festlegen und Abrufen von Parametern für Befehlsobjekte](http://msdn.microsoft.com/library/10110ecc-d2ed-4796-bb8f-74f2ecd40787)