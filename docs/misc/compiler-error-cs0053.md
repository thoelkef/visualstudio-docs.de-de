---
title: "Compilerfehler CS0053 | Microsoft Docs"
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
  - "CS0053"
dev_langs: 
  - "CSharp"
helpviewer_keywords: 
  - "CS0053"
ms.assetid: 62a96ef4-e8d2-44d0-9d39-5cd7a38efe52
caps.latest.revision: 8
caps.handback.revision: 8
author: "BillWagner"
ms.author: "wiwagn"
manager: "wpickett"
---
# Compilerfehler CS0053
Inkonsistenter Zugriff: Eigenschaftentyp 'Typ' ist weniger zugreifbar als Eigenschaft 'Eigenschaft'.  
  
 Ein public\-Konstrukt muss ein Objekt zurückgeben, auf das öffentlich zugegriffen werden kann. Weitere Informationen finden Sie unter [Zugriffsmodifizierer](/dotnet/csharp/programming-guide/classes-and-structs/access-modifiers).  
  
 Im folgenden Beispiel wird CS0053 generiert:  
  
```  
// CS0053.cs class MyClass //defaults to private accessibility // try the following line instead // public class MyClass { } public class MyClass2 { public MyClass myProperty   // CS0053 { get { return new MyClass(); } set { } } } public class MyClass3 { public static void Main() { } }  
```