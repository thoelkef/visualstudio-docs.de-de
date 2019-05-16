---
title: Hinzufügen von Code zu Datasets in n-Tier-Anwendungen | Microsoft-Dokumentation
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-data-tools
ms.topic: conceptual
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- n-tier applications, extending datasets
ms.assetid: d43c2ccd-4902-43d8-b1a8-d10ca5d3210c
caps.latest.revision: 23
author: gewarren
ms.author: gewarren
manager: jillfra
ms.openlocfilehash: 6c788e422ea8613b77d7d0c0460d7c026916baa3
ms.sourcegitcommit: 08fc78516f1107b83f46e2401888df4868bb1e40
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 05/15/2019
ms.locfileid: "65697154"
---
# <a name="add-code-to-datasets-in-n-tier-applications"></a>Hinzufügen von Code zu DataSets in N-Tier-Anwendungen
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Sie können die Funktionen eines Datasets erweitern, indem Sie die Datei eine partielle Klasse für das Dataset zu erstellen und Code hinzufügen (anstelle von Code zum Hinzufügen der *DatasetName*. Dataset.Designer-Datei). Partielle Klassen ermöglichen es sich um Code für eine bestimmte Klasse auf mehrere physische Dateien unterteilt werden. Weitere Informationen finden Sie unter [teilweise](https://msdn.microsoft.com/library/7adaef80-f435-46e1-970a-269fff63b448) oder [partielle Klassen und Methoden](https://msdn.microsoft.com/library/804cecb7-62db-4f97-a99f-60975bd59fa1).

Der Code, der ein Dataset definiert wird generiert, jedes Mal, wenn Änderungen an der Definition des Datasets vorgenommen werden. Dieser Code wird auch generiert, wenn Sie während der Ausführung des Assistenten für alle Änderungen vornehmen, die die Konfiguration eines Datasets ändert. Um zu verhindern, dass Ihr Code beim erneuten Generieren eines Dataset gelöscht wird, fügen Sie Code des Datasets partiellen Klassendatei hinzu.

Standardmäßig wird bei einer Trennung von DataSet-Code und `TableAdapter`-Code eine separate Klassendatei in jedem Projekt angelegt. Das ursprüngliche Projekt enthält eine Filenamed *DatasetName*. Designer.vb (oder *DatasetName*. "Designer.cs"), enthält die `TableAdapter` Code. Das Projekt, das angegeben die **Dataset-Projekt** Eigenschaft verfügt über eine Datei mit dem Namen *DatasetName*. DataSet.Designer.vb (oder *DatasetName*. (DataSet.Designer.cs). Diese Datei enthält den Dataset-Code.

> [!NOTE]
> Bei einer Abtrennung der Datasets und `TableAdapter`s (durch Festlegen der **DataSet-Projekt** Eigenschaft), vorhandene partielle Dataset-Klassen im Projekt wird nicht automatisch verschoben werden. Vorhandene partielle DataSet-Klassen müssen manuell in das DataSet-Projekt verschoben werden.

> [!NOTE]
> Wenn Code für die Überprüfung hinzugefügt werden muss, bietet der DataSet-Designer Funktionen zum Generieren von <xref:System.Data.DataTable.ColumnChanging> und <xref:System.Data.DataTable.RowChanging> -Ereignishandler. Weitere Informationen finden Sie unter [Hinzufügen von Validierungen zu einem n-Tier-Dataset](../data-tools/add-validation-to-an-n-tier-dataset.md).

## <a name="add-code-to-datasets-in-n-tier-applications"></a>Hinzufügen von Code zu DataSets in N-Tier-Anwendungen

1. Suchen Sie das Projekt mit der XSD-Datei (das Dataset).

2. Wählen Sie die **XSD** Datei, um das Dataset öffnen.

3. Mit der rechten Maustaste in der Datentabelle, Sie fügen Sie Code (den Tabellennamen in der Titelleiste), und wählen Sie dann möchten **Ansichtscode**.

     Eine partielle Klasse wird erstellt und im Code-Editor geöffnet.

4. Fügen Sie Code innerhalb der Deklaration der partiellen Klasse.

     Das folgende Beispiel zeigt, wo die CustomersDataTable NorthwindDataSet Code hinzufügen:

    ```vb
    Partial Public Class CustomersDataTable
        ' Add code here to add functionality
        ' to the CustomersDataTable.
    End Class
    ```

    ```csharp
    partial class CustomersDataTable
    {
        // Add code here to add functionality
        // to the CustomersDataTable.
    }
    ```

## <a name="see-also"></a>Siehe auch

- [Übersicht über N-Tier-Datenanwendungen](../data-tools/n-tier-data-applications-overview.md)
- [Gewusst wie: Hinzufügen von Code zu TableAdapters in N-Tier-Anwendungen](../data-tools/add-code-to-tableadapters-in-n-tier-applications.md)
- [TableAdapters](https://msdn.microsoft.com/library/09416de9-134c-4dc7-8262-6c8d81e3f364)
- [Übersicht über TableAdapterManager](https://msdn.microsoft.com/library/33076d42-6b41-491a-ac11-6c6339aea650)
- [Übersicht über die hierarchische Aktualisierung](https://msdn.microsoft.com/library/c4f8e8b9-e4a5-4a02-8462-d03d1e8222d6)
- [Datasettools in Visual Studio](../data-tools/dataset-tools-in-visual-studio.md)