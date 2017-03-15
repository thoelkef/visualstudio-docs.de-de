---
title: "&#39;Continue While&#39; darf nur innerhalb einer While-Anweisung verwendet werden. | Microsoft Docs"
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
  - "vbc30784"
  - "bc30784"
helpviewer_keywords: 
  - "BC30784"
ms.assetid: b26c77b2-36ae-4dce-b048-f7c4b196faa4
caps.latest.revision: 9
caps.handback.revision: 9
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# &#39;Continue While&#39; darf nur innerhalb einer While-Anweisung verwendet werden.
Eine `Continue While`\-Anweisung kann nur innerhalb einer `For...Next`\-Schleife verwendet werden.  
  
 **Fehler\-ID:** BC30784  
  
### So beheben Sie diesen Fehler  
  
1.  Wenn sich die `Continue While`\-Anweisung in einer `Do...Loop`\-Schleife befindet, müssen Sie die Anweisung in `Continue Do` ändern.  
  
2.  Wenn sich die `Continue While`\-Anweisung in einer `For...Next`\-Schleife befindet, müssen Sie die Anweisung in `Continue For` ändern.  
  
3.  Entfernen Sie andernfalls die `Continue While`\-Anweisung.  
  
## Siehe auch  
 [Continue Statement](/dotnet/visual-basic/language-reference/statements/continue-statement)   
 [While...End While Statement](/dotnet/visual-basic/language-reference/statements/while-end-while-statement)