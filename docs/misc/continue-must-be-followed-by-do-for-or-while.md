---
title: "Auf &quot;Continue&quot; muss &quot;Do&quot;, &quot;For&quot; oder &quot;While&quot; folgen | Microsoft Docs"
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
  - "bc30781"
  - "vbc30781"
helpviewer_keywords: 
  - "BC30781"
ms.assetid: a0d5854d-ca44-4c6b-9458-4fc50d29281a
caps.latest.revision: 9
caps.handback.revision: 9
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# Auf &quot;Continue&quot; muss &quot;Do&quot;, &quot;For&quot; oder &quot;While&quot; folgen
Auf eine `Continue`\-Anweisung muss `Do`, `For` oder `While` folgen, und zwar abhängig davon, ob die `Continue`\-Anweisung in einer `Do...Loop`\-Schleife, einer `For...Next`\-Schleife oder einer `While...End While`\-Schleife angezeigt wird.  
  
 **Fehler\-ID:** BC30781  
  
### So beheben Sie diesen Fehler  
  
1.  Wenn sich die `Continue`\-Anweisung in einer `Do...Loop`\-Schleife befindet, müssen Sie die Anweisung in `Continue Do` ändern.  
  
2.  Wenn sich die `Continue`\-Anweisung in einer `For...Next`\-Schleife befindet, müssen Sie die Anweisung in `Continue For` ändern.  
  
3.  Wenn sich die `Continue`\-Anweisung in einer `While...End While`\-Schleife befindet, müssen Sie die Anweisung in `Continue While` ändern.  
  
4.  Entfernen Sie andernfalls die `Continue`\-Anweisung.  
  
## Siehe auch  
 [Continue Statement](/dotnet/visual-basic/language-reference/statements/continue-statement)