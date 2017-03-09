---
title: "Compilerfehler CS0473 | Microsoft Docs"
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
  - "CS0473"
dev_langs: 
  - "CSharp"
helpviewer_keywords: 
  - "CS0473"
ms.assetid: 58eb141e-7da0-41c8-b868-7cd2a15f07f9
caps.latest.revision: 9
caps.handback.revision: 9
author: "BillWagner"
ms.author: "wiwagn"
manager: "wpickett"
---
# Compilerfehler CS0473
Die explizite Schnittstellenimplementierung 'methodenname' stimmt mit mehreren Schnittstellenmembern überein Welches Schnittstellenmember tatsächlich ausgewählt wird, hängt von der Implementierung ab. Erwägen Sie stattdessen die Verwendung einer nicht expliziten Implementierung.  
  
 In manchen Fällen kann eine generische Methode die gleiche Signatur erhalten wie eine nicht generische Methode. Das Problem liegt darin, dass das Metadatensystem der Common Language Infrastructure \(CLI\) keine Möglichkeit bietet, eindeutig festzustellen, welche Methode an welchen Slot gebunden ist. Diese Entscheidung muss von der CLI getroffen werden.  
  
> [!NOTE]
>  Dieser Fehler wird in Visual Studio 2008 an Stellen ausgelöst, an denen er in Visual Studio 2005 nicht ausgelöst wurde.  
  
### So beheben Sie diesen Fehler  
  
1.  Entfernen Sie die explizite Implementierung, und lassen Sie beide Schnittstellenmethoden durch die implizite Implementierung `public int TestMethod(int)` implementieren.  
  
## Beispiel  
 Mit dem folgenden Code wird CS0473 generiert:  
  
```  
// cs0473.cs public interface ITest<T> { int TestMethod(int i); int TestMethod(T i); } public class ImplementingClass : ITest<int> { int ITest<int>.TestMethod(int i) // CS0473 { return i + 1; } public int TestMethod(int i) { return i - 1; } } class T { static int Main() { ImplementingClass a = new ImplementingClass(); if (a.TestMethod(0) != -1) return -1; ITest<int> i_a = a; System.Console.WriteLine(i_a.TestMethod(0).ToString()); if (i_a.TestMethod(0) != 1) return -1; return 0; } }  
  
```  
  
## Siehe auch  
 [Fabulous Adventures in Coding](http://blogs.msdn.com/ericlippert/archive/2006/04/06/570126.aspx)