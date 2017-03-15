---
title: "Compilerfehler CS0410 | Microsoft Docs"
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
  - "CS0410"
dev_langs: 
  - "CSharp"
helpviewer_keywords: 
  - "CS0410"
ms.assetid: a8b11042-9119-465e-abf6-235cbc7b8db5
caps.latest.revision: 8
caps.handback.revision: 8
author: "BillWagner"
ms.author: "wiwagn"
manager: "wpickett"
---
# Compilerfehler CS0410
Keine Überladung für „method“ hat die richtigen Parameter oder Rückgabetypen.  
  
 Dieser Fehler tritt auf, wenn Sie versuchen, einen Delegaten mit einer Funktion zu instanziieren, die die falschen Parametertypen aufweist. Die Parametertypen des Delegaten müssen mit denen der Funktion übereinstimmen, die Sie dem Delegaten zuweisen.  
  
## Beispiel  
 Im folgenden Beispiel wird der Fehler CS0410 generiert:  
  
```  
// CS0410.cs // compile with: /langversion:ISO-1 class Test { delegate void D(double d ); static void F(int i) { } static void Main() { D d = new D(F);  // CS0410 } }  
```