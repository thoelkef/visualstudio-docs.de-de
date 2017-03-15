---
title: "&quot;&lt;Eigenschaftsname1&gt;&quot; kann &quot;&lt;Eigenschaftsname2&gt;&quot; nicht &#252;berschreiben, da sie sich durch &quot;ReadOnly&quot; oder &quot;WriteOnly&quot; unterscheiden. | Microsoft Docs"
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
  - "vbc30362"
  - "bc30362"
helpviewer_keywords: 
  - "BC30362"
ms.assetid: 883deb25-e6db-403e-8c03-f580baf1afa9
caps.latest.revision: 8
caps.handback.revision: 8
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# &quot;&lt;Eigenschaftsname1&gt;&quot; kann &quot;&lt;Eigenschaftsname2&gt;&quot; nicht &#252;berschreiben, da sie sich durch &quot;ReadOnly&quot; oder &quot;WriteOnly&quot; unterscheiden.
Sie haben versucht, eine Eigenschaft mit einer zweiten Eigenschaft zu überschreiben, die sich von der ersten Eigenschaft nur durch `ReadOnly` oder `WriteOnly` unterscheidet.  
  
 **Fehler\-ID:** BC30362  
  
### So beheben Sie diesen Fehler  
  
-   Stellen Sie sicher, dass sich die Eigenschaften durch mehr als `ReadOnly` und `WriteOnly` unterscheiden.  
  
## Siehe auch  
 [NICHT IM BUILD: Überschreiben von Eigenschaften und Methoden](http://msdn.microsoft.com/de-de/2167e8f5-1225-4b13-9ebd-02591ba90213)   
 [Overrides](/dotnet/visual-basic/language-reference/modifiers/overrides)