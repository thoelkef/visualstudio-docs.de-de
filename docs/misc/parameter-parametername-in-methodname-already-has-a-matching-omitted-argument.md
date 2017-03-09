---
title: "Der Parameter &#39;&lt;Parametername&gt;&#39; in &#39;&lt;Methodenname&gt;&#39; weist bereits ein passendes ausgelassenes Argument auf. | Microsoft Docs"
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
  - "vbc32021"
  - "bc32021"
helpviewer_keywords: 
  - "BC32021"
ms.assetid: f51d29ba-c5b3-4731-a426-4c5ba11b4e1f
caps.latest.revision: 8
caps.handback.revision: 8
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# Der Parameter &#39;&lt;Parametername&gt;&#39; in &#39;&lt;Methodenname&gt;&#39; weist bereits ein passendes ausgelassenes Argument auf.
Ein Prozeduraufruf stellt ein Argument nach Namen bereit, nachdem dasselbe Argument nach Position ausgelassen wurde. Beispiel:  
  
```  
Public Sub ABC(ByVal X As Byte, Optional ByVal Y As Byte = 0, _ Optional ByVal Z As Byte = 0) ' ... Call ABC(6, , Y:=3)   ' Argument Y omitted by position, supplied by name.  
```  
  
 **Fehler\-ID:** BC32021  
  
### So beheben Sie diesen Fehler  
  
-   Geben Sie das Argument nach Position an, oder entfernen Sie das Komma, durch das es ausgelassen wird.  
  
## Siehe auch  
 [Passing Arguments by Position and by Name](/dotnet/visual-basic/programming-guide/language-features/procedures/passing-arguments-by-position-and-by-name)