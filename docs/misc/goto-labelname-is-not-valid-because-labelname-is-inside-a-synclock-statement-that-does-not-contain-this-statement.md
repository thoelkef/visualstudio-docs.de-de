---
title: "&#39;GoTo &lt;bezeichnungsname&gt;&#39; ist ung&#252;ltig, da sich &#39;&lt;bezeichnungsname&gt;&#39;innerhalb einer &#39;SyncLock&#39;-Anweisung befindet, die diese Anweisung nicht enth&#228;lt. | Microsoft Docs"
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
  - "bc30755"
  - "vbc30755"
helpviewer_keywords: 
  - "BC30755"
ms.assetid: 95fb48c1-4982-45fc-81f0-f30cf0df173f
caps.latest.revision: 8
caps.handback.revision: 8
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# &#39;GoTo &lt;bezeichnungsname&gt;&#39; ist ung&#252;ltig, da sich &#39;&lt;bezeichnungsname&gt;&#39;innerhalb einer &#39;SyncLock&#39;-Anweisung befindet, die diese Anweisung nicht enth&#228;lt.
Sie können nicht in einen `SyncLock` branchen.  
  
 **Fehler\-ID:** BC30755  
  
### So beheben Sie diesen Fehler  
  
-   Strukturieren Sie Ihren Code so um, dass die Beschriftung dem `SyncLock`\-Block vorangeht.  
  
## Siehe auch  
 [SyncLock Statement](/dotnet/visual-basic/language-reference/statements/synclock-statement)