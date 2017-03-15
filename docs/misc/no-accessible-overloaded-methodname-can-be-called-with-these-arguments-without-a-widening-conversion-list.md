---
title: "Keine zugreifbare &#252;berladene &#39;&lt;Methodenname&gt;&#39; kann mit diesen Argumenten aufgerufen werden, ohne dass eine erweiternde Konvertierung verwendet wird: &lt;Liste&gt;. | Microsoft Docs"
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
  - "vbrAmbiguousCall_WideningConversion2"
ms.assetid: 5e74f5cf-80bd-4b48-b58a-465f981ec694
caps.latest.revision: 9
caps.handback.revision: 9
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# Keine zugreifbare &#252;berladene &#39;&lt;Methodenname&gt;&#39; kann mit diesen Argumenten aufgerufen werden, ohne dass eine erweiternde Konvertierung verwendet wird: &lt;Liste&gt;.
Eine überladene Methode wurde aufgerufen, aber ohne eine erweiternde Konvertierung kann keine Methode mit der Liste der bereitgestellten Argumente abgeglichen werden.  
  
### So beheben Sie diesen Fehler  
  
-   Geben Sie `Option Strict Off` an.  
  
-   Ändern Sie die Argumente, um eine Übereinstimmung mit einer der Signaturen der überladenen Methode zu erzielen.  
  
## Siehe auch  
 [Widening and Narrowing Conversions](/dotnet/visual-basic/programming-guide/language-features/data-types/widening-and-narrowing-conversions)   
 [Option Strict Statement](/dotnet/visual-basic/language-reference/statements/option-strict-statement)