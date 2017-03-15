---
title: "Generische Methoden k&#246;nnen nicht f&#252;r COM verf&#252;gbar gemacht werden. | Microsoft Docs"
ms.custom: ""
ms.date: "12/15/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-visual-basic"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "vbc30943"
  - "bc30943"
helpviewer_keywords: 
  - "BC30943"
ms.assetid: 0e3bff62-f187-4864-8520-70f6be22e869
caps.latest.revision: 8
caps.handback.revision: 8
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# Generische Methoden k&#246;nnen nicht f&#252;r COM verf&#252;gbar gemacht werden.
Eine [!INCLUDE[dnprdnshort](../code-quality/includes/dnprdnshort_md.md)]\-Komponente, die eine oder mehrere generische Prozeduren enthält, wird in eine COM\-Komponente exportiert.  
  
 Das Component Object Model \(COM\) unterstützt keine generische Typen und kann nicht mit ihnen zusammenarbeiten.  
  
 **Fehler\-ID:** BC30943  
  
### So beheben Sie diesen Fehler  
  
-   Entfernen Sie die generischen Prozeduren aus der [!INCLUDE[dnprdnshort](../code-quality/includes/dnprdnshort_md.md)]\-Komponente, oder verwenden Sie sie nicht für COM\-Interop.  
  
## Siehe auch  
 [Generische Typen in Visual Basic](/dotnet/visual-basic/programming-guide/language-features/data-types/generic-types)   
 [COM Interop](/dotnet/visual-basic/programming-guide/com-interop/index)