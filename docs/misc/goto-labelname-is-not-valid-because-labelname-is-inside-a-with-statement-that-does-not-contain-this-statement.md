---
title: "&quot;GoTo &lt;Bezeichnungsname&gt;&quot; ist ung&#252;ltig, da sich &quot;&lt;Bezeichnungsname&gt;&quot; innerhalb einer With-Anweisung befindet, die diese Anweisung nicht enth&#228;lt. | Microsoft Docs"
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
  - "bc30756"
  - "vbc30756"
helpviewer_keywords: 
  - "BC30756"
ms.assetid: 9c39d4ad-0b9b-45e9-b6c2-d983144b5b23
caps.latest.revision: 9
caps.handback.revision: 9
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# &quot;GoTo &lt;Bezeichnungsname&gt;&quot; ist ung&#252;ltig, da sich &quot;&lt;Bezeichnungsname&gt;&quot; innerhalb einer With-Anweisung befindet, die diese Anweisung nicht enth&#228;lt.
`GoTo`\-Anweisungen sind auf Sprünge innerhalb des aktuellen Codeblocks beschränkt.  
  
 **Fehler\-ID:** BC30756  
  
### So beheben Sie diesen Fehler  
  
-   Strukturieren Sie den Code um, sodass sich die `GoTo`\-Anweisung und die Bezeichnung innerhalb des `With`\-Blocks befinden.  
  
## Siehe auch  
 [GoTo Statement](/dotnet/visual-basic/language-reference/statements/goto-statement)