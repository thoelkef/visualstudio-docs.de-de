---
title: "Compilerfehler CS1925 | Microsoft Docs"
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
  - "CS1925"
dev_langs: 
  - "CSharp"
helpviewer_keywords: 
  - "CS1925"
ms.assetid: b60806a5-2ccf-47f5-873b-7ac2292fdb54
caps.latest.revision: 7
caps.handback.revision: 7
author: "BillWagner"
ms.author: "wiwagn"
manager: "wpickett"
---
# Compilerfehler CS1925
Ein Objekt vom Typ 'Typ' kann nicht mit einem Auflistungsinitialisierer initialisiert werden.  
  
 Auflistungsinitialisierer sind nur für Auflistungsklassen zulässig, die bestimmte Kriterien erfüllen. Weitere Informationen finden Sie unter [Objekt\- und Auflistungsinitialisierer](/dotnet/csharp/programming-guide/classes-and-structs/object-and-collection-initializers). Dieser Fehler wird auch ausgelöst, wenn Sie versuchen, die Kurzform eines Arrayinitialisierers zu verwenden, der in einem Auflistungsinitialisierer geschachtelt ist.  
  
### So beheben Sie diesen Fehler  
  
1.  Initialisieren Sie das Objekt durch Aufrufen seiner Konstruktoren und Methoden.  
  
## Beispiel  
 Durch den folgenden Code wird der Fehler CS1925 ausgelöst:  
  
```  
// cs1925.cs public class Student { public int[] Scores; } class Test { static void Main(string[] args) { Student student = new Student { Scores = { 1, 2, 3 } }; // CS1925 } }  
```