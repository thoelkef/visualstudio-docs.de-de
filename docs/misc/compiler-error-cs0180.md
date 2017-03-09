---
title: "Compilerfehler CS0180 | Microsoft Docs"
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
  - "CS0180"
dev_langs: 
  - "CSharp"
helpviewer_keywords: 
  - "CS0180"
ms.assetid: a21bf0a2-ed5a-4ddd-88d3-240babc5888a
caps.latest.revision: 8
caps.handback.revision: 8
author: "BillWagner"
ms.author: "wiwagn"
manager: "wpickett"
---
# Compilerfehler CS0180
"Member" kann nicht gleichzeitig extern und abstrakt sein.  
  
 Die Schlüsselwörter [abstract](/dotnet/csharp/language-reference/keywords/abstract) und [extern](/dotnet/csharp/language-reference/keywords/extern) schließen sich gegenseitig aus. Das Schlüsselwort `extern` bedeutet, dass der Member außerhalb der Datei definiert ist. Das Schlüsselwort **abstract** bedeutet, dass die Implementierung in einer abgeleiteten Klasse bereitgestellt wird. Weitere Informationen finden Sie unter [Methoden](/dotnet/csharp/programming-guide/classes-and-structs/methods).  
  
 Im folgenden Beispiel wird CS0180 generiert:  
  
```  
// CS0180.cs namespace MyNamespace { public class MyClass { public extern abstract int Foo(int a);   // CS0180 public static void Main() { } } }  
```