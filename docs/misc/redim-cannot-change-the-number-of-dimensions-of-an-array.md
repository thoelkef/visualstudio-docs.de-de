---
title: "ReDim kann die Anzahl der Dimensionen eines Arrays nicht &#228;ndern. | Microsoft Docs"
ms.custom: ""
ms.date: "11/24/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-visual-basic"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "vbc30415"
  - "bc30415"
helpviewer_keywords: 
  - "BC30415"
ms.assetid: 8ce97188-ff96-4e8c-917c-efc2f94173a3
caps.latest.revision: 9
caps.handback.revision: 9
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# ReDim kann die Anzahl der Dimensionen eines Arrays nicht &#228;ndern.
Sie haben versucht, den Rang \(die Anzahl der Dimensionen\) eines Arrays mithilfe von `ReDim` zu ändern. Die `ReDim`\-Anweisung kann verwendet werden, um die Größe der Dimensionen eines Arrays zu ändern, das bereits formal deklariert wurde. Sie kann jedoch nicht verwendet werden, um den Rang eines Arrays zu ändern.  
  
 **Fehler\-ID:** BC30415  
  
### So beheben Sie diesen Fehler  
  
-   Stellen Sie sicher, dass Sie den Rang und nicht die Arraygrößen ändern möchten, und verwenden Sie ggf. `Dim`, um ein neues Array mit dem gewünschten Rang zu deklarieren.  
  
## Siehe auch  
 [ReDim Statement](/dotnet/visual-basic/language-reference/statements/redim-statement)   
 [Dim Statement](/dotnet/visual-basic/language-reference/statements/dim-statement)   
 [NOTINBUILD: Übersicht über Arrays in Visual Basic](http://msdn.microsoft.com/de-de/ca50e2f2-b4d2-4c57-9169-9abbcc3392d8)