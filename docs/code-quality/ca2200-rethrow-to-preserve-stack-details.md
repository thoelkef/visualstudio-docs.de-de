---
title: "CA2200: Erneut ausf&#252;hren, um Stapeldetails beizubehalten | Microsoft Docs"
ms.custom: ""
ms.date: "12/02/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-devops-test"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "RethrowToPreserveStackDetails"
  - "CA2200"
helpviewer_keywords: 
  - "CA2200"
  - "RethrowToPreserveStackDetails"
ms.assetid: 046e1b98-c4dc-4515-874f-9c0de2285621
caps.latest.revision: 13
caps.handback.revision: 13
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# CA2200: Erneut ausf&#252;hren, um Stapeldetails beizubehalten
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

|||  
|-|-|  
|TypeName|RethrowToPreserveStackDetails|  
|CheckId|CA2200|  
|Kategorie \(Category\)|Microsoft.Usage|  
|Unterbrechende Änderung|Nicht unterbrechend|  
  
## Ursache  
 Eine Ausnahme wird erneut ausgelöst, und die Ausnahme wird in der `throw`\-Anweisung explizit angegeben.  
  
## Regelbeschreibung  
 Sobald eine Ausnahme ausgelöst wird, ist die Stapelüberwachung ein Teil der übertragenen Informationen.  Die Stapelüberwachung ist eine Liste der Methodenaufrufhierarchie. Sie beginnt mit der Methode, durch die die Ausnahme ausgelöst wird, und endet mit der Methode, durch die die Ausnahme abgefangen wird.  Wenn eine Ausnahme erneut ausgelöst wird, indem die Ausnahme in der `throw`\-Anweisung angegeben wird, wird die Stapelüberwachung bei der aktuellen Methode neu gestartet. Die Liste der aufgerufenen Methoden zwischen der ursprünglichen Methode, durch die die Ausnahme ausgelöst wird, und der aktuellen Methode geht dabei verloren.  Wenn die ursprünglichen Stapelinformationen mit der Ausnahme gespeichert werden sollen, verwenden Sie die `throw`\-Anweisung ohne Angabe der Ausnahme.  
  
## Behandeln von Verstößen  
 Um einen Verstoß gegen diese Regel zu beheben, lösen Sie die Ausnahme erneut aus, ohne die Ausnahme explizit anzugeben.  
  
## Wann sollten Warnungen unterdrückt werden?  
 Unterdrücken Sie keine Warnung dieser Regel.  
  
## Beispiel  
 Im folgenden Beispiel wird die `CatchAndRethrowExplicitly`\-Methode gezeigt, die gegen die Regel und eine Methode verstößt. Außerdem wird die `CatchAndRethrowImplicitly`\-Methode gezeigt, die der Regel entspricht.  
  
 [!code-cs[FxCop.Usage.Rethrow#1](../code-quality/codesnippet/CSharp/ca2200-rethrow-to-preserve-stack-details_1.cs)]
 [!code-vb[FxCop.Usage.Rethrow#1](../code-quality/codesnippet/VisualBasic/ca2200-rethrow-to-preserve-stack-details_1.vb)]