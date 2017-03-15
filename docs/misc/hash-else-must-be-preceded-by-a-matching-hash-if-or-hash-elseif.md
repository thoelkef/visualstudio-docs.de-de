---
title: "&quot;#Else&quot; muss ein entsprechendes &quot;#If&quot; oder &quot;#ElseIf&quot; voranstehen | Microsoft Docs"
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
  - "vbc30028"
  - "bc30028"
helpviewer_keywords: 
  - "BC30028"
ms.assetid: c6ed34de-d6ed-4227-9880-538055aff20a
caps.latest.revision: 12
caps.handback.revision: 12
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# &quot;#Else&quot; muss ein entsprechendes &quot;#If&quot; oder &quot;#ElseIf&quot; voranstehen
`#Else` ist eine Direktive für die bedingte Kompilierung. Einer `#Else`\-Direktive ist keine entsprechende `#If`\- oder `#ElseIf`\-Direktive vorangestellt.  
  
 **Fehler\-ID:** BC30028  
  
### So beheben Sie diesen Fehler  
  
1.  Stellen Sie sicher, dass eine vorausgehende `#If`\- oder `#ElseIf`\-Direktive nicht durch einen dazwischen liegenden Block für die bedingte Kompilierung oder eine falsch platzierte `#End If`\-Direktive von dieser `#Else`\-Direktive getrennt ist.  
  
2.  Überprüfen Sie, ob `#Else` eine andere `#Else`\-Direktive vorangestellt ist. Wenn dies der Fall ist, entfernen Sie `#Else`, oder ändern Sie die Direktive in `#ElseIf`.  
  
3.  Falls der Code ansonsten in Ordnung ist, fügen Sie am Anfang des Blocks für die bedingte Kompilierung eine `#If`\-Direktive hinzu.  
  
## Siehe auch  
 [\#If...Then...\#Else Directives](/dotnet/visual-basic/language-reference/directives/if-then-else-directives)