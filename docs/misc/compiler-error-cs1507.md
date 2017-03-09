---
title: "Compilerfehler CS1507 | Microsoft Docs"
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
  - "CS1507"
dev_langs: 
  - "CSharp"
helpviewer_keywords: 
  - "CS1507"
ms.assetid: e1be3aba-81dc-4f65-87a4-d3f90b82dc7d
caps.latest.revision: 7
caps.handback.revision: 7
author: "BillWagner"
ms.author: "wiwagn"
manager: "wpickett"
---
# Compilerfehler CS1507
Beim Erstellen eines Moduls ist eine Verknüpfung mit der Ressourcendatei 'datei' nicht möglich.  
  
 [\/linkresource](/dotnet/csharp/language-reference/compiler-options/linkresource-compiler-option) wurde in der gleichen Kompilierung wie [\/target:module](../Topic/-target:module%20\(C%23%20Compiler%20Options\).md) verwendet, was nicht zulässig ist. Folgende Optionen würden beispielsweise CS1507 generieren:  
  
```  
csc /linkresource:rf.resource /target:module in.cs  
```  
  
 Das Einbetten von Ressourcen \([\/resource](/dotnet/csharp/language-reference/compiler-options/resource-compiler-option)\) ist jedoch zulässig.