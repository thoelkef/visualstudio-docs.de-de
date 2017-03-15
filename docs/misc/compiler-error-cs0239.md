---
title: "Compilerfehler CS0239 | Microsoft Docs"
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
  - "CS0239"
dev_langs: 
  - "CSharp"
helpviewer_keywords: 
  - "CS0239"
ms.assetid: 2e07bbc2-03a9-44b2-b321-477ca95fff8c
caps.latest.revision: 8
caps.handback.revision: 8
author: "BillWagner"
ms.author: "wiwagn"
manager: "wpickett"
---
# Compilerfehler CS0239
'Member': Der geerbte Member 'geerbter Member' kann nicht überschrieben werden, da er versiegelt ist.  
  
 Ein Member kann einen [versiegelten](/dotnet/csharp/language-reference/keywords/sealed) geerbten Member nicht [überschreiben](/dotnet/csharp/language-reference/keywords/override). Weitere Informationen finden Sie unter [Checked und Unchecked](/dotnet/csharp/language-reference/keywords/checked-and-unchecked).  
  
 Im folgenden Beispiel wird CS0239 generiert:  
  
```  
// CS0239.cs abstract class MyClass { public abstract void f(); } class MyClass2 : MyClass { public static void Main() { } public override sealed void f() { } } class MyClass3 : MyClass2 { public override void f()   // CS0239 // Try the following definition instead: // public new void f() { } }  
```