---
title: "Typargumente f&#252;r die Erweiterungsmethode &#39;&lt;Methodenname&gt;&#39;, die in &#39;&lt;Typname&gt;&#39; definiert sind, konnten nicht vom Delegaten &#39;&lt;Delagatname&gt;&#39; abgeleitet werden. | Microsoft Docs"
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
  - "bc36581"
  - "vbc36581"
helpviewer_keywords: 
  - "BC36581"
ms.assetid: 2bb9ca8d-7293-40e9-9285-e20b8254b3af
caps.latest.revision: 7
caps.handback.revision: 7
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# Typargumente f&#252;r die Erweiterungsmethode &#39;&lt;Methodenname&gt;&#39;, die in &#39;&lt;Typname&gt;&#39; definiert sind, konnten nicht vom Delegaten &#39;&lt;Delagatname&gt;&#39; abgeleitet werden.
Eine Zuweisungsanweisung verwendet `AddressOf`, um die Adresse einer generischen Erweiterungsmethode zu einem Delegaten zuzuweisen, aber sie stellt keine Typargumente für die Erweiterungsmethode bereit.  
  
 Wenn Sie eine generische Methode aufrufen, geben Sie in der Regel für jeden Typparameter, der durch die generische Methode definiert wird, ein Typargument an. Wenn Sie keine Typargumente angeben, versucht der Compiler, die an die Typparameter zu übergebenden Typen abzuleiten. Wenn der Kontext nicht genügend Informationen für den Compiler für die Ableitung der Typen bereitstellt, wird ein Fehler generiert.  
  
 **Fehler\-ID:** BC36581  
  
### So beheben Sie diesen Fehler  
  
-   Geben Sie im `AddressOf`\-Ausdruck die Typargumente für die Erweiterungsmethode an.  
  
## Siehe auch  
 [Generische Typen in Visual Basic](/dotnet/visual-basic/programming-guide/language-features/data-types/generic-types)   
 [AddressOf Operator](/dotnet/visual-basic/language-reference/operators/addressof-operator)   
 [Generic Procedures in Visual Basic](/dotnet/visual-basic/programming-guide/language-features/data-types/generic-procedures)   
 [Type List](/dotnet/visual-basic/language-reference/statements/type-list)   
 [Erweiterungsmethoden](/dotnet/visual-basic/programming-guide/language-features/procedures/extension-methods)