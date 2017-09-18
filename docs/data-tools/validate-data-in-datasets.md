---
title: "&#220;berpr&#252;fen von Daten in Datasets | Microsoft Docs"
ms.custom: ""
ms.date: "12/15/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "DataTable.ColumnChanging"
  - "System.Data.DataTable.ColumnChanging"
  - "System.Data.DataTable.RowChanging"
  - "DataTable.RowChanging"
dev_langs: 
  - "VB"
  - "CSharp"
  - "C++"
  - "aspx"
helpviewer_keywords: 
  - "Datenvalidierung"
  - "Datenvalidierung, Datasets"
  - "Aktualisieren von Datasets, Validieren von Daten"
  - "Validieren von Daten, Datasets"
ms.assetid: 79500596-1e4d-478e-a991-a636fd73a622
caps.latest.revision: 24
caps.handback.revision: 17
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# &#220;berpr&#252;fen von Daten in Datasets
Bei der Datenüberprüfung wird kontrolliert, ob die in Datenobjekte eingegebenen Werte mit den Einschränkungen in einem Dataset\-Schema und den für Ihre Anwendung geltenden Regeln konform sind.  Mit Datenüberprüfungen vor dem Senden von Aktualisierungen an die zugrunde liegende Datenbank können Fehler und die mögliche Anzahl von Schleifen zwischen einer Anwendung und der Datenbank reduziert werden.  Die Gültigkeit der in ein Dataset geschriebenen Daten kann bestätigt werden, indem Sie direkt im Dataset Validierungen implementieren.  Die Daten können dann vom Dataset überprüft werden, und zwar unabhängig davon, wie die Aktualisierung erfolgt: direkt über Steuerelemente in einem Formular, innerhalb einer Komponente oder auf andere Weise.  Da das Dataset Teil Ihrer Anwendung ist, bietet es die nächstliegende Möglichkeit für die Integration anwendungsspezifischer Validierungen \(im Gegensatz zur Integration dieser Überprüfungen in das Datenbank\-Back\-End\).  
  
 Wenn Sie die Datenvalidierung in der Anwendung verwenden möchten, sollten Sie sie der Datei der partiellen Klasse des Datasets hinzufügen.  Öffnen Sie in [!INCLUDE[vbprvb](../code-quality/includes/vbprvb_md.md)] oder [!INCLUDE[csprcs](../data-tools/includes/csprcs_md.md)] den **DataSet\-Designer**, und doppelklicken Sie auf die Spalte oder die Tabelle, die Sie überprüfen möchten.  Dadurch wird automatisch ein <xref:System.Data.DataTable.ColumnChanging>\-Ereignishandler oder ein <xref:System.Data.DataTable.RowChanging>\-Ereignishandler erstellt.  Weitere Informationen finden Sie unter [Gewusst wie: Validieren von Daten während Spaltenänderungen](../Topic/How%20to:%20Validate%20Data%20During%20Column%20Changes.md) oder [Gewusst wie: Validieren von Daten während Zeilenänderungen](../Topic/How%20to:%20Validate%20Data%20During%20Row%20Changes.md).  Ein vollständiges Beispiel finden Sie unter [Exemplarische Vorgehensweise: Hinzufügen von Validierung zu einem DataSet](../Topic/Walkthrough:%20Adding%20Validation%20to%20a%20Dataset.md).  
  
## Überprüfen von Daten  
 Validierungen können in einem Dataset wie folgt implementiert werden:  
  
-   Indem Sie eine eigene anwendungsspezifische Validierung erstellen, die während der Änderung von Werten in einer einzelnen Datenspalte Daten überprüft.  Weitere Informationen finden Sie unter [Gewusst wie: Validieren von Daten während Spaltenänderungen](../Topic/How%20to:%20Validate%20Data%20During%20Column%20Changes.md).  
  
-   Indem Sie eine eigene anwendungsspezifische Validierung erstellen, die während der Änderung von Werten in einer ganzen Datenzeile Daten überprüft.  Weitere Informationen finden Sie unter [Gewusst wie: Validieren von Daten während Zeilenänderungen](../Topic/How%20to:%20Validate%20Data%20During%20Row%20Changes.md).  
  
-   Indem Sie Schlüssel, Unique\-Einschränkungen usw. als Teil der aktuellen Schemadefinition des Datasets erstellen.  Weitere Informationen zum Hinzufügen der Datenvalidierung in die Schemadefinition, finden Sie unter [Eine DataColumn darauf beschränken, eindeutige Werte zu enthalten](../Topic/How%20to:%20Add%20Columns%20to%20a%20DataTable.md#SpecifyUniqueConstraint).  
  
-   Indem Sie die Eigenschaften des <xref:System.Data.DataColumn>\-Objekts festlegen, z. B. <xref:System.Data.DataColumn.MaxLength%2A>, <xref:System.Data.DataColumn.AllowDBNull%2A> und <xref:System.Data.DataColumn.Unique%2A>.  
  
 Sobald eine Änderung in einem Datensatz auftritt, werden mehrere Ereignisse vom <xref:System.Data.DataTable>\-Objekt ausgelöst:  
  
-   Die Ereignisse <xref:System.Data.DataTable.ColumnChanging> und <xref:System.Data.DataTable.ColumnChanged> werden während bzw. nach jeder Änderung an einer einzelnen Spalte ausgelöst.  Das <xref:System.Data.DataTable.ColumnChanging>\-Ereignis ist hilfreich, wenn Änderungen in spezifischen Spalten überprüft werden sollen.  Informationen über die vorgeschlagene Änderung werden zusammen mit dem Ereignis als Argument übergeben.  Weitere Informationen finden Sie unter [Gewusst wie: Validieren von Daten während Spaltenänderungen](../Topic/How%20to:%20Validate%20Data%20During%20Column%20Changes.md).  
  
-   Die Ereignisse <xref:System.Data.DataTable.RowChanging> und <xref:System.Data.DataTable.RowChanged> werden während bzw. nach jeder Änderung an einer Zeile ausgelöst.  Das <xref:System.Data.DataTable.RowChanging>\-Ereignis funktioniert globaler, da durch dieses Ereignis lediglich darauf hingewiesen wird, dass eine Änderung an einer Stelle in der Zeile aufgetreten ist, die betroffene Spalte jedoch nicht angegeben wird.  Weitere Informationen finden Sie unter [Gewusst wie: Validieren von Daten während Zeilenänderungen](../Topic/How%20to:%20Validate%20Data%20During%20Row%20Changes.md).  
  
 Standardmäßig werden demnach bei jeder Änderung an einer Spalte vier Ereignisse ausgelöst: zuerst das <xref:System.Data.DataTable.ColumnChanging>\-Ereignis und das <xref:System.Data.DataTable.ColumnChanged>\-Ereignis für die jeweils geänderte Spalte und dann das <xref:System.Data.DataTable.RowChanging>\-Ereignis und das <xref:System.Data.DataTable.RowChanged>\-Ereignis.  Falls die Zeile mehrfach geändert wird, werden die Ereignisse für jede einzelne Änderung ausgelöst.  
  
> [!NOTE]
>  Die <xref:System.Data.DataRow.BeginEdit%2A>\-Methode der Datenzeile deaktiviert die Ereignisse <xref:System.Data.DataTable.RowChanging> und <xref:System.Data.DataTable.RowChanged> nach jeder einzelnen Spaltenänderung.  Wenn die Ereignisse <xref:System.Data.DataTable.RowChanging> und <xref:System.Data.DataTable.RowChanged> nur einmal auftreten, wird das Ereignis erst ausgelöst, nachdem die <xref:System.Data.DataRow.EndEdit%2A>\-Methode aufgerufen wurde.  Weitere Informationen finden Sie unter [Gewusst wie: Deaktivieren von Einschränkungen beim Auffüllen von Datasets](../data-tools/turn-off-constraints-while-filling-a-dataset.md).  
  
 Welches Ereignis Sie verwenden, richtet sich danach, mit welcher Detailgenauigkeit die Validierung erfolgen soll.  Wenn ein Fehler direkt während einer Spaltenänderung abgefangen werden muss, richten Sie die Validierung unter Verwendung des <xref:System.Data.DataTable.ColumnChanging>\-Ereignisses ein.  Andernfalls verwenden Sie das <xref:System.Data.DataTable.RowChanging>\-Ereignis, wodurch mehrere Fehler auf einmal abgefangen werden können.  Auch wenn die Daten so strukturiert sind, dass der Wert einer Spalte basierend auf dem Inhalt einer anderen Spalte validiert wird, sollten Sie die Validierung mit dem <xref:System.Data.DataTable.RowChanging>\-Ereignis durchführen.  
  
 Bei der Aktualisierung von Datensätzen löst das <xref:System.Data.DataTable>\-Objekt Ereignisse aus, auf die Sie reagieren können, während die Änderungen vorgenommen werden und nachdem sie abgeschlossen sind.  
  
 Wenn Ihre Anwendung ein typisiertes Dataset verwendet, können Sie stark typisierte Ereignishandler erstellen.  Dadurch werden vier zusätzliche typisierte Ereignisse hinzugefügt, für die Sie Handler erstellen können: `dataTableNameRowChanging`, `dataTableNameRowChanged`, `dataTableNameRowDeleting` und `dataTableNameRowDeleted`.  Durch diese typisierten Ereignishandler wird ein Argument übergeben, das die Spaltennamen der Tabelle enthält. Dadurch wird die Lesbarkeit und das Schreiben von Code vereinfacht.  
  
## Datenaktualisierungsereignisse  
  
|Ereignis|Description|  
|--------------|-----------------|  
|<xref:System.Data.DataTable.ColumnChanging>|Der Wert in einer Spalte wird gerade geändert.  Das Ereignis übergibt Zeile und Spalte zusammen mit dem vorgeschlagenen neuen Wert.|  
|<xref:System.Data.DataTable.ColumnChanged>|Der Wert in einer Spalte wurde geändert.  Das Ereignis übergibt Zeile und Spalte zusammen mit dem vorgeschlagenen Wert.|  
|<xref:System.Data.DataTable.RowChanging>|An einem <xref:System.Data.DataRow>\-Objekt vorgenommene Änderungen stehen kurz davor, mit einem Commit wieder in das Dataset geschrieben zu werden.  Wenn Sie die <xref:System.Data.DataRow.BeginEdit%2A>\-Methode nicht aufgerufen haben, wird das <xref:System.Data.DataTable.RowChanging>\-Ereignis direkt nach Auslösen des <xref:System.Data.DataTable.ColumnChanging>\-Ereignisses für jede Spaltenänderung aufgerufen.  Wenn Sie <xref:System.Data.DataRow.BeginEdit%2A> vor der Durchführung von Änderungen aufgerufen haben, wird das <xref:System.Data.DataTable.RowChanging>\-Ereignis nur beim Aufrufen der <xref:System.Data.DataRow.EndEdit%2A>\-Methode ausgelöst.<br /><br /> Durch das Ereignis wird die Zeile sowie ein Wert übergeben, der die jeweils ausgeführte Aktion \(Änderung, Einfügung usw.\) angibt.|  
|<xref:System.Data.DataTable.RowChanged>|Eine Zeile wurde geändert.  Durch das Ereignis wird die Zeile sowie ein Wert übergeben, der die jeweils ausgeführte Aktion \(Änderung, Einfügung usw.\) angibt.|  
|<xref:System.Data.DataTable.RowDeleting>|Eine Zeile wird gerade gelöscht.  Durch das Ereignis wird die Zeile sowie ein Wert übergeben, der die jeweils ausgeführte Aktion \(Löschen\) angibt.|  
|<xref:System.Data.DataTable.RowDeleted>|Eine Zeile wurde gelöscht.  Durch das Ereignis wird die Zeile sowie ein Wert übergeben, der die jeweils ausgeführte Aktion \(Löschen\) angibt.|  
  
 Die Ereignisse <xref:System.Data.DataTable.ColumnChanging>, <xref:System.Data.DataTable.RowChanging> und <xref:System.Data.DataTable.RowDeleting> werden während des Aktualisierungsprozesses ausgelöst.  Sie können diese Ereignisse verwenden, um Daten zu überprüfen oder anderweitig zu verarbeiten.  Da die Aktualisierung während dieser Ereignisse bereits läuft, können Sie sie abbrechen, indem Sie eine Ausnahme auslösen. Der Änderungsvorgang wird in diesem Fall nicht abgeschlossen.  
  
 Die Ereignisse <xref:System.Data.DataTable.ColumnChanged>, <xref:System.Data.DataTable.RowChanged> und <xref:System.Data.DataTable.RowDeleted> dienen zur Benachrichtigung und werden ausgelöst, nachdem die Aktualisierung erfolgreich abgeschlossen wurde.  Diese Ereignisse sind von Nutzen, wenn auf der Grundlage einer erfolgreichen Aktualisierung weitere Aktionen ausgeführt werden sollen.  
  
## Siehe auch  
 [Erstellen und Bearbeiten von typisierten Datasets](../data-tools/creating-and-editing-typed-datasets.md)   
 [Gewusst wie: Herstellen einer Verbindung zu Daten in einer Datenbank](../data-tools/how-to-connect-to-data-in-a-database.md)   
 [Gewusst wie: Überprüfen von Daten im DataGridView\-Steuerelement in Windows Forms](../Topic/How%20to:%20Validate%20Data%20in%20the%20Windows%20Forms%20DataGridView%20Control.md)   
 [Gewusst wie: Anzeigen von Fehlersymbolen für die Formularvalidierung mit der ErrorProvider\-Komponente in Windows Forms](../Topic/How%20to:%20Display%20Error%20Icons%20for%20Form%20Validation%20with%20the%20Windows%20Forms%20ErrorProvider%20Component.md)