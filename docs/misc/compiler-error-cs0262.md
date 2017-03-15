---
title: "Compilerfehler CS0262 | Microsoft Docs"
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
  - "CS0262"
dev_langs: 
  - "CSharp"
helpviewer_keywords: 
  - "CS0262"
ms.assetid: 44f8661f-c934-483f-84cd-00ca8257e50a
caps.latest.revision: 8
caps.handback.revision: 8
author: "BillWagner"
ms.author: "wiwagn"
manager: "wpickett"
---
# Compilerfehler CS0262
Partielle Deklarationen von "Typ" haben Zugriffsmodifizierer, die miteinander in Konflikt stehen.  
  
 Dieser Fehler tritt auf, wenn ein partieller Typ über inkonsistente Modifizierer wie "public", "private", "protected", "internal" oder "abstract" verfügt. Diese Modifizierer müssen in allen partiellen Deklarationen für diesen Typ einheitlich sein. Weitere Informationen finden Sie unter [Partielle Klassen und Methoden](/dotnet/csharp/programming-guide/classes-and-structs/partial-classes-and-methods).  
  
## Beispiel  
 Im folgenden Beispiel wird CS0262 generiert:  
  
```  
// CS0262.cs class A { public partial class C  // CS0262 { } private partial class C { } }  
```