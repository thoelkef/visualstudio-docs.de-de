---
title: "Compilerfehler CS0012 | Microsoft Docs"
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
  - "CS0012"
dev_langs: 
  - "CSharp"
helpviewer_keywords: 
  - "CS0012"
ms.assetid: 5523e349-22f4-4b0b-b4b0-c4bf26c461f4
caps.latest.revision: 10
caps.handback.revision: 10
author: "BillWagner"
ms.author: "wiwagn"
manager: "wpickett"
---
# Compilerfehler CS0012
Der Typ "Typ" ist in einer nicht referenzierten Assembly definiert. Fügen Sie einen Verweis auf die Assembly "Assembly" hinzu.  
  
 Die Definition für einen referenzierten Typ wurde nicht gefunden. Dies kann passieren, wenn eine erforderliche DLL\-Datei nicht in der Kompilierung enthalten ist. Weitere Informationen finden Sie unter [Add Reference Dialog Box](http://msdn.microsoft.com/de-de/2feb0fe2-0805-4cc9-8cba-b0315849dfb7) und [\/reference \(Import Metadata\)](/dotnet/csharp/language-reference/compiler-options/reference-compiler-option).  
  
 Die folgende Sequenz von Kompilierungen führt zu CS0012:  
  
```  
// cs0012a.cs // compile with: /target:library public class A {}  
```  
  
 Dann:  
  
```  
// cs0012b.cs // compile with: /target:library /reference:cs0012a.dll public class B { public static A f() { return new A(); } }  
```  
  
 Dann:  
  
```  
// cs0012c.cs // compile with: /reference:cs0012b.dll class C { public static void Main() { object o = B.f();   // CS0012 } }  
```  
  
 Sie können diesen CS0012\-Fehler auflösen, indem Sie mit `/reference:cs0012b.dll;cs0012a.dll` kompilieren oder in Visual Studio im [Add Reference Dialog Box](http://msdn.microsoft.com/de-de/2feb0fe2-0805-4cc9-8cba-b0315849dfb7) einen Verweis auf „cs0012a.dll“ zusätzlich zu „cs0012b.dll“ hinzufügen.