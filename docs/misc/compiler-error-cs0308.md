---
title: "Compilerfehler CS0308 | Microsoft Docs"
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
  - "CS0308"
dev_langs: 
  - "CSharp"
helpviewer_keywords: 
  - "CS0308"
ms.assetid: b52ef9d2-f5b3-4baf-9a7e-bb1371e79463
caps.latest.revision: 8
caps.handback.revision: 8
author: "BillWagner"
ms.author: "wiwagn"
manager: "wpickett"
---
# Compilerfehler CS0308
Der nicht generische „Bezeichner“ für Typ oder Methode kann nicht mit Typargumenten verwendet werden.  
  
 Die Methode oder der Typ ist nicht generisch, aber wurde mit Typargumenten verwendet. Entfernen Sie die spitzen Klammern und Typargumente, oder deklarieren Sie die Methode oder den Typ als generische Methode oder generischen Typ neu, um diesen Fehler zu vermeiden.  
  
 Im folgenden Beispiel wird CS0308 generiert:  
  
```  
// CS0308a.cs class MyClass { public void F() {} public static void Main() { F<int>();  // CS0308 – F is not generic. // Try this instead: // F(); } }  
```  
  
 Im folgenden Beispiel wird auch CS0308 generiert. Verwenden Sie zum Beheben des Fehlers die Direktive „using System.Collections.Generic“.  
  
```  
// CS0308b.cs // compile with: /t:library using System.Collections; // To resolve, uncomment the following line: // using System.Collections.Generic; public class MyStack<T> { // Store the elements of the stack: private T[] items = new T[100]; private int stack_counter = 0; // Define the iterator block: public IEnumerator<T> GetEnumerator()   // CS0308 { for (int i = stack_counter - 1 ; i >= 0; i--) yield return items[i]; } }  
  
```