---
title: "Compilerfehler CS0687 | Microsoft Docs"
ms.custom: ""
ms.date: "10/29/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-csharp"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "CS0687"
dev_langs: 
  - "CSharp"
helpviewer_keywords: 
  - "CS0687"
ms.assetid: b51c5e7c-f4de-4aa4-97b1-ebe220cd19b0
caps.latest.revision: 7
caps.handback.revision: 7
author: "BillWagner"
ms.author: "wiwagn"
manager: "wpickett"
---
# Compilerfehler CS0687
Der Namespacealias\-Qualifizierer '::' wird immer zu einem Typ oder Namespace aufgelöst und ist somit an dieser Stelle ungültig. Verwenden Sie stattdessen '.'.  
  
 Dieser Fehler tritt auf, wenn Sie etwas verwendet haben, das vom Parser als Typ an unerwarteter Stelle interpretiert wird. Ein Typ\- oder Namespacename ist nur in einem Memberzugriffsausdruck gültig, der den Memberzugriffsoperator \(**.**\) verwendet. Dies kann auftreten, wenn Sie den globalen Bereichsoperator \(::\) in einem anderen Kontext verwendet haben.  
  
## Beispiel  
 Im folgenden Beispiel wird CS0687 generiert:  
  
```  
// CS0687.cs using M = Test; using System; public class Test { public static int x = 77; public static void Main() { Console.WriteLine(M::x); // CS0687 // To resolve use the following line instead: // Console.WriteLine(M.x); } }  
```