---
title: "Compilerfehler CS0542 | Microsoft Docs"
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
  - "CS0542"
dev_langs: 
  - "CSharp"
helpviewer_keywords: 
  - "CS0542"
ms.assetid: 68a89948-8b56-4cd5-95e2-0df7fcad50ac
caps.latest.revision: 9
caps.handback.revision: 9
author: "BillWagner"
ms.author: "wiwagn"
manager: "wpickett"
---
# Compilerfehler CS0542
"Benutzerdefinierter Typ": Membernamen dürfen nicht dem einschließenden Typ entsprechen.  
  
 Die Member einer Klasse oder Struktur dürfen nicht den gleichen Namen wie die Klasse oder Struktur haben, es sei denn, der Member ist ein Konstruktor.  
  
 Im folgenden Beispiel wird CS0542 generiert:  
  
```c#  
// CS0542.cs class C { public int C; }  
```  
  
 Dieser Fehler kann verursacht werden, wenn Sie versehentlich einen Rückgabetyp für einen Konstruktor festlegen, der ihn tatsächlich in eine normale Methode umwandelt. Im folgenden Beispiel wird CS0542 generiert, weil `F` eine Methode und kein Konstruktor ist, da sie über einen Rückgabetyp verfügt:  
  
```c#  
// CS0542.cs class F { // Remove void from F() to resolve the problem. void F()   // CS0542, same name as the class { } } class MyClass { public static void Main() { } }  
```  
  
 Wenn Ihre Klasse den Namen "Element" hat und über einen als `this` deklarierten Indexer verfügt, kann dieser Fehler ausgegeben werden. Ein Standardindexer erhält im ausgegebenen Code den Namen "Element", wodurch der Konflikt entsteht.  
  
```c#  
// CS0542b.cs class Item { public int this[int i]  // CS0542 { get { return 0; } } } class CMain { public static void Main() { } }  
```