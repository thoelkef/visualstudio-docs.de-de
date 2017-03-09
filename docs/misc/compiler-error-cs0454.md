---
title: "Compilerfehler CS0454 | Microsoft Docs"
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
  - "CS0454"
dev_langs: 
  - "CSharp"
helpviewer_keywords: 
  - "CS0454"
ms.assetid: 2c83bc5e-53bb-473e-92aa-5122dadd79d1
caps.latest.revision: 10
caps.handback.revision: 10
author: "BillWagner"
ms.author: "wiwagn"
manager: "wpickett"
---
# Compilerfehler CS0454
Zirkuläre Einschränkungsabhängigkeit mit 'Typarameter 1' und 'Typparameter 2'.  
  
 Dieser Fehler tritt auf, da zu einem bestimmten Zeitpunkt ein Typparameter auf einen anderen verweist, während der zweite Typparameter wiederum auf den ersten verweist. Unterbrechen Sie die zirkuläre Einschränkungsabhängigkeit durch Entfernen einer der Einschränkungen, um diesen Fehler zu beheben. Beachten Sie, dass die zirkuläre Einschränkungsabhängigkeit indirekt erfolgen kann.  
  
## Beispiel  
 Der folgende Code generiert den Fehler CS0454.  
  
```  
// CS0554 using System; public class GenericsErrors { public class G4<T> where T : T { } // CS0454 }  
```  
  
## Beispiel  
 Das folgende Beispiel zeigt eine zirkuläre Abhängigkeit zwischen zwei Typeinschränkungen.  
  
```  
public class Gen<T,U> where T : U where U : T  // CS0454 { }  
```