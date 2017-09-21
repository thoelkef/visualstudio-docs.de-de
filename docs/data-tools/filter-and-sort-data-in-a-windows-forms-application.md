---
title: "Gewusst wie: Filtern und Sortieren von Daten in einer Windows Forms-Anwendung | Microsoft Docs"
ms.custom: ""
ms.date: "12/15/2016"
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
  - "Datenansichten, Filtern"
  - "Datenansichten, Sortieren"
  - "Filtern von Datasets, Mit Datenansichten"
  - "Zeilenzustände"
  - "Zeilenzustände, Filtern"
  - "Zeilenversion, Filtern"
  - "Sortieren von Datasets, Mit Datenansichten"
ms.assetid: f4f100f1-776d-46dc-b2fd-5b35b98d9561
caps.latest.revision: 18
caps.handback.revision: 14
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# Gewusst wie: Filtern und Sortieren von Daten in einer Windows Forms-Anwendung
Daten können gefiltert werden, indem die <xref:System.Windows.Forms.BindingSource.Filter%2A>\-Eigenschaft auf einen Zeichenfolgenausdruck festlegt wird, der die gewünschten Datensätze zurückgibt.  
  
 Daten können sortiert werden, indem die <xref:System.Windows.Forms.BindingSource.Sort%2A>\-Eigenschaft auf den Spaltennamen festgelegt wird, nach dem sortiert werden soll. Fügen Sie `DESC` an, um in absteigender Reihenfolge zu sortieren, oder fügen Sie `ASC` an, um in aufsteigender Reihenfolge zu sortieren.  
  
> [!NOTE]
>  Wenn in der Anwendung keine <xref:System.Windows.Forms.BindingSource>\-Komponenten verwendet werden, können Daten mithilfe von <xref:System.Data.DataView>\-Objekten gefiltert und sortiert werden.  Weitere Informationen finden Sie unter [DataViews](../Topic/DataViews.md).  
  
### So filtern Sie Daten mithilfe einer BindingSource\-Komponente  
  
-   Legen Sie die <xref:System.Windows.Forms.BindingSource.Filter%2A>\-Eigenschaft auf den zurückzugebenden Ausdruck fest.  Im folgenden Code werden beispielsweise Kunden mit einem `CompanyName` zurückgegeben, der mit "B" beginnt:  
  
     [!code-cs[VbRaddataDisplaying#6](../data-tools/codesnippet/CSharp/filter-and-sort-data-in-a-windows-forms-application_1.cs)]
     [!code-vb[VbRaddataDisplaying#6](../data-tools/codesnippet/VisualBasic/filter-and-sort-data-in-a-windows-forms-application_1.vb)]  
  
### So sortieren Sie Daten mithilfe einer BindingSource\-Komponente  
  
-   Legen Sie die <xref:System.Windows.Forms.BindingSource.Sort%2A>\-Eigenschaft auf die Spalte fest, nach der sortiert werden soll.  Im folgenden Code werden beispielsweise Kunden in der Spalte `CompanyName` in absteigender Reihenfolge sortiert:  
  
     [!code-cs[VbRaddataDisplaying#7](../data-tools/codesnippet/CSharp/filter-and-sort-data-in-a-windows-forms-application_2.cs)]
     [!code-vb[VbRaddataDisplaying#7](../data-tools/codesnippet/VisualBasic/filter-and-sort-data-in-a-windows-forms-application_2.vb)]  
  
## Siehe auch  
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