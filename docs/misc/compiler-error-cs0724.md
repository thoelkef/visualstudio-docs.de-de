---
title: "Compilerfehler CS0724 | Microsoft Docs"
ms.custom: ""
ms.date: "10/01/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-csharp"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "CS0724"
dev_langs: 
  - "CSharp"
helpviewer_keywords: 
  - "CS0724"
ms.assetid: bcdb2017-7a43-4242-b4e2-a1ae03d6d73f
caps.latest.revision: 8
caps.handback.revision: 8
author: "BillWagner"
ms.author: "wiwagn"
manager: "wpickett"
---
# Compilerfehler CS0724
Erfordert kein CLSCompliant\-Attribut, da die Assembly kein CLSCompliant\-Attribut aufweist.  
  
 Im folgenden Beispiel wird CS0724 aufgrund der `throw`\-Anweisung innerhalb des `finally`\-Klauselblocks generiert.  
  
## Beispiel  
 Im folgenden Beispiel wird CS0724 generiert:  
  
```  
// CS0724.cs using System; class X { static void Test() { try { throw new Exception(); } catch { try { } finally { throw; // CS0724 } } } static void Main() { } }  
```