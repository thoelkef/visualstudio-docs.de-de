---
title: "Compilerfehler CS1508 | Microsoft Docs"
ms.custom: ""
ms.date: "11/17/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-csharp"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "CS1508"
dev_langs: 
  - "CSharp"
helpviewer_keywords: 
  - "CS1508"
ms.assetid: 979bc615-58ce-49f8-ba73-e6cf57c56418
caps.latest.revision: 7
caps.handback.revision: 7
author: "BillWagner"
ms.author: "wiwagn"
manager: "wpickett"
---
# Compilerfehler CS1508
Der Ressourcenbezeichner "Bezeichner" wurde in dieser Assembly bereits verwendet.  
  
 In einer Kompilierung wurde derselbe Bezeichner \(***Bezeichner***\) an mindestens zwei [\/resource](/dotnet/csharp/language-reference/compiler-options/resource-compiler-option)\- oder [\/linkresource](/dotnet/csharp/language-reference/compiler-options/linkresource-compiler-option)\-Compileroptionen übergeben.  
  
 Folgende Optionen würden beispielsweise CS1508 generieren:  
  
```  
/resource:anyfile.bmp,DuplicatIdent /linkresource:a.bmp,DuplicatIdent  
```