---
title: "Compilerfehler CS0527 | Microsoft Docs"
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
  - "CS0527"
dev_langs: 
  - "CSharp"
helpviewer_keywords: 
  - "CS0527"
ms.assetid: 1acd244b-c55b-424f-b038-a130d65b8685
caps.latest.revision: 8
caps.handback.revision: 8
author: "BillWagner"
ms.author: "wiwagn"
manager: "wpickett"
---
# Compilerfehler CS0527
Der Typ "Typ" in der Schnittstellenliste ist keine Schnittstelle.  
  
 Eine [Struktur](/dotnet/csharp/language-reference/keywords/struct) oder [Schnittstelle](/dotnet/csharp/language-reference/keywords/interface) kann von einer anderen Schnittstelle, aber nicht von irgendeinem anderen Typ erben.  
  
 Im folgenden Beispiel wird CS0527 generiert:  
  
```  
// CS0527.cs // compile with: /target:library public struct clx : int {}   // CS0527 int not an interface  
```