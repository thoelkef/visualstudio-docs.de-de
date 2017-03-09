---
title: "Compilerwarnung (Stufe 4) CS0628 | Microsoft Docs"
ms.custom: ""
ms.date: "11/17/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-csharp"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "CS0628"
dev_langs: 
  - "CSharp"
helpviewer_keywords: 
  - "CS0628"
ms.assetid: a54cfad8-27c9-4abb-8c83-982615489a10
caps.latest.revision: 7
caps.handback.revision: 7
author: "BillWagner"
ms.author: "wiwagn"
manager: "wpickett"
---
# Compilerwarnung (Stufe 4) CS0628
„member“: Ein neuer geschützter Member wurde in einer versiegelten Klasse deklariert.  
  
 Eine [versiegelte](/dotnet/csharp/language-reference/keywords/sealed) Klasse kann keinen [geschützten](/dotnet/csharp/language-reference/keywords/protected) Member einführen, da keine andere Klasse von der `sealed`\-Klasse erben und den `protected`\-Member verwenden kann.  
  
 Im folgenden Beispiel wird CS0628 generiert:  
  
```  
// CS0628.cs // compile with: /W:4 sealed class C { protected int i;   // CS0628 } class MyClass { public static void Main() { } }  
```