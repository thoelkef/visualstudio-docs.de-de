---
title: Aufteilen von DataSets und TableAdapters in verschiedene Projekte
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- TableAdapters, n-tier applications
- n-tier applications, separating Datasets and TableAdapters
ms.assetid: f66a3940-6227-46af-a930-9177f425f4fd
author: gewarren
ms.author: gewarren
manager: jillfra
ms.workload:
- data-storage
ms.openlocfilehash: 3eb9e8035dd8fa4b6a3143341e7be9959254452e
ms.sourcegitcommit: 21d667104199c2493accec20c2388cf674b195c3
ms.translationtype: MTE95
ms.contentlocale: de-DE
ms.lasthandoff: 02/08/2019
ms.locfileid: "55927658"
---
# <a name="separate-datasets-and-tableadapters-into-different-projects"></a>Aufteilen von DataSets und TableAdapters in verschiedene Projekte
Typisierte Datasets wurden weiterentwickelt, damit die [TableAdapters](create-and-configure-tableadapters.md) und Dataset-Klassen in separaten Projekten generiert werden können. Dies ermöglicht eine bequeme Trennung der Anwendungsebenen und die Erzeugung von N-Tier-Datenanwendungen.

Das folgende Verfahren beschreibt den Prozess der Verwendung der **Dataset-Designer** zum Generieren von Dataset-Code in einem Projekt, das aus dem Projekt getrennt ist, die die generierten TableAdapter-Code enthält.

## <a name="separate-datasets-and-tableadapters"></a>Separate Datasets und TableAdapters
Wenn Sie Dataset-Code von TableAdapter-Code zu trennen, muss das Projekt, das den Dataset-Code enthält, in der aktuellen Projektmappe befinden. Wenn dieses Projekt nicht in der aktuellen Projektmappe befindet, nicht mehr verfügbar ist, in der **DataSet-Projekt** Liste der **Eigenschaften** Fenster.

[!INCLUDE[note_settings_general](../data-tools/includes/note_settings_general_md.md)]

#### <a name="to-separate-the-dataset-into-a-different-project"></a>So separieren Sie das DataSet in ein anderes Projekt

1.  Öffnen Sie eine Projektmappe, die ein Dataset (*XSD*-Datei) enthält.

    > [!NOTE]
    >  Wenn die Projektmappe das Projekt keinen ist in dem Sie den Dataset-Code zu trennen möchten, erstellen Sie das Projekt oder fügen Sie ein vorhandenes Projekt zur Projektmappe hinzu.

2.  Doppelklicken Sie im **Projektmappen-Explorer** auf eine typisierte Dataset-Datei (*XSD*-Datei), um das Dataset mit dem **DataSet-Designer** zu öffnen.

3.  Wählen Sie einen leeren Bereich der **Dataset-Designer**.

4.  In der **Eigenschaften** Fenster Suchen der **DataSet-Projekt** Knoten.

5.  In der **DataSet-Projekt** Liste, wählen Sie den Namen des Projekts, in dem Sie den Dataset-Code generieren möchten.

     Nachdem Sie das Projekt auswählen, in dem Sie den Dataset-Code generieren möchten, die **Datasetdatei** -Eigenschaft mit einem standardmäßigen Dateinamen aufgefüllt. Sie können diesen Namen bei Bedarf ändern. Wenn Sie den Dataset-Code in einem bestimmten Verzeichnis generieren möchten, können Sie in der **Projektordner**-Eigenschaft den Namen des Ordners angeben.

    > [!NOTE]
    >  Bei einer Abtrennung der Datasets und TableAdapters (durch Festlegen der **DataSet-Projekt** Eigenschaft), vorhandene partielle Dataset-Klassen im Projekt wird nicht automatisch verschoben werden. Vorhandene partielle Dataset-Klassen müssen manuell in der Dataset-Projekt verschoben werden.

6.  Speichern Sie das DataSet.

     Der Dataset-Code wird generiert, in dem ausgewählten Projekt im der **DataSet-Projekt** -Eigenschaft, und die **TableAdapter** Code in das aktuelle Projekt generiert wird.

Nachdem Sie das Dataset und TableAdapter-Code trennen, ist das Ergebnis standardmäßig eine separate Klassendatei in jedem Projekt. Das ursprüngliche Projekt enthält eine Datei namens *dem Namen DatasetName.Designer.vb* (oder *DatasetName.Designer.cs*), die den TableAdapter-Code enthält. Das Projekt, das angegeben die **Dataset-Projekt** Eigenschaft verfügt über eine Datei namens *dem Namen DatasetName.DataSet.Designer.vb* (oder *DatasetName.DataSet.Designer.cs*), enthält den Dataset-Code.

> [!NOTE]
>  Um die generierte Klassendatei anzuzeigen, wählen Sie das Dataset oder den TableAdapter-Projekt. Klicken Sie auf **Projektmappen-Explorer**Option **alle Dateien anzeigen**.

## <a name="see-also"></a>Siehe auch

- [Übersicht über n-schichtige Datenanwendungen](../data-tools/n-tier-data-applications-overview.md)
- [Exemplarische Vorgehensweise: Erstellen einer n schichtigen Datenanwendung](../data-tools/walkthrough-creating-an-n-tier-data-application.md)
- [Hierarchische Aktualisierung](../data-tools/hierarchical-update.md)
- [Zugreifen auf Daten in Visual Studio](../data-tools/accessing-data-in-visual-studio.md)
- [ADO.NET](/dotnet/framework/data/adonet/index)