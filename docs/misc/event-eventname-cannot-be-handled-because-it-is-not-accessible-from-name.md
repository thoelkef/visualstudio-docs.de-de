---
title: "Das Ereignis &#39;&lt;Ereignisname&gt;&#39; kann nicht verarbeitet werden, da es &#252;ber &#39;&lt;Name&gt;&#39; nicht zugreifbar ist. | Microsoft Docs"
ms.custom: ""
ms.date: "10/29/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-visual-basic"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "bc30585"
  - "vbc30585"
helpviewer_keywords: 
  - "BC30585"
ms.assetid: fe039f8f-be6f-4b52-86bd-d551c54b85cd
caps.latest.revision: 8
caps.handback.revision: 8
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# Das Ereignis &#39;&lt;Ereignisname&gt;&#39; kann nicht verarbeitet werden, da es &#252;ber &#39;&lt;Name&gt;&#39; nicht zugreifbar ist.
Sie haben versucht, ein Ereignis zu behandeln, auf das nicht zugegriffen werden kann. Wenn z. B. eine `Handles`\-Variable freigegeben wird, muss die Methode für die Ereignisbehandlung ebenfalls freigegeben werden.  
  
 **Fehler\-ID:** BC30585  
  
### So beheben Sie diesen Fehler  
  
1.  Stellen Sie sicher, dass auf das Ereignis zugegriffen werden kann.  
  
## Siehe auch  
 [NICHT IM BUILD: Ereignisse und Ereignishandler](http://msdn.microsoft.com/de-de/95074a0d-1cbc-4221-a95a-964185c7f962)