---
title: Überprüfen von Daten in Datasets
ms.date: 11/04/2016
ms.topic: conceptual
f1_keywords:
- DataTable.ColumnChanging
- System.Data.DataTable.ColumnChanging
- System.Data.DataTable.RowChanging
- DataTable.RowChanging
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- data validation, datasets
- data validation
- validating data, datasets
- updating datasets, validating data
ms.assetid: 79500596-1e4d-478e-a991-a636fd73a622
author: gewarren
ms.author: gewarren
manager: jillfra
ms.workload:
- data-storage
ms.openlocfilehash: 1b7ef69d2bb7ac9390c82ffb4e17db27a49637aa
ms.sourcegitcommit: 1fc6ee928733e61a1f42782f832ead9f7946d00c
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/22/2019
ms.locfileid: "60041590"
---
# <a name="validate-data-in-datasets"></a>Überprüfen von Daten in Datasets
Überprüfen von Daten ist der Prozess der Bestätigung der Werte, die in Datenobjekte eingegeben werden, die die Einschränkungen in einer Dataset Schema entsprechen. Der Überprüfungsprozess wird bestätigt, dass diese Werte die Regeln eingehalten werden, die für Ihre Anwendung eingerichtet wurden. Es hat sich bewährt, überprüfen Sie die Daten vor dem Senden von Aktualisierungen an der zugrunde liegenden Datenbank. Dies verringert sowohl Fehler als auch die potenzielle Anzahl von Roundtrips zwischen einer Anwendung und der Datenbank.

Sie können bestätigen, dass Daten, die auf ein Dataset geschrieben werden durch Erstellen von Überprüfungen in das Dataset selbst gültig ist. Das Dataset kann überprüfen Sie die Daten unabhängig davon, wie das Update ausgeführt wird – direkt über die Steuerelemente in einem Formular in eine Komponente, oder auf andere Weise. Da das Dataset Teil Ihrer Anwendung (im Gegensatz zu den Datenbank-Back-End) ist, ist es ein logischer Ansatzpunkt zum anwendungsspezifischen Validierung zu erstellen.

Der beste Ort zum Hinzufügen der Validierung zu Ihrer Anwendung ist in der Datei für die partielle Klasse des Datasets. In [!INCLUDE[vbprvb](../code-quality/includes/vbprvb_md.md)] oder [!INCLUDE[csprcs](../data-tools/includes/csprcs_md.md)]öffnen die **Dataset-Designer** und doppelklicken Sie auf die Spalte oder Tabelle, für die Sie die Überprüfung erstellen möchten. Erstellt diese Aktion automatisch eine <xref:System.Data.DataTable.ColumnChanging> oder <xref:System.Data.DataTable.RowChanging> -Ereignishandler.

## <a name="validate-data"></a>Überprüfen von Daten
 Validierung in einem Dataset erfolgt folgendermaßen:

- Erstellen Sie eigene anwendungsspezifische Validierungen, die während der Änderung der Werte in eine einzelne Spalte überprüfen kann. Weitere Informationen finden Sie unter [Vorgehensweise: Validieren von Daten während Spaltenänderungen](validate-data-in-datasets.md).

- Erstellen Sie eigene anwendungsspezifische Validierungen, die die Daten mit Werten, die während einer gesamten Daten prüfen kann ändert Zeile. Weitere Informationen finden Sie unter [Vorgehensweise: Validieren von Daten während zeilenänderungen](validate-data-in-datasets.md).

- Durch das Erstellen von Schlüsseln, unique-Einschränkungen, und so weiter, als Teil der Schemadefinition des tatsächlichen des Datasets.

- Durch Festlegen der Eigenschaften von den <xref:System.Data.DataColumn> des Objekts, z. B. <xref:System.Data.DataColumn.MaxLength%2A>, <xref:System.Data.DataColumn.AllowDBNull%2A>, und <xref:System.Data.DataColumn.Unique%2A>.

Mehrere Ereignisse ausgelöst werden, indem die <xref:System.Data.DataTable> Objekt, wenn eine Änderung in einem Datensatz auftritt:

- Die <xref:System.Data.DataTable.ColumnChanging> und <xref:System.Data.DataTable.ColumnChanged> Ereignisse werden ausgelöst, während und nach jeder Änderung an einer einzelnen Spalte. Die <xref:System.Data.DataTable.ColumnChanging> Ereignis ist hilfreich, wenn Sie Änderungen in bestimmte Spalten überprüfen möchten. Informationen über die vorgeschlagene Änderung wird als ein Argument mit dem Ereignis übergeben.
- Die <xref:System.Data.DataTable.RowChanging> und <xref:System.Data.DataTable.RowChanged> Ereignisse werden ausgelöst, während und nach einer Änderung in einer Zeile. Die <xref:System.Data.DataTable.RowChanging> Ereignis ist allgemeiner. Er gibt an, dass eine Änderung an einer beliebigen Stelle in der Zeile auftritt, aber Sie wissen nicht, welche Spalte geändert hat.

Standardmäßig löst jede Änderung an einer Spalte aus diesem Grund vier Ereignisse. Die erste ist die <xref:System.Data.DataTable.ColumnChanging> und <xref:System.Data.DataTable.ColumnChanged> Ereignisse für die spezifische Spalte, die geändert wird. Als Nächstes werden die <xref:System.Data.DataTable.RowChanging> und <xref:System.Data.DataTable.RowChanged> Ereignisse. Falls mehrere Änderungen an der Zeile durchgeführt werden, werden die Ereignisse für jede Änderung ausgelöst werden.

> [!NOTE]
>  Der Datenzeile <xref:System.Data.DataRow.BeginEdit%2A> Methode deaktiviert die <xref:System.Data.DataTable.RowChanging> und <xref:System.Data.DataTable.RowChanged> Ereignisse nach jeder Änderung der einzelnen Spalten. Das Ereignis wird in diesem Fall nicht ausgelöst, bis die <xref:System.Data.DataRow.EndEdit%2A> Methode wurde aufgerufen, wenn die <xref:System.Data.DataTable.RowChanging> und <xref:System.Data.DataTable.RowChanged> Ereignisse werden nur einmal ausgelöst. Weitere Informationen finden Sie unter [Deaktivieren von Einschränkungen beim Auffüllen von Datasets](../data-tools/turn-off-constraints-while-filling-a-dataset.md).

Das Ereignis, das Sie auswählen, hängt davon ab, wie präzise die Validierung werden sollen. Wenn es wichtig ist, dass Sie Fehler abfangen, sofort bei einer Spalte ändert, Buildüberprüfung mithilfe der <xref:System.Data.DataTable.ColumnChanging> Ereignis. Verwenden Sie andernfalls die <xref:System.Data.DataTable.RowChanging> -Ereignis, das dazu führen, dass gleichzeitig mehrere Fehler abgefangen. Darüber hinaus, wenn Ihre Daten so strukturiert ist, dass der Wert einer Spalte basierend auf dem Inhalt einer anderen Spalte überprüft wird, führen Sie die Überprüfung während der <xref:System.Data.DataTable.RowChanging> Ereignis.

Wenn Datensätze aktualisiert werden, die <xref:System.Data.DataTable> Objekt löst Ereignisse aus, die Sie reagieren können, wenn Änderungen auftreten, und nachdem Änderungen vorgenommen wurden.

Wenn Ihre Anwendung ein typisiertes Dataset verwendet, können Sie stark typisierte Ereignishandler erstellen. Dadurch werden vier zusätzliche typisierte Ereignisse, die für die Handler erstellen: `dataTableNameRowChanging`, `dataTableNameRowChanged`, `dataTableNameRowDeleting`, und `dataTableNameRowDeleted`. Diese typisiertes Ereignis-Handler übergeben Sie ein Argument, das die Spaltennamen der Tabelle enthält, die zum Schreiben und Lesen von Code vereinfachen.

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

- Optional können Sie ein <xref:System.Windows.Forms.ErrorProvider>-Steuerelement verwenden, um dem Benutzer eine Fehlermeldung anzuzeigen. Weitere Informationen finden Sie unter [ErrorProvider Component (ErrorProvider-Komponente)](/dotnet/framework/winforms/controls/errorprovider-component-windows-forms).

Überprüfung kann auch ausgeführt werden, während die <xref:System.Data.DataTable.RowChanging> Ereignis.

## <a name="validate-data-during-row-changes"></a>Validieren von Daten während zeilenänderungen
Sie können Code schreiben, um sicherzustellen, dass alle zu validierenden Spalten Daten enthalten, die den Anforderungen der Anwendung entsprechen. Klicken Sie dazu die Spalte an, wenn sie einen Fehler enthält, wenn ein vorgeschlagene Wert unzulässig ist. In den folgenden Beispielen wird ein Spaltenfehler festgelegt, wenn für die `Quantity`-Spalte ein Wert von 0 oder weniger gilt. Die Ereignishandler für Zeilenänderungen sollten den folgenden Beispielen entsprechen.

### <a name="to-validate-data-when-a-row-changes-visual-basic"></a>So validieren Sie Daten bei Zeilenänderungen (Visual Basic)

1. Öffnen Sie das Dataset im **DataSet-Designer**. Weitere Informationen finden Sie unter [Exemplarische Vorgehensweise: Erstellen eines Datasets im Dataset-Designer](walkthrough-creating-a-dataset-with-the-dataset-designer.md).

2. Doppelklicken Sie auf die Titelleiste der zu validierenden Tabelle. Durch diese Aktion wird der <xref:System.Data.DataTable.RowChanging>-Ereignishandler der <xref:System.Data.DataTable> in der Datei für die partielle Klasse des Datasets automatisch erstellt.

    > [!TIP]
    >  Doppelklicken Sie links neben den Tabellennamen, um den Ereignishandler für Zeilenänderungen zu erstellen. Wenn Sie den Tabellennamen doppelklicken, können Sie es bearbeiten.

     [!code-vb[VbRaddataValidating#3](../data-tools/codesnippet/VisualBasic/validate-data-in-datasets_1.vb)]

### <a name="to-validate-data-when-a-row-changes-c"></a>So validieren Sie Daten bei Zeilenänderungen (C#)

1. Öffnen Sie das Dataset im **DataSet-Designer**. Weitere Informationen finden Sie unter [Exemplarische Vorgehensweise: Erstellen eines Datasets im Dataset-Designer](walkthrough-creating-a-dataset-with-the-dataset-designer.md).

2. Doppelklicken Sie auf die Titelleiste der zu validierenden Tabelle. Durch diese Aktion wird eine Datei für die partielle Klasse der <xref:System.Data.DataTable> erstellt.

    > [!NOTE]
    >  Der **DataSet-Designer** erstellt nicht automatisch einen Ereignishandler für das <xref:System.Data.DataTable.RowChanging>-Ereignis. Sie müssen eine Methode zum Behandeln von erstellen die <xref:System.Data.DataTable.RowChanging> Ereignis und Ausführen von Code, um das Ereignis in der Tabelle Initialisierungsmethode einzubinden.

3. Kopieren Sie den folgenden Code in die partielle Klasse:

    ```csharp
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
Jede Zeile in einer Datentabelle verfügt über eine <xref:System.Data.DataRow.RowState%2A> Eigenschaft, die überwacht den aktuellen Zustand der Zeile mit den Werten in der <xref:System.Data.DataRowState> Enumeration. Sie können die geänderte Zeilen aus einer Tabelle Datasets oder eines zurückkehren, indem die `GetChanges` Methode eine <xref:System.Data.DataSet> oder <xref:System.Data.DataTable>. Sie können überprüfen, ob Änderungen vorhanden, vor dem Aufruf sind `GetChanges` durch Aufrufen der <xref:System.Data.DataSet.HasChanges%2A> -Methode eines Datasets.

> [!NOTE]
>  Nachdem ein Dataset oder eine Datentabelle commit von Änderungen (durch Aufrufen der <xref:System.Data.DataSet.AcceptChanges%2A> Methode), wird die `GetChanges` Methode keine Daten zurückgibt. Wenn Ihre Anwendung geänderte Zeilen verarbeiten muss, müssen Sie die Änderungen vor dem Aufruf verarbeiten die `AcceptChanges` Methode.

Aufrufen der <xref:System.Data.DataSet.GetChanges%2A> Methodenrückgabe einer Datasets oder einer Tabelle eine neue Datasets oder eines-Tabelle, die nur Datensätze enthält, die geändert wurden. Wenn Sie bestimmte Datensätze abrufen möchten – z. B. nur neue oder geänderte Datensätze – können Sie einen Wert von übergeben die <xref:System.Data.DataRowState> -Enumeration als Parameter an die `GetChanges` Methode.

Verwenden der <xref:System.Data.DataRowVersion> Enumeration, um Zugriff auf die verschiedenen Versionen einer Zeile (z. B. die ursprünglichen Werte, die in einer Zeile aus, bevor diese verarbeitet wird).

### <a name="to-get-all-changed-records-from-a-dataset"></a>Um alle geänderten Datensätze aus einem Dataset zu erhalten.

- Rufen Sie die <xref:System.Data.DataSet.GetChanges%2A> -Methode eines Datasets.

     Das folgende Beispiel erstellt ein neues Dataset namens `changedRecords` und füllt sie mit der geänderten Datensätze aus einem anderen Dataset `dataSet1`.

     [!code-csharp[VbRaddataEditing#14](../data-tools/codesnippet/CSharp/validate-data-in-datasets_2.cs)]
     [!code-vb[VbRaddataEditing#14](../data-tools/codesnippet/VisualBasic/validate-data-in-datasets_2.vb)]

### <a name="to-get-all-changed-records-from-a-data-table"></a>So rufen Sie alle geänderten Datensätze aus einer Datentabelle ab

- Rufen Sie die <xref:System.Data.DataTable.GetChanges%2A> Methode von einer "DataTable".

     Das folgende Beispiel erstellt eine neue Datentabelle namens `changedRecordsTable` und füllt sie mit der geänderten Datensätze aus einer anderen Datentabelle `dataTable1`.

     [!code-csharp[VbRaddataEditing#15](../data-tools/codesnippet/CSharp/validate-data-in-datasets_3.cs)]
     [!code-vb[VbRaddataEditing#15](../data-tools/codesnippet/VisualBasic/validate-data-in-datasets_3.vb)]

### <a name="to-get-all-records-that-have-a-specific-row-state"></a>Abrufen aller Datensätze, die einen bestimmte Zeile (Zustand)

- Rufen Sie die `GetChanges` -Methode der ein Dataset oder einer Datentabelle und übergeben Sie einen <xref:System.Data.DataRowState> Enumerationswert als Argument.

     Das folgende Beispiel zeigt, wie Sie ein neues Dataset namens erstellen `addedRecords` und füllen sie nur mit Datensätzen, die hinzugefügt wurden die `dataSet1` Dataset.

     [!code-csharp[VbRaddataEditing#16](../data-tools/codesnippet/CSharp/validate-data-in-datasets_4.cs)]
     [!code-vb[VbRaddataEditing#16](../data-tools/codesnippet/VisualBasic/validate-data-in-datasets_4.vb)]

     Das folgende Beispiel zeigt, wie Sie alle Datensätze zurückzugeben, die vor kurzem hinzugefügt wurden, die `Customers` Tabelle:

     [!code-csharp[VbRaddataEditing#17](../data-tools/codesnippet/CSharp/validate-data-in-datasets_5.cs)]
     [!code-vb[VbRaddataEditing#17](../data-tools/codesnippet/VisualBasic/validate-data-in-datasets_5.vb)]

## <a name="access-the-original-version-of-a-datarow"></a>Zugriff auf die ursprüngliche Version einer DataRow
Wenn an Datenzeilen Änderungen vorgenommen werden, werden im Dataset sowohl die ursprüngliche (<xref:System.Data.DataRowVersion.Original>) als auch die neue (<xref:System.Data.DataRowVersion.Current>) Version der Zeile beibehalten. Vor dem Aufruf der `AcceptChanges`-Methode kann die Anwendung z. B. auf die verschiedenen (in der <xref:System.Data.DataRowVersion>-Enumeration definierten) Versionen eines Datensatzes zugreifen und die Änderungen entsprechend verarbeiten.

> [!NOTE]
>  Verschiedene Versionen einer Zeile vorhanden sind, erst nach Abschluss der Bearbeitung und bevor sie die `AcceptChanges` -Methode aufgerufen wurde. Nach dem Aufruf der `AcceptChanges`-Methode sind die ursprüngliche und die aktuelle Version identisch.

Wenn Sie den <xref:System.Data.DataRowVersion>-Wert zusammen mit dem Spaltenindex (oder dem Spaltennamen als Zeichenfolge) übergeben, wird der Wert der spezifischen Zeilenversion aus dieser Spalte zurückgegeben. Die geänderte Spalte identifiziert wird, während die <xref:System.Data.DataTable.ColumnChanging> und <xref:System.Data.DataTable.ColumnChanged> Ereignisse. Dies ist ein guter Zeitpunkt für die verschiedenen Zeilenversionen zu Validierungszwecken zu untersuchen. Jedoch wenn Sie haben die Einschränkungen vorübergehend ausgesetzt, diese Ereignisse wird nicht ausgelöst werden und Sie programmgesteuert müssen Identifizieren der Spalten geändert haben. Sie können dazu die <xref:System.Data.DataTable.Columns%2A>-Auflistung durchlaufen und die unterschiedlichen <xref:System.Data.DataRowVersion>-Werte vergleichen.

### <a name="to-get-the-original-version-of-a-record"></a>So rufen Sie die ursprüngliche Datensatzversion ab

- Zugriff auf den Wert einer Spalte durch die Übergabe der <xref:System.Data.DataRowVersion> der Zeile zurückgegeben werden soll.

     Das folgende Beispiel zeigt, wie Sie mit einer <xref:System.Data.DataRowVersion> den ursprünglichen Wert des abzurufenden Werts eine `CompanyName` Feld eine <xref:System.Data.DataRow>:

     [!code-csharp[VbRaddataEditing#21](../data-tools/codesnippet/CSharp/validate-data-in-datasets_6.cs)]
     [!code-vb[VbRaddataEditing#21](../data-tools/codesnippet/VisualBasic/validate-data-in-datasets_6.vb)]

## <a name="access-the-current-version-of-a-datarow"></a>Zugriff auf die aktuelle Version einer DataRow

### <a name="to-get-the-current-version-of-a-record"></a>So rufen Sie die aktuelle Datensatzversion ab

- Zugriff auf den Wert einer Spalte, und fügen Sie einen Parameter klicken Sie dann auf den Index, der angibt, welche Version einer Zeile, die Sie zurückgeben möchten.

     Das folgende Beispiel zeigt, wie Sie mit einer <xref:System.Data.DataRowVersion> den aktuellen Wert des abzurufenden Werts eine `CompanyName` Feld eine <xref:System.Data.DataRow>:

     [!code-csharp[VbRaddataEditing#22](../data-tools/codesnippet/CSharp/validate-data-in-datasets_7.cs)]
     [!code-vb[VbRaddataEditing#22](../data-tools/codesnippet/VisualBasic/validate-data-in-datasets_7.vb)]

## <a name="see-also"></a>Siehe auch

- [Datasettools in Visual Studio](../data-tools/dataset-tools-in-visual-studio.md)
- [Vorgehensweise: Überprüfen von Daten in Windows Forms-DataGridView-Steuerelement](/dotnet/framework/winforms/controls/how-to-validate-data-in-the-windows-forms-datagridview-control)
- [Vorgehensweise: Anzeigen von Fehlersymbolen für die formularvalidierung mit der Windows Forms ErrorProvider-Komponente](/dotnet/framework/winforms/controls/display-error-icons-for-form-validation-with-wf-errorprovider)