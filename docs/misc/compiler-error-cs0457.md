---
title: "Compilerfehler CS0457 | Microsoft Docs"
ms.custom: ""
ms.date: "10/29/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-csharp"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "CS0457"
dev_langs: 
  - "CSharp"
helpviewer_keywords: 
  - "CS0457"
ms.assetid: 5d5cf762-c817-4468-9455-59e966b8c140
caps.latest.revision: 14
caps.handback.revision: 14
author: "BillWagner"
ms.author: "wiwagn"
manager: "wpickett"
---
# Compilerfehler CS0457
Mehrdeutige benutzerdefinierte Konvertierungen 'Konvertierungsmethodenname 1' und 'Konvertierungsmethodenname 2' beim Konvertieren von 'Typname 1' in 'Typname 2'  
  
 Es sind zwei Konvertierungsmethoden anwendbar, und der Compiler kann nicht entscheiden, welche Methode zu verwenden ist.  
  
 Ein Szenario, das diesen Fehler verursachen kann, sieht wie folgt aus:  
  
-   Sie möchten „Klasse A“ in „Klasse B“ konvertieren, wobei A und B nicht verbunden sind.  
  
-   A wird von A0 abgeleitet und es gibt eine Methode, die von A0 in B konvertiert.  
  
-   B verfügt über die Unterklasse B1 und es gibt eine Methode, die von A in B1 konvertiert.  
  
 Der Compiler bewertet die beiden Konvertierungsmethoden gleichermaßen, da die erste Konvertierung den besten Zieltyp und die zweite Konvertierung den besten Quelltyp bereitstellt. Da der Compiler keine Auswahl treffen kann, wird dieser Fehler generiert. Schreiben Sie eine neue explizite Methode zum Konvertieren von A in B, um das Problem zu beheben.  
  
 In einem weiteren Szenario, bei dem dieser Fehler auftritt, sind zwei Methoden vorhanden, die A in B konvertieren. Geben Sie die zu verwendende Konvertierung über eine explizite Umwandlung an, um das Problem zu beheben.  
  
## Beispiel  
 Im folgenden Beispiel wird CS0457 generiert.  
  
```  
// CS0457.cs using System; public class A { } public class G0 {  } public class G1<R> : G0 {  } public class H0 { public static implicit operator G0(H0 h) { return new G0(); } } public class H1<R> : H0 { public static implicit operator G1<R>(H1<R> h) { return new G1<R>(); } } public class Test { public static void F0(G0 g) {  } public static void Main() { H1<A> h1a = new H1<A>(); F0(h1a);   // CS0457 } }  
```