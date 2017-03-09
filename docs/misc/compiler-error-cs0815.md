---
title: "Compilerfehler CS0815 | Microsoft Docs"
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
  - "CS0815"
dev_langs: 
  - "CSharp"
helpviewer_keywords: 
  - "CS0815"
ms.assetid: 8f055d34-9ee4-482e-9e79-8b3698c55cb4
caps.latest.revision: 8
caps.handback.revision: 8
author: "BillWagner"
ms.author: "wiwagn"
manager: "wpickett"
---
# Compilerfehler CS0815
'expression' kann keiner implizit typisierten lokalen Variablen zugeordnet werden.  
  
 Ein Ausdruck, der als Initialisierer für eine implizit typisierte Variable verwendet wird, muss einen Typ aufweisen. Da anonyme Funktionsausdrücke, Methodengruppenausdrücke und der NULL\-Literalausdruck nicht über einen Typ verfügen, sind sie nicht als Initialisierer geeignet. Eine implizit typisierte Variable kann nicht mit einem NULL\-Wert in ihrer Deklaration initialisiert werden. Ihr kann später jedoch ein Wert von NULL zugewiesen werden.  
  
### So beheben Sie diesen Fehler  
  
1.  Geben Sie einen expliziten Typ für die Variable an.  
  
## Beispiel  
 Der folgende Code generiert CS0815:  
  
```  
// cs0815.cs class Test { public static int Main() { var d = s => -1; // CS0815 var e = (string s) => 0; // CS0815 var p = null;//CS0815 var del = delegate(string a) { return -1; };// CS0815 return -1; } }  
```  
  
## Siehe auch  
 [Implizit typisierte lokale Variablen](/dotnet/csharp/programming-guide/classes-and-structs/implicitly-typed-local-variables)