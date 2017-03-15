---
title: "Compilerwarnung (Stufe 2) CS0253 | Microsoft Docs"
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
  - "CS0253"
dev_langs: 
  - "CSharp"
helpviewer_keywords: 
  - "CS0253"
ms.assetid: e02d5dac-c2d9-45ca-9dd3-dda06c96f4d6
caps.latest.revision: 6
caps.handback.revision: 6
author: "BillWagner"
ms.author: "wiwagn"
manager: "wpickett"
---
# Compilerwarnung (Stufe 2) CS0253
Möglicherweise unbeabsichtigter Verweisvergleich. Wandeln Sie die rechte Seite in den Typ 'typ' um, um einen Wertvergleich durchzuführen.  
  
 Der Compiler führt einen Verweisvergleich aus. Wenn Sie den Wert von Zeichenfolgen vergleichen möchten, wandeln Sie die rechte Seite des Ausdrucks in `type` um.  
  
 Im folgenden Beispiel wird CS0253 generiert:  
  
```  
// CS0253.cs // compile with: /W:2 using System; class MyClass { public static void Main() { string s = "11"; object o = s + s; bool c = s == o;   // CS0253 // try the following line instead // bool c = s == (string)o; } }  
```