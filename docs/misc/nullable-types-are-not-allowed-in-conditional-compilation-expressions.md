---
title: "Typen, die NULL-Werte zulassen, sind in Ausdr&#252;cken f&#252;r die bedingte Kompilierung nicht zul&#228;ssig. | Microsoft Docs"
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
  - "bc33111"
  - "vbc33111"
helpviewer_keywords: 
  - "BC33111"
ms.assetid: 2c2587e5-2179-4a31-bcf7-7004db6f2d73
caps.latest.revision: 5
caps.handback.revision: 5
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# Typen, die NULL-Werte zulassen, sind in Ausdr&#252;cken f&#252;r die bedingte Kompilierung nicht zul&#228;ssig.
Ein Typ, der NULL\-Werte zulässt, kann nicht im Ausdruck eine Direktive für die bedingte Kompilierung verwendet werden. Beispielsweise verursacht der folgende Code diesen Fehler.  
  
```vb#  
'#Const triggerPoint = 0 '' Not valid. '#If CType(triggerpoint, Boolean?) = True Then '        ' Body of the conditional directive. '#End If  
```  
  
 **Fehler\-ID:** BC33111  
  
### So beheben Sie diesen Fehler  
  
-   Entfernen Sie die Typbezeichnung, die NULL\-Werte zulässt.  
  
## Siehe auch  
 [Nullable Value Types](/dotnet/visual-basic/programming-guide/language-features/data-types/nullable-value-types)   
 [\#If...Then...\#Else Directives](/dotnet/visual-basic/language-reference/directives/if-then-else-directives)   
 [Conditional Compilation](/dotnet/visual-basic/programming-guide/program-structure/conditional-compilation)