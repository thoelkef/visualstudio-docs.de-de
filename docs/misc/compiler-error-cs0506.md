---
title: "Compilerfehler CS0506 | Microsoft Docs"
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
  - "CS0506"
dev_langs: 
  - "CSharp"
helpviewer_keywords: 
  - "CS0506"
ms.assetid: 1286957c-2505-4b5f-ade0-154ad5f09dc1
caps.latest.revision: 6
caps.handback.revision: 6
author: "BillWagner"
ms.author: "wiwagn"
manager: "wpickett"
---
# Compilerfehler CS0506
"Funktion1": Der geerbte Member "Funktion2" kann nicht überschrieben werden, da er nicht als "virtual" , "abstract" oder "override" markiert ist.  
  
 Eine Methode wurde überschrieben, die nicht explizit als **virtual**, **abstract** oder `override` markiert ist.  
  
 Im folgenden Beispiel wird CS0506 generiert:  
  
```  
// CS0506.cs namespace MyNameSpace { abstract public class ClassX { public int i = 0; public int f() { return 0; } // Try the following definition for f() instead: // abstract public int f(); } public class ClassY : ClassX { public override int f()   // CS0506 { return 0; } public static int Main() { return 0; } } }  
```