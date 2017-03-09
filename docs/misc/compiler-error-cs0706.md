---
title: "Compilerfehler CS0706 | Microsoft Docs"
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
  - "CS0706"
dev_langs: 
  - "CSharp"
helpviewer_keywords: 
  - "CS0706"
ms.assetid: bc3ac5c0-8c96-43c8-b10a-69bd31b38e4a
caps.latest.revision: 11
caps.handback.revision: 11
author: "BillWagner"
ms.author: "wiwagn"
manager: "wpickett"
---
# Compilerfehler CS0706
Ungültiger Einschränkungstyp. Ein Typ, der als Einschränkung verwendet wird, muss eine Schnittstelle, eine nicht versiegelte Klasse oder ein Typparameter sein.  
  
 Dieser Fehler tritt auf, wenn ein ungültiges Konstrukt in einer Einschränkungsklausel verwendet wird. Verwenden Sie eine Schnittstelle oder eine nicht versiegelte Klasse anstelle des Konstrukts, das den Fehler verursacht hat, um diesen Fehler zu vermeiden.  
  
## Beispiel  
 Im folgenden Beispiel wird CS0706 generiert:  
  
```  
// CS0706.cs // compile with: /target:library class A {} class C<T> where T : int[] {}  // CS0706 class D<T> where T : A {}  // OK  
```