---
title: Füllen von Datasets mit TableAdapters | Microsoft-Dokumentation
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-data-tools
ms.topic: conceptual
dev_langs:
- VB
- CSharp
- C++
- aspx
helpviewer_keywords:
- datasets [Visual Basic]
- datasets [Visual Basic], loading data
- data retrieval
- retrieving data
- datasets [Visual Basic], filling
- data [Visual Studio], retrieving
- data [Visual Studio], datasets
ms.assetid: 55f3bfbe-db78-4486-add3-c62f49e6b9a0
caps.latest.revision: 35
author: gewarren
ms.author: gewarren
manager: jillfra
ms.openlocfilehash: 242596220b12756b6b5243b008b52db207c22cb0
ms.sourcegitcommit: 8b538eea125241e9d6d8b7297b72a66faa9a4a47
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 01/23/2019
ms.locfileid: "58960382"
---
# <a name="fill-datasets-by-using-tableadapters"></a>Füllen von Datasets mit TableAdapters
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

  
Eine Komponente des TableAdapter füllt ein Dataset mit Daten aus der Datenbank, basierend auf eine oder mehrere Abfragen oder gespeicherte Prozeduren, die Sie angeben. TableAdapter-Steuerelemente können auch ausführen, fügt, Aktualisierungen und löschungen in der Datenbank um Änderungen permanent zu speichern, die Sie auf das Dataset vornehmen. Sie können auch globale Befehle ausgeben, die nicht zu einer bestimmten Tabelle verbunden sind.  
  
> [!NOTE]
>  TableAdapters werden von Visual Studio-Designer generiert. Wenn Sie Datasets programmgesteuert erstellen, verwenden Sie DataAdapter, ist eine .NET Framework-Klasse.  
  
 Ausführliche Informationen zu Vorgängen des TableAdapter können Sie direkt auf einen der folgenden Themen überspringen:  
  
|Thema|Beschreibung|  
|-----------|-----------------|  
|[Erstellen und Konfigurieren eines TableAdapters](../data-tools/create-and-configure-tableadapters.md)|So verwenden Sie die Designer zum Erstellen und Konfigurieren eines TableAdapters|  
|[Erstellen von parametrisierten TableAdapter-Abfragen](../data-tools/create-parameterized-tableadapter-queries.md)|Benutzer geben Sie Argumente für die TableAdapter-Prozeduren oder Abfragen aktivieren|  
|[Direktes Zugreifen auf die Datenbank mit einem TableAdapter](../data-tools/directly-access-the-database-with-a-tableadapter.md)|Wie Sie mit der TableAdapter Dbdirect-Methoden|  
|[Deaktivieren von Einschränkungen beim Auffüllen von Datasets](../data-tools/turn-off-constraints-while-filling-a-dataset.md)|Arbeiten Sie mit foreign Key-Einschränkungen beim Aktualisieren von Daten|  
|[Erweitern der Funktionalität eines TableAdapter](../data-tools/fill-datasets-by-using-tableadapters.md)|Hinzufügen von benutzerdefiniertem Code zu TableAdapters|  
|[Laden von Daten in ein Dataset](../data-tools/read-xml-data-into-a-dataset.md)|Arbeiten mit XML|  
  
## <a name="tableadapters-overview"></a>Übersicht über TableAdapters  
 TableAdapter-Steuerelemente sind Designer generierte Komponenten, die eine Verbindung mit einer Datenbank, Abfragen ausführen oder gespeicherte Prozeduren, und füllen die DataTable mit den zurückgegebenen Daten. TableAdapters senden Ihnen außerdem aktualisierte Daten aus Ihrer Anwendung wieder in der Datenbank. Sie können beliebig viele Abfragen auf einem TableAdapter werden sollen, solange sie Daten, die entspricht dem Schema der Tabelle zurückgeben, die der TableAdapter zugeordnet ist, ausführen. Das folgende Diagramm zeigt die Interaktion von TableAdapters mit Datenbanken und anderen Objekten im Arbeitsspeicher:  
  
 ![Datenfluss in einer Clientanwendung](../data-tools/media/clientdatadiagram.gif "ClientDataDiagram")  
  
 Während TableAdapters mit entworfen werden die **Dataset-Designer**, die TableAdapter-Klassen werden nicht als geschachtelte Klassen von generiert <xref:System.Data.DataSet>. Sie befinden sich separaten Namespaces, die für jedes Dataset spezifisch sind. Angenommen, Sie haben ein Dataset namens `NorthwindDataSet`, die TableAdapters, die zugeordnet werden <xref:System.Data.DataTable>s in der `NorthwindDataSet` wird in der `NorthwindDataSetTableAdapters` Namespace. Um programmgesteuert auf einen speziellen TableAdapter zuzugreifen, müssen Sie eine neue Instanz des TableAdapter deklarieren. Zum Beispiel:  
  
 [!code-csharp[VbRaddataTableAdapters#7](../snippets/csharp/VS_Snippets_VBCSharp/VbRaddataTableAdapters/CS/Class1.cs#7)]
 [!code-vb[VbRaddataTableAdapters#7](../snippets/visualbasic/VS_Snippets_VBCSharp/VbRaddataTableAdapters/VB/Class1.vb#7)]  
  
## <a name="associated-datatable-schema"></a>Zugeordnetes DataTable-Schema  
 Wenn Sie einen TableAdapter erstellen, verwenden Sie die ursprüngliche Abfrage oder gespeicherte Prozedur definiert das Schema des TableAdapter zugeordnete <xref:System.Data.DataTable>. Sie führen diese anfängliche Abfrage oder gespeicherte Prozedur durch den Aufruf des TableAdapter `Fill` Methode (übernimmt den TableAdapter zugeordnete <xref:System.Data.DataTable>). Alle Änderungen, die an der Hauptabfrage des TableAdapter vorgenommen werden, werden im Schema der zugeordneten Datentabelle wiedergegeben. Beispielsweise entfernt Entfernen einer Spalte aus der Hauptabfrage auch die Spalte aus der zugeordneten Datentabelle. Wenn alle zusätzlichen Abfragen auf dem TableAdapter SQL-Anweisungen, die Spalten zurückgeben, die nicht in der Hauptabfrage enthalten sind verwenden, versucht der Designer, um die Spaltenänderungen zwischen der Hauptabfrage und die zusätzlichen Abfragen zu synchronisieren. Weitere Informationen finden Sie unter [Vorgehensweise: Bearbeiten von TableAdapters](http://msdn.microsoft.com/library/ca178745-e35a-45f1-a395-23cddfd8f855).  
  
## <a name="tableadapter-update-commands"></a>Aktualisierungsbefehle für TableAdapter  
 Die Update-Funktionalität eines TableAdapter ist abhängig von der Umfang der Informationen in der Hauptabfrage des TableAdapter-Assistenten verfügbar ist. Beispielsweise sind TableAdapters, die so konfiguriert sind, dass sie Werte aus mehreren Tabellen (JOINs), Skalarwerte, Ansichten oder die Ergebnisse von Aggregatfunktionen abrufen, bei der Erstellung anfänglich nicht in der Lage, Aktualisierungen an die zugrunde liegende Datenbank zurückzusenden. Allerdings können Sie konfigurieren die INSERT-, Update- und DELETE-Befehle manuell in die **Eigenschaften** Fenster.  
  
## <a name="tableadapter-queries"></a>TableAdapter-Abfragen  
 ![TableAdapter mit mehreren Abfragen](../data-tools/media/tableadapter.gif "TableAdapter")  
  
 TableAdapters können mehrere Abfragen, um ihre zugeordneten Datentabellen aufzufüllen enthalten. Sie können so viele Abfragen für einen TableAdapter definieren, wie für die Anwendung erforderlich sind, solange jede Abfrage Daten zurückgibt, die demselben Schema entsprechen wie die zugeordnete Datentabelle. Diese Funktion aktivieren ein TableAdapter in unterschiedliche Ergebnisse auf der Grundlage unterschiedlicher Kriterien zu laden.  
  
 Wenn Ihre Anwendung eine Tabelle mit Kundennamen enthält, können Sie z. B. eine Abfrage, die füllt die Tabelle mit den Namen jedes Kunden, die mit einem bestimmten Buchstaben beginnt und ein anderes erstellen, die in der Tabelle mit allen Kunden gefüllt, die im gleichen Zustand befinden. Zum Füllen einer `Customers` Tabelle mit Kunden in einem bestimmten Status befinden, können Sie erstellen eine `FillByState` Abfrage, die einen Parameter für den Statuswert wie folgt verwendet: `SELECT * FROM Customers WHERE State = @State`. Ausführen der Abfrage durch Aufrufen der `FillByState` -Methode und übergeben den Parameterwert folgendermaßen: `CustomerTableAdapter.FillByState("WA")`.  
  
 Zusätzlich zum Hinzufügen von Abfragen, die das gleiche Schema wie die Datentabelle des TableAdapter Daten zurückgeben, können Sie Abfragen hinzufügen, die (einzelne) Skalarwerte zurückgeben. Angenommen, eine Abfrage, die Anzahl der Kunden zurückgibt (`SELECT Count(*) From Customers`) gilt für eine `CustomersTableAdapter,` , obwohl das Schema der Tabelle die zurückgegebenen Daten entsprechen nicht.  
  
## <a name="clearbeforefill-property"></a>ClearBeforeFill-Eigenschaft  
 Standardmäßig jedes Mal, wenn Sie eine Abfrage zum Auffüllen TableAdapters-Datentabelle ausführen, werden die vorhandenen Daten gelöscht, und nur die Ergebnisse der Abfrage in die Tabelle geladen werden. Festlegen des TableAdapter `ClearBeforeFill` Eigenschaft `false` sollten Sie hinzufügen oder Zusammenführen von Daten, die an die vorhandenen Daten in einer Datentabelle aus einer Abfrage zurückgegeben werden. Unabhängig davon, ob Sie die Daten löschen müssen Sie zum Senden von Aktualisierungen explizit an die Datenbank, wenn dauerhaft gespeichert werden sollen. Denken Sie deshalb daran, Änderungen zu speichern, auf die Daten in der Tabelle vor dem Ausführen einer anderen Abfrage zum Füllen der Tabelle. Weitere Informationen finden Sie unter [Aktualisieren von Daten mit einem TableAdapter](../data-tools/update-data-by-using-a-tableadapter.md).  
  
## <a name="tableadapter-inheritance"></a>TableAdapter-Vererbung  
 TableAdapters, die die Funktionalität von Standarddatenadaptern erweitert, indem ein konfigurierter kapseln <xref:System.Data.Common.DataAdapter> Klasse? QualifyHint = False & AutoUpgrade = True. Standardmäßig erbt der TableAdapter von der <xref:System.ComponentModel.Component> Klasse und kann nicht umgewandelt werden, um die <xref:System.Data.Common.DataAdapter> Klasse. Umwandlung eines TableAdapter in die <xref:System.Data.Common.DataAdapter> Klasse führt zu einem <xref:System.InvalidCastException> Fehler? QualifyHint = False & AutoUpgrade = True. Um die Basisklasse eines TableAdapter zu ändern, können Sie eine abgeleitete Klasse eingeben <xref:System.ComponentModel.Component> in die **Basisklasse** Eigenschaft von TableAdapter in die **Dataset-Designer**.  
  
## <a name="tableadapter-methods-and-properties"></a>TableAdapter-Methoden und -Eigenschaften  
 Die TableAdapter-Klasse ist nicht Teil der [!INCLUDE[dnprdnshort](../includes/dnprdnshort-md.md)]. Dies bedeutet, Sie können nicht Nachschlagen in der Dokumentation oder der **Objektkatalog**. Er wird zur Entwurfszeit erstellt, wenn Sie einen der zuvor erwähnten Assistenten verwenden. Der Name, der einem TableAdapter zugewiesen ist, bei der Erstellung basiert auf den Namen der Tabelle, mit denen Sie arbeiten werden. Beispielsweise wird beim Erstellen eines TableAdapters basierend auf einer Tabelle in einer Datenbank mit dem Namen `Orders`, den Namen des TableAdapters `OrdersTableAdapter`. Sie können den Klassennamen für den TableAdapter ändern, indem Sie die **Name**-Eigenschaft im **DataSet-Designer** verwenden.  
  
 Es folgen die häufig verwendeten Methoden und Eigenschaften der TableAdapter-Steuerelemente:  
  
|Member|Beschreibung|  
|------------|-----------------|  
|`TableAdapter.Fill`|Füllt die dem TableAdapter zugeordnete Datentabelle mit den Ergebnissen des SELECT-Befehls für den TableAdapter auf.|  
|`TableAdapter.Update`|Sendet Änderungen an die Datenbank, und gibt eine ganze Zahl, die die Anzahl der vom Update betroffenen Zeilen darstellt. Weitere Informationen finden Sie unter [Aktualisieren von Daten mit einem TableAdapter](../data-tools/update-data-by-using-a-tableadapter.md).|  
|`TableAdapter.GetData`|Gibt eine neue <xref:System.Data.DataTable> , die mit Daten gefüllt ist.|  
|`TableAdapter.Insert`|Erstellt eine neue Zeile in der Datentabelle. Weitere Informationen finden Sie unter [Einfügen neuer Datensätze in einer Datenbank](../data-tools/insert-new-records-into-a-database.md).|  
|`TableAdapter.ClearBeforeFill`|Bestimmt, ob eine Datentabelle geleert wird, bevor Sie eine der `Fill`-Methoden aufrufen.|  
  
## <a name="tableadapter-update-method"></a>TableAdapter-Aktualisierungsmethode  
 TableAdapters verwenden zum Lesen und Schreiben in Datenbanken Datenbefehle. Der TableAdapter den anfänglichen `Fill` -(Haupt-)Abfrage dient als Grundlage zum Erstellen des Schemas der zugeordneten Datentabelle, als auch die `InsertCommand`, `UpdateCommand`, und `DeleteCommand` Befehle, die zugeordnet sind die `TableAdapter.Update` Methode. TableAdapters aufrufen `Update` Methode führt die Anweisungen, die erstellt wurden, als der TableAdapter ursprünglich konfiguriert haben, nicht eine der zusätzlichen Abfragen, die mit hinzugefügt wurde die **TableAdapter-Konfigurations-Assistenten**.  
  
 Wenn Sie einen TableAdapter verwenden, führt er effektiv dieselben Operationen mit den Befehlen aus, die Sie normalerweise ausführen würden. Z. B. beim Aufruf des Adapters `Fill` -Methode der Adapter führt den Datenbefehl in die `SelectCommand` Eigenschaft und verwendet einen Datenreader (z. B. <xref:System.Data.SqlClient.SqlDataReader>) um das Resultset in der Datentabelle zu laden. Auf ähnliche Weise werden beim Aufruf des Adapters `Update` -Methode, wird der entsprechenden Befehl ausgeführt (in der `UpdateCommand`, `InsertCommand`, und `DeleteCommand` Eigenschaften) für jeden geänderten Datensatz in der Datentabelle.  
  
> [!NOTE]
>  Wenn die Hauptabfrage genügend Informationen enthält, werden beim Generieren des TableAdapter standardmäßig die Befehle `InsertCommand`, `UpdateCommand` und `DeleteCommand` erstellt. Wenn die Hauptabfrage des TableAdapter auf mehr als eine einzelne Tabelle SELECT-Anweisung ist, kann der Designer wird nicht in der Lage, generieren `InsertCommand`, `UpdateCommand`, und `DeleteCommand`. Wenn diese Befehle nicht generiert werden, erhalten Sie möglicherweise eine Fehlermeldung beim Ausführen der `TableAdapter.Update` Methode.  
  
## <a name="tableadapter-generatedbdirectmethods"></a>TableAdapter GenerateDbDirectMethods  
 Zusätzlich zu `InsertCommand`, `UpdateCommand`, und `DeleteCommand`, TableAdapter-Erstellung mit Methoden, die direkt in der Datenbank ausgeführt werden können. Diese Methoden (`TableAdapter.Insert`, `TableAdapter.Update` und `TableAdapter.Delete`) können direkt aufgerufen werden, um Daten in der Datenbank zu bearbeiten. Dies bedeutet, Sie können eine dieser individuellen Methoden aufrufen, aus dem Code statt `TableAdapter.Update` behandelt, die einfügungen, Updates und löschungen, die ausstehend sind für die zugeordnete Datentabelle.  
  
 Wenn Sie nicht diese direkten Methoden erstellen möchten, legen Sie der TableAdapters **GenerateDbDirectMethods** Eigenschaft `false` (in der **Eigenschaften** Fenster). Zusätzliche Abfragen, die dem TableAdapter hinzugefügt werden, sind eigenständige Abfragen – sie können diese Methoden nicht generieren.  
  
## <a name="tableadapter-support-for-nullable-types"></a>TableAdapter-Unterstützung für Typen mit Nullwert  
 TableAdapters unterstützen die Typen `Nullable(Of T)` und `T?`. Weitere Informationen zu Nullable-Typen in Visual Basic finden Sie unter [Auf NULL festlegbare Werttypen](http://msdn.microsoft.com/library/9ac3b602-6f96-4e6d-96f7-cd4e81c468a6). Weitere Informationen zu nullable-Typen in C#, finden Sie unter [Using Nullable Types](http://msdn.microsoft.com/library/0bacbe72-ce15-4b14-83e1-9c14e6380c28).  
  
## <a name="security"></a>Sicherheit  
 Wenn Sie Datenbefehle mit verwenden eine `CommandType` -Eigenschaft auf festgelegt <xref:System.Data.CommandType>, sorgfältig überprüfen, die von einem Client gesendet wird, vor der Übergabe an die Datenbank. Böswillige Benutzer könnten versuchen, veränderte oder zusätzliche SQL-Anweisungen zu senden (einzufügen), um unautorisierten Zugriff zu erhalten oder die Datenbank zu beschädigen. Bevor Sie Benutzereingaben in einer Datenbank übertragen, immer überprüfen, ob die Informationen gültig sind. Es wird empfohlen ist, parametrisierte Abfragen oder gespeicherte Prozeduren, die nach Möglichkeit immer zu verwenden.  
  
## <a name="see-also"></a>Siehe auch  
 [Datasettools in Visual Studio](../data-tools/dataset-tools-in-visual-studio.md)
