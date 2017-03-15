---
title: "Compilerwarnung (Stufe 3) CS0105 | Microsoft Docs"
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
  - "CS0105"
dev_langs: 
  - "CSharp"
helpviewer_keywords: 
  - "CS0105"
ms.assetid: 96d1d5d7-79e9-424f-bbde-f87e88b70003
caps.latest.revision: 7
caps.handback.revision: 7
author: "BillWagner"
ms.author: "wiwagn"
manager: "wpickett"
---
# Compilerwarnung (Stufe 3) CS0105
Die Using\-Direktive für "Namespace" wurde bereits zuvor in diesem Namespace verwendet.  
  
 Ein [Namespace](/dotnet/csharp/language-reference/keywords/namespace), der nur einmal deklariert werden darf, wurde mehrmals deklariert. Entfernen Sie alle doppelten Namespacedeklarationen.  
  
 Im folgenden Beispiel wird CS0105 generiert:  
  
```  
// CS0105.cs // compile with: /W:3 using System; using System;   // CS0105 public class a { public static void Main() { } }  
```