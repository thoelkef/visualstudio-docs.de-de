---
title: "Compilerfehler CS0443 | Microsoft Docs"
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
  - "CS0443"
dev_langs: 
  - "CSharp"
helpviewer_keywords: 
  - "CS0443"
ms.assetid: 8f7f71ff-5eb5-4a1d-80ff-77303472eb8e
caps.latest.revision: 10
caps.handback.revision: 10
author: "BillWagner"
ms.author: "wiwagn"
manager: "wpickett"
---
# Compilerfehler CS0443
Syntaxfehler. Wert erwartet.  
  
 Dieser Fehler tritt auf, wenn Sie auf ein Array verweisen, ohne einen Wert für den Arrayindex anzugeben.  
  
## Beispiel  
 Mit dem folgenden Code wird CS0443 generiert:  
  
```  
// CS0443.cs using System; class MyClass { public static void Main() { int[,] x = new int[1,5]; if (x[] == 5) {} // CS0443 // if (x[0, 0] == 5) {} } }  
```