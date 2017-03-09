---
title: "Der Parameter &#39;&lt;Parametername&gt;&#39; weist bereits ein passendes ausgelassenes Argument auf. | Microsoft Docs"
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
  - "vbc36566"
  - "bc36566"
helpviewer_keywords: 
  - "BC36566"
ms.assetid: b37af6bc-abd0-4436-bf8a-a467e3603342
caps.latest.revision: 6
caps.handback.revision: 6
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# Der Parameter &#39;&lt;Parametername&gt;&#39; weist bereits ein passendes ausgelassenes Argument auf.
Ein Prozeduraufruf stellt ein Argument nach Namen bereit, nachdem dasselbe Argument nach Position ausgelassen wurde. Beachten Sie folgendes Beispiel:  
  
```vb#  
Public Sub ABC(ByVal X As Byte, Optional ByVal Y As Byte = 0, _ Optional ByVal Z As Byte = 0) ' ... ' Argument Y is omitted by position, but supplied by name. Call ABC(6, , Y:=3)     
```  
  
 **Fehler\-ID:** BC36566  
  
### So beheben Sie diesen Fehler  
  
-   Geben Sie das Argument nach Position an, oder entfernen Sie das Komma, durch das es ausgelassen wird.  
  
## Siehe auch  
 [Passing Arguments by Position and by Name](/dotnet/visual-basic/programming-guide/language-features/procedures/passing-arguments-by-position-and-by-name)