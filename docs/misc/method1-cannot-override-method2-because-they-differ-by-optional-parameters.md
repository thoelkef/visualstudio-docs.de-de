---
title: "&#39;&lt;methode1&gt;&#39; kann &#39;&lt;methode2&gt;&#39; nicht &#252;berschreiben, da sie sich in den optionalen Parametern unterscheiden | Microsoft Docs"
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
  - "vbc30308"
  - "bc30308"
helpviewer_keywords: 
  - "BC30308"
ms.assetid: 591dc351-4b87-4e92-81e1-2c1ff51da295
caps.latest.revision: 8
caps.handback.revision: 8
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# &#39;&lt;methode1&gt;&#39; kann &#39;&lt;methode2&gt;&#39; nicht &#252;berschreiben, da sie sich in den optionalen Parametern unterscheiden
Sie haben versucht, eine Methode mit einer anderen Methode zu überschreiben, die sich von der ersten in den Werten ihrer optionalen Parameter unterscheidet, was bedeutet, dass sich ihre Signaturen unterscheiden. Ein Typ kann eine geerbte überschreibbare Methode durch Deklarieren einer Methode mit gleichem Namen und gleicher Signatur überschreiben, die mit dem Modifizierer `Overrides` gekennzeichnet ist.  
  
 **Fehler\-ID:** BC30308  
  
### So beheben Sie diesen Fehler  
  
-   Stellen Sie sicher, dass die beiden Methoden die gleiche Signatur haben.  
  
## Siehe auch  
 [NICHT IM BUILD: Überschreiben von Eigenschaften und Methoden](http://msdn.microsoft.com/de-de/2167e8f5-1225-4b13-9ebd-02591ba90213)   
 [Overrides](/dotnet/visual-basic/language-reference/modifiers/overrides)