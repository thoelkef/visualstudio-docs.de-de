---
title: "&quot;Exit Do&quot; kann nur innerhalb einer Do-Anweisung verwendet werden. | Microsoft Docs"
ms.custom: ""
ms.date: "11/16/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-visual-basic"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "bc30089"
  - "vbc30089"
helpviewer_keywords: 
  - "BC30089"
ms.assetid: 0e1d0b35-e42b-4b90-b8a2-91fd6ef44f06
caps.latest.revision: 8
caps.handback.revision: 8
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# &quot;Exit Do&quot; kann nur innerhalb einer Do-Anweisung verwendet werden.
Eine `Exit Do`\-Anweisung befindet sich außerhalb einer `Do`\-Schleife.`Exit Do` ist nur zwischen einer `Do`\- und einer entsprechenden `Loop`\-Anweisung gültig.  
  
 **Fehler\-ID:** BC30089  
  
### So beheben Sie diesen Fehler  
  
1.  Stellen Sie sicher, dass eine gültige `Do`\-Anweisung vor `Exit Do` steht und eine gültige `Loop`\-Anweisung darauf folgt.  
  
2.  Stellen Sie sicher, dass andere Steuerungsstrukturen innerhalb der `Do`\-Schleife ordnungsgemäß abgeschlossen werden.  
  
## Siehe auch  
 [Do...Loop Statement](/dotnet/visual-basic/language-reference/statements/do-loop-statement)