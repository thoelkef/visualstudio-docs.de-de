---
title: "Compilerfehler CS1654 | Microsoft Docs"
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
  - "CS1654"
dev_langs: 
  - "CSharp"
helpviewer_keywords: 
  - "CS1654"
ms.assetid: 471c1298-1908-449d-b765-8dc3cd81a11d
caps.latest.revision: 9
caps.handback.revision: 9
author: "BillWagner"
ms.author: "wiwagn"
manager: "wpickett"
---
# Compilerfehler CS1654
Member von "Variable" können nicht geändert werden, da es sich um einen "schreibgeschützten Variablentyp" handelt.  
  
 Dieser Fehler tritt auf, wenn Sie versuchen, Member einer Variablen zu ändern, die schreibgeschützt ist, da sie sich in einem speziellen Konstrukt befindet.  
  
 Häufig ist dieser Fehler im Bereich von [forEach](/dotnet/csharp/language-reference/keywords/foreach-in)\-Schleifen zu finden. Dieser Fehler tritt während der Kompilierung auf, wenn der Wert der Auflistungselemente geändert wird. Daher können Sie keine Änderungen an Elementen vornehmen, die [Werttypen](/dotnet/csharp/language-reference/keywords/value-types) sind \(einschließlich [Strukturen](/dotnet/csharp/programming-guide/classes-and-structs/structs)\). In einer Auflistung, deren Elemente [Verweistypen](/dotnet/csharp/language-reference/keywords/reference-types) sind, können Sie zugängliche Member der einzelnen Elemente ändern, aber bei jedem Versuch, vollständige Elemente hinzuzufügen, zu entfernen oder zu ersetzen, wird [Compiler Error CS1656](/dotnet/csharp/language-reference/compiler-messages/cs1656) generiert.  
  
## Beispiel  
 Im folgenden Beispiel wird der Fehler CS1654 generiert, da `Book` eine Struktur \(`struct`\) ist. Um den Fehler zu beheben, ändern Sie die Struktur \(`struct`\) in eine Klasse \([class](/dotnet/csharp/language-reference/keywords/class)\).  
  
```  
using System.Collections.Generic; using System.Text; namespace CS1654 { struct Book { public string Title; public string Author; public double Price; public Book(string t, string a, double p) { Title=t; Author=a; Price=p; } } class Program { List<Book> list; static void Main(string[] args) { //Use a collection initializer to initialize the list Program prog = new Program(); prog.list = new List<Book>(); prog.list.Add(new Book ("The C# Programming Language", "Hejlsberg, Wiltamuth, Golde", 29.95)); prog.list.Add(new Book ("The C++ Programming Language", "Stroustrup", 29.95)); prog.list.Add(new Book ("The C Programming Language", "Kernighan, Ritchie", 29.95)); foreach(Book b in prog.list) { //Compile error if Book is a struct //Make Book a class to modify its members b.Price +=9.95; // CS1654 } } } }  
  
```