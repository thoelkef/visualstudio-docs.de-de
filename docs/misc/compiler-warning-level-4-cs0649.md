---
title: "Compilerwarnung (Stufe 4) CS0649 | Microsoft Docs"
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
  - "CS0649"
dev_langs: 
  - "CSharp"
helpviewer_keywords: 
  - "CS0649"
ms.assetid: 37137b18-12ed-4a0f-92e6-ee5fb0532ef3
caps.latest.revision: 6
caps.handback.revision: 6
author: "BillWagner"
ms.author: "wiwagn"
manager: "wpickett"
---
# Compilerwarnung (Stufe 4) CS0649
Dem Feld "Feld" wird nie etwas zugewiesen, und es hat immer seinen Standardwert von "Wert"  
  
 Der Compiler hat eine nicht initialisierte private oder interne Felddeklaration erkannt, der nie ein Wert zugewiesen wird.  
  
 Im folgenden Beispiel wird CS0649 generiert:  
  
```  
// CS0649.cs // compile with: /W:4 using System.Collections; class MyClass { Hashtable table;  // CS0649 // You may have intended to initialize the variable to null // Hashtable table = null; // Or you may have meant to create an object here // Hashtable table = new Hashtable(); public void Func(object o, string p) { // Or here // table = new Hashtable(); table[p] = o; } public static void Main() { } }  
```