---
title: "Compilerfehler CS0623 | Microsoft Docs"
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
  - "CS0623"
dev_langs: 
  - "CSharp"
helpviewer_keywords: 
  - "CS0623"
ms.assetid: c9fd6888-b9c5-48bf-b25b-2fae1446ad24
caps.latest.revision: 8
caps.handback.revision: 8
author: "BillWagner"
ms.author: "wiwagn"
manager: "wpickett"
---
# Compilerfehler CS0623
Arrayinitialisierer können nur in einer Variablen oder einem Feldinitialisierer verwendet werden. Verwenden Sie stattdessen einen neuen Ausdruck.  
  
 Es wurde versucht, ein Array mit einem Arrayinitialisierer in einem Kontext zu initialisieren, in dem es nicht zulässig ist.  
  
## Beispiel  
 Im folgenden Beispiel wird CS0623 erzeugt, weil der Compiler "\\{4\\}" als eingebetteten Arrayinitialisierer innerhalb des äußeren Arrayinitialisierers interpretiert:  
  
```  
//cs0632.cs using System; class X { public int[] x = { 2, 3, {4}}; //CS0623 }  
```  
  
## Siehe auch  
 [Arrays](/dotnet/csharp/programming-guide/arrays/index)