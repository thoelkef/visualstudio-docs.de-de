---
title: "Compilerfehler CS1929 | Microsoft Docs"
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
  - "CS1929"
dev_langs: 
  - "CSharp"
helpviewer_keywords: 
  - "CS1929"
ms.assetid: effdd5d4-e156-418b-9d45-4ca194ab4319
caps.latest.revision: 6
caps.handback.revision: 6
author: "BillWagner"
ms.author: "wiwagn"
manager: "wpickett"
---
# Compilerfehler CS1929
Instanzenargument: Konvertierung von 'TypA' in 'TypB' nicht möglich.  
  
 Dieser Fehler wird generiert, wenn Sie versuchen, eine Erweiterungsmethode über eine Klasse aufzurufen, die sie nicht erweitert. Im hier gezeigten Beispiel wird die Erweiterungsmethode für die abgeleitete Klasse `A` definiert, jedoch nicht für die Basisklasse `B`.  
  
### So beheben Sie diesen Fehler  
  
1.  Erstellen Sie eine neue Erweiterungsmethode für den Typ an der Stelle, wo Sie sie aufrufen müssen. Verschieben Sie den Aufruf andernfalls in ein Objekt des Typs, der von der vorhandenen Methode erweitert wird.  
  
## Beispiel  
 Durch den folgenden Code werden die Fehler CS1928 und CS1929 ausgelöst:  
  
```  
// cs1929.cs using System.Linq; using System.Collections; static class Ext { public static void ExtMethod(this A a) { } } class A : B { } class B { static void Main() { B b = new B(); b.ExtMethod(); // CS1929 } }  
```  
  
## Siehe auch  
 [Erweiterungsmethoden](/dotnet/csharp/programming-guide/classes-and-structs/extension-methods)