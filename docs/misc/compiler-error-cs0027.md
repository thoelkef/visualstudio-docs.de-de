---
title: "Compilerfehler CS0027 | Microsoft Docs"
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
  - "CS0027"
dev_langs: 
  - "CSharp"
helpviewer_keywords: 
  - "CS0027"
ms.assetid: 3a599876-9643-4c68-9457-3306858a73e9
caps.latest.revision: 12
caps.handback.revision: 12
author: "BillWagner"
ms.author: "wiwagn"
manager: "wpickett"
---
# Compilerfehler CS0027
Das this\-Schlüsselwort ist im aktuellen Kontext nicht verfügbar.  
  
 Das [this](/dotnet/csharp/language-reference/keywords/this)\-Schlüsselwort wurde außerhalb einer Eigenschaft, einer Methode oder eines Konstruktors gefunden.  
  
 Um diesen Fehler zu beheben, ändern Sie entweder die Anweisung so, dass das `this`\-Schlüsselwort nicht mehr verwendet wird, und\/oder verschieben Sie die Anweisung ganz oder teilweise in eine Eigenschaft, eine Methode oder einen Konstruktor.  
  
 Im folgenden Beispiel wird CS0027 generiert:  
  
```  
using System; using System.Collections.Generic; using System.Text; namespace ConsoleApplication3 { class MyClass { int err1 = this.Fun() + 1;  // CS0027 public int Fun() { return 10; } public void Test() { // valid use of this int err = this.Fun() + 1; Console.WriteLine(err); } public static void Main() { MyClass c = new MyClass(); c.Test(); } } }  
```