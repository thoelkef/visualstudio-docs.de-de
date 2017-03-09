---
title: "Die Einschr&#228;nkungen f&#252;r diesen Typparameter stimmen nicht mit den Einschr&#228;nkungen f&#252;r den entsprechenden Typparameter &#252;berein, der f&#252;r einen der anderen partiellen Typen von &quot;|1&quot; definiert wurde. | Microsoft Docs"
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
  - "vbc30932"
  - "bc30932"
helpviewer_keywords: 
  - "BC30932"
ms.assetid: a38ca4ad-6bbf-421e-a0d7-c5e0a9029160
caps.latest.revision: 9
caps.handback.revision: 9
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# Die Einschr&#228;nkungen f&#252;r diesen Typparameter stimmen nicht mit den Einschr&#228;nkungen f&#252;r den entsprechenden Typparameter &#252;berein, der f&#252;r einen der anderen partiellen Typen von &quot;|1&quot; definiert wurde.
Wenn Sie die Definition einer Klasse oder Struktur zwischen mehreren Deklarationen aufteilen, behandelt der Compiler die Klasse oder Struktur als die Union all seiner partiellen Deklarationen. Daher können Sie in den verschiedenen partiellen Deklarationen keine in Konflikt stehenden Modifizierer oder Typparameterlisten definieren.  
  
 **Fehler\-ID:** BC30932  
  
### So beheben Sie diesen Fehler  
  
1.  Bestimmen Sie, welche Typparameterliste für die Klasse oder Struktur gewünscht ist. Diese umfasst die Parameter, ihre Reihenfolge und die Einschränkungslisten.  
  
2.  Stellen Sie sicher, dass jede partielle Definition die gleiche Typparameterliste verwendet.  
  
## Siehe auch  
 [Partial](/dotnet/visual-basic/language-reference/modifiers/partial)   
 [Generische Typen in Visual Basic](/dotnet/visual-basic/programming-guide/language-features/data-types/generic-types)