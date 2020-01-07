---
title: Füllen von Datasets mit TableAdapters
ms.date: 11/04/2016
ms.topic: conceptual
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- datasets [Visual Basic]
- datasets [Visual Basic], loading data
- data retrieval
- retrieving data
- datasets [Visual Basic], filling
- data [Visual Studio], retrieving
- data [Visual Studio], datasets
ms.assetid: 55f3bfbe-db78-4486-add3-c62f49e6b9a0
author: ghogen
ms.author: ghogen
manager: jillfra
ms.workload:
- data-storage
ms.openlocfilehash: a79f7b781944bb93a60794e748eefb9375723384
ms.sourcegitcommit: d233ca00ad45e50cf62cca0d0b95dc69f0a87ad6
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 01/01/2020
ms.locfileid: "75586626"
---
# <a name="fill-datasets-by-using-tableadapters"></a>Füllen von Datasets mit TableAdapters

Eine TableAdapter-Komponente füllt ein DataSet mit Daten aus der Datenbank auf Grundlage einer oder mehrerer von Ihnen angegebenen Abfragen oder gespeicherten Prozeduren auf. TableAdapters können auch Hinzufügungen, Updates und Löschungen in der Datenbank durchführen, um Änderungen beizubehalten, die Sie am DataSet vornehmen. Sie können auch globale Befehle ausgeben, die nicht mit einer bestimmten Tabelle verknüpft sind.

> [!NOTE]
> TableAdapters werden von Visual Studio-Designern generiert. Wenn Sie Datasets Programm gesteuert erstellen, verwenden Sie DataAdapter, bei dem es sich um eine .NET-Klasse handelt.

Ausführliche Informationen zu TableAdapter-Vorgängen finden Sie direkt in einem der folgenden Themen:

|Topic|Beschreibung|
|-----------|-----------------|
|[Erstellen und Konfigurieren eines TableAdapters](../data-tools/create-and-configure-tableadapters.md)|Verwenden der Designer zum Erstellen und Konfigurieren von TableAdapters|
|[Erstellen von parametrisierten TableAdapter-Abfragen](../data-tools/create-parameterized-tableadapter-queries.md)|So ermöglichen Sie Benutzern das Bereitstellen von Argumenten für TableAdapter-Prozeduren oder-Abfragen|
|[Direktes Zugreifen auf die Datenbank mit einem TableAdapter](../data-tools/directly-access-the-database-with-a-tableadapter.md)|Verwenden der DBDirect-Methoden von TableAdapters|
|[Deaktivieren von Einschränkungen beim Auffüllen von Datasets](../data-tools/turn-off-constraints-while-filling-a-dataset.md)|Arbeiten mit Foreign Key-Einschränkungen beim Aktualisieren von Daten|
|[Erweitern der Funktionalität eines TableAdapter](../data-tools/fill-datasets-by-using-tableadapters.md)|Hinzufügen von benutzerdefiniertem Code zu TableAdapters|
|[Laden von Daten in ein Dataset](../data-tools/read-xml-data-into-a-dataset.md)|Arbeiten mit XML|

<a name="tableadapter-overview"></a>

## <a name="tableadapter-overview"></a>Übersicht über TableAdapter

TableAdapters sind vom Designer generierte Komponenten, die eine Verbindung mit einer Datenbank herstellen, Abfragen oder gespeicherte Prozeduren ausführen und Ihre Datentabelle mit den zurückgegebenen Daten ausfüllen. TableAdapters senden auch aktualisierte Daten aus Ihrer Anwendung zurück an die Datenbank. Sie können beliebig viele Abfragen auf einem TableAdapter ausführen, solange Daten zurückgegeben werden, die dem Schema der Tabelle entsprechen, der der TableAdapter zugeordnet ist. Das folgende Diagramm zeigt, wie TableAdapters mit Datenbanken und anderen Objekten im Arbeitsspeicher interagieren:

![Datenfluss in einer Clientanwendung](../data-tools/media/clientdatadiagram.gif)

Obwohl TableAdapters mit dem **DataSet-Designer**entworfen wurden, werden die TableAdapter-Klassen nicht als geschsted Klassen von <xref:System.Data.DataSet>generiert. Sie befinden sich in separaten Namespaces, die für jedes Dataset spezifisch sind. Wenn Sie z. b. ein DataSet mit dem Namen `NorthwindDataSet`haben, befinden sich die TableAdapters, die <xref:System.Data.DataTable>s in der `NorthwindDataSet` zugeordnet sind, im `NorthwindDataSetTableAdapters`-Namespace. Um programmgesteuert auf einen speziellen TableAdapter zuzugreifen, müssen Sie eine neue Instanz des TableAdapter deklarieren. Beispiel:

[!code-csharp[VbRaddataTableAdapters#7](../data-tools/codesnippet/CSharp/fill-datasets-by-using-tableadapters_1.cs)]
[!code-vb[VbRaddataTableAdapters#7](../data-tools/codesnippet/VisualBasic/fill-datasets-by-using-tableadapters_1.vb)]

## <a name="associated-datatable-schema"></a>Zugeordnetes DataTable-Schema

Wenn Sie einen TableAdapter erstellen, definieren Sie mit der ersten Abfrage oder gespeicherten Prozedur das Schema der dem TableAdapter zugeordneten <xref:System.Data.DataTable>. Sie führen diese anfängliche Abfrage oder gespeicherte Prozedur aus, indem Sie die `Fill`-Methode des TableAdapter aufrufen (die die zugeordneten <xref:System.Data.DataTable>des TableAdapters füllt). Alle Änderungen, die an der Haupt Abfrage des TableAdapters vorgenommen werden, werden im Schema der zugeordneten Datentabelle widergespiegelt. Wenn Sie z. b. eine Spalte aus der Haupt Abfrage entfernen, wird auch die Spalte aus der zugeordneten Datentabelle entfernt. Wenn zusätzliche Abfragen für den TableAdapter SQL-Anweisungen verwenden, die Spalten zurückgeben, die nicht in der Haupt Abfrage vorhanden sind, versucht der Designer, die Spalten Änderungen zwischen der Haupt Abfrage und den zusätzlichen Abfragen zu synchronisieren.

## <a name="tableadapter-update-commands"></a>Aktualisierungsbefehle für TableAdapter

Die Aktualisierungs Funktionalität eines TableAdapters hängt davon ab, wie viele Informationen in der Haupt Abfrage des **TableAdapter-Assistenten**verfügbar sind. Beispielsweise werden TableAdapters, die so konfiguriert sind, dass Sie Werte aus mehreren Tabellen abrufen (mit einer `JOIN`), skalare Werte, Sichten oder die Ergebnisse von Aggregatfunktionen, nicht anfänglich mit der Möglichkeit erstellt, Aktualisierungen an die zugrunde liegende Datenbank zurückzusenden. Sie können jedoch die Befehle `INSERT`, `UPDATE`und `DELETE` manuell im **Eigenschaften** Fenster konfigurieren.

## <a name="tableadapter-queries"></a>TableAdapter-Abfragen

![TableAdapter mit mehreren Abfragen](../data-tools/media/tableadapter.gif)

TableAdapters können mehrere Abfragen enthalten, um die zugehörigen Datentabellen auszufüllen. Sie können so viele Abfragen für einen TableAdapter definieren, wie für die Anwendung erforderlich sind, solange jede Abfrage Daten zurückgibt, die demselben Schema entsprechen wie die zugeordnete Datentabelle. Diese Funktion ermöglicht es einem TableAdapter, basierend auf unterschiedlichen Kriterien unterschiedliche Ergebnisse zu laden.

Wenn Ihre Anwendung z. b. eine Tabelle mit Kundennamen enthält, können Sie eine Abfrage erstellen, die die Tabelle mit jedem Kundennamen füllt, der mit einem bestimmten Buchstaben beginnt, und einen anderen, der die Tabelle mit allen Kunden füllt, die sich im selben Zustand befinden. Um eine `Customers` Tabelle mit Kunden in einem bestimmten Zustand zu füllen, können Sie eine `FillByState` Abfrage erstellen, die einen Parameter für den Zustandswert wie folgt annimmt: `SELECT * FROM Customers WHERE State = @State`. Sie führen die Abfrage aus, indem Sie die `FillByState`-Methode aufrufen und den Parameterwert wie folgt übergeben: `CustomerTableAdapter.FillByState("WA")`.

Zusätzlich zum Hinzufügen von Abfragen, die Daten desselben Schemas zurückgeben wie die Datentabelle des TableAdapter, können Sie Abfragen hinzufügen, die skalare (einzelne) Werte zurückgeben. Eine Abfrage, die beispielsweise die Anzahl der Kunden (`SELECT Count(*) From Customers`) zurückgibt, ist für einen `CustomersTableAdapter,` gültig, obwohl die zurückgegebenen Daten nicht dem Schema der Tabelle entsprechen.

## <a name="clearbeforefill-property"></a>ClearBeforeFill-Eigenschaft

Jedes Mal, wenn Sie eine Abfrage ausführen, um die Datentabelle eines TableAdapters auszufüllen, werden die vorhandenen Datenstandard mäßig gelöscht, und nur die Ergebnisse der Abfrage werden in die Tabelle geladen. Legen Sie die `ClearBeforeFill`-Eigenschaft des TableAdapter auf `false` fest, wenn Sie die von einer Abfrage zurückgegebenen Daten an die vorhandenen Daten in einer Datentabelle hinzufügen oder zusammenführen möchten. Unabhängig davon, ob Sie die Daten löschen, müssen Sie Aktualisierungen explizit an die Datenbank zurücksenden, wenn Sie Sie beibehalten möchten. Denken Sie daran, Änderungen an den Daten in der Tabelle zu speichern, bevor Sie eine andere Abfrage ausführen, die die Tabelle füllt. Weitere Informationen finden Sie unter [Aktualisieren von Daten mit einem TableAdapter](../data-tools/update-data-by-using-a-tableadapter.md).

## <a name="tableadapter-inheritance"></a>TableAdapter-Vererbung

TableAdapters erweitern die Funktionalität von Standarddaten Adaptern, indem eine konfigurierte <xref:System.Data.Common.DataAdapter>-Klasse gekapselt wird. Standardmäßig erbt der TableAdapter von der <xref:System.ComponentModel.Component>-Klasse und kann nicht in die <xref:System.Data.Common.DataAdapter>-Klasse umgewandelt werden. Das Umwandeln eines TableAdapter in die <xref:System.Data.Common.DataAdapter> Klasse führt zu einem <xref:System.InvalidCastException> Fehler. Um die Basisklasse eines TableAdapter zu ändern, können Sie eine Klasse angeben, die von <xref:System.ComponentModel.Component> in der **Basisklassen** Eigenschaft des TableAdapter im **DataSet-Designer**abgeleitet ist.

## <a name="tableadapter-methods-and-properties"></a>TableAdapter-Methoden und -Eigenschaften

Die TableAdapter-Klasse ist kein .NET-Typ. Dies bedeutet, dass Sie Sie nicht in der Dokumentation oder der **Objektkatalog**nachschlagen können. Sie wird zur Entwurfszeit erstellt, wenn Sie einen der zuvor erwähnten Assistenten verwenden. Der Name, der einem TableAdapter bei der Erstellung zugewiesen wird, basiert auf dem Namen der Tabelle, mit der Sie arbeiten. Wenn Sie z. b. auf der Grundlage einer Tabelle in einer Datenbank mit dem Namen `Orders`einen TableAdapter erstellen, wird der TableAdapter `OrdersTableAdapter`benannt. Sie können den Klassennamen für den TableAdapter ändern, indem Sie die **Name**-Eigenschaft im **DataSet-Designer** verwenden.

Im folgenden finden Sie die häufig verwendeten Methoden und Eigenschaften von TableAdapters:

|Member|Beschreibung|
|------------|-----------------|
|`TableAdapter.Fill`|Füllt die zugeordnete Datentabelle des TableAdapter mit den Ergebnissen des `SELECT` Befehls des TableAdapter auf.|
|`TableAdapter.Update`|Sendet Änderungen an die Datenbank zurück und gibt eine ganze Zahl zurück, die die Anzahl der von der Aktualisierung betroffenen Zeilen darstellt. Weitere Informationen finden Sie unter [Aktualisieren von Daten mit einem TableAdapter](../data-tools/update-data-by-using-a-tableadapter.md).|
|`TableAdapter.GetData`|Gibt eine neue <xref:System.Data.DataTable> zurück, die mit Daten gefüllt ist.|
|`TableAdapter.Insert`|Erstellt eine neue Zeile in der Datentabelle. Weitere Informationen finden Sie unter [Einfügen neuer Datensätze in eine Datenbank](../data-tools/insert-new-records-into-a-database.md).|
|`TableAdapter.ClearBeforeFill`|Bestimmt, ob eine Datentabelle geleert wird, bevor Sie eine der `Fill`-Methoden aufrufen.|

## <a name="tableadapter-update-method"></a>TableAdapter-Aktualisierungsmethode

TableAdapters verwenden zum Lesen und Schreiben in Datenbanken Datenbefehle. Verwenden Sie die erste `Fill` (Main)-Abfrage des TableAdapter als Grundlage für das Erstellen des Schemas der zugeordneten Datentabelle sowie die Befehle `InsertCommand`, `UpdateCommand`und `DeleteCommand`, die der `TableAdapter.Update`-Methode zugeordnet sind. Wenn Sie die `Update`-Methode eines TableAdapters aufrufen, werden die Anweisungen ausgeführt, die beim ursprünglichen Konfigurieren des TableAdapter erstellt wurden, und nicht eine der zusätzlichen Abfragen, die Sie mit dem **Konfigurations-Assistenten für TableAdapter-Abfragen**hinzugefügt haben.

Wenn Sie einen TableAdapter verwenden, führt er effektiv dieselben Vorgänge mit den Befehlen aus, die Sie normalerweise ausführen würden. Wenn Sie z. b. die `Fill`-Methode des Adapters aufzurufen, führt der Adapter den Daten Befehl in seiner `SelectCommand`-Eigenschaft aus und verwendet einen Daten Reader (z. b. <xref:System.Data.SqlClient.SqlDataReader>), um das Resultset in die Datentabelle zu laden. Wenn Sie die `Update`-Methode des Adapters aufzurufen, führt Sie entsprechend den entsprechenden Befehl (in den Eigenschaften `UpdateCommand`, `InsertCommand`und `DeleteCommand`) für jeden geänderten Datensatz in der Datentabelle aus.

> [!NOTE]
> Wenn die Hauptabfrage genügend Informationen enthält, werden beim Generieren des TableAdapter standardmäßig die Befehle `InsertCommand`, `UpdateCommand` und `DeleteCommand` erstellt. If the TableAdapter's main query is more than a single table `SELECT` statement, it's possible the designer won't be able to generate `InsertCommand`, `UpdateCommand`, and `DeleteCommand`. If these commands aren't generated, you might receive an error when running the `TableAdapter.Update` method.

## <a name="tableadapter-generatedbdirectmethods"></a>TableAdapter GenerateDbDirectMethods

In addition to `InsertCommand`, `UpdateCommand`, and `DeleteCommand`, TableAdapters are created with methods that you can run directly against the database. You can call these methods (`TableAdapter.Insert`, `TableAdapter.Update`, and `TableAdapter.Delete`) directly to manipulate data in the database. This means you can call these individual methods from your code instead of calling `TableAdapter.Update` to handle the inserts, updates, and deletes that are pending for the associated data table.

If you don't want to create these direct methods, set the TableAdapter's **GenerateDbDirectMethods** property to `false` (in the **Properties** window). Additional queries that are added to the TableAdapter are standalone queries — they don't generate these methods.

## <a name="tableadapter-support-for-nullable-types"></a>TableAdapter-Unterstützung für Typen mit Nullwert

TableAdapters support nullable types `Nullable(Of T)` and `T?`. Weitere Informationen zu Nullable-Typen in Visual Basic finden Sie unter [Auf NULL festlegbare Werttypen](/dotnet/visual-basic/programming-guide/language-features/data-types/nullable-value-types). For more information about nullable types in C#, see [Use nullable types](/dotnet/csharp/programming-guide/nullable-types/using-nullable-types).

<a name="tableadaptermanager-reference"></a>

## <a name="tableadaptermanager-reference"></a>TableAdapterManager reference

By default, a TableAdapterManager class generates when you create a dataset that contains related tables. To prevent the class from being generated, change the value of the `Hierarchical Update` property of the dataset to false. When you drag a table that has a relation onto the design surface of a Windows Form or WPF page, Visual Studio declares a member variable of the class. If you don't use databinding, you have to manually declare the variable.

The TableAdapterManager class is not a .NET type. Therefore, you cannot look it up in the documentation. It's created at design time as part of the dataset creation process.

The following are the frequently used methods and properties of the `TableAdapterManager` class:

|Member|Beschreibung|
|------------|-----------------|
|`UpdateAll`-Methode|Saves all data from all data tables.|
|`BackUpDataSetBeforeUpdate` -Eigenschaft|Determines whether to create a backup copy of the dataset before executing the `TableAdapterManager.UpdateAll` method.Boolean.|
|*tableName* `TableAdapter` property|Stellt einen TableAdapter dar. The generated TableAdapterManager contains a property for each `TableAdapter` it manages. For example, a dataset with a Customers and Orders table generates with a TableAdapterManager that contains `CustomersTableAdapter` and `OrdersTableAdapter` properties.|
|`UpdateOrder` -Eigenschaft|Controls the order of the individual insert, update, and delete commands. Set this to one of the values in the `TableAdapterManager.UpdateOrderOption` enumeration.<br /><br /> By default, the `UpdateOrder` is set to **InsertUpdateDelete**. This means that inserts, then updates, and then deletes are performed for all tables in the dataset.|

## <a name="security"></a>Sicherheit

When you use data commands with a CommandType property set to <xref:System.Data.CommandType.Text>, carefully check information that is sent from a client before passing it to your database. Böswillige Benutzer könnten versuchen, veränderte oder zusätzliche SQL-Anweisungen zu senden (einzufügen), um unautorisierten Zugriff zu erhalten oder die Datenbank zu beschädigen. Before you transfer user input to a database, always verify that the information is valid. A best practice is to always use parameterized queries or stored procedures when possible.

## <a name="see-also"></a>Siehe auch

- [Datasettools](../data-tools/dataset-tools-in-visual-studio.md)
