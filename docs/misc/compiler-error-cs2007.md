---
title: "Compilerfehler CS2007 | Microsoft Docs"
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
  - "CS2007"
dev_langs: 
  - "CSharp"
helpviewer_keywords: 
  - "CS2007"
ms.assetid: 9be20e8e-2424-4435-9371-778fb12823c0
caps.latest.revision: 8
caps.handback.revision: 8
author: "BillWagner"
ms.author: "wiwagn"
manager: "wpickett"
---
# Compilerfehler CS2007
Nicht erkannte Befehlszeilenoption: "option".  
  
 Dem Compiler wurde eine Zeichenfolge übergeben, bei der es sich trotz des Schrägstrichs \(\/\) am Anfang um keine [Compileroption](/dotnet/csharp/language-reference/compiler-options/index) handelte.  
  
 Im folgenden Beispiel wird CS2007 generiert:  
  
```  
// CS2007.cs // compile with: /recur // CS2007 expected class x { public static void Main() {} }  
```