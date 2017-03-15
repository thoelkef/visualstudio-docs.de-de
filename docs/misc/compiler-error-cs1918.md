---
title: "Compilerfehler CS1918 | Microsoft Docs"
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
  - "CS1918"
dev_langs: 
  - "CSharp"
helpviewer_keywords: 
  - "CS1918"
ms.assetid: 9ad2cbbd-3c10-4d56-b4cd-385103d005d4
caps.latest.revision: 7
caps.handback.revision: 7
author: "BillWagner"
ms.author: "wiwagn"
manager: "wpickett"
---
# Compilerfehler CS1918
Member der name\-Eigenschaft vom Typ "Typ" können nicht mit einem Objektinitialisierer zugewiesen werden, da es sich um einen Werttyp handelt.  
  
 Dieser Fehler tritt auf, wenn Sie versuchen, einen Objektinitialisierer zur Initialisierung der Eigenschaften eines Strukturtyps zu verwenden, der selbst eine Eigenschaft der initialisierten Klasse ist.  
  
### So beheben Sie diesen Fehler  
  
1.  Wenn Sie die Felder der Eigenschaft im Objektinitialisierer vollständig initialisieren müssen, ändern Sie die Struktur in einen Klassentyp. Andernfalls initialisieren Sie die Strukturmember in einem separaten Methodenaufruf, nachdem Sie das Objekt mithilfe des Objektinitialisierers erstellt haben.  
  
## Beispiel  
 Im folgenden Beispiel wird CS1918 generiert:  
  
```  
// cs1918.cs public struct MyStruct { public int i; } public class Test { private MyStruct str = new MyStruct(); public MyStruct Str { get { return str; } } public static int Main() { Test t = new Test { Str = { i = 1 } }; // CS1918 return 0; } }  
  
```  
  
## Siehe auch  
 [Objekt\- und Auflistungsinitialisierer](/dotnet/csharp/programming-guide/classes-and-structs/object-and-collection-initializers)