---
title: "Compilerfehler CS1585 | Microsoft Docs"
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
  - "CS1585"
dev_langs: 
  - "CSharp"
helpviewer_keywords: 
  - "CS1585"
ms.assetid: 429268c3-2dae-4c71-9e0d-be1badb3ca68
caps.latest.revision: 6
caps.handback.revision: 6
author: "BillWagner"
ms.author: "wiwagn"
manager: "wpickett"
---
# Compilerfehler CS1585
Der Membermodifizierer "Schlüsselwort" muss vor dem Membertyp und \-namen stehen.  
  
 Der Zugriffsspezifizierer in einer Methodensignatur steht nicht an der richtigen Stelle.  
  
 Im folgenden Beispiel wird CS1585 generiert:  
  
```  
// CS1585.cs public class Class1 { public void static Main(string[] args)   // CS1585 // try the following line instead // public static void Main(string[] args) { } }  
```