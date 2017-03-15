---
title: "Compilerfehler CS0515 | Microsoft Docs"
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
  - "CS0515"
dev_langs: 
  - "CSharp"
helpviewer_keywords: 
  - "CS0515"
ms.assetid: 0f8c0253-218d-4c21-b22c-fa5802ba4e7f
caps.latest.revision: 7
caps.handback.revision: 7
author: "BillWagner"
ms.author: "wiwagn"
manager: "wpickett"
---
# Compilerfehler CS0515
"Funktion": Zugriffsmodifizierer sind bei statischen Konstruktoren nicht zulässig.  
  
 Ein statischer Konstruktor kann keinen [Zugriffsmodifizierer](/dotnet/csharp/language-reference/keywords/modifiers) enthalten.  
  
## Beispiel  
 Im folgenden Beispiel wird CS0515 generiert:  
  
```  
// CS0515.cs public class Clx { public static void Main() { } } public class Clz { public static Clz()   // CS0515, remove public keyword { } }  
```