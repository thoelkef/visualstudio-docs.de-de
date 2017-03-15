---
title: "Compilerwarnung CS3024 | Microsoft Docs"
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
  - "CS3024"
dev_langs: 
  - "CSharp"
helpviewer_keywords: 
  - "CS3024"
ms.assetid: fef9db31-9a7f-42d5-ad37-3e7faf661f95
caps.latest.revision: 7
caps.handback.revision: 7
author: "BillWagner"
ms.author: "wiwagn"
manager: "wpickett"
---
# Compilerwarnung CS3024
Einschränkungstyp 'Typ' ist nicht CLS\-kompatibel.  
  
 Der Compiler gibt diese Warnung aus, da die Verwendung eines nicht mit CLS\-kompatiblen Typs als generische Typeinschränkung verhindern kann, dass Code, der in einigen Sprachen verfasst wurde, Ihre generische Klasse verwendet.  
  
### So beseitigen Sie diese Warnung  
  
1.  Verwenden Sie einen CLS\-kompatiblen Typ für die Typeinschränkung.  
  
## Beispiel  
 Im folgenden Beispiel wird der Fehler CS3024 an verschiedenen Stellen generiert:  
  
```  
// cs3024.cs // Compile with: /target:library [assembly: System.CLSCompliant(true)] [type: System.CLSCompliant(false)] public class TestClass // CS3024 { public ushort us; } [type: System.CLSCompliant(false)] public interface ITest // CS3024 {} public interface I<T> where T : TestClass {} public class TestClass_2<T> where T : ITest {} public class TestClass_3<T> : I<T> where T : TestClass {} public class TestClass_4<T> : TestClass_2<T> where T : ITest {} public class Test { public static int Main() { return 0; } }  
```  
  
## Siehe auch  
 [Einschränkungen für Typparameter](/dotnet/csharp/programming-guide/generics/constraints-on-type-parameters)