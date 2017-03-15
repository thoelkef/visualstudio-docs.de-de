---
title: "An „New“ in einem Typparameter k&#246;nnen keine Argumente &#252;bergeben werden. | Microsoft Docs"
ms.custom: ""
ms.date: "11/16/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-visual-basic"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "BC32085"
  - "vbc32085"
helpviewer_keywords: 
  - "BC32085"
ms.assetid: a60bf62d-2b2e-4621-b8db-e67720b918fb
caps.latest.revision: 8
caps.handback.revision: 8
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# An „New“ in einem Typparameter k&#246;nnen keine Argumente &#252;bergeben werden.
Eine Deklaration oder Zuweisungsanweisung ruft einen generischen Typ auf und stellt Konstruktorargumente für einen Typparameter bereit, der die [New Operator](/dotnet/visual-basic/language-reference/operators/new-operator)\-Einschränkung aufweist.  
  
 Eine Einschränkungsliste für einen Typparameter kann angeben, dass das an den Typparameter übergebene Typargument einen parameterlosen Konstruktor verfügbar machen muss, auf den der erstellende Code zugreifen kann. Ein Typparameter kann keinen Konstruktor erfordern, der Parameter aufweist, und ein Typparameter mit der `New`\-Einschränkung kann einen solchen Konstruktor nicht annehmen.  
  
 **Fehler\-ID:** BC32085  
  
### So beheben Sie diesen Fehler  
  
-   Entfernen Sie die Argumentliste nach dem Typargument in der Anweisung, mit der der generische Typ aufgerufen wird. Sie können keine Konstruktorargumente an den entsprechenden Typparameter übergeben.  
  
## Siehe auch  
 [Generische Typen in Visual Basic](/dotnet/visual-basic/programming-guide/language-features/data-types/generic-types)   
 [Value Types and Reference Types](/dotnet/visual-basic/programming-guide/language-features/data-types/value-types-and-reference-types)