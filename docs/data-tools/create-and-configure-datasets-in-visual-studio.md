---
title: Erstellen und Konfigurieren von Datasets
ms.date: 11/21/2018
ms.topic: conceptual
helpviewer_keywords:
- typed datasets, creating
- datasets, creating
- datasets, configuring
author: gewarren
ms.author: gewarren
manager: jillfra
ms.workload:
- data-storage
ms.openlocfilehash: cba7cf4a402b92f05f12faa39b88ab03cd5bd03b
ms.sourcegitcommit: 21d667104199c2493accec20c2388cf674b195c3
ms.translationtype: MTE95
ms.contentlocale: de-DE
ms.lasthandoff: 02/08/2019
ms.locfileid: "55943011"
---
# <a name="create-and-configure-datasets-in-visual-studio"></a>Erstellen und Konfigurieren von Datasets in Visual Studio

Ein Dataset ist ein Satz von Objekten, die Speichern von Daten aus einer Datenbank im Arbeitsspeicher und unterstützen das Nachverfolgen von Änderungen zu erstellen, lesen, aktualisieren und löschen (CRUD) für diese Daten ohne die Notwendigkeit, immer mit der Datenbank verbunden werden. DataSets wurden entwickelt, für einfache *Formulare über Daten* Geschäftsanwendungen. Für neue Anwendungen sollten Sie in Betracht ziehen, Entity Framework zum Speichern und Modellieren von Daten im Arbeitsspeicher zu verwenden. Um mit Datasets arbeiten, sollten Sie über Grundkenntnisse der Konzepte der Datenbank verfügen.

Sie können einen typisierten erstellen <xref:System.Data.DataSet> Klasse in Visual Studio zur Entwurfszeit mithilfe der **Assistenten zur Datenquellenkonfiguration**. Informationen zum programmgesteuerten Erstellen von Datasets finden Sie unter [Erstellen eines Datasets (ADO.NET)](/dotnet/framework/data/adonet/dataset-datatable-dataview/creating-a-dataset).

## <a name="create-a-new-dataset-by-using-the-data-source-configuration-wizard"></a>Erstellen Sie ein neues Dataset mit dem Konfigurations-Assistenten

1. Öffnen Sie Ihr Projekt in Visual Studio, und wählen Sie dann **Projekt** > **neue Datenquelle hinzufügen** zum Starten der **Assistenten zur Datenquellenkonfiguration**.

2. Wählen Sie den Typ der Datenquelle, die auf die Sie mit der verbunden werden.

     ![Assistent zum Konfigurieren von Datenquellen](../data-tools/media/data-source-configuration-wizard.png)

3. Wählen Sie Datenbanken aus, die die Datenquelle für das Dataset.

     ![Wählen Sie die Datenquelle eine Verbindung](../data-tools/media/data-source-choose-a-connection.png)

4. Wählen Sie die Tabellen (oder einzelne Spalten), gespeicherte Prozeduren, Funktionen und Sichten aus der Datenbank, die im Dataset dargestellt werden sollen.

     ![Datenbankobjekte auswählen](../data-tools/media/raddata-chose-objects.png)

5. Klicken Sie auf **Fertig stellen**.

   Das Dataset wird als Knoten in **Projektmappen-Explorer**.

   ![Datasets im Projektmappen-Explorer](../data-tools/media/dataset-in-solution-explorer.png)

6. Klicken Sie auf der datasetknoten in **Projektmappen-Explorer** , öffnen Sie das Dataset in den **DataSet-Designer**. Jede Tabelle im Dataset verfügt über eine zugeordnete `TableAdapter` -Objekt, das unten dargestellt wird. Der Tabellenadapter wird das Dataset zu füllen und optional zum Senden von Befehlen in der Datenbank verwendet.

   ![DataSet-Designer](../data-tools/media/dataset-designer.png)

7. Die Relation-Zeilen, die Tabellen verbinden darstellen in der Datenbank definierte tabellenbeziehungen. Standardmäßig werden fremdschlüsseleinschränkungen in einer Datenbank werden als nur eine Beziehung dargestellt, mit dem Update und Löschen von Regeln, die auf "None" festgelegt. Normalerweise ist dies erwünscht. Sie können jedoch klicken, die Zeilen aus, um die **Beziehung** Dialogfeld, in dem Sie das Verhalten hierarchischer Aktualisierungen ändern können. Weitere Informationen finden Sie unter [Beziehungen in Datasets](../data-tools/relationships-in-datasets.md) und [hierarchische Aktualisierung](../data-tools/hierarchical-update.md).

     ![Beziehung der DataSet-Dialogfeld](../data-tools/media/raddata-relation-dialog.png)

8. Klicken Sie auf Tabellen, Tabellenadapters oder Name der Spalte in einer Tabelle zum Anzeigen der Eigenschaften in der **Eigenschaften** Fenster. Sie können einige der Werte hier ändern. Denken Sie daran, dass Sie das Dataset, die nicht in der Quelldatenbank ändern.

     ![Eigenschaften des DataSet-Spalte](../data-tools/media/dataset-column-properties.png)

9. Sie können neue Tabellen oder Tabellenadapter hinzufügen, auf das Dataset, neue Abfragen für die vorhandene Tabellenadapter hinzufügen, oder geben Sie neue Beziehungen zwischen Tabellen ziehen Sie Elemente aus der **Toolbox** Registerkarte. Auf dieser Registerkarte wird angezeigt, wenn die **DataSet-Designer** im Fokus ist.

     ![DataSet-Toolbox](../data-tools/media/raddata-dataset-toolbox.png)

Als Nächstes empfiehlt es sich um anzugeben, wie das Dataset mit Daten aufzufüllen. Sie verwenden, die **TableAdapter-Konfigurations-Assistenten**. Weitere Informationen finden Sie unter [Füllen von Datasets mit TableAdapters](../data-tools/fill-datasets-by-using-tableadapters.md).

## <a name="add-a-database-table-or-other-object-to-an-existing-dataset"></a>Fügen Sie einer Datenbanktabelle oder ein anderes Objekt zu einem vorhandenen Dataset hinzu.

Diese Prozedur zeigt, wie Sie eine Tabelle aus der gleichen Datenbank hinzufügen, mit denen Sie zunächst das Dataset zu erstellen.

1. Klicken Sie auf der datasetknoten in **Projektmappen-Explorer** , schalten Sie die **DataSet-Designer** in den Fokus.

2. Klicken Sie auf die **Datenquellen** Registerkarte am linken Rand von Visual Studio oder Typ **Datenquellen** in die **Schnellstart** Feld.

3. Mit der rechten Maustaste des datasetknoten, und wählen Sie **Datenquelle mit Assistenten konfigurieren**.

     ![Data Source-Kontextmenü](../data-tools/media/data-source-context-menu.png)

4. Mithilfe des Assistenten geben Sie die zusätzlichen Tabellen, gespeicherten Prozeduren oder andere Datenbankobjekte, die dem Dataset hinzugefügt.

## <a name="add-a-stand-alone-data-table-to-a-dataset"></a>Hinzufügen einer eigenständigen Datentabelle zu einem dataset

1. Öffnen Sie das Dataset im **DataSet-Designer**.

2. Ziehen Sie eine <xref:System.Data.DataTable> -Klasse aus der **DataSet** Registerkarte die **Toolbox** auf die **Dataset-Designer**.

3. Fügen Sie Spalten hinzu, um die Datentabelle zu definieren. Mit der rechten Maustaste auf die Tabelle, und wählen Sie **hinzufügen** > **Spalte**. Verwenden der **Eigenschaften** Fenster aus, um den Datentyp der Spalte und einen Schlüssel bei Bedarf festgelegt.

Eigenständige Tabellen müssen implementieren `Fill` Logik in eigenständige Tabellen, damit Sie mit Daten gefüllt werden können. Informationen zum Füllen eigenständiger Datentabellen finden Sie unter [Auffüllen eines Datasets mit einen "DataAdapter"](/dotnet/framework/data/adonet/populating-a-dataset-from-a-dataadapter).

## <a name="see-also"></a>Siehe auch

- [Datasettools in Visual Studio](../data-tools/dataset-tools-in-visual-studio.md)
- [Beziehungen in Datasets](../data-tools/relationships-in-datasets.md)
- [Hierarchische Aktualisierung](../data-tools/hierarchical-update.md)
- [Füllen von Datasets mit TableAdapters](../data-tools/fill-datasets-by-using-tableadapters.md)