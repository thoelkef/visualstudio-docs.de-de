---
title: "Compilerfehler CS0820 | Microsoft Docs"
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
  - "CS0820"
dev_langs: 
  - "CSharp"
helpviewer_keywords: 
  - "CS0820"
ms.assetid: 38c05162-ef20-42a8-9611-02698360dec5
caps.latest.revision: 8
caps.handback.revision: 8
author: "BillWagner"
ms.author: "wiwagn"
manager: "wpickett"
---
# Compilerfehler CS0820
Arrayinitialisierer kann keiner implizit typisierten lokalen Variablen zugewiesen werden  
  
 Ein implizit typisiertes Array ist ein Array, dessen Elementtyp vom Compiler abgeleitet wird. Es muss wie im Beispielcode gezeigt mit dem `new`\[\]\-Modifizierer initialisiert werden.  
  
### So beheben Sie diesen Fehler  
  
-   Verwenden Sie den `new`\[\]\-Modifizierer mit dem Arrayinitialisierer.  
  
-   Verwenden Sie keine implizit typisierte lokale Variable.  
  
## Beispiel  
 Im folgenden Code wird CS0820 generiert und gezeigt, wie ein implizit typisiertes Array richtig initialisiert wird:  
  
```  
//cs0820.cs class G { public static int Main() { var a = { 1,2,3}; //CS0820 // Try using one of the following lines instead. // var b = new[] { 1, 2, 3 }; //int[] b = {1, 2, 3}; return -1; } }  
```  
  
## Siehe auch  
 [Implizit typisierte lokale Variablen](/dotnet/csharp/programming-guide/classes-and-structs/implicitly-typed-local-variables)