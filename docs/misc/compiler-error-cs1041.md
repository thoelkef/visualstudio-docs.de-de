---
title: "Compilerfehler CS1041 | Microsoft Docs"
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
  - "CS1041"
dev_langs: 
  - "CSharp"
helpviewer_keywords: 
  - "CS1041"
ms.assetid: 9f62c058-cd28-4cb5-835c-d0f25f4fd08e
caps.latest.revision: 7
caps.handback.revision: 7
author: "BillWagner"
ms.author: "wiwagn"
manager: "wpickett"
---
# Compilerfehler CS1041
Bezeichner erwartet; "keyword" ist ein Schlüsselwort  
  
 Ein reserviertes Wort für die C\#\-Sprache wurde gefunden, obwohl ein Bezeichner erwartet wurde. Ersetzen Sie das [Schlüsselwort](/dotnet/csharp/language-reference/keywords/index) durch einen vom Benutzer angegebenen Bezeichner.  
  
## Beispiel  
 Im folgenden Beispiel wird CS1041 generiert:  
  
```  
// CS1041a.cs class MyClass { public void f(int long)   // CS1041 // Try the following instead: // public void f(int i) { } public static void Main() { } }  
```  
  
## Beispiel  
 Wenn Sie aus einer anderen Programmiersprache importieren, die nicht den gleichen Satz von reservierten Wörtern aufweist, können Sie den reservierten Bezeichner mit dem @\-Präfix ändern, wie im folgenden Beispiel gezeigt.  
  
 Ein Bezeichner mit einem `@`\-Präfix wird als ausführlicher Bezeichner bezeichnet.  
  
```  
// CS1041b.cs class MyClass { public void f(int long)   // CS1041 // Try the following instead: // public void f(int @long) { } public static void Main() { } }  
```