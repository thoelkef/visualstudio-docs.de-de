---
title: "Überprüfen Sie die Daten in Datasets | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
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
caps.latest.revision: "24"
author: gewarren
ms.author: gewarren
manager: ghogen
ms.technology: vs-data-tools
ms.openlocfilehash: 0f328cbaac03680885bdbda97dff7bc9ac3cf2cf
ms.sourcegitcommit: ee42a8771f0248db93fd2e017a22e2506e0f9404
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 11/09/2017
---
# <a name="validate-data-in-datasets"></a>Überprüfen Sie die Daten in datasets
Validieren von Daten ist der Prozess der bestätigt, den die Werte, die in Datenobjekte eingegeben werden, die diese Einschränkungen in einer Dataset-Schemas entsprechen. Dieser Vorgang wird bestätigt, dass diese Werte die Regeln eingehalten werden, die für Ihre Anwendung eingerichtet wurden. Es wird empfohlen, überprüfen Sie die Daten vor dem Senden von Updates der zugrunde liegenden Datenbank. Dies reduziert die Fehler als auch die potenzielle Anzahl von Roundtrips zwischen einer Anwendung und der Datenbank.  
  
Sie können bestätigen, dass Daten, die ein Dataset geschrieben wird gültig ist, indem die Überprüfungen in das Dataset selbst erstellen. Das Dataset überprüfen können Sie die Daten unabhängig davon, wie das Update ausgeführt wird – direkt über Steuerelemente in einem Formular in einer Komponente oder auf andere Weise. Da das Dataset Teil Ihrer Anwendung (im Gegensatz zu den Datenbank-Back-End) ist, ist es eine logische Ort anwendungsspezifische Validierungen erstellen.  
  
Die beste Möglichkeit zum Hinzufügen von Validierung zu Ihrer Anwendung ist in der partiellen Klassendatei für das Dataset. In [!INCLUDE[vbprvb](../code-quality/includes/vbprvb_md.md)] oder [!INCLUDE[csprcs](../data-tools/includes/csprcs_md.md)]öffnen die **Dataset-Designer** und doppelklicken Sie auf die Spalte oder Tabelle, für die Sie erstellen möchten. Erstellt diese Aktion automatisch eine <xref:System.Data.DataTable.ColumnChanging> oder <xref:System.Data.DataTable.RowChanging> -Ereignishandler. 
  
## <a name="validate-data"></a>Überprüfen von Daten  
 Überprüfung innerhalb eines Datasets kann auf folgenden Arten erfolgen:  
  
-   Erstellen Sie eigene anwendungsspezifische Validierungen, die Werte in eine einzelne Datenspalte während der Änderungen überprüfen kann.  Weitere Informationen finden Sie unter [Vorgehensweise: Überprüfen Sie Daten während Spaltenänderungen](validate-data-in-datasets.md).  
  
-   Erstellen Sie eigene anwendungsspezifische Validierungen, die die Daten mit Werten, die während einer gesamten Daten prüfen kann ändert Zeile. Weitere Informationen finden Sie unter [Vorgehensweise: Überprüfen Sie Daten während Zeilenänderungen](validate-data-in-datasets.md).  
  
-   Durch Erstellen von Schlüsseln, unique-Einschränkungen usw. als Teil der tatsächliche Schema-Definition des Datasets. 
  
-   Durch Festlegen der Eigenschaften von der <xref:System.Data.DataColumn> des Objekts, z. B. <xref:System.Data.DataColumn.MaxLength%2A>, <xref:System.Data.DataColumn.AllowDBNull%2A>, und <xref:System.Data.DataColumn.Unique%2A>.  
  
Mehrere Ereignisse ausgelöst werden, indem die <xref:System.Data.DataTable> Objekt, wenn eine Änderung in einem Datensatz auftritt:  
  
-   Die <xref:System.Data.DataTable.ColumnChanging> und <xref:System.Data.DataTable.ColumnChanged> Ereignisse werden ausgelöst, während und nach jeder Änderung an einer einzelnen Spalte. Die <xref:System.Data.DataTable.ColumnChanging> Ereignis ist nützlich, wenn Sie Änderungen in bestimmte Spalten überprüfen möchten. Informationen zum Ändern der vorgeschlagenen wird als ein Argument mit dem Ereignis übergeben. 
-   Die <xref:System.Data.DataTable.RowChanging> und <xref:System.Data.DataTable.RowChanged> Ereignisse werden ausgelöst, während und nach jeder Änderung in einer Zeile. Die <xref:System.Data.DataTable.RowChanging> Ereignis allgemeineren ist. Er gibt an, dass eine Änderung an einer beliebigen Stelle in der Zeile aufgetreten ist, aber Sie nicht wissen, welche Spalte geändert hat.  
  
Standardmäßig löst jede Änderung an einer Spalte daher vier Ereignisse. Die erste ist die <xref:System.Data.DataTable.ColumnChanging> und <xref:System.Data.DataTable.ColumnChanged> Ereignisse für die spezifische Spalte, die geändert wird. Als Nächstes werden die <xref:System.Data.DataTable.RowChanging> und <xref:System.Data.DataTable.RowChanged> Ereignisse. Wenn mehrere Änderungen auf die Zeile vorgenommen werden gerade, werden die Ereignisse für jede Änderung ausgelöst.  
  
> [!NOTE]
>  Der Datenzeile <xref:System.Data.DataRow.BeginEdit%2A> Methode deaktiviert die <xref:System.Data.DataTable.RowChanging> und <xref:System.Data.DataTable.RowChanged> Ereignisse nach jeder einzelnen Spalte ändern. Das Ereignis wird in diesem Fall nicht ausgelöst, bis die <xref:System.Data.DataRow.EndEdit%2A> Methode wurde aufgerufen, wenn die <xref:System.Data.DataTable.RowChanging> und <xref:System.Data.DataTable.RowChanged> Ereignisse werden nur einmal ausgelöst. Weitere Informationen finden Sie unter [Deaktivieren von Einschränkungen beim Auffüllen von Datasets](../data-tools/turn-off-constraints-while-filling-a-dataset.md).  
  
Das Ereignis, das Sie auswählen, hängt davon ab, wie präzise die Validierung werden soll. Wenn es wichtig ist, dass einen Fehler erfasst werden sofort, wenn eine Spalte ändert, erstellen Sie Überprüfung mithilfe der <xref:System.Data.DataTable.ColumnChanging> Ereignis. Verwenden Sie andernfalls die <xref:System.Data.DataTable.RowChanging> Ereignis, das möglicherweise dazu führt, gleichzeitig mehrere Fehler abgefangen. Darüber hinaus, wenn Ihre Daten so strukturiert ist, dass der Wert einer Spalte basierend auf dem Inhalt einer anderen Spalte überprüft wird, führen Sie dann die Validierung während der <xref:System.Data.DataTable.RowChanging> Ereignis.
  
Wenn Datensätze aktualisiert werden, die <xref:System.Data.DataTable> Objekt löst Ereignisse aus, die Sie reagieren kann, wie Änderungen auftreten, und nachdem Änderungen vorgenommen wurden.  
  
Wenn Ihre Anwendung ein typisiertes Dataset verwendet, können Sie stark typisierte Ereignishandler erstellen. Dadurch wird die vier zusätzliche typisierte Ereignisse, die Handler für erstellen, können hinzugefügt: `dataTableNameRowChanging`, `dataTableNameRowChanged`, `dataTableNameRowDeleting`, und `dataTableNameRowDeleted`. Diese typisierten Ereignishandler übergeben Sie ein Argument, das die Spaltennamen der Tabelle enthält, die zum Schreiben und Lesen von Code erleichtern.  
  
## <a name="data-update-events"></a>Ereignisse zum Aktualisieren von Daten  
  
|Ereignis|Beschreibung|  
|-----------|-----------------|  
|<xref:System.Data.DataTable.ColumnChanging>|Der Wert in einer Spalte ist geändert wird. Das Ereignis übergibt die Zeilen und Spalten an, die Sie zusammen mit den vorgeschlagenen neuen Wert.|  
|<xref:System.Data.DataTable.ColumnChanged>|Der Wert in einer Spalte wurde geändert. Das Ereignis übergibt die Zeilen und Spalten an, die Sie zusammen mit den vorgeschlagenen Wert.|  
|<xref:System.Data.DataTable.RowChanging>|Die zu vorgenommenen Änderungen eine <xref:System.Data.DataRow> Objekt sind im Begriff, zurück in das Dataset ein Commit ausgeführt werden. Wenn Sie nicht aufgerufen haben die <xref:System.Data.DataRow.BeginEdit%2A> -Methode, die <xref:System.Data.DataTable.RowChanging> Ereignis wird für jede Änderung an einer Spalte unmittelbar nach der <xref:System.Data.DataTable.ColumnChanging> Ereignis ausgelöst wurde. Wenn Sie aufgerufen <xref:System.Data.DataRow.BeginEdit%2A> bevor die Änderungen, die <xref:System.Data.DataTable.RowChanging> Ereignis wird nur bei Aufruf der <xref:System.Data.DataRow.EndEdit%2A> Methode.<br /><br /> Das Ereignis übergibt die Zeile an, die Sie zusammen mit einem Wert, der angibt, welche Art von Aktion (ändern, einfügen und So weiter) ausgeführt wird.|  
|<xref:System.Data.DataTable.RowChanged>|Eine Zeile wurde geändert. Das Ereignis übergibt die Zeile an, die Sie zusammen mit einem Wert, der angibt, welche Art von Aktion (ändern, einfügen und So weiter) ausgeführt wird.|  
|<xref:System.Data.DataTable.RowDeleting>|Eine Zeile wird gelöscht. Das Ereignis übergibt die Zeile an, die Sie zusammen mit einem Wert, der angibt, welche Art von Aktion (Delete) ausgeführt wird.|  
|<xref:System.Data.DataTable.RowDeleted>|Eine Zeile wurde gelöscht. Das Ereignis übergibt die Zeile an, die Sie zusammen mit einem Wert, der angibt, welche Art von Aktion (Delete) ausgeführt wird.|  
  
Die <xref:System.Data.DataTable.ColumnChanging>, <xref:System.Data.DataTable.RowChanging>, und <xref:System.Data.DataTable.RowDeleting> Ereignisse werden ausgelöst, während des Aktualisierungsvorgangs. Sie können diese Ereignisse verwenden, Überprüfen von Daten oder andere Arten von Verarbeitung durchzuführen. Da das Update im Prozess während dieser Ereignisse ist, können Sie es abbrechen, indem eine Ausnahme auszulösen, wird verhindert, dass das Update vom abschließen.  
  
Die <xref:System.Data.DataTable.ColumnChanged>, <xref:System.Data.DataTable.RowChanged> und <xref:System.Data.DataTable.RowDeleted> Ereignisse sind Notification-Ereignisse, die ausgelöst werden, wenn das Update erfolgreich abgeschlossen wurde. Diese Ereignisse sind nützlich, wenn Sie weitere basierend auf einer erfolgreichen Aktualisierung Maßnahmen zu ergreifen möchten.  
  
## <a name="validate-data-during-column-changes"></a>Validieren von Daten während Spaltenänderungen  
  
> [!NOTE]
>  Die **Dataset-Designer** erstellt eine partielle Klasse, die in die Überprüfung auf ein Dataset Logik hinzugefügt werden kann. Die vom Designer generierte Dataset nicht gelöscht bzw. ändert keinen Code in der partiellen Klasse.  
  
Sie können Daten validieren, wenn der Wert in einer Datenspalte geändert wird, indem Sie die Antworten auf die <xref:System.Data.DataTable.ColumnChanging> Ereignis. Wenn ausgelöst, dieses Ereignis übergibt es ein Ereignisargument (<xref:System.Data.DataColumnChangeEventArgs.ProposedValue%2A>), enthält den Wert, der für die aktuelle Spalte vorgeschlagen werden wird. Basierend auf den Inhalt des `e.ProposedValue`, können Sie:  
  
-   Den vorgeschlagenen Wert annehmen, indem Sie nichts tun.  
  
-   Den vorgeschlagenen Wert ablehnen, indem Sie den Spaltenfehler festlegen (<xref:System.Data.DataRow.SetColumnError%2A>) von innerhalb der Column-changing-Ereignishandler.  
  
-   Optional können Sie ein <xref:System.Windows.Forms.ErrorProvider>-Steuerelement verwenden, um dem Benutzer eine Fehlermeldung anzuzeigen. Weitere Informationen finden Sie unter [ErrorProvider-Komponente](/dotnet/framework/winforms/controls/errorprovider-component-windows-forms).  
  
Überprüfung kann auch ausgeführt werden, während die <xref:System.Data.DataTable.RowChanging> Ereignis. 
  
## <a name="validate-data-during-row-changes"></a>Validieren von Daten während zeilenänderungen  
Sie können Code schreiben, um sicherzustellen, dass alle zu validierenden Spalten Daten enthalten, die den Anforderungen der Anwendung entsprechen. Geben Sie dazu die Spalte fest, dass er einen Fehler enthält, wenn ein vorgeschlagene Wert unzulässig ist. In den folgenden Beispielen wird ein Spaltenfehler festgelegt, wenn für die `Quantity`-Spalte ein Wert von 0 oder weniger gilt. Die Ereignishandler für Zeilenänderungen sollten den folgenden Beispielen entsprechen.  
  
#### <a name="to-validate-data-when-a-row-changes-visual-basic"></a>So validieren Sie Daten bei Zeilenänderungen (Visual Basic)  
  
1.  Öffnen Sie das Dataset in die **Dataset-Designer**. Weitere Informationen finden Sie unter [Exemplarische Vorgehensweise: Erstellen eines Datasets im Dataset-Designer](walkthrough-creating-a-dataset-with-the-dataset-designer.md).  
  
2.  Doppelklicken Sie auf die Titelleiste der zu validierenden Tabelle. Durch diese Aktion wird der <xref:System.Data.DataTable.RowChanging>-Ereignishandler der <xref:System.Data.DataTable> in der Datei für die partielle Klasse des Datasets automatisch erstellt.  
  
    > [!TIP]
    >  Doppelklicken Sie links neben den Tabellennamen, um den Ereignishandler für Zeilenänderungen zu erstellen. Wenn Sie den Tabellennamen doppelklicken, können Sie es bearbeiten.  
  
     [!code-vb[VbRaddataValidating#3](../data-tools/codesnippet/VisualBasic/validate-data-in-datasets_1.vb)]  
  
#### <a name="to-validate-data-when-a-row-changes-c"></a>So validieren Sie Daten bei Zeilenänderungen (C#)  
  
1.  Öffnen Sie das Dataset in die **Dataset-Designer**. Weitere Informationen finden Sie unter [Exemplarische Vorgehensweise: Erstellen eines Datasets im Dataset-Designer](walkthrough-creating-a-dataset-with-the-dataset-designer.md).  
  
2.  Doppelklicken Sie auf die Titelleiste der zu validierenden Tabelle. Durch diese Aktion wird eine Datei für die partielle Klasse der <xref:System.Data.DataTable> erstellt.  
  
    > [!NOTE]
    >  Die **Dataset-Designer** erstellt nicht automatisch einen Ereignishandler für das <xref:System.Data.DataTable.RowChanging> Ereignis. Erstellen Sie eine Methode zum Behandeln der <xref:System.Data.DataTable.RowChanging> Ereignis und Ausführen von Code, um das Ereignis in der Initialisierungsmethode der Tabelle zu verknüpfen.  
  
3.  Kopieren Sie den folgenden Code in die partielle Klasse:  
  
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
  
## <a name="to-retrieve-changed-rows"></a>Zum Abrufen von geänderter Zeilen  
Jede Zeile in einer Tabelle verfügt über eine <xref:System.Data.DataRow.RowState%2A> Eigenschaft, die überwacht den aktuellen Status der betreffenden Zeile mithilfe der Werte in der <xref:System.Data.DataRowState> Enumeration. Sie können die geänderte Zeilen aus einer Tabelle Datasets oder eines zurückgeben, durch Aufrufen der `GetChanges` Methode von einer <xref:System.Data.DataSet> oder <xref:System.Data.DataTable>. Sie können überprüfen, ob Änderungen vorhanden, vor dem Aufruf sind `GetChanges` durch Aufrufen der <xref:System.Data.DataSet.HasChanges%2A> -Methode eines Datasets. 
  
> [!NOTE]
>  Nach dem commit der Änderungen an einer Tabelle Dataset oder einem (durch Aufrufen der <xref:System.Data.DataSet.AcceptChanges%2A> Methode), wird die `GetChanges` Methode keine Daten zurückgibt. Wenn Ihre Anwendung geänderte Zeilen verarbeiten muss, müssen Sie die Änderungen vor dem Aufruf verarbeiten die `AcceptChanges` Methode.  
  
Aufrufen der <xref:System.Data.DataSet.GetChanges%2A> Methodenrückgabe Tabellenstatus Dataset oder eine neue Datasets oder eines-Tabelle, die nur Datensätze enthält, die geändert wurden. Wenn Sie bestimmte Datensätze abrufen möchten – z. B. nur neue oder geänderte Datensätze – kann, übergeben Sie den Wert aus der <xref:System.Data.DataRowState> -Enumeration als Parameter an die `GetChanges` Methode.  
  
Verwenden der <xref:System.Data.DataRowVersion> Enumeration, um Zugriff auf die verschiedenen Versionen einer Zeile (z. B. die ursprünglichen Werte, die in einer Zeile vor dem verarbeiten, es waren).  
  
#### <a name="to-get-all-changed-records-from-a-dataset"></a>Alle geänderten Datensätze aus einem Dataset abrufen  
  
-   Rufen Sie die <xref:System.Data.DataSet.GetChanges%2A> -Methode eines Datasets.  
  
     Das folgende Beispiel erstellt ein neues Dataset mit dem Namen `changedRecords` und füllt sie mit der geänderten Datensätze aus einem anderen Dataset mit dem Namen `dataSet1`.  
  
     [!code-csharp[VbRaddataEditing#14](../data-tools/codesnippet/CSharp/validate-data-in-datasets_2.cs)]
     [!code-vb[VbRaddataEditing#14](../data-tools/codesnippet/VisualBasic/validate-data-in-datasets_2.vb)]  
  
#### <a name="to-get-all-changed-records-from-a-data-table"></a>Alle geänderten Datensätze aus einer Datentabelle abrufen  
  
-   Rufen Sie die <xref:System.Data.DataTable.GetChanges%2A> Methode von einer "DataTable".  
  
     Das folgende Beispiel erstellt eine neue Datentabelle aufgerufen `changedRecordsTable` und füllt sie mit der geänderten Datensätze aus einer anderen Datentabelle `dataTable1`.  
  
     [!code-csharp[VbRaddataEditing#15](../data-tools/codesnippet/CSharp/validate-data-in-datasets_3.cs)]
     [!code-vb[VbRaddataEditing#15](../data-tools/codesnippet/VisualBasic/validate-data-in-datasets_3.vb)]  
  
#### <a name="to-get-all-records-that-have-a-specific-row-state"></a>Um alle Datensätze abzurufen, die einen bestimmten Zeilenstatus haben  
  
-   Rufen Sie die `GetChanges` -Methode eines Datasets oder einer Datentabelle und übergeben Sie eine <xref:System.Data.DataRowState> Enumerationswert als Argument.  
  
     Im folgende Beispiel wird gezeigt, wie ein neues Dataset mit dem Namen erstellen `addedRecords` und weisen Sie ihm nur mit Datensätzen, die hinzugefügt wurden die `dataSet1` Dataset.  
  
     [!code-csharp[VbRaddataEditing#16](../data-tools/codesnippet/CSharp/validate-data-in-datasets_4.cs)]
     [!code-vb[VbRaddataEditing#16](../data-tools/codesnippet/VisualBasic/validate-data-in-datasets_4.vb)]  
  
     Das folgende Beispiel zeigt, wie Sie alle Datensätze zurückzugeben, die kürzlich hinzugefügt wurden die `Customers` Tabelle:  
  
     [!code-csharp[VbRaddataEditing#17](../data-tools/codesnippet/CSharp/validate-data-in-datasets_5.cs)]
     [!code-vb[VbRaddataEditing#17](../data-tools/codesnippet/VisualBasic/validate-data-in-datasets_5.vb)]  
  
## <a name="access-the-original-version-of-a-datarow"></a>Zugriff auf die ursprüngliche Version einer DataRow  
Wenn an Datenzeilen Änderungen vorgenommen werden, werden im Dataset sowohl die ursprüngliche (<xref:System.Data.DataRowVersion.Original>) als auch die neue (<xref:System.Data.DataRowVersion.Current>) Version der Zeile beibehalten. Vor dem Aufruf der `AcceptChanges`-Methode kann die Anwendung z. B. auf die verschiedenen (in der <xref:System.Data.DataRowVersion>-Enumeration definierten) Versionen eines Datensatzes zugreifen und die Änderungen entsprechend verarbeiten.  
  
> [!NOTE]
>  Verschiedene Versionen einer Zeile vorhanden sind, nachdem er bearbeitet wurde und bevor sie die `AcceptChanges` -Methode aufgerufen wurde. Nach dem Aufruf der `AcceptChanges`-Methode sind die ursprüngliche und die aktuelle Version identisch.  
  
Wenn Sie den <xref:System.Data.DataRowVersion>-Wert zusammen mit dem Spaltenindex (oder dem Spaltennamen als Zeichenfolge) übergeben, wird der Wert der spezifischen Zeilenversion aus dieser Spalte zurückgegeben. Die geänderte Spalte wird während der identifiziert die <xref:System.Data.DataTable.ColumnChanging> und <xref:System.Data.DataTable.ColumnChanged> Ereignisse. Dies ist ein guter Zeitpunkt, die unterschiedliche Zeilenversionen zu Validierungszwecken zu überprüfen. Wenn Sie haben die Einschränkungen vorübergehend ausgesetzt, diese Ereignisse wird nicht ausgelöst werden, müssen Sie programmgesteuert identifizieren Sie jedoch welche Spalten sich geändert haben. Sie können dazu die <xref:System.Data.DataTable.Columns%2A>-Auflistung durchlaufen und die unterschiedlichen <xref:System.Data.DataRowVersion>-Werte vergleichen.  
  
#### <a name="to-get-the-original-version-of-a-record"></a>So rufen Sie die ursprüngliche Datensatzversion ab  
  
-   Zugriff auf den Wert einer Spalte durch die Übergabe der <xref:System.Data.DataRowVersion> der Zeile, die Sie zurückgeben möchten.  
  
     Das folgende Beispiel zeigt, wie Sie eine <xref:System.Data.DataRowVersion> den ursprünglichen Wert des abzurufenden Werts eine `CompanyName` Feld eine <xref:System.Data.DataRow>:  
  
     [!code-csharp[VbRaddataEditing#21](../data-tools/codesnippet/CSharp/validate-data-in-datasets_6.cs)]
     [!code-vb[VbRaddataEditing#21](../data-tools/codesnippet/VisualBasic/validate-data-in-datasets_6.vb)]  
  
## <a name="access-the-current-version-of-a-datarow"></a>Zugriff auf die aktuelle Version einer DataRow  
  
#### <a name="to-get-the-current-version-of-a-record"></a>So rufen Sie die aktuelle Datensatzversion ab  
  
-   Zugriff auf den Wert einer Spalte, und fügen Sie einen Parameter, die dem Index, der angibt, welche Version einer Zeile, die Sie zurückgeben möchten.  
  
     Das folgende Beispiel zeigt, wie Sie eine <xref:System.Data.DataRowVersion> den aktuellen Wert des abzurufenden Werts eine `CompanyName` Feld eine <xref:System.Data.DataRow>:  
  
     [!code-csharp[VbRaddataEditing#22](../data-tools/codesnippet/CSharp/validate-data-in-datasets_7.cs)]
     [!code-vb[VbRaddataEditing#22](../data-tools/codesnippet/VisualBasic/validate-data-in-datasets_7.vb)]  
  
## <a name="see-also"></a>Siehe auch
[Datasettools in Visual Studio](../data-tools/dataset-tools-in-visual-studio.md)  
[Vorgehensweise: Überprüfen Sie die Daten im DataGridView-Steuerelement von Windows Forms](/dotnet/framework/winforms/controls/how-to-validate-data-in-the-windows-forms-datagridview-control)   
[Gewusst wie: Anzeigen von Fehlersymbolen für die Formularvalidierung mit der ErrorProvider-Komponente in Windows Forms](/dotnet/framework/winforms/controls/display-error-icons-for-form-validation-with-wf-errorprovider)