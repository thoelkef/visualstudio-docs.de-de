---
title: "Compilerfehler CS0267 | Microsoft Docs"
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
  - "CS0267"
dev_langs: 
  - "CSharp"
helpviewer_keywords: 
  - "CS0267"
ms.assetid: 11aaab96-5838-4e36-9551-5b032a1089e1
caps.latest.revision: 7
caps.handback.revision: 7
author: "BillWagner"
ms.author: "wiwagn"
manager: "wpickett"
---
# Compilerfehler CS0267
Der "partial"\-Modifizierer kann nur unmittelbar vor "class", "struct" oder "interface" verwendet werden.  
  
 Die Platzierung des **partial**\-Modifizierers in der Deklaration der Klasse, Struktur oder Schnittstelle war falsch. Um den Fehler zu beheben, ändern Sie die Reihenfolge der Modifizierer. Weitere Informationen finden Sie unter [Partielle Klassen und Methoden](/dotnet/csharp/programming-guide/classes-and-structs/partial-classes-and-methods).  
  
 Im folgenden Beispiel wird CS0267 generiert:  
  
```  
// CS0267.cs public partial class MyClass { public MyClass() { } } partial public class MyClass  // CS0267 // Try this line instead: // public partial class MyClass { public void Foo() { } public static void Main() { } }  
```