---
title: "Fehler bei der &#220;berladungsaufl&#246;sung, da keine zugreifbare &lt;Name der generischen Prozedur&gt; diese Anzahl von Typargumenten akzeptiert. | Microsoft Docs"
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
  - "bc32087"
  - "vbc32087"
helpviewer_keywords: 
  - "BC32087"
ms.assetid: a3eaafd3-80f6-4b7d-9b75-47b043fe17b5
caps.latest.revision: 11
caps.handback.revision: 11
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# Fehler bei der &#220;berladungsaufl&#246;sung, da keine zugreifbare &lt;Name der generischen Prozedur&gt; diese Anzahl von Typargumenten akzeptiert.
Ein Aufruf einer überladenen generischen Prozedur kann nicht aufgelöst werden, da der Compiler auf keine überladene Version mit der entsprechenden Anzahl von Typparametern zugreifen kann.  
  
 Wenn Sie eine generische Prozedur aufrufen, müssen Sie für jeden Typparameter ein Typargument angeben. Alternativ können Sie den Aufruf ohne Typargumente vornehmen, sodass der Compiler versucht, einen *Typrückschluss* auszuführen. Weitere Informationen finden Sie unter „Typrückschluss“ in [Generic Procedures in Visual Basic](/dotnet/visual-basic/programming-guide/language-features/data-types/generic-procedures).  
  
 **Fehler\-ID:** BC32087  
  
### So beheben Sie diesen Fehler  
  
1.  Stellen Sie sicher, dass der aufrufende Code auf die Version, die Sie aufrufen möchten, zugreifen kann. Siehe [Access Levels in Visual Basic](/dotnet/visual-basic/programming-guide/language-features/declared-elements/access-levels).  
  
2.  Fügen Sie Typargumente zum aufrufenden Code hinzu oder entfernen Sie sie daraus, sodass die Typargumentliste mit der Typparameterliste der Version übereinstimmt, die Sie aufrufen möchten.  
  
     \- oder \-  
  
     Entfernen Sie alle Typargumente aus dem aufrufenden Code, damit der Compiler versucht, einen Typrückschluss auszuführen. Bedenken Sie, dass der Typrückschluss fehlschlagen kann, wenn Konflikte auftreten oder Mehrdeutigkeiten vorhanden sind.  
  
## Siehe auch  
 [Overloaded Properties and Methods](/dotnet/visual-basic/programming-guide/language-features/objects-and-classes/overloaded-properties-and-methods)   
 [Overload Resolution](/dotnet/visual-basic/programming-guide/language-features/procedures/overload-resolution)   
 [Generische Typen in Visual Basic](/dotnet/visual-basic/programming-guide/language-features/data-types/generic-types)   
 [Type List](/dotnet/visual-basic/language-reference/statements/type-list)