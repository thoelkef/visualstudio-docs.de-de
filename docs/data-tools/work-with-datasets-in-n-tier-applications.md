---
title: "Arbeiten mit Datasets in N-Tier-Anwendungen | Microsoft Docs"
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
  - "Daten [Visual Basic], N-Tier-Anwendungen"
  - "DataSet-Projekt [VS-N-Tier-Anwendungen]"
  - "Datasets [Visual Basic], N-Tier-Anwendungen"
  - "Verteilte Anwendungen [VS-N-Tier-Anwendungen]"
  - "Anwendungen auf mehreren Ebenen"
  - "Datenbankanwendungen auf mehreren Ebenen"
  - "N-Tier-Anwendungen"
  - "TableAdapters, N-Tier-Anwendungen"
  - "Ebenen, N-Tier-Anwendungen"
  - "Typisierte Datasets, N-Tier-Anwendungen"
ms.assetid: f6ae2ee0-ea5f-4a79-8f4b-e21c115afb20
caps.latest.revision: 22
caps.handback.revision: 20
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# Arbeiten mit Datasets in N-Tier-Anwendungen
*N\-Tier\-Datenanwendungen* sind datenzentrische Anwendungen, die in mehrere logische Ebenen \(oder *Tiers*\) unterteilt sind.  Anders ausgedrückt: Eine N\-Tier\-Datenanwendung ist eine Anwendung, die in mehrere Projekte unterteilt ist mit der Datenzugriffsebene, Geschäftslogikebene und der Präsentationsebene jeweils als eigenes Projekt.  Weitere Informationen finden Sie unter [Übersicht über N\-Tier\-Datenanwendungen](../data-tools/n-tier-data-applications-overview.md).  
  
 Typisierte DataSets wurden weiterentwickelt, damit die TableAdapters\-Klasse und die DataSet\-Klasse in gesonderten Projekten generiert werden können.  Damit ist es möglich, Anwendungsebenen schnell zu trennen und N\-Tier\-Datenanwendung zu erstellen.  
  
 Die N\-Tier\-Unterstützung in typisierten Datasets ermöglicht die iterative Entwicklung der Anwendungsarchitektur zu einem N\-Tier\-Design und beseitigt die Notwendigkeit, den Code manuell in mehr als ein Projekt zu trennen.  Beginnen Sie mit dem Design der Datenschicht, indem Sie [Erstellen und Bearbeiten von typisierten Datasets](../data-tools/creating-and-editing-typed-datasets.md) verwenden.  Wenn Sie soweit sind, dass Sie die Anwendungsarchitektur in ein N\-tier\-Design übernehmen können, legen Sie die Eigenschaft **DataSet\-Projekt** eines Datasets so fest, dass die Dataset\-Klasse in separaten Projekte erzeugt wird.  
  
## In diesem Abschnitt  
 [Gewusst wie: DataSets und TableAdapters in verschiedene Projekte aufteilen](../data-tools/separate-datasets-and-tableadapters-into-different-projects.md)  
 Beschreibt, wie die erstellte Dataset\-Klasse aus dem Projekt, das die generierten TableAdapter\-Klassen enthält, in ein neues bewegt wird.  
  
 [Gewusst wie: Hinzufügen von Code zu TableAdapters in N\-Tier\-Anwendungen](../data-tools/add-code-to-tableadapters-in-n-tier-applications.md)  
 Beschreibt, wie eine partielle Klasse generiert wird, in der Code für einen N\-Tier\-TableAdapter hinzugefügt werden kann.  
  
 [Gewusst wie: Hinzufügen von Code zu DataSets in N\-Tier\-Anwendungen](../data-tools/add-code-to-datasets-in-n-tier-applications.md)  
 Beschreibt, wie eine partielle Klasse generiert wird, in der Code für ein N\-Tier\-Dataset hinzugefügt werden kann.  
  
 [Gewusst wie: Hinzufügen von Validierungen zu einem N\-Tier\-DataSet](../data-tools/add-validation-to-an-n-tier-dataset.md)  
 Beschreibt, wo Code für das Durchführen der Validierung bei Datenänderungen hinzugefügt wird.  
  
 [Exemplarische Vorgehensweise: Erstellen einer N\-Tier\-Datenanwendung](../data-tools/walkthrough-creating-an-n-tier-data-application.md)  
 Liefert eine Schritt\-für\-Schritt\-Anleitung für das Erstellen eines typisierten Datasets und das Aufteilen des Codes für TableAdapter und Dataset in mehrere Projekte.  
  
 [Exemplarische Vorgehensweise: Hinzufügen von Validierungen zu einer N\-Tier\-Datenanwendung](../Topic/Walkthrough:%20Adding%20Validation%20to%20an%20N-Tier%20Data%20Application.md)  
 Enthält eine Schritt\-für\-Schritt\-Anleitung für das Hinzufügen einer Validierung der Anwendung in einer exemplarischen Vorgehensweise mit der N\-Tier\-Datenanwendung.  
  
## Referenz  
 <xref:System.Data.DataSet>  
  
 <xref:System.Data.TypedTableBase%601>  
  
## Verwandte Abschnitte  
 [Übersicht über N\-Tier\-Datenanwendungen](../data-tools/n-tier-data-applications-overview.md)  
  
 [Hierarchische Aktualisierung](../data-tools/hierarchical-update.md)  
  
 [Arbeiten mit Datasets in Visual Studio](../data-tools/dataset-tools-in-visual-studio.md)  
  
 [Zugreifen auf Daten in Visual Studio](../data-tools/accessing-data-in-visual-studio.md)  
  
 [Übersicht über TableAdapters](../data-tools/tableadapter-overview.md)  
  
 [N\-Tier\- und Remoteanwendungen mit LINQ to SQL](../Topic/N-Tier%20and%20Remote%20Applications%20with%20LINQ%20to%20SQL.md)