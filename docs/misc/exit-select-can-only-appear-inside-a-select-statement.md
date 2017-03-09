---
title: "&quot;Exit Select&quot; kann nur innerhalb einer Select-Anweisung verwendet werden | Microsoft Docs"
ms.custom: ""
ms.date: "11/17/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-visual-basic"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "vbc30099"
  - "bc30099"
helpviewer_keywords: 
  - "BC30099"
ms.assetid: 37c65fc8-6ad9-456a-80b8-66288c62ef24
caps.latest.revision: 8
caps.handback.revision: 8
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# &quot;Exit Select&quot; kann nur innerhalb einer Select-Anweisung verwendet werden
Eine `Exit Select`\-Anweisung befindet sich außerhalb eines `Select`\-Blocks.`Exit Select` ist nur zwischen einer `Select`\- oder `Select Case`\-Anweisung und einer entsprechenden `End Select`\-Anweisung gültig.  
  
 **Fehler\-ID:** BC30099  
  
### So beheben Sie diesen Fehler  
  
1.  Stellen Sie sicher, dass eine gültige `Select`\- oder `Select Case`\-Anweisung vor `Exit Select` steht und eine gültige `End Select`\-Anweisung darauf folgt.  
  
2.  Stellen Sie sicher, dass andere Steuerungsstrukturen innerhalb des `Select`\-Blocks ordnungsgemäß beendet werden.  
  
## Siehe auch  
 [Select...Case Statement](/dotnet/visual-basic/language-reference/statements/select-case-statement)