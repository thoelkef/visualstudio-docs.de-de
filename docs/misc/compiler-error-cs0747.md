---
title: "Compilerfehler CS0747 | Microsoft Docs"
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
  - "CS0747"
dev_langs: 
  - "CSharp"
helpviewer_keywords: 
  - "CS0747"
ms.assetid: dc1b7e38-cee5-406c-b193-a60ec4faebe1
caps.latest.revision: 7
caps.handback.revision: 7
author: "BillWagner"
ms.author: "wiwagn"
manager: "wpickett"
---
# Compilerfehler CS0747
Ungültige Deklaration des Initialisierermembers.  
  
 Ein Objektinitialisierer wird verwendet, um Werte zu Eigenschaften oder Feldern zuzuweisen. Jeder Ausdruck, der keine Zuweisung zu einer Eigenschaft oder einem Feld ist, ist ein Kompilierzeitfehler.  
  
### So beheben Sie diesen Fehler  
  
1.  Stellen Sie sicher, dass alle Ausdrücke im Initialisierer Zuweisungen zu den Eigenschaften oder Feldern des Typs sind. Im folgenden Beispiel ist der zweite Ausdruck ein Fehler, da der Wert `1` keiner Eigenschaft und keinem Feld von `List<int>` zugewiesen ist.  
  
## Beispiel  
 Der folgende Code generiert CS0747:  
  
```  
// cs0747.cs using System.Collections.Generic; public class C { public static int Main() { var t = new List<int> { Capacity = 2, 1 }; // CS0747 return 1; } }  
```  
  
## Siehe auch  
 [Objekt\- und Auflistungsinitialisierer](/dotnet/csharp/programming-guide/classes-and-structs/object-and-collection-initializers)