---
title: "Compilerwarnung (Stufe 3) CS1717 | Microsoft Docs"
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
  - "CS1717"
dev_langs: 
  - "CSharp"
helpviewer_keywords: 
  - "CS1717"
ms.assetid: 5b150a2c-5d61-4cd8-b4d4-e6c2b93b52c6
caps.latest.revision: 14
caps.handback.revision: 14
author: "BillWagner"
ms.author: "wiwagn"
manager: "wpickett"
---
# Compilerwarnung (Stufe 3) CS1717
Zuweisung zur gleichen Variablen. Wollten Sie eine andere Zuweisung durchführen?  
  
 Diese Warnung tritt auf, wenn Sie eine Variable sich selbst zuweisen, wie etwa `a = a`.  
  
 Diese Warnung kann aufgrund mehrerer häufiger Fehler auftreten:  
  
-   Das Schreiben von `a = a` als Bedingung einer **if**\-Anweisung, wie etwa in `if (a = a)`. Sie wollten vermutlich `if (a == a)` ausdrücken, was immer wahr ist, also könnten Sie das auch präziser in der Form `if (true)` ausdrücken.  
  
-   Tippfehler. Sie meinten vermutlich `a = b`.  
  
-   Auslassen des Schlüsselworts **this** in einem Konstruktor, in dem der Parameter den gleichen Namen wie das Feld hat: Sie meinten vermutlich `this.a = a`.  
  
## Beispiel  
 Im folgenden Beispiel wird CS1717 generiert:  
  
```  
// CS1717.cs // compile with: /W:3 public class Test { public static void Main() { int x = 0; x = x;   // CS1717 } }  
```