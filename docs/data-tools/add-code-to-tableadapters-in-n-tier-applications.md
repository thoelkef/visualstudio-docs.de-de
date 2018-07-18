---
title: Hinzufügen von Code zu TableAdapters in N-Tier-Anwendungen
ms.date: 11/04/2016
ms.topic: conceptual
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- TableAdapters, n-tier applications
- n-tier applications, extending TableAdapters
ms.assetid: dafac00e-df9d-4d4a-95a6-e34b4d099425
author: gewarren
ms.author: gewarren
manager: douge
ms.prod: visual-studio-dev15
ms.technology: vs-data-tools
ms.workload:
- data-storage
ms.openlocfilehash: e5a9aad4aaecb629f5860fadf56e35a55455be63
ms.sourcegitcommit: c57ae28181ffe14a30731736661bf59c3eff1211
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 07/11/2018
ms.locfileid: "38783089"
---
# <a name="add-code-to-tableadapters-in-n-tier-applications"></a>Hinzufügen von Code zu TableAdapters in N-Tier-Anwendungen
Sie können die Funktionalität eines TableAdapter erweitern, indem die Datei eine partielle Klasse für den TableAdapter zu erstellen und Code hinzufügen (anstelle von Code zum Hinzufügen der *DatasetName.DataSet.Designer* Datei). Partielle Klassen ermöglichen es sich um Code für eine bestimmte Klasse auf mehrere physische Dateien unterteilt werden. Weitere Informationen finden Sie unter [teilweise](/dotnet/visual-basic/language-reference/modifiers/partial) oder [Partial (Typ)](/dotnet/csharp/language-reference/keywords/partial-type).

Der Code, der einen TableAdapter definiert wird generiert, jedes Mal, wenn Änderungen an den TableAdapter im Dataset vorgenommen werden. Dieser Code wird auch generiert, wenn Änderungen während der Ausführung des alle-Assistenten vorgenommen werden, die die Konfiguration des TableAdapter ändert. Um zu verhindern, dass Ihr Code beim erneuten Generieren eines TableAdapter gelöscht wird, fügen Sie Code in die partielle Klasse-Datei des TableAdapter hinzu.

Nachdem Sie das Dataset und TableAdapter-Code trennen, ist das Ergebnis standardmäßig eine separate Klassendatei in jedem Projekt. Das ursprüngliche Projekt enthält eine Datei namens *dem Namen DatasetName.Designer.vb* (oder *DatasetName.Designer.cs*), die den TableAdapter-Code enthält. Das Projekt, das angegeben die **Dataset-Projekt** Eigenschaft verfügt über eine Datei namens *dem Namen DatasetName.DataSet.Designer.vb* (oder *DatasetName.DataSet.Designer.cs*), enthält den Dataset-Code.

> [!NOTE]
>  Bei einer Abtrennung der Datasets und TableAdapters (durch Festlegen der **DataSet-Projekt** Eigenschaft), werden vorhandene partielle Dataset-Klassen im Projekt nicht automatisch verschoben werden. Vorhandene partielle Dataset-Klassen müssen manuell in der Dataset-Projekt verschoben werden.

> [!NOTE]
> Das Dataset bietet Funktionen zum Generieren von <xref:System.Data.DataTable.ColumnChanging> und <xref:System.Data.DataTable.RowChanging> Ereignishandler, die bei der Überprüfung erforderlich ist. Weitere Informationen finden Sie unter [Hinzufügen von Validierungen zu einem n-Tier-Dataset](../data-tools/add-validation-to-an-n-tier-dataset.md).

[!INCLUDE[note_settings_general](../data-tools/includes/note_settings_general_md.md)]

## <a name="to-add-user-code-to-a-tableadapter-in-an-n-tier-application"></a>Benutzercode einen TableAdapter in eine n-schichtige Anwendung hinzu

1.  Suchen Sie das Projekt mit der *XSD* Datei.

2.  Doppelklicken dem *XSD* zu öffnende Datei die **Dataset-Designer**.

3.  Mit der rechten Maustaste, die Sie verwenden möchten, fügen Sie Code, und wählen Sie dann TableAdapter **Ansichtscode**.

     Eine partielle Klasse wird erstellt und im Code-Editor geöffnet.

4.  Fügen Sie Code innerhalb der Deklaration der partiellen Klasse.

5.  Das folgende Beispiel zeigt, wo Sie zum Hinzufügen von Code die `CustomersTableAdapter` in die `NorthwindDataSet`:

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

- [Übersicht über N-Tier-Data-Anwendungen](../data-tools/n-tier-data-applications-overview.md)
- [Gewusst wie: Hinzufügen von Code zu DataSets in N-Tier-Anwendungen](../data-tools/add-code-to-datasets-in-n-tier-applications.md)
- [Erstellen und Konfigurieren eines TableAdapters](create-and-configure-tableadapters.md)
- [Übersicht über die hierarchische Aktualisierung](hierarchical-update.md)
