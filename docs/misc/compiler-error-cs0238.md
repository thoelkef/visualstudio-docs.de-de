---
title: "Compilerfehler CS0238 | Microsoft Docs"
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
  - "CS0238"
dev_langs: 
  - "CSharp"
helpviewer_keywords: 
  - "CS0238"
ms.assetid: 9b50c6e2-2c3f-431d-bdb7-557b0ec51626
caps.latest.revision: 8
caps.handback.revision: 8
author: "BillWagner"
ms.author: "wiwagn"
manager: "wpickett"
---
# Compilerfehler CS0238
"Member" ist keine Überschreibung und kann daher nicht versiegelt werden.  
  
 [sealed](/dotnet/csharp/language-reference/keywords/sealed) wurde auf einen Member angewendet, der nicht gleichzeitig durch [override](/dotnet/csharp/language-reference/keywords/override) gekennzeichnet war. Weitere Informationen finden Sie unter [Vererbung](/dotnet/csharp/programming-guide/classes-and-structs/inheritance).  
  
 Im folgenden Beispiel wird CS0238 generiert:  
  
```  
// CS0238.cs abstract class MyClass { public abstract void f(); } class MyClass2 : MyClass { public static void Main() { } public sealed void f() // CS0238 // Try the following definition instead: // public override sealed void f() { } }  
```