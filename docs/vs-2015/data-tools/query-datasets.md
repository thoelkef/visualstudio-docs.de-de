---
title: Abfragen von Datasets | Microsoft-Dokumentation
ms.prod: visual-studio-dev14
ms.technology: vs-data-tools
ms.date: 11/15/2016
ms.topic: conceptual
ms.assetid: 7b1a91cf-8b5a-4fc0-ac36-0dc2d336fa1b
caps.latest.revision: 11
author: jillre
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: 7ccd5deffb0127769e2cd9dff3bf2accf75617eb
ms.sourcegitcommit: a8e8f4bd5d508da34bbe9f2d4d9fa94da0539de0
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 10/19/2019
ms.locfileid: "72607440"
---
# <a name="query-datasets"></a>Abfragedatasets
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Um bestimmte Datensätze in einem DataSet zu suchen, verwenden Sie die FindBy-Methode für die Datentabelle, schreiben Sie Ihre eigene foreach-Schleife über die Zeilen Auflistung der Tabelle, oder verwenden Sie [LINQ to DataSet](https://msdn.microsoft.com/library/743e3755-3ecb-45a2-8d9b-9ed41f0dcf17). LINQ to DataSet.

## <a name="dataset-case-sensitivity"></a>Berücksichtigung der Groß-/Kleinschreibung
 In einem DataSet wird die Groß-/Kleinschreibung von Tabellen-und Spaltennamen standardmäßig nicht beachtet – d. h., eine Tabelle in einem DataSet mit dem Namen "Customers" kann auch als "Customers" bezeichnet werden. Dies entspricht den Benennungs Konventionen in vielen Datenbanken, einschließlich SQL Server.in SQL Server, das Standardverhalten besteht darin, dass die Namen von Datenelementen nicht nur nach Groß-/Kleinschreibung unterschieden werden können.

> [!NOTE]
> Anders als bei Datasets wird bei XML-Dokumenten die Groß-/Kleinschreibung beachtet, sodass bei den in Schemas definierten Namen von Datenelementen die Groß-/Kleinschreibung Beispielsweise ermöglicht das Schema Protokoll dem Schema, eine Tabelle mit dem Namen "Customers" und eine andere Tabelle mit dem Namen "Customers" zu definieren. Dies kann zu Namenskonflikten führen, wenn ein Schema, das Elemente enthält, die sich nur nach Groß-/Kleinschreibung unterscheiden, zum Generieren einer DataSet-Klasse verwendet

 Die Berücksichtigung der Groß-/Kleinschreibung kann jedoch ein Faktor für die Interpretation von Daten innerhalb des Datasets sein. Wenn Sie z. b. Daten in einer DataSet-Tabelle filtern, geben die Suchkriterien möglicherweise andere Ergebnisse zurück, je nachdem, ob beim Vergleich die Groß-/Kleinschreibung beachtet wird. Sie können die Unterscheidung nach Groß-/Kleinschreibung beim Filtern, suchen und Sortieren steuern, indem Sie die <xref:System.Data.DataSet.CaseSensitive%2A>-Eigenschaft des Datasets festlegen. Alle Tabellen im Dataset erben standardmäßig den Wert dieser Eigenschaft. (Sie können diese Eigenschaft für jede einzelne Tabelle überschreiben, indem Sie die <xref:System.Data.DataTable.CaseSensitive%2A>-Eigenschaft der Tabelle festlegen.)

## <a name="locate-a-specific-row-in-a-data-table"></a>Suchen einer bestimmten Zeile in einer Datentabelle

#### <a name="to-find-a-row-in-a-typed-dataset-with-a-primary-key-value"></a>So suchen Sie eine Zeile in einem typisierten DataSet mit einem Primärschlüssel Wert

- Um eine Zeile zu suchen, müssen Sie die stark typisierte `FindBy` Methode, die den Primärschlüssel der Tabelle verwendet, abrufen.

     Im folgenden Beispiel ist die `CustomerID` Spalte der Primärschlüssel der `Customers` Tabelle. Dies bedeutet, dass die generierte `FindBy` Methode `FindByCustomerID` ist. Das Beispiel zeigt, wie einer Variablen mithilfe der generierten `FindBy` Methode eine bestimmte <xref:System.Data.DataRow> zugewiesen wird.

     [!code-csharp[VbRaddataEditing#18](../snippets/csharp/VS_Snippets_VBCSharp/VbRaddataEditing/CS/Form1.cs#18)]
     [!code-vb[VbRaddataEditing#18](../snippets/visualbasic/VS_Snippets_VBCSharp/VbRaddataEditing/VB/Form1.vb#18)]

#### <a name="to-find-a-row-in-an-untyped-dataset-with-a-primary-key-value"></a>So suchen Sie eine Zeile in einem nicht typisierten DataSet mit einem Primärschlüssel Wert

- Aufrufen der <xref:System.Data.DataRowCollection.Find%2A>-Methode einer <xref:System.Data.DataRowCollection> Auflistung, wobei der Primärschlüssel als Parameter übergeben wird.

     Im folgenden Beispiel wird gezeigt, wie Sie eine neue Zeile mit dem Namen `foundRow` deklarieren und ihr den Rückgabewert der <xref:System.Data.DataRowCollection.Find%2A>-Methode zuweisen. Wenn der Primärschlüssel gefunden wird, wird der Inhalt von Spalten Index 1 in einem Meldungs Feld angezeigt.

     [!code-csharp[VbRaddataEditing#19](../snippets/csharp/VS_Snippets_VBCSharp/VbRaddataEditing/CS/Form1.cs#19)]
     [!code-vb[VbRaddataEditing#19](../snippets/visualbasic/VS_Snippets_VBCSharp/VbRaddataEditing/VB/Form1.vb#19)]

## <a name="findrows-by-column-values"></a>FindRows nach Spaltenwerten

#### <a name="to-find-rows-based-on-the-values-in-any-column"></a>So suchen Sie Zeilen basierend auf den Werten in einer Spalte

- Datentabellen werden mit der <xref:System.Data.DataTable.Select%2A>-Methode erstellt, die ein Array von <xref:System.Data.DataRow>s basierend auf dem an die <xref:System.Data.DataTable.Select%2A>-Methode weiter gegebenen Ausdruck zurückgibt. Weitere Informationen zum Erstellen gültiger Ausdrücke finden Sie im Abschnitt "Ausdrucks Syntax" der Seite zur <xref:System.Data.DataColumn.Expression%2A>-Eigenschaft.

     Im folgenden Beispiel wird gezeigt, wie die <xref:System.Data.DataTable.Select%2A>-Methode des <xref:System.Data.DataTable> verwendet wird, um bestimmte Zeilen zu suchen.

     [!code-csharp[VbRaddataEditing#20](../snippets/csharp/VS_Snippets_VBCSharp/VbRaddataEditing/CS/Form1.cs#20)]
     [!code-vb[VbRaddataEditing#20](../snippets/visualbasic/VS_Snippets_VBCSharp/VbRaddataEditing/VB/Form1.vb#20)]

## <a name="access-related-records"></a>Zugreifen auf verwandte Datensätze
 Wenn Tabellen in einem DataSet verknüpft sind, kann ein <xref:System.Data.DataRelation> Objekt die verknüpften Datensätze in einer anderen Tabelle verfügbar machen. Beispielsweise kann ein DataSet, das `Customers`-und `Orders` Tabellen enthält, verfügbar gemacht werden.

 Sie können ein <xref:System.Data.DataRelation> Objekt verwenden, um verknüpfte Datensätze zu suchen, indem Sie die <xref:System.Data.DataRow.GetChildRows%2A>-Methode eines <xref:System.Data.DataRow> in der übergeordneten Tabelle aufrufen. Diese Methode gibt ein Array mit verknüpften untergeordneten Datensätzen zurück. Oder Sie können die <xref:System.Data.DataRow.GetParentRow%2A>-Methode einer <xref:System.Data.DataRow> in der untergeordneten Tabelle aufzurufen. Diese Methode gibt ein einzelnes <xref:System.Data.DataRow> aus der übergeordneten Tabelle zurück.

 Diese Seite enthält Beispiele für die Verwendung typisierter Datasets. Weitere Informationen zum Navigieren in Beziehungen in nicht typisierten Datasets finden Sie unter [Navigieren in DataRelations](https://msdn.microsoft.com/library/e5e673f4-9b44-45ae-aaea-c504d1cc5d3e).

> [!NOTE]
> Wenn Sie in einer Windows Forms Anwendung arbeiten und die Daten Bindungsfunktionen zum Anzeigen von Daten verwenden, kann das vom Designer generierte Formular ausreichend Funktionalität für Ihre Anwendung bereitstellen. Weitere Informationen finden Sie unter [Binden von Steuerelementen an Daten in Visual Studio](../data-tools/bind-controls-to-data-in-visual-studio.md).

 Die folgenden Codebeispiele veranschaulichen, wie Sie in typisierten Datasets nach oben und unten navigieren. In den Codebeispielen werden typisierte <xref:System.Data.DataRow>s (`NorthwindDataSet.OrdersRow`) und die generierten `FindBy`*PrimaryKey* (`FindByCustomerID`)-Methoden verwendet, um eine gewünschte Zeile zu suchen und die zugehörigen Datensätze zurückzugeben. Die Beispiele werden nur dann ordnungsgemäß kompiliert und ausgeführt, wenn Folgendes vorhanden ist:

- Eine Instanz eines Datasets mit dem Namen `NorthwindDataSet` mit einer `Customers` Tabelle.

- Eine `Orders` Tabelle.

- Eine Beziehung mit dem Namen `FK_Orders_Customers`relating die beiden Tabellen, die für den Bereich Ihres Codes verfügbar sind.

Außerdem müssen beide Tabellen mit Daten aufgefüllt werden, damit alle Datensätze zurückgegeben werden können.

#### <a name="to-return-the-child-records-of-a-selected-parent-record"></a>So geben Sie die untergeordneten Datensätze eines ausgewählten übergeordneten Datensatzes zurück

- Ruft die <xref:System.Data.DataRow.GetChildRows%2A>-Methode einer bestimmten `Customers` Daten Zeile auf und gibt ein Array von Zeilen aus der `Orders`-Tabelle zurück:

     [!code-csharp[VbRaddataDatasets#6](../snippets/csharp/VS_Snippets_VBCSharp/VbRaddataDatasets/CS/Form1.cs#6)]
     [!code-vb[VbRaddataDatasets#6](../snippets/visualbasic/VS_Snippets_VBCSharp/VbRaddataDatasets/VB/Form1.vb#6)]

#### <a name="to-return-the-parent-record-of-a-selected-child-record"></a>So geben Sie den übergeordneten Datensatz eines ausgewählten untergeordneten Datensatzes zurück

- Ruft die <xref:System.Data.DataRow.GetParentRow%2A>-Methode einer bestimmten `Orders` Daten Zeile auf und gibt eine einzelne Zeile aus der `Customers`-Tabelle zurück:

     [!code-csharp[VbRaddataDatasets#7](../snippets/csharp/VS_Snippets_VBCSharp/VbRaddataDatasets/CS/Form1.cs#7)]
     [!code-vb[VbRaddataDatasets#7](../snippets/visualbasic/VS_Snippets_VBCSharp/VbRaddataDatasets/VB/Form1.vb#7)]
