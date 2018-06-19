---
title: Separate Datasets und TableAdapters in verschiedene Projekte
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- TableAdapters, n-tier applications
- n-tier applications, separating Datasets and TableAdapters
ms.assetid: f66a3940-6227-46af-a930-9177f425f4fd
author: gewarren
ms.author: gewarren
manager: douge
ms.prod: visual-studio-dev15
ms.technology: vs-data-tools
ms.workload:
- data-storage
ms.openlocfilehash: fe7d774a9a5fa1e14cdbcb9c5d730a01fdcdeee9
ms.sourcegitcommit: e13e61ddea6032a8282abe16131d9e136a927984
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/26/2018
ms.locfileid: "31921444"
---
# <a name="separate-datasets-and-tableadapters-into-different-projects"></a>Separate Datasets und TableAdapters in verschiedene Projekte
Typisierte Datasets wurden weiterentwickelt, damit die [TableAdapters](create-and-configure-tableadapters.md) und Dataset-Klassen in separaten Projekten generiert werden können. Dies ermöglicht eine bequeme Trennung der Anwendungsebenen und die Erzeugung von N-Tier-Datenanwendungen.

Das folgende Verfahren beschreibt den Prozess der Verwendung der **Dataset-Designer** zum Generieren von Dataset-Code in einem Projekt, das aus dem Projekt getrennt ist, die die generierten TableAdapter-Code enthält.

## <a name="separate-datasets-and-tableadapters"></a>Separate Datasets und TableAdapters
Wenn Sie Dataset-Code von TableAdapter-Code zu trennen, muss das Projekt, das den Dataset-Code enthält, in der aktuellen Projektmappe befinden. Wenn dieses Projekt nicht in der aktuellen Projektmappe befindet, ist es nicht verfügbar, in der **DataSet-Projekt** in Liste der **Eigenschaften** Fenster.

[!INCLUDE[note_settings_general](../data-tools/includes/note_settings_general_md.md)]

#### <a name="to-separate-the-dataset-into-a-different-project"></a>So separieren Sie das DataSet in ein anderes Projekt

1.  Öffnen Sie eine Projektmappe, die ein DataSet (XSD-Datei) enthält.

    > [!NOTE]
    >  Wenn die Projektmappe das Projekt nicht in dem Sie die Dataset-Code separieren möchten enthalten, erstellen Sie das Projekt oder fügen Sie ein vorhandenes Projekt zur Projektmappe hinzu.

2.  Doppelklicken Sie auf eine typisierte Datasetdatei (XSD-Datei) in **Projektmappen-Explorer** , öffnen Sie das Dataset in die **Dataset-Designer**.

3.  Wählen Sie einen leeren Bereich der **Dataset-Designer**.

4.  In der **Eigenschaften** Fenster, suchen Sie die **DataSet-Projekt** Knoten.

5.  In der **DataSet-Projekt** Liste, wählen Sie den Namen des Projekts, in dem Sie den Dataset-Code generieren möchten.

     Nachdem Sie das Projekt auswählen, in dem Sie den Dataset-Code generieren möchten, die **Datasetdatei** Eigenschaft mit einem Standardnamen für die Datei gefüllt ist. Sie können diesen Namen bei Bedarf ändern. Darüber hinaus, wenn Sie den Dataset-Code in einem bestimmten Verzeichnis generieren möchten, legen Sie die **Projektordner** -Eigenschaft auf den Namen eines Ordners.

    > [!NOTE]
    >  Beim Trennen von Datasets und TableAdaptern (durch Festlegen der **DataSet-Projekt** Eigenschaft), vorhandene partielle Dataset-Klassen im Projekt wird nicht automatisch verschoben werden. Vorhandene partielle Dataset-Klassen müssen manuell in das Dataset-Projekt verschoben werden.

6.  Speichern Sie das DataSet.

     Der Dataset-Code wird generiert, in dem ausgewählten Projekt im die **DataSet-Projekt** -Eigenschaft, und die **TableAdapter** Code im aktuellen Projekt generiert wird.

Standardmäßig ist bei einer Trennung von Dataset und TableAdapter-Code wird eine separate Klassendatei in jedem Projekt angelegt. Das ursprüngliche Projekt enthält eine Datei mit dem Namen dem Namen DatasetName.Designer.vb (oder DatasetName.Designer.cs), die den TableAdapter-Code enthält. Das Projekt, das in festgelegten der **Dataset-Projekt** Eigenschaft verfügt über eine Datei mit dem Namen dem Namen DatasetName.DataSet.Designer.vb (oder DatasetName.DataSet.Designer.cs), die den Dataset-Code enthält.

> [!NOTE]
>  Um die generierte Klassendatei anzuzeigen, wählen Sie das Dataset oder der TableAdapter-Projekt aus. Klicken Sie auf **Projektmappen-Explorer**Option **alle Dateien anzeigen**.

## <a name="see-also"></a>Siehe auch

- [Übersicht über N-Tier-Datenanwendungen](../data-tools/n-tier-data-applications-overview.md)
- [Exemplarische Vorgehensweise: Erstellen einer N-Tier-Datenanwendung](../data-tools/walkthrough-creating-an-n-tier-data-application.md)
- [Hierarchische Aktualisierung](../data-tools/hierarchical-update.md)
- [Zugreifen auf Daten in Visual Studio](../data-tools/accessing-data-in-visual-studio.md)
- [ADO.NET](/dotnet/framework/data/adonet/index)