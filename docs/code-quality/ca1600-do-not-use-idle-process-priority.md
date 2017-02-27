---
title: "CA1600: Verwenden Sie keine Prozesse mit der Priorit&#228;t &quot;idle&quot; | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-devops-test"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "DoNotUseIdleProcessPriority"
  - "CA1600"
helpviewer_keywords: 
  - "CA1600"
  - "DoNotUseIdleProcessPriority"
ms.assetid: 9b0d073b-78b6-41be-8ef3-14692a735283
caps.latest.revision: 15
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
caps.handback.revision: 15
---
# CA1600: Verwenden Sie keine Prozesse mit der Priorit&#228;t &quot;idle&quot;
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

|||  
|-|-|  
|TypeName|DoNotUseIdleProcessPriority|  
|CheckId|CA1600|  
|Kategorie \(Category\)|Microsoft.Mobility|  
|Unterbrechende Änderung|Breaking|  
  
## Ursache  
 Diese Regel tritt auf, wenn Prozesse auf `ProcessPriorityClass.Idle` festgelegt werden.  
  
## Regelbeschreibung  
 Legen Sie für Prozesse nicht die Priorität Idle fest.  Prozesse, die über `System.Diagnostics.ProcessPriorityClass.Idle` verfügen, belegen die CPU, wenn sie sich andernfalls im Leerlauf befinden würde, und blockieren daher Standby.  
  
## Behandeln von Verstößen  
 Legen Sie Prozesse auf `ProcessPriorityClass.BelowNormal` fest.  
  
## Wann sollten Warnungen unterdrückt werden?  
 Diese Regel sollte nur dann unterdrückt werden, wenn für Prozesse die Priorität Idle erforderlich ist und Mobilitätsüberlegungen ohne Bedenken ignoriert werden können.