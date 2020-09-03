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
author: jillre
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: 3c84105387c708fa16e0b1d5c3294ef909466524
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 09/02/2020
ms.locfileid: "72631203"
---
# <a name="create-and-configure-datasets-in-visual-studio"></a>Erstellen und Konfigurieren von Datasets in Visual Studio
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Ein *DataSet* ist ein Satz von Objekten, die Daten aus einer Datenbank im Arbeitsspeicher speichern und die Änderungs Nachverfolgung unterstützen, um Erstellungs-, Lese-, Aktualisierungs-und Löschvorgänge (CRUD) für diese Daten zu ermöglichen, ohne dass immer eine Verbindung mit der Datenbank hergestellt werden muss. Datasets wurden für einfache *Formulare über Daten* Geschäftsanwendungen entworfen. Bei neuen Anwendungen sollten Sie die Verwendung von Entity Framework zum Speichern und modellieren von Daten im Arbeitsspeicher in Erwägung gezogen. Um mit Datasets arbeiten zu können, sollten Sie über grundlegende Kenntnisse der Datenbankkonzepte verfügen.

 Sie erstellen eine typisierte <xref:System.Data.DataSet> Klasse in Visual Studio zur Entwurfszeit mithilfe des **Assistenten zum Konfigurieren von Datenquellen**. Informationen zum programmgesteuerten Erstellen von Datasets finden Sie unter [Erstellen eines Datasets](https://msdn.microsoft.com/library/57629d8f-393e-4677-8b83-29ffde27f5fc).

## <a name="create-a-new-dataset-by-using-the-data-source-configuration-wizard"></a>Erstellen eines neuen Datasets mit dem Assistenten zum Konfigurieren von Datenquellen

1. Klicken Sie im Menü **Projekt** auf **neue Datenquelle hinzufügen** , um den **Assistenten zum Konfigurieren von Datenquellen**zu starten.

2. Wählen Sie den Typ der Datenquelle aus, mit der eine Verbindung hergestellt werden soll.

     ![Assistent zum Konfigurieren von Datenquellen](../data-tools/media/data-source-configuration-wizard.png "Assistent zum Konfigurieren von Datenquellen")

3. Wählen Sie für Datenbanken die Datenbank oder die Datenbanken aus, die als Datenquelle für das DataSet verwendet werden sollen.

     ![Datenquelle wählen Sie eine Verbindung aus.](../data-tools/media/data-source-choose-a-connection.png "Datenquelle wählen Sie eine Verbindung aus.")

4. Wählen Sie die Tabellen (oder einzelne Spalten), gespeicherte Prozeduren, Funktionen und Sichten aus der Datenbank aus, die im Dataset dargestellt werden soll.

     ![Datenbankobjekte auswählen](../data-tools/media/raddata-chose-objects.png "raddata hat Objekte ausgewählt.")

5. Klicken Sie auf **Fertig stellen**.

6. Das DataSet wird in **Projektmappen-Explorer**als Knoten angezeigt:

     ![DataSet in Projektmappen-Explorer](../data-tools/media/dataset-in-solution-explorer.png "DataSet in Projektmappen-Explorer")

     Klicken Sie auf diesen Knoten, und das DataSet wird im **DataSet-Designer**angezeigt. Beachten Sie, dass jeder Tabelle im Dataset ein zugeordnetes TableAdapter-Objekt zugeordnet ist, das unten dargestellt wird. Der Tabellen Adapter wird verwendet, um das DataSet zu füllen und optional Befehle an die Datenbank zu senden.

     ![DataSet-Designer](../data-tools/media/dataset-designer.png "DataSet-Designer")

7. Die Beziehungs Linien, die die Tabellen verbinden, stellen Tabellen Beziehungen dar, wie in der Datenbank definiert. Foreign Key-Einschränkungen in einer Datenbank werden standardmäßig nur als Beziehung dargestellt, wobei die Update-und Löschregeln auf None festgelegt sind. Dies ist in der Regel das, was Sie möchten. Sie können jedoch auf die Zeilen klicken, um das **Beziehungs** Dialogfeld aufzurufenden, in dem Sie das Verhalten von hierarchischen Updates ändern können. Weitere Informationen finden Sie unter [Beziehungen in Datasets](../data-tools/relationships-in-datasets.md) und [hierarchische Aktualisierung](../data-tools/hierarchical-update.md).

     ![Dialogfeld "datasetbeziehung"](../data-tools/media/raddata-relation-dialog.png "Dialogfeld ' Raddaten Beziehung '")

8. Klicken Sie in einer Tabelle auf eine Tabelle, einen Tabellen Adapter oder einen Spaltennamen, um die zugehörigen Eigenschaften im **Eigenschaften** Fenster anzuzeigen. Einige der Werte können hier geändert werden. Denken Sie daran, dass Sie das Dataset ändern, nicht die Quelldatenbank.

     ![DataSet-Spalten Eigenschaften](../data-tools/media/dataset-column-properties.png "DataSet-Spalten Eigenschaften")

9. Sie können dem DataSet neue Tabellen oder Tabellen Adapter hinzufügen oder neue Abfragen für vorhandene Tabellen Adapter hinzufügen oder neue Beziehungen zwischen Tabellen angeben, indem Sie diese Elemente von der Registerkarte **Toolbox** ziehen. Diese Registerkarte wird angezeigt, wenn der **DataSet-Designer** den Fokus hat.

     ![DataSet-Toolbox](../data-tools/media/raddata-dataset-toolbox.png "raddata-DataSet-Toolbox")

10. Als nächstes möchten Sie wahrscheinlich angeben, wie das DataSet mit Daten aufgefüllt werden soll. Dazu verwenden Sie den **TableAdapter-Konfigurations-Assistenten**. Weitere Informationen finden Sie unter [Füllen von Datasets mit TableAdapters](../data-tools/fill-datasets-by-using-tableadapters.md) .

## <a name="add-a-database-table-or-other-object-to-an-existing-dataset"></a>Hinzufügen einer Datenbanktabelle oder eines anderen Objekts zu einem vorhandenen DataSet
 In diesem Verfahren wird gezeigt, wie Sie eine Tabelle aus derselben Datenbank hinzufügen, die Sie zuvor zum Erstellen des Datasets verwendet haben.

1. Klicken Sie in **Projektmappen-Explorer** auf den Datasetknoten, um den DataSet-Designer in den Fokus zu bringen.

2. Klicken Sie im linken Rand von Visual Studio auf die Registerkarte **Datenquellen** , oder geben Sie `Data Sources` in **Quick Launch**ein.

3. Klicken Sie mit der rechten Maustaste auf den Knoten DataSet, und wählen Sie **Datenquelle mit Assistent konfigurieren** aus.

     ![Datenquellen-Kontextmenü](../data-tools/media/data-source-context-menu.png "Datenquellen-Kontextmenü")

4. Verwenden Sie den Assistenten, um anzugeben, welche zusätzlichen Tabellen oder gespeicherten Prozeduren oder andere Datenbankobjekte dem DataSet hinzugefügt werden sollen.

## <a name="add-a-stand-alone-data-table-to-a-dataset"></a>Hinzufügen einer eigenständigen Datentabelle zu einem DataSet

1. Öffnen Sie das Dataset im **DataSet-Designer**.

2. Ziehen Sie eine <xref:System.Data.DataTable> Klasse von der Registerkarte **DataSet** der **Toolbox** auf den **DataSet-Designer**.

3. Fügen Sie Spalten hinzu, um die Datentabelle zu definieren. Weitere Informationen finden Sie unter Gewusst [wie: Hinzufügen von Spalten zu einer Daten](https://msdn.microsoft.com/library/8ca21f77-b99a-47a7-a656-7cfd7a1bd9df)Tabelle.

4. Eigenständige Tabellen müssen `Fill` Logik in eigenständigen Tabellen implementieren, damit Sie Sie mit Daten füllen können. Informationen zum Auffüllen von eigenständigen Datentabellen finden Sie unter Auffüllen [eines Datasets aus einem DataAdapter](https://msdn.microsoft.com/library/3fa0ac7d-e266-4954-bfac-3fbe2f913153).
