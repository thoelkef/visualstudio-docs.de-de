---
title: "Compilerfehler CS0664 | Microsoft Docs"
ms.custom: ""
ms.date: "12/14/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-csharp"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "CS0664"
dev_langs: 
  - "CSharp"
helpviewer_keywords: 
  - "CS0664"
ms.assetid: 60fe15a7-db22-414f-a7b8-fac79dad22b4
caps.latest.revision: 9
caps.handback.revision: 9
author: "BillWagner"
ms.author: "wiwagn"
manager: "wpickett"
---
# Compilerfehler CS0664
Literale vom Typ 'double' können nicht implizit in den 'Typ'\-Typ konvertiert werden. Verwenden Sie ein 'Suffix'\-Suffix, um ein Literal mit diesem Typ zu erstellen.  
  
 Eine Zuordnung konnte nicht abgeschlossen werden. Verwenden Sie ein Suffix, um die Anweisung zu korrigieren. Die Dokumentation für die einzelnen Typen identifiziert das entsprechende Suffix für den Typ. Weitere Informationen zu Konvertierungen finden Sie unter [Umwandlung und Typkonvertierungen](/dotnet/csharp/programming-guide/types/casting-and-type-conversions).  
  
 Im folgenden Beispiel wird CS0664 generiert:  
  
```c#  
// CS0664.cs class Example { static void Main() { decimal d1 = 1.0;   // CS0664, because 1.0 is interpreted // as a double. // Try the following line instead. decimal d2 = 1.0M;  // The M tells the compiler that 1.0 is a // decimal. Console.WriteLine(d2); } }  
```  
  
## Siehe auch  
 [Typkonvertierungstabellen](../Topic/Type%20Conversion%20Tables%20in%20the%20.NET%20Framework.md)