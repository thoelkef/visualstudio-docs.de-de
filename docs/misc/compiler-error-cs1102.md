---
title: "Compilerfehler CS1102 | Microsoft Docs"
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
  - "CS1102"
dev_langs: 
  - "CSharp"
helpviewer_keywords: 
  - "CS1102"
ms.assetid: 7de798d4-1b4b-4842-ae43-9bc83e6dc9a3
caps.latest.revision: 8
caps.handback.revision: 8
author: "BillWagner"
ms.author: "wiwagn"
manager: "wpickett"
---
# Compilerfehler CS1102
Der Parametermodifizierer "out" kann nicht mit "this" verwendet werden.  
  
 Wird der erste Parameter einer statischen Methode durch das Schlüsselwort `this` geändert, wird dem Compiler signalisiert, dass die Methode eine Erweiterungsmethode ist. Für den ersten Parameter einer Erweiterungsmethode sind keine weiteren Modifizierer erforderlich oder zulässig.  
  
### So beheben Sie diesen Fehler  
  
1.  Entfernen Sie die unzulässigen Modifizierer aus dem ersten Parameter.  
  
## Beispiel  
 Im folgenden Beispiel wird der Fehler CS1102 generiert:  
  
```  
// cs1102.cs // Compile with: /target:library. public static class Extensions { // No type parameters. public static void Test(this out int i) {} // CS1102 //Single type parameter public static void Test<T>(this out T t) {}// CS1102 //Multiple type parameters public static void Test<T,U,V>(this out U u) {}// CS1102 }  
```  
  
## Siehe auch  
 [Erweiterungsmethoden](/dotnet/csharp/programming-guide/classes-and-structs/extension-methods)   
 [this](/dotnet/csharp/language-reference/keywords/this)   
 [out](/dotnet/csharp/language-reference/keywords/out)