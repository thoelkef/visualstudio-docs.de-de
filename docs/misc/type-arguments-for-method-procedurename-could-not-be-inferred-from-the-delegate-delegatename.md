---
title: "Die Typargumente f&#252;r die Methode &#39;&lt;Prozedurname&gt;&#39; konnten nicht aus dem Delegaten &#39;&lt;Delegatename&gt;&#39; abgeleitet werden. | Microsoft Docs"
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
  - "vbc30952"
  - "bc30952"
helpviewer_keywords: 
  - "BC30952"
ms.assetid: 5eb804ce-2e93-4668-b655-7fe00815e552
caps.latest.revision: 6
caps.handback.revision: 6
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# Die Typargumente f&#252;r die Methode &#39;&lt;Prozedurname&gt;&#39; konnten nicht aus dem Delegaten &#39;&lt;Delegatename&gt;&#39; abgeleitet werden.
Eine Zuweisungsanweisung verwendet `AddressOf`, um die Adresse einer generischen Prozedur zu einem Delegaten zuzuweisen, aber sie stellt keine Typargumente für die generische Prozedur bereit.  
  
 Wenn Sie einen generischen Typ aufrufen, geben Sie in der Regel für jeden Typparameter, der durch den generischen Typ definiert wird, ein Typargument an. Wenn Sie keine Typargumente angeben, versucht der Compiler, die an die Typparameter zu übergebenden Typen abzuleiten. Wenn der Kontext nicht genügend Informationen für den Compiler für die Ableitung der Typen bereitstellt, wird ein Fehler generiert.  
  
 **Fehler\-ID:** BC30952  
  
### So beheben Sie diesen Fehler  
  
-   Geben Sie im `AddressOf`\-Ausdruck die Typargumente für die generische Prozedur an.  
  
## Siehe auch  
 [Generische Typen in Visual Basic](/dotnet/visual-basic/programming-guide/language-features/data-types/generic-types)   
 [AddressOf Operator](/dotnet/visual-basic/language-reference/operators/addressof-operator)   
 [Generic Procedures in Visual Basic](/dotnet/visual-basic/programming-guide/language-features/data-types/generic-procedures)   
 [Type List](/dotnet/visual-basic/language-reference/statements/type-list)