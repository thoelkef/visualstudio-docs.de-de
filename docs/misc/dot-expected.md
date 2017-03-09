---
title: "&quot;.&quot; erwartet | Microsoft Docs"
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
  - "bc30287"
  - "vbc30287"
helpviewer_keywords: 
  - "BC30287"
ms.assetid: 7d7b4934-b521-4ed3-b054-aeb71f8daacf
caps.latest.revision: 12
caps.handback.revision: 12
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# &quot;.&quot; erwartet
Der Code enthält eine `Handles`\-Klausel mit einem Ausrufezeichen \(`!`\).  
  
 **Fehler\-ID:** BC30287  
  
### So beheben Sie diesen Fehler  
  
1.  Wenn die `Handles`\-Klausel auf ein Ereignis in einem Objekt verweist, verwenden Sie einen Punkt \(`.`\), um das Objekt von dem Ereignis zu trennen.  
  
     In diesem Beispiel wird das `Click`\-Ereignis aus dem `Button1`\-Objekt behandelt.  
  
     [!code-vb[VbVbalrEventError#21](../misc/codesnippet/VisualBasic/dot-expected_1.vb)]  
  
## Siehe auch  
 [Handles](/dotnet/visual-basic/language-reference/statements/handles-clause)