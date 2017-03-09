---
title: "Compilerfehler CS0403 | Microsoft Docs"
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
  - "CS0403"
dev_langs: 
  - "CSharp"
helpviewer_keywords: 
  - "CS0403"
ms.assetid: 6e5d55ce-d6bf-419d-aded-aaa2e5963bb6
caps.latest.revision: 14
caps.handback.revision: 14
author: "BillWagner"
ms.author: "wiwagn"
manager: "wpickett"
---
# Compilerfehler CS0403
NULL kann nicht in den Typparameter "Name" konvertiert werden, da dieser Werttyp möglicherweise nicht auf NULL festgelegt werden kann. Verwenden Sie stattdessen "default\('T'\)".  
  
 Sie können einem unbekannten benannten Typ nicht NULL zuweisen, da es sich möglicherweise um einen Werttyp handelt, für den eine NULL\-Zuweisung nicht zulässig ist. Wenn die generische Klasse keine Werttypen annimmt, verwenden Sie die Klassentypeinschränkung. Wenn die Klasse Werttypen \(z. B. die integrierten Typen\) annimmt, können Sie die NULL\-Zuweisung möglicherweise durch den Ausdruck `default(T)` ersetzen, wie im folgenden Beispiel gezeigt.  
  
## Beispiel  
 Im folgenden Beispiel wird CS0403 generiert.  
  
```  
// CS0403.cs // compile with: /target:library class C<T> { public void f() { T t = null;  // CS0403 T t2 = default(T);   // OK } } class D<T> where T : class { public void f() { T t = null;  // OK } }  
```