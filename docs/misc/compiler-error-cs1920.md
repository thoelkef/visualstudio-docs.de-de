---
title: "Compilerfehler CS1920 | Microsoft Docs"
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
  - "CS1920"
dev_langs: 
  - "CSharp"
helpviewer_keywords: 
  - "CS1920"
ms.assetid: efb4782f-a222-4fb5-9e79-8bd2d380520b
caps.latest.revision: 6
caps.handback.revision: 6
author: "BillWagner"
ms.author: "wiwagn"
manager: "wpickett"
---
# Compilerfehler CS1920
Der Elementinitialisierer darf nicht leer sein.  
  
 Ein Auflistungsinitialisierer besteht aus einer Folge von Elementinitialisierern. Die Elementinitialisierer müssen nicht in geschweifte Klammern eingeschlossen sein, sofern sie keinen Zuweisungsausdruck enthalten. Wenn Sie jedoch geschweifte Klammern bereitstellen, dürfen diese nicht leer sein. Wenn der Elementinitialisierer ein Objektinitialisierer ist, können die geschweiften Klammern leer sein, solange der Initialisierer einen neuen Objekterstellungsausdruck enthält.  
  
### So beheben Sie diesen Fehler  
  
-   Fügen Sie den fehlenden Ausdruck zwischen den geschweiften Klammern hinzu.  
  
-   Wenn der Ausdruck ein Objektinitialisierer sein soll, fügen Sie den neuen Objekterstellungsausdruck vor den Klammern hinzu.  
  
## Beispiel  
 Im folgenden Beispiel wird der Fehler CS1920 generiert:  
  
```  
// cs1920.cs using System.Collections.Generic; public class Test { public static int Main() { // Error. Empty initializer // for inner list. List<List<int>> collection = new List<List<int>>() { { } }; // CS1920 // OK. No initializer for inner list. List<List<int>> collection2 = new List<List<int>>() {  }; // OK. Inner list is initialized // to one List<int> with zero elements. List<List<int>> collection3 = new List<List<int>>() { new List<int> { } }; return 0; } }  
```  
  
## Siehe auch  
 [Objekt\- und Auflistungsinitialisierer](/dotnet/csharp/programming-guide/classes-and-structs/object-and-collection-initializers)