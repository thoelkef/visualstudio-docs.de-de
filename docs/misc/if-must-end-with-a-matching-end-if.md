---
title: "&#39;If&#39; muss mit einem entsprechenden &#39;End If&#39; abgeschlossen werden. | Microsoft Docs"
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
  - "bc30081"
  - "vbc30081"
helpviewer_keywords: 
  - "BC30081"
ms.assetid: e5905d59-56bb-4daf-aca5-5ff847fc62f6
caps.latest.revision: 9
caps.handback.revision: 9
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# &#39;If&#39; muss mit einem entsprechenden &#39;End If&#39; abgeschlossen werden.
Eine `If`\-Anweisung tritt ohne entsprechende `End If`\-Anweisung auf. Zum Beenden des `If`\-Blocks muss eine `End If`\-Anweisung verwendet werden.  
  
 **Fehler\-ID:** BC30081  
  
### So beheben Sie diesen Fehler  
  
1.  Wenn dieser `If`\-Block Teil einer Reihe von geschachtelten `If`\-Blöcken ist, stellen Sie sicher, dass jeder Block korrekt beendet wird.  
  
2.  Fügen Sie eine `End If`\-Anweisung am Ende des `If`\-Blocks hinzu.  
  
## Siehe auch  
 [If...Then...Else Statement](/dotnet/visual-basic/language-reference/statements/if-then-else-statement)