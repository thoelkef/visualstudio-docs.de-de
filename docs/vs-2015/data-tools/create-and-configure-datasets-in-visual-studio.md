---
title: Erstellen und Konfigurieren von Datasets
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
- typed datasets, creating
- datasets [Visual Basic], creating
ms.assetid: 58f33b43-24e1-43b1-b08b-b74329960bd6
caps.latest.revision: 39
author: gewarren
ms.author: gewarren
manager: jillfra
ms.openlocfilehash: 0a2930acee9e187f14b87e28190a88195b0bea7a
ms.sourcegitcommit: 53aa5a413717a1b62ca56a5983b6a50f7f0663b3
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 04/17/2019
ms.locfileid: "59656247"
---
# <a name="create-and-configure-datasets-in-visual-studio"></a>Erstellen und Konfigurieren von Datasets in Visual Studio
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Ein *Dataset* ist ein Satz von Objekten, die Daten aus einer Datenbank im Arbeitsspeicher speichern und Aktivieren der änderungsnachverfolgung zu unterstützen erstellen, lesen, aktualisieren und löschen (CRUD) für diese Daten ohne die Notwendigkeit, immer mit der Datenbank verbunden werden. DataSets wurden entwickelt, für einfache *Formulare über Daten* Geschäftsanwendungen. Für neue Anwendungen sollten Sie in Betracht ziehen, Entity Framework zum Speichern und Modellieren von Daten im Arbeitsspeicher zu verwenden. Um mit Datasets arbeiten, sollten Sie über Grundkenntnisse der Konzepte der Datenbank verfügen.

 Sie erstellen Sie eine typisierte <xref:System.Data.DataSet> Klasse in Visual Studio zur Entwurfszeit mithilfe der **Assistenten zur Datenquellenkonfiguration**. Informationen zum programmgesteuerten Erstellen von Datasets finden Sie unter [Erstellen eines Datasets](http://msdn.microsoft.com/library/57629d8f-393e-4677-8b83-29ffde27f5fc).

## <a name="create-a-new-dataset-by-using-the-data-source-configuration-wizard"></a>Erstellen Sie ein neues Dataset mit dem Konfigurations-Assistenten

1.  Auf der **Projekt** Menü klicken Sie auf **neue Datenquelle hinzufügen** zum Starten der **Assistenten zur Datenquellenkonfiguration**.

2.  Wählen Sie den Typ der Datenquelle, die Sie eine Verbindung herstellen werden.

     ![Datenquellen-Assistenten](../data-tools/media/data-source-configuration-wizard.png "Datenquellen-Assistenten")

3.  Wählen Sie für Datenbanken Datenbanken, die die Datenquelle für das Dataset aus.

     ![Wählen Sie die Datenquelle eine Verbindung](../data-tools/media/data-source-choose-a-connection.png "-Datenquelle wählen Sie eine Verbindung")

4.  Wählen Sie die Tabellen (oder einzelne Spalten), gespeicherte Prozeduren, Funktionen und Sichten aus der Datenbank, die im Dataset dargestellt werden sollen.

     ![Wählen Sie Datenbankobjekte](../data-tools/media/raddata-chose-objects.png "Raddata ausgewählten Objekte")

5.  Klicken Sie auf **Fertig stellen**.

6.  Das Dataset wird als Knoten in **Projektmappen-Explorer**:

     ![Datasets im Projektmappen-Explorer](../data-tools/media/dataset-in-solution-explorer.png "DataSet im Projektmappen-Explorer")

     Klicken Sie auf diesem Knoten aus, und das Dataset wird angezeigt, der **DataSet-Designer**. Beachten Sie, dass jede Tabelle im Dataset ein zugeordneten TableAdapter-Objekts, das am unteren Rand dargestellt wird. Der Tabellenadapter wird das Dataset zu füllen und optional zum Senden von Befehlen in der Datenbank verwendet.

     ![DataSet-Designer](../data-tools/media/dataset-designer.png "DataSet-Designer")

7.  Die Relation-Zeilen, die Tabellen verbinden darstellen in der Datenbank definierte tabellenbeziehungen. Standardmäßig werden fremdschlüsseleinschränkungen in einer Datenbank werden als nur eine Beziehung dargestellt, mit dem Update und Löschen von Regeln, die auf "None" festgelegt. Normalerweise ist dies erwünscht. Sie können jedoch klicken, die Zeilen aus, um die **Beziehung** Dialogfeld, in dem Sie das Verhalten hierarchischer Aktualisierungen ändern können. Weitere Informationen finden Sie unter [Beziehungen in Datasets](../data-tools/relationships-in-datasets.md) und [hierarchische Aktualisierung](../data-tools/hierarchical-update.md).

     ![DataSet-Beziehung Dialogfeld](../data-tools/media/raddata-relation-dialog.png "Raddata Beziehung Dialogfeld")

8.  Klicken Sie auf Tabellen, Tabellenadapters oder Name der Spalte in einer Tabelle zum Anzeigen der Eigenschaften in der **Eigenschaften** Fenster. Sie können einige der Werte hier ändern. Denken Sie daran, dass Sie das Dataset, die nicht in der Quelldatenbank ändern.

     ![Eigenschaften des DataSet-Spalte](../data-tools/media/dataset-column-properties.png "Eigenschaften des DataSet-Spalte")

9. Sie können neue Tabellen oder Tabellenadapter hinzufügen, auf das Dataset, neue Abfragen für die vorhandene Tabellenadapter hinzufügen, oder geben Sie neue Beziehungen zwischen Tabellen ziehen Sie Elemente aus der **Toolbox** Registerkarte. Auf dieser Registerkarte wird angezeigt, wenn die **DataSet-Designer** im Fokus ist.

     ![DataSet-Toolbox](../data-tools/media/raddata-dataset-toolbox.png "Raddata Dataset-Toolbox")

10. Als Nächstes sollten Sie angeben, wie das Dataset mit Daten aufzufüllen. Sie verwenden, die **TableAdapter-Konfigurations-Assistenten**. Weitere Informationen finden Sie unter [Füllen von Datasets mit TableAdapters](../data-tools/fill-datasets-by-using-tableadapters.md) .

## <a name="add-a-database-table-or-other-object-to-an-existing-dataset"></a>Fügen Sie einer Datenbanktabelle oder ein anderes Objekt zu einem vorhandenen Dataset hinzu.
 Diese Prozedur zeigt, wie Sie eine Tabelle aus der gleichen Datenbank hinzufügen, mit denen Sie zunächst das Dataset zu erstellen.

1.  Klicken Sie auf der datasetknoten in **Projektmappen-Explorer** , DataSet-Designer den Fokus zu öffnen.

2.  Klicken Sie auf die **Datenquellen** Registerkarte am linken Rand von Visual Studio, oder geben Sie `Data Sources` in **QuickLaunch**.

3.  Mit der rechten Maustaste des datasetknoten, und wählen Sie **Datenquelle mit Assistenten konfigurieren** .

     ![Data Source-Kontextmenü](../data-tools/media/data-source-context-menu.png "Data Source-Kontextmenü")

4.  Mithilfe des Assistenten geben Sie die zusätzlichen Tabellen oder gespeicherte Prozeduren oder anderen Database-Objekt, das Dataset hinzu.

## <a name="add-a-stand-alone-data-table-to-a-dataset"></a>Hinzufügen einer eigenständigen Datentabelle zu einem dataset

1.  Öffnen Sie das Dataset im **DataSet-Designer**.

2.  Ziehen Sie eine <xref:System.Data.DataTable> -Klasse aus der **DataSet** Registerkarte die **Toolbox** auf die **Dataset-Designer**.

3.  Fügen Sie Spalten hinzu, um die Datentabelle zu definieren. Weitere Informationen finden Sie unter [Vorgehensweise: Hinzufügen von Spalten zu einer "DataTable"](http://msdn.microsoft.com/library/8ca21f77-b99a-47a7-a656-7cfd7a1bd9df).

4.  Eigenständige Tabellen müssen implementieren `Fill` Logik in eigenständige Tabellen, damit Sie mit Daten gefüllt werden können. Informationen zum Füllen eigenständiger Datentabellen finden Sie unter [Auffüllen eines Datasets mit einen "DataAdapter"](http://msdn.microsoft.com/library/3fa0ac7d-e266-4954-bfac-3fbe2f913153).
