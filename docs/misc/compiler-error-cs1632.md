---
title: "Compilerfehler CS1632 | Microsoft Docs"
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
  - "CS1632"
dev_langs: 
  - "CSharp"
helpviewer_keywords: 
  - "CS1632"
ms.assetid: fa18061a-8c6c-4788-b74e-62bacb16aed8
caps.latest.revision: 8
caps.handback.revision: 8
author: "BillWagner"
ms.author: "wiwagn"
manager: "wpickett"
---
# Compilerfehler CS1632
Ein Steuerelement kann den Text einer anonymen Methode oder eines Lambda\-Ausdrucks nicht verlassen.  
  
 Dieser Fehler tritt auf, wenn eine jump\-Anweisung \(**break**, `goto`, **continue**, usw.\) versucht, die Kontrolle außerhalb eines anonymen Methodenblocks zu verschieben. Ein anonymer Methodenblock ist ein Funktionsrumpf und kann nur beendet werden, indem eine return\-Anweisung oder das Ende des Blocks erreicht wurde.  
  
 Im folgenden Beispiel wird CS1632 generiert:  
  
```  
// CS1632.cs // compile with: /target:library delegate void MyDelegate(); class MyClass { public void Test() { for (int i = 0 ; i < 5 ; i++) { MyDelegate d = delegate { break;   // CS1632 }; } } }  
```