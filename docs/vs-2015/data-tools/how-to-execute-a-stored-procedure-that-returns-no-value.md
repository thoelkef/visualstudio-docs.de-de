---
title: 'Vorgehensweise: Ausführen einer gespeicherten Prozedur, die keinen Wert zurückgibt | Microsoft-Dokumentation'
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
- ExecuteNonQuery method
- stored procedures, creating
- stored procedures, executing
ms.assetid: 8a929e96-2cf5-43a5-b5b7-c0a5a397bbc5
caps.latest.revision: 19
author: gewarren
ms.author: gewarren
manager: ghogen
robots: noindex,nofollow
ms.openlocfilehash: 0a9c80f37e5d569fd3a257f678256f01aba44925
ms.sourcegitcommit: 55f7ce2d5d2e458e35c45787f1935b237ee5c9f8
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 08/22/2018
ms.locfileid: "47523590"
---
# <a name="how-to-execute-a-stored-procedure-that-returns-no-value"></a>Gewusst wie: Ausführen einer gespeicherten Prozedur, die keinen Wert zurückgibt
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Um eine gespeicherte Prozedur auszuführen, die keinen Wert zurückgibt, können Sie eine TableAdapter-Abfrage, die konfiguriert ist, führen Sie eine gespeicherte Prozedur ausführen (z. B. `CustomersTableAdapter.UpdateTableData(CustomersDataTable)`).  
  
 Wenn Ihre Anwendung keine TableAdapters verwendet werden, rufen Sie die `ExecuteNonQuery` Methode für ein Command-Objekt, das Festlegen der `CommandType` Eigenschaft <xref:System.Data.CommandType>. ("Command-Objekt" bezieht sich auf den spezifischen Befehl für die [.NET Framework-Datenanbieter](http://msdn.microsoft.com/library/03a9fc62-2d24-491a-9fe6-d6bdb6dcb131) Ihre Anwendung verwendet. Beispielsweise wenn Ihre Anwendung die .NET Framework-Datenanbieter für SQL Server verwendet wird, klicken Sie dann das Befehlsobjekt wäre <xref:System.Data.SqlClient.SqlCommand>.)  
  
 Die folgenden Beispiele zeigen, wie Sie zum Ausführen von gespeicherter Prozeduren, die aus einer Datenbank unter Verwendung von TableAdapters keinen Wert zurückgeben oder Befehlsobjekte. Weitere Informationen zu Abfragen mit TableAdapters und Befehlen finden Sie unter [Füllen von Datasets mit TableAdapters](../data-tools/fill-datasets-by-using-tableadapters.md).  
  
 [!INCLUDE[note_settings_general](../includes/note-settings-general-md.md)]  
  
## <a name="executing-stored-procedures-that-return-no-values-using-a-tableadapter"></a>Ausführen von gespeicherten Prozeduren, die keine Werte, die mit einem TableAdapter zurückgeben  
 In diesem Beispiel wird gezeigt, wie zum Erstellen einer TableAdapter-Abfrage mit der [Bearbeiten von TableAdapters](../data-tools/editing-tableadapters.md), und klicken Sie dann stellt Informationen zum Deklarieren einer Instanz des TableAdapter, und führen Sie die Abfrage.  
  
#### <a name="to-create-a-stored-procedure-that-returns-no-value-using-a-tableadapter"></a>Um eine gespeicherte Prozedur zu erstellen, die keinen Wert, der mit einem TableAdapter zurückgibt  
  
1.  Öffnen Sie ein Dataset in den **Dataset-Designer**. Weitere Informationen finden Sie unter [Vorgehensweise: Öffnen Sie ein Dataset im Dataset-Designer](http://msdn.microsoft.com/library/36fc266f-365b-42cb-aebb-c993dc2c47c3).  
  
2.  Wenn Sie nicht bereits eine verfügen, erstellen Sie einen TableAdapter. Weitere Informationen zum Erstellen von TableAdapters finden Sie unter [erstellen und Konfigurieren eines TableAdapters](../data-tools/create-and-configure-tableadapters.md).  
  
3.  Wenn Sie bereits eine Abfrage für den TableAdapter, die eine gespeicherte Prozedur verwendet, die keinen Wert zurückgibt verfügen, fahren Sie mit dem nächsten Verfahren "So deklarieren Sie eine Instanz des TableAdapter, und führen Sie die Abfrage." Andernfalls fahren Sie mit Schritt 4, um eine neue Abfrage zu erstellen, die keinen Wert zurückgibt.  
  
4.  Mit der rechten Maustaste des TableAdapter, die Sie möchten, und verwenden Sie im Kontextmenü den Befehl zum Hinzufügen einer Abfrage.  
  
     Die **Konfigurations-Assistenten für TableAdapter-Abfragen** wird geöffnet.  
  
5.  Wählen Sie **vorhandene gespeicherte Prozedur verwenden**, und klicken Sie dann auf **Weiter**.  
  
6.  Wählen Sie eine gespeicherte Prozedur aus der Dropdown Liste, und klicken Sie dann auf **Weiter**.  
  
7.  Wählen Sie die Option zurückzugebenden **kein Wert**, und klicken Sie dann auf **Weiter**.  
  
8.  Geben Sie einen Namen für die Abfrage an.  
  
9. Klicken Sie auf **Weiter**, oder **Fertig stellen** zum Abschließen des Assistenten; die Abfrage wird dem TableAdapter hinzugefügt.  
  
10. Erstellen Sie das Projekt.  
  
#### <a name="to-declare-an-instance-of-the-tableadapter-and-execute-the-query"></a>Deklarieren Sie eine Instanz des TableAdapter, und führen Sie die Abfrage  
  
1.  Deklarieren Sie eine Instanz des TableAdapter, die die Abfrage enthält, die Sie ausführen möchten.  
  
    -   Um eine Instanz mithilfe von Entwurfszeit-Tools zu erstellen, ziehen Sie den TableAdapter, die von sollen die **Toolbox**. (Komponenten in Ihrem Projekt jetzt angezeigt werden, der **Toolbox** unter einer Überschrift, die Projektnamen Ihres entspricht.) Wenn der TableAdapter nicht, in angezeigt wird der **Toolbox**, müssen Sie eventuell das Projekt zu erstellen.  
  
         - oder -   
  
    -   Ersetzen Sie den folgenden Code zum Erstellen einer Instanz im Code, mit den Namen Ihrer <xref:System.Data.DataSet> und TableAdapter-Klasse.  
  
         `Dim tableAdapter As New DataSetTableAdapters.TableAdapter`  
  
        > [!NOTE]
        >  TableAdapters tatsächlich in der verknüpften Dataset-Klassen befinden sich nicht. Jedes Dataset verfügt über eine entsprechende Sammlung von TableAdapter-Steuerelemente in einem eigenen Namespace. Angenommen, Sie haben ein Dataset namens `SalesDataSet`, dann wäre eine `SalesDataSetTableAdapters` Namespace, der die TableAdapters enthält.  
  
2.  Rufen Sie die Abfrage, wie Sie eine andere Methode im Code aufrufen. Ihre Abfrage ist eine Methode auf dem TableAdapter. Ersetzen Sie den folgenden Code, mit den Namen des TableAdapter und der Abfrage. Sie müssen auch alle von der Abfrage erforderlichen Parameter zu übergeben. Wenn Sie nicht sicher sind, wenn die Abfrage Parameter benötigt werden, oder welche Parameter erforderlich sind, überprüfen Sie, ob IntelliSense die erforderliche Signatur der Abfrage. Je nachdem, ob die Abfrage Parameter oder nicht verwendet würde der Code in den folgenden Beispielen ähnlich aussehen:  
  
     `TableAdapter.Query()`  
  
     `TableAdapter.Query(Parameters)`  
  
     Der vollständige Code zum Deklarieren einer Instanz des TableAdapter, und führen Sie die Abfrage sollte in etwa wie folgt aussehen:  
  
     [!code-csharp[VbRaddataFillingAndExecuting#11](../snippets/csharp/VS_Snippets_VBCSharp/VbRaddataFillingAndExecuting/CS/Form2.cs#11)]
     [!code-vb[VbRaddataFillingAndExecuting#11](../snippets/visualbasic/VS_Snippets_VBCSharp/VbRaddataFillingAndExecuting/VB/Form2.vb#11)]  
  
## <a name="executing-stored-procedures-that-return-no-value-using-a-command-object"></a>Ausführen von gespeicherten Prozeduren, die unter Verwendung eines Befehlsobjekts keinen Wert zurückgeben  
 Das folgende Beispiel zeigt, wie Sie einen Befehl erstellen und Ausführen einer gespeicherten Prozedur, die keinen Wert zurückgibt. Informationen zum Festlegen und Abrufen von Parameterwerten für einen Befehl finden Sie unter [Vorgehensweise: festlegen und Abrufen von Parametern für Befehlsobjekte](http://msdn.microsoft.com/library/10110ecc-d2ed-4796-bb8f-74f2ecd40787).  
  
 Dieses Beispiel verwendet die <xref:System.Data.SqlClient.SqlCommand> Objekt und erfordert:  
  
-   Verweise auf die <xref:System>, <xref:System.Data>, und <xref:System.Xml> Namespaces.  
  
#### <a name="to-execute-a-stored-procedure-that-returns-no-value-using-a-datacommand"></a>Zum Ausführen einer gespeicherten Prozedur, die unter Verwendung ein DataCommand keinen Wert zurückgibt.  
  
-   Fügen Sie den folgenden Code an eine Methode, der die gespeicherte Prozedur ausgeführt werden soll. Rufen Sie die `ExecuteNonQuery` Methode für einen Befehl auf keinen Wert zurückgeben (z. B. <xref:System.Data.SqlClient.SqlCommand.ExecuteNonQuery%2A>).  
  
     [!code-csharp[VbRaddataFillingAndExecuting#15](../snippets/csharp/VS_Snippets_VBCSharp/VbRaddataFillingAndExecuting/CS/Form2.cs#15)]
     [!code-vb[VbRaddataFillingAndExecuting#15](../snippets/visualbasic/VS_Snippets_VBCSharp/VbRaddataFillingAndExecuting/VB/Form2.vb#15)]  
  
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