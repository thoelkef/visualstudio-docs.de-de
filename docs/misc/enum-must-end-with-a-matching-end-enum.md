---
title: "&quot;Enum&quot; muss mit einem entsprechenden &quot;End Enum&quot; abgeschlossen werden. | Microsoft Docs"
ms.custom: ""
ms.date: "11/24/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-visual-basic"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "vbc30185"
  - "bc30185"
helpviewer_keywords: 
  - "BC30185"
ms.assetid: 43dd759c-1207-4dcc-b2e2-478d91e6f2f8
caps.latest.revision: 7
caps.handback.revision: 7
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# &quot;Enum&quot; muss mit einem entsprechenden &quot;End Enum&quot; abgeschlossen werden.
Eine `Enum`\-Anweisung tritt ohne entsprechende `End Enum`\-Anweisung auf. Zum Beenden der Enumeration muss eine `End Enum`\-Anweisung angegeben werden.  
  
 **Fehler\-ID:** BC30185  
  
### So beheben Sie diesen Fehler  
  
1.  Überprüfen Sie, ob die `Enum`\-Member korrekt formatiert sind.  
  
2.  Fügen Sie am Ende der Enumeration eine `End Enum`\-Anweisung hinzu.  
  
## Siehe auch  
 [Enum Statement](/dotnet/visual-basic/language-reference/statements/enum-statement)