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
ms.sourcegitcommit: 95f26af1da51d4c83ae78adcb7372b32364d8a2b
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 03/13/2020
ms.locfileid: "79301194"
---
# <a name="fill-datasets-by-using-tableadapters"></a>Füllen von Datasets mit TableAdapters

Eine TableAdapter-Komponente füllt ein Dataset mit Daten aus der Datenbank, basierend auf einer oder mehreren Abfragen oder gespeicherten Prozeduren, die Sie angeben. TableAdapters kann auch Adds, Updates und Löschvorgänge in der Datenbank durchführen, um Änderungen beizubehalten, die Sie am Dataset vornehmen. Sie können auch globale Befehle ausgeben, die nichts mit einer bestimmten Tabelle zu tun haben.

> [!NOTE]
> TableAdapter werden von Visual Studio-Designern generiert. Wenn Sie Datasets programmgesteuert erstellen, verwenden Sie DataAdapter, eine .NET-Klasse.

Ausführliche Informationen zu TableAdapter-Vorgängen finden Sie unter:

|Thema|Beschreibung|
|-----------|-----------------|
|[Erstellen und Konfigurieren eines TableAdapters](../data-tools/create-and-configure-tableadapters.md)|Verwenden der Designer zum Erstellen und Konfigurieren von TableAdapters|
|[Erstellen von parametrisierten TableAdapter-Abfragen](../data-tools/create-parameterized-tableadapter-queries.md)|So können Benutzer Argumente für TableAdapter-Prozeduren oder Abfragen bereitstellen|
|[Direktes Zugreifen auf die Datenbank mit einem TableAdapter](../data-tools/directly-access-the-database-with-a-tableadapter.md)|Verwenden der Dbdirect-Methoden von TableAdapters|
|[Deaktivieren von Einschränkungen beim Auffüllen von Datasets](../data-tools/turn-off-constraints-while-filling-a-dataset.md)|So arbeiten Sie bei der Aktualisierung von Daten mit Fremdschlüsseleinschränkungen|
|[Erweitern der Funktionalität eines TableAdapter](../data-tools/fill-datasets-by-using-tableadapters.md)|Hinzufügen von benutzerdefiniertem Code zu TableAdapters|
|[Laden von Daten in ein Dataset](../data-tools/read-xml-data-into-a-dataset.md)|So arbeiten Sie mit XML|

<a name="tableadapter-overview"></a>

## <a name="tableadapter-overview"></a>Übersicht über TableAdapter

TableAdapters sind vom Designer generierte Komponenten, die eine Verbindung zu einer Datenbank herstellen, Abfragen oder gespeicherte Prozeduren ausführen und ihre DataTable mit den zurückgegebenen Daten füllen. TableAdapters senden auch aktualisierte Daten aus Ihrer Anwendung zurück an die Datenbank. Sie können auf einem TableAdapter beweitet viele Abfragen ausführen, solange sie Daten zurückgeben, die dem Schema der Tabelle entsprechen, der der TableAdapter zugeordnet ist. Das folgende Diagramm zeigt, wie TableAdapters mit Datenbanken und anderen Objekten im Arbeitsspeicher interagieren:

![Datenfluss in einer Clientanwendung](../data-tools/media/clientdatadiagram.gif)

Während TableAdapters mit dem **Dataset-Designer**entworfen werden, werden die <xref:System.Data.DataSet>TableAdapter-Klassen nicht als geschachtelte Klassen von generiert. Sie befinden sich in separaten Namespaces, die für jedes Dataset spezifisch sind. Wenn Sie z. B. `NorthwindDataSet`über ein Dataset mit <xref:System.Data.DataTable>dem Namen `NorthwindDataSet` verfügen, `NorthwindDataSetTableAdapters` befinden sich die TableAdapters, die s im zugeordnet sind, im Namespace. Um programmgesteuert auf einen speziellen TableAdapter zuzugreifen, müssen Sie eine neue Instanz des TableAdapter deklarieren. Beispiel:

[!code-csharp[VbRaddataTableAdapters#7](../data-tools/codesnippet/CSharp/fill-datasets-by-using-tableadapters_1.cs)]
[!code-vb[VbRaddataTableAdapters#7](../data-tools/codesnippet/VisualBasic/fill-datasets-by-using-tableadapters_1.vb)]

## <a name="associated-datatable-schema"></a>Zugeordnetes DataTable-Schema

Wenn Sie einen TableAdapter erstellen, verwenden Sie die anfängliche Abfrage oder gespeicherte <xref:System.Data.DataTable>Prozedur, um das Schema des zugeordneten TableAdapters zu definieren. Sie führen diese anfängliche Abfrage oder gespeicherte `Fill` Prozedur aus, indem Sie die <xref:System.Data.DataTable>TableAdapter-Methode aufrufen (die die zugeordnete TabelleAdapter saust). Alle Änderungen, die an der Hauptabfrage des TableAdapters vorgenommen werden, werden im Schema der zugehörigen Datentabelle widergespiegelt. Wenn Sie z. B. eine Spalte aus der Hauptabfrage entfernen, wird die Spalte auch aus der zugehörigen Datentabelle entfernt. Wenn zusätzliche Abfragen auf dem TableAdapter SQL-Anweisungen verwenden, die Spalten zurückgeben, die nicht in der Hauptabfrage enthalten sind, versucht der Designer, die Spaltenänderungen zwischen der Hauptabfrage und den zusätzlichen Abfragen zu synchronisieren.

## <a name="tableadapter-update-commands"></a>Aktualisierungsbefehle für TableAdapter

Die Aktualisierungsfunktionalität eines TableAdapters hängt davon ab, wie viele Informationen in der Hauptabfrage im **TableAdapter-Assistenten**verfügbar sind. TableAdapters, die zum Abrufen von Werten aus mehreren `JOIN`Tabellen konfiguriert sind (mit Hilfe von a ), Skalarwerten, Ansichten oder den Ergebnissen von Aggregatfunktionen werden nicht anfänglich erstellt, wenn Aktualisierungen an die zugrunde liegende Datenbank zurückgesendet werden können. Sie können jedoch `INSERT`die `UPDATE`Befehle `DELETE` , und Befehle manuell im **Eigenschaftenfenster** konfigurieren.

## <a name="tableadapter-queries"></a>TableAdapter-Abfragen

![TableAdapter mit mehreren Abfragen](../data-tools/media/tableadapter.gif)

TableAdapters können mehrere Abfragen enthalten, um die zugehörigen Datentabellen auszufüllen. Sie können so viele Abfragen für einen TableAdapter definieren, wie für die Anwendung erforderlich sind, solange jede Abfrage Daten zurückgibt, die demselben Schema entsprechen wie die zugeordnete Datentabelle. Diese Funktion ermöglicht es einem TableAdapter, verschiedene Ergebnisse basierend auf unterschiedlichen Kriterien zu laden.

Wenn Ihre Anwendung z. B. eine Tabelle mit Kundennamen enthält, können Sie eine Abfrage erstellen, die die Tabelle mit jedem Kundennamen füllt, der mit einem bestimmten Buchstaben beginnt, und eine andere, die die Tabelle mit allen Debitoren füllt, die sich im gleichen Status befinden. Um eine `Customers` Tabelle mit Debitoren in einem `FillByState` bestimmten Zustand zu füllen, können `SELECT * FROM Customers WHERE State = @State`Sie eine Abfrage erstellen, die einen Parameter für den Statuswert wie folgt annimmt: . Sie führen die Abfrage `FillByState` aus, indem Sie die `CustomerTableAdapter.FillByState("WA")`Methode aufrufen und den Parameterwert wie folgt übergeben: .

Zusätzlich zum Hinzufügen von Abfragen, die Daten desselben Schemas wie die Datentabelle des TableAdapter zurückgeben, können Sie Abfragen hinzufügen, die skalare (einzelne) Werte zurückgeben. Beispielsweise ist eine Abfrage, die eine`SELECT Count(*) From Customers`Anzahl von `CustomersTableAdapter,` Kunden ( ) zurückgibt, für eine gültig, obwohl die zurückgegebenen Daten nicht mit dem Schema der Tabelle übereinstimmen.

## <a name="clearbeforefill-property"></a>ClearBeforeFill-Eigenschaft

Standardmäßig werden jedes Mal, wenn Sie eine Abfrage ausführen, um die Datentabelle eines TableAdapters auszufüllen, die vorhandenen Daten gelöscht, und nur die Ergebnisse der Abfrage werden in die Tabelle geladen. Legen Sie die `ClearBeforeFill` Eigenschaft `false` des TableAdapter auf , wenn Sie die Daten, die von einer Abfrage zurückgegeben werden, zu den vorhandenen Daten in einer Datentabelle hinzufügen oder zusammenführen möchten. Unabhängig davon, ob Sie die Daten löschen, müssen Sie Aktualisierungen explizit an die Datenbank zurücksenden, wenn Sie sie beibehalten möchten. Denken Sie also daran, alle Änderungen an den Daten in der Tabelle zu speichern, bevor Sie eine weitere Abfrage ausführen, die die Tabelle ausfüllt. Weitere Informationen finden Sie unter [Aktualisieren von Daten mithilfe eines TableAdapter](../data-tools/update-data-by-using-a-tableadapter.md).

## <a name="tableadapter-inheritance"></a>TableAdapter-Vererbung

TableAdapters erweitern die Funktionalität von Standarddatenadaptern, <xref:System.Data.Common.DataAdapter> indem eine konfigurierte Klasse gekapselt wird. Standardmäßig erbt der TableAdapter von <xref:System.ComponentModel.Component> der Klasse und kann <xref:System.Data.Common.DataAdapter> nicht in die Klasse umgesiebt werden. Das Umstellen eines <xref:System.Data.Common.DataAdapter> TableAdapters <xref:System.InvalidCastException> in die Klasse führt zu einem Fehler. Um die Basisklasse eines TableAdapters zu ändern, können <xref:System.ComponentModel.Component> Sie eine Klasse angeben, die von der **Basisklasse-Eigenschaft** des TableAdapters im **Dataset-Designer**abgeleitet wird.

## <a name="tableadapter-methods-and-properties"></a>TableAdapter-Methoden und -Eigenschaften

Die TableAdapter-Klasse ist kein .NET-Typ. Dies bedeutet, dass Sie es nicht in der Dokumentation oder im **Objektbrowser**nachschlagen können. Es wird zur Entwurfszeit erstellt, wenn Sie einen der oben genannten Assistenten verwenden. Der Name, der einem TableAdapter beim Erstellen zugewiesen wurde, basiert auf dem Namen der Tabelle, mit der Sie arbeiten. Wenn Sie beispielsweise einen TableAdapter basierend auf einer `Orders`Tabelle in einer `OrdersTableAdapter`Datenbank mit dem Namen erstellen, trägt der TableAdapter den Namen . Sie können den Klassennamen für den TableAdapter ändern, indem Sie die **Name**-Eigenschaft im **DataSet-Designer** verwenden.

Im Folgenden sind die häufig verwendeten Methoden und Eigenschaften von TableAdapters aufgeführt:

|Member|Beschreibung|
|------------|-----------------|
|`TableAdapter.Fill`|Füllt die zugehörige Datentabelle des TableAdapter summiert sich `SELECT` mit den Ergebnissen des Befehls TableAdapter.|
|`TableAdapter.Update`|Sendet Änderungen zurück an die Datenbank und gibt eine ganze Zahl zurück, die die Anzahl der zeilenangaben darstellt, die von der Aktualisierung betroffen sind. Weitere Informationen finden Sie unter [Aktualisieren von Daten mithilfe eines TableAdapter](../data-tools/update-data-by-using-a-tableadapter.md).|
|`TableAdapter.GetData`|Gibt eine <xref:System.Data.DataTable> neue zurück, die mit Daten gefüllt ist.|
|`TableAdapter.Insert`|Erstellt eine neue Zeile in der Datentabelle. Weitere Informationen finden Sie unter [Einfügen neuer Datensätze in eine Datenbank](../data-tools/insert-new-records-into-a-database.md).|
|`TableAdapter.ClearBeforeFill`|Bestimmt, ob eine Datentabelle geleert wird, bevor Sie eine der `Fill`-Methoden aufrufen.|

## <a name="tableadapter-update-method"></a>TableAdapter-Aktualisierungsmethode

TableAdapters verwenden zum Lesen und Schreiben in Datenbanken Datenbefehle. Verwenden Sie die anfängliche `Fill` (Haupt-)Abfrage des TableAdapters als Grundlage für das `InsertCommand`Erstellen `UpdateCommand`des `DeleteCommand` Schemas der `TableAdapter.Update` zugeordneten Datentabelle sowie der , und der Befehle, die der Methode zugeordnet sind. Beim Aufrufen der `Update` Methode eines TableAdapters werden die Anweisungen ausgeführt, die bei der ursprünglichen Konfiguration des TableAdapters erstellt wurden, und nicht eine der zusätzlichen Abfragen, die Sie mit dem **TableAdapter-Abfragekonfigurations-Assistenten**hinzugefügt haben.

Wenn Sie einen TableAdapter verwenden, führt er effektiv dieselben Vorgänge mit den Befehlen aus, die Sie normalerweise ausführen würden. Wenn Sie beispielsweise die Methode `Fill` des Adapters aufrufen, führt `SelectCommand` der Adapter den Datenbefehl in <xref:System.Data.SqlClient.SqlDataReader>seiner Eigenschaft aus und verwendet einen Datenleser (z. B. ), um das Resultset in die Datentabelle zu laden. Wenn Sie die Methode des `Update` Adapters aufrufen, wird auch `UpdateCommand` `InsertCommand`der `DeleteCommand` entsprechende Befehl (in , und Eigenschaften) für jeden geänderten Datensatz in der Datentabelle ausgeführt.

> [!NOTE]
> Wenn die Hauptabfrage genügend Informationen enthält, werden beim Generieren des TableAdapter standardmäßig die Befehle `InsertCommand`, `UpdateCommand` und `DeleteCommand` erstellt. Wenn die Hauptabfrage des TableAdaptermehr als `SELECT` eine einzelne Tabellenanweisung ist, kann der `InsertCommand`Designer `UpdateCommand`möglicherweise `DeleteCommand`nicht , und . Wenn diese Befehle nicht generiert werden, wird beim `TableAdapter.Update` Ausführen der Methode möglicherweise eine Fehlermeldung angezeigt.

## <a name="tableadapter-generatedbdirectmethods"></a>TableAdapter GenerateDbDirectMethods

Zusätzlich zu `InsertCommand` `UpdateCommand`, `DeleteCommand`und , werden TableAdapters mit Methoden erstellt, die Sie direkt für die Datenbank ausführen können. Sie können diese`TableAdapter.Insert`Methoden `TableAdapter.Update`( `TableAdapter.Delete`, und ) direkt aufrufen, um Daten in der Datenbank zu bearbeiten. Dies bedeutet, dass Sie diese einzelnen `TableAdapter.Update` Methoden aus ihrem Code aufrufen können, anstatt aufzurufen, um die Einfügungen, Aktualisierungen und Löschungen zu behandeln, die für die zugehörige Datentabelle ausstehen.

Wenn Sie diese direkten Methoden nicht erstellen möchten, legen Sie die **GenerateDbDirectMethods-Eigenschaft** des TableAdapters auf `false` (im **Eigenschaftenfenster)** fest. Zusätzliche Abfragen, die dem TableAdapter hinzugefügt werden, sind eigenständige Abfragen – sie generieren diese Methoden nicht.

## <a name="tableadapter-support-for-nullable-types"></a>TableAdapter-Unterstützung für Typen mit Nullwert

TableAdapters unterstützen nullable Typen `Nullable(Of T)` und `T?`. Weitere Informationen zu Nullable-Typen in Visual Basic finden Sie unter [Auf NULL festlegbare Werttypen](/dotnet/visual-basic/programming-guide/language-features/data-types/nullable-value-types). Weitere Informationen zu nullablen Typen in C' finden Sie unter [Verwenden von nullablen Typen](/dotnet/csharp/programming-guide/nullable-types/using-nullable-types).

<a name="tableadaptermanager-reference"></a>

## <a name="tableadaptermanager-reference"></a>TableAdapterManager-Referenz

Standardmäßig generiert eine TableAdapterManager-Klasse, wenn Sie ein Dataset erstellen, das verknüpfte Tabellen enthält. Um zu verhindern, dass die Klasse `Hierarchical Update` generiert wird, ändern Sie den Wert der Eigenschaft des Datasets in false. Wenn Sie eine Tabelle mit einer Beziehung auf die Entwurfsoberfläche eines Windows-Formulars oder einer WPF-Seite ziehen, deklariert Visual Studio eine Membervariable der Klasse. Wenn Sie die Datenbindung nicht verwenden, müssen Sie die Variable manuell deklarieren.

Die TableAdapterManager-Klasse ist kein .NET-Typ. Daher können Sie es nicht in der Dokumentation nachschlagen. Es wird zur Entwurfszeit als Teil des Dataseterstellungsprozesses erstellt.

Im Folgenden sind die häufig verwendeten `TableAdapterManager` Methoden und Eigenschaften der Klasse:

|Member|Beschreibung|
|------------|-----------------|
|`UpdateAll`-Methode|Speichert alle Daten aus allen Datentabellen.|
|`BackUpDataSetBeforeUpdate`-Eigenschaft|Bestimmt, ob eine Sicherungskopie des Datasets `TableAdapterManager.UpdateAll` erstellt werden soll, bevor die Methode ausgeführt wird. Boolean.|
|*tableName-Eigenschaft* `TableAdapter`|Stellt einen TableAdapter dar. Der generierte TableAdapterManager enthält `TableAdapter` für jeden verwalteten Inhalt eine Eigenschaft. Beispielsweise wird ein Dataset mit einer Tabelle Customers und Orders `CustomersTableAdapter` `OrdersTableAdapter` mit einem TableAdapterManager generiert, der Eigenschaften enthält und eigenschaften.|
|`UpdateOrder`-Eigenschaft|Steuert die Reihenfolge der einzelnen Befehle zum Einfügen, Aktualisieren und Löschen. Legen Sie diesen Wert auf `TableAdapterManager.UpdateOrderOption` einen der Werte in der Enumeration fest.<br /><br /> Standardmäßig ist `UpdateOrder` die auf **InsertUpdateDelete**festgelegt. Dies bedeutet, dass Einfügungen, dann Aktualisierungen und anschließende Löschungen für alle Tabellen im Dataset ausgeführt werden.|

## <a name="security"></a>Sicherheit

Wenn Sie Datenbefehle mit einer CommandType-Eigenschaft verwenden, die auf <xref:System.Data.CommandType.Text>festgelegt ist, überprüfen Sie sorgfältig die Informationen, die von einem Client gesendet werden, bevor Sie sie an die Datenbank übergeben. Böswillige Benutzer könnten versuchen, veränderte oder zusätzliche SQL-Anweisungen zu senden (einzufügen), um unautorisierten Zugriff zu erhalten oder die Datenbank zu beschädigen. Bevor Sie Benutzereingaben in eine Datenbank übertragen, überprüfen Sie immer, ob die Informationen gültig sind. Es ist eine bewährte Methode, nach Möglichkeit immer parametrisierte Abfragen oder gespeicherte Prozeduren zu verwenden.

## <a name="see-also"></a>Weitere Informationen

- [Datasettools](../data-tools/dataset-tools-in-visual-studio.md)
