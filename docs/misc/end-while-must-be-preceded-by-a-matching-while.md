---
title: "&#39;End While&#39; muss ein entsprechendes &#39;While&#39; voranstehen. | Microsoft Docs"
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
  - "vbc30090"
  - "bc30090"
helpviewer_keywords: 
  - "BC30090"
ms.assetid: 302b26b8-8fa4-4e49-86f0-d7c49fec485f
caps.latest.revision: 8
caps.handback.revision: 8
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# &#39;End While&#39; muss ein entsprechendes &#39;While&#39; voranstehen.
Eine `End While`\-Anweisung tritt ohne entsprechende `While`\-Anweisung auf.`End While` muss eine entsprechende `While`\-Anweisung vorangestellt sein.  
  
 **Fehler\-ID:** BC30090  
  
### So beheben Sie diesen Fehler  
  
1.  Wenn dieser `While`\-Block Teil einer Reihe von geschachtelten `While`\-Blöcken ist, stellen Sie sicher, dass jeder Block korrekt beendet wird.  
  
2.  Stellen Sie sicher, dass andere Steuerungsstrukturen innerhalb des `While`\-Blocks ordnungsgemäß beendet werden.  
  
3.  Stellen Sie sicher, dass dieser `While`\-Block ordnungsgemäß formatiert ist.  
  
## Siehe auch  
 [While...End While Statement](/dotnet/visual-basic/language-reference/statements/while-end-while-statement)