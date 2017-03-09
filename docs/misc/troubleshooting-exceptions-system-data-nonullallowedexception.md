---
title: "Problembehandlung bei Ausnahmen: System.Data.NoNullAllowedException | Microsoft Docs"
ms.custom: ""
ms.date: "10/29/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-csharp"
ms.tgt_pltfrm: ""
ms.topic: "article"
dev_langs: 
  - "JScript"
  - "VB"
  - "CSharp"
  - "C++"
helpviewer_keywords: 
  - "NoNullAllowedException-Klasse"
ms.assetid: 1ab87572-007f-4b84-bb13-c3626e7f89cd
caps.latest.revision: 15
caps.handback.revision: 15
author: "mikeblome"
ms.author: "mblome"
manager: "douge"
---
# Problembehandlung bei Ausnahmen: System.Data.NoNullAllowedException
Bei dem Versuch, einen NULL\-Wert in eine Spalte einzufügen, bei der <xref:System.Data.NoNullAllowedException> auf <xref:System.Data.DataColumn.AllowDBNull%2A> festgelegt wurde, wird eine `false`\-Ausnahme ausgelöst.  
  
## Tipps  
 **Überprüfen Sie vor dem Hinzufügen zu einer Spalte, ob der Wert DBNull ist.**  
 Wenn <xref:System.Data.DataColumn.AllowDBNull%2A> auf `false` festgelegt wurde, können Sie keinen NULL\-Wert einfügen. Weitere Informationen finden Sie unter <xref:System.DBNull>.  
  
 **Legen Sie AllowDBNull auf true fest.**  
 Indem Sie diese Eigenschaft auf `true` festlegen, können Sie NULL\-Werte einfügen. Weitere Informationen finden Sie unter <xref:System.Data.DataColumn.AllowDBNull%2A>.  
  
## Hinweise  
 Wenn Sie mit den Navigationsschaltflächen durch die Datensätze einer Datenbanktabelle in einem Datenformular navigieren, kann es passieren, dass diese Ausnahme mit der zusätzlichen Meldung "Für die Spalte ''Spalte'' ist NULL nicht zulässig." ausgelöst wird. Dieses Verhalten tritt auf, weil der Primärschlüssel oder die "NOT NULL"\-Spalte der Datenbanktabelle im Datenformular\-Assistent nicht ausgewählt wurde. Wenn beim Erstellen des Datenformulars der Primärschlüssel oder die "NOT NULL"\-Spalte der Datenbank im Datenformular\-Assistent nicht ausgewählt wird, ist die Option **Hinzufügen \- Erstellt einen neuen Datensatz** nicht deaktiviert. Um dieses Problem zu umgehen, wählen Sie beim Hinzufügen eines Datenformulars mit dem Datenformular\-Assistenten die folgenden Spalten der ausgewählten Tabelle aus: die primäre Spalte und eine Spalte, für die NULL nicht zulässig ist.  
  
## Siehe auch  
 <xref:System.Data.NoNullAllowedException>   
 <xref:System.Data.DataRowCollection.Add%2A>   
 <xref:System.Data.DataRow.EndEdit%2A>   
 <xref:System.Data.DataRow.ItemArray%2A>   
 <xref:System.Data.DataTable.LoadDataRow%2A>   
 [Use the Exception Assistant](../Topic/How%20to:%20Use%20the%20Exception%20Assistant.md)