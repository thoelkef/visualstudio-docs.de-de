---
title: "&quot;End Class&quot; muss ein entsprechendes &quot;Class&quot; vorhergehen. | Microsoft Docs"
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
  - "vbc30460"
  - "bc30460"
helpviewer_keywords: 
  - "BC30460"
ms.assetid: 0e6989da-f281-4ac4-8579-b6d627be8de8
caps.latest.revision: 8
caps.handback.revision: 8
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# &quot;End Class&quot; muss ein entsprechendes &quot;Class&quot; vorhergehen.
`End Class` wird zum Beenden eines `Class`\-Blocks verwendet und kann daher nur am Ende des Blocks angegeben werden. Entweder ist `End Class` redundant, oder die `End Class`\-Anweisung befindet sich außerhalb des entsprechenden `Class`\-Blocks.  
  
 **Fehler\-ID:** BC30460  
  
### So beheben Sie diesen Fehler  
  
-   Suchen und entfernen Sie alle redundanten `End Class`\-Anweisungen.  
  
-   Verschieben Sie die `End Class`\-Anweisung an die gewünschte Position im Code.  
  
## Siehe auch  
 [End \<keyword\> Statement](../Topic/End%20%3Ckeyword%3E%20Statement%20\(Visual%20Basic\).md)