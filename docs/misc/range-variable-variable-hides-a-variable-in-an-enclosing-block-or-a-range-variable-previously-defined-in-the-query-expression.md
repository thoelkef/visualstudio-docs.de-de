---
title: "Die Bereichsvariable &quot;&lt;Variable&gt;&quot; verbirgt eine Variable in einem einschlie&#223;enden Block oder eine zuvor im Abfrageausdruck definierte Bereichsvariable. | Microsoft Docs"
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
  - "bc30978"
  - "vbc30978"
helpviewer_keywords: 
  - "BC30978"
ms.assetid: 806d94c1-653f-40c0-b1c4-95661c76a392
caps.latest.revision: 4
caps.handback.revision: 4
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# Die Bereichsvariable &quot;&lt;Variable&gt;&quot; verbirgt eine Variable in einem einschlie&#223;enden Block oder eine zuvor im Abfrageausdruck definierte Bereichsvariable.
Eine Bereichsvariable in einer Abfrage hat den gleichen Namen wie eine zuvor im selben Bereich definierte Variable oder wie eine zuvor innerhalb der Abfrage definierte Bereichsvariable.  
  
 **Fehler\-ID:** BC30978  
  
### So beheben Sie diesen Fehler  
  
-   Stellen Sie sicher, dass alle Bereichsvariablen in der Abfrage über eindeutige Namen verfügen, die im selben Bereich nicht doppelt vorkommen.  
  
-   Schließen Sie geschachtelte Abfragen mit doppelten Variablennamen in Klammern ein, und trennen Sie dabei die Bereiche für die einzelnen Bereichsvariablen.  
  
## Siehe auch  
 [Introduction to LINQ in Visual Basic](/dotnet/visual-basic/programming-guide/language-features/linq/introduction-to-linq)   
 [LINQ](/dotnet/visual-basic/programming-guide/language-features/linq/index)