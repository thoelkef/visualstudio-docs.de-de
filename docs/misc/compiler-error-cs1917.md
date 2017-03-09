---
title: "Compilerfehler CS1917 | Microsoft Docs"
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
  - "CS1917"
dev_langs: 
  - "CSharp"
helpviewer_keywords: 
  - "CS1917"
ms.assetid: 05688706-e4b4-4273-9244-48cce1f7f9b9
caps.latest.revision: 6
caps.handback.revision: 6
author: "BillWagner"
ms.author: "wiwagn"
manager: "wpickett"
---
# Compilerfehler CS1917
Member des schreibgeschützten Felds "Name" vom Typ "Strukturname" können nicht mit einem Objektinitialisierer zugewiesen werden, da es sich um einen Werttyp handelt.  
  
 Schreibgeschützte Felder, die Werttypen darstellen, können nur in einem Konstruktor zugewiesen werden.  
  
### So beheben Sie diesen Fehler  
  
-   Ändern Sie die Struktur in einen Klassentyp.  
  
-   Initialisieren Sie die Struktur mit einem Konstruktor.  
  
## Beispiel  
 Der folgende Code generiert CS1917:  
  
```  
// cs1917.cs class CS1917 { public struct TestStruct { public int i; } public class C { public readonly TestStruct str = new TestStruct(); public static int Main() { C c = new C { str = { i = 1 } }; // CS1917 return 0; } } }  
```