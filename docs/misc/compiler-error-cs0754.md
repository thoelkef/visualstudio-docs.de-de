---
title: "Compilerfehler CS0754 | Microsoft Docs"
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
  - "CS0754"
dev_langs: 
  - "CSharp"
helpviewer_keywords: 
  - "CS0754"
ms.assetid: c83e04b5-6ab5-45c2-805e-0ba4f041d506
caps.latest.revision: 5
caps.handback.revision: 5
author: "BillWagner"
ms.author: "wiwagn"
manager: "wpickett"
---
# Compilerfehler CS0754
Eine partielle Methode darf Schnittstellenmethoden nicht explizit implementieren.  
  
 Eine partielle Methode kann nicht als explizite Implementierung einer in einer Schnittstelle definierten Methode deklariert werden.  
  
### So beheben Sie diesen Fehler  
  
1.  Entfernen Sie die angegebene explizite Schnittstelle aus der Methodendeklaration.  
  
## Beispiel  
 Durch den folgenden Code wird der Fehler CS0754 ausgelöst:  
  
```  
// cs0754.cs using System; public interface IF { void Part(); } public partial class C : IF { partial void IF.Part(); //CS0754 public static int Main() { return 1; } }  
```  
  
## Siehe auch  
 [Explizite Schnittstellenimplementierung](/dotnet/csharp/programming-guide/interfaces/explicit-interface-implementation)   
 [Partielle Klassen und Methoden](/dotnet/csharp/programming-guide/classes-and-structs/partial-classes-and-methods)