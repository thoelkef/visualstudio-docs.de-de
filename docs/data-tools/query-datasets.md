---
title: Abfragen von Datasets | Microsoft Docs
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- VB
- CSharp
ms.assetid: 7b1a91cf-8b5a-4fc0-ac36-0dc2d336fa1b
caps.latest.revision: "8"
author: gewarren
ms.author: gewarren
manager: ghogen
ms.technology: vs-data-tools
ms.workload: data-storage
ms.openlocfilehash: f25507493237ba54c9d6820500706d06d4bf7710
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 12/22/2017
---
# <a name="query-datasets"></a>Abfragedatasets
Zum Suchen bestimmter Datensätze in einem Dataset verwenden Sie die FindBy-Methode in das DataTable-Objekt, Schreiben Sie eine eigene Foreach-Anweisung aus, um die Tabelle Zeilen Auflistung durchlaufen werden soll, oder verwenden Sie [LINQ to DataSet](/dotnet/framework/data/adonet/linq-to-dataset).  
  
## <a name="dataset-case-sensitivity"></a>DataSet Groß-/Kleinschreibung  
Tabellen- und Spaltennamen innerhalb eines Datasets werden standardmäßig Groß-/Kleinschreibung – d. h. eine Tabelle in einem Dataset mit dem Namen "Customers" kann auch bezeichnet werden als "Customers". Dies entspricht die Benennungskonventionen in vielen Datenbanken, einschließlich SQL Server. In SQL Server ist das Standardverhalten, dass die Namen von Datenelementen nur durch '-Fällen unterschieden werden können.  
  
> [!NOTE]
>  Im Gegensatz zu Datasets sind die XML-Dokumente Groß-/Kleinschreibung beachtet, damit die Namen von Datenelementen, die in Schemas definiert die Groß-/Kleinschreibung. Schemaprotokoll kann z. B. das Schema zum Definieren einer Tabelle namens "Customers" und eine andere Tabelle mit dem Namen "Customers". Dies kann zu Namenskonflikten führen, wenn ein Schema, das Elemente enthält, die nur durch '-Fällen unterscheiden sich zum Generieren einer Datasetklasse verwendet wird.  
  
Groß-/Kleinschreibung, kann jedoch ein Faktor bei der Interpretation der Daten innerhalb des Datasets. Z. B. Wenn Sie Daten in einer Datasettabelle filtern, möglicherweise die Suchkriterien andere Ergebnisse zurückgeben abhängig davon, ob der Vergleich Groß-/Kleinschreibung beachtet. Sie können steuern, die Groß-/Kleinschreibung von Filtern, suchen und sortieren, indem Sie des Datasets festlegen <xref:System.Data.DataSet.CaseSensitive%2A> Eigenschaft. Alle Tabellen im Dataset erben den Wert dieser Eigenschaft wird standardmäßig an. (Sie können diese Eigenschaft für jede einzelne Tabelle überschreiben, indem Sie der Tabelle <xref:System.Data.DataTable.CaseSensitive%2A> Eigenschaft.)  
  
## <a name="locate-a-specific-row-in-a-data-table"></a>Suchen einer bestimmten Zeile in einer Datentabelle  
  
#### <a name="to-find-a-row-in-a-typed-dataset-with-a-primary-key-value"></a>Suchen Sie nach einer Zeile in einem typisierten Dataset mit einem Primärschlüsselwert  
  
-   Um eine Zeile zu suchen, rufen Sie die stark typisierte `FindBy` Methode, die Primärschlüssel der Tabelle verwendet.  
  
     Im folgenden Beispiel die `CustomerID` Spalte ist der Primärschlüssel von der `Customers` Tabelle. Dies bedeutet, dass die generierte `FindBy` Methode ist `FindByCustomerID`. Im Beispiel wird gezeigt, wie das Zuweisen einen bestimmten <xref:System.Data.DataRow> einer Variablen mithilfe der generierten `FindBy` Methode.  
  
     [!code-csharp[VbRaddataEditing#18](../data-tools/codesnippet/CSharp/query-datasets_1.cs)]
     [!code-vb[VbRaddataEditing#18](../data-tools/codesnippet/VisualBasic/query-datasets_1.vb)]  
  
#### <a name="to-find-a-row-in-an-untyped-dataset-with-a-primary-key-value"></a>Eine Zeile in ein nicht typisiertes Dataset mit einem Primärschlüsselwert gesucht  
  
-   Rufen Sie die <xref:System.Data.DataRowCollection.Find%2A> Methode eine <xref:System.Data.DataRowCollection> Auflistung, die den primären Schlüssel als Parameter übergeben.  
  
     Das folgende Beispiel zeigt, wie eine neue Zeile deklariert `foundRow` und weisen sie den Rückgabewert der <xref:System.Data.DataRowCollection.Find%2A> Methode. Wenn der primäre Schlüssel gefunden wird, wird der Inhalt des Spaltenindexes 1 in einem Meldungsfeld angezeigt.  
  
     [!code-csharp[VbRaddataEditing#19](../data-tools/codesnippet/CSharp/query-datasets_2.cs)]
     [!code-vb[VbRaddataEditing#19](../data-tools/codesnippet/VisualBasic/query-datasets_2.vb)]  
  
## <a name="find-rows-by-column-values"></a>Suchen nach Zeilen von Spaltenwerten  
  
#### <a name="to-find-rows-based-on-the-values-in-any-column"></a>Zum Suchen von Zeilen basierend auf den Werten in einer beliebigen Spalte  
  
-   Datentabellen erstellt werden, mit der <xref:System.Data.DataTable.Select%2A> Methode, die ein Array von zurückgibt <xref:System.Data.DataRow>s, basierend auf den Ausdruck übergeben, um die <xref:System.Data.DataTable.Select%2A> Methode. Weitere Informationen zu gültige Ausdrücken erstellen, finden Sie im Abschnitt "Syntax" Ausdruck ", der Seite zum die <xref:System.Data.DataColumn.Expression%2A> Eigenschaft.  
  
     Das folgende Beispiel zeigt, wie Sie die <xref:System.Data.DataTable.Select%2A> Methode der <xref:System.Data.DataTable> bestimmte Zeilen zu suchen.  
  
     [!code-csharp[VbRaddataEditing#20](../data-tools/codesnippet/CSharp/query-datasets_3.cs)]
     [!code-vb[VbRaddataEditing#20](../data-tools/codesnippet/VisualBasic/query-datasets_3.vb)]  
  
## <a name="access-related-records"></a>Zugreifen auf Verwandte Einträge  
Wenn Tabellen in einem Dataset verknüpft sind, eine <xref:System.Data.DataRelation> Objekt kann verfügbar machen, die verknüpfte Datensätze in einer anderen Tabelle. Angenommen, ein Dataset mit `Customers` und `Orders` Tabellen verfügbar gemacht werden.  
  
Können Sie eine <xref:System.Data.DataRelation> verknüpfte Datensätze durch den Aufruf zu suchende Objekt die <xref:System.Data.DataRow.GetChildRows%2A> Methode von einer <xref:System.Data.DataRow> in der übergeordneten Tabelle. Diese Methode gibt ein Array von verknüpften untergeordneten Datensätzen zurück. Oder Sie rufen die <xref:System.Data.DataRow.GetParentRow%2A> Methode von einer <xref:System.Data.DataRow> in der untergeordneten Tabelle. Diese Methode gibt ein einzelnes <xref:System.Data.DataRow> aus der übergeordneten Tabelle.  
  
Diese Seite enthält Beispiele für die Verwendung von typisierten "Datasets". Informationen zum Navigieren in Beziehungen in nicht typisierte Datasets finden Sie unter [Navigieren von "DataRelations"](/dotnet/framework/data/adonet/dataset-datatable-dataview/navigating-datarelations).  
  
> [!NOTE]
>  Wenn Sie in einer Windows Forms-Anwendung arbeiten und die Verwendung der Datenbindung-Funktionen zum Anzeigen von Daten, möglicherweise den Formular-Designer generierter genügend Funktionalität für Ihre Anwendung bereit. Weitere Informationen finden Sie unter [Binden von Steuerelementen an Daten in Visual Studio](../data-tools/bind-controls-to-data-in-visual-studio.md). Insbesondere finden Sie unter [Beziehungen in Datasets](relationships-in-datasets.md).  
  
Die folgenden Codebeispiele veranschaulichen, wie zum Navigieren nach oben oder unten Beziehungen in typisierten Datasets. Der Code Beispiele verwenden Sie den typisierten <xref:System.Data.DataRow>s (`NorthwindDataSet.OrdersRow`) und die generierten FindBy*PrimaryKey* (`FindByCustomerID`) Methoden, um eine gewünschte Zeile zu finden und die verknüpften Datensätze zurückzugeben. In den Beispielen fehlerfrei kompiliert und ausgeführt nur, wenn Sie:  
  
-   Eine Instanz eines Datasets mit dem Namen `NorthwindDataSet` mit einem `Customers` Tabelle.  
  
-   Ein `Orders` Tabelle.  
  
-   Eine Beziehung mit dem Namen `FK_Orders_Customers`bezüglich der beiden Tabellen.  
  
Darüber hinaus müssen beide Tabellen mit Daten für alle Datensätze zurückgegeben werden gefüllt werden soll.  
  
#### <a name="to-return-the-child-records-of-a-selected-parent-record"></a>Die untergeordneten Datensätze eines ausgewählten übergeordneten Datensatzes zurückgegeben.  
  
-   Rufen Sie die <xref:System.Data.DataRow.GetChildRows%2A> -Methode eines bestimmten `Customers` Daten Zeile aus, und ein Array von Zeilen aus Zurückgeben der `Orders` Tabelle:  
  
     [!code-csharp[VbRaddataDatasets#6](../data-tools/codesnippet/CSharp/query-datasets_4.cs)]
     [!code-vb[VbRaddataDatasets#6](../data-tools/codesnippet/VisualBasic/query-datasets_4.vb)]  
  
#### <a name="to-return-the-parent-record-of-a-selected-child-record"></a>Um den übergeordneten Datensatz eines ausgewählten untergeordneten Datensatzes zurückzugeben.  
  
-   Rufen Sie die <xref:System.Data.DataRow.GetParentRow%2A> -Methode eines bestimmten `Orders` Datenzeile, und der Rückgabewert eine einzelne Zeile aus der `Customers` Tabelle:  
  
     [!code-csharp[VbRaddataDatasets#7](../data-tools/codesnippet/CSharp/query-datasets_5.cs)]
     [!code-vb[VbRaddataDatasets#7](../data-tools/codesnippet/VisualBasic/query-datasets_5.vb)]

## <a name="see-also"></a>Siehe auch
[Datasettools in Visual Studio](../data-tools/dataset-tools-in-visual-studio.md)  