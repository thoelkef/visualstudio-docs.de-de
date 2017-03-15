---
title: "Compilerfehler CS1657 | Microsoft Docs"
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
  - "CS1657"
dev_langs: 
  - "CSharp"
helpviewer_keywords: 
  - "CS1657"
ms.assetid: 6f0aeebe-5c90-4d5b-981c-1795d2e8fbb9
caps.latest.revision: 9
caps.handback.revision: 9
author: "BillWagner"
ms.author: "wiwagn"
manager: "wpickett"
---
# Compilerfehler CS1657
"Parameter" kann nicht als ref\- oder out\-Argument übergeben werden, weil "Grund"  
  
 Dieser Fehler tritt auf, wenn eine Variable als [ref](/dotnet/csharp/language-reference/keywords/ref)\- oder [out](/dotnet/csharp/language-reference/keywords/out)\-Argument in einem Kontext verwendet wird, in dem diese Variable schreibgeschützt ist. Schreibgeschützte Kontexte schließen [foreach](/dotnet/csharp/language-reference/keywords/foreach-in)\-Iterationsvariablen, [using](/dotnet/csharp/language-reference/keywords/using-statement)\-Variablen und `fixed`\-Variablen ein. Um diesen Fehler zu beheben, rufen Sie keine Funktionen auf, die `foreach`\-, `using`\- oder `fixed`\-Variablen als `ref`\- oder `out`\-Parameter in `using`\-Blöcken, `foreach`\-Anweisungen und `fixed`\-Anweisungen verwenden.  
  
## Beispiel  
 Im folgenden Beispiel wird CS1657 generiert:  
  
```  
// CS1657.cs using System; class C : IDisposable { public int i; public void Dispose() {} } class CMain { static void f(ref C c) { } static void Main() { using (C c = new C()) { f(ref c);  // CS1657 } } }  
```  
  
## Beispiel  
 Im folgenden Code wird das gleiche Problem für eine `fixed`\-Anweisung veranschaulicht:  
  
```  
// CS1657b.cs // compile with: /unsafe unsafe class C { static void F(ref int* p) { } static void Main() { int[] a = new int[5]; fixed(int* p = a) F(ref p); // CS1657 } }  
```