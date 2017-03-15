---
title: "Compilerfehler CS2017 | Microsoft Docs"
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
  - "CS2017"
dev_langs: 
  - "CSharp"
helpviewer_keywords: 
  - "CS2017"
ms.assetid: 16fd0c3b-018f-4734-809d-8d98d05a254c
caps.latest.revision: 7
caps.handback.revision: 7
author: "BillWagner"
ms.author: "wiwagn"
manager: "wpickett"
---
# Compilerfehler CS2017
\/main kann beim Erstellen eines Moduls oder einer Bibliothek nicht angegeben werden.  
  
 Sie dürfen keinen Haupteinstiegspunkt angeben, wenn Sie eine DLL\-Datei \([\/target:library](../Topic/-target:library%20\(C%23%20Compiler%20Options\).md)\) erstellen.  
  
 Im folgenden Beispiel wird CS2017 generiert:  
  
```  
// CS2017.cs // compile with: /main:MyClass /target:library // CS2017 expected class MyClass { public static void Main() { } }  
```