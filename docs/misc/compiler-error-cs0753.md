---
title: "Compilerfehler CS0753 | Microsoft Docs"
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
  - "CS0753"
dev_langs: 
  - "CSharp"
helpviewer_keywords: 
  - "CS0753"
ms.assetid: 287dd9da-da74-4290-9fa1-21ef1a8150fe
caps.latest.revision: 5
caps.handback.revision: 5
author: "BillWagner"
ms.author: "wiwagn"
manager: "wpickett"
---
# Compilerfehler CS0753
Nur Methoden, Klassen, Strukturen oder Schnittstellen können partiell sein.  
  
 Der [partial](/dotnet/csharp/language-reference/keywords/partial-type)\-Modifizierer kann nur mit Klassen, Strukturen, Schnittstellen und Methoden verwendet werden.  
  
### So beheben Sie diesen Fehler  
  
1.  Entfernen Sie den `partial`\-Modifizierer aus dem Variablen\- bzw. Sprachkonstrukt.  
  
## Beispiel  
 Durch den folgenden Code wird der Fehler CS0753 ausgelöst:  
  
```  
// cs0753.cs using System; public partial class C { partial int num; // CS0753 public static int Main() { return 1; } }  
```  
  
## Siehe auch  
 [Partielle Klassen und Methoden](/dotnet/csharp/programming-guide/classes-and-structs/partial-classes-and-methods)