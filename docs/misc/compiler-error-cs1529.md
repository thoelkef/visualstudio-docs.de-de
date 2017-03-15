---
title: "Compilerfehler CS1529 | Microsoft Docs"
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
  - "CS1529"
dev_langs: 
  - "CSharp"
helpviewer_keywords: 
  - "CS1529"
ms.assetid: 672a6fd1-3a1f-422c-a29f-46f196d15211
caps.latest.revision: 10
caps.handback.revision: 10
author: "BillWagner"
ms.author: "wiwagn"
manager: "wpickett"
---
# Compilerfehler CS1529
Eine using\-Klausel muss allen anderen im Namespace definierten Elementen mit Ausnahme externer Aliasdeklarationen vorangehen.  
  
 Eine [using](/dotnet/csharp/language-reference/keywords/using)\-Klausel muss zuerst in einem Namespace vorkommen.  
  
## Beispiel  
 Im folgenden Beispiel wird CS1529 generiert:  
  
```  
// CS1529.cs namespace X { namespace Subspace { using Microsoft; class SomeClass { }; using Microsoft;      // CS1529, place before class definition } using System.Reflection;  // CS1529, place before namespace 'Subspace' } using System;                 // CS1529, place at the beginning of the file  
```