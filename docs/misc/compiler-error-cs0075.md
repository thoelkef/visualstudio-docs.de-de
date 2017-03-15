---
title: "Compilerfehler CS0075 | Microsoft Docs"
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
  - "CS0075"
dev_langs: 
  - "CSharp"
helpviewer_keywords: 
  - "CS0075"
ms.assetid: 5084d260-705e-4ff5-8f7a-7f74052fcbbb
caps.latest.revision: 7
caps.handback.revision: 7
author: "BillWagner"
ms.author: "wiwagn"
manager: "wpickett"
---
# Compilerfehler CS0075
Negative Werte müssen in runde Klammern gesetzt werden, um umgewandelt zu werden.  
  
 Wenn Sie eine Umwandlung über ein Schlüsselwort vornehmen, das einen vordefinierten Typ angibt, benötigen Sie keine Klammern. Andernfalls müssen Sie die Klammern setzen, weil \(x\) – y nicht als Umwandlungsausdruck angesehen wird. Aus der C\#\-Spezifikation, Abschnitt 7.6.6:  
  
 *Aus der Regel zur Sicherstellung der Eindeutigkeit folgt, dass, wenn x und y Bezeichner sind, \(x\)y, \(x\)\(y\) und \(x\)\(\-y\) Typumwandlungsausdrücke sind, \(x\)\-y jedoch kein Typumwandlungsausdruck ist, auch wenn x einen Typ bezeichnet. Wenn jedoch x ein Schlüsselwort ist, das einen vordefinierten Typ bezeichnet \(z. B. int\), handelt es sich bei allen vier Formen um Typumwandlungsausdrücke \(weil ein solches Schlüsselwort an sich keinen Ausdruck bilden kann\).*  
  
 Mit dem folgenden Code wird CS0075 generiert:  
  
```  
// CS0075 namespace MyNamespace { enum MyEnum { } public class MyClass { public static void Main() { // To fix the error, place the negative // values below in parentheses int i = (System.Int32) - 4; //CS0075 MyEnum e = (MyEnum) - 1;    //CS0075 System.Console.WriteLine(i); //to avoid warning System.Console.WriteLine(e); //to avoid warning } } }  
```  
  
## Siehe auch  
 [Umwandlung und Typkonvertierungen](/dotnet/csharp/programming-guide/types/casting-and-type-conversions)