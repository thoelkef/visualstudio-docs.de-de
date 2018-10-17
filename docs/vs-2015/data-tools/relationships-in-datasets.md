---
title: Beziehungen in Datasets | Microsoft-Dokumentation
ms.custom: ''
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
f1_keywords:
- vbData.Microsoft.VSDesigner.DataSource.DesignRelation
- vbdata.Microsoft.VSDesigner.DataSource.DesignRelation
dev_langs:
- VB
- CSharp
- C++
- aspx
helpviewer_keywords:
- relationships, about relationships
- datasets [Visual Basic], relationships
- relationships, datasets
ms.assetid: cfe274f0-71fe-40f6-994e-7c7f6273c9ba
caps.latest.revision: 18
author: gewarren
ms.author: gewarren
manager: ghogen
ms.openlocfilehash: cfa1f6fa49c8fab1bd93a0d2a38b85ec958a6fed
ms.sourcegitcommit: 9ceaf69568d61023868ced59108ae4dd46f720ab
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 10/12/2018
ms.locfileid: "49275703"
---
# <a name="relationships-in-datasets"></a>Beziehungen in datasets
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

  
Datasets, die verwandte Daten enthalten Tabellen <xref:System.Data.DataRelation> Objekte aus, um eine über-/unterordnungsbeziehung zwischen den Tabellen und verknüpften Datensätze von den anderen zurück. Hinzufügen verknüpfte Tabellen zu Datasets mithilfe der **Assistenten zur Datenquellenkonfiguration**, oder die **Dataset-Designer**, erstellt und konfiguriert die <xref:System.Data.DataRelation> -Objekt für Sie.  
  
 Die <xref:System.Data.DataRelation> Objekt erfüllt zwei Funktionen:  
  
-   Verfügbar kann gemacht werden die Datensätze, die im Zusammenhang mit einem Datensatz, mit denen, dem Sie arbeiten werden. Wenn Sie sich auf einen übergeordneten Datensatz untergeordnete Datensätze bietet (<xref:System.Data.DataRow.GetChildRows%2A>) und einen übergeordneten Datensatz aus, wenn Sie mit einem untergeordneten Datensatz arbeiten (<xref:System.Data.DataRow.GetParentRow%2A>).  
  
-   Sie können erzwingen, dass Einschränkungen für die referenzielle Integrität, z. B. verknüpfte untergeordnete Datensätze löschen, wenn Sie einen übergeordneten Datensatz löschen.  
  
 Es ist wichtig zu verstehen, den Unterschied zwischen einem echten Join und die Funktion der ein <xref:System.Data.DataRelation> Objekt. Datensätze sind in einem Join "true" stammt aus über- und untergeordneten Tabellen und fügen Sie in einem flachen Recordset. Bei Verwendung einer <xref:System.Data.DataRelation> Objekt ist, wird kein neues Recordset wird erstellt. Stattdessen DataRelation verfolgt die Beziehung zwischen Tabellen und hält über- und untergeordneten Datensätzen synchron.  
  
## <a name="datarelation-objects-and-constraints"></a>DataRelation-Objekte und -Einschränkungen  
 Ein <xref:System.Data.DataRelation> Objekt wird auch zum Erstellen und erzwingen die folgenden Einschränkungen:  
  
-   Eine unique-Einschränkung, dadurch wird sichergestellt, dass eine Spalte in der Tabelle keine Duplikate enthält.  
  
-   Foreign Key-Einschränkung, die verwendet werden kann, um die Wahrung der referenziellen Integrität zwischen einer über- und untergeordnete Tabelle in einem Dataset.  
  
 Einschränkungen, die Sie an einer <xref:System.Data.DataRelation> Objekt werden implementiert, indem automatisch die entsprechenden Objekte erstellen oder Festlegen von Eigenschaften. Bei der Erstellung einer foreign Key-Einschränkung mithilfe der <xref:System.Data.DataRelation> -Objekt, das Instanzen von der <xref:System.Data.ForeignKeyConstraint> Klasse hinzugefügt werden, um die <xref:System.Data.DataRelation> des Objekts <xref:System.Data.DataRelation.ChildKeyConstraint%2A> Eigenschaft.  
  
 Implementiert eine unique-Einschränkung entweder einfach die <xref:System.Data.DataColumn.Unique%2A> Eigenschaft einer Datenspalte auf `true` oder durch das Hinzufügen einer Instanz von der <xref:System.Data.UniqueConstraint> -Klasse auf die <xref:System.Data.DataRelation> des Objekts <xref:System.Data.DataRelation.ParentKeyConstraint%2A> Eigenschaft. Weitere Informationen zum Anhalten von Einschränkungen in einem Dataset, finden Sie unter [Deaktivieren von Einschränkungen beim Auffüllen von Datasets](../data-tools/turn-off-constraints-while-filling-a-dataset.md).  
  
### <a name="referential-integrity-rules"></a>Regeln für die referenzielle Integrität  
 Im Rahmen der foreign Key-Einschränkung können Sie Regeln für die referenzielle Integrität angeben, die an drei Punkten angewendet werden:  
  
-   Wenn ein übergeordneter Datensatz aktualisiert wird  
  
-   Wenn ein übergeordneter Datensatz gelöscht wird  
  
-   Wenn eine Änderung akzeptiert oder abgelehnt wird  
  
 Die Regeln, die Sie vornehmen können, werden angegeben, der <xref:System.Data.Rule> Enumeration und sind in der folgenden Tabelle aufgeführt.  
  
|Regel für Foreign Key-Einschränkung|Aktion|  
|----------------------------------|------------|  
|<xref:System.Data.Rule>|Die Änderung (Update- oder Delete) an den übergeordneten Datensatz wird auch in verwandten Datensätze in der untergeordneten Tabelle vorgenommen.|  
|<xref:System.Data.Rule>|Untergeordnete Datensätze werden nicht gelöscht, aber der Fremdschlüssel in den untergeordneten Datensätzen wird festgelegt, um <xref:System.DBNull>. Mit dieser Einstellung können untergeordnete Datensätze als "verwaiste" bleiben – d. h., sie haben keine Beziehung zur übergeordneten Datensätze. **Hinweis:** mit dieser Regel kann ungültige Daten in der untergeordneten Tabelle führen.|  
|<xref:System.Data.Rule>|Der Fremdschlüssel in die zugehörigen untergeordneten Datensätze auf den Standardwert festgelegt ist (wie von der Spaltenwerts festgelegt <xref:System.Data.DataColumn.DefaultValue%2A> Eigenschaft).|  
|<xref:System.Data.Rule>|Verknüpfte untergeordnete Datensätze wird nicht geändert. Mit dieser Einstellung können untergeordnete Datensätze Verweise auf ungültige übergeordnete Datensätze enthalten.|  
  
 Weitere Informationen zu Updates in der Dataset-Tabellen finden Sie unter [Rückspeichern von Daten in der Datenbank](../data-tools/save-data-back-to-the-database.md).  
  
### <a name="constraint-only-relations"></a>Einschränkung nur Beziehungen  
 Bei der Erstellung einer <xref:System.Data.DataRelation> Objekt, Sie haben die Möglichkeit, anzugeben, dass die Beziehung werden nur verwendet, um Einschränkungen zu erzwingen – d. h. es nicht auch verwendet werden verknüpfte Datensätze auf. Sie können diese Option verwenden, um ein Dataset zu generieren, das ist etwas effizienter und weniger als eine mit der Zugriffsfunktion-Methoden enthält. Allerdings werden Sie nicht verknüpfte Datensätze zugreifen können. Z. B. eine Einschränkung nur Beziehung verhindert, dass Sie einen übergeordneten Datensatz, der immer untergeordnete Datensätze noch löschen, und kann nicht der Zugriff auf die untergeordneten Datensätze über das übergeordnete Element.  
  
## <a name="manually-creating-a-data-relation-in-the-dataset-designer"></a>Erstellen manuell eine datenbeziehung im Dataset-Designer  
 Wenn Sie Tabellen mit den Daten-Entwurfstools in Visual Studio erstellen, werden Beziehungen automatisch erstellt, wenn die Informationen aus der Quelle Ihrer Daten gesammelt werden kann. Wenn Sie manuell hinzufügen, von Datentabellen aus der **DataSet** auf der Registerkarte die **Toolbox**, Sie möglicherweise die Beziehung manuell zu erstellen. Weitere Informationen zum Erstellen <xref:System.Data.DataRelation> Objekte programmgesteuert, finden Sie unter [Hinzufügen von "DataRelations"](http://msdn.microsoft.com/library/a4a564fb-c1c4-4135-b6c2-b030e51195e4).  
  
 Beziehungen zwischen Tabellen angezeigt werden, als Zeilen in der **Dataset-Designer**, durch ein Symbol Schlüssel und unendlich, die mit der 1: n Aspekt der Beziehung. Standardmäßig ist der Name des der RelationshipCommentEnd Id = "1c8c78e19b7fa441" wird nicht auf der Entwurfsoberfläche angezeigt.  
  
 [!INCLUDE[note_settings_general](../includes/note-settings-general-md.md)]  
  
#### <a name="to-create-a-relationship-between-two-data-tables"></a>Um eine Beziehung zwischen zwei Datentabellen zu erstellen.  
  
1.  Öffnen Sie das Dataset in den **Dataset-Designer**. Weitere Informationen finden Sie unter [Vorgehensweise: Öffnen Sie ein Dataset im Dataset-Designer](http://msdn.microsoft.com/library/36fc266f-365b-42cb-aebb-c993dc2c47c3).  
  
2.  Ziehen Sie eine **Beziehung** -Objekt aus der **DataSet** Toolbox auf die untergeordnete Datentabelle in der Beziehung.  
  
     Die **Beziehung** Dialogfeld geöffnet wird, füllen die **untergeordnete Tabelle** Feld mit der Tabelle, die Sie gezogen haben die **Beziehung** -Objekt auf.  
  
3.  Wählen Sie die übergeordnete Tabelle aus der **übergeordnete Tabelle** Feld. Die übergeordnete Tabelle enthält die Datensätze auf der Seite "1" einer 1: n Beziehung.  
  
4.  Stellen Sie sicher, dass die richtige untergeordnete Tabelle, in angezeigt wird der **untergeordnete Tabelle** Feld. Die untergeordnete Tabelle enthält die Datensätze auf der Seite "many" einer 1: n Beziehung.  
  
5.  Geben Sie einen Namen für die Beziehung in der **Namen** ein, oder übernehmen Sie den Standardnamen, die basierend auf den ausgewählten Tabellen. Dies ist der Name des eigentlichen <xref:System.Data.DataRelation> -Objekt im Code.  
  
6.  Wählen Sie die Spalten, die Tabellen zu, in verknüpfen, der **Schlüsselspalten** und **Fremdschlüsselspalten** aufgeführt.  
  
7.  Wählen Sie, ob Sie eine Beziehung, Einschränkung oder beides zu erstellen. Weitere Informationen finden Sie unter [Einführung in DataRelation-Objekte](http://msdn.microsoft.com/library/89d8a881-8265-41f2-a88b-61311ab06192).  
  
8.  Aktivieren oder deaktivieren Sie die **geschachtelte Beziehung** Feld. Wählen diese Option wird die <xref:System.Data.DataRelation.Nested%2A> Eigenschaft `true`, und die untergeordneten Zeilen der Beziehung, die innerhalb der übergeordneten Spalte geschachtelt werden, wenn diese Zeilen werden als XML-Daten geschrieben oder mit synchronisiert <xref:System.Xml.XmlDataDocument>. Weitere Informationen finden Sie unter [Schachteln von DataRelations](http://msdn.microsoft.com/library/9530f9c9-dd98-4b93-8cdb-40d7f1e8d0ab).  
  
9. Legen Sie die Regeln erzwungen werden, wenn Sie Änderungen an Datensätzen in diesen Tabellen vornehmen. Weitere Informationen finden Sie unter <xref:System.Data.Rule>.  
  
10. Klicken Sie auf **OK** zum Erstellen der Beziehung. Eine Beziehungslinie wird auf der zwischen den beiden Tabellen-Designer angezeigt.  
  
#### <a name="to-display-a-relation-name-in-the-dataset-designer"></a>Um einen Beziehungsnamen im Dataset-Designer anzuzeigen.  
  
1.  Öffnen Sie das Dataset in den **Dataset-Designer**. Weitere Informationen finden Sie unter [Vorgehensweise: Öffnen Sie ein Dataset im Dataset-Designer](http://msdn.microsoft.com/library/36fc266f-365b-42cb-aebb-c993dc2c47c3).  
  
2.  Von der **Daten** , wählen Sie im Menü der **Beziehungsbezeichnungen anzeigen** Befehl zur Anzeige der Name der Beziehung. Deaktivieren Sie diesen Befehl zum Ausblenden der Name der Beziehung.

