---
title: "Gewusst wie: Deaktivieren von Einschr&#228;nkungen beim Auff&#252;llen von Datasets | Microsoft Docs"
ms.custom: ""
ms.date: "10/06/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "DataRow.BeginEdit"
  - "DataRow.EndEdit"
  - "DataRow.CancelEdit"
dev_langs: 
  - "VB"
  - "CSharp"
  - "C++"
  - "aspx"
helpviewer_keywords: 
  - "Einschränkungen [Visual Basic], Datasets"
  - "Einschränkungen [Visual Basic], Unterbrechen während der Datasetaktualisierung"
  - "Datasets [Visual Basic], Einschränkungen"
  - "Aktualisieren von Datasets, Einschränkungen"
ms.assetid: 553f7d0c-2faa-4c17-b226-dd02855bf1dc
caps.latest.revision: 18
caps.handback.revision: 15
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# Gewusst wie: Deaktivieren von Einschr&#228;nkungen beim Auff&#252;llen von Datasets
Wenn ein Dataset Einschränkungen enthält \(z. B. eine Fremdschlüsseleinschränkung\), werden je nach Reihenfolge der für das Dataset ausgeführten Vorgänge möglicherweise Ausnahmen ausgelöst.  Wenn z. B. untergeordnete Datensätze vor den zugehörigen übergeordneten Datensätzen geladen werden, wird möglicherweise die Einschränkung verletzt und eine Ausnahme ausgelöst.  Sobald Sie einen untergeordneten Datensatz laden, überprüft die Einschränkung das Vorhandensein des übergeordneten Datensatzes und löst einen Fehler aus.  Ohne einen Mechanismus, der die vorübergehende Aufhebung der Einschränkung zulässt, würde der Fehler bei jedem Versuch ausgelöst, einen Datensatz in die untergeordnete Tabelle zu laden.  Es besteht außerdem die Möglichkeit, alle Einschränkungen in einem Dataset mit der <xref:System.Data.DataRow.BeginEdit%2A>\-Eigenschaft und der <xref:System.Data.DataRow.EndEdit%2A>\-Eigenschaft aufzuheben.  
  
> [!NOTE]
>  Validierungsereignisse \(z. B. <xref:System.Data.DataTable.ColumnChanging>, <xref:System.Data.DataTable.RowChanging> usw.\) werden nicht ausgelöst, wenn die Einschränkungen aufgehoben werden.  
  
### So heben Sie Aktualisierungseinschränkungen programmgesteuert auf  
  
-   Im folgenden Beispiel wird veranschaulicht, wie die Einschränkungsüberprüfung in einem Dataset vorübergehend deaktiviert wird:  
  
     [!code-cs[VbRaddataEditing#10](../data-tools/codesnippet/CSharp/turn-off-constraints-while-filling-a-dataset_1.cs)]
     [!code-vb[VbRaddataEditing#10](../data-tools/codesnippet/VisualBasic/turn-off-constraints-while-filling-a-dataset_1.vb)]  
  
### So heben Sie Aktualisierungseinschränkungen mit dem Dataset\-Designer auf  
  
1.  Öffnen Sie das Dataset im [Erstellen und Bearbeiten von typisierten Datasets](../data-tools/creating-and-editing-typed-datasets.md).  Weitere Informationen finden Sie unter [Gewusst wie: Öffnen eines Datasets im DataSet\-Designer](../Topic/How%20to:%20Open%20a%20Dataset%20in%20the%20Dataset%20Designer.md).  
  
2.  Legen Sie im **Eigenschaftenfenster** die <xref:System.Data.DataSet.EnforceConstraints%2A>\-Eigenschaft auf `false` fest.  
  
## Siehe auch  
 [Speichern von Daten in Datasets](../data-tools/save-data-back-to-the-database.md)   
 [Bearbeiten von Daten in der Anwendung](../data-tools/editing-data-in-your-application.md)   
 [Exemplarische Vorgehensweisen zur Arbeit mit Daten](../Topic/Data%20Walkthroughs.md)   
 [Binden von Windows Forms\-Steuerelementen an Daten in Visual Studio](../data-tools/bind-windows-forms-controls-to-data-in-visual-studio.md)   
 [Übersicht über Datenanwendungen in Visual Studio](../data-tools/overview-of-data-applications-in-visual-studio.md)   
 [Herstellen von Datenverbindungen in Visual Studio](../data-tools/connecting-to-data-in-visual-studio.md)   
 [Vorbereiten der Anwendung auf den Empfang von Daten](../Topic/Preparing%20Your%20Application%20to%20Receive%20Data.md)   
 [Abrufen von Daten für die Anwendung](../data-tools/fetching-data-into-your-application.md)   
 [Binden von Steuerelementen an Daten in Visual Studio](../data-tools/bind-controls-to-data-in-visual-studio.md)   
 [Überprüfen von Daten](../Topic/Validating%20Data.md)   
 [Speichern von Daten](../data-tools/saving-data.md)