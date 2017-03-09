---
title: "&#39;Case&#39; kann nicht auf &#39;Case Else&#39; in derselben Select-Anweisung folgen. | Microsoft Docs"
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
  - "bc30321"
  - "vbc30321"
helpviewer_keywords: 
  - "BC30321"
ms.assetid: eeedbceb-2c8d-4acb-b84c-8b42c058f083
caps.latest.revision: 8
caps.handback.revision: 8
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# &#39;Case&#39; kann nicht auf &#39;Case Else&#39; in derselben Select-Anweisung folgen.
Eine `Case Else`\-Anweisung führt Anweisungen ein, die ausgeführt werden sollen, wenn keine Übereinstimmung für das anfängliche `Case` gefunden wird. Eine `Case`\-Anweisung wurde nach einem `Case Else` in demselben `Select`\-Block gefunden.  
  
 **Fehler\-ID:** BC30321  
  
### So beheben Sie diesen Fehler  
  
-   Verschieben Sie das `Case Else` an die gewünschte Position hinter der `Case`\-Anweisung.  
  
## Siehe auch  
 [Select...Case Statement](/dotnet/visual-basic/language-reference/statements/select-case-statement)