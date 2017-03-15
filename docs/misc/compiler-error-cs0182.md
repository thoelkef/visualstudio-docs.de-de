---
title: "Compilerfehler CS0182 | Microsoft Docs"
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
  - "CS0182"
dev_langs: 
  - "CSharp"
helpviewer_keywords: 
  - "CS0182"
ms.assetid: a9e97bb8-f06e-499f-aadf-26abc2082f98
caps.latest.revision: 11
caps.handback.revision: 11
author: "BillWagner"
ms.author: "wiwagn"
manager: "wpickett"
---
# Compilerfehler CS0182
Ein Attributargument muss ein constant\-, typeof\- oder Arrayerstellungsausdruck eines Attributparametertyps sein.  
  
 Bestimmte Einschränkungen legen fest, welche Arten von Argumenten mit Attributen verwendet werden können. Beachten Sie, dass zusätzlich zu den in der Fehlermeldung angegebenen Einschränkungen die folgenden Typen NICHT als Attributargumente zulässig sind:  
  
-   [sbyte](/dotnet/csharp/language-reference/keywords/sbyte)  
  
-   [ushort](/dotnet/csharp/language-reference/keywords/ushort)  
  
-   [uint](/dotnet/csharp/language-reference/keywords/uint)  
  
-   [ulong](/dotnet/csharp/language-reference/keywords/ulong)  
  
-   [decimal](/dotnet/csharp/language-reference/keywords/decimal)  
  
 Weitere Informationen finden Sie unter [NICHT IM BUILD: Globale Attribute \(C\#\-Programmierhandbuch\)](http://msdn.microsoft.com/de-de/7c6c41f8-f0d5-4345-8987-3d91f9bae136).  
  
## Beispiel  
 Im folgenden Beispiel wird CS0182 generiert:  
  
```  
// CS0182.cs public class MyClass { static string s = "Test"; [System.Diagnostics.ConditionalAttribute(s)]   // CS0182 // try the following line instead // [System.Diagnostics.ConditionalAttribute("Test")] void NonConstantArgumentToConditional() { } public static void Main() { } }  
```