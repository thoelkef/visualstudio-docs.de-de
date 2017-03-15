---
title: "Gewusst wie: Hinzuf&#252;gen von Code zu TableAdapters in N-Tier-Anwendungen | Microsoft Docs"
ms.custom: ""
ms.date: "12/14/2016"
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
  - "N-Tier-Anwendungen, Erweitern von TableAdapters"
  - "TableAdapters, N-Tier-Anwendungen"
ms.assetid: dafac00e-df9d-4d4a-95a6-e34b4d099425
caps.latest.revision: 19
caps.handback.revision: 16
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# Gewusst wie: Hinzuf&#252;gen von Code zu TableAdapters in N-Tier-Anwendungen
Sie können die Funktionen eines `TableAdapter` erweitern, indem Sie eine partielle Klassendatei für den `TableAdapter` erstellen und Code hinzufügen \(anstatt Code zur *DatasetName*DataSet.Designer\-Datei hinzuzufügen\).  \(Mit partiellen Klassen können Sie Code für eine bestimmte Klasse auf mehrere physische Dateien aufteilen.  Weitere Informationen finden Sie unter [Partial](/dotnet/visual-basic/language-reference/modifiers/partial) bzw. [partial \(Typ\)](/dotnet/csharp/language-reference/keywords/partial-type).\)  
  
 Der Code, der `TableAdapter` definiert, wird jedes Mal generiert, wenn Änderungen am `TableAdapter` vorgenommen werden \(im [Erstellen und Bearbeiten von typisierten Datasets](../data-tools/creating-and-editing-typed-datasets.md)\).  Dieser Code wird auch generiert, wenn Sie einen Assistenten verwenden, der die Konfigurationen von `TableAdapter` ändert.  Um zu vermeiden, dass Code beim erneuten Generieren eines `TableAdapter` gelöscht wird, fügen Sie Code der Datei für die partielle Klasse von `TableAdapter` hinzu.  
  
 Standardmäßig wird bei einer Trennung von DataSet\-Code und `TableAdapter`\-Code eine separate Klassendatei in jedem Projekt angelegt.  Das ursprüngliche Projekt enthält eine Datei mit dem Namen *DatasetName*.Designer.vb \(oder *DatasetName*.Designer.cs\), die den `TableAdapter`\-Code enthält.  Das Projekt, das in der **DataSet\-Projekt**\-Eigenschaft ausgewählt wurde, verfügt über eine Datei mit dem Namen *DatasetName*.DataSet.Designer.vb \(oder *DatasetName*.DataSet.Designer.cs\), die den DataSet\-Code enthält.  
  
> [!NOTE]
>  Wenn Sie DataSets und `TableAdapter` durch Festlegen der **DataSet\-Projekt**\-Eigenschaft trennen, werden vorhandene partielle DataSet\-Klassen im Projekt nicht automatisch verschoben.  Vorhandene partielle Dataset\-Klassen müssen manuell ins Dataset\-Projekt verschoben werden.  
  
> [!NOTE]
>  Der [Erstellen und Bearbeiten von typisierten Datasets](../data-tools/creating-and-editing-typed-datasets.md) unterstützt außerdem Funktionen zum Generieren der Eventhandler <xref:System.Data.DataTable.ColumnChanging> und <xref:System.Data.DataTable.RowChanging>, wenn Validierungscode hinzugefügt werden soll.  Weitere Informationen finden Sie unter [Gewusst wie: Hinzufügen von Validierungen zu einem N\-Tier\-DataSet](../data-tools/add-validation-to-an-n-tier-dataset.md).  
  
 [!INCLUDE[note_settings_general](../data-tools/includes/note_settings_general_md.md)]  
  
### So fügen Sie einem TableAdapter in einer N\-Tier\-Anwendung Benutzercode hinzu  
  
1.  Suchen Sie das Projekt, das die XSD\-Datei \([Erstellen und Bearbeiten von typisierten Datasets](../data-tools/creating-and-editing-typed-datasets.md)\) enthält.  
  
2.  Doppelklicken Sie auf die Datei **.xsd**, um den [Erstellen und Bearbeiten von typisierten Datasets](../data-tools/creating-and-editing-typed-datasets.md) zu öffnen.  
  
3.  Klicken Sie mit der rechten Maustaste auf den `TableAdapter`, dem Sie Code hinzufügen möchten, und klicken Sie auf **Code anzeigen**.  
  
     Eine partielle Klasse wird erstellt und im Code\-Editor geöffnet.  
  
4.  Fügen Sie Code innerhalb der Deklaration der partiellen Klasse hinzu.  
  
5.  Im Folgenden wird verdeutlicht, an welcher Stelle Code im `NorthwindDataSet` dem `CustomersTableAdapter` hinzugefügt wird:  
  
    ```vb#  
    Partial Public Class CustomersTableAdapter  
        ' Add code here to add functionality   
        ' to the CustomersTableAdapter.  
    End Class  
    ```  
  
    ```c#  
    public partial class CustomersTableAdapter  
    {  
        // Add code here to add functionality  
        // to the CustomersTableAdapter.  
    }  
    ```  
  
## Siehe auch  
 [Übersicht über N\-Tier\-Datenanwendungen](../data-tools/n-tier-data-applications-overview.md)   
 [Gewusst wie: Hinzufügen von Code zu DataSets in N\-Tier\-Anwendungen](../data-tools/add-code-to-datasets-in-n-tier-applications.md)   
 [TableAdapters](../Topic/TableAdapters.md)   
 [Übersicht über TableAdapterManager](../Topic/TableAdapterManager%20Overview.md)   
 [Übersicht über die hierarchische Aktualisierung](../Topic/Hierarchical%20Update%20Overview.md)   
 [Erstellen von Datenanwendungen](../data-tools/creating-data-applications.md)