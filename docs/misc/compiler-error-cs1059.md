---
title: "Compilerfehler CS1059 | Microsoft Docs"
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
  - "CS1059"
dev_langs: 
  - "CSharp"
helpviewer_keywords: 
  - "CS1059"
ms.assetid: 3ebd02ab-e40d-4aad-b901-a0cb6e2eace7
caps.latest.revision: 8
caps.handback.revision: 8
author: "BillWagner"
ms.author: "wiwagn"
manager: "wpickett"
---
# Compilerfehler CS1059
Der Operand eines Inkrement\- oder Dekrementoperators muss eine Variable, eine Eigenschaft oder ein Indexer sein.  
  
 Dieser Fehler wird ausgelöst, wenn Sie versuchen, einen konstanten Wert zu erhöhen oder zu verringern. Er kann auch auftreten, wenn Sie versuchen, einen Ausdruck wie `(a+b)++` zu erhöhen.  
  
### So beheben Sie diesen Fehler  
  
-   Legen Sie die Variable als nicht konstant fest.  
  
-   Entfernen Sie den Inkrement\- oder Dekrementoperator.  
  
-   Speichern Sie den Ausdruck in einer Variablen, und erhöhen Sie dann die Variable.  
  
## Beispiel  
 Im folgende Beispiel wird CS1059 generiert, da `i` eine Konstante und keine Variable und `E` ein `Enum`\-Typ ist, dessen Elemente auch Konstantenwerte sind.  
  
```  
// CS1059.cs class Program { public enum E : sbyte { a = 1, b = 2 } static void Main(string[] args) { const int i = 0; i++;            // CS1059 E test = E.a++; // CS1059 } }  
```  
  
## Siehe auch  
 [Konstanten](/dotnet/csharp/programming-guide/classes-and-structs/constants)