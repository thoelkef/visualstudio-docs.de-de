---
title: "„ReDim“ kann nur die Dimension ganz rechts &#228;ndern. | Microsoft Docs"
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
  - "vbrArray_TypeMismatch"
ms.assetid: d53cf41b-7a7a-466c-a29a-920d99698fa9
caps.latest.revision: 9
caps.handback.revision: 9
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# „ReDim“ kann nur die Dimension ganz rechts &#228;ndern.
Eine `ReDim`\-Anweisung hat versucht, mithilfe des `Preserve`\-Schlüsselworts eine Dimension eines Arrays zu ändern, die nicht die letzte Dimension ist. Bei Verwendung von `Preserve` können Sie nur die Größe der letzten Dimension eines Arrays ändern. Für alle anderen Dimensionen müssen Sie die gleiche Größe wie für das vorhandene Array angeben.  
  
### So beheben Sie diesen Fehler  
  
-   Entfernen Sie das `Preserve`\-Schlüsselwort.  
  
## Siehe auch  
 [NOTINBUILD: Übersicht über Arrays in Visual Basic](http://msdn.microsoft.com/de-de/ca50e2f2-b4d2-4c57-9169-9abbcc3392d8)   
 [NOTINBUILD: Mehrdimensionale Arrays in Visual Basic](http://msdn.microsoft.com/de-de/d92cad25-07e2-4d79-8ea4-ab269700f5de)   
 [ReDim Statement](/dotnet/visual-basic/language-reference/statements/redim-statement)   
 [Dim Statement](/dotnet/visual-basic/language-reference/statements/dim-statement)   
 [Beibehalten – Löschen](http://msdn.microsoft.com/de-de/91badeab-b4e0-48b6-92c9-9f0c8f995d81)