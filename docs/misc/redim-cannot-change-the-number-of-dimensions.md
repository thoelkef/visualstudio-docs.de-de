---
title: "ReDim kann die Anzahl der Dimensionen nicht &#228;ndern. | Microsoft Docs"
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
  - "vbrArray_RankMismatch"
ms.assetid: 52505298-9985-4682-8f6e-ff7d56077f34
caps.latest.revision: 9
caps.handback.revision: 9
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# ReDim kann die Anzahl der Dimensionen nicht &#228;ndern.
Ein Vorgang versucht über die `ReDim`\-Anweisung, den Rang \(Anzahl von Dimensionen\) eines Arrays zu ändern.`ReDim` kann die Größe einer oder mehrerer Dimensionen eines Arrays ändern, das bereits formal deklariert wurde, kann aber nicht den Rang eines Arrays ändern.  
  
### So beheben Sie diesen Fehler  
  
-   Vergewissern Sie sich, dass Sie den Rang des Arrays und nicht die Größen seiner Dimensionen ändern möchten, und verwenden Sie, sofern möglich, `Dim`, um ein neues Array mit dem gewünschten Rang zu deklarieren.  
  
## Siehe auch  
 [NOTINBUILD: Übersicht über Arrays in Visual Basic](http://msdn.microsoft.com/de-de/ca50e2f2-b4d2-4c57-9169-9abbcc3392d8)   
 [NOTINBUILD: Mehrdimensionale Arrays in Visual Basic](http://msdn.microsoft.com/de-de/d92cad25-07e2-4d79-8ea4-ab269700f5de)   
 [ReDim Statement](/dotnet/visual-basic/language-reference/statements/redim-statement)   
 [Dim Statement](/dotnet/visual-basic/language-reference/statements/dim-statement)