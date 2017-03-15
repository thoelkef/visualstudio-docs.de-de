---
title: "&quot;End Select&quot; muss ein entsprechendes &quot;Select Case&quot; voranstehen | Microsoft Docs"
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
  - "bc30088"
  - "vbc30088"
helpviewer_keywords: 
  - "BC30088"
ms.assetid: 9de8c0d4-4ce9-45cf-98d6-8f68bba507a5
caps.latest.revision: 8
caps.handback.revision: 8
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# &quot;End Select&quot; muss ein entsprechendes &quot;Select Case&quot; voranstehen
Eine `End Select`\-Anweisung tritt ohne entsprechende `Select`\- oder `Select Case`\-Anweisung auf.`End Select` muss eine `Select`\- oder `Select Case`\-Anweisung vorangestellt sein.  
  
 **Fehler\-ID:** BC30088  
  
### So beheben Sie diesen Fehler  
  
1.  Wenn dieser `Select`\-Block Teil einer Reihe von geschachtelten `Select`\-Blöcken ist, stellen Sie sicher, dass jeder Block korrekt beendet wird.  
  
2.  Stellen Sie sicher, dass andere Steuerungsstrukturen innerhalb des `Select`\-Blocks ordnungsgemäß beendet werden.  
  
3.  Überprüfen Sie, ob dieser `Select`\-Block korrekt formatiert ist.  
  
## Siehe auch  
 [Select...Case Statement](/dotnet/visual-basic/language-reference/statements/select-case-statement)