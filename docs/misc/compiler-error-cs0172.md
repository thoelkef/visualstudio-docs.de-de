---
title: "Compilerfehler CS0172 | Microsoft Docs"
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
  - "CS0172"
dev_langs: 
  - "CSharp"
helpviewer_keywords: 
  - "CS0172"
ms.assetid: 1272c575-3580-4897-95fb-83f45d7435ae
caps.latest.revision: 8
caps.handback.revision: 8
author: "BillWagner"
ms.author: "wiwagn"
manager: "wpickett"
---
# Compilerfehler CS0172
Der Typ des bedingten Ausdrucks kann nicht bestimmt werden, da "Typ1" und "Typ2" implizit ineinander konvertiert werden.  
  
 In einer bedingten Anweisung muss es möglich sein, die Typen auf beiden Seiten des `:`\-Operators zu konvertieren. Darüber hinaus dürfen keine Routinen für eine gegenseitige Konvertierung vorhanden sein; Sie benötigen nur eine Konvertierung. Weitere Informationen finden Sie unter [Konvertierungsoperatoren](/dotnet/csharp/programming-guide/statements-expressions-operators/conversion-operators).  
  
 Im folgenden Beispiel wird CS0172 generiert:  
  
```  
// CS0172.cs public class Square { public class Circle { public static implicit operator Circle(Square aa) { return null; } public static implicit operator Square(Circle aa) // using explicit resolves this error // public static explicit operator Square(Circle aa) { return null; } } public static void Main() { Circle aa = new Circle(); Square ii = new Square(); object o = (1 == 1) ? aa : ii;   // CS0172 // the following cast would resolve this error // (1 == 1) ? aa : (Circle)ii; } }  
```