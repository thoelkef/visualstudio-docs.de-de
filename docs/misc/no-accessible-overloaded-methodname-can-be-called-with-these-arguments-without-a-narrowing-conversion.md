---
title: "Keine zugreifbare &#252;berladene &#39;&lt;Methodenname&gt;&#39; kann mit diesen Argumenten aufgerufen werden, ohne dass eine einschr&#228;nkende Konvertierung verwendet wird. | Microsoft Docs"
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
  - "vbrAmbiguousMatch_NarrowingConversion1"
ms.assetid: 2fdbadb9-8ef1-404a-a2ed-ce5f5e55cfcb
caps.latest.revision: 9
caps.handback.revision: 9
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# Keine zugreifbare &#252;berladene &#39;&lt;Methodenname&gt;&#39; kann mit diesen Argumenten aufgerufen werden, ohne dass eine einschr&#228;nkende Konvertierung verwendet wird.
Eine überladene Methode wurde aufgerufen, aber ohne eine einschränkende Konvertierung kann keine Methode mit der Liste der bereitgestellten Argumente abgeglichen werden.  
  
### So beheben Sie diesen Fehler  
  
1.  Geben Sie `Option Strict Off` an.  
  
2.  Ändern Sie die Argumente, um eine Übereinstimmung mit einer der Signaturen der überladenen Methode zu erzielen.  
  
## Siehe auch  
 [Passing Arguments by Value and by Reference](/dotnet/visual-basic/programming-guide/language-features/procedures/passing-arguments-by-value-and-by-reference)   
 [Widening and Narrowing Conversions](/dotnet/visual-basic/programming-guide/language-features/data-types/widening-and-narrowing-conversions)