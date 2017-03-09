---
title: "&lt;Methodenname&gt;&#39; und &#39;&lt;Methodenname&gt;&#39; k&#246;nnen sich nicht gegenseitig &#252;berladen, da sie sich nur durch &#39;ReadOnly&#39; oder &#39;WriteOnly&#39; unterscheiden. | Microsoft Docs"
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
  - "vbc30366"
  - "BC30366"
helpviewer_keywords: 
  - "BC30366"
ms.assetid: 2440fd29-e205-4004-b2ee-9d954d17b8d3
caps.latest.revision: 8
caps.handback.revision: 8
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# &lt;Methodenname&gt;&#39; und &#39;&lt;Methodenname&gt;&#39; k&#246;nnen sich nicht gegenseitig &#252;berladen, da sie sich nur durch &#39;ReadOnly&#39; oder &#39;WriteOnly&#39; unterscheiden.
Sie haben versucht, zwei Methoden zu überladen, die sich nur durch ihre `ReadOnly`\- und `WriteOnly`\-Deklarationen unterscheiden. Sie können nur die Argumentliste verwenden, um die Versionen zu unterscheiden.  
  
 **Fehler\-ID:** BC30366  
  
### So beheben Sie diesen Fehler  
  
-   Stellen Sie sicher, dass sich die Methoden durch mehr als `ReadOnly` und `WriteOnly` unterscheiden.  
  
## Siehe auch  
 [Considerations in Overloading Procedures](/dotnet/visual-basic/programming-guide/language-features/procedures/considerations-in-overloading-procedures)