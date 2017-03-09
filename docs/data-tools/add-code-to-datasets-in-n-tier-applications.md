---
title: "Gewusst wie: Hinzuf&#252;gen von Code zu DataSets in N-Tier-Anwendungen | Microsoft Docs"
ms.custom: ""
ms.date: "11/17/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
dev_langs: 
  - "VB"
  - "CSharp"
  - "C++"
  - "aspx"
helpviewer_keywords: 
  - "N-Tier-Anwendungen, Erweitern von Datasets"
ms.assetid: d43c2ccd-4902-43d8-b1a8-d10ca5d3210c
caps.latest.revision: 20
caps.handback.revision: 17
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# Gewusst wie: Hinzuf&#252;gen von Code zu DataSets in N-Tier-Anwendungen
Sie können die Funktionen eines DataSets erweitern, indem Sie eine Datei für eine partielle Klasse des DataSets erstellen und Code hinzufügen \(anstatt Code zur *DataSetName*.DataSet.Designer\-Datei hinzuzufügen\).  \(Mit partiellen Klassen können Sie Code für eine bestimmte Klasse auf mehrere physische Dateien aufteilen.  Weitere Informationen finden Sie unter [Partial](/dotnet/visual-basic/language-reference/modifiers/partial) bzw. [Partielle Klassen und Methoden](/dotnet/csharp/programming-guide/classes-and-structs/partial-classes-and-methods).\)  
  
 Der ein DataSet definierende Code wird immer dann generiert, wenn Änderungen an der Definition des DataSets vorgenommen wurden \(im [Erstellen und Bearbeiten von typisierten Datasets](../data-tools/creating-and-editing-typed-datasets.md)\).  Dieser Code wird auch generiert, wenn Sie einen Assistenten verwenden, der die Konfiguration eines DataSets ändert.  Um zu verhindern, dass der Code bei erneutem Generieren eines DataSets gelöscht wird, fügen Sie den Code zur Datei für die partielle Klasse des DataSets hinzu.  
  
 Standardmäßig wird bei einer Trennung von DataSet\-Code und `TableAdapter`\-Code eine separate Klassendatei in jedem Projekt angelegt.  Das ursprüngliche Projekt enthält eine Datei mit dem Namen *DatasetName*.Designer.vb \(oder *DatasetName*.Designer.cs\), die den `TableAdapter`\-Code enthält.  Das Projekt, das in der **DataSet\-Projekt**\-Eigenschaft ausgewählt wurde, verfügt über eine Datei mit dem Namen *DatasetName*.DataSet.Designer.vb \(oder *DatasetName*.DataSet.Designer.cs\), die den DataSet\-Code enthält.  
  
> [!NOTE]
>  Wenn Sie DataSets und `TableAdapter` durch Festlegen der **DataSet\-Projekt**\-Eigenschaft trennen, werden vorhandene partielle DataSet\-Klassen im Projekt nicht automatisch verschoben.  Vorhandene partielle Dataset\-Klassen müssen manuell ins Dataset\-Projekt verschoben werden.  
  
> [!NOTE]
>  Der [Erstellen und Bearbeiten von typisierten Datasets](../data-tools/creating-and-editing-typed-datasets.md) unterstützt außerdem Funktionen zum Generieren der Eventhandler <xref:System.Data.DataTable.ColumnChanging> und <xref:System.Data.DataTable.RowChanging>, wenn Validierungscode hinzugefügt werden soll.  Weitere Informationen finden Sie unter [Gewusst wie: Hinzufügen von Validierungen zu einem N\-Tier\-DataSet](../data-tools/add-validation-to-an-n-tier-dataset.md).  
  
### So fügen Sie Code zu DataSets in N\-Tier\-Anwendungen hinzu  
  
1.  Suchen Sie das Projekt, das die XSD\-Datei \([Erstellen und Bearbeiten von typisierten Datasets](../data-tools/creating-and-editing-typed-datasets.md)\) enthält.  
  
2.  Doppelklicken Sie auf die Datei **.xsd**, um den [Erstellen und Bearbeiten von typisierten Datasets](../data-tools/creating-and-editing-typed-datasets.md) zu öffnen.  
  
3.  Klicken Sie mit der rechten Maustaste auf die Datentabelle, der Sie Code hinzufügen möchten \(d. h. auf den Tabellennamen in der Titelleiste\), und klicken Sie dann auf **Code anzeigen**.  
  
     Eine partielle Klasse wird erstellt und im Code\-Editor geöffnet.  
  
4.  Fügen Sie Code innerhalb der Deklaration der partiellen Klasse hinzu.  
  
     Im folgenden Beispiel wird veranschaulicht, wo der CustomersDataTable im NorthwindDataSet Code hinzugefügt werden kann:  
  
    ```vb#  
    Partial Public Class CustomersDataTable  
        ' Add code here to add functionality   
        ' to the CustomersDataTable.  
    End Class  
    ```  
  
    ```c#  
    partial class CustomersDataTable  
    {  
        // Add code here to add functionality  
        // to the CustomersDataTable.  
    }  
    ```  
  
## Siehe auch  
 [Übersicht über N\-Tier\-Datenanwendungen](../data-tools/n-tier-data-applications-overview.md)   
 [Gewusst wie: Hinzufügen von Code zu TableAdapters in N\-Tier\-Anwendungen](../data-tools/add-code-to-tableadapters-in-n-tier-applications.md)   
 [TableAdapters](../Topic/TableAdapters.md)   
 [Übersicht über TableAdapterManager](../Topic/TableAdapterManager%20Overview.md)   
 [Übersicht über die hierarchische Aktualisierung](../Topic/Hierarchical%20Update%20Overview.md)   
 [Erstellen von Datenanwendungen](../data-tools/creating-data-applications.md)   
 [Arbeiten mit Datasets in Visual Studio](../data-tools/dataset-tools-in-visual-studio.md)