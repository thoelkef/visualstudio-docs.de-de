---
title: Abfragedatasets | Microsoft-Dokumentation
ms.prod: visual-studio-dev14
ms.technology: vs-data-tools
ms.date: 11/15/2016
ms.topic: conceptual
ms.assetid: 7b1a91cf-8b5a-4fc0-ac36-0dc2d336fa1b
caps.latest.revision: 11
author: gewarren
ms.author: gewarren
manager: jillfra
ms.openlocfilehash: 69ca24f45384ef650c4a692a8ec0afc079f19bac
ms.sourcegitcommit: 47eeeeadd84c879636e9d48747b615de69384356
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 04/23/2019
ms.locfileid: "63425369"
---
# <a name="query-datasets"></a>Abfragedatasets
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Um für bestimmte Datensätze in einem Dataset zu suchen, verwenden Sie die FindBy-Methode in der DataTable-Objekt, Schreiben Sie Ihren eigenen Foreach-Schleife über der Tabelle Zeilensammlung oder verwenden Sie [LINQ to DataSet](http://msdn.microsoft.com/library/743e3755-3ecb-45a2-8d9b-9ed41f0dcf17). LINQ to DataSet.  
  
## <a name="dataset-case-sensitivity"></a>DataSet Groß-/Kleinschreibung  
 Innerhalb eines Datasets, Tabellen- und Spaltennamen sind standardmäßig Groß-/Kleinschreibung, d. h. eine Tabelle in ein Dataset namens "Customers" kann werden so genannte "Customers". Dies entspricht den Benennungskonventionen in verschiedenen Datenbanken, einschließlich SQL clientmethodenaufrufe SQL Server, das Standardverhalten, dass die Namen von Datenelementen, die nur durch Fall unterschieden werden können.  
  
> [!NOTE]
> Im Gegensatz zu Datasets sind XML-Dokumenten Groß-/Kleinschreibung beachtet, also die Namen von Datenelementen, die in Schemas definierte Groß-/Kleinschreibung beachtet. Schemaprotokoll ermöglicht beispielsweise das Schema zum Definieren einer Tabelle namens "Customers" und eine andere Tabelle, die Namen "Customers". Dies kann zu Namenskonflikten führen, wenn ein Schema, das Elemente enthält, die nur durch Fall unterscheiden verwendet wird, um eine Dataset-Klasse zu generieren.  
  
 Groß-/Kleinschreibung, kann jedoch sein, ein Faktor bei der Interpretation der Daten im Dataset. Z. B. Wenn Sie Daten in einer Datasettabelle filtern, könnte die Suchkriterien andere Ergebnisse zurückgeben abhängig davon, ob der Vergleich Groß-/Kleinschreibung beachtet. Sie können steuern, die Groß-/Kleinschreibung von Filtern, durchsuchen und Sortieren durch Festlegen des Datasets <xref:System.Data.DataSet.CaseSensitive%2A> Eigenschaft. Alle Tabellen im Dataset, den Wert dieser Eigenschaft wird standardmäßig erben. (Sie können diese Eigenschaft für jede einzelne Tabelle überschreiben, indem Sie der Tabelle festlegen <xref:System.Data.DataTable.CaseSensitive%2A> Eigenschaft.)  
  
## <a name="locate-a-specific-row-in-a-data-table"></a>Suchen einer bestimmten Zeile in einer Datentabelle  
  
#### <a name="to-find-a-row-in-a-typed-dataset-with-a-primary-key-value"></a>Suchen Sie nach einer Zeile in einem typisierten Dataset mit einem Wert des Primärschlüssels  
  
- Um eine Zeile zu finden, rufen Sie den stark typisierten `FindBy` Methode, die Primärschlüssel der Tabelle verwendet.  
  
     Im folgenden Beispiel die `CustomerID` Spalte ist der Primärschlüssel von der `Customers` Tabelle. Dies bedeutet, dass die generierte `FindBy` Methode `FindByCustomerID`. Das Beispiel zeigt das Zuweisen von eines bestimmtes <xref:System.Data.DataRow> einer Variablen mithilfe der generierten `FindBy` Methode.  
  
     [!code-csharp[VbRaddataEditing#18](../snippets/csharp/VS_Snippets_VBCSharp/VbRaddataEditing/CS/Form1.cs#18)]
     [!code-vb[VbRaddataEditing#18](../snippets/visualbasic/VS_Snippets_VBCSharp/VbRaddataEditing/VB/Form1.vb#18)]  
  
#### <a name="to-find-a-row-in-an-untyped-dataset-with-a-primary-key-value"></a>Suchen Sie nach einer Zeile in einer nicht typisierten Dataset mit einem Wert des Primärschlüssels  
  
- Rufen Sie die <xref:System.Data.DataRowCollection.Find%2A> Methode eine <xref:System.Data.DataRowCollection> Auflistung, die den primären Schlüssel als Parameter übergeben.  
  
     Das folgende Beispiel zeigt, wie Sie eine neue Zeile deklarieren `foundRow` und weisen sie den Rückgabewert der <xref:System.Data.DataRowCollection.Find%2A> Methode. Wenn der primäre Schlüssel gefunden wird, wird der Inhalt des Spaltenindex 1 in einem Meldungsfeld angezeigt.  
  
     [!code-csharp[VbRaddataEditing#19](../snippets/csharp/VS_Snippets_VBCSharp/VbRaddataEditing/CS/Form1.cs#19)]
     [!code-vb[VbRaddataEditing#19](../snippets/visualbasic/VS_Snippets_VBCSharp/VbRaddataEditing/VB/Form1.vb#19)]  
  
## <a name="findrows-by-column-values"></a>FindRows von Spaltenwerten  
  
#### <a name="to-find-rows-based-on-the-values-in-any-column"></a>Zum Suchen von Zeilen, die basierend auf den Werten in einer beliebigen Spalte  
  
- Datentabellen werden erstellt, mit der<xref:System.Data.DataTable.Select%2A> Methode, die ein Array von zurückgibt <xref:System.Data.DataRow>s, basierend auf dem Ausdruck, die an die <xref:System.Data.DataTable.Select%2A> Methode. Weitere Informationen zu gültige Ausdrücken erstellen, finden Sie im Abschnitt "Ausdruckssyntax" der Seite über die <xref:System.Data.DataColumn.Expression%2A> Eigenschaft.  
  
     Das folgende Beispiel zeigt, wie Sie mit der <xref:System.Data.DataTable.Select%2A> Methode der <xref:System.Data.DataTable> nach bestimmten Zeilen gesucht.  
  
     [!code-csharp[VbRaddataEditing#20](../snippets/csharp/VS_Snippets_VBCSharp/VbRaddataEditing/CS/Form1.cs#20)]
     [!code-vb[VbRaddataEditing#20](../snippets/visualbasic/VS_Snippets_VBCSharp/VbRaddataEditing/VB/Form1.vb#20)]  
  
## <a name="access-related-records"></a>Zugreifen auf Verwandte Einträge  
 Wenn Tabellen in einem Dataset verknüpft sind, eine <xref:System.Data.DataRelation> Objekt kann verfügbar machen, die verknüpften Datensätze in einer anderen Tabelle. Beispielsweise ein Dataset mit `Customers` und `Orders` Tabellen verfügbar gemacht werden.  
  
 Können Sie eine <xref:System.Data.DataRelation> verknüpfte Datensätze durch den Aufruf zu suchende Objekt die <xref:System.Data.DataRow.GetChildRows%2A> Methode eine <xref:System.Data.DataRow> in der übergeordneten Tabelle. Diese Methode gibt ein Array von zugehörigen, untergeordneten Datensätzen zurück. Oder Sie rufen die <xref:System.Data.DataRow.GetParentRow%2A> Methode eine <xref:System.Data.DataRow> in der untergeordneten Tabelle. Diese Methode gibt ein einzelnes <xref:System.Data.DataRow> aus der übergeordneten Tabelle.  
  
 Diese Seite enthält Beispiele zur Verwendung von typisierten "Datasets". Informationen zum Navigieren in Beziehungen in nicht typisierten Datasets finden Sie unter [Navigieren in DataRelations](http://msdn.microsoft.com/library/e5e673f4-9b44-45ae-aaea-c504d1cc5d3e).  
  
> [!NOTE]
> Wenn Sie in einer Windows Forms-Anwendung arbeiten und mithilfe der Datenbindung-Funktionen zum Anzeigen von Daten, möglicherweise das Formular-Designer generierter genügend Funktionalität für Ihre Anwendung bereit. Weitere Informationen finden Sie unter [Binden von Steuerelementen an Daten in Visual Studio](../data-tools/bind-controls-to-data-in-visual-studio.md).  
  
 Die folgenden Codebeispiele veranschaulichen, hinzuzufügen und Beziehungen in typisierten Datasets zu navigieren. Die Beispiele für Code verwenden Sie den typisierten <xref:System.Data.DataRow>s (`NorthwindDataSet.OrdersRow`) und die generierten `FindBy` *PrimaryKey* (`FindByCustomerID`) Methoden zum Suchen einer gewünschten Zeile und die verknüpften Datensätze zurückzugeben. In den Beispielen fehlerfrei kompiliert und ausgeführt, wenn ist:  
  
- Eine Instanz eines Datasets mit dem Namen `NorthwindDataSet` mit einem `Customers` Tabelle.  
  
- Ein `Orders` Tabelle.  
  
- Eine Beziehung namens `FK_Orders_Customers`im Zusammenhang der beiden verfügbaren Tabellen für den Bereich des Codes  
  
Darüber hinaus müssen beide Tabellen mit Daten für alle Datensätze zurückgegeben werden gefüllt werden soll.  
  
#### <a name="to-return-the-child-records-of-a-selected-parent-record"></a>Die untergeordneten Datensätze eines ausgewählten übergeordneten Datensatzes zurückgegeben.  
  
- Aufrufen der <xref:System.Data.DataRow.GetChildRows%2A> Methode eines bestimmten `Customers` Daten Zeile aus, und geben Sie eine Matrix von Zeilen aus der `Orders` Tabelle:  
  
     [!code-csharp[VbRaddataDatasets#6](../snippets/csharp/VS_Snippets_VBCSharp/VbRaddataDatasets/CS/Form1.cs#6)]
     [!code-vb[VbRaddataDatasets#6](../snippets/visualbasic/VS_Snippets_VBCSharp/VbRaddataDatasets/VB/Form1.vb#6)]  
  
#### <a name="to-return-the-parent-record-of-a-selected-child-record"></a>Um den übergeordneten Datensatz der ausgewählten untergeordneten Datensatzes zurückzugeben.  
  
- Rufen Sie die <xref:System.Data.DataRow.GetParentRow%2A> Methode eines bestimmten `Orders` eine Datenzeile und zurückgeben, die eine einzelne Zeile aus der `Customers` Tabelle:  
  
     [!code-csharp[VbRaddataDatasets#7](../snippets/csharp/VS_Snippets_VBCSharp/VbRaddataDatasets/CS/Form1.cs#7)]
     [!code-vb[VbRaddataDatasets#7](../snippets/visualbasic/VS_Snippets_VBCSharp/VbRaddataDatasets/VB/Form1.vb#7)]
