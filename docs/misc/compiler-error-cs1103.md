---
title: "Compilerfehler CS1103 | Microsoft Docs"
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
  - "CS1103"
dev_langs: 
  - "CSharp"
helpviewer_keywords: 
  - "CS1103"
ms.assetid: 513a26ea-9d66-4dc3-b3e6-d709c3089b1a
caps.latest.revision: 6
caps.handback.revision: 6
author: "BillWagner"
ms.author: "wiwagn"
manager: "wpickett"
---
# Compilerfehler CS1103
Der erste Parameter einer Erweiterungsmethode darf nicht den Typ "Typ" haben.  
  
 Der erste Parameter einer Erweiterungsmethode darf kein Zeigertyp sein.  
  
## Beispiel  
 Im folgenden Beispiel wird CS1103 generiert:  
  
```  
// cs1103.cs public static class Extensions { public unsafe static char* Test(this char* charP) { return charP; } // CS1103 }   
```  
  
## Siehe auch  
 [Erweiterungsmethoden](/dotnet/csharp/programming-guide/classes-and-structs/extension-methods)   
 [Unsicher](/dotnet/csharp/language-reference/keywords/unsafe)