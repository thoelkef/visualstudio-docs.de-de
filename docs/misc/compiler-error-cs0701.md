---
title: "Compilerfehler CS0701 | Microsoft Docs"
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
  - "CS0701"
dev_langs: 
  - "CSharp"
helpviewer_keywords: 
  - "CS0701"
ms.assetid: eb844e31-00bd-468d-9f77-11d10a4ef120
caps.latest.revision: 13
caps.handback.revision: 13
author: "BillWagner"
ms.author: "wiwagn"
manager: "wpickett"
---
# Compilerfehler CS0701
'Bezeichner' ist keine gültige Einschränkung. Ein Typ, der als Einschränkung verwendet wird, muss eine Schnittstelle, eine nicht versiegelte Klasse oder ein Typparameter sein.  
  
 Dieser Fehler tritt auf, wenn ein versiegelter Typ als Einschränkung verwendet wird. Verwenden Sie ausschließlich nicht versiegelte Typen als Einschränkungen, um diesen Fehler zu beheben.  
  
## Beispiel  
 Im folgenden Beispiel wird CS0701 generiert:  
  
```  
// CS0701.cs // compile with: /target:library class C<T> where T : System.String {}   // CS0701 class D<T> where T : System.Attribute {}   // OK  
```