---
title: "&quot;&lt;Methode1&gt;&quot; kann &quot;&lt;Methode2&gt;&quot; nicht &#252;berschreiben, da sie sich durch einen als &quot;ByRef&quot; bzw. &quot;ByVal&quot; gekennzeichneten Parameter unterscheiden | Microsoft Docs"
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
  - "vbc30398"
  - "bc30398"
helpviewer_keywords: 
  - "BC30398"
ms.assetid: 78d62276-4ad9-4876-8c35-a30c9c195638
caps.latest.revision: 8
caps.handback.revision: 8
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# &quot;&lt;Methode1&gt;&quot; kann &quot;&lt;Methode2&gt;&quot; nicht &#252;berschreiben, da sie sich durch einen als &quot;ByRef&quot; bzw. &quot;ByVal&quot; gekennzeichneten Parameter unterscheiden
Sie haben versucht, eine Methode mit einer anderen Methode zu überschreiben, die sich durch einen als `ByRef` anstelle von `ByVal` gekennzeichneten Parameter unterscheidet. Überschriebene Member müssen die gleichen Argumente wie die geerbten Member aus der Basisklasse aufweisen.  
  
 **Fehler\-ID:** BC30398  
  
### So beheben Sie diesen Fehler  
  
-   Stellen Sie sicher, dass die Parameter beide `ByRef` oder `ByVal` sind.  
  
## Siehe auch  
 [NICHT IM BUILD: Überschreiben von Eigenschaften und Methoden](http://msdn.microsoft.com/de-de/2167e8f5-1225-4b13-9ebd-02591ba90213)   
 [Passing Arguments by Value and by Reference](/dotnet/visual-basic/programming-guide/language-features/procedures/passing-arguments-by-value-and-by-reference)