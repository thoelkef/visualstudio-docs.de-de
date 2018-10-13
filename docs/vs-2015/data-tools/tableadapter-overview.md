---
title: Übersicht über TableAdapters | Microsoft-Dokumentation
ms.custom: ''
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
f1_keywords:
- vbData.Microsoft.VSDesigner.DataSource.DataAccessor
- vbdata.Microsoft.VSDesigner.DataSource.DataAccessor
- TableAdapter
- vs.data.TableAdapter
dev_langs:
- VB
- CSharp
- C++
- aspx
helpviewer_keywords:
- data [Visual Studio], table adapters
- TableAdapters, queries
- data [Visual Studio], TableAdapters
- query data in Visual Studio
- TableAdapter.GetData
- TableAdapter.Fill
- data [Visual Studio], datasets
- TableAdapters
- table adapters
ms.assetid: a87c46a0-52ab-432a-a864-9ba55069f9eb
caps.latest.revision: 40
author: gewarren
ms.author: gewarren
manager: ghogen
robots: noindex,nofollow
ms.openlocfilehash: fb5ebcdaa1bebe67c2fb8e378c7345467dd10b78
ms.sourcegitcommit: 9ceaf69568d61023868ced59108ae4dd46f720ab
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 10/12/2018
ms.locfileid: "49269047"
---
# <a name="tableadapter-overview"></a>Übersicht über TableAdapters
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

TableAdapter-Steuerelemente sind Designer generierte Komponenten, die eine Verbindung mit einer Datenbank herstellen, Abfragen oder gespeicherte Prozeduren ausführen und die DataTable mit den zurückgegebenen Daten zu füllen. Mit TableAdapters werden außerdem aktualisierte Daten von der Anwendung an die Datenbank zurückgesendet. Sie können beliebig viele Abfragen auf einem TableAdapter werden sollen, solange sie Daten, die entspricht dem Schema der Tabelle zurückgeben, die der TableAdapter zugeordnet ist, verwenden. Das folgende Diagramm zeigt die Interaktion von TableAdapters mit Datenbanken und anderen Objekten im Arbeitsspeicher:  
  
 ![Datenfluss in einer Clientanwendung](../data-tools/media/clientdatadiagram.gif "ClientDataDiagram")  
  
 Während TableAdapters mit entworfen werden die **Dataset-Designer**, die generierten TableAdapter-Klassen werden nicht als geschachtelte Klassen von generiert die <xref:System.Data.DataSet>. Sie befinden sich in einem separaten Namespace, der für jedes Dataset spezifisch ist. Wenn Sie beispielsweise ein Dataset mit der Bezeichnung `NorthwindDataSet` besitzen, befinden sich die TableAdapters, die mit den im <xref:System.Data.DataTable> enthaltenen `NorthwindDataSet`s verknüpft sind, im `NorthwindDataSetTableAdapters`-Namespace. Um programmgesteuert auf einen speziellen TableAdapter zuzugreifen, müssen Sie eine neue Instanz des TableAdapter deklarieren. Zum Beispiel:  
  
 [!code-csharp[VbRaddataTableAdapters#7](../snippets/csharp/VS_Snippets_VBCSharp/VbRaddataTableAdapters/CS/Class1.cs#7)]
 [!code-vb[VbRaddataTableAdapters#7](../snippets/visualbasic/VS_Snippets_VBCSharp/VbRaddataTableAdapters/VB/Class1.vb#7)]  
  
## <a name="associated-datatable-schema"></a>Zugeordnetes DataTable-Schema  
 Wenn Sie einen TableAdapter erstellen, wird die ursprüngliche Abfrage oder gespeicherte Prozedur verwendet, um das Schema der <xref:System.Data.DataTable> zu definieren, die dem TableAdapter zugeordnet ist. Sie führen diese anfängliche Abfrage oder gespeicherte Prozedur durch den Aufruf des TableAdapter `Fill` Methode (übernimmt den TableAdapter zugeordnete <xref:System.Data.DataTable>). Alle Änderungen an der Hauptabfrage des TableAdapter spiegeln sich im Schema der zugeordneten Datentabelle wider. Durch das Entfernen einer Spalte aus der Hauptabfrage wird z. B. auch die Spalte aus der zugeordneten Datentabelle entfernt. Wenn in weiteren Abfragen des TableAdapter SQL-Anweisungen verwendet werden, durch die Spalten zurückgegeben werden, die nicht in der Hauptabfrage enthalten sind, versucht der Designer, die Spaltenänderungen zwischen der Hauptabfrage und etwaigen zusätzlichen Abfragen zu synchronisieren. Weitere Informationen finden Sie unter [Vorgehensweise: Bearbeiten von TableAdapters](http://msdn.microsoft.com/library/ca178745-e35a-45f1-a395-23cddfd8f855).  
  
## <a name="tableadapter-update-commands"></a>Aktualisierungsbefehle für TableAdapter  
 Die Aktualisierungsfunktionalität eines TableAdapter ist von der Menge der Informationen abhängig, die auf der Grundlage der im TableAdapter-Assistenten enthaltenen Hauptabfrage verfügbar sind. Beispielsweise sind TableAdapters, die so konfiguriert sind, dass sie Werte aus mehreren Tabellen (JOINs), Skalarwerte, Ansichten oder die Ergebnisse von Aggregatfunktionen abrufen, bei der Erstellung anfänglich nicht in der Lage, Aktualisierungen an die zugrunde liegende Datenbank zurückzusenden. Allerdings können Sie konfigurieren die INSERT-, Update- und DELETE-Befehle manuell in die **Eigenschaften** Fenster.  
  
## <a name="tableadapter-queries"></a>TableAdapter-Abfragen  
 ![TableAdapter mit mehreren Abfragen](../data-tools/media/tableadapter.gif "TableAdapter")  
  
 TableAdapters können mehrere Abfragen, um ihre zugeordneten Datentabellen aufzufüllen enthalten. Sie können so viele Abfragen für einen TableAdapter definieren, wie für die Anwendung erforderlich sind, solange jede Abfrage Daten zurückgibt, die demselben Schema entsprechen wie die zugeordnete Datentabelle. Dadurch wird das Laden von Daten ermöglicht, die verschiedene Kriterien erfüllen. Wenn die Anwendung beispielsweise eine Kundentabelle enthält, können Sie eine Abfrage erstellen, durch die die Tabelle mit allen Kunden aufgefüllt wird, deren Name mit einem bestimmten Buchstaben beginnt. Darüber hinaus können Sie eine weitere Abfrage erstellen, durch die die Tabelle mit allen Kunden aufgefüllt wird, die aus demselben Bundesland/Kanton stammen. Um eine `Customers`-Tabelle mit Kunden in einem bestimmten Bundesland/Kanton aufzufüllen, können Sie eine `FillByState`-Abfrage erstellen, die als Parameter für den Wert für das Bundesland bzw. den Kanton Folgendes annimmt: `SELECT * FROM Customers WHERE State = @State`. Sie führen die Abfrage aus, indem Sie die `FillByState`-Methode aufrufen und den Parameterwert folgendermaßen übergeben: `CustomerTableAdapter.FillByState("WA")`. Weitere Informationen finden Sie unter [Vorgehensweise: Erstellen von TableAdapter-Abfragen](../data-tools/how-to-create-tableadapter-queries.md).  
  
 Zusätzlich zu Abfragen, die Daten zurückgeben, die demselben Schema entsprechen wie die Datentabelle des TableAdapter, können Sie Abfragen hinzufügen, die (einzelne) Skalarwerte zurückgeben. Beispielsweise ist das Erstellen einer Abfrage, die die Anzahl der Kunden zurückgibt (`SELECT Count(*) From Customers`) für einen `CustomersTableAdapter` gültig, obwohl die zurückgegebenen Daten nicht dem Schema der Tabelle entsprechen.  
  
## <a name="clearbeforefill-property"></a>ClearBeforeFill-Eigenschaft  
 Jedes Mal, wenn Sie eine Abfrage zum Auffüllen der TableAdapter-Datentabelle ausführen, werden die Daten standardmäßig gelöscht, und nur die Ergebnisse der Abfrage werden in die Tabelle geladen. Legen Sie die `ClearBeforeFill`-Eigenschaft des TableAdapter auf `false` fest, wenn Sie die von einer Abfrage zurückgegebenen Daten in die vorhandenen Daten in einer Datentabelle einfügen bzw. mit diesen zusammenführen möchten. Unabhängig davon, ob Sie die Daten löschen, müssen Sie Aktualisierungen explizit an die Datenbank zurücksenden, wenn dies erforderlich ist. Vergessen Sie also nicht, an den Daten in der Tabelle vorgenommene Änderungen zu speichern, bevor Sie eine weitere Abfrage zum Auffüllen der Tabelle ausführen. Weitere Informationen finden Sie unter [Aktualisieren von Daten mit einem TableAdapter](../data-tools/update-data-by-using-a-tableadapter.md).  
  
## <a name="tableadapter-inheritance"></a>TableAdapter-Vererbung  
 Durch TableAdapters wird die Funktionalität von Standarddatenadaptern erweitert, indem ein konfigurierter <xref:System.Data.Common.DataAdapter> gekapselt wird. Standardmäßig erbt der TableAdapter von <xref:System.ComponentModel.Component> und kann nicht in die <xref:System.Data.Common.DataAdapter>-Klasse umgewandelt werden. Die Umwandlung eines TableAdapter in einen <xref:System.Data.Common.DataAdapter> führt zu einer <xref:System.InvalidCastException>. Um die Basisklasse eines TableAdapter zu ändern, können Sie eine abgeleitete Klasse eingeben <xref:System.ComponentModel.Component> in die **Basisklasse** Eigenschaft von TableAdapter in die **Dataset-Designer**.  
  
## <a name="tableadapter-methods-and-properties"></a>TableAdapter-Methoden und -Eigenschaften  
 Die TableAdapter-Klasse ist nicht Teil der [!INCLUDE[dnprdnshort](../includes/dnprdnshort-md.md)], und daher Sie können nicht Nachschlagen in der Dokumentation oder der **Objektkatalog**. Sie wird zur Entwurfszeit erstellt, wenn Sie einen der oben erwähnten Assistenten verwenden. Der einem TableAdapter beim Erstellen zugewiesene Name basiert auf dem Namen der Tabelle, mit der Sie arbeiten. Wenn Sie beispielsweise einen TableAdapter erstellen, der auf einer Tabelle basiert, die sich in einer Datenbank mit der Bezeichnung `Orders` befindet, erhält der TableAdapter den Namen `OrdersTableAdapter`. Der Klassenname des TableAdapter kann geändert werden, mithilfe der **Namen** -Eigenschaft in der **Dataset-Designer**.  
  
 Im Folgenden werden die gebräuchlichsten TableAdapter-Methoden und -Eigenschaften vorgestellt:  
  
|Member|Beschreibung|  
|------------|-----------------|  
|`TableAdapter.Fill`|Füllt die dem TableAdapter zugeordnete Datentabelle mit den Ergebnissen des SELECT-Befehls für den TableAdapter auf. Weitere Informationen finden Sie unter [Vorgehensweise: Füllen eines Datasets mit Daten](../data-tools/how-to-fill-a-dataset-with-data.md).|  
|`TableAdapter.Update`|Sendet Änderungen an die Datenbank zurück, und gibt eine der Anzahl der vom Aktualisierungsvorgang betroffenen Zeilen entsprechende ganze Zahl zurück. Weitere Informationen finden Sie unter [Aktualisieren von Daten mit einem TableAdapter](../data-tools/update-data-by-using-a-tableadapter.md).|  
|`TableAdapter.GetData`|Gibt eine neue mit Daten aufgefüllte <xref:System.Data.DataTable> zurück.|  
|`TableAdapter.Insert`|Erstellt eine neue Zeile in der Datentabelle. Weitere Informationen finden Sie unter [Vorgehensweise: Hinzufügen von Zeilen zu einer DataTable](http://msdn.microsoft.com/library/78ebbb43-c402-49cf-81da-0715289487bf).|  
|`TableAdapter.ClearBeforeFill`|Bestimmt, ob eine Datentabelle geleert wird, bevor Sie eine der `Fill`-Methoden aufrufen.|  
  
## <a name="tableadapter-update-method"></a>TableAdapter-Aktualisierungsmethode  
 TableAdapters verwenden zum Lesen und Schreiben in Datenbanken Datenbefehle. Die anfängliche `Fill`-(Haupt-)Abfrage des TableAdapter wird ebenso als Grundlage für die Erstellung des Schemas der zugeordneten Datentabelle verwendet wie die Befehle `InsertCommand`, `UpdateCommand` und `DeleteCommand`, die der `TableAdapter.Update`-Methode zugeordnet sind. Dies bedeutet, dass beim Aufrufen des TableAdapter `Update` Methode führt die Anweisungen, die erstellt, wenn der TableAdapter ursprünglich konfiguriert wurde, und nicht eine der zusätzlichen Abfragen hinzugefügt, mit der **TableAdapter-Konfigurations-Assistenten**.  
  
 Wenn Sie einen TableAdapter verwenden, führt er effektiv dieselben Operationen mit den Befehlen aus, die Sie normalerweise ausführen würden. Wenn Sie beispielsweise die `Fill`-Methode für den Adapter aufrufen, führt der Adapter in seiner `SelectCommand`-Eigenschaft einen Datenbefehl aus und verwendet einen Datenreader (beispielsweise <xref:System.Data.SqlClient.SqlDataReader>), um das Resultset in die Datentabelle zu laden. Wenn Sie die `Update`-Methode des Adapters aufrufen, wird entsprechend der zutreffende Befehl für jeden geänderten Datensatz in der Datentabelle ausgeführt (in den Eigenschaften `UpdateCommand`, `InsertCommand` und `DeleteCommand`).  
  
> [!NOTE]
>  Wenn die Hauptabfrage genügend Informationen enthält, werden beim Generieren des TableAdapter standardmäßig die Befehle `InsertCommand`, `UpdateCommand` und `DeleteCommand` erstellt. Wenn es sich bei der Hauptabfrage für den TableAdapter um mehr als eine SELECT-Anweisung für eine einzelne Tabelle handelt, ist der Designer möglicherweise nicht in der Lage, die Befehle `InsertCommand`, `UpdateCommand` und `DeleteCommand` zu generieren. Wenn diese Befehle nicht generiert werden, tritt beim Ausführen der `TableAdapter.Update`-Methode möglicherweise ein Fehler auf.  
  
## <a name="tableadapter-generatedbdirectmethods"></a>TableAdapter GenerateDbDirectMethods  
 Zusätzlich zu den Befehlen `InsertCommand`, `UpdateCommand` und `DeleteCommand` werden für die TableAdapter-Erstellung Methoden verwendet, die direkt gegen die Datenbank ausgeführt werden können. Diese Methoden (`TableAdapter.Insert`, `TableAdapter.Update` und `TableAdapter.Delete`) können direkt aufgerufen werden, um Daten in der Datenbank zu bearbeiten. Dies bedeutet, dass Sie zum Umgang mit Einfüge-, Aktualisierungs- und Löschvorgängen, die für die zugeordnete Datentabelle ausstehend sind, diese einzelnen Methoden vom Code aufrufen und dass nicht TableAdapter.Update aufgerufen wird.  
  
 Wenn Sie nicht, um diese direkten Methoden zu erstellen möchten, legen Sie der TableAdapters **GenerateDbDirectMethods** Eigenschaft `false` (in der **Eigenschaften** Fenster). Dem TableAdapter hinzugefügte zusätzliche Abfragen sind eigenständig und können diese Methoden nicht generieren.  
  
## <a name="tableadapter-support-for-nullable-types"></a>TableAdapter-Unterstützung für Typen mit Nullwert  
 Die TableAdapters unterstützen die Typen `Nullable(Of T)` und `T?`, für die ein NULL-Wert zulässig ist. Weitere Informationen zu nullable-Typen in Visual Basic, finden Sie unter [auf NULL festlegbare Werttypen](http://msdn.microsoft.com/library/9ac3b602-6f96-4e6d-96f7-cd4e81c468a6). Weitere Informationen zu nullable-Typen in c#, finden Sie unter [Using Nullable Types](http://msdn.microsoft.com/library/0bacbe72-ce15-4b14-83e1-9c14e6380c28).  
  
## <a name="see-also"></a>Siehe auch  
 [Exemplarische Vorgehensweisen für Daten](http://msdn.microsoft.com/library/15a88fb8-3bee-4962-914d-7a1f8bd40ec4)   
 [Vorgehensweise: Herstellen einer Verbindung zu Daten in einer Datenbank](../data-tools/how-to-connect-to-data-in-a-database.md)   
 [Exemplarische Vorgehensweise: Verbinden mit Daten in einer Datenbank (Windows Forms)](http://msdn.microsoft.com/library/02d39aa6-8993-4602-be13-a13536af3d1c)   
 [Vorbereiten der Anwendung zum Empfangen von Daten](http://msdn.microsoft.com/library/c17bdb7e-c234-4f2f-9582-5e55c27356ad)   
 [Abrufen von Daten für Ihre Anwendung](../data-tools/fetching-data-into-your-application.md)   
 [Binden von Steuerelementen an Daten in Visual Studio](../data-tools/bind-controls-to-data-in-visual-studio.md)   
 [Bearbeiten von Daten in Ihrer Anwendung](../data-tools/editing-data-in-your-application.md)   
 [Überprüfen von Daten](http://msdn.microsoft.com/library/b3a9ee4e-5d4d-4411-9c56-c811f2b4ee7e)   
 [Speichern von Daten](../data-tools/saving-data.md)