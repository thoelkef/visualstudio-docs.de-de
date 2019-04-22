---
title: Überprüfen von Daten in Datasets | Microsoft-Dokumentation
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-data-tools
ms.topic: conceptual
f1_keywords:
- DataTable.ColumnChanging
- System.Data.DataTable.ColumnChanging
- System.Data.DataTable.RowChanging
- DataTable.RowChanging
dev_langs:
- VB
- CSharp
- C++
- aspx
helpviewer_keywords:
- data validation, datasets
- data validation
- validating data, datasets
- updating datasets, validating data
ms.assetid: 79500596-1e4d-478e-a991-a636fd73a622
caps.latest.revision: 27
author: gewarren
ms.author: gewarren
manager: jillfra
ms.openlocfilehash: 73eb1162411800a951566c9eb14928875966cfb7
ms.sourcegitcommit: 53aa5a413717a1b62ca56a5983b6a50f7f0663b3
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 04/17/2019
ms.locfileid: "59661320"
---
# <a name="validate-data-in-datasets"></a>Überprüfen von Daten in Datasets
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Überprüfen von Daten ist der Prozess der Bestätigung der Werte, die in Datenobjekte eingegeben werden, die die Einschränkungen in einer Dataset Schema entsprechen. Der Überprüfungsprozess wird bestätigt, dass diese Werte die Regeln eingehalten werden, die für Ihre Anwendung eingerichtet wurden. Es hat sich bewährt, überprüfen Sie die Daten vor dem Senden von Aktualisierungen an der zugrunde liegenden Datenbank. Dies verringert sowohl Fehler als auch die potenzielle Anzahl von Roundtrips zwischen einer Anwendung und der Datenbank.  
  
 Sie können bestätigen, dass Daten, die auf ein Dataset geschrieben werden durch Erstellen von Überprüfungen in das Dataset selbst gültig ist. Das Dataset kann überprüfen Sie die Daten unabhängig davon, wie das Update ausgeführt wird – direkt über die Steuerelemente in einem Formular in eine Komponente, oder auf andere Weise. Da das Dataset Teil Ihrer Anwendung (im Gegensatz zu den Datenbank-Back-End) ist, ist es ein logischer Ansatzpunkt zum anwendungsspezifischen Validierung zu erstellen.  
  
 Der beste Ort zum Hinzufügen der Validierung zu Ihrer Anwendung ist in der Datei für die partielle Klasse des Datasets. In [!INCLUDE[vbprvb](../includes/vbprvb-md.md)] oder [!INCLUDE[csprcs](../includes/csprcs-md.md)]öffnen die **Dataset-Designer** und doppelklicken Sie auf die Spalte oder Tabelle, für die Sie die Überprüfung erstellen möchten. Erstellt diese Aktion automatisch eine <xref:System.Data.DataTable.ColumnChanging> oder <xref:System.Data.DataTable.RowChanging> -Ereignishandler. Weitere Informationen finden Sie unter [Vorgehensweise: Validieren von Daten während Spaltenänderungen](http://msdn.microsoft.com/library/a2680600-67b6-4a40-a77e-b5bc638281c5) oder [Vorgehensweise: Validieren von Daten während Zeilenänderungen](http://msdn.microsoft.com/library/afc03c77-dfed-4302-9376-929400468ecc). Ein vollständiges Beispiel finden Sie unter [Exemplarische Vorgehensweise: Hinzufügen einer Validierung zu einem Dataset](http://msdn.microsoft.com/library/09351fab-d670-45e3-b53a-a944eff717e7).  
  
## <a name="validate-data"></a>Überprüfen von Daten  
 Validierung in einem Dataset kann auf folgende Weise erreicht werden:  
  
- Erstellen Sie eigene anwendungsspezifische Validierungen, die während der Änderung der Werte in eine einzelne Spalte überprüfen kann.  Weitere Informationen finden Sie unter [Vorgehensweise: Validieren von Daten während Spaltenänderungen](http://msdn.microsoft.com/library/a2680600-67b6-4a40-a77e-b5bc638281c5).  
  
- Erstellen Sie eigene anwendungsspezifische Validierungen, die die Daten mit Werten, die während einer gesamten Daten prüfen kann ändert Zeile. Weitere Informationen finden Sie unter [Vorgehensweise: Validieren von Daten während Zeilenänderungen](http://msdn.microsoft.com/library/afc03c77-dfed-4302-9376-929400468ecc).  
  
- Durch das Erstellen von Schlüsseln, unique-Einschränkungen, und so weiter, als Teil der Schemadefinition des tatsächlichen des Datasets. Weitere Informationen zum Einbinden von Validierung in der Schemadefinition finden Sie unter [eine DataColumn darauf beschränken, eindeutige Werte enthalten](http://msdn.microsoft.com/library/8ca21f77-b99a-47a7-a656-7cfd7a1bd9df).  
  
- Durch Festlegen der Eigenschaften von den <xref:System.Data.DataColumn> des Objekts, z. B. <xref:System.Data.DataColumn.MaxLength%2A>, <xref:System.Data.DataColumn.AllowDBNull%2A>, und <xref:System.Data.DataColumn.Unique%2A>.  
  
  Mehrere Ereignisse ausgelöst werden, indem die <xref:System.Data.DataTable> Objekt, wenn eine Änderung in einem Datensatz auftritt:  
  
- Die <xref:System.Data.DataTable.ColumnChanging> und <xref:System.Data.DataTable.ColumnChanged> Ereignisse werden ausgelöst, während und nach jeder Änderung an einer einzelnen Spalte. Die <xref:System.Data.DataTable.ColumnChanging> Ereignis ist hilfreich, wenn Sie Änderungen in bestimmte Spalten überprüfen möchten. Informationen über die vorgeschlagene Änderung wird als ein Argument mit dem Ereignis übergeben. Weitere Informationen finden Sie unter [Vorgehensweise: Validieren von Daten während Spaltenänderungen](http://msdn.microsoft.com/library/a2680600-67b6-4a40-a77e-b5bc638281c5).  
  
- Die <xref:System.Data.DataTable.RowChanging> und <xref:System.Data.DataTable.RowChanged> Ereignisse werden ausgelöst, während und nach einer Änderung in einer Zeile. Die <xref:System.Data.DataTable.RowChanging> Ereignis ist allgemeiner. Er gibt an, dass eine Änderung an einer beliebigen Stelle in der Zeile auftritt, aber Sie wissen nicht, welche Spalte geändert hat. Weitere Informationen finden Sie unter [Vorgehensweise: Validieren von Daten während Zeilenänderungen](http://msdn.microsoft.com/library/afc03c77-dfed-4302-9376-929400468ecc).  
  
  Standardmäßig löst jede Änderung an einer Spalte aus diesem Grund vier Ereignisse. Die erste ist die <xref:System.Data.DataTable.ColumnChanging> und <xref:System.Data.DataTable.ColumnChanged> Ereignisse für die spezifische Spalte, die geändert wird. Als Nächstes werden die <xref:System.Data.DataTable.RowChanging> und <xref:System.Data.DataTable.RowChanged> Ereignisse. Falls mehrere Änderungen an der Zeile durchgeführt werden, werden die Ereignisse für jede Änderung ausgelöst werden.  
  
> [!NOTE]
>  Der Datenzeile <xref:System.Data.DataRow.BeginEdit%2A> Methode deaktiviert die <xref:System.Data.DataTable.RowChanging> und <xref:System.Data.DataTable.RowChanged> Ereignisse nach jeder Änderung der einzelnen Spalten. Das Ereignis wird in diesem Fall nicht ausgelöst, bis die <xref:System.Data.DataRow.EndEdit%2A> Methode wurde aufgerufen, wenn die <xref:System.Data.DataTable.RowChanging> und <xref:System.Data.DataTable.RowChanged> Ereignisse werden nur einmal ausgelöst. Weitere Informationen finden Sie unter [Deaktivieren von Einschränkungen beim Auffüllen von Datasets](../data-tools/turn-off-constraints-while-filling-a-dataset.md).  
  
 Das Ereignis, das Sie auswählen, hängt davon ab, wie präzise die Validierung werden sollen. Wenn es wichtig ist, dass Sie Fehler abfangen, sofort bei einer Spalte ändert, Buildüberprüfung mithilfe der <xref:System.Data.DataTable.ColumnChanging> Ereignis. Verwenden Sie andernfalls die <xref:System.Data.DataTable.RowChanging> -Ereignis, das dazu führen, dass gleichzeitig mehrere Fehler abgefangen. Darüber hinaus, wenn Ihre Daten so strukturiert ist, dass der Wert einer Spalte basierend auf dem Inhalt einer anderen Spalte überprüft wird, dann führen Sie die Überprüfung während der <xref:System.Data.DataTable.RowChanging> Ereignis.  
  
 Wenn Datensätze aktualisiert werden, die <xref:System.Data.DataTable> Objekt löst Ereignisse aus, die Sie reagieren können, wenn Änderungen auftreten, und nachdem Änderungen vorgenommen wurden.  
  
 Wenn Ihre Anwendung ein typisiertes Dataset verwendet, können Sie stark typisierte Ereignishandler erstellen. Hiermit werden vier zusätzliche typisierte Ereignisse, die Sie Handler für erstellen können: `dataTableNameRowChanging`, `dataTableNameRowChanged`, `dataTableNameRowDeleting`, und `dataTableNameRowDeleted`. Diese typisiertes Ereignis-Handler übergeben Sie ein Argument, das die Spaltennamen der Tabelle enthält, die zum Schreiben und Lesen von Code vereinfachen.  
  
## <a name="data-update-events"></a>Ereignisse zum Aktualisieren von Daten  
  
|event|Beschreibung|  
|-----------|-----------------|  
|<xref:System.Data.DataTable.ColumnChanging>|Der Wert in einer Spalte wird geändert. Das Ereignis übergibt der Zeile und Spalte an, die Sie zusammen mit den vorgeschlagenen neuen Wert.|  
|<xref:System.Data.DataTable.ColumnChanged>|Der Wert in einer Spalte wurde geändert. Das Ereignis übergibt der Zeile und Spalte an, die Sie zusammen mit den vorgeschlagenen Wert.|  
|<xref:System.Data.DataTable.RowChanging>|Die Änderungen, die an eine <xref:System.Data.DataRow> Objekt sind im Begriff, der wieder in das Dataset ein Commit ausgeführt werden. Wenn Sie nicht aufgerufen haben die <xref:System.Data.DataRow.BeginEdit%2A> -Methode, die <xref:System.Data.DataTable.RowChanging> Ereignis wird ausgelöst, für jede Änderung an eine Spalte unmittelbar nach der <xref:System.Data.DataTable.ColumnChanging> -Ereignis ausgelöst wurde. Wenn Sie aufgerufen <xref:System.Data.DataRow.BeginEdit%2A> vor dem vornehmen von Änderungen, die <xref:System.Data.DataTable.RowChanging> -Ereignis wird ausgelöst, nur bei Aufruf der <xref:System.Data.DataRow.EndEdit%2A> Methode.<br /><br /> Das Ereignis übergibt die Zeile, zusammen mit einem Wert, der angibt, welche Art von Aktion (ändern, einfügen und So weiter) ausgeführt wird.|  
|<xref:System.Data.DataTable.RowChanged>|Eine Zeile wurde geändert. Das Ereignis übergibt die Zeile, zusammen mit einem Wert, der angibt, welche Art von Aktion (ändern, einfügen und So weiter) ausgeführt wird.|  
|<xref:System.Data.DataTable.RowDeleting>|Eine Zeile wird gelöscht. Das Ereignis übergibt die Zeile, zusammen mit einem Wert, der angibt, welche Art von Aktion (Delete) ausgeführt wird.|  
|<xref:System.Data.DataTable.RowDeleted>|Eine Zeile wurde gelöscht. Das Ereignis übergibt die Zeile, zusammen mit einem Wert, der angibt, welche Art von Aktion (Delete) ausgeführt wird.|  
  
 Die <xref:System.Data.DataTable.ColumnChanging>, <xref:System.Data.DataTable.RowChanging>, und <xref:System.Data.DataTable.RowDeleting> Ereignisse werden ausgelöst, während des Updates. Sie können diese Ereignisse verwenden, Überprüfen von Daten oder andere Arten von Verarbeitung ausführen. Da das Update im Prozess während dieser Ereignisse ist, können Sie es abbrechen, indem Sie keinen Ausnahmefehler auslöst, die verhindert, das Update dass abgeschlossen.  
  
 Die <xref:System.Data.DataTable.ColumnChanged>, <xref:System.Data.DataTable.RowChanged> und <xref:System.Data.DataTable.RowDeleted> Ereignisse sind Benachrichtigungsereignisse, die ausgelöst werden, wenn das Update erfolgreich abgeschlossen wurde. Diese Ereignisse sind nützlich, wenn Sie weitere Aktionen basierend auf einer erfolgreichen Aktualisierung ausführen möchten.  
  
## <a name="validate-data-during-column-changes"></a>Validieren von Daten während Spaltenänderungen  
  
> [!NOTE]
>  Die **Dataset-Designer** erstellt eine partielle Klasse, die in die Überprüfung Logik zu einem Dataset hinzugefügt werden kann. Die vom Designer generierte Dataset nicht löschen oder ändern Sie Code in der partiellen Klasse.  
  
 Sie können Daten validieren, wenn der Wert in einer Datenspalte geändert wird, indem er auf die <xref:System.Data.DataTable.ColumnChanging> Ereignis. Wenn ausgelöst, wird dieses Ereignis übergibt ein Ereignisargument (<xref:System.Data.DataColumnChangeEventArgs.ProposedValue%2A>), enthält den Wert, der für die aktuelle Spalte vorgeschlagen werden wird. Basierend auf den Inhalt der `e.ProposedValue`, können Sie:  
  
- Den vorgeschlagenen Wert annehmen, indem Sie nichts tun.  
  
- Den vorgeschlagenen Wert ablehnen, indem Sie den Spaltenfehler festlegen (<xref:System.Data.DataRow.SetColumnError%2A>) von in der Column-changing-Ereignishandler.  
  
- Optional können Sie ein <xref:System.Windows.Forms.ErrorProvider>-Steuerelement verwenden, um dem Benutzer eine Fehlermeldung anzuzeigen. Weitere Informationen finden Sie unter [ErrorProvider-Komponente](http://msdn.microsoft.com/library/c0f2e231-c5c9-413d-a507-75af2db499b6).  
  
  Überprüfung kann auch ausgeführt werden, während die <xref:System.Data.DataTable.RowChanging> Ereignis. Weitere Informationen finden Sie unter [Vorgehensweise: Validieren von Daten während Zeilenänderungen](http://msdn.microsoft.com/library/afc03c77-dfed-4302-9376-929400468ecc).  
  
## <a name="validate-data-during-row-changes"></a>Validieren von Daten während zeilenänderungen  
 Sie können Code schreiben, um sicherzustellen, dass alle zu validierenden Spalten Daten enthalten, die den Anforderungen der Anwendung entsprechen. Klicken Sie dazu die Spalte an, wenn sie einen Fehler enthält, wenn ein vorgeschlagene Wert unzulässig ist. In den folgenden Beispielen wird ein Spaltenfehler festgelegt, wenn für die `Quantity`-Spalte ein Wert von 0 oder weniger gilt. Die Ereignishandler für Zeilenänderungen sollten den folgenden Beispielen entsprechen.  
  
#### <a name="to-validate-data-when-a-row-changes-visual-basic"></a>So validieren Sie Daten bei Zeilenänderungen (Visual Basic)  
  
1.  Öffnen Sie das Dataset im **DataSet-Designer**. Weitere Informationen finden Sie unter [Vorgehensweise: Öffnen Sie ein Dataset im Dataset-Designer](http://msdn.microsoft.com/library/36fc266f-365b-42cb-aebb-c993dc2c47c3).  
  
2.  Doppelklicken Sie auf die Titelleiste der zu validierenden Tabelle. Durch diese Aktion wird der <xref:System.Data.DataTable.RowChanging>-Ereignishandler der <xref:System.Data.DataTable> in der Datei für die partielle Klasse des Datasets automatisch erstellt.  
  
    > [!TIP]
    >  Doppelklicken Sie links neben den Tabellennamen, um den Ereignishandler für Zeilenänderungen zu erstellen. Wenn Sie den Tabellennamen doppelklicken, können Sie es bearbeiten.  
  
     [!code-vb[VbRaddataValidating#3](../snippets/visualbasic/VS_Snippets_VBCSharp/VbRaddataValidating/VB/NorthwindDataSet.vb#3)]  
  
#### <a name="to-validate-data-when-a-row-changes-c"></a>So validieren Sie Daten bei Zeilenänderungen (C#)  
  
1.  Öffnen Sie das Dataset im **DataSet-Designer**. Weitere Informationen finden Sie unter [Vorgehensweise: Öffnen Sie ein Dataset im Dataset-Designer](http://msdn.microsoft.com/library/36fc266f-365b-42cb-aebb-c993dc2c47c3).  
  
2.  Doppelklicken Sie auf die Titelleiste der zu validierenden Tabelle. Durch diese Aktion wird eine Datei für die partielle Klasse der <xref:System.Data.DataTable> erstellt.  
  
    > [!NOTE]
    >  Der **DataSet-Designer** erstellt nicht automatisch einen Ereignishandler für das <xref:System.Data.DataTable.RowChanging>-Ereignis. Sie müssen eine Methode zum Behandeln von erstellen die <xref:System.Data.DataTable.RowChanging> Ereignis und Ausführen von Code, um das Ereignis in der Tabelle Initialisierungsmethode einzubinden.  
  
3.  Kopieren Sie den folgenden Code in die partielle Klasse:  
  
    ```  
    public override void EndInit()  
    {  
        base.EndInit();  
        Order_DetailsRowChanging += TestRowChangeEvent;  
    }  
  
    public void TestRowChangeEvent(object sender, Order_DetailsRowChangeEvent e)  
    {  
        if ((short)e.Row.Quantity <= 0)  
        {  
            e.Row.SetColumnError("Quantity", "Quantity must be greater than 0");  
        }  
        else  
        {  
            e.Row.SetColumnError("Quantity", "");  
        }  
    }  
    ```  
  
## <a name="to-retrieve-changed-rows"></a>Abrufen von geänderten Zeilen  
 Jede Zeile in einer Datentabelle verfügt über eine <xref:System.Data.DataRow.RowState%2A> Eigenschaft, die überwacht den aktuellen Zustand der Zeile mit den Werten in der <xref:System.Data.DataRowState> Enumeration. Sie können die geänderte Zeilen aus einer Tabelle Datasets oder eines zurückkehren, indem die `GetChanges` Methode eine <xref:System.Data.DataSet> oder <xref:System.Data.DataTable>. Sie können überprüfen, ob Änderungen vorhanden, vor dem Aufruf sind `GetChanges` durch Aufrufen der <xref:System.Data.DataSet.HasChanges%2A> -Methode eines Datasets. Weitere Informationen zum Verwenden von <xref:System.Data.DataSet.HasChanges%2A> finden Sie unter [Vorgehensweise: Überprüfen auf geänderte Zeilen](http://msdn.microsoft.com/library/af160d20-472b-4c13-8f15-75480c39a653).  
  
> [!NOTE]
>  Nachdem ein Dataset oder eine Datentabelle commit von Änderungen (durch Aufrufen der <xref:System.Data.DataSet.AcceptChanges%2A> Methode), wird die `GetChanges` Methode keine Daten zurückgibt. Wenn Ihre Anwendung geänderte Zeilen verarbeiten muss, müssen Sie die Änderungen vor dem Aufruf verarbeiten die `AcceptChanges` Methode.  
  
 Aufrufen der <xref:System.Data.DataSet.GetChanges%2A> Methodenrückgabe einer Datasets oder einer Tabelle eine neue Datasets oder eines-Tabelle, die nur Datensätze enthält, die geändert wurden. Wenn Sie bestimmte Datensätze abrufen möchten – z. B. nur neue oder geänderte Datensätze – können Sie einen Wert von übergeben die <xref:System.Data.DataRowState> -Enumeration als Parameter an die `GetChanges` Methode.  
  
 Verwenden der <xref:System.Data.DataRowVersion> Enumeration, um Zugriff auf die verschiedenen Versionen einer Zeile (z. B. die ursprünglichen Werte, die in einer Zeile aus, bevor diese verarbeitet wird).  
  
#### <a name="to-get-all-changed-records-from-a-dataset"></a>Um alle geänderten Datensätze aus einem Dataset zu erhalten.  
  
-   Rufen Sie die <xref:System.Data.DataSet.GetChanges%2A> -Methode eines Datasets.  
  
     Das folgende Beispiel erstellt ein neues Dataset namens `changedRecords` und füllt sie mit der geänderten Datensätze aus einem anderen Dataset `dataSet1`.  
  
     [!code-csharp[VbRaddataEditing#14](../snippets/csharp/VS_Snippets_VBCSharp/VbRaddataEditing/CS/Form1.cs#14)]
     [!code-vb[VbRaddataEditing#14](../snippets/visualbasic/VS_Snippets_VBCSharp/VbRaddataEditing/VB/Form1.vb#14)]  
  
#### <a name="to-get-all-changed-records-from-a-data-table"></a>So rufen Sie alle geänderten Datensätze aus einer Datentabelle ab  
  
-   Rufen Sie die <xref:System.Data.DataTable.GetChanges%2A> Methode von einer "DataTable".  
  
     Das folgende Beispiel erstellt eine neue Datentabelle namens `changedRecordsTable` und füllt sie mit der geänderten Datensätze aus einer anderen Datentabelle `dataTable1`.  
  
     [!code-csharp[VbRaddataEditing#15](../snippets/csharp/VS_Snippets_VBCSharp/VbRaddataEditing/CS/Form1.cs#15)]
     [!code-vb[VbRaddataEditing#15](../snippets/visualbasic/VS_Snippets_VBCSharp/VbRaddataEditing/VB/Form1.vb#15)]  
  
#### <a name="to-get-all-records-that-have-a-specific-row-state"></a>Abrufen aller Datensätze, die einen bestimmte Zeile (Zustand)  
  
-   Rufen Sie die `GetChanges` -Methode der ein Dataset oder einer Datentabelle und übergeben Sie einen <xref:System.Data.DataRowState> Enumerationswert als Argument.  
  
     Das folgende Beispiel zeigt, wie Sie ein neues Dataset namens erstellen `addedRecords` und füllen sie nur mit Datensätzen, die hinzugefügt wurden die `dataSet1` Dataset.  
  
     [!code-csharp[VbRaddataEditing#16](../snippets/csharp/VS_Snippets_VBCSharp/VbRaddataEditing/CS/Form1.cs#16)]
     [!code-vb[VbRaddataEditing#16](../snippets/visualbasic/VS_Snippets_VBCSharp/VbRaddataEditing/VB/Form1.vb#16)]  
  
-   Das folgende Beispiel zeigt, wie Sie alle Datensätze zurückzugeben, die vor kurzem hinzugefügt wurden, die `Customers` Tabelle:  
  
     [!code-csharp[VbRaddataEditing#17](../snippets/csharp/VS_Snippets_VBCSharp/VbRaddataEditing/CS/Form1.cs#17)]
     [!code-vb[VbRaddataEditing#17](../snippets/visualbasic/VS_Snippets_VBCSharp/VbRaddataEditing/VB/Form1.vb#17)]  
  
## <a name="access-the-original-version-of-a-datarow"></a>Zugriff auf die ursprüngliche Version einer DataRow  
 Wenn an Datenzeilen Änderungen vorgenommen werden, werden im Dataset sowohl die ursprüngliche (<xref:System.Data.DataRowVersion>) als auch die neue (<xref:System.Data.DataRowVersion>) Version der Zeile beibehalten. Vor dem Aufruf der `AcceptChanges`-Methode kann die Anwendung z. B. auf die verschiedenen (in der <xref:System.Data.DataRowVersion>-Enumeration definierten) Versionen eines Datensatzes zugreifen und die Änderungen entsprechend verarbeiten.  
  
> [!NOTE]
>  Verschiedene Versionen einer Zeile vorhanden sind, erst nach Abschluss der Bearbeitung und bevor sie die `AcceptChanges` -Methode aufgerufen wurde. Nach dem Aufruf der `AcceptChanges`-Methode sind die ursprüngliche und die aktuelle Version identisch.  
  
 Wenn Sie den <xref:System.Data.DataRowVersion>-Wert zusammen mit dem Spaltenindex (oder dem Spaltennamen als Zeichenfolge) übergeben, wird der Wert der spezifischen Zeilenversion aus dieser Spalte zurückgegeben. Die geänderte Spalte identifiziert wird, während die <xref:System.Data.DataTable.ColumnChanging> und <xref:System.Data.DataTable.ColumnChanged> Ereignisse. Dies ist ein guter Zeitpunkt für die verschiedenen Zeilenversionen zu Validierungszwecken zu untersuchen. Jedoch wenn Sie haben die Einschränkungen vorübergehend ausgesetzt, diese Ereignisse wird nicht ausgelöst werden und Sie programmgesteuert müssen Identifizieren der Spalten geändert haben. Sie können dazu die <xref:System.Data.DataTable.Columns%2A>-Auflistung durchlaufen und die unterschiedlichen <xref:System.Data.DataRowVersion>-Werte vergleichen.  
  
#### <a name="to-get-the-original-version-of-a-record"></a>So rufen Sie die ursprüngliche Datensatzversion ab  
  
-   Zugriff auf den Wert einer Spalte durch die Übergabe der <xref:System.Data.DataRowVersion> der Zeile zurückgegeben werden soll.  
  
     Das folgende Beispiel zeigt, wie Sie mit einer <xref:System.Data.DataRowVersion> den ursprünglichen Wert des abzurufenden Werts eine `CompanyName` Feld eine <xref:System.Data.DataRow>:  
  
     [!code-csharp[VbRaddataEditing#21](../snippets/csharp/VS_Snippets_VBCSharp/VbRaddataEditing/CS/Form1.cs#21)]
     [!code-vb[VbRaddataEditing#21](../snippets/visualbasic/VS_Snippets_VBCSharp/VbRaddataEditing/VB/Form1.vb#21)]  
  
## <a name="access-the-current-version-of-a-datarow"></a>Zugriff auf die aktuelle Version einer DataRow  
  
#### <a name="to-get-the-current-version-of-a-record"></a>So rufen Sie die aktuelle Datensatzversion ab  
  
-   Zugriff auf den Wert einer Spalte, und fügen Sie einen Parameter klicken Sie dann auf den Index, der angibt, welche Version einer Zeile, die Sie zurückgeben möchten.  
  
     Das folgende Beispiel zeigt, wie Sie mit einer <xref:System.Data.DataRowVersion> den aktuellen Wert des abzurufenden Werts eine `CompanyName` Feld eine <xref:System.Data.DataRow>:  
  
     [!code-csharp[VbRaddataEditing#22](../snippets/csharp/VS_Snippets_VBCSharp/VbRaddataEditing/CS/Form1.cs#22)]
     [!code-vb[VbRaddataEditing#22](../snippets/visualbasic/VS_Snippets_VBCSharp/VbRaddataEditing/VB/Form1.vb#22)]  
  
## <a name="see-also"></a>Siehe auch

- [Vorgehensweise: Überprüfen von Daten in das DataGridView-Steuerelement in Windows Forms](http://msdn.microsoft.com/library/d10aef35-701e-4a3c-a684-2a2ed1aeaca6)   
- [Vorgehensweise: Anzeigen von Fehlersymbolen für die Formularvalidierung mit der ErrorProvider-Komponente in Windows Forms](http://msdn.microsoft.com/library/3b681a32-9db4-497b-a34b-34980eabee46)