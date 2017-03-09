---
title: "&quot;Handles&quot; in Modulen muss eine WithEvents-Variable angeben, die durch einen einzelnen Bezeichner qualifiziert wird. | Microsoft Docs"
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
  - "bc31418"
  - "vbc31418"
helpviewer_keywords: 
  - "BC31418"
ms.assetid: 7d866577-1e42-43f1-85d1-5d7eeba881b2
caps.latest.revision: 11
caps.handback.revision: 11
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# &quot;Handles&quot; in Modulen muss eine WithEvents-Variable angeben, die durch einen einzelnen Bezeichner qualifiziert wird.
Um einen Ereignishandler zu definieren, müssen `Handles`\-Anweisungen eine Objektvariable angeben, die mit dem `WithEvents`\-Schlüsselwort deklariert wurde.  
  
 **Fehler\-ID:** BC31418  
  
### So beheben Sie diesen Fehler  
  
-   Verwenden Sie den `WithEvents`\-Modifizierer zum Deklarieren von Variablen, die mit der `Handles`\-Anweisung verwendet werden.  
  
## Siehe auch  
 [Handles](/dotnet/visual-basic/language-reference/statements/handles-clause)   
 [WithEvents](/dotnet/visual-basic/language-reference/modifiers/withevents)   
 [Events](/dotnet/visual-basic/programming-guide/language-features/events/events)