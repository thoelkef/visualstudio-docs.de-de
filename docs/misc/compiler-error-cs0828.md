---
title: "Compilerfehler CS0828 | Microsoft Docs"
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
  - "CS0828"
dev_langs: 
  - "CSharp"
helpviewer_keywords: 
  - "CS0828"
ms.assetid: e18ffe72-2fcc-436d-be7f-8c8365b86129
caps.latest.revision: 7
caps.handback.revision: 7
author: "BillWagner"
ms.author: "wiwagn"
manager: "wpickett"
---
# Compilerfehler CS0828
'ausdruck' kann keiner Eigenschaft eines anonymen Typs zugeordnet werden.  
  
 Ein anonymer Typ kann nicht mit einem NULL\-Wert, einem unsicheren Typ, einer Methodengruppe oder einer anonymen Funktion initialisiert werden.  
  
### So beheben Sie diesen Fehler  
  
1.  Fügen Sie entweder auf der linken Seite der Zuweisung eine Typdeklaration hinzu, oder ändern Sie den Ausdruck auf der rechten Seite so, dass er einen akzeptablen Typ aufweist.  
  
## Beispiel  
 Der folgende Code generiert CS0828, da ein Member eines anonymen Typs nicht mit einem NULL\-Wert initialisiert werden kann.  
  
```  
// cs0828.cs using System; public class C { public static int Main() { var a = 1; var c = new { p1 = null }; // CS0828 return 1; } }  
```  
  
## Siehe auch  
 [Implizit typisierte lokale Variablen](/dotnet/csharp/programming-guide/classes-and-structs/implicitly-typed-local-variables)