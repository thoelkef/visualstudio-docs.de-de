---
title: "Compilerfehler CS1642 | Microsoft Docs"
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
  - "CS1642"
dev_langs: 
  - "CSharp"
helpviewer_keywords: 
  - "CS1642"
ms.assetid: 2efeedf1-1839-485d-8b8c-9045df1951f0
caps.latest.revision: 10
caps.handback.revision: 10
author: "BillWagner"
ms.author: "wiwagn"
manager: "wpickett"
---
# Compilerfehler CS1642
Pufferfelder fester Größe dürfen nur Member von Strukturen sein.  
  
 Dieser Fehler tritt auf, wenn Sie ein Pufferfeld mit fester Größe in einer `class` und nicht in einer `struct` verwenden. Ändern Sie die `class` in eine `struct`, oder deklarieren Sie das Feld als normales Array, um diesen Fehler zu beheben.  
  
## Beispiel  
 Im folgenden Beispiel wird CS1642 generiert:  
  
```  
// CS1642.cs // compile with: /unsafe /target:library unsafe class C { fixed int a[10];   // CS1642 } unsafe struct D { fixed int a[10]; } unsafe class E { public int[] a = null; }  
```