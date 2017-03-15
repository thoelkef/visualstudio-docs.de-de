---
title: "&quot;While&quot; muss mit einem entsprechenden &quot;End While&quot; abgeschlossen werden. | Microsoft Docs"
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
  - "bc30082"
  - "vbc30082"
helpviewer_keywords: 
  - "BC30082"
ms.assetid: 50b722b1-906f-4cb1-b5d4-fefab2ba3907
caps.latest.revision: 8
caps.handback.revision: 8
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# &quot;While&quot; muss mit einem entsprechenden &quot;End While&quot; abgeschlossen werden.
Eine `While`\-Anweisung tritt ohne entsprechende `End While`\-Anweisung auf. Zum Beenden des `While`\-Blocks muss eine `End While`\-Anweisung angegeben werden.  
  
 **Fehler\-ID:** BC30082  
  
### So beheben Sie diesen Fehler  
  
1.  Wenn dieser `While`\-Block Teil einer Reihe von geschachtelten `While`\-Blöcken ist, stellen Sie sicher, dass jeder Block korrekt beendet wird.  
  
2.  Fügen Sie eine `End While`\-Anweisung ans Ende des `While`\-Blocks hinzu.  
  
## Siehe auch  
 [While...End While Statement](/dotnet/visual-basic/language-reference/statements/while-end-while-statement)