---
title: "Compilerfehler CS1959 | Microsoft Docs"
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
  - "CS1959"
dev_langs: 
  - "CSharp"
helpviewer_keywords: 
  - "CS1959"
ms.assetid: 20a31619-3e30-446a-becc-a7f8cfcec66d
caps.latest.revision: 5
caps.handback.revision: 5
author: "BillWagner"
ms.author: "wiwagn"
manager: "wpickett"
---
# Compilerfehler CS1959
'Name' ist vom Typ 'typ'. In einer Konstantendeklaration muss als Typ 'sbyte', 'byte', 'short', 'ushort', 'int', 'uint', 'long', 'ulong', 'char', 'float', 'double', 'decimal', 'bool', 'string', ein Enumerationstyp oder ein Verweistyp angegeben werden.  
  
 Die in eine Konstantendeklaration zulässigen Typen sind auf die in dieser Meldung beschriebenen eingeschränkt.  
  
### So beheben Sie diesen Fehler  
  
1.  Deklarieren Sie die Konstante mit einem zulässigen Typ.  
  
## Beispiel  
 Der folgende Code generiert Fehler CS1959, da `null` kein Typ ist.  
  
```  
// cs1959.cs class Program { static void Test<T>() where T : class { const T x = null; // CS1959 } }  
```  
  
## Siehe auch  
 [Konstanten](/dotnet/csharp/programming-guide/classes-and-structs/constants)   
 [null](/dotnet/csharp/language-reference/keywords/null)