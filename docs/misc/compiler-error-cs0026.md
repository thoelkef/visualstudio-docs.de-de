---
title: "Compilerfehler CS0026 | Microsoft Docs"
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
  - "CS0026"
dev_langs: 
  - "CSharp"
helpviewer_keywords: 
  - "CS0026"
ms.assetid: 8767fbc1-8ba7-4e88-a9f9-7e620411882b
caps.latest.revision: 12
caps.handback.revision: 12
author: "BillWagner"
ms.author: "wiwagn"
manager: "wpickett"
---
# Compilerfehler CS0026
Das this\-Schlüsselwort ist in einer statischen Eigenschaft\/Methode oder einem statischen Feldinitialisierer nicht gültig.  
  
 Das [this](/dotnet/csharp/language-reference/keywords/this)\-Schlüsselwort verweist auf ein Objekt, das eine Instanz eines Typs ist. Da statische Methoden unabhängig von jeder Instanz der enthaltenden Klasse sind, ist das Schlüsselwort „this“ ohne Bedeutung und daher nicht zulässig. Weitere Informationen finden Sie unter [Statische Klassen und statische Klassenmember](/dotnet/csharp/programming-guide/classes-and-structs/static-classes-and-static-class-members) und [Objekte](/dotnet/csharp/programming-guide/classes-and-structs/objects).  
  
## Beispiel  
 Im folgenden Beispiel wird der Fehler CS0026 generiert:  
  
```  
// CS0026.cs public class A { public static int i = 0; public static void Main() { // CS0026 this.i = this.i + 1; // Try the following line instead: // i = i + 1; } }  
```