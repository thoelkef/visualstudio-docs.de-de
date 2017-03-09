---
title: "Beziehungen in Datasets | Microsoft Docs"
ms.custom: ""
ms.date: "12/14/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "vbData.Microsoft.VSDesigner.DataSource.DesignRelation"
  - "vbdata.Microsoft.VSDesigner.DataSource.DesignRelation"
dev_langs: 
  - "VB"
  - "CSharp"
  - "C++"
  - "aspx"
helpviewer_keywords: 
  - "Datasets [Visual Basic], Beziehungen"
  - "Beziehungen, Informationen über Beziehungen"
  - "Beziehungen, Datasets"
ms.assetid: cfe274f0-71fe-40f6-994e-7c7f6273c9ba
caps.latest.revision: 15
caps.handback.revision: 10
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# Beziehungen in Datasets
Ein Dataset kann verknüpfte Tabellen wie in einer relationalen Datenbank enthalten.  Das Objekt, das eine Beziehung zwischen Datentabellen erleichtert, ist ein **DataRelation**\-Objekt.  Die folgenden Themen enthalten Informationen zu ADO.NET\-**DataRelation**\-Objekten, zu deren Erstellung und dazu, wie Sie sie verwendet können, um mit Daten in verknüpften Tabellen zu arbeiten.  
  
 [!INCLUDE[note_settings_general](../data-tools/includes/note_settings_general_md.md)]  
  
## In diesem Abschnitt  
 [Einführung in DataRelation\-Objekte](../Topic/Introduction%20to%20DataRelation%20Objects.md)  
 Bietet eine Übersicht darüber, wie Sie mit Datasets Beziehungen zwischen Tabellen festlegen und diese Beziehungen nutzen können  
  
 [Gewusst wie: Erstellen von DataRelations mit dem Dataset\-Designer](../Topic/How%20to:%20Create%20DataRelations%20with%20the%20Dataset%20Designer.md)  
 Erläutert, wie Sie mit dem **Dataset\-Designer** ein <xref:System.Data.DataRelation>\-Objekt zu einem Dataset hinzufügen.  
  
 [Gewusst wie: Zugreifen auf Datensätze in verknüpften DataTables](../Topic/How%20to:%20Access%20Records%20in%20Related%20DataTables.md)  
 Erläutert, wie Sie programmgesteuert verknüpfte Datensätze in einem typisierten Dataset mit Tabellen in einer 1:n\-Beziehung zurückgeben.  
  
 [Exemplarische Vorgehensweise: Erstellen einer Beziehung zwischen Datentabellen](../Topic/Walkthrough:%20Creating%20a%20Relationship%20between%20Data%20Tables.md)  
 Bietet eine schrittweise Anleitung zum Erstellen zweier Datentabellen mit dem **Dataset\-Designer** und zum Hinzufügen einer Beziehung zwischen den Tabellen.  
  
## Referenz  
 <xref:System.Data.DataRelation>  
 Stellt eine Beziehung zwischen zwei einander unter\- bzw. übergeordneten T:System.Data.DataTable\-Objekten dar.  
  
 <xref:System.Data.DataRow.GetChildRows%2A>  
 Ruft die untergeordneten Zeilen aus einer T:System.Data.DataRow ab.  
  
 <xref:System.Data.DataRow.GetParentRow%2A>  
 Ruft die übergeordneten Zeilen aus einer T:System.Data.DataRow ab.  
  
 <xref:System.Data.Rule>  
 Gibt die Aktion an, die beim Erzwingen einer <xref:System.Data.ForeignKeyConstraint> ausgeführt wird.  
  
 <xref:System.Data.DataColumn.Unique%2A>  
 Ruft einen Wert ab, der angibt, ob die Werte in jeder Zeile der Spalte eindeutig sein müssen, oder legt diesen fest.  
  
 <xref:System.Data.Constraint>  
 Stellt eine Einschränkung dar, die für ein oder mehrere <xref:System.Data.DataColumn>\-Objekte erzwungen werden kann.  
  
## Verwandte Abschnitte  
 [Hinzufügen von 'DataRelations'](../Topic/Adding%20DataRelations.md)  
 Beschreibt das Erstellen von Beziehungen zwischen Tabellen in einem <xref:System.Data.DataSet>.  
  
 [Navigieren in 'DataRelations'](../Topic/Navigating%20DataRelations.md)  
 Beschreibt, wie Sie mit Beziehungen zwischen Tabellen in einem <xref:System.Data.DataSet> untergeordnete oder übergeordnete Zeilen in einer Parent\-Child\-Beziehung zurückgeben.  
  
 [Schachteln von 'DataRelations'](../Topic/Nesting%20DataRelations.md)  
 Erläutert die Bedeutung geschachtelter <xref:System.Data.DataRelation>\-Objekte beim Darstellen des <xref:System.Data.DataSet>\-Inhalts als XML\-Daten und beschreibt deren Erstellung.