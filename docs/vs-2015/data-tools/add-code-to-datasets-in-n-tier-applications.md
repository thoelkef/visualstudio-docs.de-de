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
author: jillre
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: aed37ee9cdd8c221fcfb114db426a6286ee8ad6f
ms.sourcegitcommit: a8e8f4bd5d508da34bbe9f2d4d9fa94da0539de0
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 10/19/2019
ms.locfileid: "72673118"
---
# <a name="add-code-to-datasets-in-n-tier-applications"></a>Hinzufügen von Code zu DataSets in N-Tier-Anwendungen
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Sie können die Funktionalität eines Datasets erweitern, indem Sie eine partielle Klassendatei für das Dataset erstellen und diesem Code hinzufügen (anstatt dem *DataSetName*Code hinzuzufügen. DataSet. Designer-Datei). Partielle Klassen ermöglichen das Aufteilen von Code für eine bestimmte Klasse in mehrere physische Dateien. Weitere Informationen finden Sie unter [partielle](https://msdn.microsoft.com/library/7adaef80-f435-46e1-970a-269fff63b448) oder [partielle Klassen und Methoden](https://msdn.microsoft.com/library/804cecb7-62db-4f97-a99f-60975bd59fa1).

Der Code, mit dem ein Dataset definiert wird, wird jedes Mal generiert, wenn Änderungen an der datasetdefinition vorgenommen werden. Dieser Code wird auch generiert, wenn Sie während der Ausführung eines Assistenten, der die Konfiguration eines Datasets ändert, Änderungen vornehmen. Um zu verhindern, dass Ihr Code während der erneuten Generierung eines Datasets gelöscht wird, fügen Sie der partiellen Klassendatei des Datasets Code hinzu.

Standardmäßig wird bei einer Trennung von DataSet-Code und `TableAdapter`-Code eine separate Klassendatei in jedem Projekt angelegt. Das ursprüngliche Projekt hat einen *DataSetName mit Dateiname*. Designer. vb (oder *DataSetName*. Designer.cs), die den `TableAdapter` Code enthält. Das Projekt, das in der **DataSet-Projekt** Eigenschaft festgelegt ist, hat eine Datei mit dem Namen *DataSetName*. DataSet. Designer. vb (oder *DataSetName*. DataSet.Designer.cs). Diese Datei enthält den DataSet-Code.

> [!NOTE]
> Wenn Sie Datasets und `TableAdapter`s trennen (durch Festlegen der **DataSet-Projekt** Eigenschaft), werden vorhandene partielle DataSet-Klassen im Projekt nicht automatisch verschoben. Vorhandene partielle DataSet-Klassen müssen manuell in das DataSet-Projekt verschoben werden.

> [!NOTE]
> Wenn Validierungscode hinzugefügt werden muss, stellt der DataSet-Designer Funktionen zum Erstellen <xref:System.Data.DataTable.ColumnChanging> und <xref:System.Data.DataTable.RowChanging> Ereignis Handlers bereit. Weitere Informationen finden Sie unter [Hinzufügen von Validierungen zu einem n-Tier-DataSet](../data-tools/add-validation-to-an-n-tier-dataset.md).

## <a name="add-code-to-datasets-in-n-tier-applications"></a>Hinzufügen von Code zu DataSets in N-Tier-Anwendungen

1. Suchen Sie das Projekt, das die XSD-Datei enthält (das DataSet).

2. Wählen Sie die **XSD** -Datei aus, um das DataSet zu öffnen.

3. Klicken Sie mit der rechten Maustaste auf die Datentabelle, der Sie Code hinzufügen möchten (der Tabellenname in der Titelleiste), und wählen Sie dann **Code anzeigen**aus.

     Eine partielle Klasse wird erstellt und im Code-Editor geöffnet.

4. Fügen Sie Code in der Deklaration der partiellen Klasse hinzu

     Im folgenden Beispiel wird gezeigt, wo der customersdatbare-Datei in NorthwindDataSet Code hinzugefügt wird:

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
- [Übersicht über hierarchische Updates](https://msdn.microsoft.com/library/c4f8e8b9-e4a5-4a02-8462-d03d1e8222d6)
- [Datasettools in Visual Studio](../data-tools/dataset-tools-in-visual-studio.md)