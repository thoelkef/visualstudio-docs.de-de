---
title: "Compilerfehler CS0748 | Microsoft Docs"
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
  - "CS0748"
dev_langs: 
  - "CSharp"
helpviewer_keywords: 
  - "CS0748"
ms.assetid: da1935af-a5ea-41f4-84ae-58559b750566
caps.latest.revision: 7
caps.handback.revision: 7
author: "BillWagner"
ms.author: "wiwagn"
manager: "wpickett"
---
# Compilerfehler CS0748
Inkonsistente Verwendung des lambda\-Parameters. Alle Parametertypen müssen entweder explizit oder implizit sein.  
  
 Wenn ein Lambda\-Ausdruck über mehrere Eingabeparameter verfügt, können nicht einige Parameter implizite Typisierung verwenden, während andere explizite Typisierung verwenden.  
  
### So beheben Sie diesen Fehler  
  
1.  Weisen Sie allen Eingabeparametern entweder implizite oder explizite Typen zu.  
  
## Beispiel  
 Der folgende Code generiert Fehler CS0748, da im Lambda\-Ausdruck nur `alpha` ein expliziter Typ zugewiesen wurde:  
  
```  
// cs0748.cs class CS0748 { delegate double D(int x, int y); D d = (int alpha, beta) => { return beta / alpha; }; // CS0748 }  
```  
  
## Siehe auch  
 [Lambda\-Ausdrücke](/dotnet/csharp/programming-guide/statements-expressions-operators/lambda-expressions)