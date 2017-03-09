---
title: "„Using“ muss mit einer entsprechenden „End Using“-Anweisung enden. | Microsoft Docs"
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
  - "vbc36008"
  - "bc36008"
helpviewer_keywords: 
  - "BC36008"
ms.assetid: 83269108-b169-40a6-bbcc-af1ac8fcfd67
caps.latest.revision: 8
caps.handback.revision: 8
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# „Using“ muss mit einer entsprechenden „End Using“-Anweisung enden.
Eine `Using`\-Anweisung tritt ohne entsprechende `End Using`\-Anweisung auf.  
  
 Zum Beenden des `Using`\-Blocks muss eine `End Using`\-Anweisung angegeben werden.  
  
 **Fehler\-ID:** BC36008  
  
### So beheben Sie diesen Fehler  
  
1.  Wenn dieser `Using`\-Block Teil einer Reihe von geschachtelten `Using`\-Blöcken ist, stellen Sie sicher, dass jeder Block korrekt abgeschlossen wird.  
  
2.  Fügen Sie eine `End Using`\-Anweisung ans Ende des `Using`\-Blocks hinzu.  
  
## Siehe auch  
 [Using Statement](/dotnet/visual-basic/language-reference/statements/using-statement)   
 [How to: Dispose of a System Resource](../Topic/How%20to:%20Dispose%20of%20a%20System%20Resource%20\(Visual%20Basic\).md)