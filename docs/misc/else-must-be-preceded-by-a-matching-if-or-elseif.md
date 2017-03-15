---
title: "&#39;Else&#39; muss ein entsprechendes &#39;If&#39; oder &#39;ElseIf&#39; voranstehen | Microsoft Docs"
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
  - "bc30086"
  - "vbc30086"
helpviewer_keywords: 
  - "BC30086"
ms.assetid: 5e76b3c6-571f-4a6f-b524-26150cb6e986
caps.latest.revision: 8
caps.handback.revision: 8
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# &#39;Else&#39; muss ein entsprechendes &#39;If&#39; oder &#39;ElseIf&#39; voranstehen
Eine `Else`\-Anweisung tritt ohne entsprechende `If`\-Anweisung auf.`Else` muss eine `If`\-Anweisung vorangestellt sein.  
  
 **Fehler\-ID:** BC30086  
  
### So beheben Sie diesen Fehler  
  
1.  Wenn dieser `If`\-Block Teil einer Reihe von geschachtelten `If`\-Blöcken ist, stellen Sie sicher, dass jeder Block korrekt beendet wird.  
  
2.  Stellen Sie sicher, dass andere Steuerungsstrukturen innerhalb des `If`\-Blocks ordnungsgemäß beendet werden.  
  
3.  Stellen Sie sicher, dass dieser `If`\-Block ordnungsgemäß formatiert ist.  
  
## Siehe auch  
 [If...Then...Else Statement](/dotnet/visual-basic/language-reference/statements/if-then-else-statement)