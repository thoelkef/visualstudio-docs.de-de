---
title: "Compilerfehler CS0558 | Microsoft Docs"
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
  - "CS0558"
dev_langs: 
  - "CSharp"
helpviewer_keywords: 
  - "CS0558"
ms.assetid: af63b9ba-2790-4362-a49d-b69a5292a555
caps.latest.revision: 7
caps.handback.revision: 7
author: "BillWagner"
ms.author: "wiwagn"
manager: "wpickett"
---
# Compilerfehler CS0558
Der benutzerdefinierte Operator 'operator' muss als statisch und öffentlich deklariert sein.  
  
 Bei benutzerdefinierten Operatoren müssen beide [Zugriffsmodifizierer](/dotnet/csharp/language-reference/keywords/modifiers)**static** und **public** angegeben werden.  
  
 Im folgenden Beispiel wird CS0558 generiert:  
  
```  
// CS0558.cs namespace x { public class ii { public class iii { static implicit operator int(iii aa)   // CS0558, add public { return 0; } } public static void Main() { } } }  
```