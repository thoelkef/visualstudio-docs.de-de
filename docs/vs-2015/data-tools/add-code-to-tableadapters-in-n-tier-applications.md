---
title: Hinzufügen von Code zu TableAdapters in n-Tier-Anwendungen | Microsoft-Dokumentation
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
- n-tier applications, extending TableAdapters
ms.assetid: dafac00e-df9d-4d4a-95a6-e34b4d099425
caps.latest.revision: 22
author: jillre
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: 942850e776cdd493afaad56b782b417db2040625
ms.sourcegitcommit: a8e8f4bd5d508da34bbe9f2d4d9fa94da0539de0
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 10/19/2019
ms.locfileid: "72673102"
---
# <a name="add-code-to-tableadapters-in-n-tier-applications"></a>Hinzufügen von Code zu TableAdapters in N-Tier-Anwendungen
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Sie können die Funktionalität einer `TableAdapter` erweitern, indem Sie eine partielle Klassendatei für die `TableAdapter` erstellen und Ihr Code hinzufügen (anstatt dem *DataSetName*Code hinzuzufügen. DataSet. Designer-Datei). Partielle Klassen ermöglichen das Aufteilen von Code für eine bestimmte Klasse in mehrere physische Dateien. Weitere Informationen finden Sie unter [Partial](https://msdn.microsoft.com/library/7adaef80-f435-46e1-970a-269fff63b448) oder [Partial (Type)](https://msdn.microsoft.com/library/27320743-a22e-4c7b-b0b3-53afe3607334).

 Der Code, der eine `TableAdapter` definiert, wird jedes Mal generiert, wenn Änderungen am `TableAdapter` vorgenommen werden. Dieser Code wird auch generiert, wenn während der Ausführung eines Assistenten, der die Konfiguration des `TableAdapter` ändert, Änderungen vorgenommen werden. Um zu verhindern, dass der Code während der erneuten Generierung eines `TableAdapter` gelöscht wird, fügen Sie der Datei der partiellen Klasse des `TableAdapter` Code hinzu.

 Standardmäßig wird bei einer Trennung von DataSet-Code und `TableAdapter`-Code eine separate Klassendatei in jedem Projekt angelegt. Das ursprüngliche Projekt enthält eine Datei mit dem Namen *DataSetName*. Designer. vb (oder *DataSetName*. Designer.cs), die den `TableAdapter` Code enthält. Das Projekt, das in der **DataSet-Projekt** Eigenschaft festgelegt ist, verfügt über eine Datei namens *DataSetName*. DataSet. Designer. vb (oder *DataSetName*. DataSet.Designer.cs), die den DataSet-Code enthält.

> [!NOTE]
> Wenn Sie Datasets und `TableAdapter`s trennen (durch Festlegen der **DataSet-Projekt** Eigenschaft), werden vorhandene partielle DataSet-Klassen im Projekt nicht automatisch verschoben. Vorhandene partielle DataSet-Klassen müssen manuell in das DataSet-Projekt verschoben werden.

> [!NOTE]
> Der DataSet-Designer bietet Funktionen zum Erstellen von <xref:System.Data.DataTable.ColumnChanging> und <xref:System.Data.DataTable.RowChanging> Ereignis Handlern, wenn eine Überprüfung erforderlich ist. Weitere Informationen finden Sie unter [Hinzufügen von Validierungen zu einem n-Tier-DataSet](../data-tools/add-validation-to-an-n-tier-dataset.md).

 [!INCLUDE[note_settings_general](../includes/note-settings-general-md.md)]

### <a name="to-add-user-code-to-a-tableadapter-in-an-n-tier-application"></a>So fügen Sie einem TableAdapter in einer n-Tier-Anwendung Benutzercode hinzu

1. Suchen Sie das Projekt, das die XSD-Datei enthält (das DataSet).

2. Doppelklicken Sie auf die **XSD** -Datei, um das DataSet zu öffnen.

3. Klicken Sie mit der rechten Maustaste auf die `TableAdapter`, der Sie Code hinzufügen möchten, und wählen Sie dann**Code anzeigen**aus.

     Eine partielle Klasse wird erstellt und im Code-Editor geöffnet.

4. Fügen Sie Code in der Deklaration der partiellen Klasse hinzu

5. Im folgenden Beispiel wird gezeigt, wo der `CustomersTableAdapter` in der `NorthwindDataSet` Code hinzugefügt wird:

    ```vb
    Partial Public Class CustomersTableAdapter
        ' Add code here to add functionality
        ' to the CustomersTableAdapter.
    End Class
    ```

    ```csharp
    public partial class CustomersTableAdapter
    {
        // Add code here to add functionality
        // to the CustomersTableAdapter.
    }
    ```

## <a name="see-also"></a>Siehe auch
 [Übersicht über n-Tier-Daten Anwendungen](../data-tools/n-tier-data-applications-overview.md) [Hinzufügen von Code zu Datasets in n-Tier-Anwendungen](../data-tools/add-code-to-datasets-in-n-tier-applications.md) [TableAdapters](https://msdn.microsoft.com/library/09416de9-134c-4dc7-8262-6c8d81e3f364) [TableAdapterManager Übersicht Übersicht](https://msdn.microsoft.com/library/33076d42-6b41-491a-ac11-6c6339aea650) [über hierarchische Updates](https://msdn.microsoft.com/library/c4f8e8b9-e4a5-4a02-8462-d03d1e8222d6)