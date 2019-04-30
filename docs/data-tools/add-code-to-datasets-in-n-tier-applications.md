---
title: Hinzufügen von Code zu DataSets in N-Tier-Anwendungen
ms.date: 11/04/2016
ms.topic: conceptual
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- n-tier applications, extending datasets
ms.assetid: d43c2ccd-4902-43d8-b1a8-d10ca5d3210c
author: gewarren
ms.author: gewarren
manager: jillfra
ms.workload:
- data-storage
ms.openlocfilehash: a66250c9d376962bfef2db6b563070696fd33346
ms.sourcegitcommit: 47eeeeadd84c879636e9d48747b615de69384356
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 04/23/2019
ms.locfileid: "63402873"
---
# <a name="add-code-to-datasets-in-n-tier-applications"></a>Hinzufügen von Code zu DataSets in N-Tier-Anwendungen
Sie können die Funktionen eines Datasets erweitern, indem Sie die Datei eine partielle Klasse für das Dataset zu erstellen und Code hinzufügen (anstelle von Code zum Hinzufügen der *DatasetName*. Dataset.Designer-Datei). Partielle Klassen ermöglichen es sich um Code für eine bestimmte Klasse auf mehrere physische Dateien unterteilt werden. Weitere Informationen finden Sie unter [teilweise](/dotnet/visual-basic/language-reference/modifiers/partial) oder [partielle Klassen und Methoden](/dotnet/csharp/programming-guide/classes-and-structs/partial-classes-and-methods).

Jedes Mal, wenn der datasetdefinition (im typisierten Dataset) geändert wird, wird der Code, der ein Dataset definiert, generiert. Dieser Code wird auch generiert, wenn Sie während der Ausführung des Assistenten für alle Änderungen vornehmen, die die Konfiguration eines Datasets ändert. Um zu verhindern, dass Ihr Code beim erneuten Generieren eines Dataset gelöscht wird, fügen Sie Code des Datasets partiellen Klassendatei hinzu.

Nachdem Sie das Dataset und TableAdapter-Code trennen, ist das Ergebnis standardmäßig eine separate Klassendatei in jedem Projekt. Das ursprüngliche Projekt enthält eine Datei namens *dem Namen DatasetName.Designer.vb* (oder *DatasetName.Designer.cs*), die den TableAdapter-Code enthält. Das Projekt, das angegeben die **Dataset-Projekt** Eigenschaft verfügt über eine Datei mit dem Namen *dem Namen DatasetName.DataSet.Designer.vb* (oder *DatasetName.DataSet.Designer.cs*) . Diese Datei enthält den Dataset-Code.

> [!NOTE]
> Bei einer Abtrennung der Datasets und TableAdapters (durch Festlegen der **DataSet-Projekt** Eigenschaft), vorhandene partielle Dataset-Klassen im Projekt wird nicht automatisch verschoben werden. Vorhandene partielle DataSet-Klassen müssen manuell in das DataSet-Projekt verschoben werden.

> [!NOTE]
> Wenn Code für die Überprüfung hinzugefügt werden muss, bietet das typisierte Dataset Funktionen zum Generieren von <xref:System.Data.DataTable.ColumnChanging> und <xref:System.Data.DataTable.RowChanging> -Ereignishandler. Weitere Informationen finden Sie unter [Hinzufügen von Validierungen zu einem n-Tier-Dataset](../data-tools/add-validation-to-an-n-tier-dataset.md).

## <a name="to-add-code-to-datasets-in-n-tier-applications"></a>Hinzufügen von Code zu Datasets in n-schichtige Anwendungen

1. Suchen Sie das Projekt mit der *XSD* Datei.

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

- [Übersicht über n-schichtige Datenanwendungen](../data-tools/n-tier-data-applications-overview.md)
- [Gewusst wie: Hinzufügen von Code zu TableAdapters in N-Tier-Anwendungen](../data-tools/add-code-to-tableadapters-in-n-tier-applications.md)
- [Erstellen und Konfigurieren eines TableAdapters](create-and-configure-tableadapters.md)
- [Übersicht über die hierarchische Aktualisierung](hierarchical-update.md)
- [Datasettools in Visual Studio](../data-tools/dataset-tools-in-visual-studio.md)