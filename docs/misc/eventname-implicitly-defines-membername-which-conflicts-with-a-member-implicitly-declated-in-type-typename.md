---
title: "&#39;&lt;Eigenschaftenname&gt;&#39; definiert implizit &#39;&lt;Membername&gt;&#39;, was einen Konflikt mit einem Member verursacht, der in &lt;Typ&gt; &#39;&lt;Typname&gt;&#39; implizit deklariert wurde. | Microsoft Docs"
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
  - "bc31059"
  - "vbc31059"
helpviewer_keywords: 
  - "BC31059"
ms.assetid: 60ddb2f4-a204-41eb-b13b-b2bb13ddb69c
caps.latest.revision: 11
caps.handback.revision: 11
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# &#39;&lt;Eigenschaftenname&gt;&#39; definiert implizit &#39;&lt;Membername&gt;&#39;, was einen Konflikt mit einem Member verursacht, der in &lt;Typ&gt; &#39;&lt;Typname&gt;&#39; implizit deklariert wurde.
Der Name eines Typmembers steht in Konflikt mit dem Namen eines implizit für ein Ereignis erstellten Members. Ereignisse erstellen implizit mehrere Variablen. Beispielsweise deklariert die Deklaration `Event X` implizit die Namen `XEventHandler`, `XEvent`, `add_X` und `remove_X`.  
  
 **Fehler\-ID:** BC31059  
  
### So beheben Sie diesen Fehler  
  
-   Benennen Sie zur Behebung des Namenskonflikts den explizit deklarierten Member um.  
  
## Siehe auch  
 [NotInBuild: Deklarationsanweisungen in Visual Basic](http://msdn.microsoft.com/de-de/81f3c398-f45c-4d95-80bf-aa39d1a0fb30)   
 [Events](/dotnet/visual-basic/programming-guide/language-features/events/events)