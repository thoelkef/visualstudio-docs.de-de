---
title: Trennen von Datasets und TableAdapters in verschiedene Projekte | Microsoft-Dokumentation
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
- TableAdapters, n-tier applications
- n-tier applications, separating Datasets and TableAdapters
ms.assetid: f66a3940-6227-46af-a930-9177f425f4fd
caps.latest.revision: 21
author: jillre
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: 6f6ec76e79cc1c4759cbe05d8bdcacc1297b655b
ms.sourcegitcommit: a8e8f4bd5d508da34bbe9f2d4d9fa94da0539de0
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 10/19/2019
ms.locfileid: "72655434"
---
# <a name="separate-datasets-and-tableadapters-into-different-projects"></a>Aufteilen von DataSets und TableAdapters in verschiedene Projekte
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Typisierte Datasets wurden verbessert, sodass die [TableAdapters](https://msdn.microsoft.com/library/09416de9-134c-4dc7-8262-6c8d81e3f364) -Klasse und die DataSet-Klasse in separaten Projekten generiert werden können. Dies ermöglicht eine bequeme Trennung der Anwendungsebenen und die Erzeugung von N-Tier-Datenanwendungen.

 Im folgenden Verfahren wird beschrieben, wie der DataSet-Designer verwendet wird, um Datasetcode in einem Projekt zu generieren, das von dem Projekt getrennt ist, das den generierten `TableAdapter` Code enthält.

## <a name="separatedatasets-and-tableadapters"></a>Separatedatasets und TableAdapters
 Wenn Sie Datasetcode von `TableAdapter` Code trennen, muss sich das Projekt, das den Datasetcode enthält, in der aktuellen Projekt Mappe befinden. Wenn sich dieses Projekt nicht in der aktuellen Projekt Mappe befindet, ist es nicht in der **DataSet-Projekt** Liste im **Eigenschaften** Fenster verfügbar.

 [!INCLUDE[note_settings_general](../includes/note-settings-general-md.md)]

#### <a name="to-separate-the-dataset-into-a-different-project"></a>So separieren Sie das DataSet in ein anderes Projekt

1. Öffnen Sie eine Projektmappe, die ein DataSet (XSD-Datei) enthält.

   > [!NOTE]
   > Wenn die Projekt Mappe nicht das Projekt enthält, in das Sie den Datasetcode aufteilen möchten, erstellen Sie das Projekt, oder fügen Sie der Projekt Mappe ein vorhandenes Projekt hinzu.

2. Doppelklicken Sie in **Projektmappen-Explorer** auf eine typisierte Datasetdatei (XSD-Datei), um das Dataset im **DataSet-Designer**zu öffnen.

3. Wählen Sie einen leeren Bereich des **DataSet-Designer**aus.

4. Suchen Sie im Fenster **Eigenschaften** den **DataSet-Projekt** Knoten.

5. Wählen Sie in der Liste **DataSet-Projekt** den Namen des Projekts aus, in das Sie den DataSet-Code generieren möchten.

    Nachdem Sie das Projekt ausgewählt haben, in das Sie den Datasetcode generieren möchten, wird die Eigenschaft **DataSet-Datei** mit einem Standard Dateinamen aufgefüllt. Sie können diesen Namen ggf. ändern. Wenn Sie den Dataset-Code in einem bestimmten Verzeichnis generieren möchten, können Sie in der **Projektordner**-Eigenschaft den Namen des Ordners angeben.

   > [!NOTE]
   > Beim Trennen von Datasets und TableAdapters (durch Festlegen der **DataSet-Projekt** Eigenschaft) werden vorhandene partielle DataSet-Klassen in dem Projekt nicht automatisch verschoben. Vorhandene Dataset-partielle Klassen müssen manuell in das DataSet-Projekt verschoben werden.

6. Speichern Sie das DataSet.

    Der DataSet-Code wird in dem ausgewählten Projekt in der **DataSet-Projekt** Eigenschaft generiert, und der **TableAdapter** -Code wird im aktuellen Projekt generiert.

   Standardmäßig wird bei einer Trennung von DataSet-Code und `TableAdapter`-Code eine separate Klassendatei in jedem Projekt angelegt. Das ursprüngliche Projekt enthält eine Datei mit dem Namen DatasetName. Designer. vb (oder DatasetName.Designer.cs), die den `TableAdapter` Code enthält. Das Projekt, das in der **DataSet-Projekt** Eigenschaft festgelegt ist, verfügt über eine Datei namens DatasetName. DataSet. Designer. vb (oder DatasetName.DataSet.Designer.cs), die den DataSet-Code enthält.

> [!NOTE]
> Um die generierte Klassendatei anzuzeigen, wählen Sie das DataSet oder `TableAdapter` Projekt aus. Wählen Sie dann in **Projektmappen-Explorer**die Option **alle Dateien anzeigen** aus.

## <a name="see-also"></a>Siehe auch
 [Übersicht über n-Tier-Daten Anwendungen](../data-tools/n-tier-data-applications-overview.md) Exemplarische Vorgehensweise [: Erstellen einer n-Tier-Daten Anwendung](../data-tools/walkthrough-creating-an-n-tier-data-application.md) [hierarchische Aktualisierung](../data-tools/hierarchical-update.md) [zugreifen auf Daten in Visual Studio](../data-tools/accessing-data-in-visual-studio.md) [ADO.net](https://msdn.microsoft.com/library/5b96ed06-9759-4966-a797-a1d5f6ee50ca)
