---
title: "&#39;End With&#39; muss ein entsprechendes &#39;With&#39; voranstehen. | Microsoft Docs"
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
  - "bc30093"
  - "vbc30093"
helpviewer_keywords: 
  - "BC30093"
ms.assetid: b0f1f7d5-0c33-4b97-8043-f0f5b40ca5d7
caps.latest.revision: 8
caps.handback.revision: 8
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# &#39;End With&#39; muss ein entsprechendes &#39;With&#39; voranstehen.
Eine `End With`\-Anweisung tritt ohne entsprechende `With`\-Anweisung auf.`End With` muss eine entsprechende `With`\-Anweisung vorangestellt sein.  
  
 **Fehler\-ID:** BC30093  
  
### So beheben Sie diesen Fehler  
  
1.  Wenn dieser `With`\-Block Teil einer Reihe von geschachtelten `With`\-Blöcken ist, stellen Sie sicher, dass jeder Block ordnungsgemäß abgeschlossen wird.  
  
2.  Stellen Sie sicher, dass andere Steuerungsstrukturen innerhalb des `With`\-Blocks ordnungsgemäß beendet werden.  
  
3.  Stellen Sie sicher, dass dieser `With`\-Block ordnungsgemäß formatiert ist.  
  
## Siehe auch  
 [With...End With Statement](/dotnet/visual-basic/language-reference/statements/with-end-with-statement)