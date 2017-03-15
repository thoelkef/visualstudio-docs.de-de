---
title: "Compilerfehler CS0751 | Microsoft Docs"
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
  - "CS0751"
dev_langs: 
  - "CSharp"
helpviewer_keywords: 
  - "CS0751"
ms.assetid: 2ebaed5f-d3ca-452f-8fce-f3299b84360a
caps.latest.revision: 5
caps.handback.revision: 5
author: "BillWagner"
ms.author: "wiwagn"
manager: "wpickett"
---
# Compilerfehler CS0751
Eine partielle Methode muss in einer partiellen Klasse oder Struktur deklariert sein.  
  
 Es ist nicht möglich, eine [partielle](/dotnet/csharp/language-reference/keywords/partial-method) Methode zu deklarieren, sofern diese nicht in einer partiellen Klasse oder Struktur gekapselt ist.  
  
### So beheben Sie diesen Fehler  
  
1.  Entfernen Sie entweder den `partial`\-Modifizierer aus der Methode, und stellen Sie eine Implementierung bereit, oder fügen Sie ansonsten den `partial`\-Modifizierer zur einschließenden Klasse oder Struktur hinzu.  
  
## Beispiel  
 Im folgenden Beispiel wird der Fehler CS0751 generiert:  
  
```  
// cs0751.cs using System; public class C { partial void Part(); // CS0751 public static int Main() { return 1; } }  
```  
  
## Siehe auch  
 [Partielle Klassen und Methoden](/dotnet/csharp/programming-guide/classes-and-structs/partial-classes-and-methods)