---
title: "Compilerfehler CS0455 | Microsoft Docs"
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
  - "CS0455"
dev_langs: 
  - "CSharp"
helpviewer_keywords: 
  - "CS0455"
ms.assetid: a09840ac-ad8c-4c9c-868e-b83d937c7047
caps.latest.revision: 13
caps.handback.revision: 13
author: "BillWagner"
ms.author: "wiwagn"
manager: "wpickett"
---
# Compilerfehler CS0455
Der Typparameter "Type Parameter Name" erbt die in Konflikt stehenden Einschränkungen "Constraint Name 1" und "Constraint Name 2"  
  
 Dieser Fehler kann auf zwei unterschiedliche Arten erzeugt werden: Es werden Einschränkungen eingerichtet, sodass der Typparameter von zwei nicht zugehörigen Klassen oder sodass er von einem Klassentyp oder einer Verweistypeinschränkung und einer `struct`\-Typeinschränkung oder einer Werttypeinschränkung abgeleitet wird. Um diesen Fehler zu beheben, entfernen Sie den Konflikt aus Ihrer Vererbungshierarchie.  
  
## Beispiel  
 Der folgende Code generiert den Fehler CS0455.  
  
```  
// CS0455.cs using System; public class GenericsErrors { public class B { } public class B2 { } public class G6<T> where T : B { public class N<U> where U : B2, T { } } // CS0455 }  
```