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
author: gewarren
ms.author: gewarren
manager: jillfra
ms.openlocfilehash: c90943f64166cfd5113032d14c2c66be1db858eb
ms.sourcegitcommit: 47eeeeadd84c879636e9d48747b615de69384356
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 04/23/2019
ms.locfileid: "63425097"
---
# <a name="separate-datasets-and-tableadapters-into-different-projects"></a>Aufteilen von DataSets und TableAdapters in verschiedene Projekte
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Typisierte Datasets wurden weiterentwickelt, damit die [TableAdapters](http://msdn.microsoft.com/library/09416de9-134c-4dc7-8262-6c8d81e3f364) und Dataset-Klassen in separaten Projekten generiert werden können. Dies ermöglicht eine bequeme Trennung der Anwendungsebenen und die Erzeugung von N-Tier-Datenanwendungen.  
  
 Das folgende Verfahren beschreibt den Prozess der Verwendung von Dataset-Designer zum Generieren von Dataset-Code in ein Projekt, das aus dem Projekt getrennt ist, das die generierte enthält `TableAdapter` Code.  
  
## <a name="separatedatasets-and-tableadapters"></a>Separatedatasets und TableAdapters  
 Bei einer Abtrennung der Dataset-Code von `TableAdapter` Code wird das Projekt mit den Dataset-Code muss in der aktuellen Projektmappe befinden. Wenn dieses Projekt nicht in der aktuellen Projektmappe befindet, nicht mehr verfügbar ist, in der **DataSet-Projekt** Liste der **Eigenschaften** Fenster.  
  
 [!INCLUDE[note_settings_general](../includes/note-settings-general-md.md)]  
  
#### <a name="to-separate-the-dataset-into-a-different-project"></a>So separieren Sie das DataSet in ein anderes Projekt  
  
1. Öffnen Sie eine Projektmappe, die ein DataSet (XSD-Datei) enthält.  
  
   > [!NOTE]
   > Wenn die Projektmappe das Projekt keinen ist in dem Sie den Dataset-Code zu trennen möchten, erstellen Sie das Projekt oder fügen Sie ein vorhandenes Projekt zur Projektmappe hinzu.  
  
2. Doppelklicken Sie auf ein typisiertes Dataset-Datei (XSD-Datei) in **Projektmappen-Explorer** , öffnen Sie das Dataset in den **Dataset-Designer**.  
  
3. Wählen Sie einen leeren Bereich der **Dataset-Designer**.  
  
4. In der **Eigenschaften** Fenster Suchen der **DataSet-Projekt** Knoten.  
  
5. In der **DataSet-Projekt** Liste, wählen Sie den Namen des Projekts, in dem Sie den Dataset-Code generieren möchten.  
  
    Nachdem Sie das Projekt auswählen, in dem Sie den Dataset-Code generieren möchten, die **Datasetdatei** -Eigenschaft mit einem standardmäßigen Dateinamen aufgefüllt. Sie können diesen Namen bei Bedarf ändern. Wenn Sie den Dataset-Code in einem bestimmten Verzeichnis generieren möchten, können Sie in der **Projektordner**-Eigenschaft den Namen des Ordners angeben.  
  
   > [!NOTE]
   > Bei einer Abtrennung der Datasets und TableAdapters (durch Festlegen der **DataSet-Projekt** Eigenschaft), vorhandene partielle Dataset-Klassen im Projekt wird nicht automatisch verschoben werden. Vorhandene partielle Dataset-Klassen müssen manuell in der Dataset-Projekt verschoben werden.  
  
6. Speichern Sie das DataSet.  
  
    Der Dataset-Code wird generiert, in dem ausgewählten Projekt im der **DataSet-Projekt** -Eigenschaft, und die **TableAdapter** Code in das aktuelle Projekt generiert wird.  
  
   Standardmäßig wird bei einer Trennung von DataSet-Code und `TableAdapter`-Code eine separate Klassendatei in jedem Projekt angelegt. Das ursprüngliche Projekt enthält eine Datei mit dem Namen dem Namen DatasetName.Designer.vb (oder DatasetName.Designer.cs), enthält die `TableAdapter` Code. Das Projekt, das angegeben die **Dataset-Projekt** Eigenschaft verfügt über eine Datei mit dem Namen dem Namen DatasetName.DataSet.Designer.vb (oder DatasetName.DataSet.Designer.cs), die den Dataset-Code enthält.  
  
> [!NOTE]
> Um die generierte Klassendatei anzuzeigen, wählen Sie das Dataset oder `TableAdapter` Projekt. Klicken Sie auf **Projektmappen-Explorer**Option **alle Dateien anzeigen** .  
  
## <a name="see-also"></a>Siehe auch  
 [Übersicht über N-Tier-Data-Anwendungen](../data-tools/n-tier-data-applications-overview.md)   
 [Exemplarische Vorgehensweise: Erstellen einer N-Tier-Datenanwendung](../data-tools/walkthrough-creating-an-n-tier-data-application.md)   
 [Hierarchische Aktualisierung](../data-tools/hierarchical-update.md)   
 [Zugreifen auf Daten in Visual Studio](../data-tools/accessing-data-in-visual-studio.md)   
 [ADO.NET](http://msdn.microsoft.com/library/5b96ed06-9759-4966-a797-a1d5f6ee50ca)
