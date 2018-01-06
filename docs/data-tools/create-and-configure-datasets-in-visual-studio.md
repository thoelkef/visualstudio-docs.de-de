---
title: Erstellen und Konfigurieren von Datasets in Visual Studio | Microsoft Docs
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- typed datasets, creating
- datasets, creating
- datasets, configuring
author: gewarren
ms.author: gewarren
manager: ghogen
ms.technology: vs-data-tools
ms.workload: data-storage
ms.openlocfilehash: da81d141e453e0106d329565338f7893b4fad758
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 12/22/2017
---
# <a name="create-and-configure-datasets-in-visual-studio"></a>Erstellen und Konfigurieren von Datasets in Visual Studio

Ein *Dataset* ist ein Satz von Objekten, die Daten aus einer Datenbank im Arbeitsspeicher speichern und unterstützen, änderungsnachverfolgung, zum Aktivieren zu erstellen, lesen, aktualisieren und Löschvorgänge (CRUD) für diese Daten, ohne dass Sie immer mit der Datenbank verbunden sein müssen. Für einfache Datasets entworfen wurden *Formulare über Daten* Geschäftsanwendungen. Für neue Anwendungen sollten Sie in Erwägung ziehen, Entity Framework zum Speichern und Modellieren von Daten im Arbeitsspeicher zu verwenden. Um mit Datasets arbeiten, benötigen Sie Grundkenntnisse von Datenbankkonzepten.

Erstellen Sie eine typisierte <xref:System.Data.DataSet> Klasse in Visual Studio zur Entwurfszeit mithilfe der **Datenquellen Konfigurations-Assistenten**. Informationen zum programmgesteuerten Erstellen von Datasets finden Sie unter [erstellen ein DataSet (ADO.NET)](/dotnet/framework/data/adonet/dataset-datatable-dataview/creating-a-dataset).

## <a name="create-a-new-dataset-by-using-the-data-source-configuration-wizard"></a>Erstellen Sie ein neues Dataset mit dem Konfigurations-Assistenten

1.  Auf der **Projekt** Menü klicken Sie auf **neue Datenquelle hinzufügen** zum Starten der **Datenquellen Konfigurations-Assistenten**.

2.  Wählen Sie den Typ der Datenquelle, die Sie mit herstellen möchte.

     ![Datenquellen Konfigurationsassistenten](../data-tools/media/data-source-configuration-wizard.png "Datenquellen Konfigurationsassistenten")

3.  Wählen Sie für Datenbanken Datenbanken, die die Datenquelle für das Dataset ein.

     ![Auswählen der Datenquelle eine Verbindung](../data-tools/media/data-source-choose-a-connection.png "-Datenquelle wählen Sie eine Verbindung")

4.  Wählen Sie die Tabellen (oder einzelne Spalten), gespeicherte Prozeduren, Funktionen und Sichten aus der Datenbank, die im Dataset dargestellt werden soll.

     ![Wählen Sie Datenbankobjekte](../data-tools/media/raddata-chose-objects.png "Raddata ausgewählten Objekte")

5.  Klicken Sie auf **Fertig stellen**.

6.  Das Dataset wird als Knoten in **Projektmappen-Explorer**:

     ![Datasets im Projektmappen-Explorer](../data-tools/media/dataset-in-solution-explorer.png "Datasets im Projektmappen-Explorer")

     Klicken Sie auf diesem Knoten und das Dataset wird in der **DataSet-Designer**. Beachten Sie, dass jede Tabelle im Dataset ein zugeordneten TableAdapter-Objekt verfügt, die im unteren Bereich dargestellt wird. Der Tabellenadapter wird an das Dataset zu füllen und optional zum Senden von Befehlen in der Datenbank verwendet.

     ![DataSet-Designer](../data-tools/media/dataset-designer.png "DataSet-Designer")

7.  Die Relation-Zeilen, die Tabellen verbinden darstellen tabellenbeziehungen, wie in der Datenbank definiert. Standardmäßig foreign Key-Einschränkungen in einer Datenbank werden als nur eine Beziehung dargestellt, mit dem Aktualisieren und Löschen von Regeln, die auf none festgelegt. In der Regel ist, was Sie möchten. Sie können jedoch klicken, die Zeilen aus, um die **Beziehung** Dialogfeld, in dem Sie das Verhalten hierarchischer Aktualisierungen ändern können. Weitere Informationen finden Sie unter [Beziehungen in Datasets](../data-tools/relationships-in-datasets.md) und [hierarchische Aktualisierung](../data-tools/hierarchical-update.md).

     ![DataSet-Beziehung Dialogfeld](../data-tools/media/raddata-relation-dialog.png "Raddata Beziehung Dialogfeld")

8.  Klicken Sie auf eine Tabelle, Tabellenadapters oder Spaltennamen in einer Tabelle, um seine Eigenschaften im finden Sie unter der **Eigenschaften** Fenster. Sie können einige der Werte hier ändern. Bedenken Sie, dass Sie das Dataset, die nicht in der Quelldatenbank gewählt haben.

     ![DataSet-Spalteneigenschaften](../data-tools/media/dataset-column-properties.png "DataSet Spalteneigenschaften")

9. Sie können neue Tabellen oder TableAdapter zum Dataset hinzufügen oder fügen Sie neue Abfragen für vorhandene TableAdapter, oder geben Sie neue Beziehungen zwischen Tabellen ziehen Sie diese Elemente aus der **Toolbox** Registerkarte. Auf dieser Registerkarte wird angezeigt, wenn die **DataSet-Designer** im Fokus ist.

     ![DataSet-Toolbox](../data-tools/media/raddata-dataset-toolbox.png "Raddata Dataset-Toolbox")

10. Als Nächstes möchten Sie möglicherweise angeben, wie das Dataset mit Daten zu füllen. Verwenden Sie dazu die **TableAdapter-Konfigurations-Assistenten**. Weitere Informationen finden Sie unter [Datasets mit TableAdapters füllen](../data-tools/fill-datasets-by-using-tableadapters.md).

## <a name="add-a-database-table-or-other-object-to-an-existing-dataset"></a>Hinzufügen einer Datenbanktabelle oder ein anderes Objekt zu einem vorhandenen dataset

Diese Prozedur zeigt, wie eine Tabelle aus der gleichen Datenbank hinzuzufügen, mit denen Sie zuerst das Dataset zu erstellen.

1.  Klicken Sie auf der datasetknoten in **Projektmappen-Explorer** auf den Dataset-Designer den Fokus zu bringen.

2.  Klicken Sie auf die **Datenquellen** Registerkarte am linken Rand von Visual Studio, oder geben Sie `Data Sources` in **Schnellstart**.

3.  Mit der rechten Maustaste des Dataset-Knotens, und wählen Sie **Datenquelle konfigurieren, mit dem Assistenten**.

     ![Datenquelle-Kontextmenü](../data-tools/media/data-source-context-menu.png "Datenquelle-Kontextmenü")

4.  Mithilfe des Assistenten an, welche zusätzlichen Tabellen oder gespeicherte Prozeduren oder anderen Datenbankobjekt, das Dataset hinzu.

## <a name="add-a-stand-alone-data-table-to-a-dataset"></a>Hinzufügen einer eigenständigen Datentabelle zu einem dataset

1.  Öffnen Sie das Dataset in die **Dataset-Designer**.

2.  Ziehen Sie eine <xref:System.Data.DataTable> -Klasse aus den **DataSet** auf der Registerkarte die **Toolbox** auf die **Dataset-Designer**.

3.  Fügen Sie Spalten hinzu, um die Datentabelle zu definieren. Mit der rechten Maustaste auf die Tabelle, und wählen Sie **hinzufügen > Spalte**. Verwenden der **Eigenschaften** Fenster aus, um den Datentyp der Spalte und einen Schlüssel bei Bedarf festgelegt.

4.  Eigenständige Tabellen müssen implementieren `Fill` Logik in eigenständige Tabellen, damit Sie mit Daten gefüllt werden können. Informationen zum Füllen von eigenständigen Datentabellen finden Sie unter [Auffüllen eines Datasets mit "DataAdapter"](/dotnet/framework/data/adonet/populating-a-dataset-from-a-dataadapter).

## <a name="see-also"></a>Siehe auch

[Datasettools in Visual Studio](../data-tools/dataset-tools-in-visual-studio.md)