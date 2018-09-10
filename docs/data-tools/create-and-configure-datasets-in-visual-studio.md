---
title: Erstellen und Konfigurieren von Datasets in Visual Studio
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- typed datasets, creating
- datasets, creating
- datasets, configuring
author: gewarren
ms.author: gewarren
manager: douge
ms.prod: visual-studio-dev15
ms.technology: vs-data-tools
ms.workload:
- data-storage
ms.openlocfilehash: a65c1960e1648dce3bb8ff40d1dd6c50534934ff
ms.sourcegitcommit: 3a11feebad45a0dd4ac45efcbfdf172fce46e1de
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 08/07/2018
ms.locfileid: "39582231"
---
# <a name="create-and-configure-datasets-in-visual-studio"></a>Erstellen und Konfigurieren von Datasets in Visual Studio

Ein Dataset ist ein Satz von Objekten, die Speichern von Daten aus einer Datenbank im Arbeitsspeicher und unterstützen das Nachverfolgen von Änderungen zu erstellen, lesen, aktualisieren und löschen (CRUD) für diese Daten ohne die Notwendigkeit, immer mit der Datenbank verbunden werden. DataSets wurden entwickelt, für einfache *Formulare über Daten* Geschäftsanwendungen. Für neue Anwendungen sollten Sie in Betracht ziehen, Entity Framework zum Speichern und Modellieren von Daten im Arbeitsspeicher zu verwenden. Um mit Datasets arbeiten, sollten Sie über Grundkenntnisse der Konzepte der Datenbank verfügen.

Sie erstellen Sie eine typisierte <xref:System.Data.DataSet> Klasse in Visual Studio zur Entwurfszeit mithilfe der **Assistenten zur Datenquellenkonfiguration**. Informationen zum programmgesteuerten Erstellen von Datasets finden Sie unter [Erstellen eines Datasets (ADO.NET)](/dotnet/framework/data/adonet/dataset-datatable-dataview/creating-a-dataset).

## <a name="create-a-new-dataset-by-using-the-data-source-configuration-wizard"></a>Erstellen Sie ein neues Dataset mit dem Konfigurations-Assistenten

1.  Auf der **Projekt** Menü klicken Sie auf **neue Datenquelle hinzufügen** zum Starten der **Assistenten zur Datenquellenkonfiguration**.

2.  Wählen Sie den Typ der Datenquelle, die Verbindung hergestellt werden soll.

     ![Assistent zum Konfigurieren von Datenquellen](../data-tools/media/data-source-configuration-wizard.png)

3.  Wählen Sie Datenbanken aus, die die Datenquelle für das Dataset.

     ![Wählen Sie die Datenquelle eine Verbindung](../data-tools/media/data-source-choose-a-connection.png)

4.  Wählen Sie die Tabellen (oder einzelne Spalten), gespeicherte Prozeduren, Funktionen und Sichten aus der Datenbank, die im Dataset dargestellt werden sollen.

     ![Wählen Sie Datenbankobjekte aus](../data-tools/media/raddata-chose-objects.png)

5.  Klicken Sie auf **Fertig stellen**.

6.  Das Dataset wird als Knoten in **Projektmappen-Explorer**.

     ![Datasets im Projektmappen-Explorer](../data-tools/media/dataset-in-solution-explorer.png)

     Klicken Sie auf diesem Knoten aus, und das Dataset wird angezeigt, der **DataSet-Designer**. Beachten Sie, dass jede Tabelle im Dataset eine zugeordnete `TableAdapter` -Objekt, das unten dargestellt wird. Der Tabellenadapter wird das Dataset zu füllen und optional zum Senden von Befehlen in der Datenbank verwendet.

     ![DataSet-Designer](../data-tools/media/dataset-designer.png)

7.  Die Relation-Zeilen, die Tabellen verbinden darstellen in der Datenbank definierte tabellenbeziehungen. Standardmäßig werden fremdschlüsseleinschränkungen in einer Datenbank werden als nur eine Beziehung dargestellt, mit dem Update und Löschen von Regeln, die auf "None" festgelegt. Normalerweise ist dies erwünscht. Sie können jedoch klicken, die Zeilen aus, um die **Beziehung** Dialogfeld, in dem Sie das Verhalten hierarchischer Aktualisierungen ändern können. Weitere Informationen finden Sie unter [Beziehungen in Datasets](../data-tools/relationships-in-datasets.md) und [hierarchische Aktualisierung](../data-tools/hierarchical-update.md).

     ![Beziehung der DataSet-Dialogfeld](../data-tools/media/raddata-relation-dialog.png)

8.  Klicken Sie auf Tabellen, Tabellenadapters oder Name der Spalte in einer Tabelle zum Anzeigen der Eigenschaften in der **Eigenschaften** Fenster. Sie können einige der Werte hier ändern. Denken Sie daran, dass Sie das Dataset, die nicht in der Quelldatenbank ändern.

     ![Eigenschaften des DataSet-Spalte](../data-tools/media/dataset-column-properties.png)

9. Sie können neue Tabellen oder Tabellenadapter hinzufügen, auf das Dataset, neue Abfragen für die vorhandene Tabellenadapter hinzufügen, oder geben Sie neue Beziehungen zwischen Tabellen ziehen Sie Elemente aus der **Toolbox** Registerkarte. Auf dieser Registerkarte wird angezeigt, wenn die **DataSet-Designer** im Fokus ist.

     ![DataSet-Toolbox](../data-tools/media/raddata-dataset-toolbox.png)

10. Als Nächstes sollten Sie angeben, wie das Dataset mit Daten aufzufüllen. Sie verwenden, die **TableAdapter-Konfigurations-Assistenten**. Weitere Informationen finden Sie unter [Füllen von Datasets mit TableAdapters](../data-tools/fill-datasets-by-using-tableadapters.md).

## <a name="add-a-database-table-or-other-object-to-an-existing-dataset"></a>Fügen Sie einer Datenbanktabelle oder ein anderes Objekt zu einem vorhandenen Dataset hinzu.

Diese Prozedur zeigt, wie Sie eine Tabelle aus der gleichen Datenbank hinzufügen, mit denen Sie zunächst das Dataset zu erstellen.

1.  Klicken Sie auf der datasetknoten in **Projektmappen-Explorer** , Dataset-Designer den Fokus zu öffnen.

2.  Klicken Sie auf die **Datenquellen** Registerkarte am linken Rand von Visual Studio oder Typ **Datenquellen** in die **Schnellstart** Feld.

3.  Mit der rechten Maustaste des datasetknoten, und wählen Sie **Datenquelle mit Assistenten konfigurieren**.

     ![Data Source-Kontextmenü](../data-tools/media/data-source-context-menu.png)

4.  Mithilfe des Assistenten geben Sie die zusätzlichen Tabellen oder gespeicherte Prozeduren oder anderen Database-Objekt, das Dataset hinzu.

## <a name="add-a-stand-alone-data-table-to-a-dataset"></a>Hinzufügen einer eigenständigen Datentabelle zu einem dataset

1.  Öffnen Sie das Dataset in den **Dataset-Designer**.

2.  Ziehen Sie eine <xref:System.Data.DataTable> -Klasse aus der **DataSet** Registerkarte die **Toolbox** auf die **Dataset-Designer**.

3.  Fügen Sie Spalten hinzu, um die Datentabelle zu definieren. Mit der rechten Maustaste auf die Tabelle, und wählen Sie **hinzufügen** > **Spalte**. Verwenden der **Eigenschaften** Fenster aus, um den Datentyp der Spalte und einen Schlüssel bei Bedarf festgelegt.

4.  Eigenständige Tabellen müssen implementieren `Fill` Logik in eigenständige Tabellen, damit Sie mit Daten gefüllt werden können. Informationen zum Füllen eigenständiger Datentabellen finden Sie unter [Auffüllen eines Datasets mit einen "DataAdapter"](/dotnet/framework/data/adonet/populating-a-dataset-from-a-dataadapter).

## <a name="see-also"></a>Siehe auch

- [Datasettools in Visual Studio](../data-tools/dataset-tools-in-visual-studio.md)