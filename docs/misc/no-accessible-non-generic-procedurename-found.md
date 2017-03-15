---
title: "Es wurde kein &lt;Prozedurname&gt; (zugreifbar, nicht generisch) gefunden. | Microsoft Docs"
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
  - "vbc32117"
  - "bc32117"
helpviewer_keywords: 
  - "BC32117"
ms.assetid: a7bf8b67-8a0a-499e-9992-dc00e09b7ff4
caps.latest.revision: 4
caps.handback.revision: 4
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# Es wurde kein &lt;Prozedurname&gt; (zugreifbar, nicht generisch) gefunden.
Eine Anweisung ruft eine Prozedur mit mehr als einer überladenen Version auf, aber alle überladenen Versionen sind generisch, und der Aufruf stellt keine Typargumente bereit.  
  
 Wenn nur eine generische Version vorhanden ist und Sie diese ohne Typargumente aufrufen, kann der Compiler einen *Typrückschluss* versuchen. Weitere Informationen finden Sie unter „Typrückschluss“ in [Generic Procedures in Visual Basic](/dotnet/visual-basic/programming-guide/language-features/data-types/generic-procedures). Wenn jedoch mehrere generische Versionen vorhanden sind, kann der Compiler nur dann eine Auswahl treffen, wenn Sie Typargumente angeben. Wenn Sie ein Typargument angeben, müssen Sie ein Typargument für jeden Typparameter angeben, der von einer der überladenen Versionen definiert wird.  
  
 **Fehler\-ID:** BC32117  
  
### So beheben Sie diesen Fehler  
  
-   Rufen Sie die Prozedur mit einer Typargumentliste auf.  
  
## Siehe auch  
 [Overloads](/dotnet/visual-basic/language-reference/modifiers/overloads)   
 [Procedure Overloading](/dotnet/visual-basic/programming-guide/language-features/procedures/procedure-overloading)   
 [Generische Typen in Visual Basic](/dotnet/visual-basic/programming-guide/language-features/data-types/generic-types)   
 [Generic Procedures in Visual Basic](/dotnet/visual-basic/programming-guide/language-features/data-types/generic-procedures)