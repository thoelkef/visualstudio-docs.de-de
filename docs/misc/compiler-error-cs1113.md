---
title: "Compilerfehler CS1113 | Microsoft Docs"
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
  - "CS1113"
dev_langs: 
  - "CSharp"
helpviewer_keywords: 
  - "CS1113"
ms.assetid: ef2d828f-b5ee-4be9-ba2e-36df5502cc5a
caps.latest.revision: 8
caps.handback.revision: 8
author: "BillWagner"
ms.author: "wiwagn"
manager: "wpickett"
---
# Compilerfehler CS1113
Die im 'Name'\-Werttyp definierten 'Name'\-Erweiterungsmethoden können nicht zum Erstellen von Delegaten verwendet werden.  
  
 Die für Klassentypen definierten Erweiterungsmethoden können zum Erstellen von Delegaten verwendet werden. Für Werttypen definierte Erweiterungsmethoden können dazu nicht verwendet werden.  
  
### So beheben Sie diesen Fehler  
  
1.  Ordnen Sie die Erweiterungsmethode einem Klassentyp zu.  
  
2.  Machen Sie aus der Methode für die Struktur eine normale Methode.  
  
## Beispiel  
 Im folgenden Beispiel wird der Fehler CS1113 generiert:  
  
```  
// cs1113.cs using System; public static class Extensions { public static S ExtMethod(this S s) { return s; } } public struct S { } public class Test { static int Main() { Func<S> f = new S().ExtMethod; // CS1113 return 1; } }  
  
```  
  
## Siehe auch  
 [Erweiterungsmethoden](/dotnet/csharp/programming-guide/classes-and-structs/extension-methods)