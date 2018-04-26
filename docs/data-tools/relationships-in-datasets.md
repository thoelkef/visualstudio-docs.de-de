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
manager: douge
ms.prod: visual-studio-dev15
ms.technology: vs-data-tools
ms.workload:
- data-storage
ms.openlocfilehash: b3b101d251167a646b66568f7aacc005d7c792d7
ms.sourcegitcommit: e13e61ddea6032a8282abe16131d9e136a927984
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/26/2018
---
# <a name="create-relationships-between-datasets"></a>Beziehungen zwischen Datasets erstellen
Datasets, die verknüpfte Daten enthalten Tabellen <xref:System.Data.DataRelation> Objekte, um eine über-/unterordnungsbeziehung zwischen den Tabellen darzustellen und um verknüpfte Datensätze von den anderen zurückzugeben. Hinzufügen verknüpfte Tabellen zu Datasets mithilfe der **Datenquellen Konfigurations-Assistenten**, oder die **Dataset-Designer**, erstellt und konfiguriert die <xref:System.Data.DataRelation> Objekt für Sie.

Die <xref:System.Data.DataRelation> -Objekt führt zwei Funktionen:

-   Sie können die Datensätze verfügbar machen im Zusammenhang mit einem Datensatz, mit dem Sie arbeiten. Wenn Sie sich auf einen übergeordneten Datensatz untergeordnete Datensätze bietet (<xref:System.Data.DataRow.GetChildRows%2A>) und einen übergeordneten Datensatz bei Verwendung mit einem untergeordneten Datensatz (<xref:System.Data.DataRow.GetParentRow%2A>).

-   Es kann erzwingen, dass Einschränkungen für die referenzielle Integrität, z. B. untergeordnete Datensätze löschen, wenn Sie einen übergeordneten Datensatz gelöscht.

Es ist wichtig zu verstehen, den Unterschied zwischen einem Join "true" und die Funktion des ein <xref:System.Data.DataRelation> Objekt. Datensätze sind in einem "true" Join über- und untergeordneten Tabellen entnommen und einem Flatfile Recordset abgelegt. Bei Verwendung einer <xref:System.Data.DataRelation> -Objekt, kein neues Recordset erstellt wird. Stattdessen DataRelation verfolgt die Beziehung zwischen Tabellen und hält über- und untergeordneten Datensätzen synchron.

## <a name="datarelation-objects-and-constraints"></a>DataRelation-Objekte und Einschränkungen
Ein <xref:System.Data.DataRelation> Objekt dient außerdem zum Erstellen und erzwingen Sie die folgenden Einschränkungen:

-   Eine unique-Einschränkung, dadurch wird sichergestellt, dass eine Spalte in der Tabelle keine Duplikate enthält.

-   Foreign Key-Einschränkung, die verwendet werden kann, um die referenzielle Integrität zwischen einer über- und untergeordneten Tabelle in einem Dataset zu erhalten.

Einschränkungen, die Sie, in angeben einem <xref:System.Data.DataRelation> Objekt werden automatisch die entsprechenden Objekte zu erstellen oder Festlegen von Eigenschaften implementiert. Bei der Erstellung einer foreign Key-Einschränkung mithilfe der <xref:System.Data.DataRelation> -Objekt, das Instanzen von der <xref:System.Data.ForeignKeyConstraint> Klasse hinzugefügt werden die <xref:System.Data.DataRelation> des Objekts <xref:System.Data.DataRelation.ChildKeyConstraint%2A> Eigenschaft.

Eine unique-Einschränkung wird implementiert, entweder indem Sie einfach Festlegen der <xref:System.Data.DataColumn.Unique%2A> Eigenschaft einer Datenspalte auf `true` oder durch Hinzufügen einer Instanz von der <xref:System.Data.UniqueConstraint> Klasse der <xref:System.Data.DataRelation> des Objekts <xref:System.Data.DataRelation.ParentKeyConstraint%2A> Eigenschaft. Informationen zum Anhalten von Einschränkungen in einem Dataset, finden Sie unter [Deaktivieren von Einschränkungen beim Auffüllen von Datasets](../data-tools/turn-off-constraints-while-filling-a-dataset.md).

### <a name="referential-integrity-rules"></a>Regeln für die referenzielle Integrität
Im Rahmen der foreign Key-Einschränkung können Sie Regeln für die referenzielle Integrität angeben, die an drei Punkten angewendet werden:

-   Wenn ein übergeordneter Datensatz aktualisiert wird

-   Wenn ein übergeordneter Datensatz gelöscht wird

-   Wenn eine Änderung akzeptiert oder abgelehnt wird

Die Regeln, die Sie vornehmen können, werden angegeben, der <xref:System.Data.Rule> Enumeration und sind in der folgenden Tabelle aufgeführt.

|Regel für Foreign Key-Einschränkung|Aktion|
|----------------------------------|------------|
|<xref:System.Data.Rule.Cascade>|In verwandten Datensätze in der untergeordneten Tabelle erfolgt auch die zum übergeordneten Datensatz vorgenommene Änderung (aktualisieren oder löschen).|
|<xref:System.Data.Rule.SetNull>|Untergeordnete Datensätze werden nicht gelöscht, aber die Fremdschlüssel in der untergeordneten Datensätze auf festgelegt ist <xref:System.DBNull>. Mit dieser Einstellung können untergeordnete Datensätze als "verwaiste" gelassen werden – das heißt, sie haben keine Beziehung zur übergeordneten Datensätzen. **Hinweis:** mit dieser Regel kann dazu führen, ungültige Daten in der untergeordneten Tabelle.|
|<xref:System.Data.Rule.SetDefault>|Der Fremdschlüssel in der zugehörigen untergeordneten Datensätze auf den Standardwert festgelegt ist (wie der Spaltenwerts <xref:System.Data.DataColumn.DefaultValue%2A> Eigenschaft).|
|<xref:System.Data.Rule.None>|Verknüpfte untergeordnete Datensätze werden keine Änderung vorgenommen. Mit dieser Einstellung können untergeordnete Datensätze Verweise auf ungültige übergeordnete Datensätze enthalten.|

Weitere Informationen zu Updates in der Dataset-Tabellen finden Sie unter [Daten wieder in der Datenbank speichern](../data-tools/save-data-back-to-the-database.md).

### <a name="constraint-only-relations"></a>Einschränkung nur Beziehungen
Beim Erstellen einer <xref:System.Data.DataRelation> -Objekt, haben Sie die Möglichkeit der Angabe, dass die Beziehung verwendet werden, nur für die Einschränkungen erzwingen – d. h. es wird nicht eingesetzt werden verknüpfte Datensätze zugreifen. Sie können diese Option verwenden, um ein Dataset zu generieren, ist etwas effizienter und weniger Methoden als eine bietet die Möglichkeit, im Zusammenhang Datensätze enthält. Allerdings werden Sie nicht verknüpfte Datensätze zugreifen können. Z. B. eine Einschränkung nur Beziehung verhindert, dass ein übergeordneter Datensatz, der immer untergeordneten Datensätzen noch gelöscht und kann nicht der Zugriff auf die untergeordneten Datensätze über das übergeordnete Element.

## <a name="manually-creating-a-data-relation-in-the-dataset-designer"></a>Erstellen manuell eine datenbeziehung im Dataset-Designer
Beim Erstellen von Datentabellen mit Daten-Entwurfstools in Visual Studio werden die Beziehungen automatisch erstellt, wenn die Informationen über die Quelle der Daten erfasst werden kann. Wenn Sie manuell Datentabellen aus hinzufügen der **DataSet** auf der Registerkarte die **Toolbox**, Sie möglicherweise die Beziehung manuell zu erstellen. Informationen zum Erstellen von <xref:System.Data.DataRelation> Objekte programmgesteuert, finden Sie unter [Hinzufügen von "DataRelations"](/dotnet/framework/data/adonet/dataset-datatable-dataview/adding-datarelations).

Beziehungen zwischen Datentabellen angezeigt werden, als Zeilen in der **Dataset-Designer**, mit einem Schlüssel und Infinity-Symbol, die den Aspekt 1: n-Beziehung darstellt. Standardmäßig wird der Name der Beziehung nicht auf der Entwurfsoberfläche angezeigt.

[!INCLUDE[note_settings_general](../data-tools/includes/note_settings_general_md.md)]

#### <a name="to-create-a-relationship-between-two-data-tables"></a>So erstellen eine Beziehung zwischen zwei Datentabellen

1.  Öffnen Sie das Dataset in die **Dataset-Designer**. Weitere Informationen finden Sie unter [Exemplarische Vorgehensweise: Erstellen eines Datasets im Dataset-Designer](walkthrough-creating-a-dataset-with-the-dataset-designer.md).

2.  Ziehen Sie eine **Beziehung** -Objekt aus der **DataSet** Toolbox auf die untergeordnete Datentabelle in der Beziehung.

     Die **Beziehung** Dialogfeld geöffnet, Auffüllen der **untergeordnete Tabelle** Feld mit der Tabelle, die Sie gezogen haben die **Beziehung** -Objekt auf.

3.  Wählen Sie die übergeordnete Tabelle aus der **übergeordnete Tabelle** Feld. Die übergeordnete Tabelle enthält Datensätze auf der Seite "1" einer 1: n-Beziehung.

4.  Stellen Sie sicher, dass die richtige untergeordnete Tabelle, in angezeigt wird der **untergeordnete Tabelle** Feld. Die untergeordnete Tabelle enthält Datensätze auf der Seite "many" einer 1: n-Beziehung.

5.  Geben Sie einen Namen für die Beziehung in der **Namen** Feld ein, oder übernehmen Sie den Standardnamen, basierend auf den ausgewählten Tabellen. Dies ist der Name des eigentlichen <xref:System.Data.DataRelation> Objekt im Code.

6.  Wählen Sie die Spalten, die Tabellen, in verknüpfen, der **Schlüsselspalten** und **Fremdschlüsselspalten** aufgeführt.

7.  Wählen Sie, ob eine Beziehung oder Einschränkung erstellt.

8.  Aktivieren oder Deaktivieren der **geschachtelte Beziehung** Feld. Auswählen dieser Option wird die <xref:System.Data.DataRelation.Nested%2A> Eigenschaft `true`, und die untergeordneten Zeilen der Beziehung innerhalb der übergeordneten Spalte geschachtelt werden, wenn diese Zeilen werden als XML-Daten geschrieben oder beim Synchronisieren mit <xref:System.Xml.XmlDataDocument>. Weitere Informationen finden Sie unter [Schachteln von "DataRelations"](/dotnet/framework/data/adonet/dataset-datatable-dataview/nesting-datarelations).

9. Legen Sie die Regeln erzwungen werden, wenn Sie Änderungen an Datensätzen in diesen Tabellen vornehmen möchten. Weitere Informationen finden Sie unter <xref:System.Data.Rule>.

10. Klicken Sie auf **OK** zum Erstellen der Beziehung. Eine Beziehungslinie wird zwischen den beiden Tabellen-Designer angezeigt.

#### <a name="to-display-a-relation-name-in-the-dataset-designer"></a>Um einen Beziehungsnamen im Dataset-Designer anzeigen

1.  Öffnen Sie das Dataset in die **Dataset-Designer**. Weitere Informationen finden Sie unter [Exemplarische Vorgehensweise: Erstellen eines Datasets im Dataset-Designer](walkthrough-creating-a-dataset-with-the-dataset-designer.md).

2.  Aus der **Daten** klicken Sie im Menü der **Anzeigen von Beziehungsbezeichnungen** Befehl aus, um den Beziehungsnamen anzuzeigen. Deaktivieren Sie den Befehl zum Ausblenden der Name der Beziehung.

## <a name="see-also"></a>Siehe auch

- [Erstellen und Konfigurieren von Datasets in Visual Studio](../data-tools/create-and-configure-datasets-in-visual-studio.md)