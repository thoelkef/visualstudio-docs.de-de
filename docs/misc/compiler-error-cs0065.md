---
title: "Compilerfehler CS0065 | Microsoft Docs"
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
  - "CS0065"
dev_langs: 
  - "CSharp"
helpviewer_keywords: 
  - "CS0065"
ms.assetid: 49ca30a8-513a-40ed-aa0c-eb696a25b91f
caps.latest.revision: 7
caps.handback.revision: 7
author: "BillWagner"
ms.author: "wiwagn"
manager: "wpickett"
---
# Compilerfehler CS0065
„event“: Die Ereigniseigenschaft muss sowohl add\- als auch remove\-Accessoren besitzen.  
  
 Ein Ereignis, das kein Feld ist, muss beide Zugriffsmethoden unterstützen.  
  
 Im folgenden Beispiel wird CS0065 generiert:  
  
```  
// CS0065.cs using System; public delegate void Eventhandler(object sender, int e); public class MyClass { public event EventHandler Click   // CS0065, { // to fix, uncomment the add and remove definitions /* add { Click += value; } remove { Click -= value; } */ } public static void Main() { } }  
```  
  
## Siehe auch  
 [Ereignisse](/dotnet/csharp/programming-guide/events/index)