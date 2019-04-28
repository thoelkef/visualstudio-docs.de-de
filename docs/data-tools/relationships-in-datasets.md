---
title: Verwenden Sie zum Erstellen von Beziehungen zwischen Datasets DataRelation
ms.date: 11/04/2016
ms.topic: conceptual
f1_keywords:
- vbData.Microsoft.VSDesigner.DataSource.DesignRelation
- vbdata.Microsoft.VSDesigner.DataSource.DesignRelation
helpviewer_keywords:
- relationships, about relationships
- datasets [Visual Basic], relationships
- relationships, datasets
ms.assetid: cfe274f0-71fe-40f6-994e-7c7f6273c9ba
author: gewarren
ms.author: gewarren
manager: jillfra
ms.workload:
- data-storage
ms.openlocfilehash: 653a9b589e68c326fc40a94ed0fa3ab7e49acb8b
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/23/2019
ms.locfileid: "62567649"
---
# <a name="create-relationships-between-datasets"></a>Erstellen von Beziehungen zwischen Datasets
Datasets, die verwandte Daten enthalten Tabellen <xref:System.Data.DataRelation> Objekte aus, um eine über-/unterordnungsbeziehung zwischen den Tabellen und verknüpften Datensätze von den anderen zurück. Hinzufügen verknüpfte Tabellen zu Datasets mithilfe der **Assistenten zur Datenquellenkonfiguration**, oder die **Dataset-Designer**, erstellt und konfiguriert die <xref:System.Data.DataRelation> -Objekt für Sie.

Die <xref:System.Data.DataRelation> Objekt erfüllt zwei Funktionen:

- Verfügbar kann gemacht werden die Datensätze, die im Zusammenhang mit einem Datensatz, mit denen, dem Sie arbeiten werden. Wenn Sie sich auf einen übergeordneten Datensatz untergeordnete Datensätze bietet (<xref:System.Data.DataRow.GetChildRows%2A>) und einen übergeordneten Datensatz aus, wenn Sie mit einem untergeordneten Datensatz arbeiten (<xref:System.Data.DataRow.GetParentRow%2A>).

- Sie können erzwingen, dass Einschränkungen für die referenzielle Integrität, z. B. verknüpfte untergeordnete Datensätze löschen, wenn Sie einen übergeordneten Datensatz löschen.

Es ist wichtig zu verstehen, den Unterschied zwischen einem echten Join und die Funktion der ein <xref:System.Data.DataRelation> Objekt. Datensätze sind in einem Join "true" stammt aus über- und untergeordneten Tabellen und fügen Sie in einem flachen Recordset. Bei Verwendung einer <xref:System.Data.DataRelation> Objekt ist, wird kein neues Recordset wird erstellt. Stattdessen DataRelation verfolgt die Beziehung zwischen Tabellen und hält über- und untergeordneten Datensätzen synchron.

## <a name="datarelation-objects-and-constraints"></a>DataRelation-Objekte und -Einschränkungen
Ein <xref:System.Data.DataRelation> Objekt wird auch zum Erstellen und erzwingen die folgenden Einschränkungen:

- Eine unique-Einschränkung, dadurch wird sichergestellt, dass eine Spalte in der Tabelle keine Duplikate enthält.

- Foreign Key-Einschränkung, die verwendet werden kann, um die Wahrung der referenziellen Integrität zwischen einer über- und untergeordnete Tabelle in einem Dataset.

Einschränkungen, die Sie an einer <xref:System.Data.DataRelation> Objekt werden implementiert, indem automatisch die entsprechenden Objekte erstellen oder Festlegen von Eigenschaften. Bei der Erstellung einer foreign Key-Einschränkung mithilfe der <xref:System.Data.DataRelation> -Objekt, das Instanzen von der <xref:System.Data.ForeignKeyConstraint> Klasse hinzugefügt werden, um die <xref:System.Data.DataRelation> des Objekts <xref:System.Data.DataRelation.ChildKeyConstraint%2A> Eigenschaft.

Implementiert eine unique-Einschränkung entweder einfach die <xref:System.Data.DataColumn.Unique%2A> Eigenschaft einer Datenspalte auf `true` oder durch das Hinzufügen einer Instanz von der <xref:System.Data.UniqueConstraint> -Klasse auf die <xref:System.Data.DataRelation> des Objekts <xref:System.Data.DataRelation.ParentKeyConstraint%2A> Eigenschaft. Weitere Informationen zum Anhalten von Einschränkungen in einem Dataset, finden Sie unter [Deaktivieren von Einschränkungen beim Auffüllen von Datasets](../data-tools/turn-off-constraints-while-filling-a-dataset.md).

### <a name="referential-integrity-rules"></a>Regeln für die referenzielle Integrität
Im Rahmen der foreign Key-Einschränkung können Sie Regeln für die referenzielle Integrität angeben, die an drei Punkten angewendet werden:

- Wenn ein übergeordneter Datensatz aktualisiert wird

- Wenn ein übergeordneter Datensatz gelöscht wird

- Wenn eine Änderung akzeptiert oder abgelehnt wird

Die Regeln, die Sie vornehmen können, werden angegeben, der <xref:System.Data.Rule> Enumeration und sind in der folgenden Tabelle aufgeführt.

|Regel für Foreign Key-Einschränkung|Aktion|
| - |------------|
|<xref:System.Data.Rule.Cascade>|Die Änderung (Update- oder Delete) an den übergeordneten Datensatz wird auch in verwandten Datensätze in der untergeordneten Tabelle vorgenommen.|
|<xref:System.Data.Rule.SetNull>|Untergeordnete Datensätze werden nicht gelöscht, aber der Fremdschlüssel in den untergeordneten Datensätzen wird festgelegt, um <xref:System.DBNull>. Mit dieser Einstellung können untergeordnete Datensätze als "verwaiste" bleiben – d. h., sie haben keine Beziehung zur übergeordneten Datensätze. **Hinweis**: Mit dieser Regel kann dazu führen, dass ungültige Daten in der untergeordneten Tabelle.|
|<xref:System.Data.Rule.SetDefault>|Der Fremdschlüssel in die zugehörigen untergeordneten Datensätze auf den Standardwert festgelegt ist (wie von der Spaltenwerts festgelegt <xref:System.Data.DataColumn.DefaultValue%2A> Eigenschaft).|
|<xref:System.Data.Rule.None>|Verknüpfte untergeordnete Datensätze wird nicht geändert. Mit dieser Einstellung können untergeordnete Datensätze Verweise auf ungültige übergeordnete Datensätze enthalten.|

Weitere Informationen zu Updates in der Dataset-Tabellen finden Sie unter [Rückspeichern von Daten in der Datenbank](../data-tools/save-data-back-to-the-database.md).

### <a name="constraint-only-relations"></a>Einschränkung nur Beziehungen
Bei der Erstellung einer <xref:System.Data.DataRelation> Objekt, Sie haben die Möglichkeit, anzugeben, dass die Beziehung werden nur verwendet, um Einschränkungen zu erzwingen – d. h. es nicht auch verwendet werden verknüpfte Datensätze auf. Sie können diese Option verwenden, um ein Dataset zu generieren, das ist etwas effizienter und weniger als eine mit der Zugriffsfunktion-Methoden enthält. Allerdings werden Sie nicht verknüpfte Datensätze zugreifen können. Z. B. eine Einschränkung nur Beziehung verhindert, dass Sie einen übergeordneten Datensatz, der immer untergeordnete Datensätze noch löschen, und kann nicht der Zugriff auf die untergeordneten Datensätze über das übergeordnete Element.

## <a name="manually-creating-a-data-relation-in-the-dataset-designer"></a>Erstellen manuell eine datenbeziehung im Dataset-Designer
Wenn Sie Tabellen mit den Daten-Entwurfstools in Visual Studio erstellen, werden Beziehungen automatisch erstellt, wenn die Informationen aus der Quelle Ihrer Daten gesammelt werden kann. Wenn Sie manuell hinzufügen, von Datentabellen aus der **DataSet** auf der Registerkarte die **Toolbox**, Sie möglicherweise die Beziehung manuell zu erstellen. Weitere Informationen zum Erstellen <xref:System.Data.DataRelation> Objekte programmgesteuert, finden Sie unter [Hinzufügen von "DataRelations"](/dotnet/framework/data/adonet/dataset-datatable-dataview/adding-datarelations).

Beziehungen zwischen Tabellen angezeigt werden, als Zeilen in der **Dataset-Designer**, durch ein Symbol Schlüssel und unendlich, die mit der 1: n Aspekt der Beziehung. Standardmäßig wird der Name der Beziehung nicht auf der Entwurfsoberfläche angezeigt.

[!INCLUDE[note_settings_general](../data-tools/includes/note_settings_general_md.md)]

#### <a name="to-create-a-relationship-between-two-data-tables"></a>Um eine Beziehung zwischen zwei Datentabellen zu erstellen.

1. Öffnen Sie das Dataset im **DataSet-Designer**. Weitere Informationen finden Sie unter [Exemplarische Vorgehensweise: Erstellen eines Datasets im Dataset-Designer](walkthrough-creating-a-dataset-with-the-dataset-designer.md).

2. Ziehen Sie eine **Beziehung** -Objekt aus der **DataSet** Toolbox auf die untergeordnete Datentabelle in der Beziehung.

     Die **Beziehung** Dialogfeld geöffnet wird, füllen die **untergeordnete Tabelle** Feld mit der Tabelle, die Sie gezogen haben die **Beziehung** -Objekt auf.

3. Wählen Sie die übergeordnete Tabelle aus der **übergeordnete Tabelle** Feld. Die übergeordnete Tabelle enthält die Datensätze auf der Seite "1" einer 1: n Beziehung.

4. Stellen Sie sicher, dass die richtige untergeordnete Tabelle, in angezeigt wird der **untergeordnete Tabelle** Feld. Die untergeordnete Tabelle enthält die Datensätze auf der Seite "many" einer 1: n Beziehung.

5. Geben Sie einen Namen für die Beziehung in der **Namen** ein, oder übernehmen Sie den Standardnamen, die basierend auf den ausgewählten Tabellen. Dies ist der Name des eigentlichen <xref:System.Data.DataRelation> -Objekt im Code.

6. Wählen Sie die Spalten, die Tabellen zu, in verknüpfen, der **Schlüsselspalten** und **Fremdschlüsselspalten** aufgeführt.

7. Wählen Sie, ob Sie eine Beziehung, Einschränkung oder beides zu erstellen.

8. Aktivieren oder deaktivieren Sie die **geschachtelte Beziehung** Feld. Wählen diese Option wird die <xref:System.Data.DataRelation.Nested%2A> Eigenschaft `true`, und die untergeordneten Zeilen der Beziehung, die innerhalb der übergeordneten Spalte geschachtelt werden, wenn diese Zeilen werden als XML-Daten geschrieben oder mit synchronisiert <xref:System.Xml.XmlDataDocument>. Weitere Informationen finden Sie unter [Schachteln von DataRelations](/dotnet/framework/data/adonet/dataset-datatable-dataview/nesting-datarelations).

9. Legen Sie die Regeln erzwungen werden, wenn Sie Änderungen an Datensätzen in diesen Tabellen vornehmen. Weitere Informationen finden Sie unter <xref:System.Data.Rule>.

10. Klicken Sie auf **OK** zum Erstellen der Beziehung. Eine Beziehungslinie wird auf der zwischen den beiden Tabellen-Designer angezeigt.

#### <a name="to-display-a-relation-name-in-the-dataset-designer"></a>Um einen Beziehungsnamen im Dataset-Designer anzuzeigen.

1. Öffnen Sie das Dataset im **DataSet-Designer**. Weitere Informationen finden Sie unter [Exemplarische Vorgehensweise: Erstellen eines Datasets im Dataset-Designer](walkthrough-creating-a-dataset-with-the-dataset-designer.md).

2. Von der **Daten** , wählen Sie im Menü der **Beziehungsbezeichnungen anzeigen** Befehl zur Anzeige der Name der Beziehung. Deaktivieren Sie diesen Befehl zum Ausblenden der Name der Beziehung.

## <a name="see-also"></a>Siehe auch

- [Erstellen und Konfigurieren von Datasets in Visual Studio](../data-tools/create-and-configure-datasets-in-visual-studio.md)