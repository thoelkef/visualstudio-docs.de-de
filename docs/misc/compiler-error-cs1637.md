---
title: "Compilerfehler CS1637 | Microsoft Docs"
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
  - "CS1637"
dev_langs: 
  - "CSharp"
helpviewer_keywords: 
  - "CS1637"
ms.assetid: 95aa82ab-bd52-4def-b5f3-d65e6dcb3855
caps.latest.revision: 7
caps.handback.revision: 7
author: "BillWagner"
ms.author: "wiwagn"
manager: "wpickett"
---
# Compilerfehler CS1637
Iteratoren dürfen keine unsicheren Parameter oder yield\-Typen aufweisen.  
  
 Überprüfen Sie die Argumentliste des Iterators und den Typ eventueller yield\-Anweisungen, um zu bestätigen, dass Sie keine unsicheren Typen verwenden.  
  
## Beispiel  
 Im folgenden Beispiel wird CS1637 generiert:  
  
```  
// CS1637.cs // compile with: /unsafe using System.Collections; public unsafe class C { public IEnumerator Iterator1(int* p)  // CS1637 { yield return null; } }  
```