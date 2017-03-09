---
title: "&quot;Exit Property&quot; ist ung&#252;ltig in Function oder Sub | Microsoft Docs"
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
  - "vbc30066"
  - "bc30066"
helpviewer_keywords: 
  - "BC30066"
ms.assetid: 09e7e766-e35d-4282-b949-d227f733f950
caps.latest.revision: 8
caps.handback.revision: 8
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# &quot;Exit Property&quot; ist ung&#252;ltig in Function oder Sub
`Exit Property` wird in einer `Function`\- oder `Sub`\-Prozedur verwendet. Eine `Exit`\-Anweisung muss dem Block entsprechen, in dem sie verwendet wird.  
  
 **Fehler\-ID:** BC30066  
  
### So beheben Sie diesen Fehler  
  
-   Ersetzen Sie `Exit Property` durch die `Exit Function`\- bzw. `Exit Sub`\-Anweisung.  
  
## Siehe auch  
 [Sub Procedures](/dotnet/visual-basic/programming-guide/language-features/procedures/sub-procedures)   
 [Function\-Prozeduren](/dotnet/visual-basic/programming-guide/language-features/procedures/function-procedures)   
 [Eigenschaftenprozeduren](/dotnet/visual-basic/programming-guide/language-features/procedures/property-procedures)