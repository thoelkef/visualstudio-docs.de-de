---
title: "Keine zugreifbare &#252;berladene &quot;&lt;Methodenname&gt;&quot; kann mit diesen Argumenten aufgerufen werden, ohne dass eine einschr&#228;nkende Konvertierung verwendet wird: &lt;Liste&gt;. | Microsoft Docs"
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
  - "vbrAmbiguousCall2"
ms.assetid: 13b20ffa-9f02-4971-a3cb-e08b402fd971
caps.latest.revision: 9
caps.handback.revision: 9
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# Keine zugreifbare &#252;berladene &quot;&lt;Methodenname&gt;&quot; kann mit diesen Argumenten aufgerufen werden, ohne dass eine einschr&#228;nkende Konvertierung verwendet wird: &lt;Liste&gt;.
Eine überladene Methode wurde aufgerufen, aber ohne eine einschränkende Konvertierung kann die Methode nicht mit der Liste der bereitgestellten Argumente abgeglichen werden.  
  
### So beheben Sie diesen Fehler  
  
1.  Geben Sie `Option``Strict` `Off` an.  
  
2.  Ändern Sie die Argumente, um eine Übereinstimmung mit einer Signatur der überladenen Methode zu erzielen.  
  
## Siehe auch  
 [Passing Arguments by Value and by Reference](/dotnet/visual-basic/programming-guide/language-features/procedures/passing-arguments-by-value-and-by-reference)   
 [Widening and Narrowing Conversions](/dotnet/visual-basic/programming-guide/language-features/data-types/widening-and-narrowing-conversions)