---
title: "Compilerfehler CS0011 | Microsoft Docs"
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
  - "CS0011"
dev_langs: 
  - "CSharp"
helpviewer_keywords: 
  - "CS0011"
ms.assetid: 892553d7-a516-4631-84cd-94db5722c90d
caps.latest.revision: 18
caps.handback.revision: 18
author: "BillWagner"
ms.author: "wiwagn"
manager: "wpickett"
---
# Compilerfehler CS0011
Die Basisklasse oder Schnittstelle "Klasse" in der Assembly "Assembly", auf die vom Typ "Typ" verwiesen wird, konnte nicht aufgelöst werden.  
  
 Eine mit **\/reference** aus einer Datei importierte Klasse wird von einer nicht gefundenen Klasse abgeleitet oder implementiert eine Schnittstelle, die nicht gefunden wird. Dieser Fall kann eintreten, wenn eine erforderliche DLL nicht gleichzeitig Bestandteil der Kompilierung mit **\/reference** ist.  
  
 Weitere Informationen finden Sie unter [Add Reference Dialog Box](http://msdn.microsoft.com/de-de/2feb0fe2-0805-4cc9-8cba-b0315849dfb7) und [\/reference \(Import Metadata\)](/dotnet/csharp/language-reference/compiler-options/reference-compiler-option).  
  
## Beispiel  
  
```  
// CS0011_1.cs // compile with: /target:library public class Outer { public class B { } }  
```  
  
## Beispiel  
 Die zweite Datei erstellt eine DLL, die eine `C`\-Klasse definiert, die von der `B`\-Klasse abgeleitet wird, welche im vorherigen Beispiel generiert wurde.  
  
```  
// CS0011_2.cs // compile with: /target:library /reference:CS0011_1.dll // post-build command: del /f CS0011_1.dll public class C : Outer.B {}  
```  
  
## Beispiel  
 Die dritte Datei ersetzt die im ersten Schritt erstellte DLL und lässt die Definition der inneren `B`\-Klasse aus.  
  
```  
// CS0011_3.cs // compile with: /target:library /out:cs0011_1.dll public class Outer {}  
```  
  
## Beispiel  
 Schließlich verweist die vierte Datei auf die im zweiten Beispiel definierte `C`\-Klasse, die von der `B`\-Klasse abgeleitet wird, und die nun fehlt.  
  
 Im folgenden Beispiel wird CS0011 generiert.  
  
```  
// CS0011_4.cs // compile with: /reference:CS0011_1.dll /reference:CS0011_2.dll // CS0011 expected class M { public static void Main() { C c = new C(); } }  
```  
  
## Siehe auch  
 [Add Reference Dialog Box](http://msdn.microsoft.com/de-de/2feb0fe2-0805-4cc9-8cba-b0315849dfb7)   
 [\/reference \(Import Metadata\)](/dotnet/csharp/language-reference/compiler-options/reference-compiler-option)