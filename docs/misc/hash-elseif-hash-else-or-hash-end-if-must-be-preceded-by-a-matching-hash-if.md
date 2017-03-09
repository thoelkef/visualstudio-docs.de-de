---
title: "&#39;#ElseIf&#39;, &#39;#Else&#39; oder &#39;#End If&#39; muss ein entsprechendes &#39;#If&#39; voranstehen. | Microsoft Docs"
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
  - "vbc30013"
  - "bc30013"
helpviewer_keywords: 
  - "BC30013"
ms.assetid: 8fe2d23c-8b8f-46d8-90f2-7f8857ea43bb
caps.latest.revision: 11
caps.handback.revision: 11
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# &#39;#ElseIf&#39;, &#39;#Else&#39; oder &#39;#End If&#39; muss ein entsprechendes &#39;#If&#39; voranstehen.
`#ElseIf`, `#Else` und `#End If` sind Direktiven für die bedingte Kompilierung.`#ElseIf`, `#Else` oder `#End If` ist keine entsprechende `#If`\-Direktive vorangestellt.  
  
 **Fehler\-ID:** BC30013  
  
### So beheben Sie diesen Fehler  
  
1.  Stellen Sie sicher, dass das beabsichtigte `#If` nicht durch einen dazwischen liegenden Block für die bedingte Kompilierung oder ein falsch platziertes `#End If` von der fraglichen Klausel getrennt ist.  
  
    > [!NOTE]
    >  In jedem `#If`\-Block ist nur ein `#Else` zulässig, daher rufen zwei aufeinander folgende `#Else`\-Direktiven diesen Fehler hervor.  
  
2.  Überprüfen Sie, ob das führende `#` nicht möglicherweise bei einer früheren `#If`\-Direktive fehlt.  
  
3.  Falls der Code ansonsten in Ordnung ist, fügen Sie am Anfang des Blocks für die bedingte Kompilierung eine `#If`\-Direktive hinzu.  
  
## Siehe auch  
 [\#If...Then...\#Else Directives](/dotnet/visual-basic/language-reference/directives/if-then-else-directives)