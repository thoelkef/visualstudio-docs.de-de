---
title: "&#39;&lt;Methode1&gt;&#39; und &#39;&lt;Methode2&gt;&#39; k&#246;nnen sich nicht gegenseitig &#252;berladen, da sie sich nur durch Parameter unterscheiden, die als &#39;ParamArray&#39; deklariert sind. | Microsoft Docs"
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
  - "bc30368"
  - "vbc30368"
helpviewer_keywords: 
  - "BC30368"
ms.assetid: 6111df0c-fc3e-40b2-b536-effbd132ef72
caps.latest.revision: 8
caps.handback.revision: 8
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# &#39;&lt;Methode1&gt;&#39; und &#39;&lt;Methode2&gt;&#39; k&#246;nnen sich nicht gegenseitig &#252;berladen, da sie sich nur durch Parameter unterscheiden, die als &#39;ParamArray&#39; deklariert sind.
Sie haben versucht, zwei Methoden zu überladen, die sich nur durch einen oder mehrere `ParamArray`\-Parameter unterscheiden. Der Compiler betrachtet eine Prozedur mit einem `ParamArray`\-Parameter als Prozedur mit unendlicher Anzahl von Überladungen, die sich dadurch voneinander unterscheiden, was an das Parameterarray übergeben wird.  
  
 **Fehler\-ID:** BC30368  
  
### So beheben Sie diesen Fehler  
  
-   Stellen Sie sicher, dass sich die Methoden durch mehr als die `ParamArray`\-Parameter unterscheiden.  
  
## Siehe auch  
 [Considerations in Overloading Procedures](/dotnet/visual-basic/programming-guide/language-features/procedures/considerations-in-overloading-procedures)   
 [Parameter Arrays](/dotnet/visual-basic/programming-guide/language-features/procedures/parameter-arrays)