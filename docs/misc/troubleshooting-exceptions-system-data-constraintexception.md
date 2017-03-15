---
title: "Problembehandlung bei Ausnahmen: System.Data.ConstraintException | Microsoft Docs"
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
  - "ConstraintException-Klasse"
ms.assetid: 5e9ba3b8-73d5-4657-a76e-63ab6ea32cf1
caps.latest.revision: 19
caps.handback.revision: 19
author: "mikeblome"
ms.author: "mblome"
manager: "douge"
---
# Problembehandlung bei Ausnahmen: System.Data.ConstraintException
Eine <xref:System.Data.ConstraintException>\-Ausnahme wird ausgelöst, wenn versucht wird, eine Aktion auszuführen, die gegen eine Beschränkung verstößt.  
  
## Tipps  
 **Lockern Sie die Beschränkungen im Dataset, oder deaktivieren Sie diese**.  
 Sie können mithilfe der <xref:System.Data.DataSet.EnforceConstraints%2A>\-Eigenschaft Beschränkungen vorübergehend deaktivieren, solange Sie Tabellen in einem <xref:System.Data.DataSet>\-Objekt ausfüllen.  
  
 **Versuchen Sie nicht, einem Primärschlüsselfeld mit bereits vorhandenem Primärschlüssel einen Wert zuzuweisen.**  
 Wenn der Primärschlüssel bereits vorhanden ist, wird diese Ausnahme ausgelöst.  
  
 **Löschen Sie die DataSet\-Inhalte vor dem Laden aus dem Ansichtszustand.**  
 Diese Ausnahme wird möglicherweise ausgelöst, wenn während des Ladens im Dataset bereits Daten vorhanden sind.  
  
## Siehe auch  
 <xref:System.Data.ConstraintException>   
 [Use the Exception Assistant](../Topic/How%20to:%20Use%20the%20Exception%20Assistant.md)