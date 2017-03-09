---
title: "Gewusst wie: Erweitern der Funktionalit&#228;t eines TableAdapter | Microsoft Docs"
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
  - "Daten [Visual Studio], Erweitern von TableAdapters"
  - "Daten [Visual Studio], TableAdapters"
  - "TableAdapters, Hinzufügen von Funktionalität"
ms.assetid: 418249c8-c7f3-47ef-a94c-744cb6fe6aaf
caps.latest.revision: 11
caps.handback.revision: 7
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# Gewusst wie: Erweitern der Funktionalit&#228;t eines TableAdapter
Sie können die Funktionalität eines TableAdapter erweitern, indem Sie der partiellen Klassendatei des TableAdapter Code hinzufügen.  
  
 Der Code, der einen TableAdapter definiert, wird neu generiert, wenn im **Dataset\-Designer** Änderungen am TableAdapter vorgenommen werden oder wenn bei der Ausführung eines Assistenten, der die Konfiguration eines TableAdapter modifiziert, Änderungen vorgenommen werden.  Um zu verhindern, dass der Code beim erneuten Generieren eines TableAdapter gelöscht wird, fügen Sie den Code der partiellen Klassendatei des TableAdapter hinzu.  
  
 \(Mit partiellen Klassen können Sie Code für eine bestimmte Klasse auf mehrere physikalische Dateien aufteilen.  Weitere Informationen finden Sie unter [Partial](/dotnet/visual-basic/language-reference/modifiers/partial) bzw. [partial \(Typ\)](/dotnet/csharp/language-reference/keywords/partial-type).\)  
  
## Suchen von TableAdapters im Code  
 Während TableAdapters mit dem **Dataset\-Designer** entworfen werden, werden die generierten TableAdapter\-Klassen nicht als geschachtelte <xref:System.Data.DataSet>\-Klassen generiert.  TableAdapters befinden sich in einem Namespace, der auf dem Namen des dem TableAdapter zugeordneten Datasets basiert.  Wenn die Anwendung zum Beispiel ein Dataset mit dem Namen `HRDataSet` enthält, befinden sich die TableAdapters im `HRDataSetTableAdapters`\-Namespace.  \(Die Namenskonvention folgt diesem Muster: *DatasetName* \+ `TableAdapters`\).  
  
 Im folgenden Beispiel wird von einem TableAdapter mit dem Namen `CustomersTableAdapter` in einem Projekt mit einem `NorthwindDataSet` ausgegangen.  
  
#### So erstellen Sie eine partielle Klasse für einen TableAdapter  
  
1.  Fügen Sie dem Projekt eine neue Klasse hinzu, indem Sie im Menü **Projekt** die Option **Klasse hinzufügen** auswählen.  
  
2.  Geben Sie der Klasse den Namen `CustomersTableAdapterExtended`.  
  
3.  Klicken Sie auf **Hinzufügen**.  
  
4.  Ersetzen Sie den Code durch den Namen, der dem Namespace und der partiellen Klasse für das Projekt entspricht.  Beispiele:  
  
     [!code-cs[VbRaddataTableAdapters#2](../data-tools/codesnippet/CSharp/extend-the-functionality-of-a-tableadapter_1.cs)]
     [!code-vb[VbRaddataTableAdapters#2](../data-tools/codesnippet/VisualBasic/extend-the-functionality-of-a-tableadapter_1.vb)]  
  
## Siehe auch  
 [Übersicht über TableAdapters](../data-tools/tableadapter-overview.md)   
 [Gewusst wie: Erstellen von TableAdapters](../data-tools/create-and-configure-tableadapters.md)   
 [Gewusst wie: Erstellen von TableAdapter\-Abfragen](../data-tools/how-to-create-tableadapter-queries.md)   
 [Gewusst wie: Erweitern der Funktionen eines Datasets](../Topic/How%20to:%20Extend%20the%20Functionality%20of%20a%20Dataset.md)   
 [Exemplarische Vorgehensweisen zur Arbeit mit Daten](../Topic/Data%20Walkthroughs.md)   
 [Binden von Windows Forms\-Steuerelementen an Daten in Visual Studio](../data-tools/bind-windows-forms-controls-to-data-in-visual-studio.md)   
 [Übersicht über Datenanwendungen in Visual Studio](../data-tools/overview-of-data-applications-in-visual-studio.md)   
 [Herstellen von Datenverbindungen in Visual Studio](../data-tools/connecting-to-data-in-visual-studio.md)   
 [Vorbereiten der Anwendung auf den Empfang von Daten](../Topic/Preparing%20Your%20Application%20to%20Receive%20Data.md)   
 [Abrufen von Daten für die Anwendung](../data-tools/fetching-data-into-your-application.md)   
 [Binden von Steuerelementen an Daten in Visual Studio](../data-tools/bind-controls-to-data-in-visual-studio.md)   
 [Bearbeiten von Daten in der Anwendung](../data-tools/editing-data-in-your-application.md)   
 [Überprüfen von Daten](../Topic/Validating%20Data.md)   
 [Speichern von Daten](../data-tools/saving-data.md)