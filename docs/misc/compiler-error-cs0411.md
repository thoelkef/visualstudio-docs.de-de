---
title: "Compilerfehler CS0411 | Microsoft Docs"
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
  - "CS0411"
dev_langs: 
  - "CSharp"
helpviewer_keywords: 
  - "CS0411"
ms.assetid: 290947c9-10d0-427e-99f2-bff20299d533
caps.latest.revision: 8
caps.handback.revision: 8
author: "BillWagner"
ms.author: "wiwagn"
manager: "wpickett"
---
# Compilerfehler CS0411
Die Typargumente für die Methode 'Methode' können nicht von der Verwendung abgeleitet werden. Versuchen Sie die Typargumente explizit anzugeben.  
  
 Dieser Fehler tritt auf, wenn eine generische Methode ohne explizite Angabe der Typargumente aufgerufen wird und der Compiler nicht ableiten kann, welche Typargumente vorgesehen sind. Fügen Sie die vorgesehenen Typargumente in spitzen Klammern hinzu, um diesen Fehler zu vermeiden.  
  
## Beispiel  
 Im folgenden Beispiel wird CS0411 generiert:  
  
```  
// CS0411.cs class C { void G<T>() { } public static void Main() { G();  // CS0411 // Try this instead: // G<int>(); } }  
```  
  
## Beispiel  
 Ein weiterer möglicher Grund für diesen Fehler ist, wenn der Parameter `null` ist und somit über keine Typinformationen verfügt:  
  
```  
// CS0411b.cs class C { public void F<T>(T t) where T : C { } public static void Main() { C c = new C(); c.F(null);  // CS0411 } }  
```