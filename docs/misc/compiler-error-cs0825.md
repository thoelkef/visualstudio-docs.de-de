---
title: "Compilerfehler CS0825 | Microsoft Docs"
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
  - "CS0825"
dev_langs: 
  - "CSharp"
helpviewer_keywords: 
  - "CS0825"
ms.assetid: 49393d23-ec5f-4b44-a3fd-7e0a95ac0edd
caps.latest.revision: 7
caps.handback.revision: 7
author: "BillWagner"
ms.author: "wiwagn"
manager: "wpickett"
---
# Compilerfehler CS0825
Das kontextbezogene Schlüsselwort „var“ darf nur in einer lokalen Variablendeklaration verwendet werden.  
  
 Implizite Typisierung mit dem `var`\-Schlüsselwort kann nur auf Variablen im Gültigkeitsbereich der lokalen Methode angewendet werden.  
  
### So beheben Sie diesen Fehler  
  
1.  Wenn die Variable zum Gültigkeitsbereich einer Klasse gehört, weisen sie ihr einen expliziten Typ zu.  Verschieben Sie sie andernfalls in die Methode, in der sie verwendet wird.  
  
## Beispiel  
 Der folgende Code generiert CS0825, weil `var` in einem Klassenfeld verwendet wird:  
  
```  
// cs0825.cs class Test { private var myField; //CS0825 static int Main() { var a = 1; // var is OK here return -1; } }  
```  
  
## Siehe auch  
 [Implizit typisierte lokale Variablen](/dotnet/csharp/programming-guide/classes-and-structs/implicitly-typed-local-variables)