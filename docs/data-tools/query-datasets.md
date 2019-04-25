---
title: Abfragedatasets
ms.date: 11/04/2016
ms.topic: conceptual
dev_langs:
- VB
- CSharp
ms.assetid: 7b1a91cf-8b5a-4fc0-ac36-0dc2d336fa1b
author: gewarren
ms.author: gewarren
manager: jillfra
ms.workload:
- data-storage
ms.openlocfilehash: ccd8bd0cb37aaa2d4bfad7ea20979987048bf862
ms.sourcegitcommit: 1fc6ee928733e61a1f42782f832ead9f7946d00c
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/22/2019
ms.locfileid: "60050672"
---
# <a name="query-datasets"></a>Abfragedatasets
Um für bestimmte Datensätze in einem Dataset zu suchen, verwenden die `FindBy` Methode in der DataTable-Objekt, Schreiben Sie Ihren eigenen Foreach-Anweisung, die Schleife in der-Auflistung der Tabelle Zeilen, oder verwenden Sie [LINQ to DataSet](/dotnet/framework/data/adonet/linq-to-dataset).

## <a name="dataset-case-sensitivity"></a>DataSet Groß-/Kleinschreibung
Innerhalb eines Datasets, Tabellen- und Spaltennamen sind standardmäßig Groß-/Kleinschreibung, d. h. eine Tabelle in ein Dataset namens "Customers" kann werden so genannte "Customers". Dies entspricht die Benennungskonventionen in verschiedenen Datenbanken, einschließlich SQL Server. In SQL Server ist das Standardverhalten an, dass die Namen von Datenelementen, die nur durch Fall unterschieden werden können.

> [!NOTE]
>  Im Gegensatz zu Datasets sind XML-Dokumenten Groß-/Kleinschreibung beachtet, also die Namen von Datenelementen, die in Schemas definierte Groß-/Kleinschreibung beachtet. Schemaprotokoll ermöglicht beispielsweise das Schema zum Definieren einer Tabelle namens "Customers" und eine andere Tabelle, die Namen "Customers". Dies kann zu Namenskonflikten führen, wenn ein Schema, das Elemente enthält, die nur durch Fall unterscheiden verwendet wird, um eine Dataset-Klasse zu generieren.

Groß-/Kleinschreibung, kann jedoch sein, ein Faktor bei der Interpretation der Daten im Dataset. Z. B. Wenn Sie Daten in einer Datasettabelle filtern, könnte die Suchkriterien andere Ergebnisse zurückgeben abhängig davon, ob der Vergleich Groß-/Kleinschreibung beachtet. Sie können steuern, die Groß-/Kleinschreibung von Filtern, durchsuchen und Sortieren durch Festlegen des Datasets <xref:System.Data.DataSet.CaseSensitive%2A> Eigenschaft. Alle Tabellen im Dataset, den Wert dieser Eigenschaft wird standardmäßig erben. (Sie können diese Eigenschaft für jede einzelne Tabelle überschreiben, indem Sie der Tabelle festlegen <xref:System.Data.DataTable.CaseSensitive%2A> Eigenschaft.)

## <a name="locate-a-specific-row-in-a-data-table"></a>Suchen einer bestimmten Zeile in einer Datentabelle

#### <a name="to-find-a-row-in-a-typed-dataset-with-a-primary-key-value"></a>Suchen Sie nach einer Zeile in einem typisierten Dataset mit einem Wert des Primärschlüssels

- Um eine Zeile zu finden, rufen Sie den stark typisierten `FindBy` Methode, die Primärschlüssel der Tabelle verwendet.

     Im folgenden Beispiel die `CustomerID` Spalte ist der Primärschlüssel von der `Customers` Tabelle. Dies bedeutet, dass die generierte `FindBy` Methode `FindByCustomerID`. Das Beispiel zeigt das Zuweisen von eines bestimmtes <xref:System.Data.DataRow> einer Variablen mithilfe der generierten `FindBy` Methode.

     [!code-csharp[VbRaddataEditing#18](../data-tools/codesnippet/CSharp/query-datasets_1.cs)]
     [!code-vb[VbRaddataEditing#18](../data-tools/codesnippet/VisualBasic/query-datasets_1.vb)]

#### <a name="to-find-a-row-in-an-untyped-dataset-with-a-primary-key-value"></a>Suchen Sie nach einer Zeile in einer nicht typisierten Dataset mit einem Wert des Primärschlüssels

- Rufen Sie die <xref:System.Data.DataRowCollection.Find%2A> Methode eine <xref:System.Data.DataRowCollection> Auflistung, die den primären Schlüssel als Parameter übergeben.

     Das folgende Beispiel zeigt, wie Sie eine neue Zeile deklarieren `foundRow` und weisen sie den Rückgabewert der <xref:System.Data.DataRowCollection.Find%2A> Methode. Wenn der primäre Schlüssel gefunden wird, wird der Inhalt des Spaltenindex 1 in einem Meldungsfeld angezeigt.

     [!code-csharp[VbRaddataEditing#19](../data-tools/codesnippet/CSharp/query-datasets_2.cs)]
     [!code-vb[VbRaddataEditing#19](../data-tools/codesnippet/VisualBasic/query-datasets_2.vb)]

## <a name="find-rows-by-column-values"></a>Suchen nach Zeilen nach Spaltenwerten

#### <a name="to-find-rows-based-on-the-values-in-any-column"></a>Zum Suchen von Zeilen, die basierend auf den Werten in einer beliebigen Spalte

- Datentabellen werden erstellt, mit der <xref:System.Data.DataTable.Select%2A> Methode, die ein Array von zurückgibt <xref:System.Data.DataRow>s, basierend auf dem Ausdruck, die an die <xref:System.Data.DataTable.Select%2A> Methode. Weitere Informationen zu gültige Ausdrücken erstellen, finden Sie im Abschnitt "Ausdruckssyntax" der Seite über die <xref:System.Data.DataColumn.Expression%2A> Eigenschaft.

     Das folgende Beispiel zeigt, wie Sie mit der <xref:System.Data.DataTable.Select%2A> Methode der <xref:System.Data.DataTable> nach bestimmten Zeilen gesucht.

     [!code-csharp[VbRaddataEditing#20](../data-tools/codesnippet/CSharp/query-datasets_3.cs)]
     [!code-vb[VbRaddataEditing#20](../data-tools/codesnippet/VisualBasic/query-datasets_3.vb)]

## <a name="access-related-records"></a>Zugreifen auf Verwandte Einträge
Wenn Tabellen in einem Dataset verknüpft sind, eine <xref:System.Data.DataRelation> Objekt kann verfügbar machen, die verknüpften Datensätze in einer anderen Tabelle. Beispielsweise ein Dataset mit `Customers` und `Orders` Tabellen verfügbar gemacht werden.

Können Sie eine <xref:System.Data.DataRelation> verknüpfte Datensätze durch den Aufruf zu suchende Objekt die <xref:System.Data.DataRow.GetChildRows%2A> Methode eine <xref:System.Data.DataRow> in der übergeordneten Tabelle. Diese Methode gibt ein Array von zugehörigen, untergeordneten Datensätzen zurück. Oder Sie rufen die <xref:System.Data.DataRow.GetParentRow%2A> Methode eine <xref:System.Data.DataRow> in der untergeordneten Tabelle. Diese Methode gibt ein einzelnes <xref:System.Data.DataRow> aus der übergeordneten Tabelle.

Diese Seite enthält Beispiele zur Verwendung von typisierten "Datasets". Informationen zum Navigieren in Beziehungen in nicht typisierten Datasets finden Sie unter [Navigieren in DataRelations](/dotnet/framework/data/adonet/dataset-datatable-dataview/navigating-datarelations).

> [!NOTE]
>  Wenn Sie in einer Windows Forms-Anwendung arbeiten und mithilfe der Datenbindung-Funktionen zum Anzeigen von Daten, möglicherweise das Formular-Designer generierter genügend Funktionalität für Ihre Anwendung bereit. Weitere Informationen finden Sie unter [Binden von Steuerelementen an Daten in Visual Studio](../data-tools/bind-controls-to-data-in-visual-studio.md). Insbesondere [Beziehungen in Datasets](relationships-in-datasets.md).

Die folgenden Codebeispiele veranschaulichen, hinzuzufügen und Beziehungen in typisierten Datasets zu navigieren. Die Beispiele für Code verwenden Sie den typisierten <xref:System.Data.DataRow>s (`NorthwindDataSet.OrdersRow`) und die generierten FindBy*PrimaryKey* (`FindByCustomerID`) Methoden zum Suchen einer gewünschten Zeile und die verknüpften Datensätze zurückzugeben. In den Beispielen fehlerfrei kompiliert und ausgeführt, wenn ist:

- Eine Instanz eines Datasets mit dem Namen `NorthwindDataSet` mit einem `Customers` Tabelle.

- Ein `Orders` Tabelle.

- Eine Beziehung namens `FK_Orders_Customers`bezüglich der beiden Tabellen.

Darüber hinaus müssen beide Tabellen mit Daten für alle Datensätze zurückgegeben werden gefüllt werden soll.

#### <a name="to-return-the-child-records-of-a-selected-parent-record"></a>Die untergeordneten Datensätze eines ausgewählten übergeordneten Datensatzes zurückgegeben.

- Aufrufen der <xref:System.Data.DataRow.GetChildRows%2A> Methode eines bestimmten `Customers` Daten Zeile aus, und geben Sie eine Matrix von Zeilen aus der `Orders` Tabelle:

     [!code-csharp[VbRaddataDatasets#6](../data-tools/codesnippet/CSharp/query-datasets_4.cs)]
     [!code-vb[VbRaddataDatasets#6](../data-tools/codesnippet/VisualBasic/query-datasets_4.vb)]

#### <a name="to-return-the-parent-record-of-a-selected-child-record"></a>Um den übergeordneten Datensatz der ausgewählten untergeordneten Datensatzes zurückzugeben.

- Rufen Sie die <xref:System.Data.DataRow.GetParentRow%2A> Methode eines bestimmten `Orders` eine Datenzeile und zurückgeben, die eine einzelne Zeile aus der `Customers` Tabelle:

     [!code-csharp[VbRaddataDatasets#7](../data-tools/codesnippet/CSharp/query-datasets_5.cs)]
     [!code-vb[VbRaddataDatasets#7](../data-tools/codesnippet/VisualBasic/query-datasets_5.vb)]

## <a name="see-also"></a>Siehe auch

- [Datasettools in Visual Studio](../data-tools/dataset-tools-in-visual-studio.md)