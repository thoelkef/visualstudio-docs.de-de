---
title: "&#39;Dim&#39;, &#39;Const&#39;, &#39;Public&#39;, &#39;Private&#39;, &#39;Protected&#39;, &#39;Friend&#39;, &#39;Shadows&#39;, &#39;ReadOnly&#39; oder &#39;Shared&#39; erwartet. | Microsoft Docs"
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
  - "bc30195"
  - "vbc30195"
helpviewer_keywords: 
  - "BC30195"
ms.assetid: 95684eaa-5aa2-4ae4-9a73-5f97c491e02c
caps.latest.revision: 8
caps.handback.revision: 8
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# &#39;Dim&#39;, &#39;Const&#39;, &#39;Public&#39;, &#39;Private&#39;, &#39;Protected&#39;, &#39;Friend&#39;, &#39;Shadows&#39;, &#39;ReadOnly&#39; oder &#39;Shared&#39; erwartet.
In einer Deklarationsanweisung fehlt ein Deklarationsschlüsselwort. Eine mögliche Ursache ist, dass eine Attributdeklaration eine Methode aufruft.  
  
 **Fehler\-ID:** BC30195  
  
### So beheben Sie diesen Fehler  
  
1.  Überprüfen Sie, ob eine Methode innerhalb einer Attributdeklaration deklariert ist.  
  
2.  Beginnen Sie die Anweisung mit dem entsprechenden Deklarationsschlüsselwort.  
  
## Siehe auch  
 [Declared Elements](/dotnet/visual-basic/programming-guide/language-features/declared-elements/index)   
 [Arrays können nicht mit 'New' deklariert werden](../misc/arrays-cannot-be-declared-with-new.md)