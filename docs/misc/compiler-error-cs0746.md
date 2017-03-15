---
title: "Compilerfehler CS0746 | Microsoft Docs"
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
  - "CS0746"
dev_langs: 
  - "CSharp"
helpviewer_keywords: 
  - "CS0746"
ms.assetid: 36baf7f2-b092-422c-ab53-95154bfceb0a
caps.latest.revision: 6
caps.handback.revision: 6
author: "BillWagner"
ms.author: "wiwagn"
manager: "wpickett"
---
# Compilerfehler CS0746
Ungültige Deklaration eines anonymen Typmembers. Anonyme Typmember müssen mit einer Memberzuweisung, einem einfachen Namen oder einem Memberzugriff deklariert werden.  
  
 Ein anonymer Typ muss mit einer Memberzuweisung, einem einfachen Namen oder einem Memberzugriff deklariert werden.  
  
### So beheben Sie diesen Fehler  
  
1.  Stellen Sie sicher, dass in der Deklaration nur Memberzuweisungen, einfache Namen oder Ausdrücke für den Memberzugriff verwendet werden.  
  
## Beispiel  
 Durch den folgenden Code wird der Fehler CS0746 in der Deklaration von `incorrect_1` und `incorrect_2` ausgelöst. In den folgenden Deklarationen werden zwei Möglichkeiten aufgezeigt, einen anonymen Typ richtig zu deklarieren.  
  
```  
// cs0746.cs public class C { public static int Main() { int i = 100; string s = "Bottles of beer."; var incorrect_1 = new { a.b = 1 }; // CS0746 var incorrect_2 = new {100, "Bottles of beer."}; // CS0746 var correct_1 = new { i, s }; //OK var correct_2 = new {num = i, message = s}; // OK return 1; } }  
  
```  
  
## Siehe auch  
 [Anonyme Typen](/dotnet/csharp/programming-guide/classes-and-structs/anonymous-types)