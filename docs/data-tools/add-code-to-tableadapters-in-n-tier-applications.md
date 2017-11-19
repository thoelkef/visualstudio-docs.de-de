---
title: "Hinzufügen von Code zu TableAdapters in n-Tier-Anwendungen | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- TableAdapters, n-tier applications
- n-tier applications, extending TableAdapters
ms.assetid: dafac00e-df9d-4d4a-95a6-e34b4d099425
caps.latest.revision: "19"
author: gewarren
ms.author: gewarren
manager: ghogen
ms.technology: vs-data-tools
ms.openlocfilehash: 396e1132015c2eb37f06095f135dae878bfeb574
ms.sourcegitcommit: ee42a8771f0248db93fd2e017a22e2506e0f9404
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 11/09/2017
---
# <a name="add-code-to-tableadapters-in-n-tier-applications"></a>Hinzufügen von Code zu TableAdapters in n-Tier-Anwendungen
Sie können die Funktionalität eines TableAdapter erweitern, indem die Datei eine partielle Klasse für den TableAdapter erstellen und Code hinzufügen (anstatt zum Hinzufügen von Code, um die *DatasetName*. DataSet.Designer-Datei). Partielle Klassen können Sie Code für eine bestimmte Klasse auf mehrere physische Dateien unterteilt werden. Weitere Informationen finden Sie unter [partielle](/dotnet/visual-basic/language-reference/modifiers/partial) oder [Partial (Typ)](/dotnet/csharp/language-reference/keywords/partial-type).  
  
Der Code, der einen TableAdapter definiert wird generiert, jedes Mal, wenn Änderungen an den TableAdapter im Dataset vorgenommen werden. Dieser Code wird auch generiert, wenn während der Ausführung des Assistenten für alle Änderungen, die die Konfiguration des TableAdapter ändert. Um zu verhindern, dass Ihr Code während der erneuten Generierung eines TableAdapter gelöscht wird, fügen Sie Code in der partiellen Klassendatei des TableAdapter hinzu.  
  
Standardmäßig ist bei einer Trennung von Dataset und TableAdapter-Code wird eine separate Klassendatei in jedem Projekt angelegt. Das ursprüngliche Projekt enthält eine Datei namens *DatasetName*. Designer.vb (oder *DatasetName*. Designer.cs), die den TableAdapter-Code enthält. Das Projekt, das in festgelegten der **Dataset-Projekt** Eigenschaft verfügt über eine Datei namens *DatasetName*. DataSet.Designer.vb (oder *DatasetName*. (DataSet.Designer.cs), die den Dataset-Code enthält.  
  
> [!NOTE]
>  Beim Trennen von Datasets und TableAdaptern (durch Festlegen der **DataSet-Projekt** Eigenschaft), werden vorhandene partielle Dataset-Klassen im Projekt nicht automatisch verschoben werden. Vorhandene partielle Dataset-Klassen müssen manuell in das Dataset-Projekt verschoben werden.  
  
> [!NOTE]
>  Das Dataset bietet Funktionen zum Generieren von <xref:System.Data.DataTable.ColumnChanging> und <xref:System.Data.DataTable.RowChanging> Ereignishandler, wenn die Validierung erforderlich ist. Weitere Informationen finden Sie unter [Hinzufügen von Validierungen zu einem n-Tier-Dataset](../data-tools/add-validation-to-an-n-tier-dataset.md).  
  
[!INCLUDE[note_settings_general](../data-tools/includes/note_settings_general_md.md)]  
  
## <a name="to-add-user-code-to-a-tableadapter-in-an-n-tier-application"></a>So fügen Sie Benutzercode einem TableAdapter in einer n-Tier-Anwendung hinzu  
  
1.  Suchen Sie das Projekt, das die XSD-Datei enthält.
  
2.  Doppelklicken klicken Sie auf die **XSD** zu öffnende Datei die **Dataset-Designer**.  
  
3.  Mit der rechten Maustaste des TableAdapters, die Sie verwenden möchten, fügen Sie Code hinzu, und wählen Sie dann **Code anzeigen**.  
  
     Eine partielle Klasse wird erstellt und im Code-Editor geöffnet.  
  
4.  Fügen Sie Code innerhalb der Deklaration der partiellen Klasse hinzu.  
  
5.  Das folgende Beispiel zeigt, wo Sie zum Hinzufügen von Code die `CustomersTableAdapter` in der `NorthwindDataSet`:  
  
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
[Daten von N-Tier-Anwendungen (Übersicht)](../data-tools/n-tier-data-applications-overview.md)   
[Fügen Sie Code hinzu, um Datasets in n-Tier-Anwendungen](../data-tools/add-code-to-datasets-in-n-tier-applications.md)   
[Erstellen und Konfigurieren von TableAdapters](create-and-configure-tableadapters.md)   
[Übersicht über die hierarchische Aktualisierung](hierarchical-update.md)   
