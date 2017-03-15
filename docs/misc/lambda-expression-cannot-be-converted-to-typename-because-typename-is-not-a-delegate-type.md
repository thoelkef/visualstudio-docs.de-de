---
title: "Der Lambdaausdruck kann nicht in &#39;&lt;Typname&gt;&#39; umgewandelt werden, da &#39;&lt;Typname&gt;&#39; kein Delegattyp ist. | Microsoft Docs"
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
  - "bc36625"
  - "vbc36625"
helpviewer_keywords: 
  - "BC36625"
ms.assetid: c03634d4-d831-4f8c-b6ab-566465968e4d
caps.latest.revision: 6
caps.handback.revision: 6
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# Der Lambdaausdruck kann nicht in &#39;&lt;Typname&gt;&#39; umgewandelt werden, da &#39;&lt;Typname&gt;&#39; kein Delegattyp ist.
Lambdaausdrücke können dort verwendet werden, wo Delegaten gültig sind. Sie können in kompatible Delegattypen, aber nicht in einen anderen Typ konvertiert werden. Sie können z. B. einen Delegattyp definieren und ihm einen Lambdaausdruck zuweisen oder einen Lambdaausdruck als Argument an einen <xref:System.Func%601>\-Parameter senden. Diese Beispiele werden im folgenden Code veranschaulicht.  
  
```vb#  
Module Module1 Delegate Function FunDel(ByVal m As Integer) As Boolean Sub Main() ' Assign a lambda expression to a function delegate. Dim negative As FunDel = Function(n As Integer) n < 0 Console.WriteLine(negative(-3)) ' Send a lambda as the argument to a delegate parameter. Dim numbers() As Integer = {3, 4, 2, 8, 1, 0, 9, 13, 42} Dim evens = numbers.Where(Function(n) n Mod 2 = 0) For Each even In evens Console.WriteLine(even) Next End Sub End Module  
```  
  
 **Fehler\-ID:** BC36625  
  
## Siehe auch  
 [Lambda Expressions](/dotnet/visual-basic/programming-guide/language-features/procedures/lambda-expressions)