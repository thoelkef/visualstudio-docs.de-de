---
title: "&#39;&lt;variablenname&gt;&#39; ist weder eine lokale Variable noch ein Parameter und kann daher nicht als Catch-Variable verwendet werden. | Microsoft Docs"
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
  - "bc31082"
  - "vbc31082"
helpviewer_keywords: 
  - "BC31082"
ms.assetid: de197563-5848-4c1a-a519-cc4b5ea9a4c9
caps.latest.revision: 7
caps.handback.revision: 7
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# &#39;&lt;variablenname&gt;&#39; ist weder eine lokale Variable noch ein Parameter und kann daher nicht als Catch-Variable verwendet werden.
Variablen in `Try...Catch...Finally`\-Anweisungen müssen lokal deklariert werden oder Parameter für die aktuelle Prozedur darstellen.  
  
 **Fehler\-ID:** BC31082  
  
### So beheben Sie diesen Fehler  
  
1.  Deklarieren Sie lokale Variablen oder Parameter für `Try...Catch...Finally`\-Anweisungen.  
  
## Siehe auch  
 [Try...Catch...Finally Statement](/dotnet/visual-basic/language-reference/statements/try-catch-finally-statement)