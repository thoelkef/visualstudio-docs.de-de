---
title: "Compilerfehler CS1628 | Microsoft Docs"
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
  - "CS1628"
dev_langs: 
  - "CSharp"
helpviewer_keywords: 
  - "CS1628"
ms.assetid: 520f864c-afe3-4db2-b44e-cfaac28ff49d
caps.latest.revision: 7
caps.handback.revision: 7
author: "BillWagner"
ms.author: "wiwagn"
manager: "wpickett"
---
# Compilerfehler CS1628
Der ref\- oder out\-Parameter "Parameter" kann nicht in einer anonymen Methode, einem lambda\-Ausdruck oder einem Abfrageausdruck verwendet werden.  
  
 Dieser Fehler tritt auf, wenn Sie einen ref\- oder out\-Parameter in einem anonymen Methodenblock verwenden. Um diesen Fehler zu vermeiden, verwenden Sie eine lokale Variable oder ein anderes Konstrukt.  
  
 Im folgenden Beispiel wird CS1628 generiert:  
  
```  
// CS1628.cs delegate int MyDelegate(); class C { public static void F(ref int i) { MyDelegate d = delegate { return i; };  // CS1628 // Try this instead: // int tmp = i; // MyDelegate d = delegate { return tmp; }; } public static void Main() { } }  
```