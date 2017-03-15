---
title: "&#39;GoTo &lt;Bezeichnungsname&gt;&#39; ist ung&#252;ltig, da sich &#39;&lt;Bezeichnungsname&gt;&#39; innerhalb einer &#39;Try&#39;-, &#39;Catch&#39;- oder &#39;Finally&#39;-Anweisung befindet, die diese Anweisung nicht enth&#228;lt. | Microsoft Docs"
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
  - "bc30754"
  - "vbc30754"
helpviewer_keywords: 
  - "BC30754"
ms.assetid: 2eefc7fb-fdf0-41e9-bf60-c3bc93580e14
caps.latest.revision: 9
caps.handback.revision: 9
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# &#39;GoTo &lt;Bezeichnungsname&gt;&#39; ist ung&#252;ltig, da sich &#39;&lt;Bezeichnungsname&gt;&#39; innerhalb einer &#39;Try&#39;-, &#39;Catch&#39;- oder &#39;Finally&#39;-Anweisung befindet, die diese Anweisung nicht enth&#228;lt.
Sie können nicht in einen `Try...Catch...Finally`\-Block verzweigen.  
  
 **Fehler\-ID:** BC30754  
  
### So beheben Sie diesen Fehler  
  
-   Strukturieren Sie Ihren Code so um, dass die Beschriftung dem `Try...Catch...Finally`\-Block vorangeht.  
  
## Siehe auch  
 [Try...Catch...Finally Statement](/dotnet/visual-basic/language-reference/statements/try-catch-finally-statement)