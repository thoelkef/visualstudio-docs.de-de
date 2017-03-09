---
title: "&#39;&lt;methode1&gt;&#39; und &#39;&lt;methode2&gt;&#39; k&#246;nnen sich nicht gegenseitig &#252;berladen, da sie sich nur durch R&#252;ckgabetypen unterscheiden. | Microsoft Docs"
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
  - "bc30301"
  - "vbc30301"
helpviewer_keywords: 
  - "BC30301"
ms.assetid: 5adc442b-9671-4d93-add8-42929b1a09b9
caps.latest.revision: 8
caps.handback.revision: 8
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# &#39;&lt;methode1&gt;&#39; und &#39;&lt;methode2&gt;&#39; k&#246;nnen sich nicht gegenseitig &#252;berladen, da sie sich nur durch R&#252;ckgabetypen unterscheiden.
Sie haben versucht, eine Methode mit einer anderen Methode zu überladen, die sich lediglich im Rückgabetyp von der ersten unterscheidet. Beim Überladen müssen Sie Versionen einer Methode anhand ihrer Argumentlisten unterscheiden; Ihnen stehen für die Unterscheidung der Methoden ausschließlich die Argumentlisten zur Verfügung.  
  
 **Fehler\-ID:** BC30301  
  
### So beheben Sie diesen Fehler  
  
-   Stellen Sie sicher, dass sich die Methoden in ihren Argumentlisten unterscheiden.  
  
## Siehe auch  
 [Procedure Overloading](/dotnet/visual-basic/programming-guide/language-features/procedures/procedure-overloading)   
 [Considerations in Overloading Procedures](/dotnet/visual-basic/programming-guide/language-features/procedures/considerations-in-overloading-procedures)