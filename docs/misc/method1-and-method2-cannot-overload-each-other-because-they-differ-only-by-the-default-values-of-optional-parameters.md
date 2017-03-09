---
title: "&#39;&lt;Methode1&gt;&#39; und &#39;&lt;Methode2&gt;&#39; k&#246;nnen sich nicht gegenseitig &#252;berladen, da sich nur die Standardwerte der optionalen Parameter unterscheiden. | Microsoft Docs"
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
  - "vbc30305"
  - "bc30305"
helpviewer_keywords: 
  - "BC30305"
ms.assetid: f07f925e-9f95-4885-bdba-eaba2d0483d8
caps.latest.revision: 8
caps.handback.revision: 8
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# &#39;&lt;Methode1&gt;&#39; und &#39;&lt;Methode2&gt;&#39; k&#246;nnen sich nicht gegenseitig &#252;berladen, da sich nur die Standardwerte der optionalen Parameter unterscheiden.
Sie haben versucht, eine Methode mit einer anderen Methode zu überladen, die sich lediglich in ihren optionalen Parametern von der ersten unterscheidet. Eine Methode mit einem optionalen Parameter ist zu zwei überladenen Methoden äquivalent, eine mit dem optionalen Parameter, die andere ohne ihn. Aus diesem Grund können Sie keine Methode mit einer Argumentliste überladen, die einer von beiden entspricht.  
  
 **Fehler\-ID:** BC30305  
  
### So beheben Sie diesen Fehler  
  
-   Stellen Sie sicher, dass sich die Methoden durch mehr als nur optionale Parameter unterscheiden.  
  
## Siehe auch  
 [Procedure Overloading](/dotnet/visual-basic/programming-guide/language-features/procedures/procedure-overloading)   
 [Considerations in Overloading Procedures](/dotnet/visual-basic/programming-guide/language-features/procedures/considerations-in-overloading-procedures)