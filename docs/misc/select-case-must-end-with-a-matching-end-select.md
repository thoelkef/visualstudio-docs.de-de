---
title: "&#39;Select Case&#39; muss mit einer entsprechenden &#39;End Select&#39;-Anweisung enden. | Microsoft Docs"
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
  - "vbc30095"
  - "bc30095"
helpviewer_keywords: 
  - "BC30095"
ms.assetid: f0809aa5-e6c9-43c9-9664-4ff02825c3d8
caps.latest.revision: 8
caps.handback.revision: 8
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# &#39;Select Case&#39; muss mit einer entsprechenden &#39;End Select&#39;-Anweisung enden.
Eine `Select`\- oder `Select Case`\-Anweisung ist ohne entsprechende `End Select`\-Anweisung aufgetreten. Zum Beenden des `Select`\-Blocks muss eine `End Select`\-Anweisung verwendet werden.  
  
 **Fehler\-ID:** BC30095  
  
### So beheben Sie diesen Fehler  
  
1.  Wenn dieser `Select`\-Block Teil einer Reihe von geschachtelten `Select`\-Blöcken ist, stellen Sie sicher, dass jeder Block ordnungsgemäß beendet wird.  
  
2.  Fügen Sie eine `End Select`\-Anweisung am Ende des `Select`\-Blocks hinzu.  
  
## Siehe auch  
 [Select...Case Statement](/dotnet/visual-basic/language-reference/statements/select-case-statement)