---
title: "Compilerfehler CS1940 | Microsoft Docs"
ms.custom: ""
ms.date: "11/17/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-csharp"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "CS1940"
dev_langs: 
  - "CSharp"
helpviewer_keywords: 
  - "CS1940"
ms.assetid: 546e9bba-725d-4ea9-826f-37ec9d832add
caps.latest.revision: 8
caps.handback.revision: 8
author: "BillWagner"
ms.author: "wiwagn"
manager: "wpickett"
---
# Compilerfehler CS1940
Für den Quelltyp "Typ" wurden mehrere Implementierungen des Abfragemusters gefunden. Mehrdeutiger Aufruf von "Methode".  
  
 Dieser Fehler wird generiert, wenn mehrere Implementierungen einer Abfragemethode definiert sind, und der Compiler nicht eindeutig ermitteln kann, welche am besten für die Abfrage verwendet werden soll. Im folgenden Beispiel haben beide Versionen von `Select` dieselbe Signatur, da beide ein `int` als Eingabeparameter akzeptieren und `int` als Rückgabewert haben.  
  
### So beheben Sie diesen Fehler  
  
1.  Stellen Sie nur eine Implementierung für jede Methode bereit.  
  
## Beispiel  
 Mit dem folgenden Code wird CS1940 generiert:  
  
```  
// cs1940.cs using System; //must include explicitly for types defined in 3.5 class Test { public delegate int Dele(int x); int num = 0; public int Select(Func<int, int> d) { return d(this.num); } public int Select(Dele d) // CS1940 { return d(this.num) + 1; } public static void Main() { var q = from x in new Test() select x; } }  
```  
  
## Siehe auch  
 [Standard Query Operators Overview](../Topic/Standard%20Query%20Operators%20Overview.md)