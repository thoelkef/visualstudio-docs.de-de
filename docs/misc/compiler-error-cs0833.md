---
title: "Compilerfehler CS0833 | Microsoft Docs"
ms.custom: ""
ms.date: "11/16/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-csharp"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "CS0833"
dev_langs: 
  - "CSharp"
helpviewer_keywords: 
  - "CS0833"
ms.assetid: 4ae32454-265f-47aa-bf2a-ee1d702330b7
caps.latest.revision: 7
caps.handback.revision: 7
author: "BillWagner"
ms.author: "wiwagn"
manager: "wpickett"
---
# Compilerfehler CS0833
Ein anonymer Typ kann nicht mehrere Eigenschaften mit demselben Namen haben.  
  
 Ein anonymer Typ \(wie auch jeder andere Typ\) kann nicht zwei Eigenschaften mit dem gleichen Namen haben.  
  
### So beheben Sie diesen Fehler  
  
1.  Geben Sie jeder Eigenschaft im Typ einen eindeutigen Namen.  
  
## Beispiel  
 Im folgenden Beispiel wird der Fehler CS0833 generiert:  
  
```  
// cs0833.cs using System; public class C { public static int Main() { var c = new { p1 = 1, p1 = 2 }; // CS0833 return 1; } }  
```  
  
## Siehe auch  
 [Anonyme Typen](/dotnet/csharp/programming-guide/classes-and-structs/anonymous-types)