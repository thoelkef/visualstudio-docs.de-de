---
title: Hinzufügen von Code zu TableAdapters in n-Tier-Anwendungen | Microsoft-Dokumentation
ms.custom: ''
ms.date: 2018-06-30
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
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
author: gewarren
ms.author: gewarren
manager: ghogen
ms.openlocfilehash: bd46596ff474a33be42b8c5118404845a39c2b7d
ms.sourcegitcommit: 55f7ce2d5d2e458e35c45787f1935b237ee5c9f8
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 08/22/2018
ms.locfileid: "47514415"
---
# <a name="add-code-to-tableadapters-in-n-tier-applications"></a>Hinzufügen von Code zu TableAdapters in N-Tier-Anwendungen
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Die neueste Version dieses Themas finden Sie unter [Hinzufügen von Code zu TableAdapters in n-schichtigen Anwendungen](https://docs.microsoft.com/visualstudio/data-tools/add-code-to-tableadapters-in-n-tier-applications).  
  
  
Können Sie die Funktionalität des erweitern eine `TableAdapter` durch das Erstellen der Datei eine partielle Klasse für die `TableAdapter` und Code hinzufügen (anstelle von Code zum Hinzufügen der *DatasetName*. DataSet.Designer-Datei). Partielle Klassen ermöglichen es sich um Code für eine bestimmte Klasse auf mehrere physische Dateien unterteilt werden. Weitere Informationen finden Sie unter [teilweise](http://msdn.microsoft.com/library/7adaef80-f435-46e1-970a-269fff63b448) oder [Partial (Typ)](http://msdn.microsoft.com/library/27320743-a22e-4c7b-b0b3-53afe3607334).  
  
 Der Code, definiert ein `TableAdapter` generiert jedes Mal, wenn Änderungen vorgenommen werden die `TableAdapter` (in der [erstellen und Bearbeiten typisierter Datasets](../data-tools/creating-and-editing-typed-datasets.md)). Dieser Code wird auch generiert, wenn Änderungen während der Ausführung des alle-Assistenten vorgenommen werden, die die Konfiguration ändert die `TableAdapter`. Um zu verhindern, dass Ihr Code gelöscht wird, während die erneute Generierung von einer `TableAdapter`, fügen Sie Code in die partielle Klasse-Datei von der `TableAdapter`.  
  
 Standardmäßig wird bei einer Trennung von DataSet-Code und `TableAdapter`-Code eine separate Klassendatei in jedem Projekt angelegt. Das ursprüngliche Projekt enthält eine Datei namens *DatasetName*. Designer.vb (oder *DatasetName*. "Designer.cs"), enthält die `TableAdapter` Code. Das Projekt, das angegeben die **Dataset-Projekt** Eigenschaft verfügt über eine Datei namens *DatasetName*. DataSet.Designer.vb (oder *DatasetName*. (DataSet.Designer.cs), die den Dataset-Code enthält.  
  
> [!NOTE]
>  Bei einer Abtrennung der Datasets und `TableAdapter`s (durch Festlegen der **DataSet-Projekt** Eigenschaft), werden vorhandene partielle Dataset-Klassen im Projekt nicht automatisch verschoben werden. Vorhandene partielle DataSet-Klassen müssen manuell in das DataSet-Projekt verschoben werden.  
  
> [!NOTE]
>  Die [erstellen und Bearbeiten typisierter Datasets](../data-tools/creating-and-editing-typed-datasets.md) bietet Funktionen zum Generieren von <xref:System.Data.DataTable.ColumnChanging> und <xref:System.Data.DataTable.RowChanging> Ereignishandler, die bei der Überprüfung erforderlich ist. Weitere Informationen finden Sie unter [Hinzufügen von Validierungen zu einem n-Tier-Dataset](../data-tools/add-validation-to-an-n-tier-dataset.md).  
  
 [!INCLUDE[note_settings_general](../includes/note-settings-general-md.md)]  
  
### <a name="to-add-user-code-to-a-tableadapter-in-an-n-tier-application"></a>Benutzercode einen TableAdapter in eine n-schichtige Anwendung hinzu  
  
1.  Suchen Sie das Projekt, das die XSD-Datei enthält (die [erstellen und Bearbeiten typisierter Datasets](../data-tools/creating-and-editing-typed-datasets.md)).  
  
2.  Doppelklicken dem **XSD** zu öffnende Datei die [erstellen und Bearbeiten typisierter Datasets](../data-tools/creating-and-editing-typed-datasets.md).  
  
3.  Mit der rechten Maustaste die `TableAdapter` , die Sie verwenden möchten, fügen Sie Code, und wählen Sie dann**Ansichtscode**.  
  
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
 [Übersicht über N-Tier-Data-Anwendungen](../data-tools/n-tier-data-applications-overview.md)   
 [Hinzufügen von Code zu Datasets in n-schichtige Anwendungen](../data-tools/add-code-to-datasets-in-n-tier-applications.md)   
 [TableAdapters](http://msdn.microsoft.com/library/09416de9-134c-4dc7-8262-6c8d81e3f364)   
 [Übersicht über TableAdapterManager](http://msdn.microsoft.com/library/33076d42-6b41-491a-ac11-6c6339aea650)   
 [Übersicht über die hierarchische Aktualisierung](http://msdn.microsoft.com/library/c4f8e8b9-e4a5-4a02-8462-d03d1e8222d6)   
 [Erstellen von Datenanwendungen](../data-tools/creating-data-applications.md)

