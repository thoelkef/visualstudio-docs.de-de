---
title: "Compilerfehler CS0073 | Microsoft Docs"
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
  - "CS0073"
dev_langs: 
  - "CSharp"
helpviewer_keywords: 
  - "CS0073"
ms.assetid: 579ae534-59ab-4fc5-ad7e-f87639f3f9cd
caps.latest.revision: 8
caps.handback.revision: 8
author: "BillWagner"
ms.author: "wiwagn"
manager: "wpickett"
---
# Compilerfehler CS0073
Ein add\- oder remove\-Accessor muss Text enthalten.  
  
 Ein Schlüsselwort **add** oder **remove** in einer [Ereignisdefinition](/dotnet/csharp/language-reference/keywords/event) muss einen Textkörper aufweisen. Weitere Informationen finden Sie unter [Ereignisse](/dotnet/csharp/programming-guide/events/index).  
  
 Im folgenden Beispiel wird CS0073 generiert:  
  
```  
// CS0073.cs delegate void del(); class Test { public event del MyEvent { add;   // CS0073 // try the following lines instead // add // { //    MyEvent += value; // } remove { MyEvent -= value; } } public static void Main() { } }  
```