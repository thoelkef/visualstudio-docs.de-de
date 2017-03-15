---
title: "&lt;type1&gt; &#39;&lt;typname1&gt;&#39; steht im Konflikt mit einem Member, das implizit f&#252;r das Ereignis &#39;&lt;ereignisname&gt;&#39; in &lt;typ&gt; &#39;&lt;typname2&gt;&#39; deklariert ist | Microsoft Docs"
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
  - "vbc31061"
  - "bc31061"
helpviewer_keywords: 
  - "BC31061"
ms.assetid: de5b1121-8c8f-4aba-a3e7-1e3e60df0dc5
caps.latest.revision: 10
caps.handback.revision: 10
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# &lt;type1&gt; &#39;&lt;typname1&gt;&#39; steht im Konflikt mit einem Member, das implizit f&#252;r das Ereignis &#39;&lt;ereignisname&gt;&#39; in &lt;typ&gt; &#39;&lt;typname2&gt;&#39; deklariert ist
Der Name eines Typmembers steht in Konflikt mit dem Namen eines implizit für ein Ereignis erstellten Members. Ereignisse erstellen implizit mehrere implizite Variablen. Beispielsweise deklariert die Deklaration `Event X` impliziet die Namen `XEventHandler`, `XEvent`, `add_X` und `remove_X`.  
  
 **Fehler\-ID:** BC31061  
  
### So beheben Sie diesen Fehler  
  
-   Benennen Sie zur Behebung des Namenskonflikts den explizit deklarierten Member um.  
  
## Siehe auch  
 [Nicht im Build: Deklarationsanweisungen in Visual Basic](http://msdn.microsoft.com/de-de/81f3c398-f45c-4d95-80bf-aa39d1a0fb30)   
 [Events](/dotnet/visual-basic/programming-guide/language-features/events/events)