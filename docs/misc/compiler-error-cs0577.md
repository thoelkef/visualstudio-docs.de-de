---
title: "Compilerfehler CS0577 | Microsoft Docs"
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
  - "CS0577"
dev_langs: 
  - "CSharp"
helpviewer_keywords: 
  - "CS0577"
ms.assetid: 34f8f453-f016-4f2c-981a-0d61449cd74b
caps.latest.revision: 7
caps.handback.revision: 7
author: "BillWagner"
ms.author: "wiwagn"
manager: "wpickett"
---
# Compilerfehler CS0577
Das Conditional\-Attribut ist für "Funktion" nicht gültig, weil es sich hierbei um einen Konstruktor, Destruktor, Operator oder eine explizite Schnittstellenimplementierung handelt  
  
 `Conditional` kann auf die angegebenen Methoden nicht angewendet werden.  
  
 Sie können beispielsweise einige Attribute nicht in einer expliziten Schnittstellendefinition verwenden. Im folgenden Beispiel wird CS0577 generiert:  
  
```  
// CS0577.cs // compile with: /target:library interface I { void m(); } public class MyClass : I { [System.Diagnostics.Conditional("a")]   // CS0577 void I.m() {} }  
```