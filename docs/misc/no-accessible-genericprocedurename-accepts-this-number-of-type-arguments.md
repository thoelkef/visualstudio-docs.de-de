---
title: "Keine zugreifbare &lt;Name der generischen Prozedur&gt; akzeptiert diese Anzahl von Typargumenten. | Microsoft Docs"
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
  - "bc32118"
  - "vbc32118"
helpviewer_keywords: 
  - "BC32118"
ms.assetid: 4ee942ba-0fa1-4ec1-9c2c-a0c0dc3f1b17
caps.latest.revision: 4
caps.handback.revision: 4
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# Keine zugreifbare &lt;Name der generischen Prozedur&gt; akzeptiert diese Anzahl von Typargumenten.
Eine Anweisung ruft eine generische Prozedur auf, die mehrere überladene Versionen aufweist, aber keine der überladenen Versionen definiert die gleiche Anzahl von Typparametern, wie die Anzahl der im Aufruf angegebenen Typargumente.  
  
 Wenn nur eine generische Version vorhanden ist, rufen Sie diese ohne Typargumente auf, und der Compiler kann einen *Typrückschluss* versuchen. Weitere Informationen finden Sie unter „Typrückschluss“ in [Generic Procedures in Visual Basic](/dotnet/visual-basic/programming-guide/language-features/data-types/generic-procedures). Wenn jedoch mehrere generische Versionen vorhanden sind, kann der Compiler nur dann eine Auswahl treffen, wenn Sie Typargumente angeben. Wenn Sie ein Typargument angeben, müssen Sie ein Typargument für jeden Typparameter angeben, der von einer der überladenen Versionen definiert wird.  
  
 **Fehler\-ID:** BC32118  
  
### So beheben Sie diesen Fehler  
  
-   Entscheiden Sie, welche überladene Version Sie aufrufen möchten, und geben Sie dann die entsprechende Anzahl von Typargumenten an.  
  
## Siehe auch  
 [Overloads](/dotnet/visual-basic/language-reference/modifiers/overloads)   
 [Procedure Overloading](/dotnet/visual-basic/programming-guide/language-features/procedures/procedure-overloading)   
 [Generische Typen in Visual Basic](/dotnet/visual-basic/programming-guide/language-features/data-types/generic-types)   
 [Generic Procedures in Visual Basic](/dotnet/visual-basic/programming-guide/language-features/data-types/generic-procedures)