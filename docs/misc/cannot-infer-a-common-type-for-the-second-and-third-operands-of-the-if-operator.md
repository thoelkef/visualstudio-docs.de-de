---
title: "Es kann kein gemeinsamer Typ f&#252;r den zweiten und dritten Operanden des If-Operators abgeleitet werden | Microsoft Docs"
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
  - "vbc33106"
  - "bc33106"
helpviewer_keywords: 
  - "BC33106"
ms.assetid: 793eed88-a9f9-43e3-b657-c16795ecbbcc
caps.latest.revision: 7
caps.handback.revision: 7
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# Es kann kein gemeinsamer Typ f&#252;r den zweiten und dritten Operanden des If-Operators abgeleitet werden
Es kann kein gemeinsamer Typ für den zweiten und dritten Operanden des If\-Operators abgeleitet werden. Für einen muss eine Widening\-Konvertierung in den anderen durchgeführt werden.  
  
 Wenn der `If`\-Operator mit drei Argumenten aufgerufen wird, muss zwischen dem zweiten und dritten Argument eine Widening\-Konvertierung durchgeführt werden. Da beispielsweise keine Widening\-Konvertierung in keine Richtung zwischen `Integer` und `String` durchgeführt wird, verursacht folgender Code diesen Fehler.  
  
```vb#  
Dim divisor = 3  
' Not valid.  
' Console.WriteLine(If(divisor <> 0, number \ divisor, "Division by zero"))  
```  
  
 **Fehler\-ID:** BC33106  
  
### So beheben Sie diesen Fehler  
  
-   Geben Sie eine explizite Konvertierung für einen der Operanden an, wenn dies in Ihrem Code möglich ist.  
  
-   Verwenden Sie eine andere Bedingungskonstruktion, z. B. eine `If...Then...Else`\-Anweisung.  
  
## Siehe auch  
 [If Operator](/dotnet/visual-basic/language-reference/operators/if-operator)   
 [If...Then...Else Statement](/dotnet/visual-basic/language-reference/statements/if-then-else-statement)   
 [Widening and Narrowing Conversions](/dotnet/visual-basic/programming-guide/language-features/data-types/widening-and-narrowing-conversions)