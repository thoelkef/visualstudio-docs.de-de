---
title: "Methoden, die als &quot;Overrides&quot; deklariert sind, k&#246;nnen nicht als &quot;Overridable&quot; deklariert werden, da sie implizit &#252;berschreibbar sind. | Microsoft Docs"
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
  - "bc30730"
  - "vbc30730"
helpviewer_keywords: 
  - "BC30730"
ms.assetid: cc892f81-eb1f-42a9-8f54-eff352adb5dd
caps.latest.revision: 8
caps.handback.revision: 8
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# Methoden, die als &quot;Overrides&quot; deklariert sind, k&#246;nnen nicht als &quot;Overridable&quot; deklariert werden, da sie implizit &#252;berschreibbar sind.
Im Gegensatz zu den meisten Methoden können mit dem `Overrides`\-Modifizierer markierte Methoden standardmäßig überschrieben werden.  
  
 **Fehler\-ID:** BC30730  
  
### So beheben Sie diesen Fehler  
  
-   Verzichten Sie bei Methoden, die mit dem `Overrides`\-Modifizierer markiert sind, auf den `Overridable`\-Modifizierer.  
  
## Siehe auch  
 [Overrides](/dotnet/visual-basic/language-reference/modifiers/overrides)   
 [Overridable](/dotnet/visual-basic/language-reference/modifiers/overridable)