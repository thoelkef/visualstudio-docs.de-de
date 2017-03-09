---
title: "&quot;Sub New&quot; kann keine Schnittstellenmember implementieren. | Microsoft Docs"
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
  - "bc31042"
  - "vbc31042"
helpviewer_keywords: 
  - "BC31042"
ms.assetid: 43ad231f-878d-4d08-b43c-06bf167ddd7d
caps.latest.revision: 8
caps.handback.revision: 8
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# &quot;Sub New&quot; kann keine Schnittstellenmember implementieren.
`Sub New` ist ein Konstruktor und kann keine Member implementieren.  
  
 **Fehler\-ID:** BC31042  
  
### So beheben Sie diesen Fehler  
  
-   Entfernen Sie `Implements`\-Anweisungen aus `Sub New`\-Prozeduren.  
  
## Siehe auch  
 [Interfaces](/dotnet/visual-basic/programming-guide/language-features/interfaces/index)   
 [Implements](/dotnet/visual-basic/language-reference/statements/implements-clause)